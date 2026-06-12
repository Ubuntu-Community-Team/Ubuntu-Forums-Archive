---
title: "Working on installing Ubuntu dual boot with Windows 10"
date: 2019-07-29
forum: Installation &amp; Upgrades
---

### Post by wolfrose on 2019-07-29
Hello,

I tried to install Ubuntu directly with flash drive boot, but it didn't work, it just freeze at the start of Ubuntu install process.

Then after some search I think the problem is that my system has to be in UEFI mode, where my laptop is in Legacy mode.

So I read this link and it says that the disk shouldn't have more than 3 partitions, in step 3:
[https://www.maketecheasier.com/convert-legacy-bios-uefi-windows10/](https://www.maketecheasier.com/convert-legacy-bios-uefi-windows10/)


Is that true? Also do I have to convert the disk to GPT without losing data?

---

### Post by oldfred on 2019-07-29
Converting Windows from Legacy/BIOS to UEFI is not particularly easy. 

Windows only boots in BIOS mode from MBR partitioned drive with the 4 primary partition limit. But you can convert one primary to an extended partition and have an unlimited number of logical partitions.

Windows only boots in UEFI mode from gpt partitioned drive. No limit (actually 128) on partitions.

Microsoft has required vendors to install Windows in UEFI mode since Windows 8 released in 2012. So newer hardware is UEFI and Windows should be UEFI if on UEFI hardware. Windows 7 usually was BIOS, so upgrades from Windows 7 are often BIOS/MBR configuration.

You really need to install Ubuntu in same boot mode as Windows, and must if on same drive.

What brand/model system? What video card/chip?

Post this from Ubuntu live installer in live mode terminal:
sudo parted -l

---

### Post by wolfrose on 2019-07-29
> **oldfred said:**
> Converting Windows from Legacy/BIOS to UEFI is not particularly easy.

I think so, I'm now AOMEI to merge partitions. Then I have to convert system to UEFI, then to GPT. Then I would try installing Ubuntu.


> Windows only boots in BIOS mode from MBR partitioned drive with the 4 primary partition limit. But you can convert one primary to an extended partition and have an unlimited number of logical partitions.

Oh yeah thanks for the info, that explains why the first partitions are in dark blue and marked as primary partition and rest and light blue marked as logical partition.

But now I have only 3 partitions in dark blue and the 4th one in light blue. I don't know why maybe because I'm using AOMEI to merge the 4th with the 5th one.


> Windows only boots in UEFI mode from gpt partitioned drive. No limit (actually 128) on partitions.
That's nice but I'm doing all that for installing Ubuntu.

Is my procedure of minimizing the disk partitions and converting to UEFI mode, then to GPT to install Ubuntu right? Or it's not necessary?


> Microsoft has required vendors to install Windows in UEFI mode since Windows 8 released in 2012. So newer hardware is UEFI and Windows should be UEFI if on UEFI hardware. 

I checked the setting in the boot menu and it's "Legacy". My laptop is Dell 7559 inspiron.

> Windows 7 usually was BIOS, so upgrades from Windows 7 are often BIOS/MBR configuration.

My laptop didn't came with any HDD, only one SSD m.2 but I remember it didn't have any OS inside ..  I guess.


> You really need to install Ubuntu in same boot mode as Windows, and must if on same drive.

What you mean of this exactly ? Same drive, you mean same HDD? I have only one HDD in my laptop.

Boot mode, my current boot mode is Legacy and I tried to install Ubuntu with current settings but it didn't work, the Ubuntu install process freezes up after the initial installation guide steps.

> What brand/model system? What video card/chip?

[IMG]https://1drv.ms/u/s!Ag9h-wTCXh8w1W1U-yX0JNmR_34a[/IMG] [IMG]https://1drv.ms/u/s!Ag9h-wTCXh8w1W1U-yX0JNmR_34a[/IMG][IMG]https://i.ibb.co/Wn0mdSp/sysinfo.png[/IMG]

> Post this from Ubuntu live installer in live mode terminal:
sudo parted -l

I don't know how to do this.

---

### Post by oldfred on 2019-07-29
That is an UEFI system and should have Windows in UEFI boot mode on it.

You need to use Ubuntu live installer and start it in live mode, not the install mode.
Then you can open a terminal and run the command. 

       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Default boot setting of Legacy or UEFI is only for the installed system. If UEFI secure boot is off, and allow USB boot is on, then you should have two options to boot a Ubuntu live installer. One will clearly be UEFI:flash and other just flash which is then the BIOS/Legacy/CSM mode. The flash may be the name or label of the flash drive, my system calls it UEFI: PMAP and PMAP.

Some other Dell 7000 series, but Dell issues are often common across many models. Bigger differnces if Intel or AMD based systems.
       DELL Inspiron 15 7577 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)
Post installation issues Ubuntu 18.04-Dell inspiron 7559
[https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559](https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559)
Dell Inspiron 7566
[https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359)

---

### Post by wolfrose on 2019-07-30
> **oldfred said:**
> That is an UEFI system and should have Windows in UEFI boot mode on it.

