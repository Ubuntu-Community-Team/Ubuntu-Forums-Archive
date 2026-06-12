---
title: "Cannot see Ubuntu boot option in BIOS"
date: 2015-05-01
forum: Installation &amp; Upgrades
---

### Post by Zakarumit on 2015-05-01
Hi.
I have decided to try installing Ubuntu on my home computer. I have got 3 HDDs:
1 - Win7 installation and software
2 - NTFS HDD with windows data
3 - separate HDD for Ubuntu

I installed Ubuntu on HDD 3. I have choosen this HDD also as Ubuntu boot loader location. The point was to not write any Ubuntu stuff to windows HDDs and vice versa. I thought I will simply choose which bootloader to use in BIOS (Win7 or Ubuntu). Unfortunately, after I finished installation, I cannot see any Ubuntu boot option in BIOS.
Any ideas?

---

### Post by Mark Phelps on 2015-05-01
The BIOS loads long before any operating system, so you won't see any OS choices in the BIOS.

Hopefully, when you installed Ubuntu you had the other drives disconnected, otherwise, GRUB could have been installed to the wrong drive by default.

To test this, disconnect all but the Ubuntu drive and see if you can now boot into Ubuntu.

If that works, do the following:
1) Reconnect the other drives but continue to boot from the Ubuntu drive
2) Open a terminal in Ubuntu and enter "sudo update-grub".  This will regenerate the GRUB configuration file and add entries.  You should see if find the Windows loader in the process.
3) When you reboot, you will see a GRUB menu (not a BIOS menu) with entries for Ubuntu and Windows loader.

---

### Post by grahammechanical on 2015-05-01
What we can do in BIOS is select which hard drive to boot from. If your machine is booting from the drive with Windows on it then you will not see any option to load Ubuntu. But if you set the machine to boot from the drive with Ubuntu on it then you should see the Grub boot menu with options for Ubuntu and Windows boot loader.

Regards.

---

