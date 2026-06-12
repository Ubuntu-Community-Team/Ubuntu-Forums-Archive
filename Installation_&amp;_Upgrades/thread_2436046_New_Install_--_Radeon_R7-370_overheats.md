---
title: "New Install -- Radeon R7-370 overheats"
date: 2020-01-30
forum: Installation &amp; Upgrades
---

### Post by awaykent on 2020-01-30
I was using Win7-64 until the latest (and last) patch broke the internet connection software.  So as I have no desire to pay for the privilege of becoming an unpaid Microsoft alpha tester for Win10,  I installed Ubuntu on my new SSD (I tried Mint first on a friend's recommendation,  but my steam games do not all play nicely with it and it had the same issues as related below).  

My problem is that I have a Radeon R7-370 2g (Pitcairn 1st gen),  and even after trying to load the appropriate amd driver there appears to be no way to force the gpu fan to run.  As the computer shuts down due to heat,  THEN the gpu fan runs but not before then.  So most game programs are not playable (Factorio,  HoI4,  MoO1,  MoO2 are what I have tried)

Any suggestions?   I am on an extremely limited income atm due to knee surgery recovery (hard to walk/stand for more than 20 minutes),  so I am trying to keep my current card until I can afford a new one   I am willing to learn to write code if needed,  I just do not know if controlling it is impossible.  I used to use Fortran (and IBM 1401 fortrash),  Algpol,  Pascal,  Cobol,  up until the late 1980's,  but "Dammit I am a chemist,  not a programmer, Jim!!!    So my need to do coding has not been high.

-Computer-
Processor        : AMD FX(tm)-6300 Six-Core Processor
Memory        : 12250MB (2984MB used)
Machine Type        : Desktop
Operating System        : Ubuntu 18.04.3 LTS
User Name        : ken (Ken)
Date/Time        : Thu 30 Jan 2020 09:56:33 AM EST
-Display-
Resolution        : 1920x1080 pixels
OpenGL Renderer        : (Unknown)
X11 Vendor        : The X.Org Foundation
-Audio Devices-
Audio Adapter        : HDA-Intel - HDA ATI SB
Audio Adapter        : HDA-Intel - HDA ATI HDMI
-Input Devices-
 Power Button
 Power Button
 SEM USB Keyboard
 SEM USB Keyboard Consumer Control
 SEM USB Keyboard System Control
 PixArt USB Optical Mouse
 HDA ATI HDMI HDMI/DP,pcm:3
 HDA ATI HDMI HDMI/DP,pcm:7
 HDA ATI HDMI HDMI/DP,pcm:8
 HDA ATI HDMI HDMI/DP,pcm:9
 HDA ATI HDMI HDMI/DP,pcm:10
 HDA ATI HDMI HDMI/DP,pcm:11
 HDA ATI SB Front Mic
 HDA ATI SB Rear Mic
 HDA ATI SB Line
 HDA ATI SB Line Out
 HDA ATI SB Front Headphone
-Printers-
No printers found
-SCSI Disks-
HL-DT-ST DVDRAM GH22NS40
ATA Samsung SSD 860

---

### Post by CelticWarrior on 2020-01-30
```
 OpenGL Renderer        : (Unknown)
```

This is a symptom of serious issues with graphics drivers.

With AMD you actually don't need to install any drivers nowadays. So, please describe what you did to "load the appropriate amd driver". And, by the way, you probably need to disable Secure Boot in UEFi settings if you tried to install some proprietary drivers.

---

### Post by awaykent on 2020-01-30
Mind you I reinstalled Ubuntu...   then I wrote the post above.   As to what I did...  After searching on Duckduckg for any relevant information,   I downloaded the newest patch for ubuntu,  and followed the terminal instructions I found in relevant articles on the subject.  Since I reinstalled to clear any issues, that should not be an issue.  As for my OpenGL Renderer being "unknown",   that is what I get from hardinfo...  since formatting and reinstalling...

---

### Post by CelticWarrior on 2020-01-30
Again, if you installed the proprietary drivers from AMD, you need to disable Secure Boot as that prevents those drivers from loading and that typically causes the symptom described above. And usually you don't need to install anything else for AMD graphics.

---

### Post by awaykent on 2020-01-30
Well,  I am researching how to do that (disable secure boot)...  but no idea yet how to do this.

---

### Post by CelticWarrior on 2020-01-30
It's in UEFI settings and how to do it depends on your hardware. So, search your user's manual (or your make/model + disable secure boot UEFI).

---

### Post by awaykent on 2020-01-30
I assume you mean my motherboard,  for which I can find no references to uefi.  I build my own computers and have since 1990 or so....  I am trying to ask gigabyte tech support,  but I may have to tear apart the computer to get the serial numbers they want on their form.

After a few hours of searching,  I found this article:  [http://itadminguide.com/disable-secure-boot-in-ubuntu/](http://itadminguide.com/disable-secure-boot-in-ubuntu/)   Doing what it tells me to do,  I get  "EFI variables are not supported on this system" when I finally enter the command to disable secure boot ([COLOR=#ff6600] sudo mokutil –disable-validation )....  Over 20 hours of searching for a way to install the driver that will allow me to force my gpu fan to run...  [/COLOR]

---

### Post by rsteinmetz70112 on 2020-01-30
> **awaykent said:**
> I assume you mean my motherboard,  for which I can find no references to uefi.  I build my own computers and have since 1990 or so....  I am trying to ask gigabyte tech support,  but I may have to tear apart the computer to get the serial numbers they want on their form.

dmidecode will probably give you the information you need without a screwdriver.

---

### Post by awaykent on 2020-01-30
Well per Gigabyte tech support,  my motherboard does not have uefi support (as I thought based on the bios screens),  so the suggestion that I needed to disable it was simply another few hours of wasted time....  I guess I will re-reinstall tonight since following AMD's directions for the legacy driver is still missing dependencies,  they do not exist.  I might as well do the latest ubuntu version rather than 18....  No games until I heal enough so I can get work for a few months...

---

### Post by QIII on 2020-01-30
The legacy driver, if by that you mean fglrx, is gone.

The Linux kernel now contains two modules (open-source drivers, if you will) -- radeon and amdgpu -- one or the other of which is loaded depending on which supports the hardware installed.  You should not have to install anything from AMD.

If your hardware is supported by amdgpu, then you may be able to install AMDGPU-PRO, which is a proprietary overlay.  But it is not likely that you would really need it.

---

### Post by awaykent on 2020-02-01
Okay,  I reinstalled Ubuntu,  tried to make sure I had the open source radeon drivers loaded,  since the amdgpu one will not work with 1st gen cards like my R7-370.  Tried a Hearts of Iron 4 game at a lower res,  minimum video settings,  the gpu STILL overheated in 2 minutes of actually playing the game as the damn gpu fan will not work no matter what I do.  It worked if I set it manually in Win7 -64....

---

### Post by QIII on 2020-02-01
Could you give us the make/manufacturer of the machine -- or more particularly the motherboard.

Some Win 7 systems were built with hardware that gave GPU fan control to the OS.

---

### Post by awaykent on 2020-02-01
Gigabyte 
[TABLE]
[TR]
[TD="align: right"]Product Name: [/TD]
 							[TD="align: left"]GA-78LMT-USB3[/TD]
 						[/TR]
 								[TR]
 									[TD="align: right"]BIOS Ver: [/TD]
 									[TD="align: left"]F2[/TD]
[/TR]
[/TABLE]
Per their tech support there is no uefi support in this unit.  I have tried it with the "smart" fan control (really for cpu not gpu) both off and on.

This was a system I built myself and upgrade as I have cash.  The last upgrade is the ssd I just added,  previously it was the Mobo,  8 meg more ram and the Radeon R7-370 as I upgraded from Win7-32 to Win7-64 (have 3 license family pack).

Later tonight I will see if I can power the fans directly from the power supply so they run continuously.

I was using the catalyst control center in Win7,  and manually set the fan to 70% to keep the heat below 45C.

---

### Post by kurt18947 on 2020-02-01
I wonder if that video card / motherboard / Ubuntu don't want to play nice together. Do you have another video card you could try? Which version of Ubuntu are you trying? Maybe try 19.10 for the latest hardware support. Ryzen systems have had issues with the current LTS 18.04 but your processor/motherboard don't seem so new that they should have problems. QIII may be onto the problem, that card expects OS support that Ubuntu doesn't offer.

---

### Post by awaykent on 2020-02-01
I am using 18.04 lts atm.

---

### Post by Autodave on 2020-02-01
You should be able to do a clean install of 18.04 or newer and then NOT install anything for the GPU to work properly.  The Radeon driver should already be present when the OS is installed.

I am assuming that you have the 6 pin power connector connected??

---

### Post by awaykent on 2020-02-01
I started out not installing anything and the gpu overheated as the fan never worked UNTIL the overheating crash occurred,  then it ran continously until I rebooted.   As for the 6 wired power,  I believe so,  but I will chgeck when I shut down the system and tear it apart.

---

### Post by QIII on 2020-02-01
That Mobo is new enough that the OS-controlled-GPU issue should not be a problem.

The card's onboard firmware fan control should be able to control the fan on its own without input from the OS or the driver if the BIOS is set to do that.

Have you updated the BIOS to the most recent version?

---

### Post by QIII on 2020-02-01
I just noticed something.  Does this card have an integrated graphics controller as well as your dedicated card?

If so, check your settings in BIOS and make sure that your dedicated graphics are used and "blacklist" the integrated card.

---

### Post by awaykent on 2020-02-01
Will check.  I do not think that I am using the integrated graphics at all...  I think it was shut down.

---

### Post by awaykent on 2020-02-01
I went into the bios and made sure that the IGX was disabled.  Then I reloaded game,  gpu temp went from 57 to 75 in under a minute and was still creeping up,  and the gpu fan was not running at all.  So I stopped the game,    GPU down to 62C

---

### Post by awaykent on 2020-02-01
Again I tried it,  from 58 to 60 while in initial game menu,  the up to 64 the moment I picked the country but before I actually started the game....   The issue I think is the R7-370.  I have read a multitude of posts about fan control issues with this card,  most of them are from people whose fans run full tilt all the time.  Mine is the opposite issue,   I WANT the fan to run and it will not.

---

### Post by QIII on 2020-02-01
Arch wiki to the rescue!

I want to stress that this can cause damage -- bear that caveat in mind.

If you look [here]("https://wiki.archlinux.org/index.php/ATI#Fan_Speed") (last updated March 2019, so beware!), you'll be directed to an article updated in January 2020.

You may find some help there.

Again:  Beware the danger of damaged hardware.

---

### Post by awaykent on 2020-02-01
Will check it out,  Thanks!!

---

### Post by awaykent on 2020-02-01
It looks like it may work.  However I still have no clue about how to implement this.  not sure if I use use nano to edit some file or what.

---

### Post by awaykent on 2020-02-02
From [https://wiki.archlinux.org/index.php/Fan_speed_control#Configuration_of_manual_control](https://wiki.archlinux.org/index.php/Fan_speed_control#Configuration_of_manual_control) page,  I assume this is the link I am supposed to end up at.  From there I ended up with the following text "
Kernel 2.6.35 or newer is required.  The pm code supports three basic methods:
  
[LIST=1]
[*]"dynpm"
[*]"profile"
[*]"dpm"
[/LIST]
  You can select the methods via sysfs.  Echo "dynpm" or "profile" to  /sys/class/drm/card0/device/power_method. "dpm" support, must be  selected at boot (via radeon.dpm=1) and is only supported on R6xx and  newer asics.
  Controlling the fan speed directly is not possible (and would be very  dangerous), but it can be lowered by setting lower power profile.
  The "dynpm" method dynamically changes the clocks based on the number  of pending fences, so performance is ramped up when running GPU  intensive apps, and ramped down when the GPU is idle.  The reclocking is  attemped during vertical blanking periods, but due to the timing of the  reclocking functions, doesn't not always complete in the blanking  period, which can lead to flicker in the display.  Due to this, dynpm  only works when a single head is active.
  The "profile" method exposes five profiles that can be selected from:
  
[LIST=1]
[*]"default"
[*]"auto"
[*]"low"
[*]"mid"
[*]"high"
[/LIST]
  Select the profile by echoing the selected profile to /sys/class/drm/card0/device/power_profile."

That was from [https://www.x.org/wiki/RadeonFeature/#index3h2](https://www.x.org/wiki/RadeonFeature/#index3h2),  but there were other pages that say similar things.   

Here is what I got...
root@ken-GA-78LMT-USB3-6-0:~# echo "1" > /sys/class/drm/card0/device/hwmon/hwmon0/pwm1_enable
-bash: /sys/class/drm/card0/device/hwmon/hwmon0/pwm1_enable: No such file or directory
root@ken-GA-78LMT-USB3-6-0:~#  echo "1" > /sys/class/drm/card0/device/hwmon/hwmon0/pwm1_enable
-bash: /sys/class/drm/card0/device/hwmon/hwmon0/pwm1_enable: No such file or directory
root@ken-GA-78LMT-USB3-6-0:~# radeon.dpm=1
radeon.dpm=1: command not found
root@ken-GA-78LMT-USB3-6-0:~#  echo dynpm > /sys/class/drm/card0/device/power_method
-bash: echo: write error: Invalid argument
root@ken-GA-78LMT-USB3-6-0:~#  echo dynpm > /sys/class/drm/card0/device/power_method
-bash: echo: write error: Invalid argument
root@ken-GA-78LMT-USB3-6-0:~# echo high > /sys/class/drm/card0/device/power_method
-bash: echo: write error: Invalid argument
root@ken-GA-78LMT-USB3-6-0:~# /etc/udev/rules.d/30-radeon-pm.rules
-bash: /etc/udev/rules.d/30-radeon-pm.rules: No such file or directory
root@ken-GA-78LMT-USB3-6-0:~#

---

### Post by awaykent on 2020-02-02
I did try the first method,  same sort of errors...

---

### Post by awaykent on 2020-02-02
What really seems to stink is that unless you want to pay several hundred dollars.  most of the "new" cards sold by the reputable dealers are 5-10 year old technology....

---

