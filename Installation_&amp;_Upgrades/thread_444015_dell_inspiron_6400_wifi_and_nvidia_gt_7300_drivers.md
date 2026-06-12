---
title: "dell inspiron 6400 wifi and nvidia gt 7300 drivers install"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by scribblez on 2007-05-14
Ok so I am a complete linux noob and have been using it for about 6 hours. So far I like it alot more then vista which is what this laptop originally had on it.  However, Ive been having some problems installing the drivers for these things. Ive been hearing its a pain to get them going. But heres what  Ive done so far.

Wifi: i have the dell 1390 wifi card and have been following this guide, its for the E1505 but I hear that is very similar to the inspiron 6400. 
[http://ubuntuforums.org/showthread.php?t=297092&highlight=no+rule+to+make+target+uninstall](http://ubuntuforums.org/showthread.php?t=297092&highlight=no+rule+to+make+target+uninstall)

And at step three when it says to 
[QUOTE=STEP 3: COMPILE PROGRAM

Now we'll complile the Ndiswrapper program.  In a terminal, go to the directory where you extracted ndiswrapper and execute the following:

```

sudo make uninstall
```

**IMPORTANT: Do the above command multiple times.  You can stop when you get the message that says something about no files or directories found.**

```

sudo make
sudo make install
```[/QUOTE]

I type in sudo make uninstall and get an error "make: *** No rule to make target `uninstall'.  Stop." I also don't think I may be typing it in the right directory, I understand what a directory is but how do I change it?


For the video card:
I download the driver from [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)
but I dont understand how to install it. The command they give doesn't work and doesnt seem like its a  code used by GNOME. Any help is appreciated. some of the copy and paste stuff seems to be a bit messy for some reason as well.

---

### Post by Jamie Jackson on 2007-09-11
Yeah, I think you're trying to compile from the wrong directory.

This should get ndiswrapper installed, and in includes a directory change (enter one line at a time, ctrl-c to copy from here, and ctrl-shift-v to copy into the terminal):

```

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
mkdir -p ~/bcm43xx/ndiswrapper; cd ~/bcm43xx/ndiswrapper
sudo wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.47.tar.gz -Ondiswrapper.tar.gz
tar xvzf ndiswrapper.tar.gz
cd ndiswrapper*
make distclean
make
sudo make install

```

The line starting with "cd" is the one that takes you into the expanded ndiswrapper directory.

This is a snippet from my [HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") on how to install this device, in which you'll find that you probably didn't need to have compiled anything in the first place (but oh well, it doesn't really hurt to do so).

Finally, you owe it to yourself to get to know the Linux command line better. You'll only need an hour or two to learn the basics, and you can get those online or in any beginner's Linux book from your library. You'll learn things like: The Linux directory structure, listing directory contents, moving/copying files, etc. One of the greatest things about Linux is the command line. :)

---

