---
title: "mini.iso doesn't appear in Startup Disk Creator"
date: 2015-06-14
forum: Installation &amp; Upgrades
---

### Post by Xpdin on 2015-06-14
I am interested to make a clean install of Lubuntu Core with the mini.iso from a USB Stick. I am not interested to create a Live USB.

I've done my best to add from "Other" button form the Startup Disk Creator the mini.iso but doesn't appear anything like in here [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I've tried also..

```
sudo chmod a+r "location"/mini.iso
usb-creator-gtk -i "location"/mini.iso

```

And when the Startup Disk Creator opens, the mini.iso still not appears.

```
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:   trusty


apt-cache policy lubuntu-desktop
lubuntu-desktop:
  Installed: 0.55
  Candidate: 0.55
  Version table:
 *** 0.55 0
        500 http://dk.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status
```


I don't think that the old partition is Encrypted, when I installed Lubuntu I remember that I chose not to encrypt it... if this could be important for you. But better if you know exactly how to check it to be sure.

I've tried the dd method but still nothing happened...


I've tried like that:

```
cd ~/Downloads/
    md5sum 'mini.iso'
a2502844750ecb6477d8fb4ff6b9aaf8  mini.iso

```

[COLOR=#111111][FONT=Ubuntu]md5sum is ok.

[/FONT][/COLOR]```
cd ~/Downloads/  
sudo su  
dd if='mini.iso' of=/dev/sdb1 bs=4096
7936+0 records in
7936+0 records out
32505856 bytes (33 MB) copied, 0.0784529 s, 414 MB/s

```
[COLOR=#111111][FONT=Ubuntu]I hope that sdb1 is ok, as you can see below...[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]It could be possible that the USB stick to be mounted? Can someone say it from this?[/FONT][/COLOR]


```
lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0  18.6G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda3   8:3    0 102.5G  0 part /home
&#9500;&#9472;sda4   8:4    0 108.1G  0 part /windows
&#9492;&#9472;sda5   8:5    0   3.7G  0 part [SWAP]
sdb      8:16   1   7.2G  0 disk 
&#9492;&#9472;sdb1   8:17   1   7.2G  0 part /media/multix/0AA3-23B8
sr0     11:0    1  1024M  0 rom  


sudo mkdir /media/iso/
sudo mount -o loop /home/multix/Downloads/mini.iso /media/isomount: block device /home/multix/Downloads/mini.iso is write-protected, mounting read-only

```
Thank you.

---

### Post by yancek on 2015-06-14
Loop mounting an iso file will always be read-only.
If you want to use dd to write a bootable iso to a flash drive you would need to replace "sdb1" and use "sdb".

---

### Post by Xpdin on 2015-06-14
I would like to be clear that with the mini.iso I am interested to make a clean install of Lubuntu Core not a Live USB

```
cd ~/Downloads/  
    sudo su  
    dd if='mini.iso' of=/dev/sdb bs=4096
7936+0 records in
7936+0 records out
32505856 bytes (33 MB) copied, 2.33314 s, 13.9 MB/s




```When I access the USB Stick I can't see any files on it, but when I go to Startup Disk Creator the "Label" of the stick is "Firmware" now and the capacity of it is 6.0 MB and the free space from it is 6.0 MB too...


THis is how it looks after I use dd


```
lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0  18.6G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda3   8:3    0 102.5G  0 part /home
&#9500;&#9472;sda4   8:4    0 108.1G  0 part /windows
&#9492;&#9472;sda5   8:5    0   3.7G  0 part [SWAP]
sdb      8:16   1   7.2G  0 disk 
&#9500;&#9472;sdb1   8:17   1    25M  0 part 
&#9492;&#9472;sdb2   8:18   1     6M  0 part /media/multix/Firmware
sr0     11:0    1  1024M  0 rom  
loop1    7:1    0    31M  1 loop /media/iso

```

---

### Post by ajgreeny on 2015-06-14
That's interesting!
I haven't used the Startup-disk-creator for a long time, and after reading your post I just tried using the mini-iso file as you have, and I got exactly the same problem; the mini-iso is totally invisible to SDC, whereas all other .iso files that I have are seen and work as normal.

I wonder if this is a result of the mini.iso file not being a live system but install only; I am not sure if the SDC is only for live systems as I've not tried this before for a mini.iso and as I said, I don't use SDC an more but boot live systems and then install in VBox instead to try them out.

I also tried using unetbootin (available from the repos) and that works fine, so could be your best way forward.

---

### Post by Bucky Ball on 2015-06-14
*Thread moved to **Installation & Upgrades**.*

Try [Unetbootin]("http://unetbootin.sourceforge.net/") (check in Software Centre for it first, not sure if it's in there or not but better from there) or [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"). Launch it and point it to the mini.iso iso. Check you have the correct USB as the target and fire.

Let us know how you go. You certainly shouldn't need to be issuing all that code to get this working. It 'should' be as simple as launching the USB creator program, choosing a source .iso, choosing a tartget and hit the burn button. What OS and release are you trying this on? :-k

PS: The mini.iso should work fine with Unetbootin (and probably others) to create an installer on USB (or SD). I've never had an issue and the mini is pretty much all I use. :)

* Just reading your last post. I suggest you boot from the USB and see what happens. My suggestion if none of the above worked was to use dd. But DO SO WITH CARE as it will totally wipe anything in its path (if you choose the wrong target device, for instance ... don't think about it!).

---

### Post by sudodus on 2015-06-14
> **Xpdin said:**
> I would like to be clear that with the mini.iso I am interested to make a clean install of Lubuntu Core not a Live USB

```
cd ~/Downloads/  
    sudo su  
    dd if='mini.iso' of=/dev/sdb bs=4096
7936+0 records in
7936+0 records out
32505856 bytes (33 MB) copied, 2.33314 s, 13.9 MB/s

```

This cloning attempt was probably successful :-) ***Try to boot from the pendrive as it is!***

I made [mkusb]("https://help.ubuntu.com/community/mkusb") to wrap security around dd (to avoid overwriting valuable data on other drives by mistake). But it is basically doing the dd command that you have used.

Do not get confused by the strange partitioning. It is because the iso format was developed for CD (the ISO 9660 file system), plus some tweaks to make the iso file work when cloned to a mass storage device (in practical life almost always: USB pendrive).

*Edit:* If you use some old versions of mini.iso, you may have problem with cloned copies, but it works with the versions found via [this link]("http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730")

---

### Post by Xpdin on 2015-06-20
> **Bucky Ball said:**
> *Thread moved to **Installation & Upgrades**.*

Try [Unetbootin]("http://unetbootin.sourceforge.net/") (check in Software Centre for it first, not sure if it's in there or not but better from there) or [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"). Launch it and point it to the mini.iso iso. Check you have the correct USB as the target and fire.

Let us know how you go. You certainly shouldn't need to be issuing all that code to get this working. It 'should' be as simple as launching the USB creator program, choosing a source .iso, choosing a tartget and hit the burn button. What OS and release are you trying this on? :-k

PS: The mini.iso should work fine with Unetbootin (and probably others) to create an installer on USB (or SD). I've never had an issue and the mini is pretty much all I use. :)

* Just reading your last post. I suggest you boot from the USB and see what happens. My suggestion if none of the above worked was to use dd. But DO SO WITH CARE as it will totally wipe anything in its path (if you choose the wrong target device, for instance ... don't think about it!).

Thank you very much to all...

I used [Unetbootin]("http://unetbootin.sourceforge.net/") method, and it worked perfect.

Have a great weekend !

---

### Post by Bucky Ball on 2015-06-20
Great news! Thanks for tagging as solved and enjoy. :)

Be sure to post a new thread if you have any issues other issues.

---

