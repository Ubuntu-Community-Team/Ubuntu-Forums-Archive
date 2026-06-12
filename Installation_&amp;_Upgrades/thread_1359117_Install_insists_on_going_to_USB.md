---
title: "Install insists on going to USB"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by orlandomike on 2009-12-19
I installed remix off of a usb, formatted the hard drive etc. All seemed successful, however, if i change the boot order to hard drive or just pull the usb it will not boot. In other words, it seems to format the HD but doesnt really install Grub on it? I can tell that, even on reboot , it is actually running off the USB and it will not load via the HD. anyone know why?

---

### Post by darkod on 2009-12-19
Are you sure you have it installed on the hdd at all?
Boot with the stick again, Try Ubuntu option, open Gparted (in System-Administration) and check your hdd partitions. Your / will probably be /dev/sda1 or /dev/sda5. That will also confirm whether you have it installed on the hdd at all.
Once you find out your what partition is your /, in terminal install grub2 there with:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Reboot without the stick and see how it goes.

---

### Post by orlandomike on 2009-12-19
it suggests the boot partition is /dev/sda1 which is the 160 gb drive.  then there is a /dev/sda2 extended 2.5 gb and a sub under that of the sda5  linux swap

does that mean the os is on the hard drive but the swap file is on the usb?

i ran the first command and it said sda5 looks like swap space - not mmounted mount: you must specify the file system type.

i tried to reboot without the usb and i now get to a prompt:
sh:grub> blinking cursor.

---

### Post by darkod on 2009-12-19
/dev/sda1 is not your boot partition but is your / (root) partition, the system partition. Like C: in windows. Be careful with that because boot partition means entirely different thing.
Then /dev/sda2 is extended partition in which you have /dev/sda5, the swap as logical. Because one hdd can have only 4 primary partitions, linux always labels the logical partitions starting from 5 and onwards.
In your setup you should have adjusted the command as:
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That should do it.

---

### Post by orlandomike on 2009-12-19
thanks, i am going to reinstall as i think no matter what i do now i am sitting on that grub cursor. i will reload and try what you said. if you dont mind, check back in a bit and i will let you know pass or fail. Thanks for your help and patience.

---

### Post by orlandomike on 2009-12-19
ok before i reboot this i am in Gpart and the partition /dev/sda1 file system ext4 it is the 160 gb hd, the mount point says /,/mnt flags it says boot

before i didnt see anything on the mount pointthere but should it be /,/mnt  ? that doesnt seem right

---

### Post by darkod on 2009-12-19
Well if you mounted it as /mnt then yes, it should say that.
You have to make a difference between running from hdd and LiveCD. In LiveCD your hdd system is not used, mounted at all. That's why you need that first sudo mount command to mount your / partition (in your case /dev/sda1) as /mnt. And then the second command install grub at /dev/sda, the MBR of the hdd, with root directory /mnt/, in other words your original hdd /.

---

### Post by orlandomike on 2009-12-19
I have found that when i try to boot from the hard drive, for a quick moment it says unknown keyword  configuration gfxboot

---

### Post by orlandomike on 2009-12-19
and that command still took me to a grub rescue point

---

### Post by darkod on 2009-12-19
Download the script in my signature, move it on desktop for example, and execute it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with lots of info about your boot process. Copy the content here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above).

---

### Post by orlandomike on 2009-12-19
Well, instead of the USB method, the netbook bios had a usb/CD boot option, so I grabbed a DVD drive and connected it to a HD  USB external storage box, burned the iso image to a cd and just loaded it like a regular computer would. So it worked out. Thanks for your help.

---

