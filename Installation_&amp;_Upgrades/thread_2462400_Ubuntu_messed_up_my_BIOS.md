---
title: "Ubuntu messed up my BIOS"
date: 2021-05-20
forum: Installation &amp; Upgrades
---

### Post by happydog500 on 2021-05-20
I put in a fresh HD in my Lenovo Laptop and installed the latest Ubuntu LTS. I had a few problems like it wouldn't shut down on it's own, or won't go into the BIOS or boot menu. After a day I remembered I had to do some conferences on Zoom. I hadn't set everything up yet, so I pulled the drive and put back in my Windows HD with all my stuff on it. 

  Even with my windows HD in, I can't get into the BIOS or Boot menu. 

  What can I do to get it back the way it was before? 
 
 I got into the boot menu, changed it to boot from DVD-RW as #1, then HD as #2. Installed Ubuntu LTS, Rebooted, wouldn't shut down so I did manually. Booted up (F2) to get back into the boot order to change it to HD as the first and it booted into linux ignoring my F commands for start up or BIOS.   

Put the HD with Windows and it still bypasses the boot order or getting into the BIOS. 

I've had this laptop for 10 years so no it's not delete to get in. It shows up at the bottom of the screen F2 for boot order or F12 for BIOS. Even Lenovo says it. Even so I tried delete anyways. 

 What can I do to fix this? What happened? 

Thank you,

---

### Post by TheFu on 2021-05-20
It is probably a BIOS problem.  Linux doesn't touch the BIOS.

I have a problem where it takes 4-10 reboots to get into the BIOS. The motherboard is from a company known to be slightly hostile towards non-Windows OSes. If I attempt to get any support from the that company, they assume Windows and if I say anything about not using Windows, they say "we don't support non-Windows installs" and close the issue.

The BIOS wasn't always this way.  It was my first UEFI BIOS, but I run Linux in the Legacy mode - personal choice. I always assumed it was the hardware that had the issue.  I should check if there is a BIOS update next reboot. I seldom power off/reboot my systems. This problem machine only gets rebooted every 2-4 weeks.  The BIOS is AMI vFA from 12/01/2014. There's a 2015 version available. I've set a reminder to install it during the next maintenance window.

---

### Post by happydog500 on 2021-05-20
When I booted Windows the first time, I got to boot order. It listed;

1.Ubuntu
2.HD
3.DVD-RW

This was in Windows. 

Install Linux, can't get into BIOS. BIOS changes. Boot order name changes. Install Windows, still problem. What happened? Installed Linux.

---

### Post by TheFu on 2021-05-20
> **happydog500 said:**
> When I booted Windows the first time, I got to boot order. It listed;

1.Ubuntu
2.HD
3.DVD-RW

This was in Windows. 

Install Linux, can't get into BIOS. BIOS changes. Boot order name changes. Install Windows, still problem. What happened? Installed Linux.

That isn't what I've seen, but again, I don't have UEFI.  There are other tools to manage UEFI stuff.  I think **efibootmgr** is one, but I've never used it.  

So, I connected to a laptop that DOES use EFI booting and ran 
```
$ sudo efibootmgr 
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0001,0002,0003
Boot0000* ubuntu
Boot0001* UEFI:CD/DVD Drive
Boot0002* UEFI:Removable Device
Boot0003* UEFI:Network Device
```
I don't have any dual boot systems. I prefer to use virtual machines when that is desired. Made the switch to VMs around 2006 and completely switched, even my main desktop, around 2010.

There is a manpage for that tool. It appears to be non-trivial.
```
DESCRIPTION
       efibootmgr is a userspace application used to modify the  Intel  Extensible  Firmware
       Interface  (EFI) Boot Manager.  This application can create and destroy boot entries,
       change the boot order, change the next running boot option, and more.
```

There might be a GUI tool to manage boot stuff in EFI systems.  Google found this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
There is a warning about what happens with people have Windows installed in EFI mode, then install Ubuntu in Legacy-BIOS mode. That is bad. Could that have happened?

There are a few threads here about UEFI/EFI installs. Could be worth a search.

---

### Post by grahammechanical on 2021-05-20
There is something that I do not understand. We set the boot order in the BIOS/UEFI and that instructs the BIOS/UEFI to search for an operating system on the first drive in the list. If it does not find one it will search the next drive in the list. And so on.

With only one hard drive in the machine the OS on that drive should be loading without you needing to call up the UEFI settings utility or the boot order by pressing F2 or F12. So, why are you doing that?

With two drives in the machine you would need to use boot order to select the drive if Windows was installed in UEFI mode and Ubuntu installed in legacy mode. When both Windows and Ubuntu are installed in UEFI mode and with both drives in the machine you can set the boot order to Ubuntu and when it loads you then open a terminal and type

