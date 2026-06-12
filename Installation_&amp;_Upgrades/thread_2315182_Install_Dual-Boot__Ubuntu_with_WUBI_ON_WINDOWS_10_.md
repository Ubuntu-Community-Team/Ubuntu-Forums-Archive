---
title: "Install Dual-Boot  Ubuntu with WUBI ON WINDOWS 10 :("
date: 2016-02-26
forum: Installation &amp; Upgrades
---

### Post by halis3 on 2016-02-26
Hello guys i ve never use ubuntu before and 2 days ago I found a cd from somewhere where it s live cd of Ubuntu then I decide to install it to my system whics was windows 10.They were supposed to be Dual Boot, but when i turn on my computer it directly opens ubuntu and I cant see Windows 10 but I can see my files from ubuntu I dont know what to do but after some researches I think i suppossed to install to it with grub but i made it with WuBI what should i do to see windows 10 again Thanks for help... :(

---

### Post by yancek on 2016-02-26
Read the WubiGuide at the link below.  It doesn't work with windows 8 or newer, period.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If it is actually a CD and not a DVD, how old is it and what version of Ubuntu.  You should see this on the screen when you boot.
The Ubuntu installer usually has several installation options.  Which one did you choose?  You should see a manual option which is called "Something Else" and that is the best and safest method to use.
Was windows 10 pre-installed on the computer or was it an upgrade from an earlier windows version?
Boot either the installed Ubuntu or the DVD and open a terminal and run the two commands below consecutively.  Post the output here as it will contain useful information.

```
sudo fdisk -l
sudo parted -l
```

Lower Case Letter L in both commands.

---

### Post by halis3 on 2016-02-27
Hello thanks for reply. It says ubuntu 14.04.01 LTS and my desktop s path was 7,8 and 10.Yes I chose `something else` and i made partitions I think thats why i still have my windows files but I dont have windows boot manager or grub or whatever so it directly puts me in Ubuntu.Here is the screenshots of my Ubuntu Files (which are in the Windows) and the results of commands that you ask me to use
[ATTACH=CONFIG]267538[/ATTACH]

---

### Post by Bucky Ball on 2016-02-27
Welcome. STOP. Go Back, wrong way.

Forget Wubi. It is not supported here or by Canonical. Even though it is still included on the disk, do not install. You won't get far when you have problems as no-one uses it anymore and those that did have mostly forgetten, and most importantly, it WILL NOT WORK WITH WIN10 UEFI, or any UEFI, boot anyway.

In other words, dual-boot with Ubuntu and Windows 10. Wubi is long gone. Redundant. Forget it.

PS: Having said this it is, of course, up to you, but as mentioned, don't expect a lot of support, but if you go with Wubi, do expect a lot of what I've just said from other users.

---

### Post by halis3 on 2016-02-27
Yeah I know but the problem is I already installed it and i want to get rid of that and I dont know how to do that s actually my point I stucked in ubuntu couldnt reach windows in anyway. I wasnt aware of that it is outdated

---

### Post by halis3 on 2016-02-27
Guys I really need help because i need to get into Windows I have things to do.How to change my boot order or delete this ubuntu or whatever solution is :(

---

### Post by yancek on 2016-02-27
Did you read the link I posted earlier?  If you scroll down the page, it explains how to uninstall WUBI.

---

### Post by oldfred on 2016-02-27
Also with Windows 8 or later,it uses fast start up or always on hibernation. That is a work around as Windows could not speed up boot to be competitive. But if dual booting you have to turn that off.
       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

    
Grub cannot boot Windows that is hibernated or needs chkdsk. So you may have to temporarily reinstall the Windows boot loader. You can use your Windows repair disk which you should have as Boot-Repair can only do minor fixes to Windows. But one of minor fixes is a Windows type boot loader. 
So reinstall Windows boot loader, make sure fast start up is off. And then use Boot-Repair to run the full uninstall/reinstall of grub in its advanced options.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

    
Instructions on removing wubi are in these:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by QLee on 2016-02-27
Did everyone look closely at the screen shots posted in post 3.  halis3 shows an unistall-wubi.exe on one of the Windows partitions but partition 5&6 look more like a regular install. I've never used a wubi install but wouldn't it be totally contained inside Windows.  Maybe more than one type of install was attempted.    As usual oldfred has included links to documentation to cover whatever situation so halis3 can read about it all as  yancek is helping correct the problem.

---

### Post by Bucky Ball on 2016-02-27
> **halis3 said:**
> Yeah I know but the problem is I already installed it and i want to get rid of that and I dont know how to do that s actually my point I stucked in ubuntu couldnt reach windows in anyway. I wasnt aware of that it is outdated

Ah. My apologies. :|

[QUOTE=QLee]As usual oldfred has included links to documentation to cover whatever situation[/QUOTE]

Your first port of call. :)

---

### Post by grahammechanical on 2016-02-27
> wouldn't it be totally contained inside Windows.  Maybe more than one type of install was attempted.

I agree with you about this possibility. It was confusion about the actual situation that caused me to back out of this thread more than a dozen hours ago. That and having no idea how to fix a wubi install grub menu issue.

But how can the user run uninstall-wubi.exe if he/she cannot load Windows? If we assume that the Ubuntu that is loading an independent install and not a wubi install then this command might put Windows into the Grub boot loader.

```
sudo update-grub
```

Watch the printout. Does it list Windows bootloader as a detected OS?

Regards.

---

### Post by oldfred on 2016-02-27
Oldfred has good notes :) 

