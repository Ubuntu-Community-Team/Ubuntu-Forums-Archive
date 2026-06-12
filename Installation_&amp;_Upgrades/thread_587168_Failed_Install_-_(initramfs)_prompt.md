---
title: "Failed Install - (initramfs) prompt"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by Her Ghost on 2007-10-22
I am currently running with Kubuntu 7.04 (64bit) but want to change to 32bit because 64bit is just too much hassle :)

Anyway, I tried to install Kubuntu 7.10 (32bit) and the install halted with this prompt:

```

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7)
Built-in shell (ash)
Enter 'help' for a list of built in commands
(initramfs)_

```

so I tried again, removing the silent and splash switches.  the line:

```

end_request: I/O error, dev fd0, sector 0

```

kept appearing.  so I disabled the (unused) floppy in the bios and tried again.  Now the install appears to stop even earlier (if the line numbers are % markers, it stops at about 80% as opposed to 92%)  (anyone know of a way of outputting this entire list as it runs so that I could post it?)

I have run the memtest+ and it passed fine
I have checked the md5 checksum on the disc and this worked fine

I had similar problems trying to install the 32bit version of 7.04 that I could never resolve.

My system spec is:
AMD64 3200+
nVidia 7600GT 256mb
512mb ram

(I have a dual boot set up with XP, that is working fine.  The currently installed 64bit version of Kubuntu 7.04 is also currently installed and working fine - apart from it being 64bit and not 32 bit:) )

Any help/suggestions would be gratefully appreciated....particularly since my Norton AV subscription runs out in 5 days and I was SERIOUSLY hoping to be able to say good riddance! :D

---

### Post by Her Ghost on 2007-10-23
any suggestions for this, please?

---

### Post by pm124493 on 2007-10-23
I am having the same problem. Install starts fine, but eventually drops to initramfs. This happens with Ubuntu or Kubuntu x64 iso. 
ECS-P965T-A, bios v1.0k (latest)
E2180, I GB Mem, 300GB SATAII HDD, 6600GT 256MB, IDE CDROM.
It does not matter if I put the on board SATA in AHCI+IDE or IDE mode.
Memtest and extensive HD diagnostics show no problem. There is the issue with sometimes on reboot, Kubuntu will not boot, fails with ata errors. Have to power down for 1 minute before it will boot. This is a known unresolved issue on the internet with some SATA MB and Linux.

Note: My other system has Gigabyte GA-965P-S3 MB and It works fine in SATA ACHI mode and installed Ubuntu x64 iso without any problems. "I know some of you folks will say ECS is not a very good MB vendor and I will agree."

---

### Post by Her Ghost on 2007-10-24
yet more:

I re-enabled the floppy drive to try the suggestion of running the install with a disk in the drive.

Long story short, still no joy, but the messages that might mean something to someone are:

Part way through the install when the floppy starts being accessed frantically (somewhere around lines 94-103):

```

buffer I/O error on device hdc, sector 0

```

and then, seems to get stuck looping the following 2 output lines until line 204:

```

EXT3-fs: mounted file system with ordered data mode
kjournald starting.  Commit interval 5 seconds

```

at which point I get back to the familiar (initramfs)_ prompt

Does this get me any closer to running kubuntu??

---

### Post by kingwalterii on 2007-10-28
I am seeing this too, 7.10 amd64.  Did you figure it out?

---

### Post by chillifrost on 2007-10-30
Hi,

I am installing ubuntu 7.10 i386 Desktop Edition on a dual processor dual hard disk Xeon system. I am getting the initramfs prompt too during install. And I don't know what I should do to have it proceed from there. 

I used exactly the same CD to install on AMD64 machine earlier, and that worked fine: I never saw the initramfs prompt then.

Help would be appreciated.

Thanks,
Chill.

---

### Post by kingwalterii on 2007-10-30
I dont know if it really applies, but i copied the cd to another partition and booted to that.  I forgot to copy the .disk directory to the drive.  Once I copied that it worked

