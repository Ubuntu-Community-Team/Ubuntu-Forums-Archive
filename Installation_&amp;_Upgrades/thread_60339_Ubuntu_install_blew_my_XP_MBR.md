---
title: "Ubuntu install blew my XP MBR"
date: 2005-08-27
forum: Installation &amp; Upgrades
---

### Post by John Kinney on 2005-08-27
My effort to install Ubuntu dual booting with Win XP on a Compaq Presario 2300 laptop (with no floppy drive) went well right up until the install CD failed to find something it needed  and bombed out trying to install a "base system".  The attempted install appears to have munged my master boot record and I can't find any way to repair it without a floppy drive to boot from.  The data on the XP partition appears unharmed and can be reached with various linux live cds.

I used the Microsoft "Rescue Console" cd that came with the laptop, but to no avail.   The CD has some typical MS blackbox tools for repairing the boot sector and boot record, but who knows if they actually did anything.  The laptop still refuses to reboot XP, messaging me "error loading operating system."  

Before I give up and reformat the disk, does anybody here have suggestions to share?  I've read most of the messages here (and many elsewhere), but so far nothing has helped.

Thanks,  John Kinney

---

### Post by sto6ma9ch on 2005-08-27
Can you boot into your new Ubuntu installation? If so, you may want to check the GRUB menu file. Issue this command:
```
sudo gedit /boot/grub/menu.lst
```
At the end of this file you should have at least the three Ubuntu entries plus one Windows entry (provided it's in there). Take a look at the *root (hdx,x)* line for Windows carefully. The *(hdx* part should point to the hard drive that Windows is on. The *,x)* part should be the partition number on that drive (the first partition would be zero, the second would be one, ...). Once you've corrected it, save the file and reinstall GRUB with
```
grub-install
``` 
Does that

---

### Post by slada on 2005-08-27
I had a similar issue happen after uninstalling a different linux distro.  I was able to fix my MBR by gettting a windows 98 boot disk and running a tool to fix the MBR.

The process is described toward the bottom of this page:

[http://www.ntfs.com/mbr-damaged.htm](http://www.ntfs.com/mbr-damaged.htm)

---

### Post by swamytk on 2005-08-27
I had the same problem while installing this ubuntu 5.04 system. I have two hdd,, one for Windows XP and another one for Ubuntu. By mistake I was end up with the problem you mentioned. Try the following if it is appropriate to you also.

It was cool. Boot the system with Windows XP CD, select REPAIR option. It will show "Windows XP Pro".. asking you to select. You select it, you will get prompt. type "fixmbr". That will do.

Now your Windows XP will be default Boot OS. To change it, boot with Ubuntu CD. Go to install option (wait.. we are not reinstalling) upto parition screen. Once Partition screen comes up, go to the 4th terminal (i forgot the exact terminal number), change the root as your root device. Configure you Windows XP in grub.conf. run grub-install with your harddisk as argument.

Hope this will help you!

---

### Post by John Kinney on 2005-08-28
[QUOTE=sto6ma9ch]Can you boot into your new Ubuntu installation? If so, you may want to check the GRUB menu file...[/QUOTE]

Unfortunately, the new ubuntu installation won't boot, either.

Regards, John Kinney

---

### Post by John Kinney on 2005-08-28
[QUOTE=slada]I had a similar issue happen after uninstalling a different linux distro.  I was able to fix my MBR by gettting a windows 98 boot disk and running a tool to fix the MBR.[/QUOTE]

Thanks, I'm back up and running. Yay!

I dug around in some old dead file boxes until I found a 5-year-old Win 98 system CDROM disk.  Wiped the dust off that sucker, put it in the CD drive and rebooted. 

Message appeared asking if I wanted to run setup or go to a dos prompt with or without CDROM support.  I selected dos prompt with CDROM support and an A: prompt appeared.  

I tried to change to C: drive, but got an error message.  Ran fdisk from the A: prompt, which loaded normally.  I displayed partition info and got a message that there was no active (bootable) partition.  I set the NTFS partition to active.  

On an afterthought, since ubuntu wasn't booting anyway, I decided to delete the ubuntu partitions in case they were munged.  The "/" partition displayed as FAT something, which didn't sound right, and the swap partition displayed as "unknown" type, which sounded like Microsoft marketing strategy.

Afterward, I exited fdisk and tried to switch to C: drive, again unsuccessful.  I ran fdisk /mbr from the A: prompt and got a new prompt, no error.  I gave the three finger salute and told the computer to boot up from the harddisk, not the CD.

I was rewarded with the little XP flag showing up and what appears to be an operating system with no loss of function or data.  

I do so appreciate the suggestion and the useful link.  Thank you very much.

I've done some poking around since and discovered that the original problem with the ubuntu base system may be associated with an ubuntu installation CDROM downloaded and burned on a Windows system.  I'm going to boot the live CD and see if I can dl and burn the ubuntu install disk using that.  I don't have a CD burner on my office system.

If anything weird happens, I'll keep y'all posted -- or beg for more help...  Onward!

Regards, John Kinney

---

