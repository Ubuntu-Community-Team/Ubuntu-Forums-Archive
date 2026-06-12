---
title: "Ubuntu Feisty Server doesn't boot after install on Epia MS"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by vak on 2007-04-23
I have installed recently released Ubuntu Feisty Server at my [Epia MS]("http://www.via.com.tw/en/products/mainboards/mini_itx/epia_ms/"). Installation ended successfully, but after reboot one can see smth like a "stating up" and in few second an empty screen with the following info at bottom:

```
Int 14: CR2 c1000000 err 00000002 EIP c03f3c3e CS 00000060 flags 00010016
Stack: 373c0046 00000000 ffffffff c0490000 000011e0 00000080 001e0000 ffffff80
```

any hints?

---

### Post by neillandf on 2007-04-23
Same problem and almost exactly the same error codes on my Asus M6Ne

---

### Post by vak on 2007-04-23
I ve managed to get rid of it with Ubuntu Feisty Alternative CD distro.

see [https://launchpad.net/ubuntu/+bug/71594](https://launchpad.net/ubuntu/+bug/71594)

the issue is closed for me.

---

### Post by Damnit_Daniel on 2007-04-27
Got the same issue on Virtual PC 2k4...  No answers or recommendations yet?  Bug report?

---

### Post by az on 2007-04-27
The VIA C3 processor is not fully a 686-type processor.  The server kernel will only run on a 686 or better.  The workaround is to use the desktop kernel.  It will work fine.

As stated, installing from the alternate cd will install the desktop (386- Dapper, generic- Edgy,Fiesty) kernel.  

Right now, you can boot the server installer disk (it boots the desktop kernel, actually) and chroot into your installed system and install the desktop kernel onto it.

sudo apt-get install linux-image-386 linux-server-

---

### Post by glmeece on 2007-06-07
Hey, AZ -

For those of us ignorant types - how does one chroot from the recovery mode of the install CD?  I've tried several times, and I get lost using a terminal from the CD and using the terminal on the hard drive just causes the screen to just sit there.  Can you specify the steps necessary to do what you've described?

Thanks!

---

### Post by glmeece on 2007-06-07
OK, I sorta answered my own question.  Boot into rescue mode, run terminal from CD.  Type "chroot /target" and go.

HOWEVER, when I do so, I get the error message:
[FONT=Courier New]E: Couldn't find package linux-image-386[/FONT]

Any thoughts?

---

### Post by glmeece on 2007-06-08
Thanks to the quick response of AZ, I was able to get a bit farther, but still no joy.  

To update this thread, two additional things are needed:
[LIST]
[*]You need to do a "[FONT="Courier New"]sudo apt-get update[/FONT]" in order to connect with the repositories (I had some problems with that, but that's a separate issue).
[*]The image for Feisty is actually called "[FONT="Courier New"]linux-image-generic[/FONT]".
[/LIST]

At any rate, what happened for me is when I tried to install the generic kernel, it couldn't see my boot volume (it's a separate volume), so it couldn't update Grub.  I tried to update Grub manually (I have very little experience with that) and failed miserably.

I'm about to punt and just use a desktop install.  I had really hoped to use this machine as an optimized server setup, but at this point I guess I'll just have to take what I can get.  Unless...someone else here perhaps has a suggestion such as how to run the server installer but force it to use the generic kernel (just a SWAG on my part).

---

### Post by fanluofan on 2007-06-10
I have the same problem after installing Ubuntu Server Edition 7.04, my HP notebook mobile centrino will not start and show the following error:

Int 14: CR2 c1000000 err 00000002 EIP c03f3c3e CS 00000060 flags 00010016
Stack: 373c0046 00000000 ffffffff c0490000 000011e0 00000080 001e0000 ffffff80

I will try out the alternative CD as other guys has suggested and explained in bug#71594

---

### Post by glmeece on 2007-06-11
Here's how I was finally able to get my install to work...[LIST=1]
[*]As I mentioned, I tried doing the whole [FONT=Courier New]chroot [/FONT]thing, but had limited results (still no bootable machine).  However, when I did attempt the [FONT=Courier New]apt-get install[/FONT], it couldn't see my actual boot partition, so it created a /boot directory on my root (/) slice.  So, I used one of the live desktop CD's (in my case, I just decided to play around with the Xubuntu CD).  So, I booted with that live CD, and then looked in the [FONT=Courier New]/boot[/FONT] directory on my root slice and used that as a reference.
[*]I deleted all similarly-named files in my actual [FONT=Courier New]/boot[/FONT] directory, and then copied everything over from the directory from my root slice.
[*]Next, I edited (with [FONT=Courier New]sudo[/FONT]) the [FONT=Courier New]menu.lst[/FONT] (or whatever it's named) on my boot slice to reflect the new filenames for the Linux kernels I was using.
[*]I rebooted and it mostly worked (actually, it hung at the scripts portion of the bootup), so I tried again with a safe boot.
[*]At that point, I did an [FONT=Courier New]apt-get update[/FONT] and then install to re-install the generic kernel.  I rebooted and all was well![/LIST]So, thanks AZ and everyone else for your help.  I hope the above helps someone else.

---

