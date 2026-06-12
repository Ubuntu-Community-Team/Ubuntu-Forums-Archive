---
title: "xubuntu 14.04 live cd hangs"
date: 2014-06-30
forum: Installation &amp; Upgrades
---

### Post by Kilarin on 2014-06-30
When booting the xubuntu 14.04 live cd, it gets to the pretty blue screen that says Xubuntu with the little animated circling icon beneath, and just stays there.  The icon keeps circling, for up to 30 minute, and it never gets to the "try out xubuntu or install xubuntu" screen, and never presents me with any kind of error message.

This happens on a HP G60-441 laptop, Ram=2950MB, Processor=x86_64, that already has ubuntu 11.04 on it.  I want to do a fresh install of xubuntu 14.04 32bit, because I had it running on 32bit for ubuntu 11.04 and didn't see any reason to hassle with 64bit for a machine that only has 3gig of ram anyway. I burned a live cd of xubuntu 14.04, xubuntu-14.04-desktop-i386.iso, this is the same live cd that I successfully used to install xubuntu onto another computer, and that I can STILL use to boot another computer.  So the dvd itself is fine.  But it simply will not complete booting on the laptop.

So, my questions are:
1: Any clue what would be stopping the live-cd from booting on the G60-441 laptop?
2: Is there a secret key I can press during the booting process that will display the boot messages so I can see where it is getting hung up?

Thank you in advance for your help.

---

### Post by ajgreeny on 2014-06-30
This may be of no consequence, but I have an old laptop (Acer Travelmate 2200, with Celeron cpu, 512MB ram amd ATI 9000M graphics) which did exactly the same thing when I tried to install either Lubuntu or Xubuntu 14.04. It was already running Lubuntu 13.10 with no problems at all, so I was totally baffled.

I tried installing using the Alternate Install CD of Lubuntu 14.04 but still could not get the machine to boot to the installation medium.  By this time I had already formatted the root partition ready for the new OS so I reinstalled 13.10, fully updated it then used the 14.04 Lubuntu Alternate install CD as a repository with which to upgrade from 13.10 to 14.04.  That worked well, but when I rebooted the machine again would not boot to a working system; it just hung again just like before, and the same as yours.

As I had updated from 13.10 I still had the 3.11.0 kernel installed and available from grub, so I booted to that, uninstalled the 3.13 kernel and the machine now works brilliantly, if a bit slowly, but at least that is no different from how it ran with any previous Lubuntu version.

It therefore seems that my problem is the 3.13 kernel, which simply refuses to boot with my hardware.  I have even tried the 3.14 kernel series but that is just the same, so I have now given up any kernel updates on that machine and accepted that for now at least, 3.11 is quite good enough.

Perhaps your problem is the same, though I agree that your hardware is much more recent than mine, and amount of ram can not be your problem.  Regretably there is no Alternate Install CD for Xubuntu, only Lubuntu, so you can not do exactly what I did, but this may give you a chance to install Lubuntu then add Xubuntu-desktop to that for your chosen OS.

---

### Post by Kilarin on 2014-06-30
Thank you for the advice.  I am REALLY hoping there is a simpler solution, but if all else fails, I'll give this a try. :)

---

### Post by mörgæs on 2014-07-01
You could try booting the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") from USB. When that runs you can add the Xubuntu desktop.

---

### Post by sudodus on 2014-07-01
Another alternative is to try ***Xubuntu 12.04 LTS*** (supported until April 2015) or a community re-spin based on Ubuntu 12.04 LTS. ***Bento, Bodhi and LXLE*** promise support until April 2017, and the Ubuntu packages under the hood (desktop environment) are well debugged and polished.

You can also install standard ***Ubuntu 12.04 LTS***, and if it makes the computer slow, you can ***tweak*** the system according to this link and get a responsive gnome system with support until April 2017

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by Kilarin on 2014-07-01
Thank you for the suggestions everyone.

This story gets stranger and stranger.  Since it is a 64bit system I tried downloading and burning xubuntu-14.04-desktop-amd64.iso
And it booted to the live cd version of xubuntu!  I attempted the install, and it went fine through about 3/4 of the process, and then gave me the error:

**[Errno 5]Input/output error**

and said the dvd was probably bad.  It pops up a screen saying that once you close this screen it will generate a bug report, but that screen won't close.
I tried a bunch of different fixes, but they all still crash in the same place in the install.

