---
title: "GRUB 2 Problems after upgrading to Ubuntu 14.04 LTS with Windows 8 Installed"
date: 2014-08-30
forum: Installation &amp; Upgrades
---

### Post by qais2 on 2014-08-30
Hello there ,
I have Windows 8 installed and had  Ubuntu 12.04 LTS along side with it had to manually change from UEFI to  CSM boot manually from Bios every time i had to change between Windows 8  to Ubuntu , recently i updated to Ubuntu 14.04 LTS and ever since i  just cant boot to Ubuntu properly , i have tried reinstalling from  scratch but nothing worked , i followed this
 "[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)" 
and ended up with error after following Boot-Repair tool and got this
[http://paste2.org/COsHgnUg](http://paste2.org/COsHgnUg)


Could you please if its not too much to ask look into this ?  any further details information will be provided asap , thanks in  advance.


Regards[IMG]https://ssl.gstatic.com/ui/v1/icons/mail/images/cleardot.gif[/IMG]

[COLOR=#888888]

[/COLOR]
[COLOR=#888888]Qais Shishani[/COLOR]

---

### Post by fantab on 2014-08-30
```
parted -l: 
Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
 
Number  Start   End     Size    File system     Name                  Flags
1      1049kB  473MB   472MB   ntfs            Basic data partition  hidden, diag
[COLOR=#b22222]2      473MB   746MB   273MB   fat32           Basic data partition  boot[/COLOR]
3      746MB   880MB   134MB   ntfs            Basic data partition  msftres
4      880MB   568GB   567GB   ntfs            Basic data partition  msftdata
8      568GB   613GB   45.0GB  ext4
9      613GB   658GB   45.0GB  ext4
10      658GB   670GB   12.0GB  linux-swap(v1)
**11      670GB   675GB   5372MB                                        bios_grub**

5      675GB   676GB   367MB   ntfs                                  hidden, diag
6      676GB   990GB   315GB   ntfs            Basic data partition  msftdata
7      990GB   1000GB  9991MB  ntfs            Basic data partition  hidden, diag
 


```

> os-prober:/dev/sda2@/efi/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
/dev/sda8:Ubuntu 14.04.1 LTS (14.04):Ubuntu:linux



You must only use one boot mode UEFI or CSM/legacy. Windows in in UEFI mode , so it will be better to install Ubuntu in UEFI as well.

Install ubuntu in UEFI mode.. it is important that you boot in UEFI mode.. see the difference [HERE]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode").

Before that remove the 'bios_grub' flag using Gparted from the 11th partition, the one I marked in bold.

---

### Post by qais2 on 2014-08-31
Hey there Mr.Fantab , 
Thanks for your response , i will try what you suggested and reply if it fail or works .

Regards
Qais Shishani

---

### Post by qais2 on 2014-08-31
Hello again ,

I just tried it again , removed the "bios-grub" , boot from liveUSB , chose "Something else" , made 3 partitions 
[LIST=1]
[*]ext4 , 45 gb , mount "/"
[*]ext4 , 45 gb , mount "/home"
[*]swap area , 12 gb
[/LIST]

[LIST]
[*]install boot on "dev/sda"
[/LIST]
 PS : second installation tried with adding 4th partition 
[LIST]
[*]ext4 , 1 gb , mount "/boot"
[/LIST]


installation failed at "running "update-grub" "

Attached photos of errors

---

### Post by qais2 on 2014-08-31
here is the last photo , since only 5 photos per post allowed

---

### Post by fantab on 2014-08-31
When you have UEFI boot enabled and you have an ESP [EFI System Partition] you don't need to install Grub to MBR.
That is you don't install grub to /dev/sda... but in an EFI system *Grub installs to the ESP*, in your case it is the 2nd FAT partition marked with 'boot' flag or /dev/sda2.

To install Ubuntu in UEFI enabled mode you will HAVE to boot the Ubuntu DVD/USB in EFI mode: [see Here]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode") to know the difference. Confirm this.
In your UEFI menu (the screen-shots you posted above) we can't see the which OS is booting first Ubuntu or Windows...
Can you boot windows?

---

### Post by qais2 on 2014-08-31
Hello again ,

I can Boot to Windows , yes 

My USB is in EFI Mode , i confirmed that  , it does boot into this [IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]
its been like this from the beginning.

Im going to try and[COLOR=#000000] install grub to /dev/sda2 instead of dev/sda

[/COLOR]Thanks a million for bearing with me  , will be back with results.

Regards
Qais Shishani

---

### Post by fantab on 2014-08-31
Also tell us what machine you have there.

Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") tool from 14.04 live ubuntu.
_Note the url_ it creates to bootinfo file and paste it here.

Also try the 12.04 ubuntu... to see how it fares.

---

### Post by qais2 on 2014-08-31
Machine is Toshiba Satellite C850 Laptop

Ubuntu installed (finally , the problem was with location to install boot fixed by choosing /dev/sda2) but cant boot into it , it boots directly to Windows 8 , plugged LiveUSB , ran Boot-Repair , result was error and here is the url 
" [http://paste.ubuntu.com/8195264/](http://paste.ubuntu.com/8195264/) "

Ubuntu 12.04 was working fine before i upgraded to 14.04 , but back in 12.04 i had to manually change UEFI and CSM boot options  to switch between OS's

Regards
Qais Shishani

---

### Post by fantab on 2014-08-31
Run boot-repair tool again but this time choose 'Advanced options' -> Grub Location -> 'check' Separate/boot/efi partition and from dropdown select /dev/sda2 ; apply and run the repair... See the boot-repair page linked earlier.

I suggest you go through [this post]("http://ubuntuforums.org/showthread.php?t=2147295&p=12657352#post12657352") and see if you find anyting about your machine.

---

### Post by qais2 on 2014-08-31
Sadly still this 
> An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/8195759/](http://paste.ubuntu.com/8195759/)

---

### Post by qais2 on 2014-08-31
Hello again , 

Even though boot-repair producing errors all the time , i followed this [http://superuser.com/questions/696838/installed-updated-windows-8-uefi-after-ubuntu-restore-grub](http://superuser.com/questions/696838/installed-updated-windows-8-uefi-after-ubuntu-restore-grub) 

> [COLOR=#000000][FONT=Arial]***Solution 2: Use bcdedit in Windows***[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The Windows bcdedit tool can add a non-Windows boot loader to the boot list. The trick is figuring out what the file is. You can do it this way:[/FONT][/COLOR]

[LIST=1]
[*]Boot to Windows
[*]Open an *Administrator* Command Prompt window. (Don't use a third-party shell for this, either; I've seen reports that bcdedit won't work correctly with some of them.)
[*]Type mountvol S: /S to mount the ESP as S:. (You can change S: to something else if you like.)
[*]Using the Command Prompt, check S: to locate your Ubuntu boot loader. It's probably either S:\EFI\ubuntu\grubx64.efi or S:\ubuntu\shimx64.efi. If you see the latter, it should be safe to use it, and it may be necessary to use it -- shim is how Ubuntu deals with Secure Boot (SB), but on a non-SB computer, it will have little effect. If Secure Boot is inactive, then shim may or may not be installed, so you may need to refer to grubx64.efi directly.
[*]Type bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi, changing shimx64.efito grubx64.efi if shimx64.efi isn't present. Change the path if it's something else, which is unlikely.
[*]Optionally, type bcdedit /set {bootmgr} description "Ubuntu" to set the name that appears in the EFI's own boot manager list. Change Ubuntu to whatever you like.
[/LIST]
[COLOR=#000000][FONT=Arial]If you already know the filename for your boot loader, you can skip steps #3 and #4. (The ESP doesn't need to be mounted to use bcdedit in this way.)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]This method has the advantage that it keeps Windows from messing with the boot order -- sometimes Windows will try to adjust the boot order unbidden. I don't know if this would prevent a repeat of this problem if/when you upgrade to whatever comes after Windows 8.1, though.
[COLOR=#222222][FONT=Verdana]

And everything is working now , thanks for all your time and effort and sorry for bothering you :)

Regards 
Qais Shishani[/FONT][/COLOR][/FONT][/COLOR]

---

