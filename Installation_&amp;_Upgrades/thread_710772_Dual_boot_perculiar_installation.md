---
title: "Dual boot perculiar installation"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by elicoten on 2008-02-28
Hi

I installed Ubuntu onto a machine that had Windows XP installed. I tried to get the installer to install the MBR and bootloader onto HD1 (instead of HD0) because I didn't want to touch my XP disk at all during installation. However when it came to installing the bootloader installation failed. Using WUBI I managed to get GRUB4DOS installed on HD0 from within Windows, and if I type in the commands manually I can boot the system.

My main question is what is left not quite finished/intalled. This installation looks very much like the live CD rather than an installed version, for example the partition editior is still installed, and there is an icon to "install" in the Administration menu. My question is how can I "finish off" the installation and do all the little things that the installer didn't do at the end? Does anyone know exactly what has been left not done that still needs doing and what kind of issues it could cause? Generally speaking the system seems to be running nicely but I'm just curious about what might not be properly installed.

Thanks very much.

---

### Post by Bucky Ball on 2008-02-28
Hi elicoten. Check my post entitled -

Dual Boot Solution

If you couldn´t be bothered with that, just go straight here:

[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)

This might bring you some joy.

I suggest you make a boot CD of super grub disk, re-install Ubuntumaking sure not mix the two bootloaders on the same disk (or partition), as you say, then restart the machine and see what happens. If there is total confusion (can´t boot into either or both OS´s), restart but this time boot from Super Grub disk and (if you have another computer handy!) check out the documentation to see what is right for your situation, then let this little marvel go to work on your boot loaders. Worked for me.

---

### Post by elicoten on 2008-02-29
Thanks for your reply. I actually can boot into either now as the configuration stands although booting into Ubuntu is a hassle because I have to type the boot commands manually. 

The main reason for my post was because I still seem to have a Ubuntu that looks like a Live-CD rather than an installed version and I wondered if there was some process at the end of the installation that does a few (probably small things) to change it slightly. Two examples I have noticed is the presence of an "install" option, as well as the partition editor which do not appear on my other (regular, single boot) installation of Ubuntu.

Thanks once again.

---

### Post by dstew on 2008-02-29
How did you install it? Did you use a Live CD? It does sound like your desktop is not right.

---

### Post by logos34 on 2008-02-29
> **elicoten said:**
> The main reason for my post was because I still seem to have a Ubuntu that looks like a Live-CD rather than an installed version and I wondered if there was some process at the end of the installation that does a few (probably small things) to change it slightly. Two examples I have noticed is the presence of an "install" option, as well as the partition editor which do not appear on my other (regular, single boot) installation of Ubuntu.

You might want to try installation again.  Set the ubuntu drive as first in the Bios hard disk boot order.  Then let grub install to the mbr of the ubuntu disk (now hd0), leaving windows undisturbed.

---

### Post by elicoten on 2008-02-29
[QUOTE="dstew"]
How did you install it? Did you use a Live CD? It does sound like your desktop is not right. [/QUOTE]
Yes I used the live CD.
[QUOTE="logos34"]You might want to try installation again. Set the ubuntu drive as first in the Bios hard disk boot order. Then let grub install to the mbr of the ubuntu disk (now hd0), leaving windows undisturbed.[/QUOTE]
I can't do that because its an external drive. In any case I've already customised it quite a bit I don't want to re-install now.

Thanks for your assistance.

---

### Post by Bucky Ball on 2008-02-29
Sounds like you might have to, elicoten. That definitely does not sound right. Where are you running the Ubuntu OS from? A CD or from the external hard drive? Sounds to me like you are running the live CD from the boot image on your external hard drive. Just a guess and happy to stand corrected. More info please; ie are you booting Ubuntu from external hard drive?  :)

---

### Post by elicoten on 2008-03-01
I'm definately booting from the external hard drive and its not a CD image its properly installed just it seems that a few "clean-up" type operations at the end of the installation failed (probably because the boot-loader installation failed). 

My guess is that there's something that's supposed to happen as, or after, the bootloader is installed, and because installing the bootloader failed, whatever else this is also failed.

But apart from the that the installation seems to be running normally. I could simply use Alacarte to remove the menu entries (or synaptic to remove the partition manger) and then it would look absoultey fine I just wondered if there was anything else I needed to know or that should have happened.

---

### Post by Bucky Ball on 2008-03-02
My guess is that you are not getting a fast enough transfer rate from the external hard drive, especially if it is USB, to run the OS. I have just done a quick bit of research and,  if this is a USB drive you are talking about, it is highly likely.. As always, willing to stand corrected.

Another is the OS loads the USB drivers!

An external eSATA drive connected to eSATA port could possibly solve the data transfer rate problem, but maybe start doing some research on this and see if you can find a solution.

---

### Post by elicoten on 2008-03-02
I'm a bit confused by this - the O/S runs fine the problem was with the installation procedue I don't see how the data transfer rate would affect this. 

Running under Windows I found that the data transfer rate to/from the external hard drive when new/empty was actually significantly greater than the transfer rate to the old, much fuller internal drive. I know this is not a fair test but I don't think the problem is anything to do with the data transfer rate.

I know that on my computer, this drive has transferred at speeds of at least 20Mb/sec which should be plenty and therefore unlikely to be the cause of the problem.

Thanks for your continued assistance. We'll get there in the end!

I have since used the package manager to remove CASPER and the other Ubiquity stuff, which got rid of the install icon but I just wondered if there was anything else I should do. I have also tried reinstalling grub and running
```
sudo update-grub
``` to generate the menu.lst file which was not present before. Now the system starts up better, I haven't tested my copy of the bootsector from the NTLOADER menu entry but last time it booted I didn't have to type any commands in, and the Ubuntu splash screen showed which it never did before (presumably because I wasn't typing the right command for it)

My only question is what else is/could be missing that I should check?

---

