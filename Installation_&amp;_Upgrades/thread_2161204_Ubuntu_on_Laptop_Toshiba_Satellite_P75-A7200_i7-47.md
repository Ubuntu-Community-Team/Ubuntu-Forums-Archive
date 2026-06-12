---
title: "Ubuntu on Laptop Toshiba Satellite P75-A7200 i7-4700MQ  HD4600"
date: 2013-07-09
forum: Installation &amp; Upgrades
---

### Post by guillerd on 2013-07-09
Hi

First, I am new on the forums, but I have been using Linux for about 2 years now in my desktop computer.

I just bought a Laptop. Toshiba satellite P75-A7200.
Proc:  i7-4700MQ
Video:  HD4600
RAM 8GB
It has Windows 8 preinstalled


For what I have read, the processor and video architecture are rather new. I have not found any other thread that is having this issue:

I want to have dual boot on this computer, but before installing, I wanted to test using the LiveCD.
I followed the instructions to disable fast boot and Windows 8 fast boot feature from here:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

However, when I tried to boot from the LiveCD I got a black screen after selecting the option to try ubuntu or install ubuntu.
After reading the forums I found and used the option "nomodeset", which allowed the boot process complete and get to a command prompt session, but the gui is not working.
If I use startx, it fails. The log says that screens were found, but non is usable.

I would like to see that the livecd can work with the laptop before installing.
If you tell me how to, I can gladly post the XServer log here.


Any help will be appreciated. 
Thanks

---

### Post by guillerd on 2013-07-09
Sorry, I forgot to mention that I am using Ubuntu 13.04 LiveCD 64

---

### Post by DeathByDenim on 2013-07-09
I had somewhat the same problem with an Intel HD4000 + NVidia GT650M combo (and Kubuntu 13.04). I also got a black screen. For me the solution was to just increase the screen brightness using <Fn> + <Arrow right>. You might have a similar keyboard combination for setting the brightness. You could try that?

---

### Post by guillerd on 2013-07-09
Hi DeathByDenim

I don't think that the bright of the screen is the problem, since it seems to turn off (otherwise, when you turn the bright to the lowest level, you can still see the image), and when I use "nomodeset" option to boot, the command line appears fine on the screen.
Anyway, I tried what you mentioned just for fun, and it did not work.

---

### Post by DeathByDenim on 2013-07-09
That's too bad. That would have been an easy solution. :)
Could you try the boot parameter "acpi=off" instead of nomodeset? That's by no means a permanent solution, since it turns off all energy savings, but it might get the liveCD to work at least.

By the way, both Intel and AMD Radeon seem to have an HD4600. Which one do you have?

---

### Post by guillerd on 2013-07-10
It is Intel HD4600
I tried using Ubuntu 13.04   with  nomodeset and acpi=off, and it got stuck with a black screen that says only:
[38.783622] init:failsafe-x main process (2923) terminated with status 1

I had to force power off

Then I tried the same Ubuntu disk with acpi=off only, and it worked! :D
What does that mean?  Is it a problem with the Video Driver for intel HD4600 or the processor i7-4700MQ or Toshiba mother board?
I would not like to boot always with acpi off, since it is a laptop.

Is there something I can do to fix that?

Thanks again.

---

### Post by DeathByDenim on 2013-07-11
Yeah, acpi=off was only meant for testing purposes and at least get the liveCD going. It allows you to at least install Ubuntu 13.04 to the hard drive if you wish.
I'm not entirely sure on how to get it running afterwards though. The processor is certainly not the problem. I suspect the video driver.

Could you try these boot parameters though (instead of acpi=off):
```
acpi_osi=Linux acpi_backlight=vendor
```

---

### Post by kalliergo on 2013-07-11
> **DeathByDenim said:**
>  I suspect the video driver.

Hi, everyone.  I'm not new to the forums, but I almost never log in and post.  I've been a Linux user and system administrator for 15 years -- other *nix systems longer.

I just picked up a P75-A7200 a couple of days ago and I have the same problem.  FYI, the same thing happens during boot with all of the Linux distros I have on CD/DVD, except for Knoppix, which boots and runs from the live DVD perfectly.

This is, indeed, very likely a video driver issue.  I'm going to take a little time today to figure out which driver Knoppix is loading (Iwas doing too many things at once when I booted it yesterday), and I'll keep an eye on this thread, as well.

---

### Post by ValhalaAwaits on 2013-07-11
I'd like to throw a few more details in here.
I am also having this issue on a new p75-a7200
The graphics processor is on the CPU and is intel hd 4600
I have the same experience as guillerd with the 13.04 64-bit live dvd. I was able to edit the grub command to "nomodeset" and get into a fullscreen terminal.
Using the same "nomodeset" on the 'install ubuntu' command line allowed me to get into the graphical installer, which worked fine.

