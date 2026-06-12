---
title: "Installing latest version of Pymol from source?"
date: 2016-05-02
forum: Installation &amp; Upgrades
---

### Post by mic3 on 2016-05-02
I use Ubuntu and already have Pymol 1.7.x installed, but I get errors when I try to use the APBS plugin. I read online that installing the latest version of Pymol from source solves this error

I followed this link to try to compile the latest version of Pymol from source [http://tubiana.me/how-to-install-and-compile-pymol-windows-linux-mac/](http://tubiana.me/how-to-install-and-compile-pymol-windows-linux-mac/)

However, I only see a Pymol shell script created, not an executable. When I then try to run "./pymol" or "./pymol.sh", I get the error

    > File "/home/Softwares/Pymol/modules/pymol/__init__.py", line 72, in <module>
    import pymol
    File "/home/Softwares/Pymol/modules/pymol/__init__.py", line 536, in <module>
    import pymol._cmd
    ImportError: /home/Softwares/Pymol/modules/pymol/_cmd.so: undefined symbol: png_check_sig

Here are the contents of the newly created pymol script

     > #!/bin/bash
     export PYMOL_PATH="/home/Softwares/Pymol/modules/pymol/pymol_path"
     "/home/username/anaconda2/bin/python" "/home/Softwares/Pymol/modules/pymol/__init__.py" "$@"
    
And here are the contents of the previous pymol script that worked for Python 1.7.x

    > #!/bin/sh
    # debian wrapper script for pymol

    test -r ${HOME}/.pymol && . ${HOME}/.pymol

    PYMOL_PATH=${PYMOL_PATH:=`/usr/bin/python2.7 -c "from imp import find_module; print find_module('pymol')[1]"`}
    PYMOL_DATA=${PYMOL_DATA:=/usr/share/pymol/data}
    PYMOL_SCRIPTS=${PYMOL_SCRIPTS:=/usr/share/pymol/scripts}
    CHEMPY_DATA=${CHEMPY_DATA:=/usr/share/pymol/data/chempy}

    export PYMOL_PATH
    export PYMOL_DATA
    export PYMOL_SCRIPTS
    export CHEMPY_DATA

    /usr/bin/python2.7 -m pymol.__init__ ${1+"$@"}

---

### Post by ubfan1 on 2016-05-02
What version Ubuntu are you running?  On a 14.04, I just downloaded the pymol 1.8x and followed the tutorial exactly and the resultant executable, pymol, was put into ~/Softwares/Pymol/pymol.  Before this, I tried just running the python setup.py build  without any other defines, and didn't get an error, but no executable I could find.  After setting up the prefix and modules defines, rerunning produced the modules directory and the pymol exe.  I didn't define any other names. The executable ran successfully, not that I did anything with it other than seeing the windows.

---

### Post by ubfan1 on 2016-05-02
The missing png_check_sig is in libpgn12:
$ nm /usr/lib/x86_64-linux-gnu/libpng12.a |fgrep check
0000000000000cc0 T png_check_cHRM_fixed
0000000000000f60 T png_check_IHDR
00000000000000f0 T png_check_sig
...
And is in png.h

---

