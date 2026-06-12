---
title: "Ubuntu installs, but refuses to shot in boot manager"
date: 2015-04-30
forum: Installation &amp; Upgrades
---

### Post by simon97 on 2015-04-30
Hey there,

I've been using Ubuntu for a while, but took a pause to go back to Windows completely, as I'm a Windows software developer.
I recently decided to use a dual-boot solution for video rendering and graphics design, as I'm not willing to pay several hundred Euros for software that essentially does the same as the equally good open source software.

Anyways, today I tried installing Ubuntu Studio alongside Windows, and the installation completed without errors.
All the partitions and files are present, however the OS does not show up in the boot manager, nor does it boot up.

I installed the OS via a USB stick, as I've done plenty times before.

I'm completely stumped. I installed twice, and completely deleted the partitions created after the first install.

Here are some screenshots of the partitions and files:
[ATTACH=CONFIG]261678[/ATTACH][ATTACH=CONFIG]261679[/ATTACH]

I'm using a 2008 Dell Studio 1737, Pentium Duo T4500 w/ 4GiB DDR2 RAM.
Installed version of Ubuntu: Ubuntu Studio 15.04 x64

Any help with this would be much appreciated.

---

### Post by oldfred on 2015-04-30
Did you install grub to MBR, not a partition?

Windows does not see Linux partitions so screenshots from Windows do not show Linux.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by simon97 on 2015-04-30
I selected the "Install Ubuntu Alongside Windows 8" option

---

### Post by oldfred on 2015-04-30
Did you leave Windows fast startup on? That is always on hibernation and must be off.

       Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Post link to Summary report.

---

### Post by simon97 on 2015-04-30
My laptop doesn't have UEFI, so it doesn't support that feature in the first place. It's still got a good old BIOS.

---

### Post by oldfred on 2015-04-30
If it is Windows 8 then it still has fast startup. 
Where is link, as that is the only way we can tell anything about your system.

---

### Post by simon97 on 2015-04-30
What link?

---

### Post by simon97 on 2015-04-30
Turned Fast Startup off, rebooted the machine, only change was that it was a pain to boot up again.

---

### Post by oldfred on 2015-04-30
The link in Post #2 on Boot-Repair and it summary report.

---

### Post by simon97 on 2015-05-01
Here's the summary report. 
I used the Ubuntu install on my external drive, I don't know if that will influence anything.
[http://paste.ubuntu.com/10961653/](http://paste.ubuntu.com/10961653/)

---

### Post by grahammechanical on 2015-05-01
> => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub.

The machine is booting from the drive with Windows (sda) on and the Windows boot menu does not show Ubuntu because the Windows boot manager does not recognise any operating system other than a Microsoft operating system.

If you set the BIOS/UEFI to boot from the drive with Ubuntu on (sdb) you will see the Ubuntu boot loader (Grub) and it will show an entry for Ubuntu and a Windows 8 boot loader.

In your first post you said this

> however the OS does not show up in the boot manager,

You did not tell us that this boot manager was the Windows boot manager. Nor did you tell us that you had more than one drive and Ubuntu 14.04.2 as well as Ubuntu 15.04. All that was useful information. So, here is your situation,

If you boot from sdb you should get a Ubuntu boot menu with Ubuntu 14.04.2 and maybe Windows 8 boot loader but not Ubuntu 15.04 because Ubuntu 14.04.2 does not know about the existence of 15.04. So, load 14.04.2 and run this command

```
sudo update-grub
```

That should give a Grub boot menu with the 3 OS as boot entries. Watch the printout to confirm this.

Regards.

---

