---
title: "Help: installing kernel headers"
date: 2005-06-20
forum: Installation &amp; Upgrades
---

### Post by the_pc_dude on 2005-06-20
I need help on how to install the kernel headers.

---

### Post by intangible on 2005-06-20
Open a terminal, copy and paste this:

**sudo apt-get install linux-headers-`uname -r`** (Don't forget the backticks!!)

---

### Post by the_pc_dude on 2005-06-20
not online  I have an intel modem trying to the driver installed

---

### Post by intangible on 2005-06-20
That command should still work.

Try this to make it easy to find the headers from the console:
**sudo ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux**
Then do this to make sure the symlink is correct (make sure some items show up)
**ls /usr/src/linux**

Then, anything that needs the kernel headers should find them without a problem.

---

### Post by the_pc_dude on 2005-06-21
Will apt-get work offonline I heard it didn't. I'm an newbie to Debian Based OS's . Thanks Man Your Life saver.

---

### Post by intangible on 2005-06-21
apt-get will work offline if you have the cd added as a repository (which is the default with Ubuntu), just make sure it is in the drive.

---

### Post by the_pc_dude on 2005-06-21
I tried what you said but it has an warning: PostDrop: can't pick up public/pickup It said something like that.

---

### Post by intangible on 2005-06-21
That's a new error for me :?

Have you tried searching for "linux-headers" in synaptic and adding them that way?

---

### Post by the_pc_dude on 2005-06-21
Do I have to link the makefile with the headers?

---

### Post by intangible on 2005-06-21
What modem model do you have?  What instructions are you following trying to get it to work?  Maybe I can simplify it.  Anyway, below are some basic instructions for compiling a kernel module.

Try this, disreguard what you have already done:
```

sudo -s
apt-get install linux-headers-`uname -r`
ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux
cd /full/path/to/src/directory
./configure --prefix=/usr
make

```

There is almost certainly a README file in the directory for the src code you are trying to compile, use pico to read it, it should have more detailed instructions.

---

### Post by intangible on 2005-06-21
What modem model do you have?  What instructions are you following trying to get it to work?  Maybe I can simplify it.  Anyway, below are some basic instructions for compiling a kernel module.

Try this, disreguard what you have already done:
```

sudo -s
apt-get install linux-headers-`uname -r`
ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux
cd /full/path/to/src/directory
./configure --prefix=/usr
make

```

There is almost certainly a README file in the directory for the src code you are trying to compile, use pico to read it, it should have more detailed instructions.

hope this helped

---

### Post by az on 2005-06-21
Did you get the linux-headers installed, then?

That package creates a symlink in /lib/modues/(version)/build to the headers so that it is automagically configured if your driver is properly written.

Maybe this will help:
[https://wiki.ubuntu.com/forum/hardware](https://wiki.ubuntu.com/forum/hardware)

---

### Post by the_pc_dude on 2005-06-23
I've got the modem problems take care of I was installing the source and I dependence problems so I went into Rec Mode and installed that way. But now I have problems wvdial I typed in wvdial.txt and it says it can't find modem and says did you configure with setserial and also an warning says that wvdial.txt doesn't exist in wvdial.conf.

---

### Post by intangible on 2005-06-24
Did you setup the connection using **pppconfig**?

---

### Post by the_pc_dude on 2005-06-25
Crap! Good thing you mention that. That's not I'm Probs with intel driver [see](http://ubuntuforums.org/showthread.php?t=44127)

---

### Post by intangible on 2005-06-26
Unfortunately it looks like you'll have to find someone else with the same hardware to help you out.  After the modem module working properly, it should be just as easy as any other modem to setup with **pppconfig**

---

