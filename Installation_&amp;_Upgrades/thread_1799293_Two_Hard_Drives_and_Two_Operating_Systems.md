---
title: "Two Hard Drives and Two Operating Systems"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by almanik on 2011-07-07
I just bought 2 Samsung Hard Drives and currently have Ubuntu on one. I was wondering whether it's possible to install Windows 7 on the other.

---

### Post by wkulecz on 2011-07-07
Of course its possible.  The problem will be dueling boot loaders.  IF you let your BIOS boot menu select which drive to boot there should be no issues, but this is rarely convenient as most BIOS are slow and clunky at best to change settings.

Generally installing Windows first and letting the Ubuntu installer handle the grub2 dual boot setup is the most painless way.

If you install Windows to the second drive with Ubuntu on the first I've no experience with what the windows 7 installer might do.

---

### Post by Ad@m on 2011-07-07
It certainly is.

I recommend you set it up as follows,

/dev/sda your Ubuntu drive (Primary)
/dev/sdb your Windows 7 (Secondary)

When installing Windows 7, you may have to disconnect the Ubuntu drive as Windows will complain it cannot access the drive and prevent you from installing Win7.

Once you have installed Win7, reconnect your Ubuntu drive (/dev/sda), boot into Ubuntu and update your grub menu so you have an option for Windows.

sudo update-grub

---

### Post by jramshu on 2011-07-07
What Ad@m said is pretty much what I did. I already had Windows on a hard drive, I disconnected that drive and installed Ubuntu on the new drive. Then made the Ubuntu drive the master and the windows drive the slave. Booted Ubuntu, ran update-grub, that way I didn't have to even mess with windows or worry about the windows bootloader. It works fine and I have no problem booting either OS.

---

### Post by Grenage on 2011-07-07
You also have the option of leaving Grub as it is on the Ubuntu drive, and install Windows on the second drive, with Windows bootloader being installed on its own drive.  You'd control which OS boots using the BIOS boot menu, rather than in GRUB.

Like the previous posters, I'd just use Grub to boot into both.

---

### Post by YesWeCan on 2011-07-07
+1 jramshu
A big advantage of having Windows and Ubuntu on separate disks is that you don't have to suffer issues caused by Grub deleting the standard MBR code that Windows expects to see, and will repair from time to time. So disconnecting the Windows disk while installing Ubuntu guarantees you don't accidentally put Grub on the Windows disk.

---

