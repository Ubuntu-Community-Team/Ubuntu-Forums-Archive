---
title: "Nvidia 8400GS fails to work with ubuntu"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by xd20 on 2011-04-25
I've tried various versions of ubuntu and they never work on my PC.  Took a while to figure out why, but finally after removing my PCI graphics card (PNY Nvidia GeForce 8400GS 512mb) it worked fine.  

There's an issue with that.. I like my graphics card.  So is there any way to get it to ubuntu to work properly with a Nvidia 8400GS card?

Also, I noticed my linksys PCI card for internet didn't work either.  But that didn't stop ubuntu from working. 

When I have my graphics card in, ubuntu fails to load up period.  Just sort of hangs on the load screen.

---

### Post by walt.smith1960 on 2011-04-25
Can you get any sort of graphical desktop at all? If so, try System -> Administration -> Additional Drivers (in 10.10. 10.04 uses a different name for Additional Drivers).  I'm using an Nvidia 8400GS from BFG (now defunct) which has been no problem with or without proprietary drivers.  If you're installing from a CD, there may be a way to select "no modeset" or "low graphics" or something similar to get a very generic GUI to be able to install Ubuntu and then enable proprietary drivers.  I hope you can get your card working properly.

---

### Post by Frogs Hair on 2011-04-25
I have been using an Galaxy 8400 GS since 9.10 with the recommended proprietary driver from additional drivers . I dual boot and just updated the Windows driver two days ago. I don't know if there is a BFG issue , this is the first I've heard about it.

---

### Post by xd20 on 2011-04-25
I'm currently using a PNY GeForce 8400 GS 512mb card.

I tried Wubi and when I try to load ubuntu I pretty much just get a nonstop loading screen.
I tried regular install and it doesn't even let get to the Ubuntu graphical interface to install.

I tried the alternate installer and I got all the way to where I had to partition the drives.  But it wouldn't let me.  It would always fail to create those special partitions it required, no matter what options I selected for it.

The only way I can install it is if I take out my graphics card.  Once installed I tried searching for the drivers but I couldn't find them, so I assumed the PCI card had to be put back in.  But whenever I do that, Ubuntu fails to load.

So pretty big issue.

Note: Works fine when I boot it with virtualbox and install.  But I suppose that's cause it's just using the drivers supplied by my primary OS.  But I want it as a regular bootup process, not this virtual stuff.  Too laggy.

---

### Post by Frogs Hair on 2011-04-25
It is possible to install drivers from low graphics mode , but can't find a way to get there . Do you get a boot loop when trying to boot in recovery / safe mode. As far as brands go the cards should be pretty much the same , Nvidia uses different companies to build cards and only on the high end models will you see a difference.

---

### Post by xd20 on 2011-04-25
Can't boot into recovery if I can't install it.. Once I install I can, but I have no issues booting it without the card.  Once the card is in.. doesn't work.

---

### Post by Quackers on 2011-04-25
Is this when booting from the live cd/usb?
At the first purple screen (with the stick man at the bottom) press any key. Choose your language then on the next screen press F6. 
Some options will appear bottom right - choose the "nomodeset" option and continue. Does it boot now to a desktop (select "try ubuntu")?

---

### Post by xd20 on 2011-04-25
I've already been through all this in an older thread... [http://ubuntuforums.org/showthread.php?t=1586285](http://ubuntuforums.org/showthread.php?t=1586285)

I've probably tried every possible combination of options you can come up with.

So, what now?

---

