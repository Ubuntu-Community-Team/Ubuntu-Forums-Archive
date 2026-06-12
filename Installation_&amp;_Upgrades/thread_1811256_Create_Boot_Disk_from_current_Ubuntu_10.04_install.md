---
title: "Create Boot Disk from current Ubuntu 10.04 installation to avoid GRUB issue?"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by JSJSJS on 2011-07-24
Hello,

I'm new to Ubuntu and have been searching and searching and haven't been able to find anything that solves my issues, so I hope for some help.

I upgraded from Ubuntu 9.x to 10.04 using the upgrade feature within Ubuntu. It worked great, but then I decided to do some stuff with partitions and thought I'd wipe it clean and start with a fresh install...that's where the trouble started. Any new Ubuntu CD I used just ended up with a weird screen that started with white and faded to black  After several failed attempts with fixes when installing 10.04 directly from the .iso downloaded from Ubuntu, I instead reinstalled Ubuntu 9.x and upgraded using the upgrade manager (A painful process because I have such a slow internet connection and an old, slow computer). I'd like to be able to just have a CD that will allow me to re-install Ubuntu as it is currently configured on my machine. I have a Dell Inspiron 8000 and apparently there is some graphics  card issue with the GRUB or something like that? So I assume my current  GRUB in 10.04 is set appropriately for my system and I'd like to be able  to use it for future re-installs.

In a related issue, I want to make some changes to my partitions. Ubuntu is only running on 10 GB partition and the other partition is empty. I want to make a boot disk that will allow me to run GParted or something else that will allow me to expand the Ubuntu partition into the unused 30 GB partition. The problem is that all the tips say to use a Live CD and then unmount the partition and expand it with GParted. The problem is that that won't work due to the issue described above. Thus I found a tip about creating a Bootable Grub disk. This sort-of worked, but it just created a black screen with a command line, which is not something I know how to operate to accomplish what I need. (My memories of DOS commands are faint and I never really knew UNIX commands well)

I'd like to create a CD that would allow me to backup/reinstall my  system as it currently exists on my computer so that I don't have to  deal with installing Ubuntu 9 only to then upgrade and re-install all my  software again. Is that possible? Is there also some way that I could expand my partition, possibly by using this disk and then using GParted?

Thanks for any and all help!!!

---

### Post by ajgreeny on 2011-07-24
Have a look at clonezilla live CD, which will do what it says, ie make a clone of your disk, or partition, or whatever you ask it to clone, it will clone.

You will need somewhere to store the clone, of course, eg a usb hard disk, and then to restore it you run clonezilla again and choose the clone to restore.

I hope your problem with live CDs does not mean you can't even consider this as a possibility.

---

### Post by JSJSJS on 2011-07-24
> **ajgreeny said:**
> Have a look at clonezilla live CD, which will do what it says, ie make a clone of your disk, or partition, or whatever you ask it to clone, it will clone.

You will need somewhere to store the clone, of course, eg a usb hard disk, and then to restore it you run clonezilla again and choose the clone to restore.

I hope your problem with live CDs does not mean you can't even consider this as a possibility.

Thanks for the idea. I checked out their website ([http://clonezilla.org/](http://clonezilla.org/)) and they had this written: "The partition to be imaged or cloned has to be unmounted." Because I cannot unmount the partition that I'm currently using and I can't seem to make a boot disk that will work, I'm not sure this will solve my problem. I suppose I could try it. I wonder if it would work if I were to re-install Ubuntu 9.x on the unused partition and then log into Ubuntu 9.x and then use this software to clone the 10.04 on the other partition?  Anyone done something like this, or maybe there's a simpler way?

---

