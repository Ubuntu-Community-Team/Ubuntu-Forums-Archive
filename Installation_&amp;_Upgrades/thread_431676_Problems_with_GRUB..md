---
title: "Problems with GRUB."
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by trdlos on 2007-05-03
Good Morning...

Last night, I installed Feisty Fawn on my External WD MyBook USB HDD, but I'm running across a problem.

My Default OS on my Primary Internal Hard Drive, Windows Vista (:( ) will not boot automatically, and an option to boot Vista will only show if my External HDD is attached and powered on, then GRUB will give me the choice to go to either Vista or Ubuntu.

If the External Drive is not attached, an GRUB Error 1 or 2 I believe will show. Is there any way to have Grub Boot into Vista automatically or at least give me the option to boot into Vista if my external drive is not present?

Thanks!

---

### Post by trdlos on 2007-05-03
Any Ideas?

---

### Post by dannyboy79 on 2007-05-03
the problem is that you don't have grub's stage 1 and stage 2 anywhere when you don't have external drive plugged in. it was a bad idea to do it this way and you have 3 choices.

1. you would either need to create a small partition at the begining of your windows drive and install grub there.

2. install grub onto a floppy and boot to that everytime. which then would allow to pick either vista or ubuntu and it wouldn't matter if external drive wasn't there, the option would still be there for ubuntu, it just wouldn't work of course.

3. reinstall windows mbr by using the recovery console by booting using your vista cd, that's done with FIXMBR (i think) so then you will be using ntldr as your boot manager. then you will need to copy the mbr (or is it boot sector) from your external ubuntu install and paste it into the root of your c drive as a file and add a boot option in your boot.ini file  so that ntldr can boot linux.

---

### Post by louieb on 2007-05-03
Unfortunately when you installed Ubuntu on your external drive you also install 99% of GRUB there also. That one of the problems installing on a external drive. You have to have as you found out: the drive needs to be attached to boot to anything on the computer.   
The 1% of GRUB on the hard drive is a 400+ character long chunk of code that points to /boot/grub/stage2  in your Ubuntu install.
Haven't played with VISTA so don't know if it boots the same as XP.  Might try a forum or google/linux search on **fix VISTA boot**.

:lolflag: Well lookie there dannyboy beat me he knowns the problem and he knows the fix.

---

### Post by trdlos on 2007-05-03
Hmmm...So I messed up my first time installing Ubuntu. No Biggie, I was planning on going back to XP anyway.

So really, there would be no way to boot Ubuntu off an External Hard Drive then? Cause I would like it to not reside on the same Internal Hard Drive, due to Storage Constraints.

There's no way to edit GRUB to automatically boot into Windows after a certain period of time? I heard alot about the Menu.lst file and editing this. Any Insight?

---

### Post by confused57 on 2007-05-03
See this guide for reinstalling Vista IPL code to your internal hd mbr:
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

What happened is that grub's IPL code was installed to your internal hard drive mbr...the IPL code looks for your root partition on your external hard drive for grub, which it uses to boot your OS.  With the external hd disconnected, there's no grub for the IPL to connect to in order to boot your computer...therefore you'll need to restore Vista's IPL code to boot your internal hd without the external drive connected.

You'll need to install grub to the external hard drive mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

you would do something like this:
```
sudo grub
find /boot/grub/stage1
```
which would possibly return "root (hd1,0)"
then you would:
```
root (hd1,0)
setup (hd1)
quit
```

Then if your pc is able to boot first to the external hd, you should get a grub menu at boot...if you do, highlight your Ubuntu entry, press "e", change root from (hd1,0) to (hd0,0), then press "b" to boot...this change is temporary, but can be made permanent if it works.

So basically:
1.) You'll need to restore Vista's IPL code to your internal drive to boot without the external drive connected.
2.) Your pc will need to be able to boot first to the external hd, after installing grub to it's mbr.

Another possibility is to restore Vista's IPL code to your internal hd mbr, then download the Super Grub Disk to boot Ubuntu on your external hd:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
if you use SGD, you won't need to install grub to your external hd mbr...but you'd need SGD in order to boot to Ubuntu.

Added:  Here's an excellent tutorial for editing grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

dannyboy79 & louieb beat me to it, got to increase my typing skills.

---

### Post by trdlos on 2007-05-03
Thank you very much for the help. I have a busy night ahead of me.

*Right Click, Print*

---

### Post by louieb on 2007-05-03
> **trdlos said:**
> Hmmm...So I messed up my first time installing Ubuntu. 
Heck no you didn't mess up. You install it to an external drive and it works as long as the drive is attached.  You just ran into the **Law of unintended consequences. **

