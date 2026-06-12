---
title: "Win 10 Ubuntu dual boot on ACER - cannot get USB boot"
date: 2015-08-29
forum: Installation &amp; Upgrades
---

### Post by hans12345 on 2015-08-29
I have been trying for some time to install Ubuntu in dual boot with a new ACER XC-605 running Win 10.

I have done a lot of reading around this subject on these forums and on AskUbuntu.

Mainly my approach has been to follow the approach in:
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html]("http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html")
with several variants.

Basically, use UEFI mode, Fastboot off, Secure mode both on and off (tried both).

What always happens is that the ACER will not boot from the Pendrive UUI USB with Ubuntu 15 (64-bit) on it. Yes, I have checked the USB on another PC and it is bootable.

(Incidentally I have seen the same problem on a Lenovo PC, but that is a question for another day)

I have seen OldFred's (what a great guy he is!) comments about having to have a supervisor PW on the BIOS, which I now have.

I have not yet found a way to make the USB trusted. This could be my problem.

The BIOS is marked as 2.15.2136, Acer Inc.

In the BIOS, under the boot options I have various choices to make:

- several options which I have set to make the boot priority USB then DVD then HD : it appears that setting this has no effect

- a block of choices about Disk drive priorities. The first is the HDD which is active and gives me a choice of 1st boot device being Windows boot manager or nothing. All the other choices for Optical disk and Removable Device are stub entries offering no alternatives. It seems that this block is dominant and gives a choice between booting from the HD with Windows Boot Mgr, or not booting at all.

- also I have a boot menu option which allows a choice between Windows Boot mgr or nothing. When I open this, I see a choice enabled/disabled

Please, some help on getting my ACER to accept the USB as a bootable device.

---

### Post by oldfred on 2015-08-29
I do not know Acer other than what others have posted.
But many UEFI have to also authorize/allow USB booting, particularly if Secure boot is on.
With supervisory password set do you get more settings to allow USB boot somewhere?

You may have found these already:
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

---

### Post by grahammechanical on 2015-08-29
This may have no relevance at all as I do not have access to a machine with a UEFI boot system. On my BIOS boot system motherboard setting boot priority does not cause the machine to boot from USB stick but with the USB stick plugged in the BIOS sees it as an external USB drive and I can choose between drives. But the USB stick does have to be plugged in at the time. It does not work as with a DVD drive where we can set the priority to look for an OS first on a DVD drive and if no OS found then look on a hard drive.

Regards.

---

### Post by jackyboy633 on 2015-08-29
Hello hans12345,

Would I be able to ask you what utility in I assume Windows you used to copy the Ubuntu files onto the flash drive. I only am asking this as I own a PC with a UEFI BIOS (Gigabyte motherboard), and it can be a little particular about how the USB stick is copied over - on mine, it will only accept sticks that use a certain kind of partitioning in UEFI mode, and sometimes, Universal USB installer doesn't seem to work too well. 

For me, I've found that a tool called Rufus gives me the best results, and 95% of the time, I can boot from the stick in UEFI mode. If you download it from [https://rufus.akeo.ie/](https://rufus.akeo.ie/) and open it, click on the icon with the picture of a disc next to where it says "FreeDOS", and find the Ubuntu ISO. Then, where it says "Partition scheme and target system type", click on one of the UEFI modes (not the BIOS+UEFI mode), then click "Start" at the bottom, making sure that the USB drive you are using is selected. 

I find this method gives me the best results when using from UEFI. This may not be applicable to your Acer machine, but it may help.

Kind regards,
Jackyboy633

---

### Post by hans12345 on 2015-08-30
Thanks all of you for your good ideas.

I cannot try them all at once, but I immediately tried the idea about trying different USB slots. It was easy, but did not work.

I will start with OldFred's suggestion:

[I]But many UEFI have to also authorize/allow USB booting, particularly if Secure boot is on.
With supervisory password set do you get more settings to allow USB boot somewhere?[/I]

According to other posts, I have to make the USB device trusted.

In the BIOS Setup, with supervisor PW I have a section called 'Authentication'

