---
title: "Problem while trying to install Ubuntu 12.04LTS from USB"
date: 2014-02-16
forum: Installation &amp; Upgrades
---

### Post by Dedalo on 2014-02-16
Hi. I'm trying to install Ubuntu 12.04LTS from my USB. I have used Universal Installer in a computer with windows to create the bootable USB ([http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)). I followed all the steps, loaded the .iso, formated the usb drive to fat32, etc. ([https://help.ubuntu.com/community/Installation/FromUSBStickQuick](https://help.ubuntu.com/community/Installation/FromUSBStickQuick))

Then, I've tried to boot my other computer (which is a Dell inspiron, with intel i5 processor) from the USB. I put it from the BIOS to boot from the USB as prior, as it was told in the community help wiki. 

I get to this window: [IMG]https://help.ubuntu.com/community/Installation/FromUSBStickQuick?action=AttachFile&do=get&target=Fig02a.png[/IMG]

The thing is that when it boots from the USB, I can't do anything. It goes to the characteristic window of installation, but then it appears this windows which says "Install" on it, and this messagge:

"This Dell Recovery media can be used to restore the original factory software.
It is recomended you back up all important data before running this tool.

(!) Error: This recovery media only funcions on Dell and Alienware systems."

And the touchpad doesn't work, I can only hit enter, and then cancel, I can't even give to quit, or continue or anything, so then I have to shut down the computer to get out of it.

What can I do?

Thank you in advance.

---

### Post by Dedalo on 2014-02-17
anyone please?

---

### Post by sammiev on 2014-02-17
Hi, Have you checked [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) of your download for errors?

Usually you can press F6 for different boot options on the fist menu of the installer on boot.

---

### Post by Dedalo on 2014-02-17
I didn't do it then. I just did it, and it seems to be fine:

[ATTACH=CONFIG]250443[/ATTACH]

Anyway, I should check the one on the USB drive, perhaps it was corrupted when I copied it.

The .iso on the usb drive gave this: c7f439e864d28d9e5ca2aa885c4ec4cb  ubuntu-12.04.4-desktop-amd64.iso
Yes, it's fine. Could it be corrupted when I used the UUI to create the bootable USB? 
I think the problem is beeing created by the computer itself, because it's something of Dell. I don't know what to do.

---

### Post by Dedalo on 2014-02-17
My laptop is a dell inspiron 3420 if that means something.

---

### Post by Dedalo on 2014-02-17
Can a moderator move this to the sub forum Installation & upgrades, please? I think the problem is not that trivial.

---

### Post by fdrake on 2014-02-17
check if you can boot from the usb another pc.
if not luck try this:
format your usb to fat32 and the use UNebootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Iowan on 2014-02-17
> **Dedalo said:**
> Can a moderator move this to the sub forum Installation & upgrades, please? I think the problem is not that trivial.

Moved per request.

---

### Post by Dedalo on 2014-02-17
THanks for moving it. Now I could "try" ubuntu from the usb, it starts everything is allright, but I can't install it. I think the problem has something to do with dell architecture, and not with the bootable usb itself.

