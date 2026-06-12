---
title: "Nothing Works"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by Powerman2442 on 2009-12-07
Hello all, running a fairly old PC and trying to get some flavor of Ubuntu installed and working fully. I've tried the following. 

Ubuntu 7.04, 8.04, and (currently) 9.10 
Xubuntu 8.04 and 8.10 
Kubuntu 8.04

Basically I try to boot from the LiveCD and it sits at the loading screen, "doing nothing". From time to time 8.04 will load up the orange desktop with the mouse pointer in the middle of the screen. Never makes any intro sounds, loads the rest of the UI, and I can't move the mouse. 

After a lot of screwing around with 8.04 I reverted back to 7.04. The 7.04 LiveCD managed to boot and I got Ubuntu dual booted with Windows XP. The problem I have with 7.04 is I've tried everything to get my wireless NIC to work, with no luck (RTL8185).

I was hoping that 8.04 or 9.10 would work better in terms of connecting via wireless, but it won't work at all. What would make the LiveCD "freeze" every time I try to boot it up. With 8.04 it either gets stuck on a blank screen with a flashing white underscore in the top left hand corner, a "plain jane" black screen, or the orange desktop with the mouse pointer in the middle. With 9.10 it gets stuck on a flashing white Ubuntu logo. Waited 20 - 30 minutes (if not longer) and nothing happens.

Basic Specs:
Intel Pentium 3 550 Mhz (Slot 1)
576 MB of PC-100 RAM
GeForce2 MX 400 32 MB

Before you ask I am posting on Windows XP, same PC.

---

### Post by phillw on 2009-12-07
> **Powerman2442 said:**
> Hello all, running a fairly old PC and trying to get some flavor of Ubuntu installed and working fully. I've tried the following. 

Ubuntu 7.04, 8.04, and (currently) 9.10 
Xubuntu 8.04 and 8.10 
Kubuntu 8.04

Basically I try to boot from the LiveCD and it sits at the loading screen, "doing nothing". From time to time 8.04 will load up the orange desktop with the mouse pointer in the middle of the screen. Never makes any intro sounds, loads the rest of the UI, and I can't move the mouse. 

After a lot of screwing around with 8.04 I reverted back to 7.04. The 7.04 LiveCD managed to boot and I got Ubuntu dual booted with Windows XP. The problem I have with 7.04 is I've tried everything to get my wireless NIC to work, with no luck (RTL8185).

I was hoping that 8.04 or 9.10 would work better in terms of connecting via wireless, but it won't work at all. What would make the LiveCD "freeze" every time I try to boot it up. With 8.04 it either gets stuck on a blank screen with a flashing white underscore in the top left hand corner, a "plain jane" black screen, or the orange desktop with the mouse pointer in the middle. With 9.10 it gets stuck on a flashing white Ubuntu logo. Waited 20 - 30 minutes (if not longer) and nothing happens.

Basic Specs:
Intel Pentium 3 550 Mhz (Slot 1)
576 MB of PC-100 RAM
GeForce2 MX 400 32 MB

Before you ask I am posting on Windows XP, same PC.

I'd go for burning a Xubuntu LiveCD, at 4X speed. Check the iso image before you burn it to disk --> [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
and then re-check the cd using the above instructions.

Xubuntu is for low RAM computers, and probably gives you the best chance of success.

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)  has the images, by country. Go for 9.10, it also should have inbuilt support for your wireless card.

Regards,

phill.

---

### Post by Powerman2442 on 2009-12-07
> **phillw said:**
> I'd go for burning a Xubuntu LiveCD, at 4X speed. Check the iso image before you burn it to disk --> [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
and then re-check the cd using the above instructions.

Xubuntu is for low RAM computers, and probably gives you the best chance of success.

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)  has the images, by country. Go for 9.10, it also should have inbuilt support for your wireless card.

Regards,

phill.

I check all the ISOs MD5SUMS and "Check Integrity of CD" from the boot menu. Everything checks out fine, but I still have problems. Even ordered a free Ubuntu 8.04.1 CD.

---

### Post by phillw on 2009-12-07
There have been reported cases where burning the cd on a different machine has had positive results. - I'd also suggest cleaning the drive with a cd-cleaner. Burning ISO's can, sometimes, appear to be more an art than a science.

