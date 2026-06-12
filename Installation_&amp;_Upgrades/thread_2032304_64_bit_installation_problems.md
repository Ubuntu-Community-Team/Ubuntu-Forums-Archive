---
title: "64 bit installation problems"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by Baji P. on 2012-07-23
I am not necessarily looking for a response, I simply want to put the information out there for others. In the past, I have had [several problems using 64 bit ISOs]("http://ubuntuforums.org/showthread.php?t=1561968") on my Dell Optiplex 740 system (with Athlon X2 processor & 4 Gig of ram). Before Ubuntu 10.10, I could not get any previous 64 bit version of ubuntu to install cleanly on it.

[10.10 installed and worked great]("http://ubuntuforums.org/showthread.php?t=1569205") until it reached [End-Of-Life]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions"), at which point I had to look for a new distro. I unsuccessfully tried Ubuntu 12.04 64 bit Desktop and Alternative CDs, I then tried 64-bit Xubuntu and Debian 6.0.5 (Squeeze) CDs. In each case, I either encountered a kernel panic that broke the installation or an Initrd kernel that was so bloated that it would not even boot to a desktop.

After a day and half of trying 8 or 9 different 64 bit ISOs unsuccessfully, I gave up life in the 64-bit world and went back to a 32-bit ISO.

As expected, the installation went fine and the system is running fine, albeit in 32-bit mode.

Clearly there is nothing physically wrong with my hardware, why do 64-bit linux installations have so many issues when almost all of the new systems on the market are 64-bit ?

If I didn't know any better, or if I was a conspiracy theorist, I might have suggested that intel spies are sabotaging 64-bit ISOs.

Thank you in advance for any insights.

---

### Post by darkod on 2012-07-23
I am using the 64bit version since 9.10 was out because I have 6GB of ram that I want to be used in full. I am doing clean installs instead of upgrades, but I haven't noticed any problem with the 64bit version in each release between 9.10 and 11.10.

---

### Post by Jimmyfj on 2012-07-23
I've also been running 64 bit Ubuntu systems since 9.10 on several different computers. The one I'm using right now is an Intel Core I7 based HP Pavillion computer with 4 gig RAM and 1 TB hdd and I'm not experiensing any problems. My wifes computer is also running Ubuntu 12.04 LTS without any errors so it seems odd that you can't make it install.

---

### Post by efflandt on 2012-07-23
What video do you have?  If you have nvidia, you may need to use **nomodeset** to boot install iso (or at least I did for PC in my sig).  Although, I did not need an parameters once installed.

My early Athlon64 3200+ (2 GHz single core from 2004) runs 64-bit 10.04 which I have not updated yet.  But it boots normal 64-bit 12.04 live/install on USB stick fine with 2 GB RAM and its legacy ATI video (X1300).  It is missing the lahf_lm instruction for true 64-bit flash, but someone made a plugin for that so it would work.  Many years ago it ran 64-bit SuSE.

Strangely I had trouble doing a normal 64-bit 12.04 install to my laptop with 1.66 MHz Intel Core 2 Duo w/2.5 GB RAM, integrated Intel video. It would hang indefinitely (for hours) at 90% of "Installing system" with no errors.  Alternate 64-bit install worked fine.

---

### Post by QIII on 2012-07-23
As with those above, I have been running several 64 bit distros for a long time on 64 bit hardware.

Clearly, something is going wrong for you (and that needs to be addressed) but it would be hasty to generalize everyone else's experience as identical to your own, nor can your one machine be taken as a general indication of hardware compatibility.

---

### Post by Baji P. on 2012-07-24
darkod, Jimmfj & QIII,

I am sorry if you got the impression that I was suggesting that every Ubuntu user out there is having problems similar to my own.

That was not my intent at all. I am glad that you experienced flawless 64 bit installs, as I did with Ubuntu 10.10

Here is what I am saying, I have a vanilla 64 bit Dell machine, my machine ran 64 bit Ubuntu 10.10 without a hitch, 32 bit versions of current Ubuntu & derivatives also work fine.

All I am asking is, and it is in a rhetorical sense, what broke between 10.10 & 12.04 in the 64 bit version ?

efflandt, thank you for your comments, hwinfo says I have an "nVidia GeForce 6150 LE"

---

### Post by piranhadog on 2012-07-24
I am having issue with the 64bit installation, as well; it locks/freezes on the welcome screen, i.e., I cannot click continue.  at first, mouse lags until, after a minute or so, the mouse responds normally yet nothing else responds.  cannot get to console.  memtest passes; disk check, ok.  the freeze happens if trying out or installing.

x58 ftw3 (up2date bios)
6GB ram
raid 0, but tried to install on separate drive
gtx580  
bdr-206



not looking for a response just like initial poster.  back to 32bit, as the struggle to track down whatever burp to then tiptoe through the install, and possibly beyond, is not worth it for my purposes.  replied to thread because he is not alone.


oh yeah, no problem with opensuse-12.1-dvd-x86_64 or linuxmint-13-mate-dvd-64bit installation, same machine.

---

### Post by mastablasta on 2012-07-24
> **Baji P. said:**
>  
efflandt, thank you for your comments, hwinfo says I have an "nVidia GeForce 6150 LE"
so, did you try any of the boot options?

---

### Post by mastablasta on 2012-07-24
> **piranhadog said:**
>  linuxmint-13-mate-dvd-64bit installation, same machine.
mate doesn't use graphics 3d acceleration by default which again brings us to boot options.
 
what happens if you try Xubuntu for example?

---

### Post by Baji P. on 2012-07-24
> **mastablasta said:**
> so, did you try any of the boot options?

I tried expertmode and VGA=???, I don't recall if I used *nomodeset*, I'll try other boot options in a few days when I have time.

But I am swamped at the moment, and need to get caught up.

---

### Post by sinukas on 2012-08-14
I am having this same issue on the following hardware:

asus x58 mobo
intel core i7
samsung sata 1tb hd (x2)
8gb corsair ram
nvidia gtx580

---

### Post by oldfred on 2012-08-14
@sinukas
Best to start your own thread. Your system is a lot different.
 Also is your system UEFI or BIOS? Most new Intel i-series motherboard are both. And nVidia needs nomodeset and/or noapci. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

