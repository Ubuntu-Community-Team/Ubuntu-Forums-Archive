---
title: "Can't start Ubuntu Live CD for 13.04 installation on Win8 UEFI system"
date: 2013-06-10
forum: Installation &amp; Upgrades
---

### Post by skrishna on 2013-06-10
Folks, I feel like a lot of variants of this question have been asked but that the specific cases are pretty divergent, and nothing I've found on these threads has solved my issues -- so here goes.

I've got a new computer -- an HP Pavillion with Windows 8 preloaded, made in late 2012, with an AMD Trinity A10-5700. I've set up quite a few dual-boot computers with XP/Ubuntu and Win7/Ubuntu -- you always need the Windows for crap people send you from work! -- and that's easy enough but I get that "Fast Boot" and UEFI create all kinds of fascinating issues for Windows 8, though I'm not BIOS-savvy enough to really get those issues.

So: I made an Unbuntu installation CD (under Ubuntu, from an older Win7/Ubuntu machine). Downloaded 64-bit 13.04 (I've tried all this stuff with the 12.04 LTS too, I've gone to 13 because I know there's a UEFI support issue). If I disable "Fast boot" then I can (UEFI) boot up on the Ubuntu Installation disk and it takes me straight to the menu screen (the "Try Ubuntu" "Istall Ubuntu" "Test disk" jazz.) Cool beans. But no matter what I pick -- nothing happens. The computer hangs, forever. 

Disabling "Secure Boot" mnakes no difference (except that the screen flashes "Secure Boot not enabled" before going to that menu). 

If I _enable_ Legacy booting, then I can boot up on the install CD, I can try ubuntu and mess around, and I can go through the motions to install, but I haven't completed that process because it's my understanding that I want to install the bootloader under UEFI so it plays well with the Windows partition.


So, why can I only start up in Legacy mode?

---

### Post by sudodus on 2013-06-10
Welcome to the Ubuntu Forums :-)

Given the computer, you have done most everything right, as far as I understand. My question is if the computer is set to allow other operating systems in UEFI mode. But I'm here to learn. In spite of all my beans, I'm a newbie in the discussions about UEFI.

*Edit*: Aaah, you boot from CD. Syslinux is used in legacy booting, and grub.efi in UEFI booting. *Can grub boot from a CD, or should it be booted from USB*? I can boot my Toshiba with Windows 8 in UEFI in both modes, but I have only tried from USB (and the internal drive).

---

### Post by ajgreeny on 2013-06-10
You can certainly boot, and install, in UEFI mode from a CD (actually DVD in my case) and I did it only two or three months ago with Xubuntu 12.04.2 64bit.  I have no idea about the possibility of 32 bit systems doing the same as I did not want 32 bit and therefore did not try that out.  Neither can I help with any differences Win 8 may make as I no longer run any Windows system in the house.

Are you sure the iso file you used to burn the CD was good (see info at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")) and burn at lowest possible speed, then check the CD by hitting any key at the first screen that appears.  If all is OK you may wish to try one by one, the boot options by pressing F6.

---

### Post by sudodus on 2013-06-10
I'm glad to learn that you can boot, and install, in UEFI mode from a CD.

I think you found something. UEFI does not allow 32-bit systems (at least not Ubuntu 32-bit).

---

### Post by skrishna on 2013-06-10
Thanks for the welome! And for the thoughts.

What I've got on my DVD (sorry, "CD" was laziness on my part, it's a DVD) is in fact 64-bit Ubuntu 13.04; ain't no 32-bit involved here. So that's not my issue.  I feel good about the DVD, both becuase I got the official distro and burned it at the lowest speed and hash-checked it, and then because I thought, what the hell, DVDs are cheap -- and did it all again.  And as I mentioned, I have this problem both with the 13.04 iso and the 12.04 LTS, so I guess that's three slow-burned DVD's....

---

### Post by oldfred on 2013-06-10
It seems some computers only install with BIOS and you have to convert to UEFI with Boot-Repair. Some boot Windows with secure boot on or off and install in UEFI mode without issue. And some only boot the Windows efi file which is not per UEFI and again Boot-Repair has a work around by renaming grub's shim to make it work.

