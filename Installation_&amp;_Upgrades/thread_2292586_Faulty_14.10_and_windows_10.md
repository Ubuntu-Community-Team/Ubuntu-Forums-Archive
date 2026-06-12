---
title: "Faulty 14.10 and windows 10"
date: 2015-08-29
forum: Installation &amp; Upgrades
---

### Post by kennedyhart716_a on 2015-08-29
Please help as I'm not sure how to proceed with this one.
I've previously updated to 14.10 in dual boot with windows 7, but for some reason it was incomplete and even on a re-install I couldn't get updates etc.
Now I want to scrap 14.10 completely and fresh install on the latest ubuntu, but I also want to upgrade to windows 10.
Windows 10 won't proceed as it says it can't ascertain whether there's enough space - this with 320GB free. I gather that is linked to the dual booting with ubuntu [don't ask my how, I don't run microsoft]
My questions are:
1] How can I get rid of ubuntu 10 and its partition so that windows will upgrade. 
2] My thought is that I could then set up the latest ubuntu and partition from within windows - am I thinking straight here? I seem to remember that's what I did way back in the old days - about ten years ago.
3] If installing from within windows, do I have to turn off FastStart before installing so that I can get a dual boot?

Hope this is clear. Thanks in anticipation

---

### Post by Bucky Ball on 2015-08-29
Boot from Ubuntu live media, disk or USB. 'Try Ubuntu' and when at a desktop Launch Gparted and delete all partitions. Install Windows 10 then install Ubuntu.

---

### Post by sudodus on 2015-08-30
Some years ago there was wubi, that could 'install' Ubuntu from within Windows. But wubi cannot not work with the newest versions of Windows (8 and 10 installed with UEFI), so it is not developed any more. Instead you should install Ubuntu alongside Windows (boot directly from BIOS or UEFI). But as Bucky Ball suggests,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by hakuna_matata on 2015-08-30
> **kennedyhart716_a said:**
> 
I've previously updated to 14.10 in dual boot with windows 7, but for some reason it was incomplete and even on a re-install I couldn't get updates etc.

14.10 has reached its [&#8220;end of life"]("http://www.ubuntu.com/info/release-end-of-life"). So, if you couldn't get updates, it is a feature not a bug ;-).
> **kennedyhart716_a said:**
> 
2] My thought is that I could then set up the latest ubuntu and partition from within windows - am I thinking straight here? I seem to remember that's what I did way back in the old days - about ten years ago.

Besides the current official maintainance situation of Wubi, it doesn't make sense to use Wubi for your issue. There is no space advantage in using virtual partitions instead of real partitions.
> **kennedyhart716_a said:**
>  
3] If installing from within windows, do I have to turn off FastStart before installing so that I can get a dual boot?

Theoretically, yes. But official Wubi versions do not support UEFI and unoffical Wubi versions can turn off Fast Startup and Hibernate by using Windows command: "powercfg /h off".

---

### Post by Bucky Ball on 2015-08-30
There is _no_ official Wubi version. It hasn't been supported by Canonical in ages and you will get little to no support for it here (as no-one uses it anymore). Don't go there and if you do you will be pretty much on your own.

---

