---
title: "Error in lubuntu installation, please help"
date: 2020-03-11
forum: Installation &amp; Upgrades
---

### Post by koroshiya-san on 2020-03-11
I am a new user switching from Windows 7 to lubuntu. Got this screen after I clicked on install when booting from USB.{https://imgur.com/a/Tb7onXY}

---

### Post by guiverc on 2020-03-11
You didn't mention which release of Lubuntu you are using, the screen looks like it's an early 18.04 release (18.04 or 18.04.1 using GA or the general kernel)

I'll provide the manual pages for the latest (stable) release of Lubuntu, ie. 19.10 which relate to installing Lubuntu, ie. [https://manual.lubuntu.me/stable/1/Installing_lubuntu.html]("https://manual.lubuntu.me/stable/1/Installing_lubuntu.htmlChapter") 
Chapter 1.1 Retrieving the image - [https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html](https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html)
Chapter 1.2 Booting the Image - [https://manual.lubuntu.me/stable/1/1.2/booting_the_image.html](https://manual.lubuntu.me/stable/1/1.2/booting_the_image.html)
Chapter 1.3 Installation - [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)

Key steps needed are validating the ISO after download (found in chapter 1.1 or Downloading the image via HTTP), and then later verifying your write to your install media (mentioned in chapter 1.3 Installation, where it's the *Check disk for defects* option).

General instructions for all Ubuntu flavors can be found at
[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0) [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
(for the second link CD refers to any install media, be it CD/DVD/HDD/SSD/thumb-drive/flash-card/..)

My suspicion is you either had a bad download (flawed ISO) OR probably more likely a bad write to your install media. These checks take seconds-minutes only, yet saves hours-days of problem solving so even if the tests pass correctly, I think it's still worthwhile.

If you cannot perform a valid check on the machine you want to install on, I usually go and do the *Check disk for defects* test on another box, and if fails or I can't perform it on that box also, I assume it's a FAILed test and re-write ISO to install media.

You may not need these, but given in my experience it's the writing to media that fails most, I'll also provide generic instructions (they apply to all flavors and releases of Ubuntu inc. Lubuntu 18.04 LTS)
[https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-ubuntu/14011](https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-ubuntu/14011)
[https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-windows/14020](https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-windows/14020)
[https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-macos/14016](https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-macos/14016)

---

### Post by koroshiya-san on 2020-03-11
Thanks a lot
Yes, the version I am installing is 18.04 because I couldn't find a 32 bit option for newer versions.
I will check out all these links and try again today and will report again if I encounter some other problems.

Once again, thanks a lot

---

### Post by koroshiya-san on 2020-03-12
I was able to get into the graphical interface where it asks to choose language and all but after I pressed install it loaded for some seconds and then it hung up. The mouse pointer also doesn't move, the screen remains the same.

This has happened 2-3 times, I can't go to windows because I think my HDD got formatted because of my previous attempts


Help!!!

---

### Post by koroshiya-san on 2020-03-12
So, it's saying " ubi-partman failed with exit code 10. Further information may be found in /var/log/syslog.

---

### Post by guiverc on 2020-03-12
You haven't said that you verified the ISO download (ie. sha256sum, md5sum etc), which is not a very common issue, but given there are multiple sites that offer Lubuntu for download (but only one is related to Ubuntu/Lubuntu, the rest are not), I think it's very important.

Second you didn't mention if you verified your write to install media (ie. run the "*Check disk for defects*" option). It's this step I find more commonly fails. If you get any sort of problem here, it's most likely the write of the ISO to your install media was faulty, and thus should be performed again

---

### Post by koroshiya-san on 2020-03-12
Sorry, I forgot to mention it.
I selected "check disk for defects" option, it ran it's it's course and displayed the following message "check complete, 1error found" or something close to that.

It also displayed messages saying "error found in program" and such while installing. 

What do you suggest Mr. Guirec, should I try to reburn on the USB or should I completely download a new iso file.
The problem is I only had access to my own pc but now I messed up and windows 7 also got deleted so now I'll have to access some other pc and create another USB boot loader. I will try to check disk on the same pc from which I'll try create the boot loader. Hopefully, that will allow me to install it the next time.

PS: I'm pretty sure I downloaded from the correct site. 

I used Universal USB installer instead of Rufus, I think that might be related to the problem since I found some forums about similar troubles with Ubuntu and Universal USB installer.

Please tell me what I should do after this.
1) should I use some other pc, download another iso and remake the bootloader and check disk on that pc?

2)there is some way to maybe work around the same bootloader, which my inexperienced self is not aware of, which you might be kind enough to tell me about.

Also, please tell me the recommended iso file and lubuntu version for my system. It doesn't even have to be lubuntu, since I've deleted windows I must shift to some other OS and I think Linux might be good. I selected lubuntu because I read that it is light and good for pC's with less resources.

These are the specs of my pc: 32bit, 2gb ram, 250gb ROM, I think 2000ghz processor.

Please recommend the best distro and version according to you.

Thanks in advance.

---

### Post by yancek on 2020-03-12
Do you get anything more specific than 'error found' as that is generally the case?  If you choose to download a new iso, it will serve you well to check the iso after it is downloaded.  There is nothing wrong with the iso while it is on the Ubuntu/Lubuntu server but it can be corrupted in the process of being downloaded to your computer.  This should be explained at the Lubuntu site.

---

### Post by GhX6GZMB on 2020-03-12
The official site for Lubuntu is:

[https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

All others are fakes and may contain malicious stuff.

My experience with Lubuntu install is very positive, it generally works "out of the box".

---

### Post by guiverc on 2020-03-12
> **koroshiya-san said:**
> Sorry, I forgot to mention it.
I selected "check disk for defects" option, it ran it's it's course and displayed the following message "check complete, 1error found" or something close to that.
..
What do you suggest

Myself, an error on a check means I'd ignore that USB completely (treating it as a blank thumb-drive) and return to the prior step, ie. re-validate the ISO & re-write (burn) to the thumb-drive/install-media.


> **koroshiya-san said:**
> 
The problem is I only had access to my own pc but now I messed up and windows 7 also got deleted so now I'll have to access some other pc and create another USB boot loader. I will try to check disk on the same pc from which I'll try create the boot loader. Hopefully, that will allow me to install it the next time.

PS: I'm pretty sure I downloaded from the correct site. 

I'll deal with the site first, lubuntu.net (unofficial) tends to direct to ubuntu.com for the actual download so I can't imagine it providing an invalid ISO; as for the non-english sites that offer Lubuntu I don't know as I struggle enough with just english :)

Me (in your shoes), I'd return to validate the ISO you have (or download it again and then validate it) and write to install media again. Check it before use ("*Check disk for defects*" option, and any errors in that mean it's untrustworthy & a waste of time trying to use it)


> **koroshiya-san said:**
> 
I used Universal USB installer instead of Rufus, I think that might be related to the problem since I found some forums about similar troubles with Ubuntu and Universal USB installer.

I can't help here beyond providing links I've already provided. I only use GNU/Linux, and carry thumb-drives so I can use it when I need to use someone else's windows box.

> **koroshiya-san said:**
> 
Please tell me what I should do after this.
1) should I use some other pc, download another iso and remake the bootloader and check disk on that pc?

2)there is some way to maybe work around the same bootloader, which my inexperienced self is not aware of, which you might be kind enough to tell me about.


