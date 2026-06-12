---
title: "LiveUSB fails to boot, out of memory errors"
date: 2015-08-02
forum: MINT
---

### Post by montag dp on 2015-08-02
I normally dual boot Linux and Windows 7 on my Thinkpad T430 (dual core Intel i5, 4 GB of RAM). I mostly use Linux but keep Windows around mainly because Lenovo included some useful tools for things like battery maintenance. Today, out of curiosity, I decided to try upgrading to Windows 10. I figured it probably wouldn't work, but I backed up my files and figured the worst that could happen would be that I'd have to reinstall one or more operating systems.

Well, it failed worse than I thought it would, and I ended up with a broken boot loader. My Windows 7 recovery disk didn't work, so I figured I should be able to just wipe everything with a LiveUSB and reinstall Linux. However, the LiveUSB isn't working either. I'm getting lots of messages that say "Out of memory: kill process xxxx or sacrifice child." Running in compatibility mode, it seems to be able to do more things, but I'm still getting those errors and also errors from systemd-udev saying it failed to allocate memory. It's currently still apparently trying to do things but I have my doubts that it will work.

So, are there any ideas what's wrong? Apparently Windows really screwed up my system, but I'm not sure what exactly is screwed up. My guess is the RAM is messed up due to the out of memory errors. If that's the problem, it wouldn't be the end of the world to order some new RAM, since it's cheap anyway, but are there any other possibilities? Or, even better, ideas for fixing it without replacing any hardware?

In any case, I think this is the last straw for me with Windows. If I can fix this, I think it will be Linux full time for me.

---

### Post by Vladlenin5000 on 2015-08-03
Do you really had a dual boot? Or have you used WUBI to install it from (and inside) Windows? Are you trying to do the same now?
If not, what exactly is that "compatibility mode"? If its from UEFI/BIOS then it's legacy/CSM (speaking about "compatibility mode" in this context cause confusion - read above). 

In order to have a successful dual boot, you need to install the second OS in the same mode the first one was installed. 
Windows 7 typically installs in the old (BIOS) way (you would need the Microsoft tool for USB in order to install it in UEFI mode). For Ubuntu likewise you need a) a recent and/or still supported Ubuntu release (except 12.04; currently your only options are 14.04 LTS and 15.04) and b) boot the USB in the same way: UEFI if Windows has been installed that way and Legacy/CSM otherwise.

Make sure you have a good ISO to start with.

---

### Post by montag dp on 2015-08-03
Yes, it was really a dual boot. Is Wubi even around anymore? I think that hasn't been an option for several years.

Sorry about the confusion regarding compatibility mode. I am using a Linux Mint LiveUSB created with Unetbootin and that is one of the options on it. I'm not completely sure what its purpose is, actually, but it seemed to do more than the normal "Try Linux Mint" option. Before trying anything else, I will burn an Ubuntu DVD and see if it works, and if I get the same errors I will try to do a memory test.

Could you give more information on what you mean by "boot the USB in the same way"? I believe Windows was originally installed in the "old" (BIOS) way, but I don't know how to check which way the LiveUSB is being booted, out how to change it.

---

### Post by Vladlenin5000 on 2015-08-03
First of all, it's quite easy to check how Windows was installed: If UEFI you'll find an EFI partition; otherwise you'll find a small (~100MB) partition at the beginning of the drive.
Regarding how to boot the installation media, if you have the UEFI+Legacy setting in UEFI/BIOS you&#314;l have two entries in the one time boot menu for all bootable device, one with UEFI being explicitly mentioned and the other without it. Typically:
```
UEFI: Generic USB storage (UEFI mode)
Generic USB storage (Legacy)
```

If you have some new (or relatively new) nvidia card/chip you may need to boot with the *nomodeset *parameter.

---

### Post by montag dp on 2015-08-03
Okay, thanks for the information. It is definitely the legacy way then, because I never see a UEFI option when selecting what to boot, and I did previously have a small partition at the beginning of my hard drive, which is apparently corrupt now.

---

### Post by montag dp on 2015-08-03
Here is an update. I tried burning a live DVD instead of a USB, thinking the ISO on the USB might be bad. Unfortunately, it still is not working. Selecting the default option from the DVD (try without installing) results in an error like the following:

```
Kernel panic - not syncing. Attempted to kill unit! 
```

I am currently trying the "compatibility mode" option. It's taking a long time and still reporting out of memory errors like before, though it seems like maybe not as many.

Now for some minor good news. With the live DVD, I was able to run a memory test, which passed with no errors, so it seems like my RAM is fine. But something is clearly wrong -- I just don't know what. Can anyone help? If you need more information I would be happy to provide it. Just let me know what you need to know.

One more thing, I checked in the BIOS and UEFI is indeed disabled.

---

### Post by sudodus on 2015-08-04
Which version of Linux Mint are you trying to boot?

Did you check with ***md5sum*** that the download was good?

Did you check if you can boot from the USB pendrive or the DVD disk in another computer?

