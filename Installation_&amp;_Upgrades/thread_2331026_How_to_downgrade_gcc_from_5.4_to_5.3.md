---
title: "How to downgrade gcc from 5.4 to 5.3?"
date: 2016-07-17
forum: Installation &amp; Upgrades
---

### Post by paul263 on 2016-07-17
Hello everyone,

After letting my 64 bit Ubuntu 16.04 run some 'important updates', I discovered that a newer version of gcc has been installed and this led CUDA not to work anymore. Now, when I use CUDA, I get the following error message

```
#error -- unsupported GNU version! gcc versions later than 5.3 are not supported!
```

And after typing in a terminal console

```
gcc --version
```

I get 

```
gcc (Ubuntu 5.4.0-6ubuntu1~16.04.1) 5.4.0 20160609
```

which explains why it doesn't work anymore. After some research, I learned that a solution could be to run the following

```
apt-get remove gcc g++
apt-get install gcc-(version-number) g++-(version-number)
```

But this trick only works for gcc versions < 5 where we could type the commands with a precise version number (ex. 3.4, 4.7, ...) whereas for versions > 5, this commands only works for version-number = 5 (and this installs the latest version available = 5.4).

Therefore, I would really need to downgrade gcc from 5.4 to 5.3 but I don't know which other method I could use. Would you have any ideas about that?

Thanks a lot in advance,
Paul

---

### Post by byrne.yang on 2016-07-22
First download and tar gcc-5.3.0.tar.gz from and to anywhere you are comfortable.
Enter the folder: cd gcc-5.3.0 and download prerequisites: ./contrib/download_prerequisites.
Create a new folder for build and make: cd ..; mkdir gcc-build-5.3.0; cd gcc-build-5.3.0; ../gcc-5.3.0/configure --enable-checking=release --enable-languages=c,c++ --disable-multilib
Finally make and install: make -j4; sudo make install.
Reference: [http://blog.csdn.net/striker_v/article/details/51920627](http://blog.csdn.net/striker_v/article/details/51920627)

---

### Post by jcroteau on 2016-08-07
> **byrne.yang said:**
> First download and tar gcc-5.3.0.tar.gz from and to anywhere you are comfortable.
Enter the folder: cd gcc-5.3.0 and download prerequisites: ./contrib/download_prerequisites.
Create a new folder for build and make: cd ..; mkdir gcc-build-5.3.0; cd gcc-build-5.3.0; ../gcc-5.3.0/configure --enable-checking=release --enable-languages=c,c++ --disable-multilib
Finally make and install: make -j4; sudo make install.
Reference: [http://blog.csdn.net/striker_v/article/details/51920627](http://blog.csdn.net/striker_v/article/details/51920627)
Just a warning to others, I followed this advice, and it broke my system and forced me to reinstall. Installing into a standard location, even into /usr/local, will replace the standard libraries installed with the system with the ones built by GCC 5.3, and it seems there are some binary incompatibilities with applications built under GCC 5.4. The better way to do this is to install GCC 5.3 into an alternate location, for example I installed mine into /opt/gcc-5.3. You can do this by passing --prefix=/opt/gcc-5.3 to the configure script, and then when you run nvcc, pass -ccbin /opt/gcc-5.3/bin to get it to use your compiler.

---

