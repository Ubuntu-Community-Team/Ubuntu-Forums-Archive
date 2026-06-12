---
title: "Problems installing 10.04"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by Motjida on 2010-04-29
Hi all,

I hope you can help me out here. I'm new to the whole Linux business, and I'm trying to install the lastest and greatest Ubuntu on my HP dc7900 SFF PC.

When i first boot from the CD there are no problems, it boots into LiveCD mode and I can see the desktop and all the icons just fine.

I click Install Ubuntu 10.04 LTE and fire through the 7 steps and the installation begins. A few minutes later it's all done and prompts me to reboot. Once the "Click Enter to reboot" appears, I eject the CD, close the tray and press Enter.

Now here's the odd part.

After a second or two i get a black-blue screen with a _ flickering in the top left corner. From my experience with the install on a VM, it should very quickly continue past this step and boot into Ubuntu, but nothing happens... It just stays on the black-blue screen flickering the damn _ until I give up and close it down.

Any help is appreciated and if you need any additional information, let me know.

I've tried both the x86 and the amd64 install... same problem with both.
Also it's the Desktop install, and it's NOT a dual boot system.

Thanks in advance :)

/Mot

---

### Post by drreed on 2010-04-29
> **Motjida said:**
> Hi all,


After a second or two i get a black-blue screen with a _ flickering in the top left corner. From my experience with the install on a VM, it should very quickly continue past this step and boot into Ubuntu, but nothing happens... It just stays on the black-blue screen flickering the damn _ until I give up and close it down.

Any help is appreciated and if you need any additional information, let me know.

I've tried both the x86 and the amd64 install... same problem with both.

Thanks in advance :)

/Mot

I have a similar problem, but I thought mine was due to a failing dvd drive. (IO errors generated first) I noticed a couple other posts about beta not shutting down/rebooting normally.  I'm looking for clues on this too.

---

### Post by infamous-online on 2010-04-29
I had this strange error also, but I simply tried a re-install and it worked. I know it's not that simple for everybody but in my case it worked. What video card do you have?

---

### Post by infamous-online on 2010-04-29
> **drreed said:**
> I have a similar problem, but I thought mine was due to a failing dvd drive. (IO errors generated first) I noticed a couple other posts about beta not shutting down/rebooting normally.  I'm looking for clues on this too.

I got the I/O error twice when I tried installing it but I waited about 10 mins on the second time my box did that and turned it off. When I turned it back on, Ubuntu 10 worked just fine, I wish I knew what caused that issue in the first place. So try a fresh re-install and see if that helps.

---

### Post by Motjida on 2010-04-29
> **infamous-online said:**
> I had this strange error also, but I simply tried a re-install and it worked. I know it's not that simple for everybody but in my case it worked. What video card do you have?

The video card is just a Intel Graphics Media Accelerator 4500 integrated graphics.

Weird thing is, everything works PERFECT from LiveCD, install is smooth, no errors, no nothing. The minute I reboot after the install, it's just dead.

Also, I tried 2 reinstalls on x86 ad amd64, same same.

---

### Post by a5an0 on 2010-04-29
Two things come to mind:

1) Is your computer set to boot off the hard drive (through the bios)?

2) When you installed Ubuntu, did you install GRUB, the bootloader? If you didn't, or are unsure, you might just want to reinstall, and make sure grub gets in there

Good luck!

---

### Post by Motjida on 2010-04-29
> **a5an0 said:**
> Two things come to mind:

1) Is your computer set to boot off the hard drive (through the bios)?

2) When you installed Ubuntu, did you install GRUB, the bootloader? If you didn't, or are unsure, you might just want to reinstall, and make sure grub gets in there

Good luck!

1. Computer is set to boot from HDD
2. I know GRUB is the bootloader, but I saw no mention of it during the install. Do I need to do some magic to get it to install apart from doing a normal installation?

Thanks for the help so far :)

/Mot

---

