---
title: "Ubuntu Boot Repair Pastebin Dual Boot with Windows 10"
date: 2016-09-21
forum: Installation &amp; Upgrades
---

### Post by Tyner on 2016-09-21
[http://paste.ubuntu.com/23210167/](http://paste.ubuntu.com/23210167/)

---

### Post by Bucky Ball on 2016-09-21
Don't expect a lot of support when you post only a link to a bootinfo output on a thread with a title that doesn't describe the issue you want support with and no other details. Posting a link and nothing else in any circumstance is not encouraged here.

Please see the tips for 'Effective posting' at the first, pink link in my signature at the bottom of this post and edit your first post to improve your chances of support. Good luck.

---

### Post by Tyner on 2016-09-21
Sorry, I thought posting the Boot Repair log would imply that it won't boot and the Boot Repair program failed. I may just try to start over if I can figure out what I did wrong?

---

### Post by Bucky Ball on 2016-09-21
> Explain how you installed or are installing Ubuntu. There are many different flavours of Ubuntu and even more ways to install it. 

From the link. Your boot repair output is saying you're good to go, so what exactly is happening when you boot the machine? Give a description of your actual issue. 'It won't boot' gives us nothing to work with. What do you see? What happens? Is it a laptop or desktop?
 
Helps you to get support quicker if you post these details plus which Ubuntu release and flavour you are using, basic hardware specs, etc. Saves time as  people don't need to ask and gives potential helpers something to go on with ... ;)

Are you getting to the options screen when you boot where you can select an operating system or it's going to a black screen or cursor?

---

### Post by Tyner on 2016-09-21
Laptop, Ubuntu Desktop 16.04.1 LTS, from the boot manager when I click on Ubuntu I get that colorful background and nothing else, when I click on Windows 10 I get the Blue Screen of Death. At this point I'm thinking I may have to reformat everything and reinstall from scratch? I backed everything up to an external hard drive before I started.

---

### Post by oldfred on 2016-09-21
Do not reinstall.

Grub can only boot working Windows.
And that means Windows that is not hibernated, nor needs chkdsk. 
Did you resize Windows from Windows to make room for Ubuntu? And reboot so it can run chkdsk?
And you must turn off Windows 8 or later that uses fast start up or always on hibernation. 

       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

You probably have to reinstall temporarily the Windows boot loader to MBR so you can boot it and turn off hibernation. Best to use Windows repair flash drive, but Boot-Repair can add a generic Windows type boot loader. Then use Boot-Repair to restore grub to MBR.
       
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    
My Skylake based SFF system worked with 16.04 without any issues (in UEFI mode). Older versions of Ubuntu did need a boot parameter to work with Skylake's video. 

What model Acer? Is it newer with UEFI?

Does Ubuntu work ok in live mode?

---