### Post by hakuna_matata on 2015-08-30
> **Bucky Ball said:**
> There is _no_ official Wubi version.
Unfortunately, yes. It is unmaintained, broken and not recommended of  course, but it still exists on current ISO of Ubuntu 15.04:
[http://releases.ubuntu.com/vivid/ubuntu-15.04-desktop-amd64.list](http://releases.ubuntu.com/vivid/ubuntu-15.04-desktop-amd64.list)
...and wubi.exe is still signed by Canonical. A signed version can not be unofficial.

edit: Additionally, there are still official versions for older Ubuntu versions:
[http://releases.ubuntu.com/precise/wubi.exe](http://releases.ubuntu.com/precise/wubi.exe) for 12.04.5
[http://releases.ubuntu.com/trusty/wubi.exe](http://releases.ubuntu.com/trusty/wubi.exe) for 14.04
The version for 12.04.5 works, if you need no UEFI support. The version for 14.04 only works with workarounds and if you need no UEFI support. But no recommendation, only information.

---

### Post by kennedyhart716_a on 2015-08-30
Thanks Bucky Ball and the rest. Will do as Bucky Ball suggested. Just a couple of issues for clarification. First, sorry - I meant ubuntu 14.04 [must have windows 10 on the brain!].
1] A little confused because of what sudodus has added. "you should install directly....or UEFI". I presume that this means I do this from boot up, but will I still get a dual boot menu as I've always done?
2] Second - this proves I'm a technical nobody! - what is the difference between booting directly from BIOS or UEFI? How can I tell the difference? What difference does it make? Up to now it seemed that I just asked for an install and it pretty much was straightforward from there. Obviously I've lost the trail somewhere along the line!
Yours uncertainly
Ken

---

### Post by sudodus on 2015-08-30
Booting directly from the computer's BIOS or UEFI in a dual boot system means booting with grub, and you have a grub menu, where you can select the system you want to run.

If Windows is installed in UEFI mode, then you should also install Ubuntu in UEFI mode. Just install it without changing the mode from what you use, when you run Windows.

[Info about UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by Bucky Ball on 2015-08-30
... like sudodus says, but if UEFI, boot into Windows and make sure fastboot is off and it is not in hibernation mode. Boot to the BIOS and switch off faststart (although Ubuntu might deal with this now). You will also need to use 'Something Else' at the partitioning section and have some free space to plop Ubuntu onto. Create this free space when booted into Windows. Do not shrink the Win partition with Gparted or Linux tools. Use Win resizing software if you need. 

Hope that adds a little more to the puzzle. :)

PS: If Windows is Win7 or above and came pre-installed in the machine then it is almost certainly 99.9% a Win UEFI install, in which case install Ubuntu in UEFI mode as well.

---

### Post by kennedyhart716_a on 2015-09-03
To Bucky Ball and sudodus,
Thanks for help so far. Sorry I haven't followed this up as I've been out of circulation for a few days.
Just to make sure I get this right .......
1]  I'm currently on Win 7 and Ubuntu 14.10. 14.10 was an update. I installed Win 7 myself on machine I built. Can't remember whether it was BIOS or UEFI - or 14.10 for that matter?
2]  Faststart / fastboot - neither listed in Win Help - does this mean I'm not on UEFI?
3]  Does the amended sequence run as follows?
     Boot from Ubuntu disk - Try Ubuntu - Gparted - delete all ***UBUNTU*** [?] partitions - quit - boot into Windows - install Win 10 - reinstall  Ubuntu 14.10 from [I][B]within Windows [?] 
[/B][/I]If so, will Windows have automatically extended following deletion of ubuntu? I can't seem to find a way to repartition for Ubuntu in advance through Windows. If Windows has NOT taken in the deleted ubuntu space, how can I access it? 
Lastly, am I right in thinking I sort the partition problem AFTER upgrading to Win 10?

Sorry - this must seem incredibly obvious to you. I think it was your last advice that threw me - not your fault. I AM fairly competent at other things in life!

---

### Post by sudodus on 2015-09-03
Ubuntu 14.10 has passed end of life. I would recommend that you use a long time support version, right now 14.04 LTS. Standard Ubuntu and Kubuntu are supported for 5 years, until April 2019. Lubuntu and Xubuntu are supported for 3 years, until April 2017. I don't know about the other flavours. The next long time support version will be 16.04 LTS, to be released in April 2016.

Backup your personal files. Make a fresh install.

When you run Ubuntu, you can run the following command from a terminal window to find out if you run in UEFI mode or not:

```
test -d /sys/firmware/efi && echo "booted via EFI (UEFI)" || echo "booted via BIOS (legacy boot)"
```

No, do ***not*** install Ubuntu from within Windows (unless you want to create a virtual machine, for example with VirtualBox, and run Ubuntu inside that virtual machine). Boot directly into Ubuntu from the BIOS or UEFI and create a dual boot system.

It is better to create partitions before you install Windows 10, and try to force Windows 10 into a limited space. Then you need not edit the partitions after installing Windows (which is much slower and much more risky, because there are a lot of files there).

---

### Post by Constantin_Dolinin on 2015-09-13
Wubi in 15.04 amd64 DVD had wrong version. I downloaded it today and Wubi is trying to install 14.10 (with no result). I'm really don't know what it was and what can I do with it.

---

### Post by sudodus on 2015-09-13
Welcome to the Ubuntu Forums :-)

[Wubi is no longer developed and no longer supported](http://ubuntuforums.org/showthread.php?t=2229766) because it does not work with Windows 8 and UEFI. Please try a dual boot installation or install in a virtual machine instead.

Please start an own thread with a good descriptive title if you need help! That way you have better chances to attract people who might be able to help.

---

