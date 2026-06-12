---
title: "Can't detect DVD/CD Drive = No Install"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by Shelnutt2 on 2006-10-03
I just upgraded to my Conroe (Allendale) system, and now I can't get ubuntu to install again. When I tried using the live cd, as its loading, while its mounting the files system is dumps me to the CL and says > disabling ata1 port
disabling ata2 port
disabling ata3 port
disabling ata4 port

Then I'm just left at the command line.

I tried several times, and then I moved to trying to install with the alterative cd, and with both the text and OEM installs, it fails at detecting my cd (dvd) drive. I did not have this problem when I used this dvd drive in my old setup.

Now I am using both my IDE HDD and my Micro Advantage 16DDVDRW-A13 DVD/CD Burner, on the same(/only) IDE port on the DS3. I've got windows installed fine, just can't get Ubunutu installed now.

Thanks guys.

---

### Post by Shelnutt2 on 2006-10-05
bump

---

### Post by wellmt on 2006-10-05
Hello.

I installed a new Core2 system last night too and have a similar problem. Does your motherbaord have an Intel ICH8 (or ICH8R) controller by any chance? If so then it will also have a third party IDE controller for legacy CD/DVD drives.

I've tried Dapper Drake, the Edgy Eft Beta and Knoppix. So far none of them will work, all exhibit a similar problem. This is going to leave a lot of people without any Linux! :( 

Here is what I discovered elsewhere on the web:

from: [http://forums.anandtech.com/messageview.aspx?catid=29&threadid=1927043&frmKeyword=&STARTPAGE=1&FTVAR_FORUMVIEWTMP=Linear](http://forums.anandtech.com/messageview.aspx?catid=29&threadid=1927043&frmKeyword=&STARTPAGE=1&FTVAR_FORUMVIEWTMP=Linear)

Snippit from above link:
As ICH8 lacks PATA controllers, almost every motherboard (including Intel's own) with this chipset has an additional storage controller to support PATA devices. Intel has neglected the fact that 99% of the current optical drives are still of the PATA interface. **This will cause problems when installing Linux from an optical drive**.

---

### Post by wellmt on 2006-10-05
Hmmm..seems like Kernel 2.6.18 will add support for this hardware. Until we get a distro with that as a default kernel though, I think installation is going to be a no-no.

---

### Post by Shelnutt2 on 2006-10-05
Well if we don't currently have hardware support for it, then is it possible to install via another means, such as from hdd or ftp connection? Or will that also fail due to the lack of a working CD/DVD drive? Then when the kernel is updated we can update and have a working optical drive?

---

### Post by wellmt on 2006-10-05
Yes from a USB stick. See this Wiki page, it's all about Core2 support.

[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

---

### Post by wellmt on 2006-10-05
Looked up the spec of your mobo.  

Northbridge: Intel® P965 Express Chipset
Southbridge: Intel® ICH8
Marvel 8053 Gigabit LAN Controller 

You must have some other IDE controller for the CD/DVD though if you've got a standard IDE one connected. 

So basically there are two problems:

1. The ICH8 series of southbridge may not supported. This means that even if you could get the install media to boot, it won't find any hard disks!

2. You must have an IDE controller like a JMB for the CD/DVD. I know the  J-Micron driver isn't included in the current build of Ubuntu (including Eft beta-1 desktop). 

The drivers are supposed to be in the nightly builds now though so I'm hoping that RC1 will allow us to install Ubuntu!

Not sure about the Marvel LAN controller yet though.

---

### Post by wilsonywx on 2006-10-05
I have a similar problem. 

mobo. Intel dp965
cpu core 2 e6300
ram 1gb corsair value select

I need to install linux to be able to use the linux environment for my systems class. I am not happy that it fails to load ide modules and tells me it cannot detect my cdrom although the installer booted from a cd. I read some similar threads online, but those don't seem to be my problem. 

I really hope ubuntu developers take this more seriously so that drivers are better adapted. Although microsoft generally sucks, I must give them credit for driver and hardware compatibility. WIn xp installed on my machine w/o a problem. Hopefully they will do the same with linux so new users won't get frustrated.

---

### Post by wellmt on 2006-10-06
It's frustrating but they are working on it. You've got to remember that the drivers on Windows are generally developed by the manufacturer whereas under Linux they are often developed by volunteers (who sometimes have to use reverse engineering).

It is the manufacturers who are at fault at the end of the day.

The real trick is to always use a machine that's at least 6 months old, but I must admit the Conroe is too tempting to ignore!

---

### Post by wahidrahman on 2006-11-07
Hi there
I am a novice in installing ubuntu 6.10.I m facing a problem while "CDROM DETECTION AND MOUNT" in my installing process.At first it ask me whether i want to load CDROM module from flopy drive(i dont use any flopy drive) or not.i choice no.then it gives me a list to select a cdrom module from there.i dont know which one i will select.But i have tried selecting every option.no one works.I m using Samsung DVD writer.

My system specification:
Intel Core2Due(conroe) E6400
RAM: 512MB(667bus)
Motherboard: Intel DG965RY classic series
AGP Builtin
Hdd Samsung 80GB SATA

Is there any problem using SATA hdd.when i tried to use Fedore5 then HDD driver was a problem.anyway..............

I need proper and easier solution to install ubuntu in my system.Anybody can help me??Please.....\

---

