---
title: "Black screen when booting into Ubuntu 10.10"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by yotiao on 2010-11-08
Hello,
I have been trying to install Ubuntu 10.10 64bit on my Windows7 64bit machine. I created the Ubuntu installation on a USB stick and when I run it live from the stick, it works fine. Under Windows7, I created a partition for Ubuntu, and after reboot run the installation off the USB stick. During installation, I pointed the installer to the partition I just created, and told it to use it as "/" (root - this is the part where I think I could have screwed up, but I am not sure). I want to have both Win7 and Ubuntu on that machine. I did not create the SWAP file as I don't think I'd need it (this is a 8Gb RAM 3Ghz i7 machine). The installation goes without any problem, but then I reboot... 

When I restart after installation, and any time after that, I get to the grub screen that allows me to pick the system I want - and when I chose Win7, everything's fine. When I want to pick Ubuntu, or Ubuntu in recovery mode, the screen goes black, and after a short while it seems the monitor itself stops receiving any input from the computer, as it goes into standby. There is no error message, no restart of the computer, no message after I select Ubuntu and click enter. Nothing, just total blackness and despair, and a monitor in standby mode :-(

I've googled a bit, but it always seems that people get some errors, or problems with grub - but this is not the case.

I would be very grateful for some clues as how to fix this.

Thanks a million,
yot

---

### Post by sikander3786 on 2010-11-08
From the Grub menu, highlight the 1st entry. Press 'e' to edit it and using arrow keys, navigate to "quiet & splash". Delete them and type "nomodeset" in their place. Press Ctrl + X to continue booting. Do you get to the desktop now?

If yes, you need to install the drivers from System > Administration > Additional Drivers and the problem should be solve forever. Drivers are available for NVIDIA or ATI only.

If no drivers are available for your card, please list your card so we can find some other workaround.

---

### Post by yotiao on 2010-11-09
Woo-hooo! It worked! So it was just a bad driver after all. Thanks a million! I hope Santa will bring you lots of presents this year.

cheers
yot

---

### Post by Lesaker on 2010-11-09
I just built a new computer with an AMD Radeon HD 6870 card, and am experiencing this problem. On boot, I pass the grub screen, and the ubuntu splash, and then get a black screen. The nomodeset option doesn't fix it.

---

### Post by yotiao on 2010-11-09
Hmm, but this is a bit different than mine. I've never got to the splash screen. It seems - especially that nomodeset option doesn't help - that it is not the graphic card driver issue, but something else. Have you tried booting into recovery mode?

cheers
yot

---

### Post by sikander3786 on 2010-11-10
> **Lesaker said:**
> I just built a new computer with an AMD Radeon HD 6870 card, and am experiencing this problem. On boot, I pass the grub screen, and the ubuntu splash, and then get a black screen. The nomodeset option doesn't fix it.
For ati, you can try with **radeon.modeset=0** or **xforcevesa** instead of nomodeset.

---

### Post by janthonywj on 2010-11-11
I'm trying not to start a new thread...

I'm having the same issue... Although I couldn't get the GUI install to work either. However, I was able to install through the command line option. I know that nomodeset fixes the issue, as I've now figured out how to get the live CD to boot by selecting that option in the initial screen by pressing F6 and selecting "nomodeset". 

NOW... To actually get into my desktop to install the appropriate drivers, I need some way of booting with this option and I can't figure it out. The screen goes into standby before I even get to the grub menu it seems. I've tried pressing 'e' a bunch throughout the whole start up... 'F6' ... and banging my head on the keyboard randomly. I get no Grub menu options. 

If I get into the file system through running the live CD, is there anywhere I can insert this command to get it to give me a screen? Or, is there a way to have the restricted drivers installed with the Ubuntu installation? 

There is an Nvidia Geforce 6150 LE card that is integrated (states PCI though) in a motherboard I haven't looked up yet. I'm setting this up for a family member. 

I will love someone's advice.

---

