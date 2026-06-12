---
title: "Friday the 13th Update, Something had to go wrong"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by jonlatane on 2007-04-13
It seems today several updates were released for Feisty, however I seem to be having a problem downloading them.  Synaptic/Update Manager don't give a lot of info, but when I run sudo apt-get dist-upgrade I get:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-2.6.20-15 linux-headers-2.6.20-15-generic linux-image-2.6.20-15-generic linux-restricted-modules-2.6.20-15-generic
The following packages will be upgraded:
  app-install-data fglrx-control gnome-app-install gnome-menus gnome-power-manager hotkey-setup initramfs-tools launchpad-integration libgnome-menu2 liblaunchpad-integration0 liblpint-bonobo0
  libvte-common libvte9 linux-generic linux-headers-2.6.20-14 linux-headers-2.6.20-14-generic linux-headers-generic linux-image-2.6.20-14-generic linux-image-generic linux-libc-dev
  linux-restricted-modules-common linux-restricted-modules-generic python python-gmenu python-launchpad-bugs python-launchpad-integration python-minimal python-vte python2.5 python2.5-minimal
  readahead update-manager update-manager-core xorg-driver-fglrx xserver-xorg-input-evdev
35 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.8MB/103MB of archives.
After unpacking 180MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Err http://us.archive.ubuntu.com feisty/main linux-image-2.6.20-14-generic 2.6.20-14.23
  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb  403 Forbidden [IP: 91.189.89.8 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Is anyone else having this issue?  I seem to be able to download most of the packages fine, but when it gets to linux-image-2.6.20-14 it gets a 403 forbidden error.  Has Ubuntu removed the package and is giving me that error or what?  Do they think I have been abusing that server for some reason (I most certainly have not)?  Any ideas?

---

### Post by LermanetDOTcom on 2007-04-13
yeah I just noticed that too

---

### Post by floke on 2007-04-13
The 20-14 kernel update is a cock-up mess that won't boot - it has since been withdrawn - but the apt-get side of it probably hasn;t been updated yet - try updating via synaptic but ignore the 20-14 updates - i.e. undo them before applying.

---

### Post by teddybairs1 on 2007-04-13
Any idea why 20-15 won't show up in GRUB? It still says 20-14.

---

### Post by p0g0 on 2007-04-13
Hi, how do I get rid of the 2.6.20-14 image from appearing in my updates? I´ve just installed 2.6.20-15 so is useless to keep showing in there. I´d appreciate any tips that you can give.

---

### Post by Slipmyknot101 on 2007-04-13
Yeah it must be a Fr. the 13th thing. I've got it too. I don't want to be one of the complainers though that just carries on a thread with no apparent solution so my best advise is to wait this one out. Time will fix it (I think).

---

### Post by xopher on 2007-04-13
Too bad I'm not superstitious. :rolleyes:

---

### Post by jonom on 2007-04-13
Can anyone give tips on how to fix the boot problem?

I installed the updates today and now can't boot into Ubuntu - it stops at the Ubuntu splash screen with the status bar thingy. :(

---

### Post by p0g0 on 2007-04-13
> **jonom said:**
> Can anyone give tips on how to fix the boot problem?

I installed the updates today and now can't boot into Ubuntu - it stops at the Ubuntu splash screen with the status bar thingy. :(

Review this thread: [http://ubuntuforums.org/showthread.php?t=408253](http://ubuntuforums.org/showthread.php?t=408253)

---

### Post by old_geekster on 2007-04-13
I just installed 2.6.20-15 generic and it is doing the same thing as -14.   I am using -13 to type this post.

Just for your info, I am getting a constant "boink, boink" (Don't know how else to describe it.) sound from my system.  It is the sound that I usually get when I login.  So, I simply mute the sound.  It worked great until the update to -14.  Whatever happened, bugged all of the kernels.

Steve K's comment is appropriate " kernel -14 is a cock-up mess.  In my opinion, so is -15.

I guess that is why they call us Feisty Testers.

How do I remove kernel 10, 11, 12, 14, 15 from the GRUB screen?  I have run searches on Google, but can't find the solution.

---

### Post by p0g0 on 2007-04-13
> **old_geekster said:**
> How do I remove kernel 10, 11, 12, 14, 15 from the GRUB screen?  I have run searches on Google, but can't find the solution.
 Edit your menu.lst file located @ /boot/grub/ with gedit or your prefered text editor. You can do it by tiping in the console 

```
 sudo gedit /boot/grub/menu.lst
```

Then it´ll open up your file and scroll down until you find this section:

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4cabdb04-12d2-4eb8-928c-170fcfd64d9d ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4cabdb04-12d2-4eb8-928c-170fcfd64d9d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.20-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=4cabdb04-12d2-4eb8-928c-170fcfd64d9d ro quiet splash
initrd		/boot/initrd.img-2.6.20-14-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=4cabdb04-12d2-4eb8-928c-170fcfd64d9d ro single
initrd		/boot/initrd.img-2.6.20-14-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

And just erase the entries (or in this case, the images that you don´t want to appear in GRUB) and save. In your next boot you will see that you only have the images that you left in there.

---

### Post by skopa on 2007-04-13
i am the complainer
geekster i removed old kernels through synaptic, make a search for linux-image 2.6.20-15
for example, though i am not sure if this is the right path...
also i suggest that you keep one that boots to your machine
by the way 2.6.20-14.22 works for me,.23 that is friday the 13th's update doesn't

---

### Post by p0g0 on 2007-04-13
> **skopa said:**
> i am the complainer
geekster i removed old kernels through synaptic, make a search for linux-image 2.6.20-15
for example, though i am not sure if this is the right path...
also i suggest that you keep one that boots to your machine
by the way 2.6.20-14.22 works for me,.23 that is friday the 13th's update doesn't

Ey thanks, I couldn´t get rid of the 20-14 from showing in my updates but I did what you suggested to geekster and it worked. Although his problem is with GRUB I gave him a hand with that. Tahnks again :D .

---

### Post by Bert Mariën on 2007-04-13
> **p0g0 said:**
> Hi, how do I get rid of the 2.6.20-14 image from appearing in my updates? I´ve just installed 2.6.20-15 so is useless to keep showing in there. I´d appreciate any tips that you can give.

You might try removing the image from the synaptic package manager (search for linux-image or just image) and mark for removal. If it is not there anymore, how can it update, or can it?

---

### Post by skopa on 2007-04-13
pogo if you remove a kernel through synaptic the init tools automatically removes it from the grub entry, at least that worked for me and i think it's safer, maybe an expert eye would be more convenient

---

### Post by p0g0 on 2007-04-13
> **Bert Mariën said:**
> You might try removing the image from the synaptic package manager (search for linux-image or just image) and mark for removal. If it is not there anymore, how can it update, or can it?

I already did it, thanks :).

---

### Post by p0g0 on 2007-04-13
> **skopa said:**
> pogo if you remove a kernel through synaptic the init tools automatically removes it from the grub entry, at least that worked for me and i think it's safer, maybe an expert eye would be more convenient

Yeah, it has  already been taken care off, thanks man :).

---

### Post by lancest on 2007-04-13
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_display_only_one_kernel_on_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_display_only_one_kernel_on_GRUB_menu)
Just - sudo gedit /boot/grub/menu.1st (then comment out the old kernels)
Important for Ubuntu user to learn sooner or later (unless GUI grub tool comes)

---

### Post by lancest on 2007-04-13
Ok you mean complete removal. Got it.

---

### Post by wuzzerd on 2007-04-13
> **old_geekster said:**
> 
How do I remove kernel 10, 11, 12, 14, 15 from the GRUB screen?  I have run searches on Google, but can't find the solution.

Edit or comment them out in /boot/grub/menu.lst

Be sure to remove all lines for each boot option.

---

### Post by old_geekster on 2007-04-13
> **wuzzerd said:**
> Edit or comment them out in /boot/grub/menu.lst

Be sure to remove all lines for each boot option.
Thanks for the quick reply.:D 

This forum is truly like IM.  I have seen some posts about no receiving replies quickly enough.  This has never been my problem.

This is one more turn in my learning curve.  I will make a note of how it is done.

---

### Post by muncrief on 2007-04-13
Please see my mini Howto on how to update to the latest Feisty. Aptitude is broken, but the kernel has been fixed

[http://ubuntuforums.org/showthread.php?t=408860](http://ubuntuforums.org/showthread.php?t=408860)

---

