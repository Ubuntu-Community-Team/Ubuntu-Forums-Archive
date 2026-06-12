---
title: "Gutsy won't boot."
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by MikeReiner on 2007-10-18
Installed fine, won't boot.
```

Starting up ...
Loading, please wait...
            Check root= bootarg cat /proc/cmdline
            or missing modules, devices: cat /proc/modules ls /ev
ALERT! /dev/disk/by-uuid/5e2e4a8f-c90b-42a9-af3c-88cdd74bc52e does not exist. Dropping to a shell!

takes me to alt+F8 to show this:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-In Shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_

```

I thought that maybe the iso I downloaded was bad, or that I burned it improperly.. so I re downloaded it, burned it at a slower speed, and I got the same result.

Hardware:
AMD64 X2 4200+ Toledo Dual Core
2Gigs Corsair Ram
MSI K8N Neo4-F nForce 4 motherboard

Ubuntu is installed on an 80gb Hard drive.
50 gigs to ubuntu, 25 to Windows XP, and 2 gigs for the swap file.

Grub is working fine. I can boot into XP perfectly.

This left me sad after hearing all the hype and great things to come with gutsy gibbon..

---

### Post by MikeReiner on 2007-10-18
bump.

Ok come on, somebody has to have an idea whats going on here.
This is getting aggravating. Everybody seems to only have that 'stuck at 82%' issue and nothing else. I can't even get the bloody thing to boot once it finishes installing.

It's got a tiny little sliver on the progress meter for a solid 5 minutes, then displays the error mentioned above.

---

### Post by tommcd on 2007-10-18
So gutsy installed ok, you get the grub menu, you can boot XP, but you get that error when booting gutsy, right??
I think it's those darned UUIDs. Try booting to recovery mode and comment out the UUID part and set up the grub entry for gutsy like:
kernel 2.6.xxx ro root=/dev/sdaxxx
In other words, set up the grub entry like it used to be before the UUIDs came along. Just back up the menu.lst first to be safe.

---

### Post by MikeReiner on 2007-10-19
I started recovery mode, and I got the same error. I did not see anything about "UUID"
A large list of text is on the screen, and I dont' know how to scroll back up to read anything it might have gone through that I didn't catch.

I'm not familiar with editing grub, you'll need to give me a little bit more information. Such as where I find this menu.lst

---

### Post by DavidTangye on 2007-10-19
It is essential that you checksum your download. Eg
```
md5sum ubuntu-xxx-iso|diff ubuntu-xxx-iso.md5 -
```should give an empty result. If not, you have been burning and using a dud iso.

---

### Post by MikeReiner on 2007-10-19
I tried two different ISOs, turns out both are fine.

---

### Post by tommcd on 2007-10-19
> **MikeReiner said:**
> I started recovery mode, and I got the same error. I did not see anything about "UUID"
A large list of text is on the screen, and I dont' know how to scroll back up to read anything it might have gone through that I didn't catch.

I'm not familiar with editing grub, you'll need to give me a little bit more information. Such as where I find this menu.lst

Boot up the gutsy live CD, then

sudo mkdir /mnt/gutsy
sudo mount /dev/sdaX /mnt/gutsy ##Replace the X with your gutsy partition number.
sudo cp /mnt/gutsy/boot/grub/menu.lst /mnt/gutsy/boot/grub/menu.lst.bak
sudo gedit /mnt/gutsy/boot/grub/menu.lst

Scroll down to ##End Default Options## part. Your first gutsy entry will look like:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=215bbf5c-2944-4fae-ba82-8e07527d731c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```
Remove the part that looks like: "UUID=215bbf5c-2944-4fae-ba82-8e07527d731c" and add the partition that your gutsy is on after root= so the kernel line looks like:
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda2 ro

Your /dev/sdaX will of course be the partition gutsy is on. If XP is first and ubuntu is 2nd it will be sda2 like mine.
Save the file and try to boot gutsy. If it don;t work you can always replace the original menu.lst by doing:
"sudo cp /boot/grub/menu.lst.bak /boot/grub/menu.lst

Hope this helps. I've had problems when booting Zenwalk from Ubuntu's grub due to those UUIDs and this is how I fixed it.

---

### Post by MikeReiner on 2007-10-19
I'm afraid that didn't work. Thanks for the effort though.

Help me understand something here, is it *grub* that is broken here, or gutsy?

Could I use a different boot loader if grub is the problem?

---

### Post by DavidTangye on 2007-10-19
> **MikeReiner said:**
> Help me understand something here, is it *grub* that is broken here, or gutsy?It looks like gutsy broke grub.
Try this
```
cat /proc/cmdline
```I get> root=UUID=fa7d610b-d443-4a22-ade3-b0bc088e81d2 ro quiet splashSo then I -
```
grep fa7d610b-d443-4a22-ade3-b0bc088e81d2 /etc/fstab
```I get > UUID=fa7d610b-d443-4a22-ade3-b0bc088e81d2 /               ext3    defaults,errors=remount-ro 0       1which proves that my bootup is looking for the correct partition to mount at /.

What happens in your case?

---

### Post by tommcd on 2007-10-19
MikeR, 
perhaps you could try reinstalling grub from the live CD. At this point it can't hurt anything:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

DavidT,
that's a cool trick you posted! I didn't know about that.

---

### Post by my_linux on 2007-10-19
H,

I have got the same problem with my Ubuntu 7.10 (Alternate CD) install. In my case the stall occurs after an IDE driver is loaded, I guess for the optical drive as the hard disk is sata.

There are three partitions with only Ubuntu installed. Ubuntu 7.10 RC had no problems booting on this same computer.

Does anyone know if the kernel was changed or what changes were made from RC to release 7.10? Is there a bug reported in launchpad?

I have tried all the possible changes listed here and on other forums not been able to boot Ubuntu 7.10 release :(

---

### Post by Desd on 2007-10-19
Hi David T and others,

I got an error saying that "Mounting local filesystems" Failed to acces '/dev/disk/byuuid/404CE7934CE781D0': File or directory does not exist. 

So, I tried your grep trick and no message was printed. How do I correct this not / wrongly mounted file system?

Thanks in advance!

---

### Post by tommcd on 2007-10-19
To everyone who gets the < Failed to acces '/dev/disk/byuuid/404CE7934CE781D0'> error, try to boot by following post #4 of this thread:
[http://ubuntuforums.org/showthread.php?t=393379](http://ubuntuforums.org/showthread.php?t=393379)
with a slight modification. Just hit "e" when the grub menu comes up and start from "When you get to the grub menu...." in that post.This will not make any permanent alterations to menu.lst so it is safe to try. Either that or reinstall grub as per the link in my last post.  Do any of you have more than one hard drive? If so then grub could be pointing to the wrong drive or something. Otherwise I don't know.

---

### Post by Simeonus on 2007-10-20
Hello Ubuntu-dudes!

I had the same problem. However, I'm writing this msg in Ubuntu.
How did I fix it?

In Grub I edited the line starting with the word kernel.
The line starting with kernel ends with "splash"
So I removed the splash. Now I saw what was wrong.
It gave me a couple of errors and "Maybe you should add irqpoll"
When I added that word to the kernel line, it booted.

Haha this is the first day I use Ubuntu. :-D

Hope it works for you too.

Cheers,
Me

---

