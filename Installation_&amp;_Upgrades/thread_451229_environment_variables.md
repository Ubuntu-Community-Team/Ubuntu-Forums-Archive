---
title: "environment variables"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by Barthpi on 2007-05-22
Hello,

i am still trying to install the meep package and its dependancies. To do that, i have to link libraries. THere is one library, hdf5, which is installed, and working, but that meep doesnt see. 
According to meep website, i have to change the environment variables 
LDFLAGS
CPPFLAGS 
LD_LIBRARY_PATH 

how can i modify these environment variables. Is there a file that i should change, or do i make it from the terminal ?

Thanks

Pierre

---

### Post by lloyd_b on 2007-05-22
Setting environment variables is typically done in a terminal window, like follows:
```
export LDFLAGS=somevalue
```
This sets the value of LDFLAGS (deleting any previous value).

If you need to add something to an existing environment variable:
```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/somevalue
```
This appends "/usr/lib/somevalue" onto the end of the existing path.

Note that these changes only affect the current terminal window.  So once you've set the environment variables, you need to run the "./configure" or "make" command in that terminal window.

You can potentially add these commands to the file "~/.bashrc", which will make them affect any terminal window you open afterward.  But if I'm understanding what you're doing corrrectly, you only need these values set long enough to get the program compiled and installed, so it's probably best just to manually add them in a terminal window, and then run the "./configure" and "make" from that window.

Lloyd B.

---

