---
title: "Imac bootcamp ubuntu 10.04 install problem?"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by alchemistic on 2010-07-24
Hi Everyone, I've just been trying to enter the world of linux, but I'm having problems with the install. I've followed the guide, and I understand what I'm doing, but the install keeps freezing after I boot with CD on my Imac..

I've tried burning the CD's on my PC and mac, burning different downloads etc.. So far the only progress I've made is instead of getting a black screen with flashing underscore, I get the white screen with the penguin.

Is this normal? In the guide it says that there is a waiting period where it appears to freeze on the boot menu, but is this longer than an hour?

Does ubuntu 10.04 work on Imacs? Does it work on OSX 10.5+?

Any help would be much appreciated!

Thanks

---

### Post by metapunk on 2010-07-24
Ok, so I've lost everything in the sense of formatting errors and partitions not being recognized after attempting to install 10.04 on my aluminum imac, but I did find a way to get it working, although it's still a constant battle between mac and linux.

First you need REFIT bootloader, occasionally mac os x rewrites over it, so it's a good idea to have the CD on hand for later when Mac decides to wipe it out.

This is what I've done to get it working after I end up with the unhappy question mark boot.

I boot to the live CD for Ubuntu 10.04

Next I get into the terminal - accessories - terminal
Then I go into /etc/apt/sources.list and uncomment the universe repository.
sudo nano /etc/apt/sources.list 
find the lines that say universe and delete the # sign in front of it
CTRL X and yes to save

Next run
sudo apt-get update

sudo apt-get install gdisk

then I just run 
sudo gdisk
 and write over the MBR - WARNING - this may cause data loss 

after that I run 
sudo apt-get install gptsync
sudo gptsync
and let it sync and pretty much confirm

After that I can follow the instructions for the file not found error at the bottom of [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) - see Error 15 - File not found

This will mount the linux partition as and reinstall grub.

After I do this I can reboot into linux using REFIT and also get into mac os x. I hope that this helps someone.

---

### Post by alchemistic on 2010-07-26
Thanks for the help - I decided to try downloading an older version (9.10), and so far all is going well - just installing so hopefully make happytime

---

