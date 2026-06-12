---
title: "Ubuntu won't load on MSI A6000 (MS1683)"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by rhardie on 2010-10-25
I've attempted to load Ubuntu 10.04 and 10.10 as well as Kubuntu 10.10 on my MSI A6000 laptop (For dual boot).

The OS has failed to load 100% of the time.  I've even attempted the USB option and it fails to load.

The 10.04 version will hang up and give me a white box.  The 10.10 version just get's quiet on me after loading the pretty purple (Ubuntu) or blue (Kubuntu) screen.

The optical drive is no longer accessed and there is no indication that hard drive is being accessed like in a normal load.

I believe I read somewhere that this was a graphic card issue, but I'm not sure.  It could be that the system is waiting for a keyboard input, but I don't know that because I don't see the prompt.

I would appreciate any suggestions.

System configuration is:
Laptop
Pentium dual core T4500
32 Bit
3 GB RAM
nvidia GeForce 8200m G

The HD is partitioned as follows:

OS Install C: 172 GB with 56.2 GB free space
Data D: 3 GB with 1.52 GB free space (this stores the Windows 7 recovery data

---

### Post by mörgæs on 2010-10-26
Have you tried adding boot parameters, for example nomodeset?

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by SuperKumario64 on 2010-11-14
Hello, I have the same Laptop. MSI A6000 MS-1683

I have had ubuntu working in the past, however when I recently tried to reformat ubuntu would freeze at random points, I did change the boot settings and was able to install ubuntu however once booting into the hard drive it would freeze. With the latest version of ubuntu there is a couple error messages that appear during the splash screen where it normally freezes for me. Some times it will boot further and freeze durring installation. Here are the error messages I experience:

Well of course this time it didnt show the error messages. I am going to go ahead and attempt to install ubuntu, however I feel it will have an error with my recent experiences trying to install ubuntu. The weird part is that ubuntu doesn't seem to freeze at the same spot, it will hang up at some random unreproducible time.

I have been looking into getting a HP computer as my experience with ubuntu's comparability with HP seems to be very good. Any comments?

Kumar

PS: I am slightly techy, but not much more then a few college programming courses including upper divs. I have used ubuntu since 7.04 as my primary desktop, and am having to use windows now on my new <6month old laptop.... SOS

[This is the HP laptop I have been drooling over]("http://http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Category&v1=Everyday+computing&series_name=G42t_series&jumpid=in_R329_prodexp/hhoslp/psg/notebooks/Everyday_computing/G42t_series")

---

### Post by mörgæs on 2010-11-15
When you write 'Ubuntu', I assume it means the regular version of 10.10. Have you tried the alternate one and / or 10.04?

---

### Post by SuperKumario64 on 2010-11-16
> **mörgæs said:**
> When you write 'Ubuntu', I assume it means the regular version of 10.10. Have you tried the alternate one and / or 10.04?

I have tried alternative 10.04. I got it to install completely however whenever I booted from the hard drive it would freeze.


I have only tried regular 10.10 and it did not work, school is keeping me busy. This next week I will have time to play with 10.10, and report my finding with detail.

---

### Post by SuperKumario64 on 2010-11-18
Hello, 

I have just finished administering two tests on my MSI A6000 (Ms1683) 

1) I have tried to boot and install ubuntu 10.10 from usb, this usb drive is known to boot and install on other pcs. It freezes during installation or gives error msg during splash screen and freezes.

here is the error msg when it freezes at the splash screen. interestingly I can here the sound it makes when the login screen should appear:

*PulseAudio configured for per-user sessions: Error - PBF System register not ready. Saned disabled; edit /etc/default/sanedy_vend: Error-Indirect registry access failed: offset = 0x00007010 , value 0x192629f9
[   18.861366] phy0 -> rt2800pci_load_firmware: Error-PBF system register not ready.
[   18.861894] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0x192629f9 speech-dispatcher disabled: edit /etc/default/speech-dispatcher

Sorry for the bad formatting, I wrote it down on a note card. However, The text came up very weirdly on the splash screen starting right after the 4 dots.



2) Burned Ubuntu alternate to a cd, and it installed completely from the newly burned cd. Once I boot up from the hard drive it freezes at the splash screen before the login page.   


I hope this information can help someone diagnose my problems, and those of the MSI A6000 ms1683 .

best,
Kumar

---

### Post by mörgæs on 2010-11-19
Again, have you tried the boot parameters shown in the first post?

---

### Post by SuperKumario64 on 2010-11-20
> **mörgæs said:**
> Again, have you tried the boot parameters shown in the first post?
 
I was unable to set boot parameters in the live-cd, however the alternate cd has the option to set them. The problem is that the alternate cd will install completely however when it boots it freezes. 
 
Is there a way to set the boot parameters on the live-cd or on the install after the alternate cd has installed on the hard drive. will setting the boot parameters on the alternate cd change anything even though it installs completely?

---

### Post by mörgæs on 2010-11-20
Setting boot parameters on the CD does not transfer to the system being installed. You have to set the parameters as described here:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by rhardie on 2011-03-29
Thanks for all of the suggestions.  I didn't mean to abandon the thread and appear lacking in gratitude.  I moved to another country back in November (culture shock, etc.) and I'm just now getting settled down to the point that I can attempt to address the issue again.

My Ubuntu skills have gone rusty so I may need to get some Canonical support to see if there is even a possibility of my laptop working.

I enjoy the laptop and it would be sad to not get it up and running on Ubuntu.

By the way, Ubuntu 9.04 loads up just fine...but I want the later versions.  If I upgrade 9.04, then the software/hardware breaks and I have issues similar to this original thread.

Thanks, again everyone.

---

### Post by mörgæs on 2011-03-30
Welcome back :-)

I wouldn't recommend upgrading a 9.04. Go for a fresh install of 10.04 or 10.10. There should be plenty of advice in the posts above, if the install does not work in first attempt.

---

### Post by ericools on 2011-07-08
I am having this same problem.  Can't find a solution anywhere. Turned off everything in the BIOS that could be turned off, tried every setting on F6 on the boot CD now luck.

---

### Post by mörgæs on 2011-07-09
Hi, welcome to the fora.

Please begin with a thorough description of hard- and software, including the versions of *buntu you have tried. 

Can you run a live session?

---

