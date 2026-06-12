---
title: "another: &quot;/bin/sh: can't access tty; job control turned off&quot; case :("
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by Annie Versary on 2007-04-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi there,

I'm just another one facing a problem that many people round the globe seem to have. After - at least seemingly - upgrading to Feisty with success I'm no longer able to boot into Ubuntu. After some seconds the boot process freezes and some minutes later the following error message appears:

```
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
```


Three or four complete installations afterwards didn't solve the problem. Though not using (and luckily needing) Ubuntu for my work I'm quite irritated that my afore smoothly working Ubuntu 6.10 was shred by a release Mr. Shuttleworth - of course - [praised](http://www.ubuntu.com/news/congratulations-ubuntu-7.04) as "the recommended best version of Ubuntu for anyone who wants to use the best of free software!". Thank you so much, Mark!

I've already searched this forum (and other ones in various languages I assume to understand sufficiently) as well as the w3 in general and found a range of 'solutions' oscillating from 'remove all optical drives and USB devices during installation and for the following ten boot ups' to some (other) voodoo kind of stuff. So - to come to an end - as I'm not interested in hacking miles of code, dismantling all the devices my laptop and my PC (same result on both machines) are made of or doing some other sledgehammer-and-screwdriver-work my only point  is:

Does anybody know if there is some kind of workaround to come?

Thanks in advance

Annie

---

### Post by silverbullet007 on 2007-04-24
Here, Here!

---

### Post by arcik on 2007-04-27
Without changing anything in the configuration of my computer, I can boot Feisty using the Super Grub Disk ([http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org)).  I use the "Boot GNU/Linux directly" option on the menu and then the sub-option labeled "SCSI".

Unfortunately, I have very little knowledge about Linux, so I don't know how to find out which settings is the Super Grub Disk using to boot Ubuntu and where to correct the standard settings coming with Feisty.

Can someone help?

---

### Post by patis on 2007-04-27
Bug  [106864]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864") covers this. Here's a summary of the solution:

To Install Feisty:

[LIST=1]
[*]From the main live CD menu press the F6 (? I don't really remember which F key it is) key to customize the boot command. Add the option [FONT="Courier New"]break=top[/FONT] to it and boot up your PC.
[*]When you get to the dreaded (initramfs) prompt, type [FONT="Courier New"]modprobe piix[/FONT], and press enter.
[*]Type [FONT="Courier New"]exit[/FONT] to resume the normal live CD boot.
[/LIST]
The install process should go smoothly from here on. However, when you reboot your PC your are likely to run into the same problem. So do as above to be able to boot your PC into your brand new installation. The permanent fix is the following:

[LIST=1]
[*]Add [FONT="Courier New"]piix[/FONT] to [FONT="Courier New"]/etc/initramfs-tools/modules[/FONT].
[*]Run the command [FONT="Courier New"]sudo update-initramfs -u[/FONT].
[/LIST]
If everything goes well, you won't see this problem ever again. I hope this helps.

---

### Post by silverbullet007 on 2007-04-27
Might I reiterate patis: your above mentioned "fix" does not work for everyone.  Beside's isnt that the one of many reported fixes where you have to keep adding the modprobe value upon each subsequent reboot?  At least I remember seeing posts concerning having to retype the modprobe each time they boot..

---

### Post by patis on 2007-04-27
This is not "my" solution, it is the solution presented by Ben Collins (from the Ubuntu's kernel team) in the referenced bug thread. And I'm not claiming that this is a solution for everyone, I can't tell that. I'm just trying to present in a clean way how I fixed the problem, YMMV.

I myself went through this problem on three different PCs, two at home and one at work. In all cases I applied the fix as I described and it worked well. I have no problems booting those PCs today; fixing the initramfs image with [FONT="Courier New"]update-initramfs[/FONT] fixed the problem permanently for me.

---

### Post by arcik on 2007-04-29
Annie: I've had the same problem as you have and spent hours going through the jungle of posts on this topic. In the end, the solution was, for me at least, VERY simple: I changed the UUID of my disk in my menu.lst (/boot/grub/menu.lst) to the classical identification of device location.

And as the disks are treated by Feisty (as far as I know) as SCSI disks (don't ask me why), you'll have to put sdaX (where X is the number of the partition where Ubuntu is installed) instead of the classical hdaX.

This is the relevant part of my menu.lst right now:
```

title		Ubuntu
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```

Hope this helps. Let me know, if it worked for you!

---

### Post by AchimRS on 2007-05-08
Hi,
so I tried now all what was suggested above - nothing helped:

- Change the UUID in menu.lst and fstab to hda -> exact same behaviour
- Change the hda  in menu.lst and fstab to sda -> less time (only seconds instead of minutes) to come to the same error
- modprobe piix -> no chance to exit the prompt, so no possibility to reboot with the loaded piix module. Simly nothing happened when I entered "exit".
- Boot from DVD and select "Boot from Harddisk" -> same behaviour

So, no I reformat my root partition and make a fresh installation... :-(
After several upgrades with SuSE (9.1 -> 9.2 -> 10.0 -> 10.1 -> 10.2) this is the first time, that an upgrade failed...

Cheers
  Achim

---

### Post by hoagies on 2007-05-10
Hi:

I downloaded and burned Linux Mint 3.0, "Cassandra", BETA, (which is entirely based on Ubuntu 7.04).  (Linux Mint is actually very very pretty, and featureful). ->  The results are the same:  bad!!

I have 4 computers total.  Out of the 4, only one SATA controlled computer agrees with 7.04.  Three PATA controlled computers do not!!

I have watched the loading and installation of (k)ubuntu 6.04, 6.10, and Linux Mint "Bianca", which all load and install well!!  What happens with these versions is, that during the loading/installation process, the installer will halt for something called, (paraphrased):  "Loading modules for the IDE Chipset".  ->  Obviously this is absent in 7.04 and its derivatives!!

I had hoped that Linux Mint would have fixed the problem, since they had all the bug reports  from 7.04 available to them, before launching their BETA.

I also downloaded and burned the new version of Zenwalk, which also uses the 6.2.20 kernel.  Zenwalk will modify the system itself:  Changing everything to "/sdx", (remember, this is "/hdx" territory), and then wrecking everything else on the system!!

The problem lies with the 6.2.20 kernel.  I can not understand why (k)ubuntu, its derivatives, or distros using the 6.2.20 kernel,  are not coming out with "ready made" acknowledgments, statements, patches, fixes, solutions, 

After all, not everybody  is a "computer geek"!!  And after all, problems like this will drive away hordes of "noobs", right out of the box!!  Or worse, they do suspect there's something wrong with their own systems, which I have noticed.  Right??  :lolflag: 

As far as myself goes:  I personally am not interested in having 7.04, for the sake of having 7.04, through the use of "gimmicks".   What the rest of the world needs is an Operating System which works "right out of the box".   :guitar:

---

