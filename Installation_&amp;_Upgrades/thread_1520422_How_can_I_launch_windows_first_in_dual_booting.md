---
title: "How can I launch windows first in dual booting"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2010-06-29
I have install lucid, and windows, I want when the computer start it should launch windows first, now it launch ubuntu first.

---

### Post by cpplinux on 2010-06-29
If you are using GRUB, try the savedefault option. Remove this option from ubuntu section and add it to the windows section.

---

### Post by hoboy on 2010-06-29
> **cpplinux said:**
> If you are using GRUB, try the savedefault option. Remove this option from ubuntu section and add it to the windows section.

Specifically how do I do this ?
i have tried 
sudo gedit /boot/grub/menu.lst

but it does not contain anything

---

### Post by stlsaint on 2010-06-29
> I have install lucid
> sudo gedit /boot/grub/menu.lst

Lucid does not use Grub but Grub2 which is NOT located at /boot/grub/meun.lst.

For the Grub2 wiki please see my signature.

Also if you want the system to boot windows first you can edit your grub2 to have it boot windows. Either use the default option or move the entries to show windows first.

---

### Post by C.S.Cameron on 2010-06-29
Do a AltF2 gksu nautilus
Go to boot/grub/grub.cfg and move the windows menuentry to be the first menuentry, before the Ubuntu menuentry.
This should work until someone does an update-grub on the machine.

---

### Post by oldfred on 2010-06-29
The quickest way for new users is:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

Another way:
But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/default/grub, and you won't have to edit Grub after kernel updates.
to copy entry from:
gedit /boot/grub/grub.cfg
To paste entry into ( I have to have both windows open for the copy/paste to work):
or
cat /boot/grub/grub.cfg | grep Windows
gksudo gedit /etc/default/grub
Change GRUB_DEFAULT=0 to your windows entry like this as example
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"

---

### Post by C.S.Cameron on 2010-07-02
One more method, see #6:

[http://ubuntuforums.org/showthread.php?t=1287602&highlight=usb](http://ubuntuforums.org/showthread.php?t=1287602&highlight=usb)

---

