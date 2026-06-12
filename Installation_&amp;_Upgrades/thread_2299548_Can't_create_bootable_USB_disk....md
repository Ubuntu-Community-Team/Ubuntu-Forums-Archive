---
title: "Can't create bootable USB disk..."
date: 2015-10-19
forum: Installation &amp; Upgrades
---

### Post by orange2k on 2015-10-19
No matter what I do, I can't create a bootable USB disk. I have a 8 GB usb pendrive, I formated it to fat32, but when I run unetbootin, the LED on the usb drive stops blinking at writing filesystem.squash.fs, and then it says it is complete, but when I try to boot from the disk, it won't start. I have previously installed ubuntu this way more than a couple of times, but now it doesn't work anymore. What should I do?
I run ubuntu 15.04.

---

### Post by sudodus on 2015-10-19
Is this in the same or in another computer?

Have you checked the [md5sum](https://help.ubuntu.com/community/UbuntuHashes)?

Try with another tool, for example [mkusb](https://help.ubuntu.com/community/mkusb) (if you create the pendrive in Ubuntu or an Ubuntu flavour). See the following link for more details.

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by orange2k on 2015-10-19
Its on the same computer, and yes I have checked the md5sum...

---

### Post by ubfan1 on 2015-10-19
Try typing "sync" (no  quotes) a few times at the terminal before removing the USB.  Flushes the write buffers, completing the USB creation.  Maybe try putting a 4G fat partition on the USB and install to that -- big partitions have caused some problems in the past.

---

### Post by sudodus on 2015-10-19
> **orange2k said:**
> Its on the same computer, and yes I have checked the md5sum...

You unetbootin might be old. Try the version from the developer's PPA or try another tool.

-o-

There might be problems with the pendrive's hardware or the low level management of the memory. See also the following link

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by orange2k on 2015-10-19
I've formated the drive twice, first to NTFS (the slow way) in windows, then to FAT32 (also in windows, the slow way also), and then I used unetbootin to write the ISO, and it failed...
I think that the pendrive is somehow broken, will make sure tommorow with another pendrive to see if the problem persists...

---

### Post by sudodus on 2015-10-19
It show be evident if the pendrive is broken or not, when you format it 'the slow way'.

Unetbootin works most of the time when I try it, yet I would try with another tool (other than Unetbootin).

Sometimes it makes a difference if you wipe the first megabyte (remove traces of previous systems, that might confuse the boot process).

But there might be another problem - hardware mismatch between the pendrive and the computer. Even if it can be used for reading and writing, there might be problems to boot from it. In that case you will have better luck with another pendrive (other brand and/or model).

---

### Post by orange2k on 2015-10-20
> **sudodus said:**
> 

Sometimes it makes a difference if you wipe the first megabyte (remove traces of previous systems, that might confuse the boot process).



How do I do that? Can I do that from the CLI, Or is there a program that does that?

---

### Post by sudodus on 2015-10-20
Both. Do it 'without safety belt' with ***dd***, which is nick-named 'disk destroyer' because it does what you tell it to do without questions, even if you tell it to wipe the family pictures. Or do it with ***mkusb*** which 'wraps a safety belt around dd'.

[/mkusb#Wipe_the_first_megabyte_or_the_whole_device](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device)

You can install mkusb (the newest version with a wipe menu) with the following commands

```
sudo add-apt-repository ppa:mkusb/unstable
sudo apt-get update
sudo apt-get install mkusb
```

***Edit:*** But you can also use mkusb to create the USB install drive directly (to flash the content of the iso file into it) without wiping the first megabyte.

---

### Post by yawanathan_israel2 on 2015-10-23
Hello,

I had a similar issue with unetbootin and Ubuntu. I created the bootable drive and when I tried to get it to boot it would not. I had to go into my bios (MSI Gaming7) and make sure to use only UEFI. I had to make sure it was loaded first in bios before the hard drive. Once I did that the USB Key Drive was seen and I was able to install.  If you have your bios set to legacy+UEFI it for some reason doesn't want to install. 

Now this may work or not, or it may not even be in the ballpark, but it's just something I did and it worked.

Thanks
Yawanathan

---

