---
title: "i am unable to boot windows 8.1 after installing ubuntu 15.04"
date: 2015-10-31
forum: Installation &amp; Upgrades
---

### Post by pkishensuraj on 2015-10-31
Hi,

My laptop has windows 8.1 pre-installed. Now i installed ubuntu 15.04 in an empty drive.

during my installation,I made three partitions

one for \ as ext4 journaling file system
two for \home as ext4 journaling file system
rest for swap area

 device for boot loader installation - was left to the default option.

during the start of my computer, i get two boot options
1)boot from efi file - when i press enter i gives a screen which has file explorer on it and is stuck like that forever.
2)notebook harddrive - when i press this ubuntu starts

how to figure out what has happened?

do i have a way to figure out what happened

---

### Post by oldfred on 2015-10-31
If Windows 8 or later is pre-installed it is the newer UEFI, not older BIOS boot install.
But most UEFI systems have CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
    
UEFI and BIOS are not compatible and from grub you can only boot systems installed in same boot mode. So did you install Ubuntu in UEFI boot mode?
 
The other issue is that you must turn off Windows fast start-up or always on hibernation. If UEFI you should be able to directly boot Windows from UEFI boot menu or perhaps one time boot key, often f10 or f12 but check your manual.

Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Bucky Ball on 2015-10-31
*Thread moved to **Installation & Upgrades**.*

---

### Post by pkishensuraj on 2015-10-31
I don't know whether i installed ubuntu in UEFI boot mode. When legacy mode(which has notebook hard drive) is enabled my ubuntu starts otherwise no.

I created a boot-info using boot-repair on [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

then following file is generated , [(https://help.ubuntu.com/community/Boot-Info)then following file is generated , https://drive.google.com/file/d/0B7WP0CFc966rU2FZbTd4MV9lRDA/view?usp=sharing"]https://drive.google.com/file/d/0B7WP0CFc966rU2FZbTd4MV9lRDA/view?usp=sharing]("http://I don't know whether i installed ubuntu in UEFI boot mode.I created a boot-info using boot-repair on [https://help.ubuntu.com/community/Boot-Info)

my files of windows c drive are still existing and are visible in my ubuntu

---

### Post by pkishensuraj on 2015-11-01
[INDENT]Hi,

My hp laptop has windows 8.1 pre-installed. Now i installed ubuntu 15.04 in an empty drive.

during my installation,I made three partitions

one for \ as ext4 journaling file system
two for \home as ext4 journaling file system
rest for swap area

 device for boot loader installation - was left to the default option.

during the start of my computer, i get two boot options
1)boot from efi file - when i press enter i gives a screen which has file explorer on it and is stuck like that forever.
2)notebook harddrive - when i press this ubuntu starts

					I don't think(not sure) i installed ubuntu in UEFI boot mode. When  legacy mode(which has notebook hard drive) is enabled my ubuntu starts  otherwise no.

I created a boot-info using boot-repair on [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

then following file is generated , [(https://help.ubuntu.com/community/Boot-Info)then%20following%20file%20is%20generated%20,%20https://drive.google.com/file/d/0B7WP0CFc966rU2FZbTd4MV9lRDA/view?usp=sharing"]https://drive.google.com/file/d/0B7WP0CFc966rU2FZbTd4MV9lRDA/view?usp=sharing]("http://I%20don%27t%20know%20whether%20i%20installed%20ubuntu%20in%20UEFI%20boot%20mode.I%20created%20a%20boot-info%20using%20boot-repair%20on%20[https://help.ubuntu.com/community/Boot-Info)

my files in windows c drive are still existing and are visible in my ubuntu 				


do i have a way to solve this
[/INDENT]

---

### Post by yancek on 2015-11-01
Clicking on your second link show file not found, post it again.
Most likely is that you installed Ubuntu in MBR while your windows was installed using UEFI.  The results you are showing are expected.  Both systems must be UEFI or both systems must be MBR.  Ubuntu documentation at the site below:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2015-11-01
Your Windows is in BIOS boot mode on a MBR(msdos) drive.
Windows only boots in UEFI mode from a gpt partitioned drive.

So do not boot in UEFI mode unless you want to totally erase and reinstall everything on your drive.
Of course you should have good backups whether converting to UEFI or not.

You show Boot-Repair/Live installer booted in UEFI mode. Best to boot in BIOS mode since installs are BIOS/MBR based.

Have you tried this from your Ubuntu install.
sudo update-grub

Often issues of not finding Windows are related to Windows 8 or later's fast start up or always on hibernation or NTFS needing chkdsk. You can only run chkdsk from Windows repair console, so best to have a separate Windows repair flash drive or separate Windows installer flash drive.

---

### Post by oldfred on 2015-11-01
Thread merged with previous thread.

Please do not post duplicate threads on same topic.

---

### Post by pkishensuraj on 2015-11-01
paste it in the address bar

---

### Post by pkishensuraj on 2015-11-01
hey 
sudo update-grub 

has worked.
You are great!

---