I also found this: [http://www.ubuntu.com/certification/hardware/201202-10589/](http://www.ubuntu.com/certification/hardware/201202-10589/)

and this: [http://www.ubuntu.com/certification/hardware/201202-10590/](http://www.ubuntu.com/certification/hardware/201202-10590/) this last is almost the same than mine computer, my processor is quite different i5 3210M, 2.50Ghz. I'll try if it work with the iso on this link and I'll let you know.

Thank you all by now :)

(Excuse my english, I know it sucks from time to time).

---

### Post by Dedalo on 2014-02-17
THanks for moving it. Now I could "try" ubuntu from the usb, it starts everything is allright, but I can't install it. I think the problem has something to do with dell architecture, and not with the bootable usb itself.

I also found this: [http://www.ubuntu.com/certification/hardware/201202-10589/](http://www.ubuntu.com/certification/hardware/201202-10589/)

and this: [http://www.ubuntu.com/certification/hardware/201202-10590/](http://www.ubuntu.com/certification/hardware/201202-10590/) this last is almost the same than mine computer, my processor is quite different i5 3210, 2.50Ghz.

I think I'll try dowloading the .iso in the last link, and then I'll tell you.

This .iso says: Ubuntu 12.04.1LTS; the one I downloaded before was: Ubuntu 12.04.4LTS

THis one is older? it isn't the one that has support until 2017?

---

### Post by fdrake on 2014-02-17
have you tried if you have any luck with the 32bit version of ubuntu?

---

### Post by Dedalo on 2014-02-17
No, I didn't. As I said, the problem doesn't seem to be the installation it self, or the booting, but the architecture. Now I have ubuntu 11.10 64bit. It has to do with the manufacturers certificate, as it says in one of the links:

*[COLOR=#333333][FONT=Ubuntu]The [/FONT][/COLOR]**Dell Inspiron 3420**[COLOR=#333333][FONT=Ubuntu] portable with the components described below has been awarded the status of [/FONT][/COLOR]**Certified**[COLOR=#333333][FONT=Ubuntu] for Ubuntu.[/FONT][/COLOR]****[B]Please note that for pre-installed systems:***[/B]


[LIST=1]
[*]*The system is available in some regions with a special image of Ubuntu pre-installed by the manufacturer. It takes advantage of the hardware features for this system and may include additional software. You should check when buying the system whether this is an option.*
[*]*Standard images of Ubuntu may not work at all on the system or may not work well, though Canonical and computer manufacturers will try to certify the system with future standard releases of Ubuntu.*
[/LIST]
[http://www.ubuntu.com/certification/hardware/201202-10590/](http://www.ubuntu.com/certification/hardware/201202-10590/)

I think thats the problem. So, I'll try to install this version, and then tu update. I'm downloading it right now. I'll tell you later what happened.

I bought this computer last year, and it had ubuntu 11.10 preinstalled. I couldn't do anything, like installing programs, or updates, anything. I took my time, and now I decided it's time to install a new version of it. I think that one that I've found should work.

---

### Post by Dedalo on 2014-02-17
Well, bad news. The problem persists on that version. I don't know what to do. It seems I'll have to move to windows.

---

### Post by sammiev on 2014-02-17
> **fdrake said:**
> check if you can boot from the usb another pc.
if not luck try this:
format your usb to fat32 and the use UNebootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

+1 to both comments.

---

### Post by Dedalo on 2014-02-18
All right, I'll try that, but I'm not too optimistic. I think the problem is with dell and not the bootable USB. Perhaps I should format my HD first. Anyway, I don't know how Dell platform interferes when I boot from the USB. The touchpad gets blocked, but I've could use an USB mouse that I have. That the touchpad gets blocked tells me that something is going on with the Dell drivers I think.

---

### Post by oldfred on 2014-02-18
Dell's are pretty common across models.
With 12.04 Dell issue something called sputnik to add all the extra drivers needed with Ubuntu 12.04. Someone posted that all those features were in 13.10.

Very new Haswell processors need 13.10. Not sure if 12.04.4 includes all those or not.

       Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

Is system configured for UEFI or BIOS?
      
 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

---

### Post by Dedalo on 2014-02-19
Well, I think I've tried everything. I've tried writing different dvds. Now, with the dvds the problem was different. I get to the installation preparation windows, and then it freezes there. I've written the .iso in many different dvds following the instructions given in the ubuntu manuals, the dvd was correctly written. I thought that perhaps some of the dvds wasn't working correctly, so I've burnt like three of them, with all of it I had the same problem. Than I took an other pen drive I have, this one is a hp of 16gb (v165w). Same problem than I had with the kingston data traveler.

I also tried to boot the hp from other computer, I had problem with it too, I couldn't boot it, I don't know why, it gave me an error on a black screen. It looks like a different problem.

---

### Post by Dedalo on 2014-02-20
How do I know it its configured with UEFI or BIOS? I think its BIOS, but I'm not sure.

Oldfred, I appreciate the recopilation you made there. The thing is I don't have the time to read all that. I really wasn't expecting to loose all this time installing ubuntu. I need it before April, when I'll start to work in a research group, on computational physics. I'm a physics student, not an expert on this things. And right now I have to study a lot, and I have a lot of things to do. I hoped to find a quick answers to this sort of things, because I'm not really familiarized with Linux, I've used it before, but I have to learn to use the terminal, to install some software, and all that stuff. I hoped to do this before I started to work on the research project. I'm also working on the department of physics at my university, and all that stuff is time consuming. I'm losing some time trying to get over this, but I really can't give me that luxury right now, because I have lot of stuff to study. I wrote to dell, I hope they can help me. If anyone finds a solution on this, I'll really appreciate that. If anyone has the same laptop model as me, and is using ubuntu, please, let me know your experience.

Sorry I have to explain all this, but is not that I don't have a predisposition to solve this problem, I just can't give me that luxury right now, and I thought that all of these was going to be much quicker than it resulted.

Regards.

---

### Post by tasos2 on 2014-03-09
I have the same problem with a dell 15R 5521..still don't know what to do..

---

