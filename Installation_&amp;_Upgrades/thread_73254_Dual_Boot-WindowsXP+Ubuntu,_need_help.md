---
title: "Dual Boot-WindowsXP+Ubuntu, need help"
date: 2005-10-08
forum: Installation &amp; Upgrades
---

### Post by ultra.nj on 2005-10-08
Ok, I've been pretty much following everything in this thread

[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

But everytime I try to load up the GRUB thing after I restart, there's an error that says "HAL.DLL" is missing or corrupt, and it forces me to start Windows.  I tried replacing the HAL.DLL file with another one, but it messed up Windows.  Luckily, I was able to run the repair on the Windows XP CD, and I'm now back to where I started.  Any help would be greatly appreciated.  Yes, I am a newbie at this, this is my first time installing Linux.

Edit: I don't have Ubuntu installed yet.

---

### Post by aysiu on 2005-10-08
Does [this thread](http://ubuntuforums.org/showthread.php?t=6747) help?

---

### Post by ultra.nj on 2005-10-08
I am unsure of what he did exactly, I don't know which partition number he is talking about.

---

### Post by kondor on 2005-10-08
Start Windows, select "run" and type" msconfig" at the command prompt.

When the System Configuration window comes up, click on Boot.ini at the top.

You can compare your boot file to his and see what partition your windows is, etc.

Good luck.

---

### Post by Elrohir on 2005-10-09
had the same problem not long ago... tried every suggestion given by users... no luck... as you dont have Ubuntu installed, backup your info and reinstall everything from scratch...

it cost me a lot, but it works...

btw, install WinXP first, then Ubuntu on top... ;-)

---

### Post by thomsuey on 2005-10-19
I had the same issue and got it to work.  

First, mount your Windows boot volume.  To do this, as root, I add the following line to /etc/fstab:

/dev/hda2       /mnt/c          ntfs    umask=0222       0       0

Then, as root, did 'cd /mnt' followed by 'mkdir c' to get the mount point added.

Next was to issue the terminal command:  

'sudo mount /mtn/c' to get the filesystem visible.

I then browsed to /mnt/c and copied boot.ini to my home directory so that I could modify it.

My original was:
...
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows...
...

I modified the instances of 'partition(1)' to be 'partition(2)'

Then I found a utility, from [http://linux-ntfs.sourceforge.net/status.html#ntfstools](http://linux-ntfs.sourceforge.net/status.html#ntfstools)

Downloaded from:  [http://prdownloads.sourceforge.net/linux-ntfs/ntfsprogs-1.12.1.tar.gz](http://prdownloads.sourceforge.net/linux-ntfs/ntfsprogs-1.12.1.tar.gz)

and extracted to my home dir and from that location I ran

./configure
make
sudo make install

I had to add some development tools from the package manager (gcc etc.).  When you run ./configure,  it will tell you which ones are missing.

Once that was done, I ran (after unmounting my Windows volumen via 'sudo umount /dev/hda2'):

sudo ntfscp /dev/hda2 /home/mthompson/boot.ini boot.ini

Windows now boots again!

---

### Post by comforteagle on 2006-01-30
[QUOTE=Elrohir]had the same problem not long ago... tried every suggestion given by users... no luck... as you dont have Ubuntu installed, backup your info and reinstall everything from scratch...

it cost me a lot, but it works...

btw, install WinXP first, then Ubuntu on top... ;-)[/QUOTE]

I'm having this hal.dll problem, but I installed winxp first!  WTF?

---

### Post by yud on 2006-07-16
> **thomsuey said:**
> I had the same issue and got it to work.  

First, mount your Windows boot volume.  To do this, as root, I add the following line to /etc/fstab: ...

Windows now boots again!


I had to register only to say THANKS :p :mrgreen: 

I was losing my hair having lost my wife windows partition, but your walkthrough worked perfect!

---

### Post by fokuslee on 2006-12-29
thomsuey THANKS
good guide 
I will post a how-to credited to you and leezer (because soo many posts on the same question are unanswered) 
his guide is largely similar to yours 
[http://www.ubuntuforums.org/showthread.php?t=78509&highlight=hal.dll+missing](http://www.ubuntuforums.org/showthread.php?t=78509&highlight=hal.dll+missing)
thx again.

---

### Post by SimonFinch on 2007-07-19
I've followed the above guides and got as far as rebooting into XP.  It still won't do it. :confused:

I've attached a screen grab of my partitions - do I need to change any of the numbers?
e.g.

> modified the instances of 'partition(1)' to be 'partition(2)'

should I be using another number?

I've managed for a month like this, so I guess I don't really need Windoze that much :o

Cheers,

Simon.

---

