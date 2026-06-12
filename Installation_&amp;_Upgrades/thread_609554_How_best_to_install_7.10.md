---
title: "How best to install 7.10"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by Cloudedbrains on 2007-11-11
Hi again ;)
I've just received my 7.10 gutsy disks and after replacing some hardware recently, 
I am wondering whether I should just give Gutsy a go alone :)

I tried dual booting with feisty and hated it so was wondering if I should just 
format windows and give Gutsy ago on its own :confused:

I have a 250gig hard-drive and was wondering how is best to partition it if I 
am just going to try Gutsy (with no windows) :(

SOme advice in simple terms would be gratefully received :)

---

### Post by Lem on 2007-11-11
Use the installer and simply choose 'guided - use all of disk' (or something along those lines)

OK, you end up with one big partition, but the default ext3 filesystem is pretty stable compared to fat/ntfs. The installer will choose  a suitable swap partition size and set that up for you automatically.

---

### Post by Cloudedbrains on 2007-11-11
Thanks Lem :)

Another basic question here:
If I back up my documents to dvd will I be able to put the stuff itself back on under Ubuntu ???

---

### Post by Lem on 2007-11-11
Yep.. no problem. You can back up to dvd, usb stick whatever. Ubuntu can read/write windows filesystems.

---

### Post by Cloudedbrains on 2007-11-11
Thanks

---

### Post by Cloudedbrains on 2007-11-12
Okay have finally done my backups of the partition with My Documents on :o
But I realised that windows would probably be happy to live on its own partition which is 100gig and that I could use the bigger partition (135gig) for Gutsy :)

But when I tried dual booting with feisty I hated it !!
Is it any better under Gutsy ??

And how would be best to do this ??

Try a virgin install of Gutsy all alone or try a dual boot ??

SIMPLE terms needed please ;)

Also would WUBI be an option for me ??

---

### Post by bulldog on 2007-11-12
> **Cloudedbrains said:**
> Okay have finally done my backups of the partition with My Documents on :o
But I realised that windows would probably be happy to live on its own partition which is 100gig and that I could use the bigger partition (135gig) for Gutsy :)

But when I tried dual booting with feisty I hated it !!
Is it any better under Gutsy ??

And how would be best to do this ??

Try a virgin install of Gutsy all alone or try a dual boot ??

SIMPLE terms needed please ;)

Also would WUBI be an option for me ??

I f you can explain to us what you hated when you dual boot,we can help you better.
Was it GRUB......don't dual boot.
Was it changing the bootorder in BIOS to boot either one......use GRUB.

Some partition advice:

Installing and partitioning:
If you plan to use ubuntu only,some advice.
To avoid upgrades and the chance of breaking things consider the following partition plan.

Create 2 partitions 10GB each.
Create one swap 1-2GB max
Create one /home as big as you like

Now you can install ubuntu on one of 10GB partitions [/] and mount the /home partition as /home

Now you can install another ubuntu or what ever,or if there's a new release you can install it without loosing your excisting install.[clean install]
Use the same /home and swap,only,and this is important,use another user name,so there will be a new user created in your /home,and no mixing up between the distro's will happen.
You can,as root,copy files you want between the two users.

---

### Post by Cloudedbrains on 2007-11-12
The problem I had with dual boot was getting it to boot direct to Ubuntu as I had to keep a ps2 keyboard plugged in to select Ubuntu as my main keyboard is USB :)

If I can get it to boot direct to Ubuntu and only needing to choose windows IF I needed to would be better but I just couldnt do it last time :(

Windows is on a 100gig partition and the other 135gig one could be free for Ubuntu IF I can get it too boot direct to Ubuntu ;)

---

### Post by MotHaiBa on 2007-11-12
Hi, I first installed Ubuntu 8 months ago and this was one of the sites I used to help with partitions and installations.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Hope that helps.

Cheers

---

### Post by erfahren on 2007-11-12
> **Cloudedbrains said:**
> The problem I had with dual boot was getting it to boot direct to Ubuntu as I had to keep a ps2 keyboard plugged in to select Ubuntu as my main keyboard is USB 


did you check your BIOS for Legacy USB support?
see this search: [http://www.google.com/search?hl=en&q=grub+usb+keyboard&btnG=Google+Search](http://www.google.com/search?hl=en&q=grub+usb+keyboard&btnG=Google+Search)

---

### Post by misawa on 2007-11-12
> **Cloudedbrains said:**
> The problem I had with dual boot was getting it to boot direct to Ubuntu as I had to keep a ps2 keyboard plugged in to select Ubuntu as my main keyboard is USB :)

If I can get it to boot direct to Ubuntu and only needing to choose windows IF I needed to would be better but I just couldnt do it last time :(

Windows is on a 100gig partition and the other 135gig one could be free for Ubuntu IF I can get it too boot direct to Ubuntu ;)

Navigate to this directory: /boot/grub/menu.lst  You can do this either from a terminal (where you'll have to log in as the root user) or select Places>Computer and double-click file system.  Once you're in the grub directory, find menu.lst and open it.  From here you can change the boot order.

---

### Post by Cloudedbrains on 2007-11-12
Cheers have enabled legacy USB and will see if that helps ;)
Just need to find time to install Gutsy now :o

---

### Post by Cloudedbrains on 2007-11-12
I've done it :D
Did the USB legacy think and have installed Gutsy :)
And it boots into it just fine ;)

---

