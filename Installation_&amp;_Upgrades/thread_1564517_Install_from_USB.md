---
title: "Install from USB?"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by anxiousdog on 2010-08-30
I have followed [the directions]("http://www.ubuntu.com/netbook/get-ubuntu/download") to install the Netbook Edition onto my Acer Aspire One via usb drive.

When I created the USB using the Universal USB Installer app, I created a 1GB persistence on my 4GB USB. I now want to install rather than run from the thumb drive, except when I get to partition area, it's showing no drives at all.

I had XP, but I'd like to use the entire disk for UNE now. Any help as to how to get it to install?

Thanks!

---

### Post by snowpine on 2010-08-30
If I understand your question correctly (you want to install Ubuntu to a USB drive) you will need 2 of them, one with the "Live" image to install *from*, and another to install *to*. You can't install onto the drive you're currently running from. ;)

---

### Post by anxiousdog on 2010-08-30
Actually, I have it installed on the thumb drive already, I'm trying to get it onto the netbook's hard drive. The installer runs, but when it gets the partition area, there is nothing there. No hard drives...

If I go into gparted, it only shows the USB drive as the available hard drive. Therefore, I can't install it to the netbook!

---

### Post by snowpine on 2010-08-30
Sorry; I misunderstood! :(

Can you see and browse your internal hard drive from the Places menu?

---

### Post by anxiousdog on 2010-08-31
No, I can't see anything except the usb drive! Weird!

I'm using the Netbook version and it doesn't have the "Places" so I might not be looking in the correct spot. But looked all around and don't see any other file system except the thumb drive.

---

### Post by anxiousdog on 2010-09-01
Anyone have any thoughts on this? The details again are:

1: I have a netbook with XP on it

2: I'd like to install Ubuntu Network Edition

3: I downloaded it onto a USB drive and booted my computer

4: When the menu came up, I selected "Install to Hard Drive"

5: I walked through the steps, but when it comes to the partition screen, there is no options for any hard drives. 

6: I can quit the install and boot into Live Mode. When I open gparted or run fsdisk -l I only see the thumb drive as /dev/sda

Not sure what to do. I don't want to save my XP install, I just want to install UNE and use it. Any help out there?

---

### Post by snowpine on 2010-09-01
Sorry I do not have experience with this specific hardware. You may find the following guides helpful:

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Also I always recommend using the "Check CD for defects" option as it can save a lot of headaches if you have a bad "burn".

---

### Post by oldfred on 2010-09-01
My system would not see my sda which has XP. My XP would boot without any problem that I could see, but  I ran chkdsk anyway and then I could mount it and gparted would see it. It also may not see hibernated systems as that also puts a flag to prevent you from corrupting it.

---