---

### Post by chillifrost on 2007-10-31
Hi there,

I looked up what initramfs does here:[http://linuxdevices.com/articles/AT4017834659.html](http://linuxdevices.com/articles/AT4017834659.html)

Then I poked around with commands in the initramfs shell. I saw that the directory called 'cdrom' in the OS ubuntu install booted into was empty. So I figured that it wasn't finding the "root". So the next time I booted from the Live CD, I specified an additional boot option (by pressing F6 when the ubuntu install menu comes up; each item in the install menu has a different set of options. You want to add in the options line for the install option) root=/dev/cdrom and hit install.  

Viola!

I am writing from my newly installed Ubuntu. Hope this helps someone.

Chill.

---

### Post by tgcUbuntu on 2007-10-31
> **chillifrost said:**
> Hi there,

I looked up what initramfs does here:[http://linuxdevices.com/articles/AT4017834659.html](http://linuxdevices.com/articles/AT4017834659.html)

Then I poked around with commands in the initramfs shell. I saw that the directory called 'cdrom' in the OS ubuntu install booted into was empty. So I figured that it wasn't finding the "root". So the next time I booted from the Live CD, I specified an additional boot option (by pressing F6 when the ubuntu install menu comes up; each item in the install menu has a different set of options. You want to add in the options line for the install option) root=/dev/cdrom and hit install.  

Viola!

I am writing from my newly installed Ubuntu. Hope this helps someone.

Chill.

I´ll have to try this out. On my system I got dumped into BusyBox with the initramfs prompt. I ended up working around the problem by using the old kernel(2.6.20-16-generic) to boot into Gutsy. But this causes a problem with my ATI graphics card as the fglrx driver is tied into a certain kernel version. So I´m now using the open source ati driver.

---

### Post by Trizik on 2007-11-02
same exact problem

tried what chillifrost suggested but that did not help

---

### Post by Trizik on 2007-11-02
i was able to solve the problem by redownloading the image and burning it to a CD instead of a DVD

maybe the image i burned to the DVD was corrupt or maybe the computer is picky about DVDs...

anyway, try a different mirror and burn it to a CD

---

### Post by Trizik on 2007-11-07
i take that back

booting off the newly burned CD does get me into the windowed livecd, but from there all i can do is move the mouse cursor. double clicking the install icon does nothing except highlight the icon. i can open the visible folder on the desktop, but that's all i can do and it takes a lot of time.

---

### Post by lewdogg on 2008-02-07
I had this problem and fixed it by going into the BIOS before installing, choosing boot from CD, and disabling all other booting options.  When I was ready to boot from the HD, I set the HD as the second boot device, and kept all other boot devices disabled.  This was the only way I could install and run it :)

Hope this helps

---

### Post by nickppv2000 on 2008-03-06
I resolve that problem than I kicked out Sony DVD-ROM and put into the system SONY DVD-RW :). No more changes and everything installed:popcorn:

---

### Post by maheshjagadeesan on 2008-03-09
I had this same problem, and one of the suggestions I saw in the forums - adding a boot parameter "all_generic_ide" - while booting off the LiveCD solved my problem.

---

### Post by napzilla on 2008-05-12
I just ran into this issue again with the 64-bit version of Hardy. I haven't found a solution yet, but a bug report is available ([https://bugs.launchpad.net/ubuntu/+bug/203054](https://bugs.launchpad.net/ubuntu/+bug/203054)). In the report, setting the CD drive to slave and unplugging the other devices on the cable resolved the issue. If I don't find an easier solution, I'll try that and report back.

---

### Post by napzilla on 2008-05-13
I was never able to coerce the CD into working, but I was able to create a USB version of the LiveCD ([https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)). I managed to install the system, now I just need to figure out how to get grub to boot from the Hard Drive instead of looking for the USB drive! ](*,)

---

### Post by chinab0wl on 2008-06-07
hi folks,

