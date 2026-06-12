---
title: "Feel like killing myself... grub rescue error after trying to dualboot"
date: 2015-09-26
forum: Installation &amp; Upgrades
---

### Post by jackywhlee on 2015-09-26
Hi folks.. I have spent the last 11 hours literally in front of my computer trying to fix one problem, but one comes after the next and after the next and I have never felt so depressed with a computer before, the last time being when my water cooler wasn't properly fitted on my motherboard, causing it to fry. 

So my problem right now is when I start my computer, I get this:

error: no such device: xxxxx
Enter rescue mode...
grub rescue>


First order of business, this is my Boot info summary, which I had obtained from running Boot Repair via a live USB Ubuntu: [http://paste.ubuntu.com/12576838/](http://paste.ubuntu.com/12576838/)

Background what I had done:

My computer had Windows installed on my SDD (sda) which I consider it as my main HDD. I had installed Ubuntu 15.04 on another HDD (sdc). After using Ubuntu for a few weeks for my coding course, I decided to make Ubuntu my main OS. I decided to first copy and paste Windows from sda onto sdb, then remove Ubuntu from sdc, then reinstall a fresh Ubuntu on sda. This would ideally result in my SDD being solely used for Ubuntu and sdb fully used for Windows.

However in my limited knowledge, I had deleted a ton of partitions including what I suspect the system boot partition, boot manager, and all that jazz. After copy pasting Windows via Gparted to another HDD, I stupidly deleted the original Windows (sda), which effectively killed my windows from booting.

I then proceeded to completely delete everything in sda, and installed Ubuntu onto it. Once booted onto the Ubuntu on sda, I used the Gparted to delete all the small partitions I found (I didn't know!) in sda, sdb, and sdc, and finally deleted the Ubuntu in which I had installed weeks ago.

I restarted my computer and BAM, grub rescue error.

I have tried many many things to fix it, but problems comes on top of one another. I can't even get do a fresh Windows anymore (all my partitions have a MMT or something) and before I attempt reinstalling Ubuntu for the 4th time, I really hope there is a method that can fix all this... 

Please, I am at my wits end. I still have 40 hours of javascript homework to do and my inexperience and lack of understanding with dualbooting is deteriorating my health...

---

### Post by Bucky Ball on 2015-09-26
Welcome. Your boot info shows you have four boot sectors on four drives. 

Please run Boot Repair again now and post the link after the repair.

---

### Post by jackywhlee on 2015-09-26
Hi, thanks for replying. I'm in the process of erasing Ubuntu of sda, with a few minutes remaining. I just ran Boot repair and it gave me the following error:

"GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again."

A little note: I don't mind reinstalling Ubuntu again for (4th time in progress), but I'd really, really, really like to recover my the Windows I cloned from sda (which is now located on sdb) if possible..

---

### Post by Bucky Ball on 2015-09-26
Let's stop for a minute and take a breath. :)

Boot from Ubuntu live media (USB/DVD)> 'Try Ubuntu'> Get to a desktop> Install Boot Repair using [these]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu") instructions> run the bootinfo script option and post the link here. Thanks.

Just wondering: Is there a reason you are having Win and Ubuntu installed on separate disks? OSs on the SSD is normal as that's the fastest. HDDs for storage, /swap, /home, etc.

If you are intending to dual-boot then you should be installing Windows first for a smoother ride in any case.

---

### Post by jackywhlee on 2015-09-26
Hey, I don't know what's wrong but my USB boot sticks no longer work!! I tried a Windows USB boot stick and an Ubuntu bootstick, but the computer boots directly to Ubuntu!! Problems one after another!! I can't run Boot Repair if I can't get into the tryUbuntu!

I have Win and Ubuntu on separate HDDs because my SSD doesn't have enough space for both OSs. I know there is 120GB on my SDD but I am saving the space to install video games since there is a massive performance upgrade when installing them onto SSD (especially mmos). Therefore I have opted to keep Windows separately on another HDD.

I felt it was smart to have Windows installed first, which is why I cloned my original Windows onto a different HDD, but after spending 5 hours trying to get it to boot, I decided to install Ubuntu onto my SSD since I was clueless with fixing Windows from disappearing on the boot menu (Windows loader, it kept pointing that my Windows was in sda when in fact, I had moved it to sdb). 

Now my entire computer won't even load anything besides Ubuntu....there's no more menus when I restart my computer...sigh

---

### Post by grahammechanical on 2015-09-26
Do not forget that with multiple drives the motherboard (BIOS) will have a squence as to which drive it will look at to find an OS to load.

Delete Ubuntu off of one drive but with the Grub boot loader code is still in the MBR of that drive. then when the motherboard looks in the MBR of that drive it will find Grub but Grub cannot find its configuration files becasue the files have been deleted. So, it enters Grub rescue mode.

Reinstall Ubuntu but if the BIOS is booting to another hard drive that had Ubuntu on it and the partitiojns had been deleted then you will stll get Grub rescue or Insert disk with OS on it. My advice?

Decide which is to be the main OS and which drive it is going to be on and decide which OS is going on what other drives. And install each OS one by one and disconnect the other drives each time. There is no need to delete partitions. A reinstall will format the drive anyway.

When all OS are installed in all drives, then connect them up, when you get into Ubuntu run. 

```
sudo update-grub
```

And the printout should show Grub detecting the other installs. And then set the BIOS to load the Ubuntu drive. When you restart you should get a Grub boot menu that gives you the options to load whatever OS you wish. 


Regards.

---

### Post by oldfred on 2015-09-26
Was your Windows on sda UEFI or BIOS?
Your sda drive is now gpt partitioned and Windows from gpt only boots with UEFI.
And Windows from MBR partitioning as you have on sdb only boots with BIOS. But you cannot copy a UEFI boot Windows to BIOS boot and have anything that works. 

You sdb drive shows one NTFS partition, but none of the Windows boot files.
Windows normally installs to two partitions, a 100MB boot partition and the main install with BIOS/MBR. With UEFI it has multiple required partitions. 

And with BIOS installs the 100MB boot partition is always on the drive set as default in BIOS, so even an install to sdb, may put boot partition on sda.

Almost always better just to keep Windows on sda. And install Ubuntu in same boot mode, UEFI or BIOS as Windows is installed to avoid boot issue. Ubuntu boots just fine from any drive or any partition.

       Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You show none of the above. Your winload.exe should be in the main Windows install. If that is the case and Boot-Repair's summary report just did not show it, then you may be able to repair it with a Windows repair flash drive. You need that to add both bootmgr & BCD to main install.

---

### Post by jackywhlee on 2015-09-26
My Windows on sda was UEFI. I cloned it to sdb and it no longer boots. I have apparently deleted the multiple partitions that existed anywhere across all my HDDs. Is there anyway to fix this?

What I want is to have Ubuntu installed on sda and Windows installed on sdb, sounds simple? But it sounds impossible to do so at this point.

Should I just go back to Windows and give up on Ubuntu? I can't even get Grub to boot up when I restart my computer. WIthout Grub, how can I even reinstall Windows? My computer boots DIRECTLY to Ubuntu, no matter what USB sticks I have plugged in. 

And is it not possible to load files on Ubuntu from other Hard disk? I can access files on other hard disks but when I try to use VMWare to load a Windows .iso from a different Hard disk, I couldn't even access that hard disk through the File manager gui. And I can't even link Dropbox to my dropbox folder on another hard disk.

Do I have to move every file I want to access onto my sda (Ubuntu OS) folder, while Windows can load files from cross-hard disks?

how can i get windows usb to load? i've given up trying to restore my cloned windows.

---

### Post by oldfred on 2015-09-26
If you truly cloned Windows from UEFI, it should be on a gpt partitioned drive? Or did you just try to copy one NTFS partition?

With UEFI hardware you have two boot choices for most flash drives, both Windows 8 or later and all current Ubuntu versions. One is clearly UEFI and one is not, or is CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

You really need to be consistent, or only boot in UEFI mode or only boot in BIOS mode.
And with Ubuntu drive can be gpt and be either UEFI or BIOS if you have correct supporting partitions.

Almost all UEFI systems seem to want to boot from the ESP - efi system partition on sda. Ubuntu/grub only installs to that even when I have tried to install Ubuntu to a gpt partitioned sdb drive with its own ESP. The only way to get it to use sdb's ESP, was to disconnect sda, so my sdb was seen as a sda during install. And then UEFI did not see it correctly.

Sometimes too many boots seem to confuse UEFI. You may have to totally shutdown or cold boot. And if a laptop remove battery.  With power off hold power switch for 10 sec or so to drain all power and then reboot into UEFI or one time boot key. If that does not work a total system reset may. Either short pins on motherboard (see your manual) or remove coin battery on mother board. That will reset all UEFI/BIOS settings to default, so you have to go back and reset to secure boot off, fast boot off, and turn on USB port booting and perhaps other settings. I must have had 10 settings in UEFI that were required or probably needed to change for system to fully work.

You may have turned secure boot on, or Windows did, And to boot USB ports, some systems need you to change UEFI settings to specifically allow that.

What motherboard, cpu & video system do you have?

---

### Post by jackywhlee on 2015-09-26
thread can be closed. i decided to go back to windows on my desktop by uninstalling ubuntu for the 5th time and reinstalling a fresh windows, which works perfectly fine.

i'll keep ubuntu on my laptop.

good riddance.

---

