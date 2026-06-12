---
title: "How to Install Creative Webcam PD1001 on linux."
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by AngelicNecro77 on 2012-04-25
I don't know how to do this but I like messing with things to learn it myself and finally, I admit defeat. I have a USB webcam that needs the CD to install or software installational downloads. I downloaded epcam-src-1.3.2.tar.gz off the internet. Then I extracted them like the instructions said:

```
To install epcam linux driver follow this:

1. Download the source files that are included in epcam-src-<version>.tar.gz
2. Open a terminal
3. Go the directory where you downloaded epcam-src-<version>.tar.gz
4. Make sure you have kernel development packages installed, otherwise you won't be able to build the driver from source files.
5. Type in your terminal each of the following commands:

	tar xfvz epcam-src-<version>.tar.gz
	make
	sudo make install
	sudo modprobe epcam

To deinstall the driver:

	sudo rmmod epcam
	sudo make uninstall

To clean up files created during the build:

	make clean
```

I opened the terminal, but when I tried to type it in or copy and paste it in, it kept saying it couldnt read it. I tried everything I could think of. Please help? I would love step by step instructions please. I'm still new to this.

---

### Post by papibe on 2012-04-25
Hi AngelicNecro77. Welcome to the forums!

You can skip a couple of steps if you use nautilus (file manager). Open the directory where you downloaded the file. Right click on it and select 'extract here'.

A new directory will be created.

Then we can walk you to the rest of the steps.

Regards.

---

### Post by cmont899 on 2012-04-25
If you downloaded the files in your browser they probably ended up in the Downloads directory. Try the following:

1) Open Terminal
2) change to your downloads directory
```
cd ~/Downloads
```3) Run the commands supplied by Creative:
```
tar xfvz epcam-src-<version>.tar.gz
make
sudo make install
sudo modprobe epcam
```*make sure you are replacing <version> with the actual version that is in the filename.

*Alternatively you can use epcam-src-*.tar.gz to replace the filename

---

### Post by AngelicNecro77 on 2012-04-25
What's a Kernal source tree? it told me to remember that I need read/write access to it. Maybe that's what's wrong with the code creative gave me? If so, then how to I gain access to it? Do I need to install or download it?

---

