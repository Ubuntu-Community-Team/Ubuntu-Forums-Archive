---
title: "[SOLVED] How to change install.sh to ubuntu comatible ?"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by UncleCz on 2008-02-11
Hello, i am total noob to ubuntu, switched from windows a few days ago..but i allways managed to get my things working with the help of this forum. Now i am trying to get my stoneage motherboard working like it should with the help of i815 tweaker which i finally found for linux too.
The problem is, install.sh doesn't work for me:

```


#!/bin/sh
make -C /usr/src/linux SUBDIRS=$PWD modules
make -C /usr/src/linux SUBDIRS=$PWD modules_install
depmod -ae


```

After i run the install.sh i get this:

```

sudo sh install.sh
make: Entering directory `/usr/src/linux'
make: *** No rule to make target `modules'.  Stop.
make: Leaving directory `/usr/src/linux'
make: Entering directory `/usr/src/linux'
make: *** No rule to make target `modules_install'.  Stop.
make: Leaving directory `/usr/src/linux'

```

btw, i had to create the linux dir on my own to actually get it to show me at least this..



I downloaded the file from: 

[http://linux.softpedia.com/get/System/System-Administration/i815-linux-tweak-27780.shtml#](http://linux.softpedia.com/get/System/System-Administration/i815-linux-tweak-27780.shtml#)

Thank you in advance for helping me, thus this is driving me crazy..

Your UncleCz :-)

---

### Post by rich.bradshaw on 2008-02-11
Did you run it as root?

sudo ./install.sh

---

### Post by UncleCz on 2008-02-11
Yes, i do ..Wow, what a fast response :-)

---

### Post by henrismail on 2008-02-11
Hmm... heres the oraninal sourceforge site you could try compileing from code manually; 

[http://sourceforge.net/project/showfiles.php?group_id=197534]("http://sourceforge.net/project/showfiles.php?group_id=197534")

---

### Post by UncleCz on 2008-02-11
That is what i downloaded..
I untarred it and ran the install.sh as root.... that's what i originally did...

---

### Post by niethslim on 2008-02-11
usr/src/linux is usually a link to the directory where your kernel source is.
In /usr/src there should be a folder named linux-headers-2.6.22-14 or some thing like that.
Deleting the empty Linux folder you created and in stead putting a link may help.
```

cd /usr/src
rm linux
ln -s  linux-headers-2.6.22-14 linux
```
I not really sure this will help and not mess up your computer, so you should wait for a more experienced user to confirm it's safe before trying it.

---

### Post by hyperair on 2008-02-11
First of all, what kernel are you using? Find out using the command "uname -r". You should get a string akin to 2.6.24-7-generic or 2.6.24-7-386 for example. What you need to take note of is the "generic" or "386" keyword at the end. It could also be rt or something else.

Then install the kernel headers for your kernel. 
```
sudo apt-get install linux-headers-generic
```
Replace "generic" with any other keyword as you've identified above.

Next, you need to make /usr/src/linux point to the appropriate linux header folder:
```

sudo ln -sf /usr/src/linux /usr/src/linux-headers-`uname -r`

```

EDIT: Looks like I was late.

---

### Post by UncleCz on 2008-02-11
Thank you all, this works for me... :-)

---

### Post by hyperair on 2008-02-11
Great to hear.

---