As you say, quite an old wee beastie.. This thread may be of help to you --> [http://ubuntuforums.org/archive/index.php/t-499326.html](http://ubuntuforums.org/archive/index.php/t-499326.html)

That is invoking the Wubi method, which does not require partitioning of drives, the xubuntu will run as an application within the Windows area. It may be one area to explore.

Assuming the computer has USB capability, even if it does not have the option to boot via USB device. You can also get ubuntu (or any of its variants) that way.

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Have references to that, for a computer that doesn't support booting from USB device, you have the option to follow this method --> [http://www.pendrivelinux.com/category/usb-boot-cds/](http://www.pendrivelinux.com/category/usb-boot-cds/)

Needless to say, those guyz at pendrivelinux are certifiabely insane with what they get pen-drives to do !!!! - But, their methods work - and work very well.

Hope that gives you some further options.

Regards,

Phill.

---

### Post by Powerman2442 on 2009-12-07
> **phillw said:**
> There have been reported cases where burning the cd on a different machine has had positive results. - I'd also suggest cleaning the drive with a cd-cleaner. Burning ISO's can, sometimes, appear to be more an art than a science.

As you say, quite an old wee beastie.. This thread may be of help to you --> [http://ubuntuforums.org/archive/index.php/t-499326.html](http://ubuntuforums.org/archive/index.php/t-499326.html)

That is invoking the Wubi method, which does not require partitioning of drives, the xubuntu will run as an application within the Windows area. It may be one area to explore.

Assuming the computer has USB capability, even if it does not have the option to boot via USB device. You can also get ubuntu (or any of its variants) that way.

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Have references to that, for a computer that doesn't support booting from USB device, you have the option to follow this method --> [http://www.pendrivelinux.com/category/usb-boot-cds/](http://www.pendrivelinux.com/category/usb-boot-cds/)

Needless to say, those guyz at pendrivelinux are certifiabely insane with what they get pen-drives to do !!!! - But, their methods work - and work very well.

Hope that gives you some further options.

Regards,

Phill.

By "burning on a different PC" do you mean a different PC then the one I am trying to install Ubuntu on, or a different PC then I have been burning the discs on? I don't have a burner in this machine (the one I am trying to put Ubuntu on). 

I'm burning the discs on my Dad's PC. Some of the discs I am using I burnt on my laptop (before I sold it). They ran and installed fine on my laptop. Also, like I said, I have Ubuntu and Kubuntu 8.04 that I ordered from the site. They do the same thing.

I have looked into booting from USB (for Damn Small Linux and a Frugal install), unfortunately this PC is to old and the mobo doesn't support it. I will look into the USB boot CD though.

Going to try to run these discs on my Dad's PC a bit later. His is fairly old as well but a lot newer then my system. I'll let you know if his runs them fine or if the same problem persists.

---

### Post by Powerman2442 on 2009-12-08
> **Powerman2442 said:**
> By "burning on a different PC" do you mean a different PC then the one I am trying to install Ubuntu on, or a different PC then I have been burning the discs on? I don't have a burner in this machine (the one I am trying to put Ubuntu on). 

I'm burning the discs on my Dad's PC. Some of the discs I am using I burnt on my laptop (before I sold it). They ran and installed fine on my laptop. Also, like I said, I have Ubuntu and Kubuntu 8.04 that I ordered from the site. They do the same thing.

I have looked into booting from USB (for Damn Small Linux and a Frugal install), unfortunately this PC is to old and the mobo doesn't support it. I will look into the USB boot CD though.

Going to try to run these discs on my Dad's PC a bit later. His is fairly old as well but a lot newer then my system. I'll let you know if his runs them fine or if the same problem persists.

Put the 9.10 LiveCD in my Dad's PC and it runs perfectly. In fact I am posting from it right now.

Specs:
Intel Pentium 4 1.5 Ghz (Socket 478 )
768 MB of PC-133 RAM
GeForce2 MX 400 32 MB

So since the discs run fine on his PC and not mine is it safe to assume that it is because of my lower end system? I am going to download Xubuntu 9.10 and try to run the LiveCD. Like I said though, I have a copy of Xubuntu 8.04 and when I boot from the disc (select English and select "Try Xubuntu before you install it") it has a blinking white underscore in the top left hand corner of the screen. I've let the underscore blink for 30+ minutes at a time. :(

Should I try the Alternate install CD? I've read it needs less then 100 MB of RAM to run and install. Is it as easy to use as a normal LiveCD (in terms of setting up partitions for a dual boot)? Hopefully if everything runs perfectly I can get rid of Windows XP once and for all!

Edit: Finished burning the Xubuntu 9.10 LiveCD. Works perfectly in my Dad's PC. Tried it in my old PC with the same result; flashing white mouse in the middle of the screen. I've tried normal mode and safe graphics mode. The disc drive seems to have a lot of activity as it loads up the first menu with all the options. After I make my selection and it begins booting up there is CD drive activity, but after a minute or two the disc drive activity light stops flashing.

---

### Post by Powerman2442 on 2009-12-09
Bump - Anyone got anything? Should I try the Alternate CD or would I just be wasting another disc? Every disc that I've tried works perfectly fine in all of the other computers I've put them in. Obviously it has to be something hardware related with this particular PC. Maybe a BIOS update... if I can find one. This motherboard is fairly old so I don't know if I'd even be able to find any BIOS updates.

---

### Post by darkod on 2009-12-09
Alternate Install image does require less resources but the installer is text based, in other words no GUI during install. Depending if you plan to do manual partitioning it might be difficult dong it without GUI.
The end system will have GUI desktop, it's the installer that's text based. Also, during install watch out to select the desktop GUI if asked, not sure if it's a default choice on alternate install. Otherwise you might end up with text based system.
I also support the idea to try 9.10 xubuntu desktop. The alternate install would be the last option, especially if you want GUI during install.

---

### Post by Powerman2442 on 2009-12-16
> **darkod said:**
> Alternate Install image does require less resources but the installer is text based, in other words no GUI during install. Depending if you plan to do manual partitioning it might be difficult dong it without GUI.
The end system will have GUI desktop, it's the installer that's text based. Also, during install watch out to select the desktop GUI if asked, not sure if it's a default choice on alternate install. Otherwise you might end up with text based system.
I also support the idea to try 9.10 xubuntu desktop. The alternate install would be the last option, especially if you want GUI during install.

I've tried Xubuntu 9.10, like I said above, with the same result as everything else. Think I might try a way off distro, like SUSE, and see if it reacts the same. So far any distro based on Ubuntu has the same loading problems on this PC. All the LiveCDs work fine on my Dad's PC.

---

### Post by Bartender on 2009-12-16
I think you're going down the wrong path blaming the PC as such.  I've got an old PIII 600 MHz with 512 RAM that runs full Ubuntu fine.  Well, I should qualify that.  It's acceptable for most basic tasks, word processing and such, but excruciatingly slow in other areas.

I've got a basic HP inkjet that "just works" with Ubuntu.  If I plug it into a modern PC running Ubuntu and ask it to print a test page, it spits that page out pronto.  Plug that same printer into the PIII 600 and it prints one line of the test page every couple of minutes.  It might finish in a week.

So within limits, your PIII 500 should work.  

Definitely +1 on the alternate install CD, and I'm guessing that the optical drive in the old PC is worn out or dirty or the laser's just too weak.  If you're handy with such things (it's not hard) I'd try slipping a newer optical drive in and see if that makes a difference.

One more thing.  The standard Ubuntu installation uses about 300 to 350 MB RAM at idle.  So if you can get it installed, almost all your work will be done with Ubuntu dipping into swap a lot.  That's going to make things very slow.  More RAM would be a big improvement.

Or go to a very lightweight distro like Puppy or maybe Ubuntu running LXDE as the desktop environment.

---

### Post by presence1960 on 2009-12-16
Did you try hitting F4 at the boot menu and trying Safe Graphics mode? See here for more info: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If that or any of the F6 options do not work then I would advise the alternate text based installer.

For a very lightweight distro based on Ubuntu try Masonux. It uses the LXDE desktop. See here: [http://sites.google.com/site/masonux/home](http://sites.google.com/site/masonux/home)
Although my machine does not need lightweight distos or desktops I tried Masonux 9.04 because a community member (Earthpigg) was involved with it. It worked good for me.

---

### Post by Powerman2442 on 2009-12-24
> **Bartender said:**
> I think you're going down the wrong path blaming the PC as such.  I've got an old PIII 600 MHz with 512 RAM that runs full Ubuntu fine.  Well, I should qualify that.  It's acceptable for most basic tasks, word processing and such, but excruciatingly slow in other areas.

I've got a basic HP inkjet that "just works" with Ubuntu.  If I plug it into a modern PC running Ubuntu and ask it to print a test page, it spits that page out pronto.  Plug that same printer into the PIII 600 and it prints one line of the test page every couple of minutes.  It might finish in a week.

So within limits, your PIII 500 should work.  

Definitely +1 on the alternate install CD, and I'm guessing that the optical drive in the old PC is worn out or dirty or the laser's just too weak.  If you're handy with such things (it's not hard) I'd try slipping a newer optical drive in and see if that makes a difference.

One more thing.  The standard Ubuntu installation uses about 300 to 350 MB RAM at idle.  So if you can get it installed, almost all your work will be done with Ubuntu dipping into swap a lot.  That's going to make things very slow.  More RAM would be a big improvement.

Or go to a very lightweight distro like Puppy or maybe Ubuntu running LXDE as the desktop environment.

I'm blaming the PC because all of the LiveCDs work fine on my Dad's PC (which has an older optical drive then my old PC), and I’m sure the LiveCDs will work in other newer PCs. Also, I had to replace the old optical drive with a new one when I got the computer. Ordered the drive brand new from TigerDirect.

---

### Post by Powerman2442 on 2009-12-24
> **presence1960 said:**
> Did you try hitting F4 at the boot menu and trying Safe Graphics mode? See here for more info: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If that or any of the F6 options do not work then I would advise the alternate text based installer.

For a very lightweight distro based on Ubuntu try Masonux. It uses the LXDE desktop. See here: [http://sites.google.com/site/masonux/home](http://sites.google.com/site/masonux/home)
Although my machine does not need lightweight distos or desktops I tried Masonux 9.04 because a community member (Earthpigg) was involved with it. It worked good for me.

Yes, “Safe Graphics Mode” was the first thing I tried. I’ve also tried some of the other boot options, like “acpi=force”, etc.

I’ll check out that distro as well. However, I don’t think using a different distro (lightweight or not) will help my situation. I mean the LiveCD doesn’t even get past the loading screen. If it would get past the loading screen then crash while loading the desktop environment then I might consider switching to a distro with a different or more lightweight GUI.

---

### Post by Powerman2442 on 2009-12-24
Also I'd like to add that while loading these LiveCDs I get a message in white text similar to this

[   000000.0] BIOS AGE OLDER THEN 2000 (1999) ACPI=FORCE IS NEEDED TO ENABLE ACPI

Not exactly what is says but something to that effect pops up for a split second then the system hangs on the white Ubuntu logo in the middle of the screen.

---

### Post by bshosey on 2009-12-24
Press F6 it gives you a choice to install with out ACPI
ACPI=Off

---

### Post by Powerman2442 on 2009-12-24
> **bshosey said:**
> Press F6 it gives you a choice to install with out ACPI
ACPI=Off

What exactly is ACPI? When I boot with ACPI=Off the system hangs with a blinking white underscore in the top left hand corner. Of by the way. I am downloading the alternate CD now to see if that works.

Edit: Nevermind I Googled ACPI. Not sure why turning it off would make the system hang though. :S

---

### Post by lisati on 2009-12-24
> **Powerman2442 said:**
> What exactly is ACPI? When I boot with ACPI=Off the system hangs with a **blinking white underscore** in the top left hand corner. Of by the way. I am downloading the alternate CD now to see if that works.

Edit: Nevermind I Googled ACPI. Not sure why turning it off would make the system hang though. :S

<aside>FYI, it's called a "cursor"</aside>

---

### Post by Powerman2442 on 2009-12-24
> **lisati said:**
> <aside>FYI, it's called a "cursor"</aside>

NICE! My LiveCD works perfectly now that I've changed my mindset from a blinking white underscore (which is what it is if you want to get technical) to a cursor. Sarcasm aside... just finished burning the alternative CD and I'm going to try it now.

Edit: Okay the alternate CD ran fine and I installed 9.10 to my hard drive. It loads up the white Ubuntu logo that pulses in the middle of the screen for about 15 - 20 seconds. After that it disappears and a flashing "cursor" appears in the top left hand corner. Been sitting like that for at least 5 minutes now. What would cause the flashing cursor?

The main reason I wanted to get 9.10 installed was because someone told me that my wireless NIC would work out of the box with 9.10. However, during the installation when it tried to detect any network controllers it said that none were present. So my guess is my wireless NIC won&#8217;t work out of box with 9.10. If I can&#8217;t get any help and get 9.10 up and running I might just revert back to 8.04. 

This PC is so old when I got it all it had was a dial-up modem and there is no onboard Ethernet. I just ordered a cheap 10/100 NIC off of Ebay a few days ago so maybe I can use that to connect directly to my modem and try to get my wireless NIC up and running. Back when I had my laptop my Broadcom chipset wasn&#8217;t supported so I plugged it directly into the router and updated Ubuntu. Ubuntu found drivers for my chipset and from that point on I was able to connect via wireless. 

Also, heading to a Christmas Eve party so I probably won't be on to respond tonight. Don't expect on getting very many responses either, due to the season. :)

---

### Post by Powerman2442 on 2009-12-25
Okay, got 8.04 installed and almost everything appears to be working fine. As I said though the wireless NIC is not in working condition. The sad part is the box says it is compatible with Linux and they even have drivers on the CD. The company doesn't have any decent documentation on how to install the drivers in Linux and offers no support on their website, even though one of the major selling points is that it works with Windows, Mac, and Linux.

Hopefully the wired NIC works out of the box with Linux and I can get my wireless connection up and running.

**Update!** - Okay well like I said I wasn't able to get 9.10 to load up at all. However I did get 8.04 LTS installed and running. I received my Ethernet card in the mail and installed it. Hardy detected it right away and I was able to connect via Ethernet on my wireless game adapter. Still working on getting my wireless card up and running, but I consider this thread solved. Thanks to all who tried to help!

---

