---
title: "Installation  woes (hardy heron)"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by AndrewKeith80 on 2008-06-02
Hi, i recently convinced my wife to switch to using linux because her computer's hardware is aging and she doesnt want to buy a new computer. 

What struck me as difficult to sell her on the idea of using linux was that even a distro like ubuntu would be difficult to install and use. So I convinced her to give it a try and sure enough, the installation was PAINSTAKINGLY difficult. 

Here is the list of problems I encountered

1) Hang during boot while loading floppy controllers. (Solved by reseting the BIOS to defaults)

2) Secondary partition which contained files cannot be mounted. The drive is NTFS and I wanted to copy out the files before formatting to ext3. The reason it cant mount is because the partition was "dirty". I had to go to the terminal and force mount to clear the "dirty" bit. Why the heck doesnt the GUI give an option to force mount, is beyond my understanding. To ask my non computer literate wife to mount on the command line is ludicrous. (Solved by force mounting)

3) CD-Writer would not recognise empty discs. The computer has an ATAPI CD-ROM on hdc and an ATAPI CD-WRITER on hdd. After checking dmesg, i found that the if there is no disc in hdc while booting, ubuntu would not recognise hdd. After alot of tweaks to modules.conf, fstab , etc etc . I still could not get it to work. Finally , I moved the CD-WRITER to hdc and removed the CD-ROM. The problem is how can anyone expect a sane person to configure modules, fstab just to get a freaking CD-WRITER to work. (Solved by removing CD-ROM).

The root of my problems is that if the person using the ubuntu isnt a software engineer, i dont see any hope of them using it rationally. (I am a software engineer, but my wife is a salesperson). Finally , after 2 weeks of using ubuntu, she finally relented and asked if we could buy a notebook with at least windows XP or Vista because now the printer is broken and we dont know how to fix it.

There is simply no excuse in requesting the user to edit files on the disk just to install a driver or configure some hardware settings on their new ubuntu installation. There is no excuse in typing cryptic commands just to find out if the CD-WRITER is recognised by cdrecord -scanbus. I was especially disappointed when I clicked the hardware test program and didnt even test the CD-ROM or CD-WRITER. 

I am not trying to berate ubuntu. I use ubuntu on some of my computers in the office. The difference is that my entire office is made up of software engineers which dont mind editing files and typing long complicated commands. Plain jane users dont have a clue on what to do.

---

### Post by Amarsingh0793 on 2008-06-02
As hardware get older, it's best to get a new computer anyway depending on how old the computer is. I think you should give Ubuntu another chance on a more modern computer. Just boot the live cd on a more modern computer and ask your wife to try it again:KS. I use ubuntu on an old AMD Athlon XP 2000+ with just 256MB RAM and it runs smoothly on mine.:)

You could also try a previous version of Ubuntu like Ubuntu 7.10.

---

### Post by wpshooter on 2008-06-02
> **AndrewKeith80 said:**
> 
There is simply no excuse in requesting the user to edit files on the disk just to install a driver or configure some hardware settings on their new ubuntu installation. There is no excuse in typing cryptic commands just to find out if the CD-WRITER is recognised by cdrecord -scanbus. I was especially disappointed when I clicked the hardware test program and didnt even test the CD-ROM or CD-WRITER.

OOOOO, what you said.

Don't you know that you just committed the unpardonable sin of speaking against the holy grail of Linux !!!

Not having to edit this, that and the other configuration file to fix every broken thing in a Linux distribution and to not know every linux terminal command in the instant of a heartbeat !!! 

What kind of heritic are you ???

---

### Post by AndrewKeith80 on 2008-06-03
LOL .. 

I have finally got the printer to work by using some really cryptic commands and writing my own boot scripts to load the printer properly. 

My wife currently is keen to continue using ubuntu for awhile longer if it remains intact and doesnt self implode. I have assured her that we can get a new computer if her ubuntu self-destructs or requires more cryptic commands to continue functioning. 

The sad thing is that all she wants to do is surf the net, print some web documents, burn a few pictures to a CD and other simple home user tasks.

---

