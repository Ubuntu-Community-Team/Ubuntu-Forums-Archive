---
title: "Windows 7 with Ubuntu 15.10 not working"
date: 2015-11-29
forum: Installation &amp; Upgrades
---

### Post by sujoydc on 2015-11-29
I have looked at the list of issues in this forum before posting this. 
My issue is a little weird and I guess mostly my ignorance with both the operating systems.

I have installed Windows 7 freshly and then installed Ubuntu 15.10.
Windows (all primary partitions): 
System Partition : 100mb
C: 100gb 
D: 200gb
E: 400gb  (installed ubuntu here)

Now after installation it didn't prompt me to update the startup sequence. 
And when I start my laptop, it now starts with Windows 7 only and doesn't give me an option to choose. 

Please help.

---

### Post by yancek on 2015-11-29
In order to give you accurate advice, a lot more information will be needed.  The simplest way to get it is to go to the site below and download the boot repair script and burn it as a bootable image to a CD, then boot it and select the option to Create BootInfo Summary.  I would suggest reading through the page before doing this.  You will get some output and it will tell us a lot about your system so paste a link here so member can view it.

If windows 7 is booting and Ubuntu is not seen, then you didn't install the Ubuntu bootloader to the MBR.  A default windows system will not boot any Linux without manual user intervention.  The Ubuntu bootloader will do that.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by F35Blackbird on 2015-11-30
Go to "Advanced system settings" . I go like this:
.   Press the "Windows" and "Pause" keys.

On the left panel, click on "Advanced system settings" link.

On the System Properties, make sure that you are on the "Advanced" tab.

Under the "Startup and Recovery" section, click on the "Settings..."  button.

Make appropriate settings on this page, I would say the "check" the setting "Time to display list of operating systems" and set it to 5 seconds.

That is it.

Umar.

---

### Post by sujoydc on 2015-11-30
Hi Umar, 
Thanks for your reply. I have followed your steps and figured out that default operating system drop down shows only "Windows 7". 
So, which means whatever I have installed in the "E: 400gb" was not correct.
Going forward what should I do? Should I re-install?

---

### Post by kansasnoob on 2015-11-30
> Going forward what should I do? Should I re-install? 

No. First follow the advice in post #2:

[http://ubuntuforums.org/showthread.php?t=2304771&p=13399021#post13399021](http://ubuntuforums.org/showthread.php?t=2304771&p=13399021#post13399021)

Without looking at the bootinfo we'll just be guessing and may well make things worse instead of better.

---

### Post by sujoydc on 2015-12-01
Thanks guys for your inputs. 

I had copied the iso file into a usb drive using Universal USB Installer. 
But after I restart my computer it still loads Windows 7 and doesn't start the repair software. 
I followed these steps here [http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

I even tried to change my boot sequence by pointing to the USB drive. In that case it doesn't boot at all. 
It waits in the console saying 

SYSLINUX 4.07 EDD 2013-07025 Copyright (c) 1994-2013 H.Peter Anvin et al
Loading the boot file...
Failed to load the boot file
boot: _

---

### Post by kansasnoob on 2015-12-03
How did you install Ubuntu? Boot Repair can also be run from the Ubuntu live USB/DVD:

[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

I assume you used either a live USB or DVD to install Ubuntu?????

---

### Post by sujoydc on 2015-12-07
Hi, 
Thanks for the tips. I could run boot repair. 
Now, after that I can't login to windows. I didn't try ubuntu yet. 
This is the url: [http://paste2.org/65VaMJ1a](http://paste2.org/65VaMJ1a)

---

### Post by yancek on 2015-12-07
You will need to explain a little more in detail what is happening than "can't log in to windows".  Do you get a Grub boot menu?  How many options do you see for windows?  Have you tried booting Ubuntu?  Did it succeed?  I suggested a week ago after your first post that you select the option to "Create BootInfo summary" when running the boot repair script.  It seems you tried to do a repair based on the output of boot repair and now you have Grub installed on the MBR of the second drive, the one with xp.  Did you mean to do that?  Is that an install of xp or just an ntfs partition?  If you have multiple options for windows on the boot menu as shown in boot repair, the second one should be the one to use as that appears to be your system partition.  Have you set the BIOS to boot from sda, the first and larger drive.

---

### Post by sujoydc on 2015-12-08
Sorry about that. I guess I just followed that link and didn't re-read your steps. 
Now everything is working as expected. Last time it was taking too much time to boot to windows so I thought it was not working.
I again tried today and it's working now. 
Thanks a lot to you guys. I have learnt something new.

---

