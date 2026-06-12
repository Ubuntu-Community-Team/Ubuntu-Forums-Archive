---
title: "Can't boot from Ubuntu 11.04 CD - ASUS G51JX 3D"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by joaomaradao on 2011-05-02
So, it all started the first time I wanted to install Ubuntu on my laptop (ASUS G51JX 3D). I downloaded the 10.10 (32-bit) version from Ubuntu website and burnt it to a CD, and when I tried to boot it, after the "loading dots" I got some weird image on my screen, tried it again - same thing.
Since I had a 10.04 CD, I used it, and everything went fine.
Recently, I decided that I wanted to upgrade to 11.04, and so I did. I was afraid that it would fail at some point with the upgrade to 10.10, but it turned out that it only failed on the upgrade from 10.10 to 11.04. I had to boot using the failsafe graphic mode (not sure if it's called like this), uninstall the nvidia drivers, reboot, and back in failsafe graphic mode install the nvidia drivers back.
After that I was able to normally boot into Ubuntu 11.04, but then I noticed something: when I go to the "Additional Drivers" the nvidia one says: "driver is activated but not in use".
I've already tried to reinstall it, but it still says that.
Today I thought: well I can also try to do a clean install of Ubuntu 11.04 since I don't have that much things there to backup... So I downloaded the iso image, burnt it (using PowerISO) and guess what, just like the 10.10 CD, after showing the "loading dots" I got a weird image on my screen.

This is how it looks after booting from the CD and loading:
[http://i53.tinypic.com/6jits4.jpg](http://i53.tinypic.com/6jits4.jpg)
(those color dots you see are really on the screen, they're not noise of the photo)

My laptop specs: [http://www.asus.com/Notebooks/Gaming_Powerhouse/G51Jx_3D/#specifications](http://www.asus.com/Notebooks/Gaming_Powerhouse/G51Jx_3D/#specifications) (from those points that have more than 1 option: 6GB 1333MHz RAM, 640GB, DVD Super Multi)

What do you think I should do? Reinstalling Ubuntu 10.04 and trying to upgrade to 11.04 is out of question, at least for now, since it would take an eternity do it all again. I'd say I can live with the nvidia driver not being used, since I haven't noticed anything wrong until now, but still... it's always better when everything seems to be working properly, isn't it? :roll:

Sorry for this BIG wall of text, and thanks ;-)

---

### Post by mik112 on 2011-05-04
Same problem here... old Znote machine

---

### Post by Frantumn on 2012-04-18
OMG, same problem, same screen, ever since 10.10

I've even had the checkerd screen show a fragmented image of my windows environment! What the heck?! It makes me sad because I haven't been able to use Ubuntu since 10.04. I've tried 32, and 64 bit, and I've tried multiple downloads of the ISO.

I have an Asus G51Jx (non 3D)

I should mention, if I try to update from a 10.04 installation, it freezes during installation, and I get a corrupt distro that won't boot. (I've tried this way more than once.) Unfortunately I don't remember exactly where it freezes.

---

### Post by oldfred on 2012-04-18
I recent have seen different users post these. So check BIOS.

Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.

Also video mode issues often need nomodeset:
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Frantumn on 2012-04-24
> **oldfred said:**
> I recent have seen different users post these. So check BIOS.

Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.

Also video mode issues often need nomodeset:
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I've updated my Asus G51Jx BIOS to the latest version available on the Asus site. This didn't fix my problem. I looked for the options you spoke of but have nothing even remotely similar in my BIOS menus. The options are very limited on my machine.

---