### Post by janthonywj on 2010-11-12
Well... I took a stab in the dark and when I got the live CD to boot, I did the "get additional drivers" like normal, and then went on to re-install Ubuntu, and I guess the programming is smart enough to include those drivers because it worked. 

All I have to do now is tweak the xorg.conf file and such and I'll be set.

---

### Post by sikander3786 on 2010-11-12
> I've tried pressing 'e' a bunch throughout the whole start up... 'F6' ... and banging my head on the keyboard randomly. I get no Grub menu options.


For future references, you'll neeed to press down and hold the Shift key at your Bios screen until you see the Grub menu ;-) It is not the 'e' or F6 key, it's Shift.

Yes, the software you install on a Live CD, is included in the original install unless you don't restart your sessions.

Cheers.

---

### Post by pixelnate on 2010-11-12
I am having the same black screen after grub scenario with an hd6870 and it appears as if this card is too new for Ubuntu.

When I run 'sudo aticonfig --initial' the response is 'No supported adapters detected'.

And according to the AMD forums it looks like they are only drivers for windows:
[http://forums.amd.com/game/messageview.cfm?catid=260&threadid=141868](http://forums.amd.com/game/messageview.cfm?catid=260&threadid=141868)

and

[http://forums.amd.com/devforum/messageview.cfm?catid=390&threadid=141934](http://forums.amd.com/devforum/messageview.cfm?catid=390&threadid=141934)

This really pisses me off. I just dropped $250 for a card that I cannot even use in linux yet. ](*,)

---

### Post by cesar.ramsan on 2010-11-12
I have the same problem, install drivers then ubuntu wont start.
Then using recovery option will restore previous configurtion.
Then try to run the aticonfig but it wont find any supported adapter.
:S

---

### Post by pixelnate on 2010-11-12
You are not getting any video because the fglrx driver doesn't yet include support for the 6xxx series. ATI/AMD's monthly update will surely fix the issue, but until then you/we are out of luck.

I am tired of the ATI/AMD issues with linux and I've already RMA'd the card and will go back to nVidia, permanently. :mad:

---

### Post by Karjix on 2010-11-24
ATI/AMD's monthly update will surely fix the issue, but until then you/we are out of luck.


Hey there i am a "Proud" more like sad owner of a 6870 who would love to use ubuntu since i lack interest in windows and probebly will leave it behind when i get the hang of Ubuntu. Would like to know when the update is released and where i can read more about the other implements the patch will give.

Cheers

---

### Post by mahmoodkamal on 2010-11-24
> **sikander3786 said:**
> From the Grub menu, highlight the 1st entry. Press 'e' to edit it and using arrow keys, navigate to "quiet & splash". Delete them and type "nomodeset" in their place. Press Ctrl + X to continue booting. Do you get to the desktop now?

If yes, you need to install the drivers from System > Administration > Additional Drivers and the problem should be solve forever. Drivers are available for NVIDIA or ATI only.

If no drivers are available for your card, please list your card so we can find some other workaround.

Heard that profiling can improve booting time. Have you tried adding the profile option in Grub?

---

### Post by sikander3786 on 2010-11-24
> **mahmoodkamal said:**
> Heard that profiling can improve booting time. Have you tried adding the profile option in Grub?
I have not heard of profile option in Grub nor tried it ever.

As long as my boot time is < 40 sec, I am ok with that. Don't want a super fast boot as I only have to boot it once a day and all the other time, it is running ;-)

Did you try that?

---

### Post by mahmoodkamal on 2010-11-27
> **sikander3786 said:**
> I have not heard of profile option in Grub nor tried it ever.

As long as my boot time is < 40 sec, I am ok with that. Don't want a super fast boot as I only have to boot it once a day and all the other time, it is running ;-)

Did you try that?

Good point :)

---

### Post by Spyderkid on 2010-11-27
What you might want to do if your screen has an extension cable for the power make sure its pushed together tightly it can come undone quite easily, it happened to me till i heard a fizzing sound and saw that the connectors wetre only just joined together

---