```
sudo update-grub
```

The printout should show both Ubuntu and Windows detected. Then, when you switch on the machine you should get the Grub boot menu where you can select either Windows or Ubuntu. No need to set the boot order or to enter the UEFI settings utility.

Regards

---

### Post by ajgreeny on 2021-05-21
Is Ubuntu and grub the method you are using to boot or have you used **bcdedit** as discussed at [https://forums.linuxmint.com/viewtopic.php?t=300030?](https://forums.linuxmint.com/viewtopic.php?t=300030?)

I can not comment further as I have not used Windows for 16 years so **bcdedit** is nothing more than a name to me, but as TheFu has said, Linux doesn't touch the BIOS so this must be something else.

---

### Post by tea for one on 2021-05-21
> **happydog500 said:**
>  I got into the boot menu, changed it to boot from DVD-RW as #1, then HD as #2. Installed Ubuntu LTS, Rebooted, wouldn't shut down so I did manually. Booted up (F2) to get back into the boot order to change it to HD as the first and it booted into linux ignoring my F commands for start up or BIOS.   

Put the HD with Windows and it still bypasses the boot order or getting into the BIOS. 

I've had this laptop for 10 years so no it's not delete to get in. It shows up at the bottom of the screen F2 for boot order or F12 for BIOS. Even Lenovo says it. Even so I tried delete anyways. 

 What can I do to fix this? What happened? 

Thank you,

If you are in an Ubuntu session, you can reach the UEFI set-up with:-
```
sudo systemctl reboot --firmware-setup

```
From Windows, have a look at this:-
[https://www.windowscentral.com/how-enter-uefi-bios-windows-10-pcs](https://www.windowscentral.com/how-enter-uefi-bios-windows-10-pcs)

---

### Post by anneranch on 2021-05-21
I hate "...I have same problem ..." posts.

Here is mine - little harsh for people who do not like term "shell-shock"  but that is what it is 



BTW 
sudo systemctl reboot --firmware-setup
created endless string of " asking for cache data failed " 

My 21.04 "upgrade" destroyed my multiboot Ubuntu OS , no Windows, only system. 
I ended up with physically removing my main UEFI "load OS " HDD !!!
(UEFI recovered nicely Kudos ) 

My best uneducated guess is 21.04 fouled my UEFI firmware (??) 
and added garbage to "grub". 

"way to go Idaho..."

---

### Post by ipv2 on 2021-05-23
> **TheFu said:**
> Linux doesn't touch the BIOS.

not sure what exactly you mean by **touch**.

every linux distro that i have installed on my system has added the name of the operating system to the bios which shows up in the list of boot devices.

even after the disk has been wiped clean & the linux distro uninstalled the name of the linux operating system still stays there,

the only way to remove the name / names of the linux operating system from the list of boot devices is to reset the bios.

i can 100% confirm that the following linux distros add the name of the linux operating system to the bios :

alma, arch, clear, debian, endeavour, fedora, manjaro, neon & ubuntu.

so yes linux does **touch** the bios.

windows has never done that, not in xp, vista, 7, 8, & 10.

---

### Post by yancek on 2021-05-23
>  so yes linux does **touch** the bios.


I think what the other member meant in that post is that Linux/Ubuntu will not make the changes the OP is talking about, preventing access to the BIOS which is correct.  Of course, Linux/Ubuntu puts entries in the BIOS firmware on EFI installs or it would not be able to boot.  This is an old (10 years) computer per the OP so likely isn't an EFI install.  Best option would have been to run boot rrepair to get some acxtual information on the system.

---

### Post by TheFu on 2021-05-23
> **ipv2 said:**
> not sure what exactly you mean by **touch**.

every linux distro that i have installed on my system has added the name of the operating system to the bios which shows up in the list of boot devices.
That isn't the BIOS. That just a boot list. On legacy systems, grub shows that list. In Window it is whatever the Windows boot manager is. I haven't dual booting in years.  Virtualization is much easier, safer, and doesn't end up with MSFT / Linux fighting over which system controls booting.  I understand that about once a year in the MSFT-world, they update the boot program or just reinstall it, ignoring Linux.  

> **ipv2 said:**
> even after the disk has been wiped clean & the linux distro uninstalled the name of the linux operating system still stays there,
I've never seen that, unless I didn't remove grub - or just run **update-grub**.  Only 1 of my systems uses UEFI to boot and I never see any boot menu with it even when booting from SDHC or USB flash media.  It has other "funky boot" stuff, since it is a laptop and uses 2FA, yubikey, and whole disk encryption at the same time.

> **ipv2 said:**
> the only way to remove the name / names of the linux operating system from the list of boot devices is to reset the bios. Huh?  There is a boot editor for UEFI or just run **sudo update-grub**.

> **ipv2 said:**
> i can 100% confirm that the following linux distros add the name of the linux operating system to the bios :
alma, arch, clear, debian, endeavour, fedora, manjaro, neon & ubuntu.
I honestly don't consider UEFI as "BIOS", since it is stored on the disk in the FAT32 partition with ESP label.  BIOS is in the firmware of the motherboard - the stuff that tells it to look on the default boot device for a FAT32 partition ... with an ESP label for how to boot.
BTW, a raspberry pi doesn't really have any BIOS. It is quite minimal, yet we can still setup multi-boot on a microSD device that will list 10 distros to boot.

> **ipv2 said:**
> so yes linux does **touch** the bios.
I disagree, but think we are just disagreeing about terms and perspective.

> **ipv2 said:**
> windows has never done that, not in xp, vista, 7, 8, & 10.
No, Windows has done much worse.  Install Linux onto a system, then install any Windows as dual boot.  Let us know how that works out.

Someday, it would be nice if Windows didn't wipe Linux. Alas, I'll never know, since my Windows use is dropping off all the time. Down to just 1 copy inside a virtual machine to deal with tax and financial software these days.

---

### Post by happydog500 on 2021-05-27
Very sorry I couldn't reply to anything. I was in the hospital. 

I never dual booted. Right now I have a Windows computer that won't let me into the BIOS. Someone asked, why do you want to get into the BIOS? Because that's the way it came. I want to get my computer back the way it worked before I installed Linux. 

 The ssd drive I'm using is only 120GB. Drive is pretty full so that's why I didn't dual boot but put another complete HD in. That HD is getting pretty old so i'm just trying to get computer back the way it was. I posted in the Linux forums because using Linux is what I did to have this problem. 

 When I installed Linux, the computer wouldn't shut down. Had to hold the power button to get it to shut off. When I put the Windows drive back in, it doesn't shut down now.

  Thought about pulling the cmos battery out. If it doesn't fix it, i won't be able to boot. When I installed the SSD, I switched to AHCI. If I reset it and it doesn't allow me to get in, it will switch back to IDE. I don't believe the computer will boot. 

A person on the internet has a computer similar to mine. He unplugs the battery from a white connector. Mine will not disconnect. I've almost wrecked the plug trying to get it off.   

Didn't use Linux for several years so I forgot a lot of things. Wanted to get back into it but now on this machine just want to get it back to the way it was. 

Thank you,
 Chris

---

### Post by tea for one on 2021-05-28
> **happydog500 said:**
> I never dual booted. Right now I have a Windows computer that won't let me into the BIOS.

Did you not try the suggestion in the link I mentioned in post no. 7?

---

### Post by ipv2 on 2021-05-29
> **yancek said:**
> Of course, Linux/Ubuntu puts entries in the BIOS firmware on EFI installs or it would not be able to boot.

thank you for the confirmation.

---

### Post by yancek on 2021-05-29
>  That isn't the BIOS. That just a boot list. 

Yes it is.  The BIOS firmware has listings for each and any OS installed.  That is how the system knows which OS to select from the EFI partition which has separate directories for each system.  In addition to having separate listings in the BIOS firmware for devices, the Boot Options menu has listings for each OS.  If there is a LInux Install with Grub, it will also (hopefully) have a listing of menuentries for each OS installed.

>  even after the disk has been wiped clean & the linux distro  uninstalled the name of the linux operating system still stays there,

That's standard and expected behavior on an EFI system.  You format or reinstall over the previous partition but haven't removed the EFI entry which is not on the partition on which the OS is installed but is on the EFI partition which you do not want to delete.  You can use efibootmgr to delete any entry for a system you no longer have so you don't see it when you access the firmware.  If you run update-grub I would not expect to see the removed systems in the Grub menu..

---

### Post by happydog500 on 2021-06-02
> **tea for one said:**
> Did you not try the suggestion in the link I mentioned in post no. 7?

 Thank you for the suggestion. No, I can not do that. When I go to troubleshooting, I don't have UEFI listed as a choice.

---

### Post by tea for one on 2021-06-03
Shot in the dark:-

Remove your HDD and all USB attached devices so that no operating system is available.
Power on and try the Lenovo dedicated key to reach the firmware set-up pages.

---

### Post by happydog500 on 2021-06-07
I found the reply's are going in my junk folder. Sorry it takes me so long, didn't think I had responses.

I just accidentally hit, "report as phishing" so not sure I'll get anymore. I will try suggestion and post back. 

Thanks for the reply

---

