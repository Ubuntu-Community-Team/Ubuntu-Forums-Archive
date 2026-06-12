---
title: "Alternate CD Install Menu Flickers Non-Stop"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by Spydrdude on 2009-12-15
Hello,

I am having some difficulty installing Ubuntu 9.10 from the "alternate" iso image.  I have both regular image and alternate but I want to use alternate to turn on full disk encryption from the get go.

The computer I am installing on is an old Gateway Solo 1450 Laptop, rough specs as follows:

Intel® Celeron-T™ CPU -OR- Intel® Pentium® III Processor-M CPU (1.2 Ghz I think)
512 MB SDRAM
Intel 4X AGP graphics core (chipset integrated) 
DISPLAY:

[LIST]
[*]14.1 or 15-inch active matrix (TFT) XGA (LVDS)
[*]Variable backlight brightness
[*]Maximum panel resolution: 1024 x 768
[*]Maximum color depth: 24-bit (16.7 million colors)
[*] 85 Hz maximum refresh rate
[/LIST]
ESS 1988 Allegro PCI audio

 Further specs: [http://support.gateway.com/s/Mobile/Solo_Series/P1450/3501269sp25.shtml](http://support.gateway.com/s/Mobile/Solo_Series/P1450/3501269sp25.shtml)

Now, as to the issue, when I boot the regular cd in live mode I can get to a desktop and see everything and it all seems to work, no problem.  When I put in the alternate CD and choose "Install Ubuntu" the blue/red screens for installing with the text menu flicker so badly I cannot use them (well, I suppose I could, but given I want to specify a lot of my parameters I'd prefer not hurt my eyes if I can avoid it).  The screen also seems sort of twisted when it's like this, kind of like someone is pushing the top left corner in and pulling the bottom right out and squeezing.

Any suggestions would be helpful, I was thinking perhaps there is something I can add to the install command line by hitting F6, but I'm new to this particular problem so I'm not sure what to do.

Thanks so much.

---

### Post by tommcd on 2009-12-15
> **Spydrdude said:**
> 
Intel 4X AGP graphics core (chipset integrated) 

The intel graphics should not be a problem, especially with the alternate CD. Do you know the specific model number of the intel graphics chip that is in the computer?
> **Spydrdude said:**
> 
Now, as to the issue, when I boot the regular cd in live mode I can get to a desktop and see everything and it all seems to work, no problem.  When I put in the alternate CD and choose "Install Ubuntu" the blue/red screens for installing with the text menu flicker so badly I cannot use them ... 
This is most unusual. So the graphics on the live CD are ok; but the alternate CD flickers badly? Is that correct? 
Have you tried running the live CD for a while? Open firefox and browse the web. Open programs and use them, etc. Does all this work on the live CD? 
Are you sure the monitor is not faulty? If the live CD works ok, then I would assume that there is nothing wrong with the monitor. A faulty monitor would be another thing to rule out though.
> **Spydrdude said:**
> 
Any suggestions would be helpful, I was thinking perhaps there is something I can add to the install command line by hitting F6, but I'm new to this particular problem so I'm not sure what to do.

First, lets rule out a bad CD. When you boot the alternate CD, first run the option that says: "check disc for defects". This will take a minute or so to run. If it reports errors, then the CD is bad and you need to burn a new one. If the CD passes, then it is likely ok.
If you are burning the CD from Windows, I would use Iso Recorder or Infra Recorder:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
And be sure to burn the CD at the slowest possible speed.

Assuming the alternate CD is ok, when you boot the alternate CD and come to the menu, hit F6, then hit the Esc key to open the boot command at the bottom of the screen for editing. Hitting the Tab key moves the cursor to the boot line also for editing. See this:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
After the -- at the end of the boot options line, try adding:
```
vga=vesa
```
Then hit enter. This will load the basic vesa driver. Other options you could try, one at a time:
```

vga=771
vga=791
vga=normal

```
You could also try the noapic, nolapic, and acpi=off if nothing else helps. This seems to be a problem with the graphics though.
If you can't get the alternate CD working ok, I would try installing using the live CD if that works. 
Write back if you need more help.

And welcome to the Ubuntu forums!

---

### Post by Spydrdude on 2009-12-15
I'm running the cd-checker now, it does same flickering, etc.  I'm closing the lid and will look when it finishes.  After that I'll post results and I'll try out the 4 boot options you mentioned and report back.

Thank you so much for taking the time to reply, hopefully I can get this going with the encryption, as that was my main goal with the alternate cd.

Edit: I burned it using InfraRecorder in Windows from the ISO file, first disk wouldn't even boot at all, second one does what I described (this is my second alternate disk I've burned).

As for the monitor, I've had this machine for a while and used Ubuntu 7 or 8 a while back, then XP again and then the Network Systems Toolkit linux live cd with hdd install, and I don't recall any video problems like this from those.

---

### Post by Spydrdude on 2009-12-15
CD Check finished it says "The CD Is Valid" with no errors ... moving on to the boot parameters now...

---

### Post by tommcd on 2009-12-15
Ok, write back with the results of the "check CD for defects".

Also please answer:
The live CD runs fine with no flickering or graphics problems? Id that correct?

Are you sure the monitor is not faulty? If the live CD runs ok, then we can assume the monitor is good.

Also try the boot options I suggested, one at a time. Write back with what happens when you try each of them.

---

### Post by Spydrdude on 2009-12-15
We're making progress.  VGA=771 helps, just as you said, no flickering anymore!

vga=vesa (did not work)
vga=771 (works!!!)
vga=791 (haven't tried as the above seems to have fixed the flicker)
vga=normal (haven't tried as the above seems to have fixed the flicker)

I can go through and try the other options later if you folks need them for documentation.

I didn't do further testing on the regular live cd, as I was largely just interested in seeing it get to desktop.  If I continue to have issues I can check that out as well though.

Thanks so much!!

---

### Post by tommcd on 2009-12-15
> **Spydrdude said:**
> We're making progress.  VGA=771 helps, just as you said, no flickering anymore!

vga=771 (works!!!)
vga=791 (haven't tried as the above seems to have fixed the flicker)
vga=normal (haven't tried as the above seems to have fixed the flicker)

Ok, glad we are making progress here.
If booting with **vga=771** works and fixes the flickering problem, then go ahead and install Ubuntu using that boot option.
Hopefully, once you get Ubuntu installed and up and running, the intel graphics should just work fine. If you still have screen flickering on the desktop after you have installed Ubuntu, we can add vga=771 to the kernel line in the grub menu for booting Ubuntu if we need to. 
So go ahead and install Ubuntu using the alternate CD and boot to the desktop and lets see how that goes.
Write back if you need more help.

---

### Post by Spydrdude on 2009-12-16
The install went fine.  I am at the desktop now and writing this from Firefox on the laptop.  Full disk encryption appears to be working as expected so that is a major plus for me. 

Thanks so much for your help with this, I was loathe to go back to an XP install just because of video issues.

There is still a small flicker during the bootup process, after the encryption pass is entered I see the circle with the lines rotating around in it and that is flickering for about 3 seconds, then I see the "UBUNTU" with the light shining down on it and the bar moving from left to right, that flickers for 3 seconds too, then goes off screen and then shows up normal in center screen in color and does not flicker.  Once I'm at the desktop everything seems good, so I'm not too worried about it.

Thanks again!  I'm going to mark this one solved!

I am a bit curious though, what does vga=771 do differently?  Is that just another intel default driver or something?  I love to learn new things about this stuff when I can.

---

### Post by tommcd on 2009-12-17
> **Spydrdude said:**
> 
There is still a small flicker during the bootup process ...
Once I'm at the desktop everything seems good, so I'm not too worried about it.

You can see some flickering during the bootup process. Although the new kernel mode setting (KMS) support for intel and ati drivers in the linux kernel is supposed to provide less flickering. You can read about KMS here:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_ati_kms&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_ati_kms&num=1)
[http://www.workswithu.com/2009/07/15/ubuntu-910-preview-kernel-mode-setting/](http://www.workswithu.com/2009/07/15/ubuntu-910-preview-kernel-mode-setting/)
> **Spydrdude said:**
> 
I am a bit curious though, what does vga=771 do differently?  Is that just another intel default driver or something? 
Setting vga= during the bootup process sets the video resolution for the bootup screen. I don't know a whole lot about the technical details, but you can read a little about the different vga modes you can use in this thread:
[http://www.linuxquestions.org/questions/debian-26/lilo-vga-modes-152575/](http://www.linuxquestions.org/questions/debian-26/lilo-vga-modes-152575/)
That thread deals with lilo, but it also applies to grub.
And more here:
[http://www.pendrivelinux.com/vga-boot-modes-to-set-screen-resolution/](http://www.pendrivelinux.com/vga-boot-modes-to-set-screen-resolution/)

---

