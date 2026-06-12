---
title: "Ubuntu 10.10 [64 Bit] hang on boot"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by m_e_71 on 2011-01-08
Hi,

I upgraded my ubuntu 64 bit from 10.04 to 10.10 using the update manager on my Laptop ASUS, F80Series, 4Gb Ram, CPU Duo T8100.

Ubuntu 10.10 could never boot: it always gets stuck. I tried the "recovery mode". The last two messages written, before getting stuck are:

[1.729408 ] NET: Registered Protocol Family 1
[1.730110] Registered Taskstat Version 1

Any ideas?

Thanks,

Marco

---

### Post by SeiryuZ on 2011-01-24
Hi everyone,

I'm currently having the same problem. The problem occur when I'm using linux kernel above 6.32 ( in my case, all 6.35 variants ). I can't seem to boot into ubuntu with those kernels, it only shows blank screen and white cursor blinking in the top left of the monitor. Running the "recovery mode" of the kernel, will print the same message as m_e_71 and it stuck.

[some number] Registered Taskstat Version 1


for this reason, I've been holding back to upgrade to 10.10, since I cannot boot into the live CD at all. It got stuck with the same message. I assume that the live CD comes with kernel above 6.32 that works fine with my laptop.

My laptop:

ASUS-F81SE
2 GB RAM
Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
M92 [Mobility Radeon HD 4500 Series]

32 Bit Ubuntu 10.04


All helps/hints/directions will be much appreciated. Been struggling with this issues for a month. Decided that I need help, so I finally make an account here.


Steven

---

### Post by near31 on 2011-01-24
Hi,

I thought I was alone with this problem... And in fact I am not ^^ I have exactly the same problem since I have upgraded to ubuntu 10.10... Ubuntu can't run at all...

My laptop:
ASUS-X71SLseries
3 GB RAM
Intel(R) Core(TM)2 Duo P7350 CPU  @ 2.10GHz
Nvidia GeForce 9300m GS 
ubuntu 64bit

I hope there is a solution...

thanks

Maxime

---

### Post by SeiryuZ on 2011-01-24
Hi,


I can't help to see that all (3 persons) that has this problems are using ASUS laptop. I'm really curious whether ASUS specific hardware are causing the problem. In the meantime, I'm going to try to install Ubuntu 10.10 in another ASUS laptop and see whether this is the case.

If anyone has hints/directions/solutions for us, it will be greatly appreciated


Steven

---

### Post by m_e_71 on 2011-01-27
Hi,

Having seen that the issue seems to be related to ASUS notebooks, I tried to upgrade to latest available BIOS (F80SAS.220).

It did not work.

Marco

---

### Post by coalcracker on 2011-02-03
I have an ASUS F50S laptop and upgraded from 10.04 to 10.10 and have the same exact problem. I can boot into kernel 2.6.32-28 but not 2.6.35-25 or 2.6.35-26. I attached the Results.txt from the boot script. If anyone can figure out what's going on it would be greatly appreciated.

---

### Post by Janghou on 2011-02-08
> Ubuntu 10.10 could never boot: it always gets stuck. I tried the "recovery mode". The last two messages written, before getting stuck are:

[1.729408 ] NET: Registered Protocol Family 1
[1.730110] Registered Taskstat Version 1

I had the same with my Acer and a cheap/faulty USB hub. I removed it and Ubuntu rebooted again.

So remove all USB cables and see if problem persists.

---

### Post by P4man on 2011-02-08
Try some kernel options, like nomodeset and possibly acpi_osi. See my signature for details.

---

### Post by FrostByghte on 2011-02-08
ASUS F50S here.  Same issue.  Using nolapic or apci=off gets me a bit further down the road. After selection the laptop hangs waiting for roughly 3 to 4 minutes.  Then I get a ton of "stdin: error 0" and finally "Unable to find a medium containing a live file system"  

After reading a bit, is this a problem with the DVD drive or perhaps the DVD/CD itself? If I get time I'll burn another CD and try an external drive instead of the internal one.

Also I've unplugged all USB devices, this didn't solve anything for me.

---

### Post by FrostByghte on 2011-02-08
Ok...I simply connected my external DVD drive. Moved the 10.10 64bit install disc to it, and booted up.  Booting is MUCH faster now. However, there is still an issue as I have to use "nolapic" There is no longer a 4 min wait after specifying boot options. 

