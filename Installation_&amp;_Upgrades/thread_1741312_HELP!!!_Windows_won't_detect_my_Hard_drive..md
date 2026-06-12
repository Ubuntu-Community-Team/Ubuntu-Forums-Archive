---
title: "HELP!!! Windows won't detect my Hard drive."
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by JOSEISCOOL on 2011-04-28
Okay so I made partitioned my hard drive using Gparted Live CD and I now have a 55GIG Partition that I made for Windows Seven, now when I load up windows Seven installation it won't detect my new partition and if it does(I managed to go back into gparted and mess with it a bit a few times) if it does detect the partition then it still can't use or detect my drive because it says that it isn't the proper format(even though, I formatted it to ntfs using gparted) anyone know how to fix this? I need to install windows vista or windows seven. Thanks for your time. BTW, the Linux distro I'm using currently is Ubuntu 11.04 Beta.

By the way, I don't want to delete my Ubuntu Partition because I need it, I only want Windows for a few programs that won't run in wine.

It's a laptop, I didn't open anything inside of it o.o.

---

### Post by wilee-nilee on 2011-04-28
> **JOSEISCOOL said:**
> Okay so I made partitioned my hard drive using Gparted Live CD and I now have a 55GIG Partition that I made for Windows Seven, now when I load up windows Seven installation it won't detect my new partition and if it does(I managed to go back into gparted and mess with it a bit a few times) if it does detect the partition then it still can't use or detect my drive because it says that it isn't the proper format(even though, I formatted it to ntfs using gparted) anyone know how to fix this? I need to install windows vista or windows seven. Thanks for your time. BTW, the Linux distro I'm using currently is Ubuntu 11.04 Beta.

By the way, I don't want to delete my Ubuntu Partition because I need it, I only want Windows for a few programs that won't run in wine.

It's a laptop, I didn't open anything inside of it o.o.

In gparted make sure you right click that ntfs then manage flags then boot, it needs a boot flag to work.

Otherwise post a screen shot of gparted looking at the HD.

You will also have to reload the grub bootloader to the mbr if you want grub as the boot control, after installing windows.

---

### Post by JOSEISCOOL on 2011-04-28
I added the flag for boot but it still says that it can't use my drive because it needs drivers or something for that. Please help? This didn't happen before on my desktop x.x...

This by the way is a pc.

---

### Post by jordanae on 2011-04-28
Depending on how good your computer is and what kind of programs you need to run in Windows you might want to take a look at Virtualbox. That way you don't have to mess with partitioning and you can use the apps while still being logged in to Ubuntu.

You can download and view information about Virtualbox in the Ubuntu Software Center or on the Virtualbox website.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Ramon444 on 2011-04-28
Delete that not working partition and then create one with Windows 7 install disk or with Acronis Disk Director or fdisk if you are console guru :) Also it MUST be primary and bootable.

---

### Post by JOSEISCOOL on 2011-04-28
It is a primary, and now bootable but it still won't do it, it detects it but says it needs a drive x.x. I'd be willing to settle for windows xp x.x...

I can't create a partition with windows 7 because it won't use my hard drive.

I have a laptop 32 bit, 1 Gig of ram o.o so virtual box won't do it for me D:.

---

### Post by wilee-nilee on 2011-04-28
OP post a picture of gparted, did you make a ntfs inside an extended partition?

---

### Post by JOSEISCOOL on 2011-04-28
[http://s1182.photobucket.com/albums/x458/joseiscoolforreal/?action=view&current=Screenshot.png](http://s1182.photobucket.com/albums/x458/joseiscoolforreal/?action=view&current=Screenshot.png)

Thats a link to a picture of my screen shot.

---

### Post by wilee-nilee on 2011-04-28
> **JOSEISCOOL said:**
> [http://s1182.photobucket.com/albums/x458/joseiscoolforreal/?action=view&current=Screenshot.png](http://s1182.photobucket.com/albums/x458/joseiscoolforreal/?action=view&current=Screenshot.png)

Thats a link to a picture of my screen shot.

You have the sda2 flag set as raid it should be boot, doing this will remove the boot flag from sda1 where it is not needed at all. Ubuntu does not need a boot flag the booting windows does.

Here is my setup.
[ATTACH]190216[/ATTACH]

---

### Post by JOSEISCOOL on 2011-04-28
Okay, I'll brb, I'm going to try it again.

---

### Post by JOSEISCOOL on 2011-04-28
WOOT it installed thank you guys :D. but now I need to get the thing so it can show me the boot menu so I choose between windows and linux because I need my linux partition o.o so do you know how I would go about doing that?

---

### Post by wilee-nilee on 2011-04-28
> **JOSEISCOOL said:**
> WOOT it installed thank you guys :D. but now I need to get the thing so it can show me the boot menu so I choose between windows and linux because I need my linux partition o.o so do you know how I would go about doing that?

Boot the live cd of the installed Ubuntu and in the terminal run.
```
sudo mount /dev/sda1 /mnt
```
then
```
sudo grub-install --root-directory=/mnt /dev/sda
```
Reboot to the computer not the cd and you should see the grub menu choose Ubuntu and run in the Ubuntu installed terminal.
```
sudo update-grub
```

---

### Post by Sal33m on 2011-04-28
Windows doesn't recognize partitions formatted by Ubuntu. You'll also not be able to do a Windows reformat on a Ubuntu formatted partition while the hard drive is in the computer and thus will probably not be able to install Windows.

A solution that worked for me is to take out the hard drive, connect it to a jacket and then into another PC. Format the partition and then install Windows 7. If you can't format the partition, you might just have to bite the bullet and format the whole drive. Then FIRST install Windows 7 and then Ubuntu.

---

### Post by wilee-nilee on 2011-04-28
> **Sal33m said:**
> **Windows doesn't recognize partitions formatted by Ubuntu.** You'll also not be able to do a Windows reformat on a Ubuntu formatted partition while the hard drive is in the computer and thus will probably not be able to install Windows.

A solution that worked for me is to take out the hard drive, connect it to a jacket and then into another PC. Format the partition and then install Windows 7. If you can't format the partition, you might just have to bite the bullet and format the whole drive. Then FIRST install Windows 7 and then Ubuntu.

Have you read the thread?

---

### Post by JOSEISCOOL on 2011-04-28
Now when it boots up it just turns black -_- nothing actually shows up no menu or anything so...yeah...T.T how would I fix this?

---

### Post by wilee-nilee on 2011-04-28
> **JOSEISCOOL said:**
> Now when it boots up it just turns black -_- nothing actually shows up no menu or anything so...yeah...T.T how would I fix this?

To make this easiest lets run the bootscript in my signature, just click on it and follow the instructions. You will generate a text file come back to the thread open a reply and click on the (#) in the reply panel. This generates code tags paste all the text from that generated file between.

This script is a good if not the best way to get a full look at your setup.

You will have to use a live cd to run the script if you have no boot in to Ubuntu.

If needed you can boot the W7 install disc and restore the MS boot. 
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
bootrec.exe /fixmbr
here is a forum link as a visual.
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by JOSEISCOOL on 2011-05-01
I just installed ubuntu again(on a 2.9 gig partition) so I got the menu back, it was less work...

---

### Post by Dutch70 on 2011-05-01
I haven't been following this thread, but 2.9GB is kind of small isn't it?

---

### Post by ottosykora on 2011-05-01
one note to w7 install:

you can install it to one partition true, but later this might lead to problems. For example installing service pack 1 to w7 is not possible when it has no separate boot partition. (abt 300mb insize)
If w7 installs automatically, it will create separate small boot partition. Only then all updates and service packs will be possible.

---

