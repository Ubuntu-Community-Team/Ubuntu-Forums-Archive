---
title: "Can't Fix Windows 98"
date: 2006-05-15
forum: Installation &amp; Upgrades
---

### Post by bobpur on 2006-05-15
I have an IBM Aptiva E Series 550 with a PIII 500 Mhz cpu, 96 mb RAM, a 17gb Harddrive, a floppy drive, CD-RW, and a DVD-ROM. It had a Windows 98 OS that was so corrupted it would barely boot. I want to make a Ubuntu machine out of it.
1). I made a boot floppy before I trashed the OS. 
2). Could not get machine to accept Ubuntu v5.04 (Hoary) CD. 

Does anyone know how to install Ubuntu in a machine like this? I'm using the older edition because of the amount of RAM that is in this computer. I'm not sure what Hoary requires but Breezy needs 128 mb Ram (right?).

                                          Thanks.

---

### Post by Sef on 2006-05-15
> Does anyone know how to install Ubuntu in a machine like this? I'm using the older edition because of the amount of RAM that is in this computer. I'm not sure what Hoary requires but Breezy needs 128 mb Ram (right?).

I would go with Dapper Xubuntu.  It is a lightweight manager.  It is in beta testing for about another 2 weeks, then it is planned to become stable on 1 June.

---

### Post by bobpur on 2006-05-16
Sef, Thanks for the reply.
The problem I'm having is trying to run the Hoary Install CD. The computer won't boot from it. Trying to use the boot floppy will get the machine going, however; it won't recognize the linux CD. Will Dapper have a way around this? Or, am I missing something here? BTW, I'm a Linux Newby (If you haven't guessed).

---

### Post by aysiu on 2006-05-16
Maybe you burnt it as data instead of as a disk image?

See the first half of this page for more details--it features Dapper Beta, but the same principles apply to any ISO you burn:

[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by confused57 on 2006-05-16
On some older machines, the bios does not support booting from the CD drive,
you'll need to make a boot floppy with SmartBootManager on it:

[https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

You need to download the SBM file and rawrite to the same folder.  Extract the rawrite zip file, double-click on the .exe file, which should guide you in copying the SBM file "as an image" to create a boot floppy.  Boot up the machine with the SBM boot floppy and install CD inserted( set your bios to boot 1st from the floppy drive), SBM will start with a menu to select boot from CD drive.  Highlight boot from CD rom, press "F2" to save, then enter.  May have to repeat a couple of times, I usually get an error message the first time.

You may want to consider Xubuntu, using this guide:

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

Check out this link for "LowMemorySystems" install:

[https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

---

### Post by aysiu on 2006-05-16
I love Xubuntu, and it's wonderful on my old computer, but that has 128 MB of RAM.

96 MB may be a bit slow.

---

### Post by bobpur on 2006-05-16
I was using the CD's that Ubuntu distributes. I did not burn these.
I have been checking out the Xubuntu website. it looks promising. I think I like this better than Hoary.
Thanks for the response. It's appreciated.

---

### Post by Sef on 2006-05-16
> I was using the CD's that Ubuntu distributes. I did not burn these. 

Sometimes the CDs from Ubuntu are bad.  

Can you set the BIOS to boot from the CD-ROM?

---

### Post by bobpur on 2006-05-16
Can you set the BIOS to boot from the CD-ROM?
__________________
No, I can't. This is a machine that was new in 1998. The boot sequense is fixed. Floppy then CD-ROM then harddrive.

                                        Thanks

---

### Post by Sef on 2006-05-16
It should boot from the CD-ROM then.  First it'll check the floppy drive and if it is empty, then it will check the CD-ROM.  Since you can do that, either that is broken or your install disc was bad.

---

### Post by bobpur on 2006-05-16
I tried the CD burner and the DVD-ROM before I reformatted the harddrive and tried to install Ubuntu. They worked. I have also tried installing from the DVD-ROM since they will play CD's too. A website for this computer said I would have to use a Boot Floppy to get an OS back in it. See first post in this thread for specs.
I'm still working on confused57s suggestion but I must be doing something wrong. It hasn't worked either. Probably my fault.

                                           Thanks

---

### Post by Sef on 2006-05-16
> I'm still working on confused57s suggestion but I must be doing something wrong. It hasn't worked either. Probably my fault.

Don't be so quick to blame yourself.  It might be a hardware problem, or just an error on your part. However, an error on your part is not your fault.  It is a learning experience.  The more you have, the more you learn.

---

### Post by confused57 on 2006-05-16
Here's another link for SBM,  I used rawrite; but looks like there's other options to write SBM as an image to a floppy:

[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

I already had WinZip to extract the rawrite.zip in the folder where I downloaded rawrite and SBM.  If you can't find another way to write the image to floppy, you could download and install WinZip(free for 30 day trial); use it to extract rawrite.zip, then uninstall WinZip.  After extracting, double-click on the .exe file, type in the sbm file in the menu window, click write and that should copy sbm as an image to a floppy(format the floppy first).

Do you have the win98 install CD or is win98 still installed on the computer?  You may want to "play" around with setting up a dual-boot, just for a learning experience, since this doesn't appear to be your main computer.  If you haven't completely trashed your win98 OS, there may be a "cab" folder in windows that you can repair win98.  Just some suggestions you may want to consider...once you get it booting from the CD drive.  It took me several tries to get SBM working, I couldn't do it at the time with the DOS instructions.

---

### Post by bobpur on 2006-05-16
I am pleased to announce that with everyones help and my own dogged persistance, I have a functional Ubuntu Hoary Hedgehog machine. It is slower than I'm used to but it's only a 500 Mhz CPU and 96 MB of RAM. I found more memory to get me 256 MBs of RAM. When I get it installed, I'll upgrade. Confused57s tips did the trick. I just had to keep stumbling around each step until I got it right. Sef and Aysiu, thanks for your input it was appreciated. If ther is a downside, my daughter just claimed it for her own. Oh well;)
                                               Thanks again, bobpur

---

### Post by confused57 on 2006-05-16
Good to hear you got it working, I've been there & done that, and persistence pays off.  I have an old machine with pretty much the same specs; but with Breezy installed and using Automatix, it was "usably" fast.  If you have a fast internet connection, you may want to try a "dist-upgrade" to Breezy, or better yet, consider installing Xubuntu Dapper when the final version is released.

You may want to bookmark this link for future reference:

[http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by bobpur on 2006-05-16
Yeah, I got DSl. I'm going to leave it as is for awhile until I get the memory upgraded. My daughter gets extra credit for learning linux in her computer class, so I might wait about a month until she's out of school to change.
My regular Ubuntu machine is a dual boot Breezy / Win Me on an old Compaq. It has the OSs on two different harddrives and works great. That setup and install was effortless. I haven't used it for awhile as I had to set iot aside to make room for other projects.
                                        Thanks Again

---

