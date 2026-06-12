---
title: "Installing to external HDD"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by Aloshi on 2008-02-01
I recently bought an external hard drive (40 GB) for just Ubuntu, and have been trying to install it for the past few hours.  I have a 7.10 LiveCD and have checked it for defects. I tried running the install and having it just take the whole external drive and successfully finish installation.  However, when I try to boot, GRUB returns error 21.  I ran fixmbr, completely reformatted the drive, and tried again - same result.

I plan to have this external drive be primarily for MY computer, however I need to be able to remove the drive and still be able to boot into XP and would like to be able to use it on multiple computers (not that important though).
I have Windows XP on my Hard Drive at the moment, and plan to leave it that way.
I think I can boot from USB with this computer.

How can I get it to install correctly?

---

### Post by Aloshi on 2008-02-01
Bump... :|

---

### Post by mättu on 2008-02-01
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

helps?

---

### Post by Aloshi on 2008-02-01
Not really - my computer doesn't have GRUB, I want to be able to load GRUB from my USB Drive (but not require the drive to be in all the time so it'll load). :\

---

### Post by mättu on 2008-02-01
GRUB is the bootloader used by ubuntu.
Did you install it in the MBR (master boot record) of your internal HD or of your USB-disk?
If you don't understand the question, please read 
[https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29)

:m)

---

### Post by Aloshi on 2008-02-01
It was installed to my internal hard drive, but I had to use fixmbr to replace it so I could boot into windows (as GRUB would just return error 21 before even giving a menu).

---

### Post by mättu on 2008-02-01
[http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/#more-253](http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/#more-253)

please note eapecially:

IMPORTANT: Ensure that all internal hard drives are disconnected from your computer during the install (pull your SATA or IDE cables)

That means you onplug your internal HD, so that GRUB cannot be installed into it's MBR. After the install is complete, plug it back in.

---

### Post by Aloshi on 2008-02-01
I can't go digging into my internal hard drive (not allowed...).  Isn't there an advanced button at the end of the install where you can change the HDD it installs GRUB to, though?

---

### Post by Aloshi on 2008-02-01
Bump...

---

### Post by Aloshi on 2008-02-01
Bump AGAIN... :|

---

### Post by logos34 on 2008-02-02
You can install grub to usb drive MBR [using the live cd]("http://ubuntuforums.org/showthread.php?t=224351").

Then go into /boot/grub/menu.lst and change root from (hd1,x) to (hd**0**,x)

> **Aloshi said:**
> I can't go digging into my internal hard drive (not allowed...).  Isn't there an advanced button at the end of the install where you can change the HDD it installs GRUB to, though?

Yes.  step 7 'Ready to Install' screen -- press 'Advanced' button lower right.  You would replace default '(hd0)' with **(hd1)**, or **/dev/sdb** (or whatever the external drive is)

---

### Post by Aloshi on 2008-02-02
Okay, I'll try that.

I think the problem is my computer won't boot from USB...(The drive shows up as a Hard Drive in windows, strangely enough, so I think that's why it isn't detecting a USB device)

---

### Post by SpiderGorilla on 2008-02-02
Uh, I told mine to install without a boot loader at all, since I didn't want to mess up my Vista installation. I just jump into my boot loader menu (F12 on my Dell) before it mounts the Windows drive and tell it to boot from Linux. Hasn't failed me yet.

For clarity: my Ubuntu partition is on an external HDD under USB 2.0. My system is able to support booting from USB 2.0

---

### Post by logos34 on 2008-02-02
> **SpiderGorilla said:**
> Uh, I told mine to install without a boot loader at all, since I didn't want to mess up my Vista installation. I just jump into my boot loader menu (F12 on my Dell) before it mounts the Windows drive and tell it to boot from Linux. Hasn't failed me yet.

???

---

