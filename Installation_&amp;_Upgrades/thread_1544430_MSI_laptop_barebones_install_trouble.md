---
title: "MSI laptop barebones install trouble"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by Stefan Kuzminski on 2010-08-02
I have a brand new MSI VR705 laptop ( 17" screen w/Nividia chipset ). I thought it would be a bargain, but I am having big trouble with the 10.04 Ubuntu install.  The installer freezes consistently on the first or second screen, just a grey background of the dialog box on the Ubuntu default desktop.  

I tried editing the boot line to remove the 'no splash' qualifier but to no avail.  Debian installs fine on the machine, so the hardware is functioning, but I need Ubuntu..

Any suggestions would be greatly appreciated, I have been stuck on this for days..

thanks,
Stefan

---

### Post by snowpine on 2010-08-02
Does the Live CD work? Can you boot to the Ubuntu desktop "with no change to your computer"?

Have you checked the CD for errors? Run a memtest to check your RAM?

Have you read the Nvidia documentation on the Ubuntu website? 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

If that's over your head, here's another how-to: [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by Stefan Kuzminski on 2010-08-02
I cannot live boot into Ubuntu at all ( this is from a USB sick ) it hits the same freeze as if I was trying to install.  

I validated that I can use this USB stick to install other machines with Ubuntu so it's not the USB stick.

I use the Nvidia drivers on hardware so that where I am planning to wind up, but cannot get the past this screen freeze.

thanks,
Stefan

---

### Post by snowpine on 2010-08-02
Assuming you have checked the "CD" (the USB) for errors and run a memtest, it may just be that Debian has better support for your hardware. I am typing this from Debian now so you know my preference. :)

---

### Post by Stefan Kuzminski on 2010-08-02
Ah..  Interestingly when I boot the laptop in Debian, there is no external monitor support, the external monitor is dead.  BUT, when I *try* to boot Ubuntu, the external monitor comes right up and looks fine.  So my thinking is that Debian has some older 'safer' driver that does not drive the external monitor and Ubuntu does better in supporting the external monitor but bombs out for some other reason.  Maybe I should try the text install..

S

---

### Post by confused57 on 2010-08-02
You might check out the live cd nvidia options posted by oldfred:
[http://ubuntuforums.org/showpost.php?p=9586925&postcount=7](http://ubuntuforums.org/showpost.php?p=9586925&postcount=7)

---

### Post by snowpine on 2010-08-02
> **Stefan Kuzminski said:**
> Ah..  Interestingly when I boot the laptop in Debian, there is no external monitor support, the external monitor is dead.  BUT, when I *try* to boot Ubuntu, the external monitor comes right up and looks fine.  So my thinking is that Debian has some older 'safer' driver that does not drive the external monitor and Ubuntu does better in supporting the external monitor but bombs out for some other reason.  Maybe I should try the text install..

S

Debian uses older software that is very well-tested and known to be stable. If you are looking for a comparable experience with Ubuntu, you might give 8.04 Hardy Heron a test-drive (keeping in mind however support for 8.04 ends in April).

---

### Post by linux18 on 2010-08-02
you could try my distro (see sig) it's specially formulated to install faster than the text installer cli option of the alternate install cds. just install, plug in an ethernet cable, and grab a desktop environment (sudo apt-get install lubuntu-desktop  is my preference)

---

### Post by Stefan Kuzminski on 2010-08-03
I worked around this issue, here are some notes for anyone else who has the same problem.

I used the alternate installation .iso to install Ubuntu. 

Then I booted the machine into recovery mode ( hold down shift on grub boot and follow menus to a root prompt ) and disabled the nouveau drivers as per these instructions ( thanks above ).

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I then booted into normal Ubuntu, ran the update manager and applied all updates, switched to the proprietary Nvidida drivers through the System->Hardware gui and I was able to configure the external monitor through the Administration->Nvidia gui.  I had to save the xorg.conf manually ( copied from preview ) as it gives a 'failed to parse' error.

S

---