The internal drive works PERFECTLY in Windows 7.  No issues at all.  Just throwing that in there.

My suggestions would be try installing from flash or grab an external drive if this is causing you issues. I'm at the Welcome screen now in Ubuntu, so I'm going to try and finish this up.  I hope this helps someone...should we post a bug report on this?

---

### Post by m_e_71 on 2011-02-17
Hi,

As the last message was 

[1.729408 ] NET: Registered Protocol Family 1
[1.730110] Registered Taskstat Version 1

I compiled a new 10.10 kernel without Taskstat. It did not fix the issue. Ubuntu 10.10 continues to hang on boot. 

Any (other) ideas?

Marco

---

### Post by FrostByghte on 2011-02-17
Marco,

I listed fixes that worked for me.  Did you try those?

---

### Post by m_e_71 on 2011-02-18
I added nolapic to boot option to the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" in the /etc/default/grub. Then I run update-grub.

Catastrophic. No way to boot with any kernel. Not even with 10.04. 

I did not try to boot from DVD. I don't consider it a real, practical solution.

Bye,

Marco

---

### Post by P4man on 2011-02-18
> **m_e_71 said:**
> I added nolapic to boot option to the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" in the /etc/default/grub. Then I run update-grub.

Catastrophic. No way to boot with any kernel. Not even with 10.04. 

I did not try to boot from DVD. I don't consider it a real, practical solution.

Bye,

Marco

Just edit the grub entry again from within grub menu, remove nolapic. If you are not sure how, see my signature again, the procedure to temporarily modify kernel option on in installed ubuntu.

---

### Post by FrostByghte on 2011-02-18
Sorry to hear it didn't work.  Are you using an Asus laptop? You could try some of the other vars and see if they help.  I just kept going through them all until I could boot.  My system is now installed and running fine.  I'm not using any CD or image file to boot.

---

### Post by m_e_71 on 2011-02-19
Yes I have  Laptop ASUS, F80Series, 4Gb Ram, CPU Duo T8100.
I removed the parameter and I updated grub. 10.04 works again, but 10.10 continue to hang on boot.

[SIZE=6]**I WILL NEVER BUY AN ASUS AGAIN!**[/SIZE]

---

### Post by FrostByghte on 2011-02-19
I think Asus makes some AWESOME motherboards, but I have had nothing but trouble from their laptop products.  On mine the sound crackles constantly with every driver I try under windows 7.  Also the screen flickers, and I sent it back twice for repairs.  Finally I just pulled the bezel off the screen and there is a wire at the bottom of the damn thing I just wiggle when it starts to flicker and all is well. :(

Sound works fine under linux.  I wouldn't give up, just keep plugging in options....make sure and unplug all your USB stuff and I finally had to get around the internal CD rom with an external unit.

---

### Post by richmurphy on 2011-02-22
Exactly the same issue with my Asus Pro61S.  Previously had 10.04 working without a hitch (before my HDD died!).  This is a fresh install not an upgraded kernel.  I'm not sure if this is significant but the message prior is "PM: Resume from disk failed".

---

### Post by m_e_71 on 2011-02-27
Ubuntu 10.10 does not boot on several ASUS Laptops. 
- I tried with fresh kernel and recompiled ones. 
- I upgraded the BIOS to the lasted available release
- I tried various Linux boot options
- I removed all USB devices
- I tried with the CD boot
NOTHING worked. The latest message printed seems not to be relevant.
Any ideas?
Bye,
Marco

---

### Post by coalcracker on 2011-03-04
For all those that have the Asus laptop, I added the acpi=off to the grub config file and I am now able to boot into kernel 2.6.35-28

---

### Post by m_e_71 on 2011-03-07
I modified the two following lines in the file /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
GRUB_CMDLINE_LINUX="acpi=off"

then I run update-grub.

Finally my awful F80S laptop works with ubuntu 10.10. 

ANYHOW: now Ubuntu 10.10 does not suspend, hibernate, switch off automatically.

I think that the only solution could be to re-compile a kernel with asus-acpi driver, which is not enabled in 10.10. Did anyone try it?

Thanks,

Marco

---

### Post by cronco on 2011-03-17
Hello, been having the same issue on an ASUS X71SL laptop. There's a bug on launchpad related to it (actually more) [https://bugs.launchpad.net/bugs/626622](https://bugs.launchpad.net/bugs/626622), but there's no advance on it.

It indeed seems to be a lapic issue, and one specific to Ubuntu, as the latest openSuse, using 2.6.37 boots on my pc (try to see if it does for yours)

Oh, and acpi=off is no solution :)

