---
title: "Problem with 686 kernel - it's installed, but how do I enable it?"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by kry10 on 2006-08-11
Hello, everyone:

Relatively new Ubuntu user here with a strange problem (at least, I couldn't find anything similar on the forums). I've got a Pentium D, and I'd like to use the 686 kernel so I can use both processors. I've installed linux-686 using Synaptic. However, when I boot, I only have a choice in grub to use the default 386 kernel. It looks like I have all of the required 686-related files in /boot. Any advice on booting using the 686 kernel? Thanks in Advance for your help!

Mark

---

### Post by christhemonkey on 2006-08-11
Type in a terminal:
```
sudo update-grub

```

That should add it to your bootup GRUB menu.

---

### Post by az on 2006-08-11
You installed linux-686 and you do not have a grub entry?  Were there any errors when you installed?

What does

sudo apt-get -f install

say?


Unrelated, but I think you need 686-SMP....

---

### Post by christhemonkey on 2006-08-11
linux-686 and linux-686-smp both give the same version of kernel.
SMP support has for a longish while now, been included by default in the 686 kernel.

Although, if they do change this, for upgrades sake, it may be better if they have the 686-smp package...

---

### Post by kry10 on 2006-08-11
> **christhemonkey said:**
> Type in a terminal:
```
sudo update-grub

```

That should add it to your bootup GRUB menu.

Well, when I do that, here's what I get:

```
Searching for GRUB installation directory ...
No GRUB directory found.
 To create a template run 'mkdir /boot/grub' first.
 To install grub, install it manually or try the 'grub-install' command.
 ### Warning, grub-install is used to change your MBR. ###

```

---

### Post by kry10 on 2006-08-11
> **azz said:**
> You installed linux-686 and you do not have a grub entry?  Were there any errors when you installed?

What does

sudo apt-get -f install

say?


Unrelated, but I think you need 686-SMP....

Nope, no errors when I originally installed. When I run sudo apt-get -f install, I get:

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by christhemonkey on 2006-08-11
Can you do this please?
```
sudo apt-get remove grub
sudo apt-get install grub 
```

Although it may complain about wanting to remove lots of things, so if you feel likely to want to do this, write down all the things you want to reinstall afterwards!

---

### Post by kry10 on 2006-08-11
> **christhemonkey said:**
> Can you do this please?
```
sudo apt-get remove grub
sudo apt-get install grub 
```

Although it may complain about wanting to remove lots of things, so if you feel likely to want to do this, write down all the things you want to reinstall afterwards!

Thanks for the replies. OK, I've done the apt-get remove and install, rebooted, and still only have the 386 choice. BTW, I tried sudo update-grub again, but got the same error message.

Curiously, during the reinstall of grub, apt-get recommended I also install grubconf. However, when I tried apt-get install grubconf, I receive:

```
Reading package lists... Done
Building dependency tree... Done
Package grubconf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grubconf has no installation candidate

```

Any more ideas?

---

### Post by kry10 on 2006-08-14
Bump. 

BTW, this weekend I also updated my home machine with Ubuntu. It's an Athlon X2 and, at first, Ubuntu used the 386 kernel (as expected). However, I just upgraded to the K7 kernel and, low and behold, I have the K7 option in GRUB, and I now have multi-processor goodness at home!

However, no such love with the Pentium D at work. I've gone so far as to do a clean reinstall, but I'm still having the same problems as I reported earlier. I know that I could just complile my own kernel and install it by hand, but I'd really rather get it working "The Ubuntu Way" first :D

---

### Post by kry10 on 2006-08-14
SOLVED!

And the answer is soooo out of left field ... 

I tried booting off of the Ubuntu LiveCD and rebuilding GRUB from there. Well, after running sudo fdisk -l, just to double-check my partitions, I noticed it reported a RAID device, /dev/md0. Well, I didn't set up any raid partions during my install, but I did have a raid installation on these hard drives from a previous installation. After a little more detective work, I noticed that the partition that /boot was on still had a RAID superblock! So, using mdadm, I removed the superblock info, did a fresh install again, and voila! I can upgrade to the 686 kernel without any problems.

Moral of the story: If you think you're installing onto a fresh drive, make sure it's really fresh :)

---

