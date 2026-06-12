---
title: "Unable to install Ubuntu 7.10 on HP Pavilion dv6000"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by manmohanpv on 2008-01-08
Hi Frnds,

Is there any work around for this problem? I'm unable to install ubuntu 7.10 on my brand new HP Pavilion dv6000 laptop, system details and error messages below:-

System Manufacturer: Hewlett-Packard
System Model: HP Pavilion dv6000 (RV010UA#ABA)
BIOS: PhoenixBIOS 4.0 Release 6.1
Processor: AMD Turion(tm) 64 X2 Mobile Technology TL-50 (2 CPUs), ~1.6GHz

Steps to Reproduce:-

Try to install Ubuntu 7.10 in the system

Defect:
Unable to load Ubuntu 7.10 on HP Pavilion dv6000 (RV010UA#ABA)

System Output for your information
################

0.660000 ] PCI: BIOS BUG #81(49435000) found
...........................

*Starting common Unix Printing System: cupsd

[108.020000] bcm43xxx: Error : Microcode "bcm43xxx_microcode5.fw" is not available, load failed.

Please suggest.

-thanks
manmohanpv

---

### Post by Sef on 2008-01-08
1) Did you md5sum the download? (verifies a good download)

2) Did you burn the iso as an iso? (not as data)

3) Did you burn the iso at 4x or less? (faster can corrupt the burn)

4) At the start/install menu, go down to 'Check Disk for Errors'?

---

### Post by manmohanpv on 2008-01-09
Hi Sef

i got the both 7.04 and 7.10 CD from canonical. 

i'm not sure why both are not working on HP dv6000 series.

Any suggestions?

-thanks
manmohan

---

### Post by locash on 2008-01-09
try running the live disc is safe graphics mode 

it is the second item to choose from the top of the text menu

---

### Post by Gina on 2008-01-09
> [108.020000] bcm43xxx: Error : Microcode "bcm43xxx_microcode5.fw" is not available, load failed.
This is due to it detecting a bcm43xx wireless device.  I got that with my laptop.  The boot error does't matter and you can download and install the firmware later using the Restricted Drivers Manager.

---

### Post by Partyboi2 on 2008-01-09
Have you tried to update your bios?

---

### Post by slafko on 2008-01-09
You have to use "noapic" (grub options) to load LiveCD. I also have dv6000 and that solved my problem.

---

### Post by manmohanpv on 2008-01-10
Hi Slafko,

can u give me the details on how u solved it?

How should i use that grub option (>grub>noapic)

how can i specify the root, kernel path and root file system to boot from 7.10 cd, at grub prompt?

please suggest

-thanks
manmohan

---

### Post by Partyboi2 on 2008-01-10
With the Live cd, when you get to the main menu 
Press F6 for boot options
at the end of the line add
```
noapic
```
then press enter 
If that works you will need to add it to grub menu lst. Post back if it works and someone will tell you how to add it to grub menu.lst

---

### Post by mioemi2000 on 2008-03-01
:popcorn::popcorn::popcorn::popcorn:

I tried it out it still didn't work for me. All I saw was a dark screen with dashes

---

### Post by Pumalite on 2008-03-01
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by mioemi2000 on 2008-03-03
With the Live cd, when you get to the main menu
Scroll to:
**[SIZE="6"]Start Ubuntu in safe graphics mode[/SIZE]**

Press F6 for boot options
at the end of the line add:

noapic

---

### Post by rebshalom on 2008-03-03
I had the same problem on an HP tx1320us. I still have not added noapic but now I will. The other problem I still have is that I cannot get to any USB ports or the ethernet port. As a result I cannot get to the internet to do any maintenance downloads.  I assume all other ports are also inoperable. Any suggestions?

---

### Post by hojthojt on 2008-03-04
Hi,
I have a tx1151ea which is running Gutsy 7.10 AMD64 since a week back. I have BIOS version F.1D and use the following kernel options to make it boot correctly:

noapic irqpoll noirqdebug

I do not know how similar my tx1151ea is to tx1320us and dv6000 respectively, but from reading the forums here, there seems to be some general problem with HP Pavilion laptops / The crappy HP BIOS / Gutsy 7.10 kernel

But for me it works almost fine with the kernel options above and the latest BIOS version (still have some issues with suspend and hibernate).

regards
hojthojt

PS There is a lot of useful info on running Ubuntu on the HP  tx1000 series notebooks in this thread:
[http://ubuntuforums.org/showthread.php?t=442483]("http://ubuntuforums.org/showthread.php?t=442483")

---

### Post by Nordkraft on 2008-03-04
I have such a laptop myself and I thought I just might add that a lot of the problems I ran into initially in setting up Gutsy were taken care of by blacklisting the webcamera-module "uvcvideo", as is mentioned in the wiki linked to above  as well [https://wiki.ubuntu.com/HP_dv6000_Series]("https://wiki.ubuntu.com/HP_dv6000_Series")

:)

---

### Post by deos on 2008-03-06
i also have a pavilion dv6000, and the problem is the same. after boot i can see just a dark screen and nothing else. to update Bios is not a solution. i spoke with some guys from HP and they told me than on dv6000 series we can use just windows OS :(

---

### Post by Pumalite on 2008-03-06
What link have you used to install? Did you finished installation and on reboot you have a blank screen?

---

### Post by firecrow8 on 2008-03-06
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=713309](http://ubuntuforums.org/showthread.php?t=713309) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have the same issue with a Compaq Presario F500 which is also made by HP and very similar to the presario. 

the blank screen with lines.

have posted some details on another thread of my problem




still looking for boot options that work with the live cd

---

### Post by Nordkraft on 2008-03-07
> **deos said:**
> i also have a pavilion dv6000, and the problem is the same. after boot i can see just a dark screen and nothing else. to update Bios is not a solution. i spoke with some guys from HP and they told me than on dv6000 series we can use just windows OS :(

Well, that's by no means the whole story. The thing is, Gutsy can require some "extra" work in being set up on the dv6000-series (and some others as well, as far as I can gather) - a quick search in the forums will make that quite clear. However, if you follow some of the methods around dealing for instance with boot options, and install method etc. Gutsy can DEFINITELY be set up on a dv6000. I'm running this exact setup myself which is why I'm so sure of it :)

---

