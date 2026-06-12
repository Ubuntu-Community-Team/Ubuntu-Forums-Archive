---
title: "initramfs boot failure"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by stevecole on 2010-10-13
Hi all,

So my daughter says she didnt do anything but now here ubuntu wont boot up.  It goes right to command line prompt and I see:

initramfs.  This at the root level.  Upon further investigation and an ls -l command I see many missing directories.

So, I dl 10.10 32 bit attempting a full install.  It gets to the preparing for ubuntu installation and hangs there.

Any ideas how to wipe this thing clean and install?

---

### Post by Lrpbpb on 2010-12-22
I got the same error after manually (by pressing the button) rebooting while ubuntu was trying to reenter the sytem after a locked screen (sorry...2 am in the morning....not sure that made sense). I also get the initramfs command and don't know what to do, however grub  works well and all, soI'm not sure what the problem is. 

Anyway, if you are absolutley suire you wan't a clean install:
1. Boot from live usb/cd and open gparted (System->Administration)
2. In gparted just format/delete the ubuntu partition
3. Install ubuntu again

---

### Post by acce on 2011-02-05
I had the same trouble. What I did is_ insert a ubuntu live cd_, _boot in live session_ and _mounting my hard drive_. Once mounted I just checked in a few folders. When I restarted my system, ubuntu asked me to verify the disk / and after a few minutes of checking the system booted normally and my problem was solved.

---

### Post by dino99 on 2011-02-05
sudo update-initramfs -u

---

### Post by Congolese on 2011-05-07
You've probably fixed it by now, but for anyone else... I had the same problem, initramfs thingy, booting from usb didn't work. 

Fixed it by opening grub menu (holding shift during startup) then choosing the recovery mode (there were 2 recovery modes, I chose the lower one ending in .31). It gave me the option then of fixing broken packages, which it then did automatically. It then allowed me to continue normal boot. This opened another command line screen, but with my login and password required, much like the terminal. After typing in login and password I  typed "sudo reboot", entered my sudo password and everything was back to normal. 

Not sure how or why this worked (as an ubuntu beginner), but hope it helps someone.

Wheelo

---

### Post by hope_never_dies on 2011-05-20
Hopefully you might have solved by this time..!

Anyway

I had the same problem with installing Ubuntu 11.04. I had already a  windows 7 installed in my system and ubuntu 10.04, since i was not able  to upgrade my 10.04 through network connections i planned to install it via USB  disk and upgrade while installation to 11.04. but then i got initramfs error,

Before solving problem

1) I was using a Sandisk 8GB USB with U3 software on it.
2) The USB installation  was created using  Universal USB installer  (metioned in ubtunu honepage)  [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

changes made to solve the problem

1) I used a new hp 8 GB USB drive which doesnt have U3 software 
2) I created a USB installation drive on this disk using Unetbooting [URL="http://unetbootin.sourceforge.net/"]http://unetbootin.sourceforge.net/
[/URL] 
Dont what solved the problem

Cheers

---

