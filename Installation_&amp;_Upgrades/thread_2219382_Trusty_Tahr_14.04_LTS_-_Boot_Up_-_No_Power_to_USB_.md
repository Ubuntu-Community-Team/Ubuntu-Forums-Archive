---
title: "Trusty Tahr 14.04 LTS - Boot Up - No Power to USB Devices (Mouse, Keyboard, etc)"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by lordbalmung on 2014-04-23
Hi,

I updated Ubuntu Saucy 13.10 to Trusty Tahr 14.04 LTS. Everything worked fine till I turned off my desktop and turned it on again. I wasn't able to log into my account. Keyboard and mouse did not receive any power. It works after I force shutdown (hold the power button for 10 seconds) and reboot once again.

**Problem Type:** Bug (Potential)
**Frequency:** Often - (Observed 2/5)
**Brief Description:** USB Devices do not receive power.
**Description:** I am stranded on the "log in" screen till I force shutdown and start again due to the lack of power to my keyboard and mouse.

**Solution:**
Upgrade kernel - Thanks to @tokyobadger
refer: [http://ubuntuforums.org/showthread.php?t=2219382&p=13226148#post13226148](http://ubuntuforums.org/showthread.php?t=2219382&p=13226148#post13226148)

---

### Post by lordbalmung on 2014-05-08
I'm very disappointed having no response, I patiently waited and the bug is getting on my nerves. I'm bumping this post, I seek some help.. Any help!

---

### Post by jdeca57 on 2014-05-08
Intermittent failures - 2/5 - are often the most difficult to answer. There is no software problem, since it works -3/5- and software, well, should be more consistent. So this points to a hardware problem, ranging from a contact somewhere (for instance, do you use a usb hub) to a motherboard failure. Of course, it worked with 13.10 but perhaps it's a coincidence the failure occurred after the upgrade. Were there any other changes like new hardware?

---

### Post by lordbalmung on 2014-05-08
@jdeca57,

First of all, I thank you for your swift reply.

Regarding hardware changes, I do not even use a USB key. I keep my data transfer mostly through the LAN and no other peripherals were newly added since 2 months before Installing Trusty Tahr. This is the worst of the two bugs I face, the other one I've mentioned in a different thread (with no responses yet) is a complete system freeze/paralyze. Ofcourse, I am just pointing it out in case it helps.

---

### Post by buggy2 on 2014-06-28
Hello,

I have exactly the same problem over here - no, and it is not the hardware. My PC is dual-boot and the USB ports never loose power in (or before) the grub screen or in win 7. When booting in Ubuntu, all power get's turned off to the USB ports and only sometimes the power is turned back on in the boot process. It nearly always fails on first booting and it nearly always works on second try (after doing a forced shutdown with the power switch on the PC).

Any ideas where to look? Is this power-save going wrong?

Thanks.

---

### Post by static0verdrive on 2014-09-18
I have this same problem. I had installed a 3.15 kernel at one point a few months back and everything was fine (I'd rebooted a few times with no problems) but ever since about 3 weeks ago after some automated updated installed and I saw the message that a reboot was required, I no longer have power to my keyboard. I only clued in because the backlighting wasn't working. It freezes at the Grub screen. The keyboard works fine in another PC. What scares me is I can't even get into the BIOS, which is weird because the whole PC is only 4 months old and it was working fine until I issued the reboot command. Any assistance would be GREATLY appreciated seeing as I have about 6 TB of data that worst-case I'd like to start pulling off in case I'll need to format.

---

### Post by lordbalmung on 2015-01-17
Booooooooooooooooooooooooooossssssssssssssssssstttttttttttttttttttttttt!!!!

Why doesnt anyone address this?

---

### Post by QIII on 2015-01-17
Perhaps because there is little information to go on.

Could you please give us the hardware specs of your machine, including the motherboard OEM and model?  Despite the mention above that another's problem is not a hardware problem, it may very well be.  There are some motherboards from certain OEMs that can have similar issue when running Linux that do not appear when running Windows.

And are your devices plugged in to USB3 or USB2 ports?

---

### Post by tokyobadger on 2015-01-17
> **lordbalmung said:**
> Hi,

I updated Ubuntu Saucy 13.10 to Trusty Tahr 14.04 LTS. Everything worked fine till I turned off my desktop and turned it on again. I wasn't able to log into my account. Keyboard and mouse did not receive any power. It works after I force shutdown (hold the power button for 10 seconds) and reboot once again.

**Problem Type:** Bug (Potential)
**Frequency:** Often - (Observed 2/5)
**Brief Description:** USB Devices do not receive power.
**Description:** I am stranded on the "log in" screen till I force shutdown and start again due to the lack of power to my keyboard and mouse.
I second QIII's request for more info - I note earlier that you say you do not have even a USB key, but especially with a laptop it could be an internal USB device.

Having said that, I've encountered something similar before both in Ubuntu and other distros. If you're issue is similar to what I have encountered, then I think it is not an issue of USB devices losing power, but an issue of how the current kernel is handling the various USB devices at boot.

In my experience, I found that after arriving at the login greeter screen my keyboard and/or mouse would be unresponsive - my own process of elimination went something like this

1) check keyboard and mouse have fresh batteries (if cordless)
2) check connections
3) wait (sometimes up to 10 minutes) at the login screen for USB keyboard and/or mouse to respond  <-- this was key to identifying the problem
4) try booting previously working kernels <-- results varied, some kernels never had the issue, some had the issue after booting from the current problematic kernel
5) redo step #3 and look at dmesg (dmesg | grep USB) - if you see error messages such as "unable to enumerate USB device..." then it's the same problem I had
6) took stock of all USB devices connected, unplugged all except KB and mouse and started process of elimination by adding one-by-one and then USB port rotation
7) culprit for me was a cheap USB webcam bought a long time ago
8) since ditching it, no issues - this was maybe 3 years ago