Now I have ubuntu 13.04 installed and can boot into it but there is no gui.
I do see the purple ubuntu screen with the four colored dots, then an error which is too quick to read, and then the full screen terminal.
I've tried adding the [xorg-edgers repository]("https://launchpad.net/~xorg-edgers/+archive/ppa") with mesa 9.2 video driver (because I read somewhere that this was working on intel hd 4600) but that didn't seem to do anything for me.
I use the command line all the time, but this isn't really the linux experience I was looking for.

I would also like to note that I didn't disable fastboot or secure boot.  I don't think those are relevant here but you never know.

---

### Post by kalliergo on 2013-07-11
Just a quick note:  DBD's suggested acpi boot parameters (osi=Linux, backlight=vendor) worked fine for me.

I'll install to the HD and explore and report.

---

### Post by kalliergo on 2013-07-11
> **ValhalaAwaits said:**
> I would also like to note that I didn't disable fastboot or secure boot.  I don't think those are relevant here but you never know.

No, that shouldn't be relevant with this version of Ubuntu.  Anyway, if secure boot was a problem, you couldn't boot the OS at all.

Try the suggested boot parameter changes and see if they help.

---

### Post by japadamaray on 2013-07-15
Those boot options are also working for me. This laptop is now working quite nicely with Linux; I haven't encountered any other issues.

---

### Post by oldfred on 2013-07-16
Another different Intel system:
 Asus i3 with Intel graphics, 
"acpi_osi=Linux"
"video=1280x1024-24@75" or whatever native resolution is

      Some have used this boot parameter with hd4000
  i915.i915_enable_rc6=1


 Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

 Intel HD4000