### Post by PhoenixGI on 2010-11-27
I installed to USB and am having the same issue.  I tried editing the GRUB entry removing "quiet splash" and replacing it with "nomodeset".  And am still getting the black screen.  It's something in particular with this PC as the same type of install works fine on my laptop.  Any suggestions as to what I need to do next? Besides just use the laptop :D ;)

---

### Post by Kir_B on 2010-11-28
> **PhoenixGI said:**
> I installed to USB and am having the same issue.  I tried editing the GRUB entry removing "quiet splash" and replacing it with "nomodeset".  And am still getting the black screen.  It's something in particular with this PC as the same type of install works fine on my laptop.  Any suggestions as to what I need to do next? Besides just use the laptop :D ;)

Is this happening regularly, or is this an intermittent issue?

My main hard drive has my original Ubuntu install on it, but it is having the same issue, full time... That is, it won't boot, period!!! Kernels appear, but when selected, never reach the log in screen. 

For the past three months, I've been using a backup of my original install(250GB): This was a backup I performed, about two months after the upgrade to Lucid. I used Clonezilla to clone the system to my Verbatim 500GB usb hard drive. I've taken the Verbatim case a part, removed the hard drive, and installed it directly into my PC's case, replacing the original 250GB HDD (Which contains my original Ubuntu install). The backup of the original has been running flawlessly for three months, so I don't think it's a hardware issue, but instead, something not configured, or something else stupid, that's only mission, is to make us feel intelligently challenged. 

I would very much like to get that original install working again, but the hill is a lot steeper than I've been prepared for and help was very hard to obtain when it originally took place.

One day soon, I'll get back to it... I hope.

Peace and best of luck. Kirby

---

### Post by PhoenixGI on 2010-11-28
> **Kir_B said:**
> Is this happening regularly, or is this an intermittent issue?

My main hard drive has my original Ubuntu install on it, but it is having the same issue, full time... That is, it won't boot, period!!! Kernels appear, but when selected, never reach the log in screen. 

For the past three months, I've been using a backup of my original install(250GB): This was a backup I performed, about two months after the upgrade to Lucid. I used Clonezilla to clone the system to my Verbatim 500GB usb hard drive. I've taken the Verbatim case a part, removed the hard drive, and installed it directly into my PC's case, replacing the original 250GB HDD (Which contains my original Ubuntu install). The backup of the original has been running flawlessly for three months, so I don't think it's a hardware issue, but instead, something not configured, or something else stupid, that's only mission, is to make us feel intelligently challenged. 

I would very much like to get that original install working again, but the hill is a lot steeper than I've been prepared for and help was very hard to obtain when it originally took place.

One day soon, I'll get back to it... I hope.

Peace and best of luck. Kirby

For me this is happening regularly, I haven't actually loaded into a desktop yet for the first time (not counting the live CD). I've tried booting to recovery also.  No luck there.  Is there some log file that I could look at (using the live CD to boot into then looking at the file system on the Thumb drive) to see where it's hanging up?

---

### Post by Kir_B on 2010-11-30
> **PhoenixGI said:**
> For me this is happening regularly, I haven't actually loaded into a desktop yet for the first time

Same thing here!

> I've tried booting to recovery also.Sorry, I meant to mention that the recovery options, when selected, result in a black screen and nothing else for me also.

[QUOTE]Is there some log file that I could look at (using the live CD to boot into then looking at the file system on the Thumb drive) to see where it's hanging up?Well judging by the silence, I'm guessing not, but that is a fantastic question. Unfortunately, I don't have the for sure answer either way. If someone knows of a way, I'd think they would have posted by now, but then again, everyone may have bigger fish to fry right now, as there's a lot of bug hunting going on right now.

Best of luck. Kirby

---

### Post by sikander3786 on 2010-11-30
> **PhoenixGI said:**
> I installed to USB and am having the same issue.  I tried editing the GRUB entry removing "quiet splash" and replacing it with "nomodeset".  And am still getting the black screen.  It's something in particular with this PC as the same type of install works fine on my laptop.  Any suggestions as to what I need to do next? Besides just use the laptop :D ;)