I've already said this, I wouldn't trust your existing media with errors being detected, yes it could be used given enough days-weeks of work but it's just not time-economical when a new ISO can be downloaded and written to media in 10 minutes or less. 

> **koroshiya-san said:**
> 
Also, please tell me the recommended iso file and lubuntu version for my system. It doesn't even have to be lubuntu, since I've deleted windows I must shift to some other OS and I think Linux might be good. I selected lubuntu because I read that it is light and good for pC's with less resources.
These are the specs of my pc: 32bit, 2gb ram, 250gb ROM, I think 2000ghz processor.
Please recommend the best distro and version according to you.
Thanks in advance.

If you CPU is x86 only, then Lubuntu 18.04 LTS is the best release for you. However if your machine came with windows 7 it'll likely have a 64-bit CPU (you didn't provide cpu specs) coming with the x86 windows because microsoft charged less for it so OEMs used it as buyers only noted the "Windows 7" not the x86/x86_64 difference.  The box I'm typing this into is from 2009 & runs x86_64 fine (a c2q-q9400 so before the i3/i5/i7 were released)

The 2GB of ram is the main issue, yes it'll run fine, but the OS I'd opt for would depend on how you want to use your machine, and the software you want to use. On my *lenovo thinkpad sl510 (c2d-t6570, 2gb ram, i915) where specs are (cpu, ram, gpu)* I have installed Lubuntu 18.04 LTS (with Xubuntu also installed as I do like using XFCE too).  I have the LTS on that box as I rarely use it (*I hate laptop keyboards*) so opted for something I can install & forget.

If your box is x86 (32-bit) I'd stick with Lubuntu 18.04 LTS.  However if you've got the bandwidth, I'd download the Lubuntu 19.10 and write to install media (thumb-drive), validate it & then boot it using "*Start Lubuntu*" and I'd expect it'd run fine. That will give you another choice. 

Lubuntu 18.04 LTS is supported until 2021-April, so if you're happy with that use 18.04 LTS.  If you can use 19.10 and want to use your device longer than 2021-April then I'd likely install Lubuntu 19.10, and in a month or two *release-upgrade* to 20.04 LTS using the new LXQt desktop. That's not an option with Lubuntu 18.04 LTS due to it's use of LXDE  (possible yes, I did it on my box, but there are problems & aren't fun to fix, hence unsupported..)  My next option would be Xubuntu 18.04 LTS (which will upgrade to 20.04 LTS easily).  My 2c anyway.

---