It has these entries:

System Boot state :  User - Greyed out
Secure Boot Mode state :  Enabled  - Greyed out
Secure Boot : Enabled
Secure Boot Mode : Standard
Default Key provisioning: Enabled - Greyed out

So only 2 to play with.

Secure boot I have tried both ways, no change, still will not boot from USB.

Secure boot mode can be changed to Custom.

When I do that, I get these new options:
- Default Key provisioning: Enabled
- Manage All Factory Keys : Greyed Out
- Install Default Secure Boot Keys

If I change Default Key provisioning to disabled, I get a new option to 'Clear Secure Boot Keys'. This looks scary. Should I try it?
The ' Install Default Secure Boot Keys' option seems redundant, all it does is changes the value for 'Default Key provisioning', which I can do directly.

Any ideas on how to make my USB device trusted?

---

### Post by oldfred on 2015-08-30
Do not mess with keys. Ubuntu uses the same key as Windows and will boot with secure boot on.
But you should be able to turn secure boot off, but have UEFI on. That is a Microsoft requirement at least thru Windows 8 systems.

Some users just have issue with certain tools to create flash drives, or which port used on system, or even brand of flash drive.

As jackyboy633 suggests I have seen several recommendations on rufus.

---

### Post by hans12345 on 2015-08-31
Wow - I did not believe it.

But I downloaded a new copy of 15.04 64 bit (AMD) on a new USB stick and made my bootable USB stick with Rufus.

Now, with Secure boot off, if I hit F12 in startup (for the boot menu which never worked before) it offers me the choice of Win Boot Mgr or the USB !

Magic.

Thanks to you all.

I am going to do further reading before proceeding. More to come.

---

### Post by oldfred on 2015-08-31
The links in my signature below have just about everything UEFI related you need. But many new users get overwhelmed as there is a lot of info.

Key points on installing.
Use Windows to shrink Windows NTFS partition and immediately reboot so it can run chkdsk.
Usually better with secure boot off in UEFI and if UEFI has fast boot turn it off.
Turn off fast start up in Windows which is always on hibernation.
Backups are essential, for Windows & all your data.

If Windows is not shown, do not proceed. Either hibernation still on, or chkdsk needed. And then auto install may overwrite Windows. And do not reinstall Windows with auto options, as there was a major bug which is only fixed in newest 14..04.3 & 15.04 versions.

Better to use Something Else but you have to understand partitioning a bit. Auto install options only create / (root) & swap with default sizes of some sort. I find it easier to partition in advance with gparted & then use Something to change/choose the partitions I created as /. Swap will be automatically found then. Often good to have either /home separate or create a shared NTFS data partition (cannot do this in installer). But Windows hibernation keeps data partition mounted also, so fast boot must still be off.

---

### Post by hans12345 on 2015-08-31
Thanks OldFred

All seems to be good so far. I follow the process on EveryDayLinux (mentioned earlier):
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html]("http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html")
 and now have Ubuntu installed.

Now I am at the critical point of 'Boot Repair'

I am told:

  Within the terminal window enter the following commands one by one.
  sudo add-apt-repository ppa:yannubuntu/boot-repair
  sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list"
  sudo apt-get update
  sudo apt-get install -y boot-repair && boot-repair

I just want to check that this advice is still current since this was written for Win 8.1 and not 10.

---

### Post by oldfred on 2015-08-31
With Acer and the need to set "trust" on grub/ubuntu boot files, you should not need Boot-Repair. Nothing is needed to be fixed.
I regularly run either Boot-Repair or which really is about the first third of Boot-Repair's Summary Report bootinfoscript which is a terminal bash file just to document system, but not to fix anything.

You do not have to change versions. It has been updated for all current Ubuntu versions.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I believe Boot-Repair is using the updated fork.

 Updated fork  as bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)

---

### Post by hans12345 on 2015-08-31
Hi OldFred

You note 'With Acer and the need to set "trust" on grub/ubuntu boot files, you should not need Boot-Repair.'

But I did not get anything trusted. I never had a 'trust' option.

