---
title: "Ubuntu Live USB with Semi Persistance For Online Banking"
date: 2012-08-11
forum: Installation &amp; Upgrades
---

### Post by Chakolos on 2012-08-11
Hi, I'd like to create a Live Bootable USB of Ubuntu for online banking only.

I first created a non-persistant bootable usb, this works apart from the fact that I have to keep entering my wifi password.

Is there a way of creating a bootable USB of ubuntu with basic information in it such as my wifi Password and Bookmarks, but is not persistent to make it as secure as possible.

My first thought was to create a persistent USB of Ubuntu and someone "lock" casper from making changes, but I don't know how to do that?

Thanks

---

### Post by Bliepo32 on 2012-08-11
Well, personnaly I'd do the following:
[LIST=1]
[*]Partition the USB device: 1 partition for /boot (ext2) and one for / (ext2, 3 or 4)
[*]Use the alternate installer cd to install Ubuntu to the USB device. Make an encrypted home folder.
[*]Install GRUB to the USB device, **not to your hard disk**
[*]When the pc boots, select the USB device if you want to boot ubuntu. If your pc supports booting from USB, Grub will appear.
[*]Make a 'wipe' script that deletes everything from the home partition before shutdown except for certain excluded files and the replaces them with the default files.
[/LIST]

This way you can keep your packages up to date and have a secure system :)

---

### Post by prshah on 2012-08-11
> **Chakolos said:**
> Is there a way of creating a bootable USB of ubuntu with basic information in it such as my wifi Password and Bookmarks, but is not persistent to make it as secure as possible.

"Persistence" in the Live-USB  is a two part operation. One part is writing the information to the casper-rw persistence file.

The second part is informing the booting session that persistence is available. This is done by the keyword "persistent" in the grub command line.

Remove this keyword while booting for a transient session.

So, in effect, to get the result you want, boot into a persistent session (which is the default) and make the changes you want preserved. reboot to save the settings.

Then, update the /etc/grub.d/10_linux file (your filename / path may be different) and remove the word "persistent" from the line for the kernel entry-building options.

run```
sudo update-grub
``` and confirm that the word "persistent" is not preset in the relevant kernel options line in /etc/default/grub

Now, every session you boot will be transient. To make a session TEMPORARILY persistent, in the boot up mainmenu, press F6 for advanced options, and just add the word "persistent" to the kernel options (before the "--")

Please post back if you need more details.

---

### Post by C.S.Cameron on 2012-08-11
It is possible to mount casper-rw and read everything in it, (from a second o/s).

You can make a custom bootable iso using Remastersys.
No need to make persistent.

If you do a full install to USB you can encrypt the home folder.

I would hate to loose a bootable flash drive with my banking data on it

---

### Post by Chakolos on 2012-08-11
Thanks everyone for your help. I'm going to try suggestions and let you know how I get on.

---