### Post by Quackers on 2011-04-25
Going back to basics, have you checked the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Have you checked the cd for errors (if it's getting that far)?
Your other thread has no mention of it.

Is your machine using RAID?

---

### Post by wojox on 2011-04-25
Did you check the BIOS to see if the onboard video was disabled?

---

### Post by xd20 on 2011-04-25
> **Quackers said:**
> Going back to basics, have you checked the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Have you checked the cd for errors (if it's getting that far)?
Your other thread has no mention of it.

Is your machine using RAID?

THE downloaded iso file assumes I downloaded it once.  I've done it with multiple versions thus the natural assumption is that there is no issue with THE iso since there were multiple instances and various types of installation methods.

And how do you tell if your computer is using a RAID system.
Also how is it relevant to the issue with my graphics card?

---

### Post by xd20 on 2011-04-25
> **wojox said:**
> Did you check the BIOS to see if the onboard video was disabled?

I don't think my BIOS settings have that option.  But the onboard is disabled in XP, and there are no drivers installed for it.  Just my regular graphics card.

---

### Post by Quackers on 2011-04-25
For somebody requesting help you seem to have a marked reluctance to answering questions, I see.
I'm aware that you have downloaded several iso's. 
I am not currently aware as to whether all of these iso's were writtin to cd's with the same program and using the same cd drive. If they have all been written with the same drive and none of the cd's have been checked for errors, it may be that the cd drive has a problem. You would not be the first person to have a faulty cd drive and not know it.

---

### Post by xd20 on 2011-04-25
Then it's a good thing I said "various types of installation methods", eh?

I've tried burning it on multiple CD burners, on various disc mediums, onto a bootable USB, installing directly into windows through Wubi.

And all these methods work fine so long as I don't have my PCI graphics card in at the time.  So I know that is what's at fault here.



ALSO, I just rechecked my BIOS settings.  There is an option for "Primary Video Adapter" and it is currently set to my "PCI" instead of "onboard".

There is also another option that says onboard video memory or something which is currently set to "8 mb", the other options being "1 mb" and "512 kb"  But no "none" or "disable" option.


And I imagine if I changed it back to onboard, plugged the monitor into the original VGA slot, it would work fine.  Doesn't resolve how I get it to work with my PCI card though.  And I can't do this and download any drivers needed because the internet doesn't work when I do this as my PCI card for my internet doesn't work properly either, but it doesn't prevent ubuntu from loading when enabled.

---

### Post by xd20 on 2011-04-25
Okay, so I made my onboard graphics the primary and plugged my monitor into the regular VGA port.  Now, I loaded up ubuntu and it worked fine.  With my PCI card disabled as primary, but still in the computer.

I then managed to get my internet to work on ubuntu, so I am chatting to you from Ubuntu 10.04.  (Had an old disc, I'll update after I resolve the issues)

Anyway, where do I go now to get the proper drivers for my PCI card (PNY GeForce 8400gs 512mb)?

---

### Post by xd20 on 2011-04-25
I looked in the software center for some nvidia drivers and got the most recent one.  Installed it.  Installation was successful.  Rebooted, and changed my primary back to PCI instead of onboard.  Switched the VGA back so the screen was visible.. ubuntu fails to load yet again.

---

### Post by walt.smith1960 on 2011-04-26
Just a though that may or may not be relevant.  You talk about PCI.  Is your card PCI or PCIe?  I'm wondering whether you have a PCI card and Ubuntu is trying to use PCIe drivers and the two are incompatible.  Big performance difference between PCI & PCIe video.

---

### Post by xd20 on 2011-04-26
PCI, my computer only has PCI slots, no PCIe.

---

### Post by xd20 on 2011-04-26
Anymore suggestions?

EDIT:

Could it be that on my graphics card I use the DVI adapter instead of the VGA plug?  This works fine in windows.  Never tried using the VGA plug on my graphics card.

---

### Post by walt.smith1960 on 2011-04-26
> **xd20 said:**
> Anymore suggestions?

EDIT:

Could it be that on my graphics card I use the DVI adapter instead of the VGA plug?  This works fine in windows.  Never tried using the VGA plug on my graphics card.

I don't see any harm in using the VGA plug.  I wish I was more knowledgeable about the inner working of Linux and hardware. I hope you can figure out what's going on with your Nvidia card.

---

### Post by xd20 on 2011-04-27
Well I posted back in October, they couldn't figure out anything then.  Again 6 months later, no one has a resolution. 

Also, since my monitor is VGA anyway, I decided to use the VGA on my graphics card.  It works great.. on windows xp.  Still the same problems with Ubuntu.

So anyone have anymore helpful suggestions?

---

### Post by coffeecat on 2011-04-27
Hi, I'm yet another person who has used a nvidia 8400GS card with three different motherboards and not had a problem with Ubuntu. It's not your 8400GS that is the problem. I'd put serious money on this being a BIOS issue. For example:

> **xd20 said:**
> ALSO, I just rechecked my BIOS settings.  There is an option for "Primary Video Adapter" and it is currently set to my "PCI" instead of "onboard".

There is also another option that says onboard video memory or something which is currently set to "8 mb", the other options being "1 mb" and "512 kb"  But no "none" or "disable" option.

That's very odd. It *should* be possible to reduce the allocated memory for the onboard to none, effectively disabling it. See if there's another BIOS entry. Sometimes they can be very obscure and non-obvious.

Also - I couldn't find whether you had told us what the onboard video is. Is it a nvidia, or something else?

---

### Post by xd20 on 2011-04-27
There is no option to select no allocated memory, just 8 mb, 1 mb, and 512 kb.

Even though my onboard is suppose to support 64mb, and it did back when I installed the drivers for it before I got a graphics card.  Ever since then I don't bother with the drivers for the onboard.  The option to change it to 64mb was never available in the BIOS however.

But no there's no option to completely disable the onboard.

Unless you feel like helping me find a way to update my bios.  The HP Compaq site that has my computer specifications has no BIOS updates.

But the specs for my motherboard are:

```
Motherboard
    Manufacturer    MICRO-STAR INTERNATIONAL CO., LTD
    Model    Gamila/Giovani/Neon series
    Version    0n31411RE101GIOVA10
    Chipset Vendor    Intel
    Chipset Model    i845G
    Chipset Revision    B1
    Southbridge Vendor    Intel
    Southbridge Model    82801DB (ICH4)
    Southbridge Revision    02

        BIOS
            Brand    Phoenix Technologies, LTD
            Version    3.26
            Date    05/09/2005
```

If you can find driver updates for that, it'd be great, but I've had zero luck with it.

---

### Post by xd20 on 2011-04-27
Oh btw, I should mention I have updated my BIOS in the past.  A couple years ago I updated it back when I had no CD drive, cause I wanted to reinstall Windows XP.  And the update promised USB support.  It worked.

So I dunno if maybe the updated BIOS interferes or what.  But I wouldn't know how to "downgrade" it to see.

---

### Post by xd20 on 2011-04-27
Anyone figure out a way to help me yet?  It's only been since October 2010 since this issue occured.. >_>

---

### Post by xd20 on 2011-04-28
anyone?

---

### Post by xd20 on 2011-04-28
Hello? >_>

---

### Post by xd20 on 2011-04-28
bump.. gonna give 11.04 a try, see if maybe the issue is fixed in this version.

---

### Post by coffeecat on 2011-04-28
> **xd20 said:**
> bump.. gonna give 11.04 a try, see if maybe the issue is fixed in this version.

Good luck with that but I suspect, as I said before, that this is a BIOS problem. Possibly a buggy BIOS. Some simply do not play well with Linux, and there's nothing much you can do about it.

I did, in fact, have a minor issue with one of the three motherboards that I used with a 8400GS card, but not as serious as your problem. The BIOS did not autodisable the onboard (nvidia) graphics when I fitted the 8400GS card and I saw some peculiar things happening when I used the proprietary driver in 8.10, I think it was. The xserver was being confused by the BIOS reporting the presence of two cards. I solved that when I worked out how to disable the onboard graphics - by setting no memory to it. Which, of course, your BIOS is not letting you do.

I have no other suggestions - sorry.

By the way, there was some suggestion earlier that the fact that yours is a PCI rather than a PCIe card is the problem. I do not believe that this is so. The driver is the same. It's the graphics chipset that matters as far as the driver is concerned.

---

### Post by xd20 on 2011-04-28
Okay so I installed 11.04 through wubi, rebooted and ubuntu works fine on 11.04 with my PCI card!

Sort of.. it let me boot up with no issues into the desktop with my PCI set as primary.. but everything is all wonky in that it lags when I move a window.. so I'm curious if it doesn't have the drivers installed or what?  So I went to System > Administration > Additional Drivers and its currently "Downloading and updating packaging indexes..."

So hopefully that'll fix the laggy issues and install the proper drivers I need for my card.  But at least ubuntu boots up with my PCI card now, thanks to 11.04!

EDIT:  Forgot to mention, when I tried to load up the regular Ubuntu desktop it said that my Hardware isn't compatible with Unity.  Then it loaded the classic Ubuntu desktop or something.  So maybe AFTER I install the additional drivers, everything will be okay.

---

### Post by coffeecat on 2011-04-28
That's good news. You won't get particularly good performance with the default open source nouveau driver for nvidia cards - and it sounds as though it has fallen back to the classic gnome desktop rather than Unity. Hopefully the proprietary nvidia driver will make all the difference for you. Good luck again!

If, by chance the proprietary driver fails, post back. There's an experimental package to complement the nouveau driver which you could try instead.

---

### Post by Hreinsi on 2011-04-28
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at ef00 [size=128]
	[virtual] Expansion ROM at fb000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb


No prob just did fresh install

---

### Post by xd20 on 2011-04-28
I installed the recommended driver for nvidia and there's no more "window lag" and everything APPEARS okay.. but I'm not sure if I'm in unity or not.. how do I check?

---

### Post by unisol on 2011-04-28
Ive been using nvidia 8400 gs since  9.10 and have had no problems at all, no matter what drivers i used. i even tried the live cd from 11.04 and it worked without any problems.

---

### Post by xd20 on 2011-04-28
Just because you might not have problems, doesn't mean someone else won't..  So that was a senseless post.

Anyway, I in 11.04 everything works fine after getting the proprietary drivers.

Only issue now is, the internet.. it works, but sometimes it goes terribly slow.  It doesn't do that to me in windows xp.

---

### Post by xd20 on 2011-04-29
How do I edit the first post to make it say "Solved"?

I can't find the option for it.

---

### Post by 23dornot23d on 2011-04-29
In red to the right hand side towards the top of the screen if you scroll up

[COLOR=Red]THREAD TOOLS[/COLOR] ..... mark as solved is in there ( clicking the arrow to the right opens up the options for it )

---

### Post by riptool on 2011-12-18
I know this is marked solved but I found different solution.  Someone mentioned adding vmalloc=192 to the grub cmd line.  It seems this occurres a lot with the combo of 8400gs and hauppauge 1600. Everywhere I read said to add vmalloc=192MB.  But the correct syntax is vmalloc=192M.  Not 192MB.   Works for 10.04, 10.10, 11.10.  

Take out the hvr 1600 and nvidia proprietary driver boots fine. Put it back in and won't boot unless modify grub with more memory.  

Hope this helps.  I spent 2 DAYS installing tons of times only to find 192MB was incorrect.

---