Other HPs.

 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by skrishna on 2013-06-13
Thanks, oldfred -- it's taken me a while to work through all those suggestions, but still no dice.

On the other hand --MAN, there's a lot of Windoiws 8 dual-boot install threads running around here, new ones even since I posted.  So I'm going to read through all that stuff.  If nothing else works I'll legacy boot the DVD, install off of that, and then see if I can somehow Boot-Repair/EasyBCD myself into a dual-boot UEFI system....

---

### Post by oldfred on 2013-06-13
Part of the issue with UEFI and secure boot is that every vendor has implemented it somewhat differently and sometime even different models of one vendor are not the same.

So it requires the user to understand a lot about UEFI, which almost no one does, and then see what differences are with his specific system.

Eventually vendors will clean up bugs in UEFI, Ubuntu/grub will figure out most of the different ways and have work arounds for most of them. But that is a while into the future. In the mean time we just have to try various alternatives and see what works.

---

### Post by jgreindl on 2013-06-14
Same problem for me, with diff computer (MSI GT 60)
I've tried everything i've found - w/o success. always black screen if i try or install ubuntu (same version as above)

If i try a "legacy" boot with a non uefi ubuntu, install works, but doesnt not see my windows install. So i didnt execute installation, for now.

---

### Post by Rebelli0us on 2013-06-14
Laptop makers  cater to Microsoft with their custom BIOS. What's wrong with Legacy mode? I [wiped off Win8 from my laptop]("http://ubuntuforums.org/showthread.php?t=2120763") and Linux works just fine.

---

### Post by skrishna on 2013-06-15
That's a luxury many of us don't have!  At any given time my family has a simgle computer; I prefer to do everything on Ubuntu and so do my wife and kids.  But our most recent machine is ten years old, and folks from work send me Microsoft Office stuff -- no, LibreOffice is great but never quite seamlessly converts -- and my daughter gets PowerPoint assignments from school, and software that works with other electronics in the house often has no Linux equivalent -- so Windows is always going to be there somewhere.  If I have to pick only one, I _want_ to pick Ubuntu -- but _have_ to pick Windows.

---

### Post by oldfred on 2013-06-15
Some systems only install in BIOS mode but Boot-Repair can convert a BIOS install to UEFI by uninstalling grub-pc(BIOS) and installing grub-efi(UEFI).

---

### Post by skrishna on 2013-06-16
I'm trying that now, oldfred, will post on the results....

---

### Post by skrishna on 2013-06-16
OK, here's something I don't understand at all, maybe it'll help jgriendl too, but there's clearly Deep Bios Stuff going on here that I don't get.

So again, the issue has been, if I boot up from the 13.04 installation DVD under UEFI, I get to the GRUB menu but no further -- any choice (try, install, check disk) and everything hangs.  If I enable legacy booting and boot up legacy (and of course the route to the GRUB menu looks different), then I can do all that stuff and maybe install but I have been reluctant to do the install because I want to UEFI dual boot (although per oldfred's note above it is conceivable that boot repair will "convert" the legacy boot to a UEFI boot.)  Now I do all this by hitting F10 at startup and getting intothe BIOS menu where I can do things like enable Legacy boot, disable "fast boot" (disabled throughout of course), disable Secure Boot (necessary to enable legacy booting), etc.  Then I get to the BIOS boot menu and tell it what source I want to boot up from and whther I want to UEFI boot or legacy boot.

SO, I've given up and am going to legacy boot from the DVD, and install, and see what happens.  Meaning, I go into the BIOS menu, disable secure boot, enable legacy boot, boot up off the DVD.  Now note: I've disabled secure boot before without enabling legacy boot, UEFI booted up off the DVD, and had the problem above.  And I've enabled legacy boot and legacy booted up off of the DVD and things were fine.

But today, with legacy boot enabled, I chose for the hell of it -- one last hurrah -- to UEFI -- not legacy -- boot off of the DVD.  And it did it.  Just fine.  And I'm running, and the install seems OK.  But if I disable legacy boot -- even though the GRUB menu comes up as if I UEFI booted -- then the computer hangs.  Now, GRUB sees Windows, but it can't boot off of Windows, so I'm going to start going through the whole boot repair jazz and see what happens.  But, just FYI -- and in the hopes that this helps jgriendl, who can maybe push this more forward -- this is what I've got so far.

---

### Post by skrishna on 2013-06-16
Wow, that's entertaining.  Did boot-repair, got [http://paste.ubuntu.com/5771586](http://paste.ubuntu.com/5771586).  

Now the GRUB menu comes up and if I boot into Ubuntu, it hangs for all time.  But if I boot into WIndows, all is well.  Go figure.  Ubuntu seems to have killed itself.

---

### Post by sudodus on 2013-06-16
I had a similar situation with a Toshiba laptop, installed Ubuntu 12.04.2 alongside Windows 8 in UEFI, and had to use *YannBuntu*'s ***Boot-Repair script*** to make grub able to boot both Ubuntu and Windows. It worked with the default one-button method.

But after a while, I think after updating Windows, the booting was damaged, and I had to run Boot-Repair once more. It is still working.

A difference was that I managed to install in the first try.

But I am a total noob regarding UEFI and needed help from *oldfred*, in spite of all my beans ;-)

