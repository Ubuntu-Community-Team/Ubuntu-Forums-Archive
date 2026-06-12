---
title: "dualboot :: no grub - error 15"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by Ampi on 2010-10-25
Yesterday my 5th ubuntunisation took place :)

But still this guy wanted a dualboot just in case. So I did. Of course I had to reinstall grub to make sure both systems would show on boot (I first installed Ubuntu, then Windows). 
I tried all night, I just couldn't work it out. 

I tried everything I could find on the web, but it just didn't work. The only system that shows up is Ubuntu. I also looked at 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows). Everytime I try 
```
find /boot/grub/stage1
```
I get a grub error 15. All the fixes include a step where I get an error. Any other ideas? Maybe reinstall Windows?

It's Windows 7 and it is installed on the first primary partition. Ubuntu is on the rest of the disk in an extended partition with seperate swap partition, seperate /home partition (ext4) and a seperate /DATA partition (xfs).

---

### Post by Rubi1200 on 2010-10-25
From a LiveCD, post the results of the boot-script linked at the bottom of my post.

The results will make offering solutions easier.

Thanks.

---

### Post by Ampi on 2010-10-25
Thanks, as Im not behind my friend's computer itll have to wait a little bit.. as soon as I know Ill post the results here.

---

### Post by psusi on 2010-10-25
Error 15 is what you get when grub legacy's MBR boot code can not load the grub image.  It is not a possible result of the find command.  You must mean that the find command reports that the file is not found, and that is because grub2 does not have a stage1 file.

---

### Post by Ampi on 2010-10-27
@Psusi: Thanks for the explanation. The whole grub-thing is one of the things a still don't understand.. :(

@Rubi1200: Maybe a stupid question, but the script has to be run from the liveCD? The computer automatically boots up into Ubuntu, cant I do it from there? In that case I might be able to explain him by email how to do it. If not Ill bring him a liveCD and do it myself :)

---

### Post by wilee-nilee on 2010-10-27
> **Ampi said:**
> @Psusi: Thanks for the explanation. The whole grub-thing is one of the things a still don't understand.. :(

@Rubi1200: Maybe a stupid question, but the script has to be run from the liveCD? The computer automatically boots up into Ubuntu, cant I do it from there? In that case I might be able to explain him by email how to do it. If not Ill bring him a liveCD and do it myself :)

You can run the script from the installed Ubuntu. You can have them run it and send the text to you as a attachment in a email then post it. Post it in code tags by clicking on the # in the reply and put the text in between the tags.

---

### Post by psusi on 2010-10-27
> **Ampi said:**
> 
@Rubi1200: Maybe a stupid question, but the script has to be run from the liveCD? The computer automatically boots up into Ubuntu, cant I do it from there? In that case I might be able to explain him by email how to do it. If not Ill bring him a liveCD and do it myself :)

Umm... I thought the whole problem was that it wouldn't boot?  If it boots into Ubuntu then what is the problem?  No option to boot Windows?  Running sudo update-grub should pick up Windows, but yes, running the boot info script will provide all relevant information to diagnose the problem.

---