Best thing is to get a launchpad account and start airing your grievances on that bug report, maybe we'll get some support from Canonical then (if they see a large number of people are affected by the bug)

---

### Post by razorxpress on 2011-07-14
Hi all, I had similar problem.

I set

pci=noacpi acpi_osi=linux

After appending this at GRUB_CMDLINE_LINUX_DEFAULT at /etc/default/grub and doing a sudo update-grub it worked. I even had installed smcfancontrol.0.3.2.zip which I don't no is required anymore. Since the default driver for dell obtained by enabling it from Additional Drivers is buggy for me. It completely disables 3D support, however fan seemed to be cool. So to find a better solution for fans, I installed smcfancontrol which I think did not work. The setting acpi_osi=linux was what helped my laptop switch fan from being cooler and wake up when needed. However to actually boot from hanging, pci=noacpi worked. I have not tested doing a hibernate and other, but three of my major problems of having a crappy graphics support, not booting to ubuntu 64bit and noisy fan are all solved.

Cheers!!

---

### Post by m_e_71 on 2011-07-16
**THANK YOU razorxpress!**

I opened this thread in JANUARY 2011 and "pci=noacpi acpi_osi=linux" is the solution to the hang on boot on my ASUS awful laptop avoing disabling ACPI.


Anyway: I am going to buy another laptop. It won't be an ASUS for sure.

---

### Post by Daredevil76 on 2011-08-23
Hello,

I have a Asus N90 and i have exactly the same probleme but when i desactivate the Wifi in the Bios Ubuntu start normally, 

On ubuntu 11.04

I hope that can help you.

Sorry for my english.

---

### Post by Laerten on 2011-11-18
Try follow [this discussion]("http://translate.google.it/translate?hl=it&sl=it&tl=en&u=http%3A%2F%2Fforum.ubuntu-it.org%2Findex.php%2Ftopic%2C487071.msg3860260.html")!
[http://translate.google.it/translate?hl=it&sl=it&tl=en&u=http%3A%2F%2Fforum.ubuntu-it.org%2Findex.php%2Ftopic%2C487071.msg3860260.html](http://translate.google.it/translate?hl=it&sl=it&tl=en&u=http%3A%2F%2Fforum.ubuntu-it.org%2Findex.php%2Ftopic%2C487071.msg3860260.html)

---

### Post by VeRychard on 2012-04-17
I SOLVED IT!!!!!

If you have an Asus laptop, or you have this option in BIOS CHECK IT!!!!!

Go to bios >
Security> I / O interface Security> [COLOR=red]"New interface card"[/COLOR] or so. SET IT TO LOCKED!!! 

After that everything went fine for me ^^

Booted properly

Hope it helps :)

---

### Post by papypapou on 2012-04-24
:p Yes it helps!

MANY THANKS TO YOU !

I have an Assus X71SL and no more problem !

---

### Post by emerson1234567890 on 2012-04-26
Thanks!!!!  It worked!!!!!!!!!

I used to set the parameters to nolapic when I install Ubuntu.  Now I don't need to!!!

Specs: ASUS F81se(descriptive enough)

You:guitar:

---

### Post by faizal23 on 2012-07-31
> **VeRychard said:**
> I SOLVED IT!!!!!

If you have an Asus laptop, or you have this option in BIOS CHECK IT!!!!!

Go to bios >
Security> I / O interface Security> [COLOR=red]"New interface card"[/COLOR] or so. SET IT TO LOCKED!!! 

After that everything went fine for me ^^

Booted properly

Hope it helps :)
  
thanks it's work for me  \\:D/ i'm using AsusF80S after a few years i can't update my ubuntu     :guitar:

---

### Post by maxlath on 2013-03-01
.

---

### Post by maxlath on 2013-03-01
> **VeRychard said:**
> I SOLVED IT!!!!!

Go to bios >
Security> I / O interface Security> [COLOR=red]"New interface card"[/COLOR] or so. SET IT TO LOCKED!!! 



Sir, you did save my laptop and my nerves, please accept my eternal gratitude! :guitar:

---