If it is a device you need, then there is a workaround [at this launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354832") <-- again you'll see it's not a new topic

[Here is an alternate and more recent suggestion from launchpad](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1238194)

---

### Post by lordbalmung on 2015-01-17
**@QIII, **Thank you for your response, I appreciate it. These are the specs (I am not sure about the motherboard, I will update that information soon)

**Processor:** i7-4770
**RAM:** 16GB
**Graphic Card:** NVidia GTX 645 OEM
**USB Ports**: I Tried both USB2 and USB3

Also, note that I've been using Linux mint as the loss of power to the peripheral devices was increasing in frequency of occurrence, though linuxmint did not exhibit that particular behavior, it used to crash on Firefox, Flash Rendering and VLC when hardware acceleration is activated (issues I also faced with Ubuntu). I later realized that the x64 versions of these two operating systems failed for more users. Hope this information is of any use :)

---

### Post by tokyobadger on 2015-01-17
Thanks for the info - home-build or pre-build? Also, which version of Mint?

---

### Post by lordbalmung on 2015-01-17
Hii @tokyobadger,

I am so thrilled with all the responses, my joy aside, let me answer you to the best of my knowledge.

1. I hate cordless keyboard and mouse, the lag they produce in periods of low battery annoys me a lot.
2. Connections are good :)
3. I left the system idle an entire night yet, won't budge
4. Haven't tried changing to previous kernels though I read (after shifting to another OS) that it helped some
5. I will try out dmesg
6. I only have my Keyboard and mouse connected at all times, don't even use USB keys (except for installing OSes <- I don't know if that is an actual word :P)
7. Nope, no webcams here (or any other USB devices)
8. Same as above.

Also, it might help to know that I did not have this issue with Ubuntu 13 and Linuxmint 16

---

### Post by lordbalmung on 2015-01-17
@tokyobadger

**Pre-Built** Linuxmint 15 and 16

(But now I want to try the home built one :P)

---

### Post by tokyobadger on 2015-01-17
Thanks for the replies.
[QUOTE=lordbalmung]Also, it might help to know that I did not have this issue with Ubuntu 13 and Linuxmint 16[/QUOTE]
Given that then the 2nd link I posted should be of particular interest as LM 15 & 16 are based on the two 13.xx releases of Ubuntu and the thread is directly related to fixes required for USB "recognition" during the boot process - suggested fix included

---

### Post by lordbalmung on 2015-01-17
> **tokyobadger said:**
> Thanks for the replies.

Given that then the 2nd link I posted should be of particular interest as LM 15 & 16 are based on the two 13.xx releases of Ubuntu and the thread is directly related to fixes required for USB "recognition" during the boot process - suggested fix included

Interesting, I checked it out and sounds very similar to the issue we were facing however,

1. The error is not with a pre-boot stage but actually after the system is fully functional and ready to log in.
2. The post in launchpad doesn't hint anything about occasional dysfunction but a steady dysfunction for some users.

---

### Post by tokyobadger on 2015-01-18
[QUOTE=lordbalmung]1. The error is not with a pre-boot stage but actually after the system is fully functional and ready to log in.
2. The post in launchpad doesn't hint anything about occasional dysfunction but a steady dysfunction for some users.[/QUOTE]
Time to boot in text mode so you can see what's going on and then also run dmesg from the console

