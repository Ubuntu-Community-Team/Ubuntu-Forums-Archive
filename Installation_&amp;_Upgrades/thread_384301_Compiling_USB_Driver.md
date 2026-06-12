---
title: "Compiling USB Driver"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by OzOle on 2007-03-14
Please help a novice if you can.

I have an older Toshiba laptop on which I installed K/ubuntu (6.06).
Unfortunately, the Ethernet port has stopped working, 
so I purchased a USB-to-RJ11-Ethernet adaptor. Alas, it came without a driver.
I went to the vendor's website and found what I hope is a usable driver,
however, it is source code and I haven't been able to figure out how to compile it. 
Here are the instructions from the manufacturer (in *Chenglish* (Chinese English)):

====================================================
  DAVICOM Semiconductor Inc.				05/16/2003


        A Davicom DM9601 USB Fast Ethernet driver for Linux. 

        Copyright (C) 1997  Sten Wang


  **A. Compiler command:**


     A-1: For normal single processor kernel

          "gcc -DMODULE -D__KERNEL__ -I/usr/src/linux/include -Wall -Wstrict-prototypes -O6 -c dm9601.c"


===================================================
**Here is what I did:**

1) I opened a terminal, cd'ed to the directory with the installed files:
    dm9601.c
    dm9601.h
    Makefile
    readme.txt

2) **I typed:**
"gcc -DMODULE -D__KERNEL__ -I/usr/src/linux/include -Wall -Wstrict-prototypes -O6 -c dm9601.c"
**REPLY:** bash: gcc: command not found

Looks to me like I'm doing something fairly basically wrong.
===================================================


**The instructions continue:**


  **B. How to compile driver** 
  

     B-1: Login by supervisor  [how  do I do that? sudo???]

     B-2: Copy dm9601.c and Makefile into your HD. You can make a new directoty

          to put.

     B-3: Keep driver source file name as "dm9601.c" and makefile name as 

	  "Makefile"

     B-4: You can type the following command to compile driver. Please according

     	  to your system to pick one.

     		make org
===================================================


I haven't attempted step B. yet because step A. didn't work.
Could somebody please put a newbie on the right track?

Thanks in advance,
Ole from Australia

---

### Post by Arby on 2007-03-14
```
bash: gcc: command not found
```

That means you don't have gcc compiler installed. You'll need that to compile code from source. It isn't installed as standard on ubuntu. If you run the following command it should fix the problem
```
sudo apt-get install build-essentials
```

That will give you gcc and some other standard tools for compiling source code. You can install the same package through Synaptic if you prefer. Then run part A of the manufacturers instructions again.

If you have more trouble just ask

Arby

---

### Post by OzOle on 2007-03-14
Hi Arby,

Thanks for the quick reply, however, mega-problem here:

I can't run apt-get or synaptic because I can't get on the
net because my ethernet connection isn't working, that's
what I need to compile the driver for  :( 

Are those build-essentials perhaps on the standard
Ubuntu live CD? Because then I could perhaps get them
there.

Alternatively, could I download them on another computer
and then transfer them across to the laptop via a memory
stick?

Thanks for trying to help me,

Ole

---

### Post by Arby on 2007-03-14
> I can't run apt-get or synaptic because I can't get on the
net because my ethernet connection isn't working, that's
what I need to compile the driver for 

Oops my bad, sorry. Yes you can use the install CD as a repository. I don't know if build-essentials is on there or not but we can try. We will need to edit your apt sources.list, heres how.

1. Back up your sources.list before you start. If it all goes wrong you have a fall back (but it shouldn't). Run this command in a terminal.
```
sudo cp /etc/apt/source.list /home/you/sources.list_backup
```

2. Now we can edit your source list. next command.
```
sudo nano -w /etc/apt/sources.list
```
This will open your sources.list using the text editor nano

You need to add the following line to that file
```
deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted 
``` If your lucky ubuntu may have done this automatically at install time, mine did. Make sure you change the bit in [ ] to match the version of Ubuntu you are using.

press Ctrl-X to save the change, and press Y when prompted.

3. You'll need to run the following to get apt-get to recognise the new repository.
```
sudo apt-get update
```.
now try running ```
sudo apt-get install build-essentials
```

Disclaimer: I've never needed to use a CD as a repository so we might need some more help from someone else in a bit. 

Anyway try that and let us know what you get. As a guide I've attached my sources.list so you can see how it should look. Let us know how you get on

Arby

---

### Post by OzOle on 2007-03-14
Thanks Arby,

The command to include the cdrom in the sources list doesn't
quite work, but I was informed to simply type: **apt-cdrom**
and sure enough that worked, it now recognized the cdrom

I didn't need to type apt-get update, that happened automatically.
I then typed: apt-get install build-essentials but
unfortunately, they were not on the cdrom.

Now it's getting a bit harder. When I find out where and how to 
source them from the Net, then I will need to copy them to 
a memory stick (or burn them to a cdrom (format?)) and then
use that on the laptop.

Hmmm! Well I got one little step further.

Thanks for your help, much appreciated.

PS. I will be going to bed now, it's just getting to 2 am here,
so I will have to continue tomorrow.

Cheers,
Ole

---

### Post by Arby on 2007-03-14
OK, here's a few things for when you wake up again. 

First another screw up on my part, sorry. The package name is build-essential NOT build-essentials. Oops. So it might be worth trying. ```
sudo apt-get install build-essential
```. It's still possible that the package just isn't available on the CD. In which case, you will need to download the packages from the web. I don't know where to get these from unfortunately, hopefully someone else will jump in with this info.

If you can find them you want to get the files as .deb files. This is the same format that apt-get would have downloaded if it could. Then you copy them to a memory stick or CD (doesn't matter which) to transfer them to the machine in question. Then to install them you would run ```
sudo dpkg install filename.deb
```.

We may run into further problems I just don't know. Something to be aware of is that build-essential is a metapackage. This means it is essentially a list of other packages that need to be installed. This might mean we have to resort to downloading and installing the individual bits seperately, but lets hope not that would be a pain. However I did a bit of digging just in case. You can get apt-cache to tell you what dependencies a given package has. The dependencies of build-essential are below

```
sudo apt-cache depends build-essential
build-essential
 |Depends: libc6-dev
  Depends: <libc-dev>
    libc6-dev
  Depends: gcc
  Depends: g++
  Depends: make
  Depends: dpkg-dev

```

One way or another we need to get that lot onto your system. Hopefully we won't have to resort to getting them individually.

we'll get there eventually :)

---

### Post by OzOle on 2007-03-15
Thanks Arby, I will have a go at it tomorrow and let you know the outcome.

Cheers

---

