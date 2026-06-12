---
title: "Installing Python 2.6.2 on 10.04, Strange Issue"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by smagister on 2010-08-10
Hello,

I'm running Ubuntu 10.04-Desktop 64bit within a VMWare virtual machine.

I've encountered a strange problem while trying to install an older version of Python (2.6.2) which is different than the version (2.6.5) which comes installed by default on Ubuntu 10.04-Desktop.

As for why I'm installing an older version of Python, it's because of some requirements for a pre-existing application which is known to work with 2.6.2.

Since Python is already installed, I've set up an isolated folder, /usr/local/assets/python where python 2.6.2 is to be installed via the --prefix configure flag.

I do:

$ cd /usr/local/src
$ wget [http://www.python.org/ftp/python/2.6.2/Python-2.6.2.tgz](http://www.python.org/ftp/python/2.6.2/Python-2.6.2.tgz)
$ tar zxvf Python-2.6.2.tgz
$ cd Python-2.6.2
$ ./configure --enable-shared --with-zlib=/usr/include --prefix=/usr/local/assets/python
$ make

At this point, to test the binary that (I thought) I made, I run
$ /usr/local/src/Python-2.6.2/python

And I am greeted with this:

Python 2.6.5 (r265:79063, Apr 16 2010, 14:15:55) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.

Somehow, the Python 2.6.5 binary which is included with the Ubuntu 10.04 distribution has been copied to the source code directory rather than the Python 2.6.2 binary that I thought that I had compiled. Running "make install" just copies 2.6.5 to the installation destination.

I thought that somewhere in the make script the included Python 2.6.5 binary was being called and somehow being used as the compiled binary so I actually deleted the binary from /usr/bin/python2.6, along with the symbolic links /usr/bin/python and /usr/bin/python2. Upon repeating the same steps the python 2.6.5 binary again appears! I don't even know where it is coming from!

If anyone has any insight or suggestions or an explanation, please let me know.

Thanks,

Sam

---

### Post by newbie02 on 2010-09-10
Ok, i ran across your post was having to build an older image and followed your process with the same outcome.

So I deleted the folder and started over
then did
./configure
make
after it built everything was good. When I executed the binary python file the version number matched.
I think something about you configure line must have tainted the build.

Hope that helps
Newbie02

---

### Post by 3rr0r on 2010-12-13
Totally worked.  Thank you very much!!

---