- When grub comes up hit shift, then select the kernel you are having problems with and hit e
- In the line "linux /boot ... quiet splash", replace "quiet splash" with "nosplash --verbose text"
- hit ctrl-x to boot

If it boots successfully to the console see if the keyboard is responsive and login; if not did you see any error messages that might hint at the cause

If you can get in, try dmesg | grep USB as a first step

---

### Post by lordbalmung on 2015-01-18
-- Read the next post please

---

### Post by lordbalmung on 2015-01-18
I wasn't able to test it on Ubuntu 14.04 itself however you are a genius! your method to debug atleast helped me find the error (Using Linuxmint 17.1). This is the error message

"usb 3-13: device not accepting address 6, error -71"

Edit: I am currently trying this solution [http://askubuntu.com/questions/117524/usb-device-not-accepting-address](http://askubuntu.com/questions/117524/usb-device-not-accepting-address) which is to use the old boot scheme.

---

### Post by tokyobadger on 2015-01-19
Try this
```
echo Y | **sudo tee** /sys/module/usbcore/parameters/old_scheme_first
```
If it doesn't work you can undo by running the same command replacing "Y" with "N"

---

### Post by lordbalmung on 2015-01-20
> **tokyobadger said:**
> Try this
```
echo Y | **sudo tee** /sys/module/usbcore/parameters/old_scheme_first
```
If it doesn't work you can undo by running the same command replacing "Y" with "N"

Hehe, Thank you, you know my computer better than I (because the other solution failed after 2 days). I am trying your solution now.

---

### Post by lordbalmung on 2015-01-27
> **tokyobadger said:**
> Try this
```
echo Y | **sudo tee** /sys/module/usbcore/parameters/old_scheme_first
```
If it doesn't work you can undo by running the same command replacing "Y" with "N"

Hi again, yet another brilliant idea foiled by my computer :(, any other suggestions?

---

### Post by tokyobadger on 2015-02-01
Influenza + annual work peak + a few random items kept me away.

Recap: what kernel are you running?

---

### Post by lordbalmung on 2015-02-02
> **tokyobadger said:**
> Influenza + annual work peak + a few random items kept me away.

Recap: what kernel are you running?

Haha, you seem to be living my life :D, but I really appreciate your help. Thank you.

The **Kernel** is **3.13.0-37**

"3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux"

---

### Post by tokyobadger on 2015-02-03
re hardware again - can you give more info on mobo, keyboard and mouse please?

---

### Post by lordbalmung on 2015-02-03
Keyboard and Mouse are both DELL, I could not find any other information except that they are made in China :(. They were supplied with the Computer and I first doubted those but then again they worked fine with the previous versions of Ubuntu. The processor is i7-4770 and I am not sure about the mother board. I can provide more information on the mother board within a week, I will have open the CPU.

---

### Post by tokyobadger on 2015-02-04
[going back to the old_scheme topic](http://askubuntu.com/questions/117524/usb-device-not-accepting-address/118538#118538) take a look at the 2nd post in the link - grub modification

---

### Post by lordbalmung on 2015-02-04
> **tokyobadger said:**
> [going back to the old_scheme topic](http://askubuntu.com/questions/117524/usb-device-not-accepting-address/118538#118538) take a look at the 2nd post in the link - grub modification

Already tried that last week, I mentioned that in Post #18 ([http://ubuntuforums.org/showthread.php?t=2219382&page=2&p=13210613#post13210613](http://ubuntuforums.org/showthread.php?t=2219382&page=2&p=13210613#post13210613)), but I edited it hence you might not have noticed it. And that doesn't work either. However, I do not know if this would help but I notice the NVidia logo appear before my keyboard and mouse stop working (I've not tested it enough times to be sure of the co-relation. My graphic card is GTX 645 NVIDIA)

---

### Post by lordbalmung on 2015-02-07
> **lordbalmung said:**
> Already tried that last week, I mentioned that in Post #18 ([http://ubuntuforums.org/showthread.php?t=2219382&page=2&p=13210613#post13210613](http://ubuntuforums.org/showthread.php?t=2219382&page=2&p=13210613#post13210613)), but I edited it hence you might not have noticed it. And that doesn't work either. However, I do not know if this would help but I notice the NVidia logo appear before my keyboard and mouse stop working (I've not tested it enough times to be sure of the co-relation. My graphic card is GTX 645 NVIDIA)

I hope this helps,

Motherboard Information: [http://www.findlaptopdriver.com/dell-0kwvt8-mainboard-specifications/](http://www.findlaptopdriver.com/dell-0kwvt8-mainboard-specifications/)

Also, After I noticed the NVIDIA logo flashing just before the keyboard and mouse die out, I removed the proprietary (recommended) drivers of NVIDIA and Installed the Nouveau drivers, I've not faced the issue after that which is surprising, as the NVIDIA Drivers were the ones recommended by the OS.

---

### Post by NunoLava1998 on 2015-02-08
Does Restart fix the problem temporarily? Try typing Alt+SysRq(PrtSc)+B, if it doesn't work, try Ctrl+Alt+T or Ctrl+Alt+C and C will be replaced by a number from 1-6, 7 is X. If that doesn't work, then your computer is REALLY hanging.

---

### Post by lordbalmung on 2015-02-08
> **NunoLava1998 said:**
> Does Restart fix the problem temporarily? Try typing Alt+SysRq(PrtSc)+B, if it doesn't work, try Ctrl+Alt+T or Ctrl+Alt+C and C will be replaced by a number from 1-6, 7 is X. If that doesn't work, then your computer is REALLY hanging.

Restart some times fixes it but I cannot type anything because my keyboard and mouse do not receive any power. Hence I cannot confirm if it is hanging or not but I don't think it does.

---

### Post by tokyobadger on 2015-02-10
It appears some people are having problems with USB devices and the 3.13.0-xx kernels with 3.13.0-37 coming up frequently.

You could try either the rescue mode (select advanced options under one of the kernels at grub screen) or chroot from a livecd/dvd environment.

From there you could try 
1. fixing 3.13.0-37 [as this user did](http://ubuntuforums.org/showthread.php?t=2248510)

2. upgrading to a 3.16.xx kernel [as this user did](http://ubuntuforums.org/showthread.php?t=2231553) or[as this mint user did](http://forums.linuxmint.com/viewtopic.php?t=185269&p=961782)

3. reinstall ubuntu 14.04 from scratch opting for updates during install (which you would also do from the livecd/dvd but no chroot)

Personally I'd go for reinstall as last option and try the options in numerical order

---

### Post by lordbalmung on 2015-02-11
> **tokyobadger said:**
> It appears some people are having problems with USB devices and the 3.13.0-xx kernels with 3.13.0-37 coming up frequently.

You could try either the rescue mode (select advanced options under one of the kernels at grub screen) or chroot from a livecd/dvd environment.

From there you could try 
1. fixing 3.13.0-37 [as this user did](http://ubuntuforums.org/showthread.php?t=2248510)

2. upgrading to a 3.16.xx kernel [as this user did](http://ubuntuforums.org/showthread.php?t=2231553) or[as this mint user did](http://forums.linuxmint.com/viewtopic.php?t=185269&p=961782)

3. reinstall ubuntu 14.04 from scratch opting for updates during install (which you would also do from the livecd/dvd but no chroot)

Personally I'd go for reinstall as last option and try the options in numerical order

I've tried reinstalling with updates many times hence I'm scratching that out :), in one of the links you provided an user commented that he would always go with the latest kernel with a new computer, and that sounds very plausible because even NVidia GeForce did not have an official driver for download for a long time hence I would assume that GTX 645 (in the beginning of 2014) was fairly new hence I am more inclined towards upgrading my kernel.

I've updated to 3.19 and I have not faced that issue yet, I will keep you updated and thank you again for your effort :

---

### Post by tokyobadger on 2015-02-12
[quote="lordbalmung"]in one of the links you provided an user commented that he would always  go with the latest kernel with a new computer, and that sounds very  plausible because even NVidia GeForce did not have an official driver  for download for a long time hence I would assume that GTX 645 (in the  beginning of 2014) was fairly new hence I am more inclined towards  upgrading my kernel.[/quote]
Are you using nvidia proprietary or nouveau? I have GTX680 in this box since 2013 and had no problems with proprietary until the last 6 to 9 months which has typically boiled down to Unity/Compiz/kernel issues.

That aside, I'm glad to hear (if I understood correctly) that 3.19.xx is working for you. Might have to try it myself at the weekend when it comes

---

### Post by lordbalmung on 2015-02-18
> **tokyobadger said:**
> Are you using nvidia proprietary or nouveau? I have GTX680 in this box since 2013 and had no problems with proprietary until the last 6 to 9 months which has typically boiled down to Unity/Compiz/kernel issues.

That aside, I'm glad to hear (if I understood correctly) that 3.19.xx is working for you. Might have to try it myself at the weekend when it comes

Hi, @tokyobadger, you are right, I think it is the Unity/Compiz/kernel issues and the 3.19.xx has fixed it, I ran it for a week without crashing even once, that to me sounds like a life time :O, The issue is solved!!!! Thank you very much and yes, if you have an issue with the Graphic card, you should try upgrading too. Thank you for your constant help, I really appreciate it :)

---