There might be problems with some drivers for ***graphics*** or ***wifi*** - so please specify the chip/card for each of them.

-o-

Maybe you can try Ubuntu 14.04.2 LTS, amd64 alias 64-bit. Maybe you need a proprietary driver.

---

### Post by howefield on 2015-08-04
Thread moved to the "*MINT*" forum.

---

### Post by montag dp on 2015-08-04
> **sudodus said:**
> Which version of Linux Mint are you trying to boot?

Did you check with ***md5sum*** that the download was good?

Did you check if you can boot from the USB pendrive or the DVD disk in another computer?

There might be problems with some drivers for ***graphics*** or ***wifi*** - so please specify the chip/card for each of them.

-o-

Maybe you can try Ubuntu 14.04.2 LTS, amd64 alias 64-bit. Maybe you need a proprietary driver.Unfortunately, I don't have another machine to try the Live DVD/USB. Since they are both having the same issue, I really doubt it's a bad image, but I will check the md5sum tomorrow. (To clarify, I downloaded and burned the DVD from my work computer, but I don't want to try booting that from the Live DVD. It's probably not allowed.)

My computer is a Thinkpad T430 with integrated Intel HD4000 graphics. I'm not sure of wireless card, but I've never needed proprietary drivers before. The USB is Linux Mint Cinnamon 17.2 and on the DVD I have Mint KDE 17.1. Thanks for your suggestions.

I'm going to take the computer to a repair shop tomorrow. He should hopefully be able to at least figure out if there is something wrong with the hardware. If he's stumped too, the next thing I'll do is try Ubuntu 14.04 LTS as you suggested. But, if the expert can't figure it out then I'm really in trouble...

---

### Post by sudodus on 2015-08-05
Maybe you can visit a friend or relative and borrow a computer to test to boot from the DVD and USB drives. It is often easier to boot a middle-aged computer than an new one (because of UEFI and because of drivers for the graphics). I think Linux Mint is developed from Ubuntu 14.04 LTS, so it is one year old, and computers that are 2-5 years old should be easy to boot.

It is possible that it is a hardware problem, but very unlikely that Windows 10 should destroy hardware. Maybe the UEFI software is borked, and the computer might work in BIOS or CSM or legacy mode.

Can you get into the BIOS/UEFI menus?

There should be a hotkey to get there (press the hotkey while booting). Maybe it is the Escape key, maybe F1 ... F12. Some Thinkpads have a special 'access' key. If you can't find it, I think the repair guy should be able to tell you.

Of course it is possible that some hardware component happened to break while you were installing Windows 10 (just a coincidence, not caused by Windows), but it is also very unlikely.

---

### Post by montag dp on 2015-08-05
Yes, I am able to get into the BIOS. I tried resetting the defaults there and making sure UEFI is off, but it didn't help.

---

### Post by sudodus on 2015-08-05
Sorry, I have no other idea right now except that you visit a friend or relative and borrow a computer to test to boot from the DVD and USB drives. That way you can verify that the USB pendrive and/or DVD disk can boot a computer.

---

### Post by montag dp on 2015-08-06
Well, the computer repair guy was able to fix it.  Apparently he needed to remove the CMOS battery and let it sit for awhile to reset it, and then it was able to boot.  I thought I could do the same thing by resetting the BIOS settings, but that didn't work.  Anyway, it wasn't cheap per se, but it was a lot cheaper than what Lenovo was going to charge to repair it (almost as much as the cost of the laptop when I bought it new).  He also put Windows 10 on it for me, which definitely seems better than 7, but still I'm not sure if I will keep it.  Thanks everyone for your suggestions.

---

### Post by sudodus on 2015-08-07
Thanks for sharing your solution :-)

I'm glad it worked out, even if you had to pay for the CMOS battery to be removed. Next time a person at our Ubuntu Forums has a similar problem, I hope someone will remember your solution and suggest it ;-)

---

### Post by hiyoooo4 on 2015-09-09
> **montag dp said:**
> Well, the computer repair guy was able to fix it.  Apparently he needed to remove the CMOS battery and let it sit for awhile to reset it, and then it was able to boot.  I thought I could do the same thing by resetting the BIOS settings, but that didn't work.  Anyway, it wasn't cheap per se, but it was a lot cheaper than what Lenovo was going to charge to repair it (almost as much as the cost of the laptop when I bought it new).  He also put Windows 10 on it for me, which definitely seems better than 7, but still I'm not sure if I will keep it.  Thanks everyone for your suggestions.


Ah, I just got the same problem after attempted to upgrade to windows 10. I tried many different live USBs (ubuntu, mint, win03pe, win8pe, boot repair, ubcd), none were able to boot, some are able to tell me "Not enough memory", including Win10 "page fault in nonpaged area". I have 6144MB memory installed. 

Just removing the CMOS battery (I made it rest for 6 hours) didn't help, what else did the computer guy do to fix the problem?

---

