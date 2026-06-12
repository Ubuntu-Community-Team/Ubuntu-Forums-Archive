---
title: "Can anyone help with duel booting from usb installer please?"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by Lawrence_Kim on 2015-03-28
hello, i'm a noob in this linux system in general (switched to linux a few weeks ago) and i'm having quite a difficulty playing games in linux (wine and playonlinux showed pretty much awful performance for me).

So i decided to have a duel boot with windows 7 and ubuntu. I have a 1 TB hard disk installed in my laptop, with 2 main partitions. one for elementary os luna and the other for ubuntu (it says on the GUI disk view that I have 5 partitions precisely, but i think they were kinda subs).

I have installed both luna and ubuntu through usb installer so i know there shouldn't be any bios issues with this, however, when i created windows 7 bootable usb with dd command and tried to boot it from the thing (you know... the screen you can enter by pressing f2 before the main os boots up)

it just goes straight to the normal booting screen where i choose between ubuntu and luna. Is this because the two main partitions are already full? or are there any more steps to do for windows 7? I had no problem at all when I installed luna and ubuntu











btw, luna's brilliant. you guys should try it :)

---

### Post by yancek on 2015-03-28
The method explained at the site below worked with windows 10 so I expect it would work with windows 7.

[http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html)

The page below gives some options that might work and there is an example of using the dd command.  Make sure you get the right device or you will destroy all the data if you select the wrong device.  I've never tried this with windows so have no idea if it will work.  The above method does.

[http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu](http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu)

---

### Post by Lawrence_Kim on 2015-03-29
> **yancek said:**
> The method explained at the site below worked with windows 10 so I expect it would work with windows 7.

[http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html)

The page below gives some options that might work and there is an example of using the dd command.  Make sure you get the right device or you will destroy all the data if you select the wrong device.  I've never tried this with windows so have no idea if it will work.  The above method does.

[http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu](http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu)


thx so much for the reply, man. i don't really care about destroying data cos i've lost them all alraedy when i ****ed up with installing linux luna a few weaks ago lol.

i'll try your suggestions, thx.

---

### Post by Lawrence_Kim on 2015-03-31
> **yancek said:**
> The method explained at the site below worked with windows 10 so I expect it would work with windows 7.

[http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.com/2014/09/make-bootable-windows-usb-from-ubuntu.html)

The page below gives some options that might work and there is an example of using the dd command.  Make sure you get the right device or you will destroy all the data if you select the wrong device.  I've never tried this with windows so have no idea if it will work.  The above method does.

[http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu](http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu)


well, thx very much for the links. i've followed them and i think that is a really safe way to create a bootable usb. i was worrying about the dd command anyway.

but it still hasn't fixed the problem yet. i deleted the entire partition for 'os luna'. it shows 'unallocated' on disk viewer. so luna should be totally deleted now but i can still see it from the boot menu. when i choose luna, it goes back to the boot menu instead of booting (which is actually obvious since i deleted partition). plus i can select boot from usb though, it straight goes to boot menu again. so whatever i do, it goes to boot menu. and this beautiful line for os luna greets me.

btw, windows 10 64bit iso is copied to the usb. format is fat 32.

---

### Post by yancek on 2015-03-31
I would not expect the dd command to work for a windows iso but haven't ever really tried it so, maybe it would.  If not extremely careful with dd, it's pretty easy to muck up the whole system.

> btw, windows 10 64bit iso is copied to the usb. format is fat 32. 		

I'm not sure what your plans are.  Are you trying to follow the link I gave yesterday to put windows 7 on a flash drive and boot from the flash drive to install windows 7?  If that's what you want, you need to format the flash as ntfs as it states in the link I gave you.  FAT32 won't work.  You also need to extract the windows files from the iso and not just copy the iso to the flash.  Most Linux systems won't boot directly from an iso in that manner.  Ubuntu and most of its derivatives will but I don't believe you will get that to work with windows so use the Disk Image Mounter to extract the files and then copy them to the ntfs formatted partition on the flash and follow the rest of the steps to get Grub on the flash drive.

---

### Post by corneliuss2 on 2015-03-31
Are you trying to boot in UEFI mode? If so, it is OK to use FAT32.  As @yancek  said, extract ISO contents to USB,  don't copy the file directly.

---

### Post by Lawrence_Kim on 2015-03-31
thx guys. i'll try again.

---

### Post by yancek on 2015-03-31
> Are you trying to boot in UEFI mode? If so, it is OK to use FAT32

Actually, he is trying to put the windows 7 iso, extracted on a flash drive as per the instructions in the link in my first post in the hope he would be able to use it to then install windows 7.  According to the link, formatting the flash FAT32 won't work.  I haven't tried it but it does work on an ntfs formatted flash, at least with windows 01.

---

### Post by Lawrence_Kim on 2015-04-01
thx you all. formatting to ntfs has fixed the problem :)

---