---

### Post by dannyboy79 on 2007-05-03
> **trdlos said:**
>  Hmmm...So I messed up my first time installing Ubuntu. No Biggie, I was planning on going back to XP anyway. 
You didn't mess up, you merely weren't aware of grub's boot process.

> **trdlos said:**
>  So really, there would be no way to boot Ubuntu off an External Hard Drive then?  
Um, you must not have read any of my solution, you can certainly boot an external hard drive. 

> **trdlos said:**
> There's no way to edit GRUB to automatically boot into Windows after a certain period of time? I heard alot about the Menu.lst file and editing this. Any Insight? 
Nope, it's because as the other's have pointed out, grub's stage 1 and stage 2 files are no where to be found, you installed only a portion of grub into your internal hard drives mbr and left all of it within the external drive

so, either use NTLDR to boot into either OS 

OR

use Super Grub Disc or make your own floppy to boot into your OS's

OR

make a boot partition at the begining of your drive (only has to be like 100mb) and install grub there.


OR you could cheat and do it the super cheezy way, first do like confussed said above and install grub into the mbr of your External Drive, then also fix Vista's mbr using FIXMBR. 

most new computers will have a menu for the device to boot to if you tap a Function Key, this will bring up a list of devices like your hard drive, your cdrom, hopefully your usb drive if your bios supports it etc etc, then which ever OS you want to boot into you chose that device and that's it. chosing external usb will get ya to grub then Ubuntu OR Vista and chosing your internal Hard drive will get ya to Vista. talk about a cheezy fix but it would work. you just need to make sure your bios can boot to usb devices, and that you have a function key that will bring up boot menu.

Let us know what ya do so other's can learn also.

---

### Post by psusi on 2007-05-03
It sounds like you want to just boot windows normally from the internal disk, and only boot linux when you connect the external usb drive.  In that case you need to use the windows recovery console FIXMBR command to put the windows boot loader back on the hard disk, then install grub to the external disk only, and set your bios to boot from there when it is plugged in.

---

### Post by dannyboy79 on 2007-05-03
> **psusi said:**
> It sounds like you want to just boot windows normally from the internal disk, and only boot linux when you connect the external usb drive.  In that case you need to use the windows recovery console FIXMBR command to put the windows boot loader back on the hard disk, then install grub to the external disk only, and set your bios to boot from there when it is plugged in.

bingo

---

### Post by trdlos on 2007-05-03
Thanks for all your Help Guys! Ubuntu Support is Awesome! Thanks!

---

### Post by dannyboy79 on 2007-05-03
> **trdlos said:**
> Thanks for all your Help Guys! Ubuntu Support is Awesome! Thanks!

well what ya gonna do? other users will be curious about this also, that's the benefit of forums, almost every single thing a person wants to do, most likely some1 has already tried it and we just hope that they documented it in a forum.

---

### Post by trdlos on 2007-05-03
Well, I'll have to wait till tonight to access the machine with the issues. But I plan to do what someone suggested earlier, using the NTLDR to boot into Ubuntu, placing GRUBs entire contents onto my External Drive and setting my External Drive to the first Device to boot if present. It seems like the easier way to fix this. Updates tomorrow.

---

### Post by dannyboy79 on 2007-05-04
> **trdlos said:**
> Well, I'll have to wait till tonight to access the machine with the issues. But I plan to do what someone suggested earlier, using the NTLDR to boot into Ubuntu, placing GRUBs entire contents onto my External Drive and setting my External Drive to the first Device to boot if present. It seems like the easier way to fix this. Updates tomorrow.

sounds great, this should work well for ya.

---

### Post by sandman55 on 2007-05-04
How would he do this after he has repaired his MBR I would say unplug internal HDD so that Ubuntu completely installs on removable HDD plug in internal HDD then edit Bios for the removable HDD to be first. Any comments?

---

### Post by dannyboy79 on 2007-05-04
> **sandman55 said:**
> How would he do this after he has repaired his MBR I would say unplug internal HDD so that Ubuntu completely installs on removable HDD plug in internal HDD then edit Bios for the removable HDD to be first. Any comments?

he wouldn't have to remove his internal drive. He would merely install grub into his external drive's mbr. this is done thru the grub command line

sudo grub

find /boot/grub/stage2

this will return something like (hd1,0) note that this should be his external drive.

then he would do

root (hd1,0)

setup (hd1)

exit

then yes, he would change his bios so that first boot device is the removable device.

---

### Post by sandman55 on 2007-05-05
Thanks dannyboy79

---

### Post by dannyboy79 on 2007-05-07
glad I could help.

---

