---
title: "Can't install 11.04"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by jrj350 on 2011-07-08
I have downloaded  *Ubuntu 11.04* (Natty Narwhal) three times. I installed it in my SONY laptop with no problems. It runs well and I like it. 
Using the same disk, I tried to install it in my HP All-in-One 200is. Nothing happens. It refuses to initiate. I can hear the disk spinning but nothing happens. This holds true for all three downloads. I have no problems with running other disks in the drive. Just the 11.04 iso. Therefore I don't think I have a problem with  broken hardware. I am presently running dual boot with Windows 7 and Ubuntu 10.10. I would really like to run 11.04. Any help will be deeply appreciated.
For what good it might do here are the some specs on the computer:

                      p { margin-bottom: 0.08in; }>  [COLOR=#000000][FONT=Calibri][SIZE=2]Hewlett-Packard 200-5120is[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Calibri][SIZE=2]Dual boot - Windows 7 Home Premium (x64) & Ubuntu 10.10
[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Calibri][SIZE=2]Main Circuit Board - Board: Hewlett-Packard 2AA2[/SIZE][/FONT][/COLOR]
  [COLOR=#000000]                                       [FONT=Calibri][SIZE=2]- Bus Clock: 200 megahertz[/SIZE][/FONT][/COLOR]
  [COLOR=#000000]                                        [FONT=Calibri][SIZE=2]- BIOS: American Megatrends Inc. 6.08 08/19/2010[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Calibri][SIZE=2]Processor  - 2.70 gigahertz Intel Pentium Dual-Core[/SIZE][/FONT][/COLOR]
  [COLOR=#000000]                      [FONT=Calibri][SIZE=2]- 64 kilobyte primary memory cache[/SIZE][/FONT][/COLOR]
   [COLOR=#000000][FONT=Calibri][SIZE=2]Chip set - Intel G45S Express [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2]Video - Integrated graphics using Intel GMA x4500[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Calibri][SIZE=2]4062 Megabytes Usable Installed Memory[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Calibri][SIZE=2]SAMSUNG HD502HJ [Hard drive] (500.11 GB) [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Calibri][SIZE=2]hp DVDRAM GT30L [Optical drive][/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Calibri][SIZE=2]Printers - HP Officejet J4500 series[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Calibri][SIZE=2]Display - Intel(R) G45/G43 Express Chipset [Display adapter] (2x)[/SIZE][/FONT][/COLOR]
  [COLOR=#000000]                 [FONT=Calibri][SIZE=2]- Generic PnP Monitor (21.3"vis, s/n 257, July 2009)[/SIZE][/FONT][/COLOR]
 

Oh yes, another thing. I tried both 32-bit and 64-bit versions.

---

### Post by TeoBigusGeekus on 2011-07-08
Silly question, but are the bios settings (boot from cd) ok?

---

### Post by jrj350 on 2011-07-09
Oh yes, the BIOS is set correctly. Otherwise I wouldn't have been able to load in the Ubuntu 10.10. Also, I successfully downloaded and installed Linux-Mint_Debian, so there is no problem there.
By the way, I have been playing with computers since early 1980, and I want to say there are no "silly" questions. I have made so many dumb mistakes I am glad to hear any and all suggestions.
Thanks for replying. I appreciate it.

---

### Post by mörgæs on 2011-07-09
If 10.10 works, I would stay with this one as long as it is supported. 

If you absolutely want 11.04: Have you tried the alternate ISO?

---

### Post by R Smit on 2011-07-09
Almost same problem here; the funny thing is that Mint 11 (based on Ubuntu 11.04) en Kubuntu 11.04 run without any problems?!

Packard Bell iXtreme I6803
My spec:

Processor Intel® Core™ i5 2300 Processor 2.80 GHz

Geheugen 4096 MB

Harddisk 1 TB

DVD-Rewriter DVD+-RW double layer

Videokaart 1024 MB nVidia GeForce GT420

---

### Post by jrj350 on 2011-07-09
Yep, tried the alternative. I have Ubuntu 10.10 and Linux-Mint-Deb installed along with MS Windows 7. I have Ubuntu 11.04 install on my laptop and I like it. So... ????

---

### Post by Perfect Storm on 2011-07-09
You could install a fresh 10.10 and then upgrade it to 11.04.

---

### Post by jrj350 on 2011-07-11
I  am not happy with this situation. Linux-Mint Debian works very well and I like it a lot, so I will just stick with it. Just too fed up to fight the Ubuntu thing any more. Thanks for the replies, and fare-thee-well.

---

### Post by eb sol on 2011-08-03
I have the same exact problem :( ..

I tried installing ubuntu 11.04 from DVD and a flash memory .. I even tried the last suggesting "updating a fresh 10.10" but had no luck ..

I'm using only ubuntu :( .. 

Any other suggestions ?

---

### Post by Hakunka-Matata on 2011-08-03
What solved the problem?  Thanks

---

### Post by Blasphemist on 2011-08-03
As long as the cd works for installing anything and therefore cd boot issues are not the culprit, I'd say the issue has to do with video. There are changes to grub, the kernel and x in natty that can cause issues. Please see the first 3 posts at least in this sticky thread to troubleshoot and solve this. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by mörgæs on 2011-08-06
Installing Xubuntu in stead of Ubuntu is also worth trying.

---

### Post by eb sol on 2011-08-08
> **mörgæs said:**
> Installing Xubuntu in stead of Ubuntu is also worth trying.

Thanks for the suggesting .. But I want to have a full Ubuntu experience, specially when I have the required hardware ..

I'm having the same problem .. I can't install ubuntu 11.04 on my machine ..

Help anyone !!

---

### Post by mörgæs on 2011-08-08
Even if you are not planning on keeping Xubuntu, it will help troubleshooting to know if the install works.

---

### Post by R Smit on 2011-08-10
> **R Smit said:**
> Almost same problem here; the funny thing is that Mint 11 (based on Ubuntu 11.04) en Kubuntu 11.04 run without any problems?!

Packard Bell iXtreme I6803
My spec:

Processor Intel® Core™ i5 2300 Processor 2.80 GHz

Geheugen 4096 MB

Harddisk 1 TB

DVD-Rewriter DVD+-RW double layer

Videokaart 1024 MB nVidia GeForce GT420

There is hope:Ubuntu 11.10 alpha 3 runs fine on this system! So I will skip 11.04.

---

### Post by woodbyrd on 2011-09-05
i have a intel d805 dual core  on start up change to singel core in bios then 11.04 worked but no second cure

---

### Post by eb sol on 2011-10-14
NOW I can NOT install the new ubuntu 11.10 too ??


HELP,, I won't use windows ,, I'll sell my computer if I have to ..

---

### Post by Blasphemist on 2011-10-14
> **eb sol said:**
> NOW I can NOT install the new ubuntu 11.10 too ??


HELP,, I won't use windows ,, I'll sell my computer if I have to ..

You should create a new thread on this since this one is marked solved and you aren't the original requester.

Please be as specific as possible about exactly what is happening and what your platform is.

---

### Post by eb sol on 2011-10-25
Solved in this link : [http://ubuntuforums.org/showthread.php?p=11390325](http://ubuntuforums.org/showthread.php?p=11390325)

Cheers

---