Yep! You're right. Now I converted the boot system to UEFI without problems.

But I converted it back to Legacy, and them to UEFI again trying to install Ubuntu with newer methods.
> 
You need to use Ubuntu live installer and start it in live mode, not the install mode.
Then you can open a terminal and run the command. 

Do you mean virtual box?

       > Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Yep that's correct, now I understood what you mean. But still both won't work, there's a freeze of the installation process.

Maybe I have to convert the HDD to GPT.


> Default boot setting of Legacy or UEFI is only for the installed system. If UEFI secure boot is off, and allow USB boot is on, then you should have two options to boot a Ubuntu live installer. One will clearly be UEFI:flash and other just flash which is then the BIOS/Legacy/CSM mode. The flash may be the name or label of the flash drive, my system calls it UEFI: PMAP and PMAP.

I converted the system to UEFI with secure boot off. But it didn't work.

When I booted from UEFI with USB Ubuntu installer, the same Ubuntu install menu of the Legacy mode but GUI layout different.

In Legacy mode the GUI is purple, in UEFI it's pure black with small font size. Both freeze up during the first steps of installation.

> Some other Dell 7000 series, but Dell issues are often common across many models. Bigger differnces if Intel or AMD based systems.
       DELL Inspiron 15 7577 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)
Post installation issues Ubuntu 18.04-Dell inspiron 7559
[https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559](https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559)
Dell Inspiron 7566
[https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359)

Tried their trick of removing and reconnecting the USB during the initial installation, but didn't work.

---

### Post by oldfred on 2019-07-30
Terminal is Control-ALT-T
You then can copy & paste command into terminal & copy & paste output back here.
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

You never mentioned video card/chip?
Link posted above on your model says it has nVidia and explains the steps in detail.
If nVidia you probably need nomodeset. Some versions of Ubuntu will auto install correct nVidia driver if you check install proprietary drivers. Otherwise with first boot, you have to also use nomodeset  and then install nVidia driver from Ubuntu repository.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

      [/URL]
 If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 
    [URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

### Post by wolfrose on 2019-07-30
> **oldfred said:**
> Terminal is Control-ALT-T
You then can copy & paste command into terminal & copy & paste output back here.
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)


Which terminal ? I couldn't log to any Ubuntu installation window that is stable to work with! I started to think it's a difficult system to install in dual boot with another system.

When I converted the system to UEFI, the UEFI is then programmed to run the USB directly. Even when I disconnected the USB, and did a restart, the UEFI started to search for the USB right away. I thought it would switch to the HDD automatically.

These are the windows I got with UEFI and USB installation.



> You never mentioned video card/chip?
Link posted above on your model says it has nVidia and explains the steps in detail.
If nVidia you probably need nomodeset. Some versions of Ubuntu will auto install correct nVidia driver if you check install proprietary drivers. Otherwise with first boot, you have to also use nomodeset  and then install nVidia driver from Ubuntu repository.

Yep I read that thread, and thought even if it's a discrete component, why would Ubuntu search for it in the installation process, but maybe Ubuntu is different than Windows, as I think I have to install the necessary drivers during installation, is it correct?


I thought those threads are complicated and they have different situations than I do, and maybe my problem is simple and it's about converting the HDD to GPT which I can't do right now, why? I don't know.

       > At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
      [/URL]

Is NOMODESET a tool that would help me to do what exactly ?

Also what are "both BIOS liveCD & grub first boot", in my situation where I want to boot from USB, which one would I get ?


 > If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 
    
I don't know what to do! I don't know if the GPU is the problem in the installation process, or the HDD is still in MBR or what exactly ! The problem is that the issue that is causing the Ubuntu install is something specific, it could be the HDD must be in GPT or it could be something else as I want to know what is the problem so I can try in solving it.

---

