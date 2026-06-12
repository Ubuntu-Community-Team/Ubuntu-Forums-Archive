---
title: "Windows doesn't show up if I boot. Solved"
date: 2019-11-03
forum: Installation &amp; Upgrades
---

### Post by lazar07 on 2019-11-03
So i had Windows 10 installed but needed Linux for school so I decided to install it too(ubuntu 18.04 LTS). I did some research on the net and when I was brave enough i tried it: I set up a bootable USB-Disk and so on and everything worked.
But Ubuntu didnt detect Windows so I clicked on the option "something other" and made myself a partition. I have 2 drives: 1 3TB HardDrive where all of my files are and a 500 GB SSD with windows. I split the 500 GB into 2 partitions and chose "/" as an option because i got an "no  root device" error if i didnt. I installed it
and everything and I can access Ubuntu. But here is the problem:

Ubuntu autostarts: I can't see Grub or anything. Sure, i spammed ESC but when i got in grub i only had 4 options: Ubuntu; Advanced Ubuntu; Memtest; and something with Memtest too

i read some other posts about this problem and i found the command "sudo uptade-grub" but it didnt work.

Im completely new to Ubuntu and Linux and don't know what I am doing but i need Windows asap.
I hope this community is friendly and can help me. If you need information from me like something like idk:


Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1023999   1021952   499M Windows recovery environment
/dev/sda2    1024000   1226751    202752    99M EFI System
/dev/sda3    1226752   1259519     32768    16M Microsoft reserved
/dev/sda4    1259520 491763711 490504192 233,9G Microsoft basic data
/dev/sda5  491763712 976771071 485007360 231,3G Linux filesystem


or

Device          Start        End    Sectors   Size Type
/dev/sdb1          34     262177     262144   128M Microsoft reserved
/dev/sdb2      264192 3812532223 3812268032   1,8T Microsoft basic data
/dev/sdb3  3812532224 5860530175 2047997952 976,6G Microsoft basic data



Hope I will get clear answers to fix my problem

---

### Post by CatKiller on 2019-11-03
So, I have two bits of bad news for you.

14.04 is no longer supported. Support ran out in April. 16.04 and 18.04 are still supported.

Windows 10 doesn't shut down properly, it simply hibernates to mask its boot-up time. This leaves its partitions in a dirty state. Ubuntu won't touch those dirty partitions, since any change to them would destroy your Windows install. There is an option to make Windows shut down properly - disabling Fast Startup in Windows - but Windows silently turns it on again with updates. With Windows shut down properly one can adjust its partitions as required, and their bootloaders can coexist in the EFI System Partition. I suspect it's too late for *that* Windows install in any case.

---

### Post by uRock on 2019-11-03
Did you create a Windows system repair disk and backups?

---

### Post by oldfred on 2019-11-03
If newer hardware with Windows 10 in UEFI boot mode better to use latest LTS long term support version of Ubuntu. Only use even newer 9 month support version if hardware is brand new, to have very latest drivers.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Be sure to boot install media in UEFI boot mode, since Windows is UEFI.
More details on UEFI installs in  link in my signature below.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by lazar07 on 2019-11-03
sorry got something wrong, will change it. I got 18.04.

---

### Post by lazar07 on 2019-11-03
I did nothing with windows before I installed Linux. No backup, no repair disk

---

### Post by lazar07 on 2019-11-03
@olfred

I actually got Ubuntu 18.04 LTS but got something mixed up in my mind. I'm really sorry.

I have read all the fast startup links. But my question is: What will it do for me? Will it help me to be able to use both Systems again?

In my BIOS I read that my Computer uses UEFI+Legacy. And I don't know what Ubuntu is doing; just installed the ISO file and used Rufus.
So now you are telling me that I should check if Windows got Uefi and if Ubuntu got UEFI and change both to the same, right?

---

### Post by CatKiller on 2019-11-03
> **lazar07 said:**
> I did nothing with windows before I installed Linux. No backup, no repair disk

That is unfortunate. At least, from your description, you haven't touched the 3 TB drive "where all your files are." You should back those up before you do anything else.

Then it's probably a reinstall of Windows, then turning off Fast Startup, followed by a reinstall of Ubuntu. Windows doesn't play nice if you install it second.

A Windows install disc may have a utility to repair your installation without having to reinstall, but I wouldn't know about that.

---

### Post by lazar07 on 2019-11-03
So, if I unplug my 3TB drive it's save, right? Sorry if I'm asking so much but I'm really nervous and want this to be working in the end...
Should i delete everything from my SSD? How am I able to do this? Some gentlleman, already sent something about that Fast Startup but can someone explain why I have to do it?
Do I have to do anything differently than before or does the FastStartup fix everything for me? TY a lot btw (to everyone who replied <3)

---

### Post by CatKiller on 2019-11-03
If you've backed up the data on the other drive, and disconnected it, it will be safe. Data that isn't backed up isn't backed up.

If you've blown away your Windows install because Windows hid it from the Ubuntu installer, which seems to be the case, nothing will fix that for you.

Disabling Fast Startup is so that you don't do it again.

With Fast Startup disabled, the Ubuntu installer will be able to see your (new) Windows install, and you'll be able to resize your partitions accordingly.

You want to use UEFI for both Windows and Ubuntu. That means turning off "Legacy," or "Compatibility Support Module," or however it's labelled in your setup. The old BIOS and the new UEFI don't mix-and-match very well.

---

