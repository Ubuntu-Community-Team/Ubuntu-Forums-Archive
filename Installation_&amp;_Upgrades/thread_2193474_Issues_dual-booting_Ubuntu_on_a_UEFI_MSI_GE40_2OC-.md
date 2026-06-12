---
title: "Issues dual-booting Ubuntu on a UEFI MSI GE40 2OC-218USK laptop?"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by Tiny Grasshopper on 2013-12-13
So this is a post with two questions. One is about UEFI and one is about nouveau. Details below

[SIZE=6]UEFI[/SIZE]

I have a [GE40 2OC-218USK]("http://www.amazon.com/gp/product/B00F3JQRGO/ref=oh_details_o07_s00_i00?ie=UTF8&psc=1") laptop. I am trying to repartition the hard drive to have it dual boot Ubuntu and Windows 8.

Nothing but endless problems. I've been progressively turning more and more things off and it still won't boot the LiveCD.

I've tried the following scenarios, booting into the Ubuntu 13.10 64-bit LiveCD and the LiveUSB with the following options turned off in this order:

FAIL == Black screen after moving past the bootloader screen, with ANY Linux

[LIST]
[*]Turning off Secure Boot - FAIL
[*]Turning off Secure Boot and Intel Rapid Start Technology - FAIL
[*]Turning off Secure Boot, Intel Rapid Start and Win 8 Fast Startup - FAIL
[*]Switching from UEFI to UEFI with CSM, with all the other previous stuff still off - FAIL
[*]Turning off UEFI and Switching into Legacy Mode - It will boot gParted and Fedora, but still won't boot Ubuntu or Lubuntu. Both *buntus get to the loading screen that says *buntu and has the progress bar made of dots below it and then they just sit there. This is not a tenable option either from what I've read because Windows 8 won't boot in Legacy Mode anyways.
[*]Updated my BIOS to the latest one available on the website and tried every previous step AGAIN - The exact same results :(
[/LIST]
I should say, I installed the Windows 8.1 upgrade prior to attempting any of this.

So it sounds like there are two problems here. The UEFI issue and something else preventing it from loading properly even in Legacy Mode.

And I don't know what the problem is with the Legacy Mode? Perhaps an nVidia issue? Is there a set of boot parameters I can use? The laptop uses a nvidia gfx controller.

I have also heard of a boot manager called reFind. Will this assist me?

Any assistance PLEASE would be appreciated. I haven't had so much problems putting Linux on anything in a long time.

[SIZE=6]Nouveau[/SIZE]

at the moderator's suggestion, that has been split off into another thread here:
[http://ubuntuforums.org/showthread.php?t=2193610](http://ubuntuforums.org/showthread.php?t=2193610)

---

### Post by QIII on 2013-12-13
Hello!

It is much easier for the community to respond to one issue per thread.  Would you please consider editing this post to contain only one issue and starting a new thread regarding the other?

Thanks.

---

### Post by oldfred on 2013-12-13
Another user with similar issues - looks unresolved.

[http://ubuntuforums.org/showthread.php?t=2184191](http://ubuntuforums.org/showthread.php?t=2184191)
[http://ubuntuforums.org/showthread.php?t=2192356](http://ubuntuforums.org/showthread.php?t=2192356)
But this user seems to be running Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2191437](http://ubuntuforums.org/showthread.php?t=2191437)

You may want to try MSI forums.
[http://forum-en.msi.com/](http://forum-en.msi.com/)
       MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)

---

### Post by Tiny Grasshopper on 2013-12-13
@QIII Okay, I'll split off the Nouveau behavior into a different thread.

@oldfred, This person is literally getting the exact same behavior as me, in relation to the Nouveau behavior:
[http://ubuntuforums.org/showthread.php?t=2183578](http://ubuntuforums.org/showthread.php?t=2183578)

---

### Post by oldfred on 2013-12-13
I offered the standard suggestions to that user, not sure I can offer any more. 

You need this as the starting point.
Secure Boot, Intel Rapid Start and Win 8 Fast Startup

If you have Intel SRT you probably need to remove the meta-data from the hard drive. I think it does not matter brand of computer, as it is Intel.
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

Do you know which video chip you boot with. Intel or nVidia? If nVidia then nomodeset works. If Intel there seem to be a variety of settings and some may work.

---

### Post by Tiny Grasshopper on 2013-12-14
Well the only thing that I realised that I'm missing in the list of things to disable is is Intel Smart Response Technology. The reason that I didn't think I had it was that I think it's called Intel Rapid Storage Technology in Windows and SpeedStep in the BIOS.

I turned off SpeedStep and set other related setting to from RAID to AHCI and I booted into Ubuntu 12.04LTS in legacy mode and tried to run the commands. They both said that there was no raid.

That didn't help though. It still put up the black blank screen booting a LiveCD in UEFI


As for the gfx, it's an nvidia chip. I'll look into the nomodeset option. Fortunately I tried the daily image of Trusty and it didn't exhibit that behavior, so the problem should go away at some point unlike the UEFI thing.

---

### Post by Tiny Grasshopper on 2013-12-14
sorry, this was a duplicate post.

---

### Post by oldfred on 2013-12-14
Some others with Haswell also had to turn this off to install. But I think that stops networking.
User did not want hard wired Ethernet so he left it off.

       Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

