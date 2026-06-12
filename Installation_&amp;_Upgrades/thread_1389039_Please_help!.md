---
title: "Please help!"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by reaply on 2010-01-23
I am happy with ubuntu it's cool, but I want to go back to windows. I lost my windows cd. So I made a blank disc with an iso file. But the problem is. When I try to keep it inside my computer and restart it won't load. I think grub has something to do with this.

---

### Post by reaply on 2010-01-23
Can someone, please help? :confused:

---

### Post by Fir3chi3f on 2010-01-23
Not booting off of a disk sounds like a bios setting. grub is installed on the hard drive and does not change any other settings. 

Entering bios is usually F2 - F12 depending on your system. And make sure that the CD drive is the first boot device. 

I must ask though, when you installed Ubuntu for the first time, did you delete windows? The ubuntu default option is to just move windows over and install next to it. Allowing you to still boot into windows at startup.

Backup copies of windows usually don't work very well. The disk's signature isn't copied along with its content and could cause it to not boot.

---

### Post by reaply on 2010-01-23
Thank you for the reply, here's the story. Ive had ubuntu, windows xp, windows 7 partitioned for like almost a year. And so one day when I go to startup I chose my xp startup and it made it go into recovery mode and I let it as soon as that was done windows 7 was gone and windows xp would say a boot up or something is missing. So I popped in ubuntu 9.10 disk. And installed it completely on my C:, ive checked my bios and it says "press enter" so when it says boot disc on startup I press enter but after 5  sec grub loads.

---

### Post by Fir3chi3f on 2010-01-23
Do you have another computer in the house that you can try booting off that disk on? To make sure it is infact bootable.

---

### Post by flabdablet on 2010-01-23
What make and model is your PC?

---

