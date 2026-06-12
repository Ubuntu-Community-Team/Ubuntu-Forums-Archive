---
title: "Not enough RAM?"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by 0faber on 2008-09-17
I'm trying to install Hardy on my mom's Dell Latitude C810 laptop. Got an error message saying at least 256 MB of RAM required for installation. It has 256 MB of RAM. Tried running the Feisty live CD (which also requires 256 MB of RAM), it worked fine. I ignored the error message, rebooted and tried to install. It got stuck on partitioning (I was trying to dual boot).

For now I can't print the out-put of Windows' System Information, because I can restart the computer until the battery runs down ... But I will when I can. Any other diagnostics I should try? Any ideas about what the problem might be? 

Thanks.

---

### Post by ronnielsen1 on 2008-09-17
I think you need 384 M to install it and supposedly 256 to run it but I wouldn't want to. You could install xubuntu, puppy, antiX or MiniMe

---

### Post by ronnielsen1 on 2008-09-17
> **Recommended minimum requirements**

 Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly. 

[LIST]
[*]700 MHz x86 processor 
[*]384 MB of system memory (RAM) 
[*]8 GB of disk space 
[*]Graphics card capable of 1024x768 resolution 
[*]*Sound card* 
[*]*A network or Internet connection*
[/LIST]

> **Low-spec computers (Xubuntu)**

 If you have an old or low-spec computer, using a lightweight desktop system such as **Xubuntu** is recommended, as it should make more efficient use of your system's resources. 
If your system has less than 192 MB of system memory, use the *Alternate Installation CD*. 
**Note:** If you have a low-specification computer, certain features may be automatically turned off to conserve system resources. For example, if you have a graphics card with only a small amount of video memory (VRAM), the boot-up screen may not be shown. 
Follow this link for detailed instructions: [Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems"). 
 
**Minimum requirements**

 
[LIST]
[*]166 MHz processor 
[*]64 MB of system memory (RAM) 
[*]At least 1.5 GB of disk space 
[*]VGA graphics card
[/LIST]

You might also want to do a memtest and make sure the 256 stick is good

---

### Post by 0faber on 2008-09-17
Thanks. Actually it requires 384 MB to run the live CD, but 256 MB to install - at least that's what the CD says. Nevertheless, I'll try XUbuntu if nothing else works. 

System Information in Windows says:

OS Name                       Microsoft Windows XP Professional
Version                       5.1.2600 ServicePack 2 Build 2600
OS Manufacturer               Microsoft Corporation
System Name                   VA780BB1H
System Manufacturer           Dell Computer Corporation
System Model                  Latitude C810  
System Type                   X86-baced PC
Processor                     x86 Family 6 Model 11 Stepping 1 GenuineIntel ~1129 Mhz 
BIOS Version/Date             Dell Computer Corporation A04    9/13/2001
SIMBIOS Version               2.3
Windows Directory             C:\WINDOWS
System Directory              C:\WINDOWS\system32
Boot Device                   \Device\HarddiskVolumn1
Locale                        United States
Hardware Abstraction...       Version = "5.1 26000.2180 (xpsp_sp2_rtm.040803-2158)"
User Name                     VA780BB1H\Owner
Time Zone                     Eastern Standard Time
Total Physical Memory         256.00 MB
Available Physical Me...      29.54 MB
Total Virtual Memory          2.00 GB
Available Virtual Mem...      1.96 GB
Page File Space               618.14 MB
Page File                     C:\pagefile.sys

Disk has 32.56 GB of free space, according to disk manager.

---

### Post by howefield on 2008-09-17
Even  you can install it, just booting to the desktop won't leave you much memory to run applications, you'll be using swap very quickly and performance will likely be poor.

Like the other guys, I'd say go for a lighter weight version. Or install another 256 memory chip assuming you have the slot available.

---

### Post by snowpine on 2008-09-17
Try using the Alternate Install CD. It uses a text based installer (instead of a Live CD) and I have used it sucessfully in the past on a 256mb computer.

If you find Ubuntu to be too slow on that computer, you can easily install Xubuntu on top of it using 'sudo aptitude install xubuntu-desktop' then selecting Xfce from the Sessions menu at the login screen. There are many options that are even faster than Xubuntu, but let's take it one step at a time. :)

---

### Post by 0faber on 2008-09-17
Thanks ronnielsen, howfield & snowpine. I'll give the alternate installation CD a try, and have an XUbuntu CD handy.

---

### Post by Pumalite on 2008-09-17
I'd say you better use the Xubuntu Alternate CD:
[http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/)

---

### Post by Shazaam on 2008-09-17
You also have what's called "Shared Memory" when using a laptop. So, depending on the laptops bios setting, part of your 256mb of memory is being "shared" with the onboard video card. That is probably why the error message pops up.

---

### Post by steelxenon on 2008-09-17
on my brother's laptop, I used the xubuntu cd to install, then used some apt-get commands I found somewhere else in the forums to install ubuntu-desktop and it works just fine

---

