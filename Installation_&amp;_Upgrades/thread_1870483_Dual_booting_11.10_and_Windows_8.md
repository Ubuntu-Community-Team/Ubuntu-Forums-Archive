---
title: "Dual booting 11.10 and Windows 8"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by faz. on 2011-10-27
Got a dev preview of W8 and trying to run this as a dual (or more) boot with Ubuntu 11.10. Installed W8 first, then attempted to install ubuntu from the disc but it won't appear as a dual boot. Just starts straight into Windows 8.

So I try it within Windows 8, run it inside, and it does it's thing, restarts a few times, says it is done, shuts down and I get a boot menu, but it only has one item on it; Windows 8 Developer Preview.

odd.

So I boot into W8, have a look on my drives and the partition I created for Ubuntu has gone. Next thing I click onto my shared network drive which is on a file server, completely seperate PC, and it is displaying all the ubuntu installation files. Right.......

So Windows 8 thinks a partitioned drive is now a random network drive? Probably why it can't boot to it?

Can I easily install Windows AFTER ubuntu? If I can then I will do that.

Cheers

---

### Post by raja.genupula on 2011-10-27
> **faz. said:**
> Got a dev preview of W8 and trying to run this as a dual (or more) boot with Ubuntu 11.10. Installed W8 first, then attempted to install ubuntu from the disc but it won't appear as a dual boot. Just starts straight into Windows 8.

So I try it within Windows 8, run it inside, and it does it's thing, restarts a few times, says it is done, shuts down and I get a boot menu, but it only has one item on it; Windows 8 Developer Preview.

odd.

So I boot into W8, have a look on my drives and the partition I created for Ubuntu has gone. Next thing I click onto my shared network drive which is on a file server, completely seperate PC, and it is displaying all the ubuntu installation files. Right.......

So Windows 8 thinks a partitioned drive is now a random network drive? Probably why it can't boot to it?

Can I easily install Windows AFTER ubuntu? If I can then I will do that.

Cheers

yes you can get ubuntu after installing windows  ...look at my signature for grub recovery that gonna help you.But Ubuntu have every stuff that Windows have and doing more than that ...so my suggestion keep ubuntu and close windows. Have a nice day,

---

### Post by oldfred on 2011-10-27
Windows 7 has never seen ext3 or ext4 partitions on the same system. Samba converts that when using networks.

After a Windows install you always have to reinstall grub2's boot loader to the MBR. Windows never boots Ubuntu (wubi exception), but grub boots Windows.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 with grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - also METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by Mark Phelps on 2011-10-27
You do realize that the Win8 DP is essentially the same level of maturity as an Alpha version of Ubuntu, right?

And, you do know that when the Beta comes out (probably in a few weeks, since it's already been leaked), and if it is PUBLIC (like the DP) you will have to remove your Win8 DP install and start all over again, right?

Just mentioning this so that you know that everything you're doing to get this working now -- will have to be done again when (if) the public Beta of Win8 is available.

---

### Post by faz. on 2011-10-28
I totally realise this, just wanted to poke some feelers out there to see if it was possible. I also just found a thread on my phone which links to [http://boyans.my3gb.com/](http://boyans.my3gb.com/) where you can download a tool to edit all the stuff, I guess this would work however... surprise surprise... windows dp wont allow me to run it.

Think I will do what you said and start with a working operating system, then try and install another on top of that.

Cheers all.

---

### Post by oscarivera9 on 2011-10-28
I also have a W8 DP which I installed with Fedora 15 through Virtual Box  specifically to see if there were any Grub problems and I personally  didn't have any.  Then again, it wasn't a REAL installation, it was  through Virtual Box, but then again, that's why we have that type of  software, right?

 > After a Windows install you always have to reinstall grub2's boot loader  to the MBR. Windows never boots Ubuntu (wubi exception), but grub boots  Windows.I installed W8 first, then Fedora 15 second and installed Grub to sda,  not sda1 or sda2 but just plain old sda, which if I understand correctly  means that it installs it to the MBR.  I was still able to boot to both  systems except for the fact that W8 would only boot if I selected the  W8 Recovery Environment.

---

### Post by oldfred on 2011-10-28
When you installed Windows 8 was the boot flag on the recovery environment. Windows always combines boots into one active (boot flag) partition.

---

