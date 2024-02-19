[![Downloads](https://static.pepy.tech/badge/sourceshot)](https://pepy.tech/project/sourceshot) [![Downloads](https://static.pepy.tech/badge/sourceshot/month)](https://pepy.tech/project/sourceshot) [![Downloads](https://static.pepy.tech/badge/sourceshot/week)](https://pepy.tech/project/sourceshot)

The purpose of this package is taking pictures of code.

To run sourceshot, do
```
from sshot import shot
from PIL import Image
code='''
print('Hello World!')
'''
image=shot(code,lang='python')
Image.fromarray(image).save('code.png')
```

The code above will create something like:
![](https://i.postimg.cc/sxLHWpJ7/code.png)

Use in command line:
```commandline
sshot -i test.py -l python -o code.png
sshot -i test.py -l python -o code.png -b bg.png # Add background image.
sshot -i test.py -l python -o code.png -b 00FF00FF0000 # Red code background color, green line number background color.
sshot -i test.py -l python # Show the image in a tkinter window.
```

Here is a picture of a C++ program generated using this tool:
![](https://i.postimg.cc/vThsBYJh/rc.png)


It is also supported to set the background image of code, like:

```python
from sshot import shot
from PIL import Image
from sshot.background import Background
import numpy as np
code='''
print('Hello World!')
'''
bg=np.array(Image.open('bg.png'))
image=shot(code,lang='python',background=Background(bg))
Image.fromarray(image).save('code.png')
```

### Syntax highlight config in JSON file.

A correct syntax highlight config should have a 'config' key.
It can also have an optional 'default' key.

The 'config' key is a dictionary, the key in that dictionary stands for the token name in the TokenChecker class (builtin, identifier, etc.)
The 'default' key stands for the default color.

For example:

```json
{
  "config": {
    "builtin": [127,0,0],
    "exception": [0,127,0],
    "string": [0,0,127]
  },
  "default": [127,127,127]
}
```

Using the JSON file above to create a picture of the code "print('Hello World!'), you will get:
![](https://i.postimg.cc/Mp48Jdxz/code2.png)

How to install?

```commandline
pip install sourceshot
```

[link](https://pypi.org/project/sourceshot/)