### Post by wolfrose on 2019-07-30
Found this thread:
[https://askubuntu.com/questions/760116/grub-failing-to-install-installation-crashes](https://askubuntu.com/questions/760116/grub-failing-to-install-installation-crashes)

As you said, live mode.

---

### Post by oldfred on 2019-07-30
Please do not post screen shots in line. You can attach with Forum's advanced Editor and the paperclip icon.
       [http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098) 

There are hundreds of threads on Dell installs and most are very similar.

The Ubuntu installer is both a live bootable system that runs Ubuntu. Often used to test if Ubuntu works on your system before install.  And then you then can use it to install or if needed to repair your system. Windows has you create a separate flash drive for doing repairs. Which of course you did do as well as do full backups of your system. My Dell wanted Dell backkup, Windows backup & then I did a full image backup when I first booted it in Windows.

It looks like your system needs nVidia driver. That normally is not installed directly, you have to install it after you boot into your install. And to boot live installer or your install you may need the nomodeset boot parameter. 

Are you not installing in UEFI boot mode? You should be with an UEFI system.

Can you still boot Ubuntu live installer in live mode?
If so run this, so we can see details. Only post link, not full report.
       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    

But you are booting to a grub command line, which means grub/Ubuntu was not correctly installed, or you have an old grub from previous install that is not for new install and then does not work. May just be which boot mode you are booting in UEFI or BIOS.

System came with Windows installed in UEFI boot mode and therefore drive must be gpt partitioned.
Windows only boots in UEFI mode from gpt partitioned drives.

---

### Post by wolfrose on 2019-08-01
OK, I have an idea and I thought about it before but I thought I won't have all Linux Ubuntu features for heavy use.

My whole goal of installing Ubuntu is to test gaming and my gamepads specifically, because I have a problem in Windows and couldn't solve the problem. So I thought I would test the games and the controller on Ubuntu.

The idea is to test everything on virtualbox, so my question now is, can I play games and test all Ubuntu features on virtualbox?

It would be a lot of work to install Ubuntu in dual boot with Windows. Installing Ubuntu should've been done from the start of working with a new or fresh HDD so that I can set everything up easily; like, changing boot to UEFI and changing HDD format to GPT. It's difficult and sensitive process of moving all my files to the C drive to convert it to GPT.

I think I can cut this long trip and run virtualbox, I should've done that in the first place, but after going through all failed Ubuntu installation attempts, I started to like virtual box more.

Found some titles on YouTube about gaming on virtualbox, hope I can work with it. Even to test any small game just to test the gamepad problem.

---

### Post by oldfred on 2019-08-01
Do not know virtualbox.

It was my understanding that gamers did not use virtual installs as it is a bit slower.

---

### Post by cruzer001 on 2019-08-01
Fred is right, vBox is not a good choice for gamers.  Just too slow for the high end games.  You may want to have a look at LXC/LXD or Docker.
[https://discuss.linuxcontainers.org/t/lxc-game-server/3661](https://discuss.linuxcontainers.org/t/lxc-game-server/3661)

[https://www.docker.com/why-docker](https://www.docker.com/why-docker)

Easier solution is just to dual boot.  Want to take snapshots?  Could use LVM for that.
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

---

### Post by wolfrose on 2019-08-01
> **oldfred said:**
> Do not know virtualbox.

It was my understanding that gamers did not use virtual installs as it is a bit slower.

Yep! It would be much slower, even running Linux from boot is also slower than Windows.


> **cruzer001 said:**
> Fred is right, vBox is not a good choice for gamers.  Just too slow for the high end games.  You may want to have a look at LXC/LXD or Docker.
[https://discuss.linuxcontainers.org/t/lxc-game-server/3661](https://discuss.linuxcontainers.org/t/lxc-game-server/3661)

[https://www.docker.com/why-docker](https://www.docker.com/why-docker)

Easier solution is just to dual boot.  Want to take snapshots?  Could use LVM for that.
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

I think I have to stop trying to install Ubuntu, the reason is because I want to test a problem with my gamepad in Windows, and thought about testing it in Linux.

But as I'm facing difficulties in installing Ubuntu and it's not installing, because my disk is MBR I guess, I tried to change the boot system to UEFI but it didn't work.

My question is it necessary that my system is UEFI and the disk much be GPT to install Ubuntu?

If I change the boot mode to UEFI and my disk is in MBR, then the install freeze up every time, during the install steps, but it's different each time, some times, it freeze up in the 1st step some times in the 2nd .. etc.

---

### Post by wolfrose on 2019-08-01
I'm trying virtualbox now, it should be enough for only testing the gamepad.

---

### Post by oldfred on 2019-08-01
With two drives you can have one system in BIOS/MBR and another in UEFI/gpt. But may have to change UEFI settings to correctly boot.
But with one drive must have both systems in same boot mode & partitioning type.

Since most new hardware is UEFI, often better to use UEFI. 
Originally Microsoft did not want to let developers create drivers for BIOS with new hardware, so everyone had to update to Windows 8 & UEFI. But so many large users had/have Windows 7, that drivers were still developed for BIOS boot.

---

### Post by wolfrose on 2019-08-02
That's interesting.

But now; for example, if I changed my boot mode to UEFI, with USB disconnected, the system search for the USB and not booting directly from the HDD ! And I have to restart and go to boot options and select the HDD !

Also, do you mean my gamepad issue is caused by the fact I'm booting from the old bios mode and not from UEFI?

---

### Post by oldfred on 2019-08-02
Do not know about gamepad issue, but may be worth testing to see if driver is different in an UEFI install.
But if installing in UEFI mode better to install to a separate drive. And Ubuntu's Ubiquity installer only wants to install grub2's boot loader to first drive's ESP. Or easiest to disconnect first drive if installing to second drive. May  be able to logically disconnect in UEFI settings rather than physically.

---

### Post by wolfrose on 2019-08-02
Yep ! didn't quite understand what you mean but I should be when I go through something similar or exact to what you described.

I actually deleted an option for the boot manage in UEFI mode, now I can't control the boot in UEFI. I don't know how to add a boot option.

It's my mistake, I deleted the only boot option that was available. Now there's no option, so UEFI can't find any order to boot for. So I switched back to Legacy mode.

[ATTACH=CONFIG]283729[/ATTACH][ATTACH=CONFIG]283730[/ATTACH]

---

