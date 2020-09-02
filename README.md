bin2png
=======

A simple cross-platform script for encoding any binary file into a lossless PNG.
Each pixel of the output image encodes three bytes of the input file: The first byte is encoded in the red channel,
the second byte in the green channel, and the third byte in the blue channel.  All files will be tail-padded with zeros
so that they have a byte count that is a multiple of three.  The dimensions of the output image are automatically
calculated such that they are as close to a multiple of three as possible.  If there are multiple dimensions that
require minimal padding, the one that is closest to square is chosen.  The width and height of the output image can
also be optionally overridden.

bin2png is backward compatible with both Python 2 and Python 3.

On Windows, this is another solution: https://github.com/leeroybrun/Bin2PNG

## Usage

```shell
$ pip install bin2png

$ bin2png file_to_encode -o output.png

$ bin2png -d output.png | diff - file_to_encode -s
Files - and file_to_encode are identical
```

Additional instructions are availble by running with the `-h` option.

## Author

Evan Sultanik<br />
https://www.sultanik.com/<br />

Initial Python3 port by [zenarcher007](https://github.com/zenarcher007), along with implementation of the `-v` and `-s`
options.


-----------  
Fork by zenarcher007:  
Latest commit:  
• Changed --no-progress to -p --progress in order to follow standards and eliminate confusion in the code and
when being used as a module.  
• You can now use bin2png.encode(infile, outfile=(path), square=(bool), width=(number), height=(number), progress=(bool), verbose=(bool))
when importing bin2png as a module in a script.  
```
>>> import bin2png
>>> f = bin2png.encode("test")
>>> print(f)
<PIL.Image.Image image mode=RGB size=72x1987 at 0x10752DD90>
```
I will try to implement bin2png.decode next.
