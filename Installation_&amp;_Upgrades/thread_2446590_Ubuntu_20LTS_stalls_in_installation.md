---
title: "Ubuntu 20LTS stalls in installation"
date: 2020-07-03
forum: Installation &amp; Upgrades
---

### Post by Richard_York on 2020-07-03
I am trying to install Ubuntu 20LTS to a new Asus VivoBookX    (Spec below)  and the installation process keeps failing at different points.

 I first intended to dual-boot with Windows, (thread here: [https://ubuntuforums.org/showthread.php?t=2445714](https://ubuntuforums.org/showthread.php?t=2445714))  but eventually decided to go for a clean install,  partly because the partitioning was getting too far beyond my technical understanding level.

 
 I used the Windows process to set the Boot order the first time.  
Regrettably I’d wrongly identified the French-Canadian keyboard this thing came with [ATTACH=CONFIG]286385[/ATTACH]so although Ubuntu appeared to install smoothly and cleanly, and downloaded updates, some keys didn’t do what I expected.

 I don’t know if you can reassign a keyboard once it’s installed, but since installation had been so easy I decided simply to re-run it and start again.

 I used the bootable USB which had worked earlier, but it now stalled. 

I wiped and re-loaded the USB, after the initial scan announced there was now an error. No error found on the re-load, but it stalled again, either after the original appearance of the Ubuntu logo, or at points between identifying the keyboard, and once even getting as far as trying to connect to our Wifi.

I tried allowing it open with the Ubuntu installation which had worked, but this now resulted in a black screen after the initial Ubuntu logo.

 I tried it with 18LTS bootable USB, from a download I know works – it’s driving our PC and another laptop at present: it got as far as asking for the code for the WiFi but again stalled. The other laptop, next to it on the table, was receiving signal well, so I doubt it’s a signal issue.

 I experimented with the “Try Ubuntu” option when it did get that far, but this resulted in the screen scrolling through lines too fast to read, until it came to rest at
  
[  323.846114 ]  pcireport 0000:001c – 5: AER: pc1e Bus Error : severity=Corrected  type=Physical Layer. (Receiver ID) device [8086:9d15] error status/mask=00000001/ 00002000 [ 0] RxErr

 I think I copied this accurately, apologies if not, and  include it in the hope it makes more sense to those with more understanding than I have.

 I have disabled “Fastboot” in the Asus setup menu.
 
I’m sure there’s a way out of this impasse, and will be grateful for patient pointers at how to get there.


 Asus has: Intel Core i3 6th Gen. ;  8 GbB RAM; 1TB  HDD, was running Windows 10. Manufacturer re-furbished, new.

---

### Post by Richard_York on 2020-07-06
For lack of advice, I'm still stuck, other than keeping on trying in case it works next time. So far, it doesn't.

I found discussions of Asus computers freezing, but none of them fits what I'm doing, solutions vary, and they assume a knowledge of terminology beyond my level.

I found this recent thread here  [https://ubuntuforums.org/showthread.php?t=2446589](https://ubuntuforums.org/showthread.php?t=2446589)with "The USB was listed twice. Selecting the non-UEFI option results in the installer working normally "

Boot option in my case offers both "Kingston USB" and "Kingston USB Partition 1" options. Option 1 once got as far as connecting WiFi, but then spent around 45 minutes stuck on the revolving wheel icon, and lost the Wifi connection, before I yet again switched off.
 Option 2, for "partition 1"  sticks at the initial Ubuntu logo, no sign of any other movement. 
 Trying to open with the Ubuntu 20 which I originally installed, but with the wrong keyboard ID, still gets the screen full of lines, as quoted in my original post here, and sticks there.

So I would be truly grateful for pointers to a way out of this to get Ubuntu up & running, or even options open to me to try, other than asking my local repair shop to re-install Windows, which I hate using, apart from the extra expense involved.

Thank you.

---

### Post by GhX6GZMB on 2020-07-06
It's not clear how far you get in the install.
1: do you get to the DOS-like F2/F3 select language/keyboard screen?
2: do you get to the "Start/Try Ubuntu screen?
3: do you get to the Ubuntu desktop?

---

### Post by Richard_York on 2020-07-07
Sorry for my lack of clarity. Regrettably it's not consistent.

Until yesterday I'd have replied:
1:  select language / keyboard - usually, though sometimes it stalls here.
2: Try  / Install Ubuntu screen - usually, sometimes has stalled at this point too.  
3: Ubuntu Desktop - no.
and would have added: Recent attempts usually fail somewhere round the "connect Wifi" stage.

But today it sticks much earlier in the process.

Power on & Esc key leads to 
> Please select boot device
Ubuntu (PO: ST000LMO35 -1RK172)
UEFI: USB DISK 2.00 PMAP
UEFI: USB DISK 2.00 PMAP, Partition 1
Enter Setup

... As my post #2 says, up until yesterday it identified the USB as "Kingston" and I don't believe it mentioned UEFI, though can't swear to that. 
I used Setup  last week to disable Quickstart, and that has stayed disabled. I used it to re-order the Boot order, and that's reverted to the order shown.

Today, choosing USB, or USB Partition 1, both lead to Grub 2.04 screen, offering Ubuntu as first option, with others below, but this moves on too soon to properly read them all. 
OEM for manufacturers, and Firmware are among the offers.
 This screen appeared less pixellated when  I chose the "Partition 1" option of UEFI USB.

Today. either USB option gets the disk check - no errors - then both the Asus logo and Ubuntu Logo, and then no more.

If screen photos would help I can take these, though it's such a reflective screen this is not easy. No access to "Print Screen" at present.

---

### Post by ActionParsnip on 2020-07-07
Make sure you have the latest BIOS too. This can help

---

### Post by Richard_York on 2020-07-07
So far the only "How to"  pages I'm spotting to do this assume I can use Windows. Sadly, I can't, since it was wiped with my first installation of Ubuntu (see #1).
 Is there another route, please? I can access the Setup pages using Power on/ Esc,

---

### Post by Richard_York on 2020-07-07
My apologies - I finally thought of actually looking in Setup! It's BIOS version 311, vendor American Megatrends. I don't know how I'd update that if needed, hopefully it's up to date enough.

---

### Post by GhX6GZMB on 2020-07-07
To me, there are so many problems here that I'd suggest a more radical approach.

1: The i3 CPU is a bit lightweight for a Ubuntu install, I'd go for one of the lighter distros. Personally I'm running Lubuntu 20.04 LTS and extremely happy with it.
2: It seems to me me that the instability factor is the WLAN connectivity (could be driver problems in the live boot .iso). You don't really need WLAN for the live boot. _Don't turn it on during live boot._ Hopefully this will bring you to the (K/L/X)Ubuntu desktop.
3: Perhaps switch to an external USB-DVD drive for the live boot. This brings the advantage that you can actually see/hear if the installation is proceeding. Maybe borrow one from a friend?

This is very basic I know, but perhaps it'll bring you forward, right now you're at zero.

---

### Post by Richard_York on 2020-07-08
Thanks for these replies so far.

I'm reluctant to abandon Ubuntu 20LTS, since the reason for buying this Asus was to allow us to do things the current Acer laptop, c.2011, is too small to  handle. GNU (GIMP) works perfectly well on the Acer, but Shotcut seems to fall over, and I was advised the answer is more RAM and more disk space, which the Asus machine has. 
I understand Lubuntu doesn't handle these apps, but please correct me if I'm wrong.

I begin to wonder if I've made an expensive mistake in buying the Asus - although if its i3 processor is a problem for Ubuntu, the Acer is working 18.04LTS perfectly well with an older generation of i3.

I'll need to find how to not turn on WLAN when live booting. Would simply taking the Asus out of Wifi range (other end of garden) suffice?

I'm still puzzled that it initially installed Ubuntu 20 perfectly well, and other than my mistake over the keyboard ID meaning that some keys didn't do what they said, all appeared to work very happily. If it can do it once, I'm clinging to hope that it can do it again, but with the right keyboard ID this time! The only condition which has changed, as far as I can see,  is that I was going from Windows, and now that's not there. 

Is there something I can adjust in Setup mode which would replicate the conditions which allowed it to work so easily before?

---

### Post by GhX6GZMB on 2020-07-08
> **Richard_York said:**
> Thanks for these replies so far.
I'll need to find how to not turn on WLAN when live booting. Would simply taking the Asus out of Wifi range (other end of garden) suffice?


Probably not, as the WLAN circuit will still be active and demand a driver. If you have the option, turn it off in the BIOS. You can always turn it back on later.

---

### Post by Richard_York on 2020-07-09
I cannot yet see a way of switching WLAN through the BIOS setup. Other than options I can see are obviously irrelevant, the ones on offer are:

Intel AES-NI
VT-d
Asus EZ Flash 3 Utility
SMART settings
Network Stack Configuration
USB Configuration
Graphics Config
SATA Config

None of these appears to relate to WLAN, but I'm willing to be guided!

The one consistent thing at present is the message line I copied in my OP, when I tried allowing the Ubuntu I'd installed before messing things up to try opening.
The USB just now allowed me as far as the "Try Ubuntu" / "Install Ubuntu" stage. I pressed "Try" and got the same screen full of scrolling lines, ending in
> AER : PC1e Bus Error : Severity=Corrected, type=Physical layer, (Receiver ID) device [8086:9d15] error status/mask=00000001/00002000 [ 0] RxErr

Does this mean anything to anyone here?

---

### Post by GhX6GZMB on 2020-07-09
AER is "advanced error reporting" which fits with the gazillion messages you get.

Perhaps this can help?
[https://itsfoss.com/pcie-bus-error-severity-corrected/](https://itsfoss.com/pcie-bus-error-severity-corrected/)

Otherwise I suspect WLAN is under "Network Stack Configuration".

---

### Post by Richard_York on 2020-07-09
Thank you, that's interesting.

 I wish I could understand more of the linked article, but it does seem to describe what I'm getting.  It also assumes the reader can open a terminal, and at present I can't, as far as I can tell.

...Though I got quite excited just now when, on again experimenting with opening the Ubuntu I first installed, no USB inserted, it got as far as allowing me to sign in with my password,  The icon top right of screen while I signed in indicated that WiFi was successfully connected.
Now it's frozen on the purple screen, so I got no further.

Meanwhile, "Network Stack Configuration" in Setup leads me only to an option of Enabling or Disabling this. Its default setting appears to be Disabled.

Am I yet in danger of needing, reluctantly,  to head to my local computer guy for him to reload Windows?

---

### Post by GhX6GZMB on 2020-07-09
If you have a partial boot without the USB-stick, try again.
From my link:
"If your system doesn&#8217;t show the grub screen, press and hold shift key at boot. In some systems, pressing the Esc key brings the grub screen."

Then go into recovery mode from there and follow the other instructions. I'm quite certain that your log files are immense from the error messages.

GRUB stands for "Grand Unified Boot Loader" and will load both Linux/Ubuntu and Windows for dual boot.

---

### Post by Richard_York on 2020-07-12
Thanks.
 Unfortunately it won't let me in even that far now. Repeated attempts with no USB in place stall at the Ubuntu Logo, sometimes brief appearance of progress wheel, then nothing. Holding the power key to force switching off fills the screen with the now familiar error messages until it goes off.
I tried with the USB again, and at the GRUB screen thought to experiment with "Install Ubuntu for Manufacturers" but when it got to entering a batch password, or something of the sort, for this installation, to refer to error logs,  I chickened out, as I feared getting further out of my depth with what followed .
I am almost resigning myself to paying the local repair shop to re-install Windows and being stuck with that, which really wasn't the plan.

---

