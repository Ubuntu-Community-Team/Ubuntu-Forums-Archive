---
title: "grub rescue after update"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by justtoby on 2010-09-22
Hello,

I just installed the laptop version of ubuntu. It had some updates wich i have run. After the installation of the updates it wanted to reboot and i agreed. Now it won't start anymore

I have had a double boot with windows xp. Now i can't choose anymore and it gives the message:

error: no such device: 884f1442-0941-4a8f-b3a7-f54b8d5233be
grub rescue>

What can i do to boot again? I cant boot windows and/or ubuntu :(

I hope you can help!

---

### Post by Skaperen on 2010-09-22
GRUB is looking for a partition or filesystem based on its UUID.  Something got out of sync somewhere.  Maybe the script to rebuild the GRUB config file failed (I know it did for me recently and is preventing my system from running the updated kernel ... though I can still boot the old kernel).  Offhand I don't remember the GRUB command line commands.  But at that grub rescue prompt, the right command, with the right device name (you probably won't know the right UUID) could get it up.  But after that I don't know the magic grub command to make it persistent, or to get the Windows reference back.

---

### Post by justtoby on 2010-09-22
so what can i do about it? i see some people had the same experience after a update? how come?

---

### Post by drs305 on 2010-09-22
Hey justtoby, welcome to the Ubuntu forums.

Do you know the partition your Ubuntu install is on? 
Is this a normal install or a wubi install (inside Windows)?
Do you see the Grub2 menu at boot?

If you give us that info we can get a quick start and we might be able to give you some grub terminal commands to allow you to boot. 

After that, the best thing you can do for us is to boot to the LiveCD and run *meierfra's* boot info script. It will give us the information we really need to see what's happening on your system.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by justtoby on 2010-09-22
Hello,

It is an install besides windows. So it is not installed in windows

What i see when i start is pretty much as what i said in the first post. Jus the error and then the grub rescue> command line. I found some commands in these forums but lot of those commands get the reply of Unknown command ''

I went to the link you supplied but when can i try that? I dont have any control over the laptop anymore and all i get is the rescue command.

when i try the LS command i get hd0 so i understand that he is missing any partition?

I am new at this so all the information i can get is welcome. And there is no better way to learn something if it aint working haha

---

### Post by drs305 on 2010-09-22
You would have to boot the LiveCD and then download and run the boot info script from the LiveCD environment. From the LiveCD we can also reinstall Grub2 fairly easily with a bit of terminal work.

Since grub doesn't see any partitions (hd0) you aren't going to be able to boot from the grub prompt. I saw a similar post a few days ago but I don't know if we ever found a solution. I'll do some searching.

---

### Post by justtoby on 2010-09-22
I found that post as well but it didn't had a solution. I have NO idea how i will be able to make a cd. I will try it though

---

### Post by drs305 on 2010-09-22
> **justtoby said:**
> I have NO idea how i will be able to make a cd. I will try it though

I forgot it was a netbook. How did you install Ubuntu originally - a thumbdrive? I always default in my thinking to the LiveCD, but all you need is a method to get to a working Ubuntu desktop - via CD, thumb drive, etc.

---

### Post by justtoby on 2010-09-22
i installed it with a exe file...then choose the option for a clean installation, so no try version or in windows. It was working all okay and then disaster follows. I am afraid i lost my windows files as well now :S

---

### Post by drs305 on 2010-09-22
You can probably get your Windows back with this (unless netbooks have special considerations):
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by |Alex| on 2010-09-24
Here is my similar situation: I have an asus P5K PRO motherboard with an Intel core 2 quad processor, two samsung sata HDDs 500 GB each one. On the first there is installed XP SP3 and on the second nothing. I prepared a bootable usb with Ubuntu 10.04.1 LTS, I connected an 30 GB IDE hard drive behind the optical drive and I started from usb. I choose a full hard drive installation with no partition on the IDE disk, I remember that at the ending of installation details (maybe at the final summary before the installation) I saw a "advanced" button, selecting this one it came up a window with the possibility to select on which HDD put the grub, it was selected the sata one, maybe the one with XP but i canceled without taking care of this.

Now yhe problem is the same, when I switch on the computer it goes directly to "error: no such device: (UUID). grub rescue>"

I tried to disconnect the IDE drive but the same is happening than I thought that the grub is installed on sata hdd. Looking on "http://ubuntuforums.org/showthread.php?t=1014708" I tried to start with the original XP disk to restore the original bootloader but every time it says "The file ohci1394 is damaged. Press a button to continue." (while loading the files from the CD at various points apparently randomly because the name of the file changes) an than restarts the computer with no difference.

To check the possibility of a damaged CD i tried to start another computer and it works, than I disconnected both the IDE and the first sata hdd and tried to boot from CD but the same thing is happening.

I tried to be as complete as i could, my problem is that on XP I have installed some programs that were working fine but they needed a lot of configurations so for me is very hard to think about a complete re-installation of OS (also if i wanted to i couldn't for the problem above...)

My last thought is that the optical drive is damaged (quite new...).

Booting in try mode from the usb I see all the files on the first sata hdd.

Can this be solved in any way?

---

### Post by |Alex| on 2010-09-27
So, i tried an external USB optical drive and the Windows CD was loaded without problems!
the point is that was not recognizing my Administrator password...
I tried to install lilo and now it is all OK!!!!!!!:popcorn:

---

### Post by gluki on 2011-04-13
I have same problem, and found this -> 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

I would like to use LiveCD, now downloading iso, and then burn it to a flash drive and I will try.
Also below there is a third part software.

half year of work withouth backups in windows oO

---