[http://communities.intel.com/thread/34221](http://communities.intel.com/thread/34221)
[http://ubuntuforums.org/showthread.php?t=2089640](http://ubuntuforums.org/showthread.php?t=2089640)
[http://ubuntuforums.org/showthread.php?t=2126191](http://ubuntuforums.org/showthread.php?t=2126191)
Also one used nolapic.
[http://ubuntuforums.org/showthread.php?t=2133816](http://ubuntuforums.org/showthread.php?t=2133816)
GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux quiet splash"
Needs Raring & new kernel
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1175029](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1175029)

---

### Post by guillerd on 2013-07-18
Hey, that is good news.
 I have not tested that yet in my computer, but I will.
Were you able to install and work fine with those options?

---

### Post by guillerd on 2013-07-18
Yes

That worked for me to. I just want to perform some more testing before installing.
Thanks for your help!

Boot options:

acpi_osi=Linux acpi_backlight=vendor

---

### Post by leespa on 2013-07-20
Folks - any help would be appreciated.

Have a new Haswell laptop:  i7-4700MQ with Nvidia GT740M, etc...full details here: [http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)

I can't get past the initial GRUB loader screen off any LiveCD's recently tried...at a standstill now.

I can work with the Nvidia binary drivers, futz with different Intel drivers, etc IF I can get to the stage where I can even boot the damn thing.  Any and all hints would be much appreciated.

---

### Post by Sixdown on 2013-08-12
Want to confirm that acpi_osi=Linux acpi_backlight=vendor as boot options worked perfectly for me.  But Ubuntu still does not always boot up correctly and I often need to force restart.  Also, I cannot get the keyboard brightness keys to function.

---

### Post by leespa on 2013-08-13
Running 13.10 on a Toshiba Satellite P50 with i7-4700MQ HD4600, etc.

All the backlights, dimming, sound, video, etc work perfectly.

------------------------------

The problems I was having is unrelated to boot options...I had to disable integrated NIC or laptop ignored USB as a boot device. Once installed I re-enabled NIC and everything works.

---

### Post by ke7kto on 2013-08-30
I'm a relatively new linux user (abt 1 year), and I'm looking at getting this laptop. It looks like a great deal for the price, but I saw some bad reviews for linux compatibility, so I wanted to clarify:

Are there any problems people haven't been able to fix with this? Are you satisfied with how the computer runs?

---

### Post by oldfred on 2013-08-30
Notice that leespa said he is running 13.10. Normally we do not recommend the next version unless you really are a tester, bit more knowledgeable and willing to work around crashes as the software is not final.

But the very new hardware just about has to have the very newest versions of the kernel and Intel or nVidia drivers. So it is up to you, possible better hardware support but possible breakage as the software is not final.

---

### Post by leespa on 2013-08-30
13.10 has worked very well hw-wise, but yes there are crashes of applets, etc but main system very stable.

I managed to get VMWare 9.x working with some patches if that's important to you.

---

### Post by guillerd on 2013-12-12
Hi Guys. I know this thread is a little old now.

I have been running linux on this computer for 6 month now. Even removed completely windows8 and run some virtual Window 7 machines with VirtualBox (of course I made a system image just in case I need Windows8 original again).
The only thing I have not been able to make work entirely are some of the Fn keys:
Brightness
Video mode switch
Touchpad on/off
Wifi on/off
(All the rest work fine: Media play, next, previous, vol up, vol down, mute)

Can somebody point me in the right direction on how to get this keys working?

Thanks!

---

### Post by guillerd on 2013-12-12
By the way, acpi_osi=Linux acpi_backlight=vendor in the kernel commands at boot was the solution to get this laptop going with Linux.
However, I still would like to know if that is something that can somehow be "fixed". I mean to make those commands unnecessary in future ubuntu releases (Or even other distros), is there something that I can report somewhere or modifications to make and submit?

---

### Post by oldfred on 2013-12-12
I do not know specific settings. But Intel & kernel developers are still adding updates for the very new systems.

If you have another 20GB on hard drive, you might try installing the 14.04 version as dual boot. I would consider that only for testing as it may crash as any time and somethings may not work at any time. They now say they are trying to keep the daily download version working where in the past one update might cause entire system not to boot. But no guarantees that everything works or works well.
I just zsync ISO and install ISO using grub's loopmount. If it boots I run updates inside it, but periodically  run a new zsync and reinstall.

I create an iso folder in /home and change to that. And run this. You can download entire ISO first time or just run this. And every time after it will recreate ISO just by downloading changes since last download.
 zsync [http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync)
I cannot seem to save above as one text string.  Note that the http is shortened on display with .. and you need to have to full path. just copying will not work. click on link and copy that in front of the zync to have full string.
And with .zync on end of path it will not directly download correctly. Just click on it to see full name.

Then I add a boot entry to directly boot the ISO in grub. And install to another partition that I already have created using Something else or manual install.
       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by guillerd on 2013-12-12
Thanks for the quick reply!.

I will give that a try and let you know the results.

---

### Post by oldfred on 2013-12-12
This is my grub entry.

```
menuentry "Ubuntu 14.04 Trusty ISO 64bit" {
    set isofile="/iso/trusty-desktop-amd64.iso"
    insmod part_gpt
    loopback loop ([COLOR=#ff0000]hd2,4[/COLOR])$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile [COLOR=#ff0000]nomodeset[/COLOR]
    initrd (loop)/casper/initrd.lz
}

```

I have several drives, and I boot from hd2,4 or second drive, 4th partition, your may be hd0,Y where Y is partition with your iso files (not test install partition).
I also have nVidia and ISO will not boot without nomodeset, you may need your boot options or can test what you need by editing this boot stanza with e when booting.
I always install grub to sda which is my old XP install, so I do not care what boot loader is in that drive. With your UEFI, it may overwrite the grub in your efi partition? I might backup efi first just to be sure you can boot.

---

### Post by electrocoder on 2014-03-05
[COLOR=#000000]I had somewhat the same problem with an Intel HD4000 + NVidia GT650M combo (and Kubuntu 13.04). I also got a black screen. For me the solution was to just increase the screen brightness using <Fn> + <Arrow right>. You might have a similar keyboard combination for setting the brightness. You could try that?[/COLOR]

i solve problem :D thanks.

---

### Post by Drew_B._Roberts on 2014-04-23
[SIZE=3][SIZE=1]I bought my Toshiba Satellite P75-A7200, cpu i7-4700MQ, HD HGST HTS541075A9 750GB, RAM 8GB, with Windows 8 preinstalled in Dec. 2013.  
I used the Win 8 OS for about a week and did not like it.  Enough said, except I am a big fan of Linux and UBUNTU!  
I completely removed Windows 8  (or at least I tried to) using GParted.
I don't like the EUFI.  Prefer standard BIOS, but we all have to learn new things when new technology brings us changes.
I still have problems wih some of the function keys, and cannot turn off the Touch Pad, turn on the Camera, or the built-in Flash drive port.
I'm also not sure how to use this laptop's 4 USB 3.0 ports at their full USB 3.0 capability.  (Disk Utility shows that a WD 1 TB HDD in a Themaltake Max 5 G external enclosure with a SATA to USB 3.0 plugin to this Toshiba reports it's only doing Read only Bench mark speeds via USB 1.0.  So, may be Disk Utility doesn't work, or this laptop needs Win 8 or updated Bios/EUFI version to recognise/activate/use USB 3.0?)
Yes, I will reread   [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)  
I should add that I've ben using Linux, starting with Ubuntu 6.0, and tried other Linux Live Distributions, and dual-booted or had several OS with GRUB, but loaded Linux Mint 13 Maya (MATE) 64-bit on this Toshiba P75-A7200 with no other problems.  I downloaded the ISO image file and burned the image to a DVD-R from which I booted it Live first.
I still use UBUNTU in this way.  ;-))
Thanks...  Glad to be here and hope I didn't break any Forum rules?
[/SIZE][/SIZE]

---