It might not be the same issue for you.

How did you load the USB? Which software used?

Did you check the MD5SUM of the downloaded image?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

For burning to USB,

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

What happens exactly when you boot? Black screen, any errors or what?

---

### Post by PhoenixGI on 2010-12-01
I actually started another Post regarding my issue at [http://ubuntuforums.org/showthread.php?t=1634032](http://ubuntuforums.org/showthread.php?t=1634032) but to answer your questions

> **sikander3786 said:**
> It might not be the same issue for you.

How did you load the USB? Which software used?

I used a liveCD to install Ubuntu to a thumbdrive

> **sikander3786 said:**
> 
Did you check the MD5SUM of the downloaded image?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Yep it's good

> **sikander3786 said:**
> 
For burning to USB,

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

What happens exactly when you boot? Black screen, any errors or what?

I'm not making a live(Thumb)Disk, I'm doing an actual install per [http://ubuntuforums.org/showpost.php?p=10117203&postcount=14](http://ubuntuforums.org/showpost.php?p=10117203&postcount=14) Now though the trouble shooting of a few other folks, yes, I maybe in a whole new realm of hurt... err problem. It appears that the install isn't going past GRUB.  Don't know, still looking into it, just had the similar symptom of the black screen at boot.

---

### Post by sikander3786 on 2010-12-01
> **PhoenixGI said:**
> I actually started another Post regarding my issue at [http://ubuntuforums.org/showthread.php?t=1634032](http://ubuntuforums.org/showthread.php?t=1634032) but to answer your questions


I used a liveCD to install Ubuntu to a thumbdrive


Yep it's good



I'm not making a live(Thumb)Disk, I'm doing an actual install per [http://ubuntuforums.org/showpost.php?p=10117203&postcount=14](http://ubuntuforums.org/showpost.php?p=10117203&postcount=14) Now though the trouble shooting of a few other folks, yes, I maybe in a whole new realm of hurt... err problem. It appears that the install isn't going past GRUB.  Don't know, still looking into it, just had the similar symptom of the black screen at boot.
Hmmm. I see **oldfred** and **C.S.Cameron** are helping you in the other thread so you are in safe hands :P

Good Luck!

---

### Post by PhoenixGI on 2010-12-01
> **sikander3786 said:**
> Hmmm. I see **oldfred** and **C.S.Cameron** are helping you in the other thread so you are in safe hands :P

Good Luck!

Thanks, I think I'm going to need it.  They're giving me great information, but my PC don't seem to be cooperating.  :)

---

### Post by hencha on 2010-12-10
Hi and thanks.  This appears to have worked for me on a HP Pavilion laptop. - gabriel

---

### Post by Kir_B on 2010-12-14
> **hencha said:**
> Hi and thanks.  This appears to have worked for me on a HP Pavilion laptop. - gabriel

Hey Gabriel

Glad to hear that something worked for you. Could you elaborate for me please. What worked?

Thanks. Kirby

---

### Post by WillisIVXX on 2011-04-18
> **sikander3786 said:**
> From the Grub menu, highlight the 1st entry. Press 'e' to edit it and using arrow keys, navigate to "quiet & splash". Delete them and type "nomodeset" in their place. Press Ctrl + X to continue booting. Do you get to the desktop now?
 
If yes, you need to install the drivers from System > Administration > Additional Drivers and the problem should be solve forever. Drivers are available for NVIDIA or ATI only.
 
If no drivers are available for your card, please list your card so we can find some other workaround.
 
i have a mobile intel hd graphics and have the same black screen, tried the nomodeset and didn't work, any ideas on how to fix?

---

### Post by sikander3786 on 2011-04-18
> **WillisIVXX said:**
> i have a mobile intel hd graphics and have the same black screen, tried the nomodeset and didn't work, any ideas on how to fix?
This page might help you.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

You may try some other boot parameters like i915.modeset=1 or i915.modeset=0 or xforcevesa instead of nomodeset. Instructions are there on the page linked above.

---

