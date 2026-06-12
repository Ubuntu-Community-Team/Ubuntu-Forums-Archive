---
title: "Trying to install Ubuntu srver Dual Boot with Windows 10"
date: 2019-06-18
forum: Installation &amp; Upgrades
---

### Post by ctylersills on 2019-06-18
Okay, Ive run into the biggest problems with installing a copy of Ubuntu Server and Windows 10. The very few questions on the matter say that this is possible and that server has no differences with desktop as far as booting, so it is the same. However my problems I ran into started when I installed Server and already had windows 10 installed. I didn't realize it because it never prompted me but when I did the format in setup, for what I thought was just left over disk space on my HDD it turns out the setup completely erased the HDD. Now I think I´ve figured out why after creating a windows 10 Home installation USB. When I try to re-setup Windows 10 Home in the spot that got erased for windows, It tells me that windows cannot put an installation on the disk because the type of formatting is GPT. So am I understanding this right in saying that, basically, If you only have on HDD, you cant Dual Boot. Or is it possible to re-setup Ubuntu Server as MBR, or someone please tell me what I need to do here. I'm so confused as to why It seems like all the dual booting information/instructions are in forums, not on the official Ubuntu support. And like I said, little if anything mentions how to do dual boot with Ubuntu Server. Please help

---

### Post by oldfred on 2019-06-18
How you boot install media, UEFI or BIOS is how it installs for both Windows & Ubuntu. 
But if you boot in one mode & drive is configured for other mode, installer will complain.

Windows only boots from gpt partitioned drives with UEFI.
Windows only boots from MBR partitioned drives with BIOS.
If you change partitioning, you typically erase drive.

If system is UEFI, generally better to use UEFI with gpt partitioning.
Microsoft has required vendors to use UEFI/gpt since Windows 8 released in 2012.

Some server installs use LVM which is a full drive install by default & erases everything else on drive. You can use LVM manually to dual boot but lose some of the advantages of LVM. Better to stay with gpt & standard partitions.

---

### Post by ctylersills on 2019-06-19
Right and i def understand that part of it but the thing of it is... this is an older laptop, BIOS is the only choice... So I dont see what Im doing wrong here shouldntthe setups like automatically detect this. I saw the LVM option in the Ubuntu Server setup and decided STRONGLY against it as I knew the extra features would require a complete format of the drive, after doing some research. As I said, originally, the system already had windows 10 installed, but when I went to install Ubuntu server, I didn't pick LVM, but when I installed it acted like there was no other operating systems installed, and just basically showed the entire disk as free space, Ive now realized. I just thought at the time it wouldn't be able to detect Windows as an operating sytstem, you know, I know... kinda stupid, but I´ve never done this before? What should I do in this case since UEFI is clearly NOT an option with this machine. how do I go about installing a Dual Boot system, or is this going to be impossible. Basically, just so you can all understand what  I'm doing here, I'm starting a company that I will need to run a server or maybe multiple as we expand, and, from what Ive seen, Linux is the way to go with the type of optimization and control that I'm going to want over it (Im one of those micro-managers, and I&#7743; the only employee out of 3 that knows anything about software tech/IT on my level lol). So I'm just trying to get this setup on a machine that I can play around with the CLI, and server features on something that isn't actually going to cost my company for me to learn. Basically I want this to be my ¨learning server machine¨. BUT... I also HAVE TO HAVE windows as I am a programmer working on a project that I need VS 2019, and the hardware I have would be very difficult to A. even get drivers for, but also, B. program to work with the pos system I am working on with ANY Linux Distro. So, please can anyone explain to me , what do I need to do on this system. Restart the server setup and try something else, just give up on server on this machine and reinstall Windows? Is what I am trying to do even possible since this is a BIOS-only machine? from what I read I thought this made the dual boot scenario more possible. I'm just SOOOOOOOOOO confused I seem to be getting incomplete information. But beyond everything, I DEFINITELY want to familiarize myself with the system and learn how to use an Ubuntu server, rather than just going with a windows server option for my company just because I know Windows better. Surely the smartest group of tech people in the world (linux distro/Ubuntu users) can help me out. Ive got faith in you guys and finally want to join you, but Im not having much luck here.

