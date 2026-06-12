---
title: "Lucid bug or hardware failure?"
date: 2010-01-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by infamousrev on 2010-01-04
Hello,

I noticed a strange phenomenon:

Sometimes my screens suddenly turns 100% green, or 100% [RANDOM COLOR].

The underlying system will keep on running but it will simply display nothing. using ctrl+alt+F? does not work either.

The only way to bring my screen back is putting the laptop in suspend by closing the lid and then reopening it.

lspci
> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)



I searched the error logs, but it shows nothing.



One reason for me to expect a hardware failure is that my arch linux has the exact same problem.

Both are using the 2.6.32 kernel though

---

### Post by GeorgeVita on 2010-01-05
Hi **infamousrev**, running various versions of Ubuntu on my EeePc 1000h I noticed this problem ONLY on** LL a1+updates** only. Last days is better (any update?). 

Another problem I can reproduce is a 'psychedelic' result to my screen after trying ```
lshw | grep -i ethernet
``` Screen capture at [http://ubuntuforums.org/showpost.php?p=8576581&postcount=17](http://ubuntuforums.org/showpost.php?p=8576581&postcount=17)
Can you test it?

Possibly VGA drivers not working well...

Regards,
George

---

### Post by Ibidem on 2010-01-17
Acer Aspire One, same graphics (945GME), same bug.
I ran lshw and it was alright as long as it was just showing the (PCI) message,
but as soon as it started printing output the screen turned psychedelic (looked like an oil slick or something).
The first output of lshw is "screen", so I think it's something with how it probes hardware.
But I grabbed a screenshot and everything looks normal in it, so...

Anyone have a clue here?
Is this the Intel drivers, or is it lshw?

Ibidem

---

### Post by GeorgeVita on 2010-01-20
The 'psychedelic' effect ([photo here]("http://ubuntuforums.org/showpost.php?p=8576581&postcount=17")) remains on DailyLive 19-Jan, but it resumes correctly when **screensaver** takes control!
G

---

### Post by ranch hand on 2010-01-20
Oh Wow, pretty colors man, far out.

I have not had this, yet, in 10.04 really.  Did in 9.10.

Maybe todays update with the new kernel will help.

---

### Post by dino99 on 2010-01-20
both on startup & shutdown, i have a black screen with 4 columns of about 20 lines with fullfilled color dots: lenght up to 15 cm, widht of 1 cm.

That seem to slow down the process but there is nothing logged.

---

### Post by miriad on 2010-01-21
Same problem for me here, Has anyone posted a bug about this?

---

### Post by goldsniper on 2010-01-21
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

I got flickering and then blank screen after some time... even alt+F1 are blank! Not having this before .. except in Lucid, 

Using Compaq Presario V3000

---

### Post by ranch hand on 2010-01-21
> **goldsniper said:**
> ```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```I got flickering and then blank screen after some time... even alt+F1 are blank! Not having this before .. except in Lucid, 

Using Compaq Presario V3000

Welcome to testing.  This is not, by a long way, a stable release.  You were warned on the first screen of the install disk.

Remember to breath, don't panic, keep updating, file bugs, and most important if you want to stay healthy - HAVE FUN.

---

### Post by goldsniper on 2010-01-22
Thank you ranch hand..

I know this is still in Alpha stage, and although I seldom post, but I was testing Lucid since before it was even alpha 1 :D . And it also goes back to Hardy too. :popcorn:

p/s : My English was not good. Sorry if misinterpreted.

---

### Post by ranch hand on 2010-01-22
> **goldsniper said:**
> Thank you ranch hand..

I know this is still in Alpha stage, and although I seldom post, but I was testing Lucid since before it was even alpha 1 :D . And it also goes back to Hardy too. :popcorn:

p/s : My English was not good. Sorry if misinterpreted.
I have no idea what your language is but I can tell you that your english is great compared to my skill at yours.

Don't worry about it.

The flickering seems to be a "feature" for now.  I have had a few days where it did not flicker but they are far apart.  I am sure this will be corrected.

---

### Post by goldsniper on 2010-02-02
I hope this would be resolved ASAP so that i could also test lucid! :KS

---

### Post by ranch hand on 2010-02-02
Have you been upgrading?

Maybe you should give more information on your computer like what is in my signature (see below).

If you can I would check the System>Preferences>Appearance>Visual Effects and set them at none.  This may or may not help but I would try it.

---

### Post by goldsniper on 2010-02-04
> **ranch hand said:**
> Have you been upgrading?

Maybe you should give more information on your computer like what is in my signature (see below).

If you can I would check the System>Preferences>Appearance>Visual Effects and set them at none.  This may or may not help but I would try it.


Nope. No upgrade what-so-ever. It stills on the same hardware I used to install Gutsy, Gutsy, Intrepid and Karmic

I wonder if this is a kernel related problem?

---

### Post by ranch hand on 2010-02-04
I doubt that it is in the kernel because of the number of x updates.  I suspect that all the x related stuff is not up with the kernel yet and that is what is causing the problem.

---

### Post by rv65 on 2010-02-05
My Laptop has an ATI mobility radeon x300 and Lucid isn't able to make it to the login screen. It has errors and one of the IRQ's isn't connected.

---

### Post by goldsniper on 2010-02-12
I'm on LUCID right now...! and the problem is no longer exist.

using  2.6.32-13-generic kernel with compiz fully enable and looking good. 

using the latest xserver-xorg-video-intel
X.Org X server -- Intel i8xx, i9xx display driver came with the kernel:

2:2.9.1-1ubuntu4(lucid)

---

### Post by GeorgeVita on 2010-02-13
> **GeorgeVita said:**
> ... the 'psychedelic' result to my screen after trying ```
lshw | grep -i ethernet
```
Above still exists on EeePC 1000H (LL daily live of 12-Feb plus today updates).
[IMG]http://acomelectronics.com/GeorgeVita/various/LLpsychedelic.jpg[/IMG]

Regards,
George

---

### Post by GeorgeVita on 2010-03-14
Hi again and sorry for the 'sequential' photo posting.
Just tested Ubuntu LL liveUSB of 13-Mar-10 and the display goes 'psychedelic' after running a terminal command 
```
sudo lshw
```


[IMG]http://acomelectronics.com/GeorgeVita/various/LLmar13.jpg[/IMG]

Can you suggest what package could cause this in order to search/submit a 'bug' report?

Regards,
George

---

### Post by GeorgeVita on 2010-03-19
I have better 'psychedelic' effects with newer LL b1 desktop colors as
executing a '**sudo lshw**' command from terminal makes my screen funny!

>>> **the problem still exists on LL beta 1** (from liveUSB).

>>> can anybody test it on another system? (I am using EeePC 1000H netbook)
>>> and/or suggest what package could cause this in order to search/submit a 'bug' report?

Regards,
George

---

### Post by cariboo on 2010-03-19
I'm using a Compaq Mini 110 with the 945 chipset. I don't have the psychedelic colors when running the same command. I running Lucid UNR. see screen-shot

---

### Post by GeorgeVita on 2010-03-19
Hi **cariboo907**,
I am using LL desktop from LiveUSB stick (.iso -> USB startup creator).
Any lshw command creates the trouble.

I will test tomorrow LL B1 desktop on a Compag mini 110 (as yours).

Regards,
George

---

### Post by GeorgeVita on 2010-03-19
> **GeorgeVita said:**
> ...**Any lshw** command creates the trouble.

Sorry, simple lshw (as that tested by you) works!

Can you try a: ```
sudo lshw
```
Thanks,
George

Edit: **ctrl+alt+F2** and then **alt+left** arrow and again **alt+left** arrow redraws screen to normal
as also screensaver.

---

### Post by Mars73 on 2010-03-19
> **GeorgeVita said:**
> Sorry, simple lshw (as that tested by you) works!

Can you try a: ```
sudo lshw
```
Thanks,
George

Same problem here.
Installed the Beta on my HP 6820s laptop with Ati Mobility 1350 freshly and noticed flickering and when moving or opening a window the screen goes weird and very light. No response anymore though hitting crtl+alt+del a few times gets me back to normal desktop but after a few seconds it starts again.
I was anxious to test it but I can't even get that far.
Problem is with or without desktop effects on.
Luckily it's a spare laptop, I wouldn't want this on my production machine (it's still beta I know)

---

### Post by cariboo on 2010-03-19
I just had the same thing happen on my netbook when I ran:

```
sudo lshw -C bluetooth
```

Strangely enough, when I take a screen-shot, the desktop looks normal.

---

### Post by GeorgeVita on 2010-03-19
> **cariboo907 said:**
> ...Strangely enough, when I take a screen-shot, the desktop looks normal.

Yes, screensaver or use of ctrl+alt+F2 and then back with 2x ctrl+left 'redraws' correctly the screen. Can you suggest any possible package in order to search launchpad?

Regards,
George

(P.S. my fotos are via mobile phone)

---

### Post by davidryderuk on 2010-03-19
Hi,
I have the same problem on my eeepc 1000 when running the lucid beta off a LiveUSB stick. However I do not get the problem if I boot using the "nomodeset" boot parameter.

In addition when I compare the kernel.log files on each boot I found that the following lines are absent when using the "nomodeset" boot parameter (they are also absent when booting karmic normally).

Hope this helps.

```
[drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 54
Mar 19 23:06:16 ubuntu kernel: [    6.435123] [drm:edid_is_valid] *ERROR* Raw EDID:
Mar 19 23:06:16 ubuntu kernel: [    6.435131] <3>00 ff ff ff ff ff ff 00 22 64 e9 03 00 00 00 00  ........"d......
Mar 19 23:06:16 ubuntu kernel: [    6.435138] <3>12 12 01 03 80 16 0d 78 0a 86 26 94 57 51 90 27  .......x..&.WQ.'
Mar 19 23:06:16 ubuntu kernel: [    6.435143] <3>21 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01  !OT.............
Mar 19 23:06:16 ubuntu kernel: [    6.435149] <3>01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23  ..........@X. 5#
Mar 19 23:06:16 ubuntu kernel: [    6.435155] <3>45 00 dc 81 00 00 00 19 16 14 00 d8 40 58 26 20  E...........@X& 
Mar 19 23:06:16 ubuntu kernel: [    6.435161] <3>5d 23 15 04 dc 81 00 00 00 00 00 00 00 fe 00 00  ]#..............
Mar 19 23:06:16 ubuntu kernel: [    6.435167] <3>00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe  ................
Mar 19 23:06:16 ubuntu kernel: [    6.435173] <3>00 00 00 00 00 00 00 00 00 01 ff 00 00 00 00 ff  ................
Mar 19 23:06:16 ubuntu kernel: [    6.435177] 
Mar 19 23:06:16 ubuntu kernel: [    6.536956] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 130
Mar 19 23:06:16 ubuntu kernel: [    6.536962] [drm:edid_is_valid] *ERROR* Raw EDID:
Mar 19 23:06:16 ubuntu kernel: [    6.536968] <3>00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff  ................
Mar 19 23:06:16 ubuntu kernel: [    6.536974] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
Mar 19 23:06:16 ubuntu kernel: [    6.536980] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
Mar 19 23:06:16 ubuntu kernel: [    6.536986] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
Mar 19 23:06:16 ubuntu kernel: [    6.536991] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
Mar 19 23:06:16 ubuntu kernel: [    6.536997] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
Mar 19 23:06:16 ubuntu kernel: [    6.537007] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
Mar 19 23:06:16 ubuntu kernel: [    6.537015] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
Mar 19 23:06:16 ubuntu kernel: [    6.537021] 
Mar 19 23:06:16 ubuntu kernel: [    6.547341] fb0: inteldrmfb frame buffer device
Mar 19 23:06:16 ubuntu kernel: [    6.547348] registered panic notifier
Mar 19 23:06:16 ubuntu kernel: [    6.547365] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
```

---

### Post by pressureman on 2010-03-19
I can also trigger the psychedelic effects on my Thinkpad T500 (switchable Intel/ATI graphics, but running with ATI card disabled). In order to get the trippy colours, I have to execute "sudo lshw". Running it as a non-root user doesn't trigger it.

```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

I also get regular (but infrequent) screen "jumps". It's like a loss of vsync (which isn't possible on an LCD, but that's what it looks like). Kernel package 2.6.32-15 didn't have the problem, but anything since then has.

---

### Post by GeorgeVita on 2010-03-19
Closest bug found: [#528974]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/528974")

Regards,
George

---

