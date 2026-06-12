---
title: "Went from 8.04 to 9.10 no menu.lst?!?  Need help with multi boot!!!"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by markjs on 2009-12-29
Oh NO!  I can't figure out how to set up my other hard drives with the other OSs!  I was so proud to have figured out how to put my windows OSs into menu.lst in 8.04, but in 9.10 everything is different and I am COMPLETELY lost!

I installed 9.10 with only it's hard drive plugged in so as to not mess any of the other boot sectors up.  See I have Win7 on one drive, OSX86 10.5.7 (Hackintosh) on another and XP and Vista on still one more.  It was quite easy to manage with menu.lst in 8.04.  I need to set them all up in grub to boot but I want all of them able to boot on their own if I remove all the others.  I really need help, because  as it stands I have to switch boot drives in the BIOS which is a monumental pain in the a**!

---

### Post by taurus on 2009-12-29
9.10 is using GRUB 2 now so there is no /boot/grub/menu.lst.  Instead, there are a bunch of files so here is a link that you want to look at.

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by bpalone on 2009-12-29
It is the NEW GRUB, so things are considerably different.  Do a search here for Grub 2 and I am sure you will get a valid answer.  I am still using the old version, but have seen some things on the new version.  It seems that there is new command to have it check for other OSes and to set it up for you.  I can't remember what it is, but a search should find it.

---

### Post by oldfred on 2009-12-29
grub2 is very good at finding other operating systems. But if you did not have you other hard drives plugged in your device.map may only show the one drive not all the drives.

Normally to update:
sudo update-grub

typical two drive
/boot/grub/device.map
(hd0)    /dev/sda
(hd1)    /dev/sdb

Full update and reinstall of grub to drive 
sudo dpkg-reconfigure grub-pc

reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc

Comment by a user who did  not want a MBR overwritten:
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/apt/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

---

### Post by Darkz_Soul on 2009-12-29
Yeah the sudo update-grub basically takes care of everything... there are more manual ways but they do require more time. and can break grub if not done carefully so i would stick to update-grub and for the most part it will work

---

### Post by markjs on 2009-12-30
Oh this is an absolute NIGHTMARE IMHO.  I wanted simple, is there any way to keep 9.10 but uninstall grub 2 and go back to the old grub?

---

### Post by markjs on 2009-12-30
Somehow simplifying things by making them much more complex seems to defeat the purpose....

---

### Post by markjs on 2009-12-30
Well I've tried to fix it but all I get is headaches.  No matter what I still have to manually switch boot drives in the BIOS so I guess I'll just go back to just using Windoze, rather than trying to complicate my life with this ********.  They had something that worked well so they fixed it, and now it's crap!

Everything is always geared towards folks with one hard drive and multiple partitions (which has always seemed to me to be an incredibly stupid way to do things and just asking for trouble) and it was hard for me to find adequate information on how to get that to work with grub 1 and impossible for grub 2 which is garbage in my opinion.  The only way I see of making this work is to let grub go on to all the hard drives which is just exactly what I WILL NOT allow it to do, so back to Windoze because at least it and EasyBCD work unlike this bullcrap.

It's a shame because I really liked grub 1 and 8.04, but I am not going backwards, so I guess until they fix this or there is better info, then Ubuntu 9.10 just isn't worth bothering with for me.....

I suppose I can just wipe this drive and format it NTFS and use it for storage....

Thanks a lot developers for fixing stuff that wasn't broken!

---

### Post by markjs on 2009-12-30
Well I did just look at going back to old grub and that looks to be an incredible monumental nightmare as well.  When I did all this grub crap it found my OS X and Win 7 but did not add entries for them, just boots to Ubuntu only, and I still have to manually reset the BIOS to boot anything else.  I have done a lot of work just to get 8.04 working how I liked it, and I am just not willing to risk having to reinstall all of my OSs because they wrecked grub and 9.10 with it, so I am going to re-boot and reformat this drive right now.  Perhaps in a year or two this issue will be fixed and I will re-visit it but as of now I haven't the time nor will to bash my head against the wall and spend many hours trying to fix something that should not have even been broken, but has none the less.

](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by markjs on 2009-12-30
I'll still be checking if anyone has any solutions, but because of past experience I am EXTREMELY leary of doing anything thta might potentially alter my Windows install which is unfortunately mission critical.

---

### Post by markjs on 2009-12-30
OK, just because I really wanted Ubuntu 9.10 I took the risk and re-installed it with all the hard drives connected.  It seems to have worked OK, but it was a good catch the at the end about installing the boot loader that I clicked on advanced, or it would have screwed with my big (750GB) drive for windoze 7 bloatware.  That is precisely what I had feared!  I already had it set with the 320GB I am using now to be the boot drive in BIOS, so why does Ubuntu insist on intruding into the other hard drives unless you specifically prevent it?

---

### Post by markjs on 2009-12-30
But mind you I said ***seems*** to have worked.  I have yet to try to boot into anything else.  My fingers are crossed!

---

### Post by markjs on 2009-12-30
OK, it worked fine, BUT when I tried to update all the updates, one was for Grub and it once again wanted to write itself to my 7 drive!  This time though I wasn't 100% clear, but I told it to just install it where it is now and still things are fine.  I just do not understand why it wants to take over my other drives and OSs.

I also need to know where do I change variables. like default OS and time before it automatically boots the default?

---

### Post by oldfred on 2009-12-30
Lots of info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) 


See my post #4 on how to not have grub install to the wrong drive.

Most settings are here:
/etc/default/grub

You can choose by number or:
If you refer to Windows by its number, you will have to edit on every update. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find windows entry in this and copy to
gedit /boot/grub/grub.cfg
and copy here
gksudo gedit /etc/default/grub
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"

---

### Post by joshedmonds on 2009-12-31
Although this will probably result in severe karmic reprisals (geddit?) from Grub2 lovers, you can quite easily install grub with 9.10. It is in the repos and is probably best installed with apt-get install grub so you can see exactly what is happening.

See this thread from yesterday:

[http://ubuntuforums.org/showthread.php?t=1367875&page=2]("http://ubuntuforums.org/showthread.php?t=1367875&page=2")

The only issues with the install were that I could not use the find command in grub, as it had not yet installed anything (something I was used to from re-installing) and it did not create a default menu.lst

---

