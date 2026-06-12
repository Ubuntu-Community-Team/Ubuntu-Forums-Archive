---
title: "live usb, blank screen, stuck"
date: 2015-08-05
forum: Installation &amp; Upgrades
---

### Post by salsify2 on 2015-08-05
Let me preface that I feel more comfortable in the "new to" subforum because although I've run Xubuntu for several years now, my experience is actually *very* limited in anything beyond simply being a user. 

The problem is with a new Dell XPS 8700 desktop with GeForce GTX 745. 
I want to install Xubuntu 14.04; I have no intention to dual boot and plan to wipe the Win 8.1 that came on it. BUT I don't want to wipe it (because I assume trying to reinstall will screw up in some subtle fashion) in case I cannot get the live version to run as I'll have to return it. 

Secure and unsecure boot took me to just a blank screen and nothing. Taking it down to legacy took me to grub where I chose the "try" option. That takes me to the black screen.
Legacy mode and nomodeset takes me the rest of the way to the Xubuntu desktop but it's entirely illegible. It looks like a resolution problem, but things are so pixilated that I can barely recognize the shutdown icon--I originally just guessed at it based upon location.

In searching through the forums I've found huge threads that are essentially over my head (too many options for me to evaluate suitability) and nothing that seems to address this specific issue encountered at just this point. The gist I've gathered is that the next thing is to, from this live desktop, install a new/different driver OR change out the graphics card. The latter I don't want to do as I'm trying not to have to rebuild the hardware. The former...I can't do because I can't even find the terminal let alone read anything in it, and it's not clear to me whether this is to be done in the live usb environment anyway (that is, whether that's meant for people who have already installed it on their hard drive). 

Is there a nondestructive way to proceed or is this basically an impossible situation and I should just put it back in the box and return it to the store? I truly don't want to use Windows but I also don't want to just take up buying computers at random to see if I can get a successful install on them.

---

### Post by oldfred on 2015-08-05
Probably better to stay with UEFI boot but secure boot off, not CSM/Legacy/BIOS boot.

With nVidia you almost always need nomodeset until you get nVidia driver installed from repository.
But is this dual video and you may be booting with Intel. That needs different settings to specify x by y size to match monitor/screen.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

[/URL]
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

Use Windows disk managment tools to shrink the NTFS partition and reboot so it can run chkdsk & make repair for new size. Make sure its fast startup or always on hibernation is off.
       
 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

    


[URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

### Post by salsify2 on 2015-08-05
Thank you, oldfred, for your help. As it turns out, I have several followup questions.

> [COLOR=#000000]Probably better to stay with UEFI boot but secure boot off, not CSM/Legacy/BIOS boot.[/COLOR]

Just repeated this, turning on NOMODESET as per linked instructions. Got the illegible screen again, just as  I reported in my original post.

> [COLOR=#000000]But is this dual video and you may be booting with Intel. That needs different settings to specify x by y size to match monitor/screen.[/COLOR]

I'm not sure what "dual video" means. I'm not trying to use two monitors, if that is the question.

 But if I need to specify monitor size, I don't understand where to set that.

> [COLOR=#000000]Use Windows disk managment tools to shrink the NTFS partition and reboot so it can run chkdsk & make repair for new size. [/COLOR]

I have to do this to use the live usb? Even though I plan to install only Xubuntu, not dual boot?

> [COLOR=#000000]Make sure its fast startup or always on hibernation is off.[/COLOR]

The reference quoted immediately above, [COLOR=#000000]Linux on UEFI: A Quick Installation Guide, indicates that this is necessary only if you cannot boot from usb. Is that wrong?

And, finally, 

> [/COLOR][COLOR=#000000]With nVidia you almost always need nomodeset until you get nVidia driver installed from repository.[/COLOR][COLOR=#000000]

How do I do this while in the live usb when I cannot read the screen or even locate the terminal?[/COLOR]

---

### Post by salsify2 on 2015-08-05
Update to above:
I went into Windows and turned off fast boot even though I demonstrably *was* able to boot from the live usb. Rebooting the live usb in UEFI, secure OFF, with NOMODESET on, got me the same illegible screen.

---

### Post by oldfred on 2015-08-05
You install nVidia driver after you have Ubuntu installed. But normally nomodeset gets you into installer and then nomodeset set works to boot but in lower quality graphics.

If not dual booting with Windows then you skip all the fast startup & hibernation issues. While Ubuntu should install with secure boot on, often better to have it off.
The fast boot in UEFI may prevent you from getting into UEFI as it skips all system checks for new hardware & just boots. But then no time to press key to get into UEFI. It seem to be assumed that you use Windows to get into UEFI. Grub now has a new entry at bottom that should also work to get you into UEFI.

Some systems have dual or switchable video. They use Intel for low power and switch to nVidia for heavy duty graphics. That adds a complication. So does you system only boot with nVidia or is it using the Intel video also?
Most desktops do not have the dual video, but you may have two video connections. One on motherboard for Intel and one on Video card for nVidia.

If desktop what monitor and what cable HDMI, VGA or what are you using?

---

### Post by salsify2 on 2015-08-05
Here's what the back of the box looks like. I'm using the cable that you can see me holding at the bottom. It looks to me as though it's plugged into the card.
[IMG]http://i169.photobucket.com/albums/u206/seldsalt/2015-08-05%2014.56.06_zpsemcirrdn.jpg[/IMG]

The monitor is a Samsung SyncMaster 2443 BWX. I'm have been using this cable/monitor combination for several years now with Xubuntu on my old box and no particularly special settings or difficulty encountered when installing or upgrading.

---

### Post by oldfred on 2015-08-05
No, that is good & that is the nVidia.
Just confirming as you do show HDMI & maybe other connections on motherboard which would then be Intel video.
Most then do work with nomodeset, but get low quality graphics. Not sure how to change it then if nomodeset is not working.

Is your video card in the Maxwell family from nVidia? Those do have issues. And need the newest kernel, support software and open source driver just to boot.
[http://askubuntu.com/questions/581024/i-need-drivers-for-nvidia-geforce-gtx-745-card-dont-work-correct](http://askubuntu.com/questions/581024/i-need-drivers-for-nvidia-geforce-gtx-745-card-dont-work-correct)
       
Top end Maxwell cards.
The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)

Some others with new nVidia. It just may be the combination of default size of monitor and default size nVidia card is using. 
 Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)

You will want to add a ppa for the nVidia drivers. I might download 15.04 and see if with nomodeset it works. Or even 15.10, but would not use it as main install, yet.


    
I recently purchased a Dell SFF system but only had Intel internal video. But with 15.04 it just installed & worked. It took me several days to do all the backups & resizing of Windows. And with partitions set in advance took 10 to 15 min to install & reboot.

---

### Post by salsify2 on 2015-08-05
> [COLOR=#000000]Is your video card in the Maxwell family from nVidia? Those do have issues. And need the newest kernel, support software and open source driver just to boot.[/COLOR]
[http://askubuntu.com/questions/58102...t-work-correct]("http://askubuntu.com/questions/581024/i-need-drivers-for-nvidia-geforce-gtx-745-card-dont-work-correct")

I really can't understand this post, but there seems to be an issue of two monitors involved, which is not my situation. 

I don't know how to determine if it's a "Maxwell" but this is the specs page: [http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-745-oem/specifications](http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-745-oem/specifications) and that doesn't use the term Maxwell.

Looking at the other links, however, it appears as though it's not possible to set up an nvidia card with Linux. And since I can't get a usable display using the live usb, there's no way I can use either terminal or the software center to install other drivers in any case. 

I'll admit to being disappointed that this has failed and that I can't get Linux running. And given as how graphics seem to be so problematic with so many new machines (I gather from all of the posts here with so many variations on this), I'm guessing this takes Xubuntu back out of the reach of someone who just wants to use it but doesn't want to get into rewriting all of the programming. Which for me means going back to running it on my old hardware until that dies and then being forced to return to Windows, the thought of struggling with which makes me even more queasy. 

Thanks for trying to help.

---

### Post by oldfred on 2015-08-05
Does you monitor have other connections to use Intel motherboard video?
 Or can you use a HDMI cable to connect to TV? That would be using Intel.

You are the very first that nomodeset has not worked with nVidia that I have seen.

Are you able to get to grub menu?
 From a grub command line to see available settings pressing <c> & escape to get back to menu then enter this:

vbeinfo

---

### Post by salsify2 on 2015-08-07
Ah, sorry to be delayed in responding, but I've already returned the computer. I'd like to help you explore this issue, but there's an urgency for me right now in getting a computer that works given as how the one I was replacing that was flaky when I unplugged it is now refusing to start up again. Guess I'm looking at a laptop now from Dell with Ubuntu pre-installed; all the desktops they offer seem to be with the older Ubuntu versions, which I assume can't be upgraded due to proprietary drivers. 

Thanks for your help and I'm sorry I couldn't stick with the whole troubleshooting thing. Good luck with it to the next person this affects, though.

---

### Post by oldfred on 2015-08-07
I do not think Dell uses any proprietary drivers.

The version they released with 12.04 had to have spuknik added which was a set of drivers. But then all those were including in 14.04. Some Dell's need some settings changed in UEFI or have some issues in certain configurations. 

 Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)


 Dell LATITUDE E5450  LInks to Dell fixes for 14.04
[http://ubuntuforums.org/showthread.php?t=2270275](http://ubuntuforums.org/showthread.php?t=2270275)
Dell M3800 with 14.04 Some issues
[http://arstechnica.com/gadgets/2015/03/review-dell-m3800-developer-edition-is-a-great-linux-pc-with-a-few-rough-edges/2/](http://arstechnica.com/gadgets/2015/03/review-dell-m3800-developer-edition-is-a-great-linux-pc-with-a-few-rough-edges/2/)
Dell XPS13 - New Broadwell, not yet fully supported Feb 2015
[http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/](http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/)
[http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly](http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly)

---