Wubi was designed as an easy way to use Ubuntu. And then Windows 7 systems used all 4 primary partitions, so for newer users that often did not even understand partitions, deleting & creating partitions was a big hump, just to get started.

I have somewhere in notes, .meierfra's post on installing wubi without Windows. He proved it was possible to just install wubi to a partition and boot with grub. .meierfra was one of the original creators or bootinfoscript which still is used by Boot-Repair's Summary Report.

One of the very few posters that knows wubi, hakuna_matata, has created a fork that works with UEFI/gpt. I cannot say I recommend it as I have not used it and with gpt it is not as difficult to create partitions.

---

### Post by hakuna_matata on 2016-03-07
> **oldfred said:**
> 
I have somewhere in notes, .meierfra's post on installing wubi without Windows. He proved it was possible to just install wubi to a partition and boot with grub. .meierfra was one of the original creators or bootinfoscript which still is used by Boot-Repair's Summary Report.
Wubi also installs GRUB2 to boot into Ubuntu, but the default boot loader sequence is Windows boot loader -> GRUB4DOS -> GRUB2. Of course, it is possible to use GRUB2 only but a typical Wubi user does not want to overwrite the "Windows" MBR with GRUB2.

So the solution of grahammechanical should work for a Wubi install, too.
 > **grahammechanical said:**
> If we assume that the Ubuntu that is  loading an independent install and not a wubi install then this command  might put Windows into the Grub boot loader.

```
sudo update-grub
```


IMHO [this picture]("http://ubuntuforums.org/attachment.php?attachmentid=267538") does not show a booted Wubi install. The ubuntu folder of a Wubi install is there but it is not mounted as **/host** 

Windows 10 is also not installed in UEFI mode. The partition table is **msdos** and not **gpt **and there is no EFI partition.

So no special Wubi help is needed and no special UEFI help. Maybe, meanwhile no help is needed at all. 

If somebody is interested in GRUB2 commands to boot into a Wubi install, here they are:
```

insmod ntfs
search -s -f -n /ubuntu/winboot/wubildr.cfg
configfile  /ubuntu/winboot/wubildr.cfg
```
If somebody is interested in a Wubi project, [here]("https://github.com/hakuna-m/wubiuefi/wiki") it is. Feel free to ask me.

---