---

### Post by yancek on 2019-06-19
A major reason for the Ubuntu or other Linux installer not to recognize and installed windows 10 is because the windows default is to leave it hibernated and no Linux OS will mount a hibernated partition.  YOu might review the Ubuntu documentation below on dual booting with windows 10.  Also has info on coverting from GPT to Legacy/BIOS.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-06-19
Ubuntu can use gpt partitioning with BIOS systems, I used it since 2010 on old BIOS system.
But Windows cannot use gpt.
So if your system is before 2012 and BIOS only, you need to convert drive back to MBR. Probably best to erase Ubuntu and install Windows.  Then make sure Windows fast start up is off. Use Windows to make unallocated space for Ubuntu and install Ubuntu.

If not familiar with server you can install desktop and add any server apps you need. Its just most server installs may not even have a gui and are command line only. Some suggest newer users install server and add a minimal gui, but not a desktop & all its apps. Older info:
[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

Many with servers also use a virtual install, but that may need a bit newer system. And then graphics are more limited.

See this by TheFu:
       [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)
[https://ubuntuforums.org/showthread.php?t=2395081](https://ubuntuforums.org/showthread.php?t=2395081)

---

### Post by ctylersills on 2019-06-27
> **oldfred said:**
> Ubuntu can use gpt partitioning with BIOS systems, I used it since 2010 on old BIOS system.
But Windows cannot use gpt.
So if your system is before 2012 and BIOS only, you need to convert drive back to MBR. Probably best to erase Ubuntu and install Windows.  Then make sure Windows fast start up is off. Use Windows to make unallocated space for Ubuntu and install Ubuntu.

If not familiar with server you can install desktop and add any server apps you need. Its just most server installs may not even have a gui and are command line only. Some suggest newer users install server and add a minimal gui, but not a desktop & all its apps. Older info:
[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

Many with servers also use a virtual install, but that may need a bit newer system. And then graphics are more limited.

See this by TheFu:
       [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)
[https://ubuntuforums.org/showthread.php?t=2395081](https://ubuntuforums.org/showthread.php?t=2395081)

Okay, so which should i start with? Windows, or Ubuntu server? How do I go about making sure that it is changed to MBR on ubuntu setup. One of the answers said that ubuntu didnt recognize it beause of hibernate, or ¨&#7719;ybrid mode¨, however I turned off both hibernate and fast startup in the power options of windows 10 before I installed Ubuntu Server. Beyond that, I dont understand how hybrid mode could cause the partition to appear as if it wasnt there I dont see how that could happen. Im still confused about how to make sure both setups will use MBR. As far as the server goes, yes, I know that server installs no gui. Had Windows not got erased thats exactly how I want it so I can get used to CLI and not having a GUI in a server enviroment. I know that for a dedicated server guis A. Install a bunch of junk that I wouldnt need, and B. tend to hog resources.

---

### Post by yancek on 2019-06-27
If there is currently nothing useful on the drive, start with windows as it would be a convoluted process to even attempt to boot Ubuntu from windows.  Make sure your disk are NOT GPT which you can do by running the command:  sudo parted -l  which will show the Partition table type.  Make sure it is NOT gpt.   You can use gparted to create a new partition table if you need to.

Boot your windows install media and install windows.  When you have finished, reboot as many times as necesssary to get windows functioning in a basic manner.  When you are sure windows is working, you need to create unallocated space on which to install Ubuntu so go into windows Disk Management and shrink the windows partition.  When that finishes, reboot to test.  You might want to run chkdsk in windows also.  You should then be able to install Ubuntu.  Make sure you use the default for the bootloader install to the MBR so that it will boot Ubuntu and windows.

---

