---
title: "gpp can't find the string header file"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by gulyman on 2012-01-14
Here is my code
```
#include <iostream>
#include <string>
using namespace std;

int main(){
    string input;
	return 0;
}
```
When I use this
```
gpp test.cpp
```
I get this
```
test.cpp:2: error: Requested include file not found
```
That's all that gpp prints out. I looked to see if gpp had a verbose mode, but couldn't find anything.

I just installed xubuntu 2 hours ago. I did install the build-essential package.

Do I have to install the missing header files? Or maybe gpp doesn't know where to look for them? Any help would be very appreciated :)

---

### Post by lkraemer on 2012-01-19
If you are compiling from source, (yours or downloaded) you will need to
extract the source, then cd to the source subdirectory. Once there you
need to look for a readme file or document describing how to compile the
source.  You also need to look for a makefile and a configure file. They
may or may not exist. Same for any/some documentation.............
That's your responsibility.

[B]
INSTALL REQUIRED SOFTWARE FOR COMPILE:[/B]
Typically you need to install build-essential and the headers for the
kernel you are running, if you are going to compile code.
```

uname -r

```
will tell you the kernel you are currently running.
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install the software needed to compile your code.

Next you need to locate what your error is telling you.  To do this you
need to update your database for searches with:
```

sudo updatedb

```
Now, your searches will contain the updated information.  Search for
"string" without the quotes with:
```

locate string

```
To narrow your search you may use grep also:
```

locate string | grep include

```
Notice that the file name to be included appears to be string.h.......
Also note that it is enclosed with <string.h>.......versus "string.h"
which is used if the include file is located within your SOURCE directory.

Now find the versions of the compilers you are using:
```

gcc --version
g++ --version
gfortran --version
gcc --version > gcc.txt

```
If you can't locate gcc.txt use:
```

sudo updatedb
locate gcc.txt

```
It should be at /home/loggedinuser/

The next step you need to do is to find the "SHELL" and "env" you are using.  Google will assist you in this......

You need to list the *rc file to verify the contents and set the PATHS. 


**TYPICAL COMPILE STEPS: (from within your source directory)**
assumes you have searched for the configure & makefiles, and Documentation on compiling....
```

./configure
make clean
make
sudo make install

```
"make clean" won't remove anything on the first compile, but will clean up on a successive compile.
It also removes the Bin file from the source subdirectory. It should be obvious to you that if make
doesn't work, there is no need to execute the "sudo make install" command because nothing was built
that could be installed. And after your software is installed, you can do a "make clean" to remove all
the un-necessary files that were generated.

Now try your compile again.....


lk

---