-o-

Anyway, as soon as you have a working dual boot system, ***make a complete backup*** of it, so that you can restore it, if it gets corrupted.

---

### Post by sudodus on 2013-06-16
I ran Boot-Repair from a ***live*** USB drive (not from the installed system). It is a the system suggested by YannBuntu, if I remember correctly based on Ubuntu 12.10 (so more or less Ubuntu desktop 12.10 plus Boot-Repair).

[COLOR=#696969]I leave the interpretation of the pastebin data to the experts.[/COLOR]

---

### Post by oldfred on 2013-06-16
If you get to grub menu after install and can Boot Windows that is great and you are past the UEFI issues and probably into video issues or other boot parameters needed.

What video card/chip?

Does recovery mode, possibly under Advanced options submenu, boot?

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS live installer Boot Options
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by skrishna on 2013-06-16
Perhaps, oldfred, but I am confused -- Ubuntu runs just fine under the live DVD (UEFI boot with legacy boot enabled, again --?) after all, there's no missing video driver there.  The video card is a Radeon HD 7660D (so there should be an open-source driver).

Recovery mode does not boot.

---

### Post by skrishna on 2013-06-16
OK, I'm 90% there.  I can boot Ubuntu or Windows.   Windows is never an issue.  Ubuntu will _only_ startup if legacy booting is enabled and secure boot disabled.  So much for UEFI or secure booting -- BootRepair can't help me.  Latest result at [http://paste.ubuntu.com/5772728](http://paste.ubuntu.com/5772728).  I suppose this will work; I have both operating systems there.  But I'll try to get Secure Boot enabled.

---

### Post by oldfred on 2013-06-17
I am not sure what the install does differently for some systems, but I cannot boot live flash drive nor first boot without nomodeset and have to install nVidia drivers to not need nomodeset.

Also UEFI writes hardware system info differently than BIOS and then grub & Ubuntu have to read that data. If UEFI not correct then it can be an issue.
Have you updated UEFI/BIOS to latest version. 
Only one system so far have I seen where BIOS worked and users were not ever able to get UEFI video to work was Asus K55N, but similar Asus models worked.

All this various HPs have worked. Not sure if any posted video issues or not.
       HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by wc711 on 2013-06-17
I downloaded the USB Penn Drive Linux, usb universal installer then I downloaded 13.04 to a DVD.  The Penn drive locked on to the iso file on the DVD and proceeded to install.  My original intention was to install on my USB 50 gig hard drive, but when the options page popped up, it showed the options which included partitioning.  I figured with a 500 gig hard drive, why not just set up a partition and install it there.  With no experience to speak of, I just took my time and tried to make sure I made the right selections.  The big problem was my Nvidia graphics driver is a proprietary drive so it has to be loaded after the fact, and it's really hard to read the screen without it, but if you really strain your eyes you'll figure it out.

The partition took a long time to set up, but when it was done, all I had to do is click the install button.  Installation takes a long time because I opted to download all the updates and software at the same time.  When It was done, I rebooted and got a boot screen with ubuntu listed first.  I just waited and it loaded Ubuntu by default.  Everything was there except it was almost impossible to read, but I found the Additional Drivers button and clicked it.  The screen pop showed 3 Nvidia drivers,but I didn't know which one I needed.  It takes a little time because the first driver I tried to load was not compatible so I went to the next one, it turned out to be the right one.  After a reboot, my new 13.04 appeared and it was a thing of beauty.  What is really tremendous is that it shows all your drives.  I can go into my Windows 8 partition and copy files right from there into my Ubuntu. 

I started last week for the first time by setting up 12.01 on a DVD, but there was so much freezing and stalling along with the screen dimming that I decided to do a side by side installation.  That was better but still freezing and stalling. No screen dimming though.  I had the same problem with the Nvidia driver so I had to fire up Fire Fox and go to Nvidia to download the dirver.  I had also installed the Wine program loader too, so when the driver was downloaded I just selected the Wine program to install it.  I was all set up, but  things went all bad when I got a notification that I had around 300 updates ready to install.  This took a long time and eventually said I didn't have enough disk space.  I knew I did, so I rebooted and when it opened up All I got was a screen that stated I had graphics problems and would have to go to a low graphics mode.  I clicked Ok and got the terminal.  I'm not a terminal guy.  All I know how to do is type DIR to get a directory.  I Tried everything I could, but couldn't resolve anything.  That's when I discovered the Penn Drive program.  The description made it look very simple.  Since I was having trouble with 12.01 I decided to go with 13.04.  Penn Drive uninstalls all previous Ubuntu files before it goes to work on the new install.  I got loads of help from all the people herre and I want to say thanks.  I had been into Fire Fox, Open Office.org and most recently Thunderbird email.  It was my total disappointment with Vista and Windows 8 that made me begin to research Linux, and I am so glad I did.

---

### Post by sudodus on 2013-06-17
Welcome to the Ubuntu Forums wc711 :-)

---

### Post by skrishna on 2013-06-17
Oldfred -- wow, that's a lot to research!  Will do, and will post here when it's fixed; I feel close to it, but I'm neglecting my kids a bit.  Man, the amount of back-and-forth collected in these fora is staggering; it's frustrating because I suspect the answers to everything are in here, but I can't find 'em.  I think many of us would be screwed without, well, you!  

But I will try NOMODESET tonight -- try it temporarily from the GRUB menu and see if it makes a difference.  From what I'm learning about secure UEFI it sounds like, yeah, I might've been way off base as to whether it could make a difference.

---

### Post by skrishna on 2013-06-18
Well, it's not NOMODESET -- makes no difference on the booting behavior.  I'm still limited: I can only boot with legacy BIOS boot enabled (an, perforce, Secure boot disabled).

---

### Post by skrishna on 2013-06-18
Truth be told, I just bricked everything -- for a second time -- screwing with boot-repair, and had to re-set-up to factory config.  I'm in a bind -- I'm a scientist who's never written anything large nor made a presentation without EMACS and TeX (well, OK, I used to use overheads for presentations) in twenty years, and my kids have grown up with Ubuntu -- but I don't think my four-year-old -- skilled though he is -- needs to go screwing with the BIOS every time he boots up, so I think we're going back to a Windows-only system for the first time in aeons; professionally I need that and my kids need it.  I figure in a year or so people will have some good, consistent work around for dual booting.  FIguring it out right now is like a second job for me in terms of all the BIOS stuff I need to learn, and, I haven't time.

The upshot of which is: man, this Secure Boot stuff sucks.

---

### Post by sudodus on 2013-06-18
It serves its purpose, to lock you inside the Windows world, so those who made it think it rocks ;-)

Right now you can get out of the Windows world with a cheap second-hand computer and an Ubuntu flavour (selected depending on the horsepower of that computer).

---

