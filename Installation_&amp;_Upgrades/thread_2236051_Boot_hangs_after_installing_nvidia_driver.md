---
title: "Boot hangs after installing nvidia driver"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by larry23 on 2014-07-24
Update:

Followed the steps here: [http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers](http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers)



I'll preface this by admitting that I am a linux novice. I do run commands through linux at work but this is my first experience with setting up a desktop with linux. It is not as nurturing as I would've hoped.

Lubuntu version 14.04
GTX 750 TI

I've removed quiet splash from grub
I've added nomodeset
I've tried this with nvidia-current (version 304), nvidia-331, nvidia-340... PPAs, command line, synaptics package manager
Reinstalled twice just to start with a 'clean' state


After I install my nvidia drivers and reboot the machine, the bootup hangs/stops/freezes at the line ```
Adding 4051964K swap on /dev/sda5. Priority:-1 extents:1 across 4051964K FS.
```
Booting with recovery mode shows a different message with the same result of freezing: ```
nvidia : module verification failed: signature and/or required key missing - tainting kernel
```

I have used several different methods for installing the new driver, and follow the instructions to a tee. I've spent two whole days trying to do this on my own (with the help of google, of course) and now it's time I ask for your help, as I cannot figure out how to resolve this.

Thanks in advance.

edit:

Here's some additional info.
```

sedna@sedna:~$ uname -a
Linux sedna 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```


```

    sedna@sedna:~$ sudo lspci -vnn|grep VGA -A 12
    01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] [10de:1380] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device [3842:3753]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [250] Latency Tolerance Reporting
```

---

### Post by sp40140 on 2014-07-24
When you have fresh install, do you have any issues with display? Any reason that you want to install prop drivers instead of running open source ones?
What version of Ubuntu? what is the version of kernel?

---

