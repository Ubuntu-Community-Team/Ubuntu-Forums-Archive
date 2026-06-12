---
title: "cannot make changes to hard drive"
date: 2015-08-28
forum: Installation &amp; Upgrades
---

### Post by Jaap_Plas on 2015-08-28
Hello,
I am new to Linux, kubuntu etc. Last days i tried to install Linux several times. First i tried archlinus with kde, now i have installed Kubuntu 14, and i have also tried kubuntu 15. Till now in all versions of Linux i get error messages when trying to launch applications or do anything at all. 
The error messages are like: Configuration file "/home/user/.kde/share/config/[application]" not writable. Please contact your system administrator."
I also cant do anything in the Konsole, if i want to change to su, it says "Authentication failure". 
It looks like the system can't make any changes to the hard drive at all. 
I have now set the bios to load-fail defaults. But that does not change anything. 
Searched the internet about this problem, but couldn't find anything similar to this problem.
can anyone help me out?

---

### Post by sudodus on 2015-08-28
Welcome to the Ubuntu Forums :-)

We need more information in order to help you. Please describe your computer (hardware and software) and how you intend to use it!

1. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

2. Are you running Windows or MacOS now? In that case, do you intend to keep it (and have a dual boot system)?

3. What tasks do you intend to perform in the computer?

- internet browsing
- mail, chat ...
- video playing and conversion
- advanced word processing
- advanced editing of pictures
- computing (scientic programs ...)
- ...

4. How did you try to install Kubuntu?

- Did you check the md5sum of the iso file?
- Which tool did you use to make a DVD or USB drive bootable with Kubuntu?
- Does it run live (booted from the DVD or USB drive without installing)?
- Does the installation finish without error messages?

---

### Post by dino99 on 2015-08-28
you should not get issue using the graphical mode (if your user session is active); but from a terminal, use 'sudo' to get rights privilege

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by SeijiSensei on 2015-08-28
If the Linux partition on the hard drive has any errors, it will be marked read-only.  That sounds like what is happening here.  Try this:

1) When you get the boot menu, choose the recovery mode option.
2) You'll eventually see a menu; choose "root shell."
3) Now enter these commands, one per line, at the "#" prompt:
```

cd /
mount -o remount,rw /
touch /forcefsck

```

Now reboot.  The system will run a file system check when it starts up.  Does that solve your problem?

Note there is no space after the comma in "remount,rw".

---

### Post by yancek on 2015-08-28
Check the permissions in that directory and post the output here.   Your user should be the owner of all directories/files and have rw permissions.

```
ls -l /home/user/.kde/share/config/[application
```

---

### Post by Jaap_Plas on 2015-08-28
@seijisensei. Fsck did run, but it did not fix the problem.
@Sudodus. You are  right, I didn't check the md5, I never heard of it before, so I skipped it. After doing the check the codes seem to be invalid. So it is really my fault, sorry for the time it took from you. 
Now I try to download the ISO again. Do you have any idea how I can avoid this problem? Just re-downloading till the md5 does match? I don't even know really what md5 is, and what is essentially going wrong.

---

### Post by Jaap_Plas on 2015-08-28
Took me two more times to download, but now I have one with the right sum. Looks like downloading from mirror works better then torrent.

---

### Post by Jaap_Plas on 2015-08-28
Reinstalled with pen drive, made with Rufus 2.2
No changes, still the same messages.
now I wilt gather your requested information..

---

### Post by Jaap_Plas on 2015-08-28
@Yancek. I did the command with /home/user/.kde/share/config 
Looks like that is the folder where the configuration files of different applications are. 
I can't copy and paste them here with my Linux desktop, because I almost can't do anything with the Linux desktop. But almost all the configuration files have -rw-------
Only five of the total of about 40 have -rw-rw-r--

---

### Post by sudodus on 2015-08-28
> **Jaap_Plas said:**
> Took me two more times to download, but now I have one with the right sum. Looks like downloading from mirror works better then torrent.

Often but always it works faster with torrent. And the torrent clients ususally check for the md5sum automatically as part of the process. But now you have a correct iso file, so that's fine.

---

### Post by sudodus on 2015-08-28
> **Jaap_Plas said:**
> Reinstalled with pen drive, made with Rufus 2.2
No changes, still the same messages.
now I wilt gather your requested information..

Please tell us what works, and what you want to do (that does not work) :-)

1. Does it work to boot Kubuntu and get a graphical desktop environment (the KDE desktop)?

Does anything work in the desktop environment?

Can you do anything in the terminal window (konsole)?

It is not intended to log in as root in the Ubuntu flavours. Use sudo (for text programs) or gksudo (for GUI programs) instead. It reduces the risks to damage the system. For example

```
sudo parted -l
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install htop
# but
gksudo gedit file.ext
```

2. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card (there may be issues with the driver for your graphics chip)
- wifi chip/card (there may be issues with the driver for your wifi chip)

It will be easier to understand and help, if you also reply to the other questions in my first post (post #2 in your thread).

---

### Post by Jaap_Plas on 2015-08-29
My computer:
Motherboard: MSI MS 7302 (very 1.1)
AMD Athlon (tm) II X4 630 processor
Physical Memory: 4096MB (2x2 gb, but different units)
Cache size: 2048KB
No wifi, internet trough LAN
Graphics card: AMD/ATI EAH850 Radeon HD 6850

2. I have only installed kubuntu on the computer right now. So no dual-boot system. I was planning to only use Linux.

3. I only need to use it for basic tasks. Like working with LibreOffice, music, maybe watching a movie.  

4. md5sum checked and fine this time.
Used Rufus latest version to make bootable drive
It runs totally fine when booted from installation drive.
The installation finished without errors.

---

### Post by Jaap_Plas on 2015-08-29
KDE loads almost fine. The background is black. 
It shows up the taskbar, but loads a second bar over it, which I can remove. 
Some examples of what's working and what not:
Firefox does not work, gives only an error. Konsole does work after showing an error. Dolphin does work after showing error,  but it doesn't show any folders or files. Updates fail to install, it starts downloading but it can't make the changes in the system. Libreoffice does only show a small window and starts load, but that's all where it is getting.

---

### Post by Jaap_Plas on 2015-08-29
It fanally works. This time i used a sata hard disk instead of an IDE one. i installed it on the sata hard disk, and now everything runs fine without errors.

---

### Post by sudodus on 2015-08-29
Good catch :KS and thanks for sharing your solution :-)

I did not expect problems due to an IDE hard disk drive.

---

