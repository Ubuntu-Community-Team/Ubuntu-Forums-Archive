---
title: "Installed Ubuntu 9.10, upgraded to 11.04, now GRUB won't work."
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by pah2Ji5j on 2011-08-10
I'm pretty sure it's a GRUB issue.

I have 2 hard drives, one with Windows 7 on it, the other was completely empty.

I installed Ubuntu 9.10 on the empty hard drive with a CD that I had, with the intentions of upgrading to 11.04.

9.10 installed fined, GRUB worked.
I upgraded to 10.04, GRUB worked, but the boot selection had the old selection (version number, distro, links, whatever you may call them) there.

Basically like this: (random image found online)
[http://img170.imageshack.us/img170/3927/bootinguptowindowsvista.jpg](http://img170.imageshack.us/img170/3927/bootinguptowindowsvista.jpg)

I didn't think much of it, I figured when I finish upgrading I'll clean it up.

I upgraded to 10.10, same thing, worked fine, but GRUB now had a 3rd selection.

Then I upgraded to 11.04. During the process it asks you what you want to do with GRUB, previously, I left it where it was, at "keep the current blah blah don't really remember what it said".

This time I thought, let me look at the options, maybe there's something there to clean it up.

So I selected one of the other options that said something along the lines of "replace current with blah blah".

I wasn't too worried, I figured what could go wrong, and even if something does go wrong I really don't care because I'll find a way to get it fixed anyway.

Now when GRUB tries to start, I get this:


[[IMG]http://img846.imageshack.us/img846/4200/photoii.th.jpg[/IMG]](http://imageshack.us/photo/my-images/846/photoii.jpg/)


Not to sure what to do from here.

Any help would be appreciated.

I'm running on the same live CD I used to install, because GRUB still tries to load on my Windows drive even when I disconnect the hard drive I installed Ubuntu on.

---

### Post by oldfred on 2011-08-10
It is a lot better to install from a liveCD with the version you want. Also you need to accept the maintainer version in just about every case. If you have modified the file that is getting updated then you should have a separate backup.

You can only repair 11.04 with a 11.04 liveCD.

When you installed to the second drive you needed to use Advanced Install (Something Else in Natty) to get the choice on where to install the grub2'boot loader. It is best to install the boot loader to sdb and set BIOS to boot from the drive that is SDB as grub will give you a choice to boot Ubuntu or Windows. Then you still have the windows boot loader in sda and can directly boot it.

Your 9.10 lost support on 2011-04-30 so I do not think you can download any tools to help with fixes.

You can use your windows repair CD to fix the windows boot loader in sda.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)

BootRec.exe /fixMBR 

Then you can download the 11.04 Ubuntu liveCd and make a Cd or USB to boot from.
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by pah2Ji5j on 2011-08-10
Thanks, I just thought maybe it wouldn't be too difficult to fix GRUB, I didn't want to have to start from square one again.

---

### Post by dFlyer on 2011-08-10
9.10 is no longer supported. Why not install a more recent version? 10.04 is the LTS version and is good to go for a while. 10.10 and 11.04 are also out there.

---

### Post by pah2Ji5j on 2011-08-10
> **dFlyer said:**
> 9.10 is no longer supported. Why not install a more recent version? 10.04 is the LTS version and is good to go for a while. 10.10 and 11.04 are also out there.

I requested a 9.10 CD for free back when 9.10 was out.
I didn't have any burnable disks to install 11.04 on, and didn't think it would be too difficult to just upgrade it from 9.10 -> 11.04, and thought it may be quicker than waiting for 11.04 to download had I decided to use Daemon Tools.

It's not really a problem now, I found a blank DVD lying around.

---