Now, if I just boot normally, I arrive in Win 10, no choice.

So I'll try with boot repair.

---

### Post by oldfred on 2015-08-31
Boot-Repair cannot set the trust you require.

Several of the users posted that you only get the option to set trust when you have supervisor password set and it is buried pretty deep. I do not know details in Acer's UEFI, but several users have posted enough info that you should be able to follow how they did it.

One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

Another:
[http://ubuntuforums.org/showthread.php?t=2256083&page=2&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&page=2&p=13203044#post13203044)

---

### Post by hans12345 on 2015-08-31
My boot-repair is being help up for normal computing issues.

I am working on:

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list"
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

Firstly, the file name has changed from trusty to vivid. OK.

But now I cannot get through to launchpad.net so the apt-get fails.

I'll try again tomorrow. Unless someone has a good way to get boo-repair by another route?

---

### Post by oldfred on 2015-08-31
You do not need to do the sed name change. See post #10.

And if you have added it you need to undo that.

---

### Post by hans12345 on 2015-09-01
Firstly OldFred, I really appreciate the time that you are spending helping me with this problem.
Second, I am sometimes working on the problem and I have not seen your latest posts. Please do not think I am ignoring them.
Third, even with your help, this is very complicated for me, with many alternative steps that I can take at any moment.

Status now:
I can boot into Ubuntu by keeping the USB with Ubuntu plugged in.
I ran boot repair (with the wrong sed command that you tell me I should not have used) and made just the Boot repair summary.
See:
[http://paste.ubuntu.com/12243999/]("http://paste.ubuntu.com/12243999/")


At the bottom it says:
=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda9, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file
=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda (1000GB) disk!
If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\...\grub*.efi

Should I proceed with this recommended repair?


Thanks again

---

### Post by oldfred on 2015-09-01
Please review the two threads posted above. They explain how they set supervisory password with then opened more settings, and they had to drill down and set trust on these efi boot files.
/EFI/ubuntu/MokManager.efi 
/EFI/ubuntu/grubx64.efi 
/EFI/ubuntu/shimx64.efi

Boot-Repair's suggested fix for for many other systems. Do not know if it would work with Acer or not.
But then you have to boot into Windows & it reboots into Ubuntu.

---

### Post by hans12345 on 2015-09-01
> **oldfred said:**
> Please review the two threads posted above. 

OK will do. 

I will investigate the option with Secure Boot on.

> 
They explain how they set supervisory password with then opened more settings, and they had to drill down and set trust on these efi boot files.

I believe I have exhausted this option - but I will look again.

> 
/EFI/ubuntu/MokManager.efi 
/EFI/ubuntu/grubx64.efi 
/EFI/ubuntu/shimx64.efi

Boot-Repair's suggested fix for for many other systems. Do not know if it would work with Acer or not.
But then you have to boot into Windows & it reboots into Ubuntu.

I will back off the boot-repair path for the time being.

I have a time problem, and probably will not be able to return to this issue for another 10 days.

---

### Post by hans12345 on 2015-09-13
I do not know how, but Dual Boot Win 10 / Ubuntu seems to be working.

If I want Win 10 (rarely), I hit F12 in startup (I have earlier set the boot menu, using F12, in the BIOS) which gives me one choice only, Win Boot Manager, and I get Win 10.

Otherwise I just let it start normally, and it sends out a warning that I am booting in insecure mode, then first GRUB and then Ubuntu 15.04 starts.

I was working at the same time on the same dual boot problem with a Lenovo (not yet solved) and I not certain which steps led to this success. But here are a few notes.

BIOS is ACER 2.15.1236
This BIOS does not allow the possibility to make devices trusted, so I did not do that.

Fastboot off.
Secure Boot disabled.
Rufus program used to create bootable Ubuntu USB. Pendrive did not work for me.

I did not run Boot-repair.
I followed USB advice on this site and made certain that I was using a USB 2 port, not a dual USB 2 and 3.

Thanks to everyone that made suggestions and/or gave advice, especially OldFred.

---