i had experienced the same problem as described by the original poster.  i found this thread while googling for an answer.  i figured out how to fix my problem, so i hope this info might be helpful to some of you guys.  it's really kind of silly... but sometimes it's the simple little things that drive you nuts.  

basically, my system has an ide hdd and an ide cdrom.  i only had one ide cable.  there are three connectors on my idea cable (one for the motherboard, one for the master device, and one for the slave device).  the spacing of these connectors on the ide cable is not equal.  for me to use one ide cable to connect both the hdd and cdrom, i have to "invert" (that is... make the ide cable upside down) the ide cable.  

i was able to boot the pc without an issue.  the bios recognized both ide devices and i was able to get the ubuntu cd boot menu, so i thought it's no problem.  but then i kept booting into the initiramfs prompt, which lead me to my google search.  finally, i thought maybe i need to sway out some hardware, so while i had the case open, i thought i would flip the ide cable.  viola.

so yeah, that's what resolved my issue.  i hope this may come in handy for someone out there.  if this post is confusing or doesn't make sense, please let me know and i will do my best to clarify.  good luck folks!


> **Her Ghost said:**
> I am currently running with Kubuntu 7.04 (64bit) but want to change to 32bit because 64bit is just too much hassle :)

Anyway, I tried to install Kubuntu 7.10 (32bit) and the install halted with this prompt:

```

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7)
Built-in shell (ash)
Enter 'help' for a list of built in commands
(initramfs)_

```

so I tried again, removing the silent and splash switches.  the line:

```

end_request: I/O error, dev fd0, sector 0

```

kept appearing.  so I disabled the (unused) floppy in the bios and tried again.  Now the install appears to stop even earlier (if the line numbers are % markers, it stops at about 80% as opposed to 92%)  (anyone know of a way of outputting this entire list as it runs so that I could post it?)

I have run the memtest+ and it passed fine
I have checked the md5 checksum on the disc and this worked fine

I had similar problems trying to install the 32bit version of 7.04 that I could never resolve.

My system spec is:
AMD64 3200+
nVidia 7600GT 256mb
512mb ram

(I have a dual boot set up with XP, that is working fine.  The currently installed 64bit version of Kubuntu 7.04 is also currently installed and working fine - apart from it being 64bit and not 32 bit:) )

Any help/suggestions would be gratefully appreciated....particularly since my Norton AV subscription runs out in 5 days and I was SERIOUSLY hoping to be able to say good riddance! :D

---

### Post by sunzeev on 2008-06-11
hey folks 
i'm new to ubuntu...m using the latest one..8.04 LTS hardy heron 32 bit...i was doin well with it...till  my comp hung up...and i  shut-down it forcefully..on restarting it gave me initramfs promt..what should i do..plz help...plz tell me in algorithmic way and in basic way as i dont knw shell programming much..
thanks in advance

---

### Post by dandaman0061 on 2008-06-18
I kept booting into the busybox initramfs prompt no matter what menu option I tried. The 'all_generic_ide' boot option fixed my problem.

---

### Post by eranu on 2008-06-20
> **maheshjagadeesan said:**
> I had this same problem, and one of the suggestions I saw in the forums - adding a boot parameter "all_generic_ide" - while booting off the LiveCD solved my problem.

This solution seems to be working for me at the moment...installing OK. I have two IDE HDD's.

---

### Post by riversbooks on 2008-06-22
Hi
Please clarify something for me. I am trying the Ubuntu experence from the Live CD. When I boot from the CD, the Ubuntu CD menu appears. I select Install Within Windows and after it runs the install, I received the initramf at a command prompt. I poked around the command line and  found nothing that would take me to the desktop. Please advise how I can get to the Ubuntu desktop.

If at the Ubuntu CD Menu, I select Demo and Install, I can run Ubuntu from the CD and get the Desktop. 

This is my first experience with Linux. I have worked with Windows and DOS since '86. 

Thanks
Rivers

---