### Post by reaply on 2010-01-23
RIG:
Manufacturer:                  Gateway
                        Processor:                  AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (2 CPUs), ~2.0GHz
                        Memory:                  2432MB RAM
                        Hard Drive:                  149 GB
                        Video Card:                  NVIDIA GeForce 8600 GT 
                        Monitor:                  
                       Sound Card:                  Speakers (Realtek AC'97 Audio)
                        Speakers/Headphones:                  
                       Keyboard:                  USB Root Hub
                        Mouse:                  USB Root Hub
                        Mouse Surface:                  razor
                        Operating System:                  Windows 7 Ultimate 32-bit (6.1, Build 7600) (7600.win7_rtm.090713-1255)
                        Motherboard:                  
                       Computer Case:                  Gate Way


And no, I don't got another pc around here :/. I might be able to use my friends though heh heh. And ignore the OS. Old system information from last month before the problem.

---

### Post by flabdablet on 2010-01-23
Is there a Gateway model number? That will help track down the correct keystrokes to use to force it to boot from CD.

---

### Post by flabdablet on 2010-01-23
Also: if you've got Ubuntu running, and you pop your Windows setup CD in the drive, what files do you see on it?

---

### Post by reaply on 2010-01-23
gt5056

---

### Post by reaply on 2010-01-23
Nothing pops up.

---

### Post by reaply on 2010-01-23
Oh ya, just incase. gt5056 is the model number.

---

### Post by Fir3chi3f on 2010-01-23
No icons? Nothing under Places>CDrom?

---

### Post by reaply on 2010-01-23
Oh ya, it's under place>CDROM.

---

### Post by Fir3chi3f on 2010-01-24
If it looks like my screen shot than its a start, but it is still possible that it is a bootable disk. Have you used this disk before?

ps- I'm running out of coffee ](*,)

---

### Post by reaply on 2010-01-24
Oh ya, sorry I forgot to mention. I made 1 disc with an iso. And the other everything extracted from the iso. The one with the iso a folder will automaticly pop up and the one without the iso doesn't do anything except you have to look for it under places.

---

### Post by reaply on 2010-01-24
Running out of coffee!??!!? :(, no I just made the disc today. Heck, I just bought it 2 hours ago. It is DVD-R. and also nice desktop xD and the disc without the iso looks like that.

---

### Post by reaply on 2010-01-24
Oh ya, I suggest putting black on your ip address ;).

---

### Post by Fir3chi3f on 2010-01-24
Thanks for the compliment, but you need to figure out if your windows install disk is even usable before we can help you anymore. 

I have lost my $400 windows install disk many times, but it was always somewhere, I think you can handle everything once you have it.

---

### Post by reaply on 2010-01-24
I shall test my friends pc then. So untill then, good night ubuntu users! And thank you for helping me.

---

### Post by presence1960 on 2010-01-24
> **reaply said:**
>  **_So I made a blank disc with an iso file._** But the problem is. When I try to keep it inside my computer and restart it won't load. I think grub has something to do with this.

If all you did was copy the iso to the disk it will never boot. If you burned the iso as an image to CD/DVD then it should boot as long as you have CD/DVD ahead of hard disk in the device boot order in BIOS.

---

### Post by lisati on 2010-01-24
> **reaply said:**
> Thank you for the reply, here's the story. Ive had ubuntu, windows xp, windows 7 partitioned for like almost a year. And so one day when I go to startup I chose my xp startup and it made it go into recovery mode and I let it as soon as that was done windows 7 was gone and windows xp would say a boot up or something is missing. So I popped in ubuntu 9.10 disk. And installed it completely on my C:, **ive checked my bios and it says "press enter" so when it says boot disc on startup I press enter but after 5  sec grub loads.**
It is normal for grub to start before Ubuntu - grub is Ubuntu's boot loader
> **reaply said:**
> Oh ya, sorry I forgot to mention. I made 1 disc with an iso. And the other everything **extracted from the iso**. The one with the iso a folder will automaticly pop up and the one without the iso doesn't do anything except you have to look for it under places.

:confused: Don't extract anything from the ISO before putting it on disk!
Do what presence1960 says: burn the ISO file as a disk image. See here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by reaply on 2010-01-24
> **lisati said:**
> It is normal for grub to start before Ubuntu - grub is Ubuntu's boot loader


:confused: Don't extract anything from the ISO before putting it on disk!
Do what presence1960 says: burn the ISO file as a disk image. See here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
I do burn them. And are you saying grub can be canceling the disc from starting?

---

### Post by reaply on 2010-01-24
> **presence1960 said:**
> If all you did was copy the iso to the disk it will never boot. If you burned the iso as an image to CD/DVD then it should boot as long as you have CD/DVD ahead of hard disk in the device boot order in BIOS.
And what do you as an image? I just burned the iso into the disc isn't that what I do?

---

### Post by flabdablet on 2010-01-24
First off: I'm not 100% sure that XP Setup will boot and run correctly from a DVD. You might actually need to use a CD-R.

Second: if I understand you correctly, you say that the disc you "made with an iso" **does** cause a file browser window to pop open when you insert it in your drive while Ubuntu is running. I'm still interested in seeing the names of all the files that appear in that window.

---

### Post by presence1960 on 2010-01-24
> **reaply said:**
> And what do you as an image? I just burned the iso into the disc isn't that what I do?

No it is not see the link lisati gave you.

---

### Post by jdeca57 on 2010-01-24
> **reaply said:**
> Thank you for the reply, here's the story. Ive had ubuntu, windows xp, windows 7 partitioned for like almost a year. And so one day when I go to startup I chose my xp startup and it made it go into recovery mode and I let it as soon as that was done windows 7 was gone and windows xp would say a boot up or something is missing. So I popped in ubuntu 9.10 disk. And installed it completely on my C:, ive checked my bios and it says "press enter" so when it says boot disc on startup I press enter but after 5  sec grub loads.
I'll let others try and help you with the hardware since I don't own a Gateway computer, but... You can make a recovery startup disk in Windows 7. I'd do that once you get the system underway, since using an iso for a new install erases all data. I hope you made a backup?

---

