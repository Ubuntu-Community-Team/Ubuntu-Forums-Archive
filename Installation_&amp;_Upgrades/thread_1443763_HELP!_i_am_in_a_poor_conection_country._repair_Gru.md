---
title: "HELP! i am in a poor conection country. repair Grub2 using Grub?"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by linuxd00 on 2010-03-31
Short: my grub2 broke and i cant download much. how to repair?

slightly longer:

I am currently in a country where the internet speed is roughly 15KB at best... if at all. So i cant download the 9.10 live CD.
My grub2 broke when i reinstalled windows (because its so virus prone).

This guide: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

says how to repair grub2 using grub2 live CD... currently i have access to a 6.10 Ubuntu CD... but when i try to mount the boot partition i get an error saying that the filesystem has unknown options.. i think that the latest filesystem didnt exist back then... and even if that would work... 

can i reinstall grub2 using grub? 

or is there any possibilty to download an ultra small linux live system image with grub2? it seems all ubuntu variations come in 500MB+ packs. :(

thanks for any help.. i miss my linux. :(

---

### Post by dstew on 2010-03-31
Do you have access to another computer that boots using grub2? If so, you can make a grub2 boot .iso file using the grub-mkrescue command. You can burn this .iso onto a CD or even a floppy disk, and then you will have a bootable grub2 rescue CD (or floppy). If you boot it you get a grub2 command line. You can enter commands on the grub2 command line to boot your Ubuntu system. Once that is booted, you can re-install grub onto the hard disk. Or, you can try and re-install grub from the grub rescue CD. Here is [Herman's page]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkrescue") on how to do this. Once you have a command line, [here is how to boot]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html").

EDIT: [Another good example.]("http://www.linuxquestions.org/questions/linux-general-1/how-i-make-bootable-cd-contains-grub2-766336/")

EDIT again: I looked around, there are some sites with downloadable "grub2 rescue CD" files that you could try if you don't have access to another Linux computer with grub2 on it. I have not tested these, and I don't know if they are safe. Alternatively, you could get a friend to make the .iso or floppy disk image and email it to you. Maybe even me if you ask!

---

### Post by linuxd00 on 2010-04-04
hi, thanks for answering. i still have the problem. could you create an iso file for me? that would be great. i can burn it to a cd here. i think with luck my internet line could handle some 20MB without resetting.
it would be great if you could upload it to rapidhare or somthing and post it here so others can profit from it if needed. :)

damn... even if i do repair it i will still be dying to try 10.4.. but hey you cant get5 everything :D

---

### Post by new_tolinux on 2010-04-04
> **linuxd00 said:**
> i think with luck my internet line could handle some 20MB without resetting.
Maybe you want to try usenet.
Every file (from 1b to many TB) goes in packets of a few thousand lines, so if the connection resets you may be missing that block, but you won't have to redownload the complete file.
When par2-files are included, you can even repair your download when some blocks are missing.

---

### Post by 2hot6ft2 on 2010-04-04
Wow, I just looked at the manual pages for it and ran the command to make it without any special options and it's only 1.2 MB. Let's see if I can find a place to put it for you.
It's a cdrom iso

Never used that before so no promises as to it's functionality.

---

### Post by 2hot6ft2 on 2010-04-04
Here you go.
[http://rapidshare.com/files/371944343/grub2.iso.html](http://rapidshare.com/files/371944343/grub2.iso.html)
MD5: B80257FCAC3630F971A3A67F5A7E9D35

It also said this on the upload page:
> Your file has been saved and can now be downloaded 10 times. It will be deleted after 60 days without download. If you would like to enable more people to download your file, please transfer it to a free Collector's Account or a Premium Account.
So I guess it will only be there for 10 downloads.
Here's the command I ended up using to make sure it would be a cdrom iso
```
grub-mkrescue --image-type=cdrom grub2.iso
```

---

### Post by dstew on 2010-04-04
@2hot6ft2: Thanks for getting the .iso for the original poster.

One more thing of interest: there is an Ubuntu package named [grub-rescue-pc]("http://packages.ubuntu.com/search?keywords=grub-rescue&searchon=names&suite=karmic&section=all") which contains the CD and floppy disk images already made. If you install this package using Synaptic, apt-get or Software Center, the images will be found in the /usr/lib/grub-rescue directory, with instructions for use in the /usr/share/doc/grub-rescue-pc directory. The grub-rescue-cdrom.iso for the CD in this package is less than a megabyte.

---

### Post by linuxd00 on 2010-04-05
hi! thanks for your help.. i am a step closer but not there yet.

i dloaded and started the image..
then booted to my ubuntu using the commands from the link you provided:

```

grub> linux   (hd0,7)/boot/vmlinuz-2.6.27-9-generic root=/dev/sda7
grub> initrd  (hd0,7)/boot/initrd.img-2.6.27-9-generic
grub> boot

```

This worked perfectly.. i have windows xp on sda1 and linux on sda7 (boot is from this unit)

then i used 

```


sudo mount /dev/sda7 /mnt

sudo grub-install --root-directory=/mnt /dev/sda

sudo umount /mnt

```

all this from the ubuntu on my hardrive.(should i unmount something?)

now Grub loads but does not offer the menu but only an error saying "file not found" and throws me to grub rescue mode.

in total now my laptop is completely unusable :(

i have tried running os-probe and update-grub2/update-grub to no avail.

then i tried the same with

```

sudo mount /dev/sda1 /mnt



```
 because fdisk -l said that sda1 is boot partition... now i get grub 1.97 beta4 in normal mode but still no boot menu :(

anybody knows why is this failing?

 i feel quiet close..

---

### Post by dstew on 2010-04-06
If I understand you correctly, you are now able to boot into your Ubuntu using the grub rescue CD. Once you are in Ubuntu, you can reconfigure grub from that system. I think the method you are following, using the mount command, is for installing grub from a Live CD boot, not from a hard-disk boot that already has grub on it.

Check to see that you have the installed grub 2 package:```
grub-install -v
```If it comes back with a version that is greater than 1, like 1.96 or 1.97, then grub is installed (the software is there). To reconfigure grub so it boots your system, do```
sudo grub-install /dev/sda
```After that try```
update-grub
```

---

### Post by linuxd00 on 2010-04-07
```
sudo grub-install /dev/sda
```

THANKS!!! this did it!! i am now proudly working on my own PC again.
Thanks a lot!!

this tread is happily closed!

---

