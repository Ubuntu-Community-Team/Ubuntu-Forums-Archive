---
title: "howto compile cam drivers"
date: 2019-03-18
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2019-03-18
Hi,
  my Lenovo IdeaPad Miix 320-10ICR runs ubuntu-mate 18.04 nicely except that the two cams are not being recognized. Even updating to kernel 5.02 did not help. However, I  recently found 2 files on Linus' page with the corresponding ov2680.c and ov5670.c files that are supposedly the listings of the corresponding driver modules. 
Can anybody please indicate how I can compile these files and install the resulting modules!

Thanks, D-E

---

### Post by oldrocker99 on 2019-03-23
It's easier to compile and install source code than you might thihk. To compile source code, first do this:```
apt install build-essential
```
That will install everything to compile source code, but read below.

Download the files, and decompress them with an archive manager. Cd to that folder and look for a file called "configure." It is very likely to be there. Then run it:```
./configure
```
Either all the -dev files are installed, or you will be told which files are missing. Use Synaptic to find the files, and they **must** end in -dev, which are the libraries that compilation uses.

Once you have all the libraries installed, the configure script will create, and tell you it is doing so, a file called "make." So, ```
make
```
This command compiles the code. Some errors may be displayed, but don't worry about them. After compilation,```
sudo make install
```

This is, as I said, not all that hard. Post any problems you may have.

---

### Post by dieter-erich on 2019-07-13
Hi oldrocker99,
  please forgive me for coming back to you only now! Thanks a lot, but can you please give me some more hints how to proceed from here:
  [https://github.com/torvalds/linux/blob/master/drivers/media/i2c/ov2680.c](https://github.com/torvalds/linux/blob/master/drivers/media/i2c/ov2680.c). I tried to git clone this repository, but it is huge and I certainly do not need to do it. So, should I just download the file shown and then follow your instructions?  But there is no Makefile included... 
bw D-E

---

