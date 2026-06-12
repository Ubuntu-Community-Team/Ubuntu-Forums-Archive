---
title: "2 Ubuntu Installs + 1 Windows Install, Grub Problem"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by Grogger on 2007-01-23
I have a problem with knowing how to install grub to my new ubuntu installation.  I suspect there is an easy way to do this.  I just haven't found it yet.  

I first have windows xp on a 160gb sata.  Then I installed ubuntu on an older 10gb ide with the other hd still connected.  This worked great once I found how to install my wireless network card.  I liked ubuntu so much I decided to get a new hard drive for it to have a clean and wide open space for itself.  So with both the first two hard drives still connected I installed ubuntu dapper again on the new 120gb sata.  This also worked fine until I tried to set this hard drive as the first boot device on my bios boot menu.  I received an error on booting to the new hard drive.  I don't remember what the error was, but it simply seemed to not be able to read the boot commands for loading into ubuntu.  

My problem:  I believe grub is running from the 10gb ide and not the 120gb sata that I want to run as primary for ubuntu.  I really would like to reformat the 10gb ide with my first ubuntu install and use it for playing with other linux installs.  But I don't think I can remove this ide drive until I can get grub loaded and set to run on the new 120gb hard drive.  

Can someone point me in the direction for how to get grub up and running on my new ubuntu dapper so that it isn't dependent on ubuntu install on the old hard drive?  

Of course that is without reinstalling ubuntu on the new hard drive with the old hard drive disconnected (yes that is a really lame old trick for fixing problems in windows, "hey, just reinstall windows, that'll solve most problems ; windows has a short half-life anyway."  It helped make up for my lack of knowledge for using windows administrative tools.  It'd be nice to actually learn some of those tools in ubuntu.)  :D    

Thanks.

Oh yeah, my pc specs:  

Intel D915GEVL Mobo
3.0 Ghz P4 Proc
1 Gb Ram
160 Gb Sata HD
120 Gb Sata HD
10 Gb Ide HD
ATI X-700 Pro video card
Plextor DVD Burner

---

### Post by nimphelos on 2007-01-23
There is something odd about GRUB. If you check grub.conf you can see that GRUB know hard drives as hd0, hd1, .... and for sata drives and USB disks sd0, sd1.... etc.

Now I think you problem here is changing drive locations on BIOS confuse GRUB. When you install your Ubuntu, GRUB knows first boot device as sd0 and second boot device sd1. But when you change your device locations on BIOS, at boot time GRUB looks for sd0 but it can't find what is expected. 

So if you want to make your sata primary. Make 120 gb sata primary.  Install ubuntu on 120GB sata and install GRUB on it's MBR. Ubuntu will scan all your Harddrives for Operating Systems and it will add them to GRUB menu.If Ubuntu can't find operating systems when installing you can add them after installing.

And I hope it woll work fine ;)

---

### Post by scrooge_74 on 2007-01-23
If you go back to the point where you made changes to the bios you only needed to tell GRUB what was going to start by default.