### Post by lazar07 on 2019-11-03
I am in Linux right now and if I go to Files, I can go to the second partition where all of my Windows files are located. Am i not able to delete everything manually and then deinstall Ubuntu with the deinstaller and then deleting the partitions. Maybe some sort of cleanup
program and then im good to go? Getting my windows boot stick and installing windows, turning of fast startup, getting a new partition, getting ubuntu, plugging my harddrive in and boom I'm ready to go.

Another question: Am i able to use the data and files on my 3tb harddrive? Because its labeled "other locations" if i go into my files.
("Other Locations" is also where i can go into my first partition for windows..)

---

### Post by lazar07 on 2019-11-03
Am I not able to delete the files manually? I am in Ubuntu right now, went to files --> Other locations and I see my Windows partition... Who is going to stop me from deleting all this?

And then: Deleting Ubuntu with some Ubuntu deinstaller, cleaning the ssd with a cleanup program or idk, getting windows running, disabling startup, getting ubuntu running, plugging in my 3tb harddrive and im ready to go?

And am i able to use my data from my 3tb harddrive because it is listed in "Other locations" ?

Edit: Already wrote that sorry

---

### Post by CatKiller on 2019-11-03
You can use the files on your data partition, sure, especially if you've backed them up. Ubuntu is OK at reading and writing to Windows filesystems like NTFS, it just can't do maintenance things like defragmentation that those filesystems need over time, or repairing them when they break themselves.

If you're able to see your Windows install's files, then it might potentially be possible to repair it with some Windows utility. It's possible that, because you're trying to boot it in BIOS mode rather than UEFI mode, it's simply looking in the wrong place for the bootloader.

However, it's also possible that the files you're looking at are from a recovery partition, which wouldn't have been mounted, and so wouldn't have been marked as dirty, rather than from your Windows install. We can't really tell you what you're looking at.

Both the Windows installer and the Ubuntu installer have the facility to add and remove partitions. Manually deleting individual files would be an unnecessary step.

Operating Systems don't have an uninstaller; you simply install a different operating system.

---

### Post by lazar07 on 2019-11-03
So I will get my windows boot stick and just overwrite my old windows and then do the same with ubuntu.
I have looked everything through, on my Windows Partition arent that many programs that are important (only things like drivers and some games).
Except the Fast StartUp I install windows as I did in the past and then ubuntu?

---

### Post by CatKiller on 2019-11-03
> **lazar07 said:**
> Except the Fast StartUp I install windows as I did in the past and then ubuntu?

Yep.

Things to be aware of:

You'll want to be using UEFI and not Legacy.

 It *is* possible to make Secure Boot work, but it's a pain, so you'll probably want to disable that.

OEM installs of Windows stick the drive in RAID and need a driver update before it will work in non-RAID. I don't know if that's the case when you install it yourself.

Since you have no OS and you're mucking about in Setup anyway, you might as well check to see if there's a BIOS update available. Some significant bugs have been fixed with BIOS updates.

---

### Post by lazar07 on 2019-11-03
1. Before Installing Ubuntu, I will set it to UEFI in the bios.
2. I don't know what SecureBoot is, don't know if I had it. I'll just let it as it is.
3. So what should I do? It worked last year but I have lost the key to a high percentage, but I will buy a new key for Windows. I can use a bootStick more than one time, right?
4. So before I install Ubuntu I will go into my BIOS and search for some option called Bios Update?

---

### Post by CatKiller on 2019-11-03
> **lazar07 said:**
> 3. So what should I do? It worked last year but I have lost the key to a high percentage, but I will buy a new key for Windows. I can use a bootStick more than one time, right? 

I don't really know much about Windows licensing, but I understand that the licence is distinct from the install media. As long as you have a valid key for each machine you should be able to use the same media for each. You may potentially have a copy of your old key somewhere in your computer's documentation. 

> 4. So before I install Ubuntu I will go into my BIOS and search for some option called Bios Update?

You'd get a BIOS update from the website of your motherboard's manufacturer. You stick the file on a USB drive and select Update from within the BIOS.

The downside is that it might confuse an existing OS install, and you might need to run through the settings since they'll be reset to defaults. The first is no longer an issue for you, and you're doing the second anyway, so now is as good a time as any.

---

### Post by lazar07 on 2019-11-03
Yeah then... I will start working.
I won't write for some time because I need to install everything and all but once I've got Windows I will write and then I will continue with Ubuntu.
Ty very much...See ya later

---

### Post by lazar07 on 2019-11-03
I got an error which i didnt think of...
How can I change the boot order in Ubuntu. I can't start UEFI and i don't find anything useful in GRUB. (I need to change it to USB)
ty

---

### Post by CatKiller on 2019-11-03
Most systems will have a key that you can press to bring up the boot menu: one of the F keys normally. You can check your documentation for which key that is for your machine.

If you're using UEFI rather than BIOS you can also use ```
sudo systemctl reboot --firmware-setup
``` from Ubuntu to reboot into your machine's setup.

---

### Post by oldfred on 2019-11-03
What brand/model system?

If Windows was pre-installed the Windows license is in the UEFI. So if you reinstall in UEFI mode, it is using your system's license.

UEFI systems have 3 boot modes. UEFI Secure Boot, UEFI (without Secure Boot) and CSM.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

UEFI Secure Boot provides some protection to boot process, but is mostly marketing by a company that has historically has many virus, but boot virus are very rare. Main boot virus with old BIOS was from Sony to implement DRM to prevent you from playing unlicensed Sony music.

---

### Post by lazar07 on 2019-11-07
I got everything thank you very much. Everything is working

---