### Post by Zakarumit on 2015-05-01
When installing Ubuntu, all drives were connected. I have used the Something else mode of installation and picked the empty drive for boot loader installation.
I know I wont see installed OS in Bios or something like that, but there are simple boot order options: DVD/RW, SSD (with my win7) and when I connected USB before turning on the computer, I can also boot from USB. (thats how I installed Ubuntu - created installation USB, inserted and switched boot priority in BIOS to boot from it) The whole problem is I expected here to see one additional option after the installation, and that should be in my opinion to boot from the HDD with Ubuntu. I just dont see this option.
Could you please tell me, whats wrong with my ideas? I cannot test connecting/disconnecting drives right now, as I am gone for weekend. I kinda also dont want to, as I find very annoying to open my PC and connect/disconnect cables just because of installing OS :-[
Whole point was to have 2 completely independent OS on 2 separate HDDs and selecting which one to boot from via priority list in BIOS.

---

### Post by oldfred on 2015-05-01
Run the Summary report just to see if grub correctly installed to the MBR of your Ubuntu drive. BIOS will not show it as a boot option unless boot code is in MBR.
Do not run any autofix options with Boot-Repair. That just installs grub to the MBR of every drive, so Ubuntu will boot regardless of which drive in BIOS is boot drive. But you correctly want to keep the Windows boot loader on the Windows drive. If grub is not in MBR of Ubuntu drive, you have to use advanced options of Boot-Repair to choose operating system and then choose drive to install boot loader.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Zakarumit on 2015-05-09
Hi. Thanks for the advice.
I have managed to create bootinfo:
[http://paste.ubuntu.com/11042062/](http://paste.ubuntu.com/11042062/)
Unfortunately, I am not really sure what to do now. I do not understand all the information it provides, but it seems to me like Ubuntu is installed properly and theres the grub installed as well, pointing on Ubuntu. Can you please take a look and tell me what to do, i.e. exact setting I need to use in boot-repair to fix the issue and not change anything on my Windows HDDs?
Ps. sdd in the bootinfo is live USB.

---

### Post by oldfred on 2015-05-09
You have Windows installed on sda booting with BIOS on a MBR drive. 
And Ubuntu on sdc booting with BIOS on a gpt partitioned drive.

With gpt partitioning and booting in BIOS mode, you must have a small 1 or 2MB unformatted partition with the bios_grub flag if using gparted to create it. If using gdisk to create it the the code is ef02.
Grub does not correctly install unless you have the bios_grub partition when using gpt.

Then you can use Boot-Repair to reinstall grub to sdc. Do not run auto fix as that will install grub to all drives which you do not want. Use advanced mode.

---

### Post by Zakarumit on 2015-05-09
Ok, thanks. Considering the Ubuntu installation is pretty much empty, I can definitelly wipe it out and install again. How can I choose not to use GPT and use MBR instead? I did not use any program for formatting, neither gparted or gdisk.When installing windows on sda, it was automatic and ended up with this MBR version. On the other hand, when I installed Ubuntu on sdc, there wasnt a single question about MBR/GPT partitioning and I ended up with GPT I seem cannot boot from :-[

---

### Post by oldfred on 2015-05-09
If drive is unpartitioned an somewhat over 1TB Ubuntu defaults to gpt. 
Gpt is required for drives over 2TiB.

But I normally suggest gpt for any system that has a separate drive for Linux and will not have Windows on it. Windows only boots from gpt with UEFI. Ubuntu does not care, but requires correct partitions.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by Zakarumit on 2015-05-13
So yesterday I tried as you suggested:
-used gparted on liveUSB to create bios_grub partition
-run Boot-Repair on sdc to reinstall grub
-ended up hanging on something like "Install last kernel sdc(ins)" for 30 minutes or so, then aborted (figured its not working, as it said it will také few minutes and last longer than whole Ubuntu installation)

After this I just tried to use gparted again to wipe out all partitions on sdc and create new ones and later use them to install Ubuntu. I managed to unmount all the parts of sdc except one, which I was unable to unmount and format, gparted claiming its being used by other program or something like that (no idea why, as I was running everything from live USB)

After this I just started Ubuntu install again and wiped out all partitions on sdc in the installation manager and created new ones:
-bios_grub (5 MB)
- / (60 GB)
- /home (200 GB)
- swap (10 GB)
...and installed Ubuntu. Everything went fine, was asked to restart computer at the end. After restart, situation still the same same - BIOS doesnt allow me to boot from the drive with Ubuntu. 
Honestly, I really have no idea why its so easy to create bootable Ubuntu USB and run it, use it etc, and its so hard to install Ubuntu on HDD and use it. USB stick appears in BIOS after I turn computer with the USB connected and I simply choose to boot from it before Windows. On the other hand, when I install Ubuntu on separate HDD, it still does not appear bootable :-[
Any ideas?

---

### Post by oldfred on 2015-05-13
Rerun Boot-Repair's summary report so we can see what is where now.

---

### Post by Vladlenin5000 on 2015-05-13
Apparently the one step missing is making BIOS boot from the drive where the bootloader was installed and per your instructions. Different motherboard manufacturers use different solutions but usually there's a second step for multiple drives which is select the HDD/SSD order priority after selecting the boot order with the internal drive (HDD or SSD). If the BIOS doesn't offer such possibility then you have to move the HDD to the first position, ie, SATA0 (when it doesn't allow redefining of the boot order the default is to boot HDDs/SSDs in the same order as they are physically connected to the board.

Posting info about the hardware is a good idea.

---

### Post by Zakarumit on 2015-05-14
Hello again.
So yesterday, I did following:
-Used gparted on live USB to change partition table on the HDD from GPT to MBR (in gparted its called MS-DOS partition table as far as I understand)
-Used instructions from [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) for partitioning: 1GB /boot, 10 GB swap and 250 GB /.
-Installed Ubuntu from live USB
...the reason was I think its just too much hassle to work with GPT. Why use it, when I dont really need it at all? Anyway, after installation, result was still the same-on the main screen in BIOS with boot priorities, I was only able to see my Kingston SSD (Windows), DVD/RW drive and that was all. I tried to dig much deeper in advanced setting in BIOS and saw fast boot option. Remembered I read somewhere it could help to disable it, so I did. I also managed to find some pretty well hidden screen also called boot priorities, which suprisingly included all my drives, USB ports, DVD/RW etc. I Switched my Windows SSD to last position and rebooted. Suprisingly, saw first a violet screen, then black screen and then booted into Ubuntu.
To sum it up, I guess most likely I just wasnt using the correct BIOS option for boot priorities, for which I am sorry. I have no idea why the boot priorities are on different screen in my BIOS and why each of the screens shows something else. It could be also because of the change to MBR or bacause I turned off fast boot. Anyway, I hope my problem is now solved, thanks everyone for help.

---

### Post by oldfred on 2015-05-14
Glad you got it working.

The newer UEFI systems seem to have a lot more settings that you have to change.

---

### Post by Vladlenin5000 on 2015-05-15
> **oldfred said:**
> The newer UEFI systems seem to have a lot more settings that you have to change.

A lot more is an understatement. 
However, the option required in this case was already present in most old BIOS but often only visible when multiple drives were detected. I'm typing right now on one of those systems and although I didn't used it (all OSs are in the disk connected to SATA0 - sda - and so is the bootloader; the other two have data only) but could if I had to. It was already present in many PATA only motherboards also where the typical pair of IDE connectors could fit up to 4 drives.

---