You can check this thread [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)
  or this one [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by confused57 on 2007-01-23
I'm guessing that when you installed Dapper to your new 120Gb SATA that it installed the new Dapper install's grub to the mbr of your 10 Gb IDE drive.  If you're not going to remove your IDE drive, I would leave it as your first boot device, since grub on it's mbr is pointing to your root partition on your SATA drive.

If somehow your mbr gets overwritten when you're installing any other Linux OS to your IDE drive, you can reinstall your Dapper grub to the mbr with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

A good way to test & boot other Linux OS is to install grub to the root partition of the OS, then add an entry to boot to your Dapper /boot/grub/menu.lst using chainloading, e.g.

title   Linux OS
rootnoverify (hd0,0)
chainloader +1

As nimphelos pointed out, changing the boot order will change how grub recognizes the order of your hard drives(hd0, hd1, hd2) & you'd need to manually make changes to your grub entries in order to boot from the SATA drive.

---

### Post by Grogger on 2007-01-23
Thanks for the help!  

I'm not totally sure that I want to keep the 10gb (hd0) with the older ubuntu install connected in my computer.  I also worry just a little if the drive fails or becomes corrupted or something because it is an older drive.  

So if I would like to remove the 10gb ide and want grub to boot from the 120 gb sata separate from the 10gb drive, then I would need to install grub to the mbr on the 120gb, mapped (sd0) on ubuntu, and manually modify the /boot/grub/menu.lst  file entry for ubuntu on (sd0) to choose this hard drive to be the primary boot hard drive?

Or do the manual changes need to be done on this file?:
/boot/grub/device.map whose text entries read: 

(hd0)	/dev/hda
(hd1)	/dev/sda
(hd2)	/dev/sdb    


I'm starting to feel like I understand what I can do to make this happen.  :eek:

---

### Post by confused57 on 2007-01-23
> **Grogger said:**
> Thanks for the help!  

I'm not totally sure that I want to keep the 10gb (hd0) with the older ubuntu install connected in my computer.  I also worry just a little if the drive fails or becomes corrupted or something because it is an older drive.  

So if I would like to remove the 10gb ide and want grub to boot from the 120 gb sata separate from the 10gb drive, then I would need to install grub to the mbr on the 120gb, mapped (sd0) on ubuntu, and manually modify the /boot/grub/menu.lst  file entry for ubuntu on (sd0) to choose this hard drive to be the primary boot hard drive?

Or do the manual changes need to be done on this file?:
/boot/grub/device.map whose text entries read: 

(hd0)	/dev/hda
(hd1)	/dev/sda
(hd2)	/dev/sdb    


I'm starting to feel like I understand what I can do to make this happen.  :eek:

If you set your SATA drive with Ubuntu to boot first, it will be designated (hd0) in grub(grub doesn't differentiate hda from sda) & if your Windows drive is set as the second boot device it "should" be (hd1).
What you could try is set your Ubuntu SATA drive as the first boot hard drive in bios, then boot up with the desktop live cd & install grub to the mbr of your SATA drive.
   After installing grub to the SATA mbr, reboot, when the grub menu is displayed, highlight the entry to boot Ubuntu, press "e" for edit, then change the root from (hd2,1) to (hd0,1) & try to boot...if Ubuntu successfully boots, you can make it permanent in your /boot/grub/menu.lst.
   Your current /boot/grub/menu.lst entry to boot Windows probably has these lines:
root   (hd2,0)
map   (hd0) (hd2)
map   (hd2) (hd0)

you'll probably need to change it to(which I see it already is):
root   (hd1,0)
map   (hd0) (hd1)
map   (hd1) (hd0)

I can't guarantee any of this will work, but it'll give you some ideas.  
Here's an excellent site explaining how grub works:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

You may want to wait for  further replies & suggestions before proceeding...good luck.

Add:  Here's how I have my system set up...may be some info here you can use(i.e. editing /boot/grub/menu.lst):
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Some posters have reported having problems installing grub to their SATA mbr...just thought I'd mention it, you may not have this problem.

---

### Post by Grogger on 2007-01-23
> If you set your SATA drive with Ubuntu to boot first, it will be designated (hd0) in grub(grub doesn't differentiate hda from sda) & if your Windows drive is set as the second boot device it "should" be (hd1).
What you could try is set your Ubuntu SATA drive as the first boot hard drive in bios, then boot up with the desktop live cd & install grub to the mbr of your SATA drive.
After installing grub to the SATA mbr, reboot, when the grub menu is displayed, highlight the entry to boot Ubuntu, press "e" for edit, then change the root from (hd1,0) to (hd0,0) & try to boot...if Ubuntu successfully boots, you can make it permanent in your /boot/grub/menu.lst.
Your current /boot/grub/menu.lst entry to boot Windows probably has these lines:
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)

you'll probably need to change it to:
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)

I can't guarantee any of this will work, but it'll give you some ideas.
Here's an excellent site explaining how grub works:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

You may want to wait for further replies & suggestions before proceeding...good luck.


Thanks for the suggestion.  I've attached a copy of my /boot/grub/menu.1st  If you'd like to check it out.  

It looks like the last entry for my windows xp installation is already listed as you suggest it should be changed to for the 'root, map, map.'  

 I'll see what other posts come up and maybe try something later. ;)

---

### Post by confused57 on 2007-01-23
Just looked over your /boot/grub/menu.lst, I assume your boot order is hda, sda(Windows),sdb(Ubuntu)...if & when you try to install grub to the Ubuntu SATA mbr, you might want to have the IDE drive connected to ensure that you install grub to the Ubuntu SATA drive mbr...your Windows entry should be fine as is.

Your new boot order should probably be sdb(Ubuntu), sda(Windows), hda(if you leave it connected).  Since your current Ubuntu root in grub is (hd2,1), you'd need (hd0,1).

Might be wise to wait for other suggestions, there's probably an easier way.

Add:  You might want to try this...leave your system set up as it is now, all hard drives connected in your current boot order...boot up the live cd, & install grub to the mbr of the Ubuntu SATA drive:
```
sudo grub
```
this will give you a grub prompt, enter:
```
find /boot/grub/stage1
```
you should get root (hd0,0) and root (hd2,1), enter:
```
root (hd2,1)
```
then
```
setup (hd2)
```
to exit grub prompt:
```
quit
```

Your OS should still boot OK with your current setup to boot first to hda...go into bios and change your Ubuntu SATA to be the first boot device.  You should get a grub menu, as I mentioned before, highlight your Ubuntu entry, press "e" for edit, change the root from (hd2,1) to (hd0,1) & try to boot...this wil let you know that you can boot first to the Ubuntu SATA drive and bootup Ubuntu without affecting your current setup.

---

### Post by Grogger on 2007-01-23
Thank you much.  I'll give this a shot in the morning.  ;)

---

### Post by Grogger on 2007-01-27
> **confused57 said:**
> Just looked over your /boot/grub/menu.lst, I assume your boot order is hda, sda(Windows),sdb(Ubuntu)...if & when you try to install grub to the Ubuntu SATA mbr, you might want to have the IDE drive connected to ensure that you install grub to the Ubuntu SATA drive mbr...your Windows entry should be fine as is.

Your new boot order should probably be sdb(Ubuntu), sda(Windows), hda(if you leave it connected).  Since your current Ubuntu root in grub is (hd2,1), you'd need (hd0,1).

Might be wise to wait for other suggestions, there's probably an easier way.

Add:  You might want to try this...leave your system set up as it is now, all hard drives connected in your current boot order...boot up the live cd, & install grub to the mbr of the Ubuntu SATA drive:
```
sudo grub
```
this will give you a grub prompt, enter:
```
find /boot/grub/stage1
```
you should get root (hd0,0) and root (hd2,1), enter:
```
root (hd2,1)
```
then
```
setup (hd2)
```
to exit grub prompt:
```
quit
```

Your OS should still boot OK with your current setup to boot first to hda...go into bios and change your Ubuntu SATA to be the first boot device.  You should get a grub menu, as I mentioned before, highlight your Ubuntu entry, press "e" for edit, change the root from (hd2,1) to (hd0,1) & try to boot...this wil let you know that you can boot first to the Ubuntu SATA drive and bootup Ubuntu without affecting your current setup.

I did everything as you suggested above in the "add:..." portion above.  This worked great!  Now I'm not sure how to proceed to change the ubuntu root from (hd2,1) to (hd0,1) permanently.  

Do I need to use a text editor like nano to edit the /boot/grub/menu.lst file? Then change the root names?  

Thanks.

---

### Post by confused57 on 2007-01-27
I'm amazed it worked, but I'm glad it did...this link may give you an idea of how to edit your /boot/grub/menu.lst:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Yes, you could also use:
```
sudo nano /boot/grub/menu.lst
```

Be sure to create a backup first:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
```

You can restore by:
```
sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst
```

---

### Post by Grogger on 2007-01-27
Yeah, I'm really glad that it worked too!  I also made the changes to my grub boot file using the gedit commands you gave on the dualboot page.  It worked great when I booted up to Ubuntu.  Many thanks for your help!!  I'm finding that ubuntu is working faster than windows now that I have it on an sata drive.  Eventually maybe I'll be able to use all ubuntu and let go of windoze.  :D

---

### Post by Grogger on 2007-01-27
Well things work somewhat.  I can boot with the sata hd with ubuntu as first boot device in my bios, but I tested doing that with the ide hda unplugged.  That didn't work though.  It errored out because it couldn't detect the hda to mount it during booting of the various options in loading the kernel.  So I'm not exactly sure why it still requires something from the hda to boot.

---

### Post by confused57 on 2007-01-27
> **Grogger said:**
> Well things work somewhat.  I can boot with the sata hd with ubuntu as first boot device in my bios, but I tested doing that with the ide hda unplugged.  That didn't work though.  It errored out because it couldn't detect the hda to mount it during booting of the various options in loading the kernel.  So I'm not exactly sure why it still requires something from the hda to boot.

You might need to comment out the entry to mount hda1 in your SATA drive's /etc/fstab file that would prevent hda from being mounted at startup.  Does the error mention something about pressing ctrl+D to continue when you're booting Ubuntu on your SATA with the hda disconnected?
You might want to boot Ubuntu from the SATA drive, open a terminal, enter:
```
cat /etc/fstab
```

there's probably a line to automatically mount hda1 at startup.

To edit the file:
```
sudo cp /etc/fstab /etc/fstab_backup
```
to make a backup, then
```
gksudo gedit /etc/fstab
```
place a # in front of the line to mount your hda partition

If you want, just post the output of cat /etc/fstab first & see if that is the case.

---

### Post by Grogger on 2007-01-27
Here's my printout for cat /etc/fstab:

grogger@Grog:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda5       none            swap    sw              0       0
/dev/sdb1       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
grogger@Grog:~$


I did remember seeing something about pushing a button to continue for boot up, but whatever the button was it didn't work.  Commenting out hda sounds like it might just work, since it was the inability to mount hda that seemed to cause the error on booting.

---

### Post by Grogger on 2007-01-27
This might be a little clearer log of my fstab file.

---

### Post by confused57 on 2007-01-27
> **Grogger said:**
> Here's my printout for cat /etc/fstab:

grogger@Grog:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda5       none            swap    sw              0       0
/dev/sdb1       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
grogger@Grog:~$


I did remember seeing something about pushing a button to continue for boot up, but whatever the button was it didn't work.  Commenting out hda sounds like it might just work, since it was the inability to mount hda that seemed to cause the error on booting.

I'm in Windows right now, so I can't open your .odt  file, but I believe all you need to do is put a number in front of the lines:
/dev/hda1
/dev/hda5

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
#/dev/hda1       /media/hda1     ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
#/dev/hda5       none            swap    sw              0       0
/dev/sdb1       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Grogger on 2007-01-27
This worked to make a # before the dev/hda1 and dev/hd5.  

The 10gb doesn't need to be attached now to boot into my sata ubuntu install.  Woohoo!

---

### Post by confused57 on 2007-01-27
> **Grogger said:**
> This worked to make a # before the dev/hda1 and dev/hd5.  

The 10gb doesn't need to be attached now to boot into my sata ubuntu install.  Woohoo!

Great, glad it worked.  Commenting (placing a # in front of a line), means that Linux doesn't
read nor execute that line.  You'll be helping in the forum before you know it.

---

### Post by Grogger on 2007-01-27
lol, I suppose if I learn a few more things I could help out a couple people.  ;)  

Thanks for your help.

---