### Post by larry23 on 2014-07-24
> [COLOR=#000000]When you have fresh install, do you have any issues with display?[/COLOR]

Depends what you mean by "issues." After choosing to install (or try lubuntu without install), the screen would hang with a blinking cursor. I had to turn on *nomodeset* to get past it. The screen also doesn't appear "crisp" but I would expect that before installing the driver.

> [COLOR=#000000]Any reason that you want to install prop drivers instead of running open source ones?[/COLOR][COLOR=#000000]

[/COLOR]I've done both. I wanted to go for proprietary drivers in the beginning because I could get the very latest version but now I'm willing to take any driver.

> [COLOR=#000000]What version of Ubuntu? what is the version of kernel?[/COLOR]

Ubuntu version is Lubuntu 14.04. Installed from aflash drive, I performed an MD5 checksum to verify it was correct.
Kernel version is 3.13.0-24 generic

---

### Post by Bucky Ball on 2014-07-24
Might not fix your problem, might be a little off topic, but I advise you open a terminal and:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

The 14.04 LTS kernel is at 3.13.0-32 now so that is an older one (much) you're using. See if that gives you any joy. Generally first thing on the agenda with a new install is to do an update then see what, if anything, is broken. An update to the newest kernel will give us a better idea of where things sit as if you fix it now and then do an upgrade (leapfrogging a heap of kernels) it may just break again anyway (or the new kernel may have fixed it in the first place).

Also, after the update/software upgrade, what driver, if any, do you get offered in 'Additional Drivers' (may be 'Hardware Drivers' for you)?

---

### Post by larry23 on 2014-07-24
I upgraded to the 3.13.0.32 kernel during a previous install and it didn't help at all, which leads me to believe my problems lie elsewhere, but I will upgrade the kernel again.

> [COLOR=#000000]Also, after the update/software upgrade, what driver, if any, do you get offered in 'Additional Drivers' (may be 'Hardware Drivers' for you)?[/COLOR]

None. I did see two after adding a PPA (sorry, name escapes me) . Installing the binary from this did not correct the problem.

---

### Post by Bucky Ball on 2014-07-24
Appears the GTX 750 TI is fairly new and problematic. Someone did get a 'kinda' fix here:

[http://ubuntuforums.org/showthread.php?t=2214805&page=2&p=13021101&viewfull=1#post13021101](http://ubuntuforums.org/showthread.php?t=2214805&page=2&p=13021101&viewfull=1#post13021101)

Looks like the noveau open source drivers are do-able also. That whole thread may give you some ideas.

Not sure where development of a Linux driver for that is at, but you could do some research. Careful about installing too many PPAs and trying too many drivers. May cause confusion, other issues, and PPAs are not all trustworthy or stable. ;)

---

### Post by larry23 on 2014-07-24
What's the  connection between the nvidia driver and ***Adding 4051964K swap on /dev/sda5. Priority:-1 extents:1 across 4051964K FS***?
No one in the thread (or  linked threads) mentioned the message I'm getting... is it irrelevant?

---

### Post by Bucky Ball on 2014-07-24
> **larry23 said:**
> What's the  connection between the nvidia driver and ***Adding 4051964K swap on /dev/sda5. Priority:-1 extents:1 across 4051964K FS***?
No one in the thread (or  linked threads) mentioned the message I'm getting... is it irrelevant?

You never mentioned it here that I can see. When are you getting this? Don't think it has anything to do with the graphics problem, but you never know. You better explain that in more detail, when it's happening specifically. :-k

---

### Post by larry23 on 2014-07-24
I mentioned it in the OP:

> After I install my nvidia drivers and reboot the machine, the bootup hangs/stops/freezes at the line **Adding 4051964K swap on /dev/sda5. Priority:-1 extents:1 across 4051964K FS.**

And this happens after *any *&#8203;method of driver installation.

edit:

> [COLOR=#000000]You better explain that in more detail, when it's happening specifically.[/COLOR]

Sorry. Usually it'll take between 5-10 seconds (after initial bootup time) to display this, but then it just hangs there. I read online that some people were experiencing this step taking a long amount of time, ~2 minutes, but I've waited up to 30 on a couple of occasions and no luck. Ctrl-Alt-F1 (or F2-6) doesn't do anything. In order to get out of this mess, I have to boot into bios, choose integrated graphics, switch HDMI cable to motherboard, boot up, and uninstall the driver. Then I can switch it back to the video card's port.

---

### Post by Bucky Ball on 2014-07-24
Apologies, my mistake. Hmm. And that has just started with the driver install I presume. The machine was booting to a desktop okay before the driver install? Hard to see how it is related as it is referring to the /swap partition. Maybe someone else might see the connection. 

 Have you scanned the fix I linked to here:

[http://ubuntuforums.org/showthread.p...1#post13021101](http://ubuntuforums.org/showthread.p...1#post13021101)

Reading the whole post might give you some clues. As I mentioned, Linux might not have caught up with that card yet, but the noveau drivers appear to work.

---

### Post by larry23 on 2014-07-24
Yes, the boot process hangs only after the nvidia-driver install. If I remove the driver it will work again.

I believe OP's issue in the linked thread was his kernel.. they were on 3.11. They haven't posted an update so it's tough to say what the real issue was there.

---

### Post by Bucky Ball on 2014-07-24
> **larry23 said:**
> Yes, the boot process hangs only after the nvidia-driver install. If I remove the driver it will work again.

In that case I suggest you remove the driver, boot to a desktop and try installing the driver suggested in the fix in the link if you haven't already. You could also try a search for 'GTX 750 TI ubuntu' (add 14.04 if you want to get specific) with a search engine and see what that digs up. I hit a few.

---

### Post by larry23 on 2014-07-24
I was able to get it to work! I took your advice on searching specifically for my graphics card and followed the steps here:

[http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers](http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers)

Thanks for the help, Bucky

---

### Post by Bucky Ball on 2014-07-24
Great news and good work! Enjoy. 

The one mentioned in my link was the 337.19, which is more recent, but as long the 334 is working to your satisfaction, all good. ;)

---