The file system DOES seem to be written to the partition, but GRUB no longer works and I can't even boot into windows.  I may have to go back to my pre install image.

Attempts to fix:
[list]
[*]confirmed the md5 of the burned dvd matches the website md5:
```
$ dd if=/dev/cdrom | md5sum
1869824+0 records in
1869824+0 records out
ae446659057ee49e57773bf446398856  -
957349888 bytes (957 MB) copied, 90.7356 s, 10.6 MB/s
```
[*]burned another dvd anyway and tried that, same error.
[*]I tried skipping the "try xubuntu" and going straight to the install xubuntu, same error.
[*]I tried not checking "download updates", same error.
[*]I switched from formatting to ext4 back to ext3, same error.
[*]I unchecked the "encrypt homedrive" option, same error.
[*]did an fsck -f on the partition, it found no problems. 
[*]I did a memtest, it indicated no errors
[/list]

I copied the logs from /var/log, but I'm not entirely certain what is significant in them.  The following stands out
/var/log/installer/dm:
```

(nm-applet:2162): GLib-CRITICAL **: Source ID 84 was not found when attempting to remove it
xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 21 requests (21 known processed) with 0 events remaining.
(EE) Server terminated successfully (0). Closing log file.
ubiquity-dm: set_locale
Generating locales...
  en_US.UTF-8... up-to-date
Generation complete.
ubiquity-dm: Exiting with code 0
```

/var/log/syslog:
```
Jul  1 16:47:27 xubuntu kernel: [ 2141.234883] Thunar[4282]: segfault at 8 ip 00007fe22cdbfbc5 sp 00007fffc10cb900 error 4 in libglib-2.0.so.0.4000.0[7fe22cd5c000+106000]
```

I archived the whole var/log folder and put it here if it can help anyone analyze whats going on:
[http://www.mediafire.com/download/4oc1quwnsc8od6d/log-frm-install.tar.gz](http://www.mediafire.com/download/4oc1quwnsc8od6d/log-frm-install.tar.gz)
/var/crash was empty.

I guess that the next options are to try the 12.04, the minimal cd, or attempt to install from usb?

Again, thank you everyone very much for your help so far.  Any further advice would be greatly appreciated.

---

### Post by sudodus on 2014-07-01
Maybe the 64-bit system is so early that everything does not work properly (if the cpu is OK maybe something on the motherboard is not), so you may have better luck with a 32-bit iso file. Errors looking like yours might occur with too little RAM, but you have enough RAM (with a margin). There might be a problem due to some driver's cooperation with its hardware too.

Anyway I agree, that ***Xubuntu 12.04 LTS*** is a good option for your next attempt. Bear in mind, that it is only supported until April 2015.

Other alternatives promise support until April 2017: Install ***standard Ubuntu 12.04 LTS and tweak it*** according to this link to make it lighter

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

or install a community re-spin based on Ubuntu 12.04 LTS,* **Bento, Bodhi or LXLE***.

Try them live before installing.

---

### Post by Kilarin on 2014-07-01
GOOD NEWS!
I burned a copy of 12.04 32bit live cd and it installed just fine!
updating the system now.  Then will attempt an upgrade from there to 14.04.  If the upgrade doesn't work, I'll go back to 12.04 for now.

Thank you for your help folks!

---

### Post by sudodus on 2014-07-01
Congratulations :KS

Please tell us which flavour of Ubuntu you are running: Xubuntu or ... ?

When you feel that the problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by Kilarin on 2014-07-01
> **sudodus said:**
> Please tell us which flavour of Ubuntu you are running: Xubuntu or ... ?
I downloaded xubuntu-12.04.4-desktop-i386.iso from [http://cdimage.ubuntu.com/xubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/12.04/release/)
It installed pretty smoothly.  Updated, then used sudo update-manager -d  to upgrade to 14.04, which also went pretty smoothly!

[quote="sudodus"]When you feel that the problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED[/QUOTE]
Took a bit of a twisted path to get there, but I'm now running xubuntu 14.04 on the laptop, which was the goal.  So this is solved.  

Again, thank you everyone for your help!

---

### Post by mörgæs on 2014-07-02
Good, the lesson of this is to use USB as much as possible for install. 

It's probably good if you take a look at the hard disk, especially the SMART data, to see if it's close to failing. Also the **badblocks** command is worth trying.

---