### Post by SgtPepperKSU on 2010-04-29
Regarding the I/O Errors at the end of the install, be sure to read the [release notes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#I/O%20error%20after%20CD%20is%20ejected%20at%20end%20of%20install) (it's just cosmetic; if you would've hit enter, the system would have rebooted properly).

---

### Post by infamous-online on 2010-04-29
> **SgtPepperKSU said:**
> Regarding the I/O Errors at the end of the install, be sure to read the [release notes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#I/O%20error%20after%20CD%20is%20ejected%20at%20end%20of%20install) (it's just cosmetic; if you would've hit enter, the system would have rebooted properly).

Perhaps this should be a sticky message, because I simply just turned off my box and things worked properly. However I feel this should be put as a sticky for others who run across this message.

---

### Post by drreed on 2010-04-29
> **SgtPepperKSU said:**
> Regarding the I/O Errors at the end of the install, be sure to read the [release notes]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#I/O%20error%20after%20CD%20is%20ejected%20at%20end%20of%20install") (it's just cosmetic; if you would've hit enter, the system would have rebooted properly).

Thanks, I'm going to buy another drive tonight from newegg, so some of my (computer related) weirdness should go away.

---

### Post by drreed on 2010-04-29
> **Motjida said:**
> 1. Computer is set to boot from HDD
2. I know GRUB is the bootloader, but I saw no mention of it during the install. Do I need to do some magic to get it to install apart from doing a normal installation?

Thanks for the help so far :)

/Mot

The boot loader is "under" a little button labeled "Advanced" on the lower right hand side of the same screen with the summary of all the stuff it's about to do, and that comes up right before the real install begins.

The default appears to be to install grub.

I'm not sure how it chooses the default drive to install it too, but I think it chooses the drive you installed to. In my case, I think it said "/dev/sdb", and I didn't need it there, and didn't want it anyway. I unchecked the install grub option and then booted my other distro and ran update-grub from there. I've had bad experiences letting another distro overwrite the grub record installed by another existing distro. (It was probably my stupidity, but I don't want to revisit that day any time soon)

---

### Post by daqron on 2010-04-29
> **SgtPepperKSU said:**
> Regarding the I/O Errors at the end of the install, be sure to read the [release notes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#I/O%20error%20after%20CD%20is%20ejected%20at%20end%20of%20install) (it's just cosmetic; if you would've hit enter, the system would have rebooted properly).

I did hit enter; the CD ejected and the system rebooted. When it came back up, I got the flashing underscore in the top left corner of the screen. I tried turning it off and back on several times. Attempting a reinstall now.

**Edit:**
As with others, my problem turned out to be grub being installed in the wrong place. If you're installing on a system with multiple hard drives/partitions, make sure you follow drreed's advice above and select the right drive in the Advanced options.

Time to go break something else now ...

Cheers!

---

### Post by Motjida on 2010-04-30
Thanks for the replies so far.

I have only one HDD and it's just one big partition, 
so I doubt GRUB would install itself anywhere else.

However, I did fail to mention that I did the install from a USB stick. When i read my OP, it reads like I'm using a CD when I'm actually not. Could that be part of the issue?

Cheers

/Mot

---

### Post by Motjida on 2010-04-30
By the way, I forgot to mention.

When I install 10.04 through a VM like VirtualBox, first thing I see is the language selector with the option to boot into LiveCD or and starting the install.

When I plug in the USB stick and boot up my empty PC, it boots directly into LiveCD and I have to double click the "Install Ubuntu 10.04 LTS" icon for the install to proceed. Why is there a difference?

Cheers

/Mot

---

### Post by Motjida on 2010-04-30
O M G


You can call off the hounds now, I think I got it!

When I installed using the USB stick, I failed to notice that ubuntu selected the USB stick to install to, so obv. it can't boot after I remove the USB post installation.

I'm such an idiot, will reinstall now and make sure that I select the right drive during install. :lolflag:

Cheers for the help guys, I hope my solution can end some of the similar problems others are having :)

/Mot

---

### Post by manfromthezoo on 2010-04-30
Guys, I was having the exact same problem as you on the DC7900. Tried with desktop and server i386 and amd64 versions, same buggerance.

Think I found the problem while running the installer again. When you get to the section regarding the final install options, press the 'Advanced' button to check the grub config. I found mine was pointing at the USB stick I was installing from as the place to boot from. In my case, it was set to boot from /dev/sdb1 (the USB drive).

I made sure to change it to my hard disk (dev/sdb in the drop-down list), and voila. That worked on re-boot. Maybe something is dodgy with the installer that defaults grub to the install volume, I dunno.

If you've already installed I'd wager there's no need to install the whole system again - just boot from a LiveCD or LiveUSB and change the appropriate line in the grub conf.

---

### Post by Motjida on 2010-04-30
> **manfromthezoo said:**
> Guys, I was having the exact same problem as you on the DC7900. Tried with desktop and server i386 and amd64 versions, same buggerance.

Think I found the problem while running the installer again. When you get to the section regarding the final install options, press the 'Advanced' button to check the grub config. I found mine was pointing at the USB stick I was installing from as the place to boot from. In my case, it was set to boot from /dev/sdb1 (the USB drive).

I made sure to change it to my hard disk (dev/sdb in the drop-down list), and voila. That worked on re-boot. Maybe something is dodgy with the installer that defaults grub to the install volume, I dunno.

If you've already installed I'd wager there's no need to install the whole system again - just boot from a LiveCD or LiveUSB and change the appropriate line in the grub conf.

You are completely right of course, it installed correctly onto the HDD, NOT the USB, however it DID install the GRUB onto the USB.

Cheers!

---

