---
title: "Ubuntu-Mepis dualboot, grub issues"
date: 2006-05-04
forum: Installation &amp; Upgrades
---

### Post by cjm5229 on 2006-05-04
I finally got my wife off WinXP, couldn't get her to use Ubuntu, Kubuntu, but I got her to use Mepis 6.0. She loves it. However, I don't know much about it. so I want to dualboot Mepis with Ubuntu. I took Windows out of my computer:D  so I could install Mepis. OK, no problem there, but I can not get Grub to load both OS's I can get the Mepis grub to load Mepis but not Ubuntu, the Ubuntu grub will load Ubuntu but not Mepis. The only solutions I have found are to edit grub lst. I have done that with both grubs and neither one works. Does anybody have any idea how to make Ubntu grub recognize Mepis or vice-versa? Ubuntu grub recognized Mepis when Windows was installed.

---

### Post by Jimmey on 2006-05-04
Maybe you edited menu.lst wrongly.

To find out the state of your partition table, use this command:
> sudo fdisk -l

I may be wrong, but I believe that /dev/hda1 is the equivalent of GRUB's hd0,0. So, if your Ubuntu was on /dev/hda1, and Mepis on /dev/hda2, then your menu.lst might look something like:

> 
title	         Ubuntu
root		(hd0,0)
kernel		
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Mepis
root		(hd0, 1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single 
savedefault
boot


Also, you'll want to make sure that the menu.lst in Mepis and Ubuntu match.

---

### Post by cjm5229 on 2006-05-06
Jimmey
Thanks for the reply.  I tried that, neither grub will recognize the other one. For two operating systems that are supposedly working together you would think they could be dual booted on the same computer. I have tried every how-to I could find and nothing works. Guess I will just tell her she's on her own unless she wants to come over to Ubuntu:p. I'm going to put Ubuntu on mine all by it's self. (that's what I really wanted to do anyway):-$ Thanks again,
 Carl

---

### Post by Jimmey on 2006-05-06
I think that the solution is to write Grub to the MBR, and not the boot sector of each partition. To be honest, I don't know how this is done - Unless..

You where to install Mepis first, and Ubuntu second. That way the Ubuntu install would recognize the Mepis installation and make an entry in menu.lst.

By the way, if you were to 

> sudo apt-get install kubuntu-desktop whilst using Ubuntu, or install Kubuntu, then you could use KDE ( Mepis' default window manager ) on Ubuntu; It would look and feel like Mepis.

---

### Post by lha on 2006-05-06
Hi,

Easiest solution is to install Ubuntu's grub to mbr and Mepis' grub to the boot sector of a primary partition or vice versa. Then add

title           The Other Distro
root            (hd0,1)
chainloader     +1

to grub in mbr. (Replace (hd0,1) with relevant partition.) Because both Mepis and Ubuntu will have their own menu.lst, new kernels are automatically available at boot.

---

### Post by cjm5229 on 2006-05-08
Hi, 
Thanks guys, I tried every configuration I could find, including these. Nothing worked. It finally got to where I couldn't install grub at all. Wiped my hard drive again, did a clean install of Ubuntu Dapper Drake Beta 2. Told the Wife she was just going to have to learn to like Kubuntu. Wiped her hard drive, took out Windows and Mepis. Installed Ubuntu DD Beta 2 put in the KDE desktop. Now she likes it better than Mepis or Windows. (Ahhh,  The power  of Ubuntu!!!):) Now we are both happy. And when she screw's it up, I can revert back to Gnome and  I know what to do without battling KDE.   Mepis 6.0 does seem like it is going to be a really nice OS, course that's probably because it's based on Dapper. Why use a copy when you can have the original?:-D Thanks again,
Carl

---

### Post by towsonu2003 on 2006-05-08
I was subscribed to this one hoping you'll find a solution. I'll soon start trying out distros, and would love to hear a solution to such a problem. 

Anyway, I'd file a bug report to either/both of ubuntu and mepis, so they fix this so others can enjoy mepis+ubuntu. 

by the way, you know that when you install ubuntu and sudo apt-get install kubuntu-desktop, you'll ave both ubuntu and kubuntu without dual booting and stuff, right? :)

---

### Post by lha on 2006-05-09
[QUOTE=towsonu2003]I was subscribed to this one hoping you'll find a solution. I'll soon start trying out distros, and would love to hear a solution to such a problem. 

Anyway, I'd file a bug report to either/both of ubuntu and mepis, so they fix this so others can enjoy mepis+ubuntu. 

by the way, you know that when you install ubuntu and sudo apt-get install kubuntu-desktop, you'll ave both ubuntu and kubuntu without dual booting and stuff, right? :)[/QUOTE]
Hi towsonu2003,

The method I described above *does* work, I'm using it to boot Breezy/Dapper(/Windows/Windows). In my opinion, it is easy and flexible way to install multiple distros.

If you want to have four distros (which is the maximum number of distros that can be installed this way), make three primary partitions hda1-hda3 for distros 2,3&4, an extended partition that contains partitions for your primary distro (Ubuntu, of course ;)), common swap and maybe /home or some other way of transfering data between different os's (especially if you have also Windows). Then start with Windows, if you want. Install it to hda1. Continue with Ubuntu. Use the logical partition for /, install grub to mbr.

Finally, you can start installing those other distributions. Start the installer and proceed as normal, but *do not* let installer overwrite mbr. You have to instruct it to install boot loader to the boot sector of the partition you are installing it into. When installer restarts, you'll be presented with Ubuntu's grub menu. Boot Ubuntu and add a chainloader line into grub that loads the other boot loader. Restart, select the new menu entry and watch your new distro boot up. Finish installation and repeat until you run out of empty partitions.

---

### Post by towsonu2003 on 2006-05-09
will try, thanks :)

---

### Post by cjm5229 on 2006-05-11
towsuno2003,
I believe the method Iha described would work, I just couldn't get a boot partition put in with my Ubuntu install. It wanted to make it a primary partition and I already had the max primary's. To get them to change to a logical Partition would have required me to wipe my entire HDD and I didn't really want to do that.

I have dual booted several other Linux OS and never had a problem with Ubuntu's grub not picking them up. I even had Windows, Ubuntu, and Mepis triple booted and Ubuntu's grub found them. but with  just Mepis and Ubuntu neither grub  would detect the other OS.  It is a Mepis problem I believe rather than Ubuntu, because for some reason Mepis Grub will not recognize any other Linux system. Like I finally convinced my wife, Mepis and Ubuntu with the KDE desktop installed, (I don't like KDE so I do put in Ubuntu and then install the KDE desktop) I have it in my computer that way also because I do like some KDE apps and I find that with the KDE desktop installed they run OK in Gnome also. 
Since Mepis is now working with Ubuntu, (Even they recognize a superior product;)) Maybe Mepis will get off their  high horse and  let their  grub work with something other than Windows. 

Anyway have fun playing with other Distro's I know I do, but in the end, when you want a distro that is able to be set up the way You, want it instead of the way someone else wants it, unless you pay more, Ubuntu just works!
Good Luck, Carl

---

