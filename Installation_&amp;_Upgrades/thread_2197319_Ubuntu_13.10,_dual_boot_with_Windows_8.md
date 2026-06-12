---
title: "Ubuntu 13.10, dual boot with Windows 8"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by shubham.twit189 on 2014-01-03
Hey Everyone,
I am new to Linux and I tried to install Ubuntu 13.10 Desktop version on my laptop.

My laptop config are 
Core i7 4700mq
12 GB DDR3
GTX 765m
120GB SSD + 1 TB HDD

Currently I am using Windows 8 and I want to dual boot it with Ubuntu 13.10

So I downloaded the amd64 version iso file from the main site and used the Universal USB Installer to make a bootable USB stick.
Everything worked so far and I was able to boot via my USB
But after the "Ubuntu" Logo I got an error. I cant do anything after that. I am just stuck there. No keys work there and I have to press the power key to shut off the computer.
Now I have tried 20 times but I get the same thing.
I put it again and again freshly but still the same error.

What am I doing wrong here?
Can you please guide me how to properly install this OS on my laptop.

P.S. The image is the error I am getting.

---

### Post by shubham.twit189 on 2014-01-05
Bump

---

### Post by Bucky Ball on 2014-01-05
You won't get much help with that attitude. Forum users are all volunteers and under no obligation to help, but quite apart from that, people come here for the specific purposes of helping others and being helped themselves. If you have received no help to this point it would be because no one has anything to say or any help to give. 

My guess is that, seeing as it's Win8, you have problems with EFI. If you have a pre-installed Win8 then it is installed with EFI and probably with secureboot set. It is a Microsoft thing. If this is the case you need to install Ubuntu in EFI mode also. 

I'm no expert on this so perhaps you will get lucky and someone will jump in who knows about these things (EFI is new and there aren't a lot of experts).

Next time you want to bump your thread (after twenty four hours) simply post 'bump' to get it to the top of the list again rather than throwing in ill-informed assumptions about the forum community (and what could be considered 'flame-bait'). You've got a much better chance of getting support that way. 

Thanks and good luck.

PS: To date, 110 users have looked at this thread and the ONLY reason you haven't yet had a post would be because they can't help you. The forums are free, users and staff are voluntary, this is not paid support. ;)

---

### Post by ubfan1 on 2014-01-05
Could be a video problem.  You can try some options on the grub boot:

For UEFI machines (with a black screen grub (grub-efi)  without any function key options, like the older grub-pc, edit the grub menu and add the below options on the "linux" line, then boot with F10 or ctrl-X.


Options for Video problems:

nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic
i915.i915_enable_rc6=1
video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

To allow Nvidia hybrid machines to boot.
nouveau.blacklist=1

To slow SSDs to allow them to boot:
libata.force=noncq

---

### Post by shubham.twit189 on 2014-01-06
> **Bucky Ball said:**
> You won't get much help with that attitude. Forum users are all volunteers and under no obligation to help, but quite apart from that, people come here for the specific purposes of helping others and being helped themselves. If you have received no help to this point it would be because no one has anything to say or any help to give. 

My guess is that, seeing as it's Win8, you have problems with EFI. If you have a pre-installed Win8 then it is installed with EFI and probably with secureboot set. It is a Microsoft thing. If this is the case you need to install Ubuntu in EFI mode also. 

I'm no expert on this so perhaps you will get lucky and someone will jump in who knows about these things (EFI is new and there aren't a lot of experts).

Next time you want to bump your thread (after twenty four hours) simply post 'bump' to get it to the top of the list again rather than throwing in ill-informed assumptions about the forum community (and what could be considered 'flame-bait'). You've got a much better chance of getting support that way. 

Thanks and good luck.

PS: To date, 110 users have looked at this thread and the ONLY reason you haven't yet had a post would be because they can't help you. The forums are free, users and staff are voluntary, this is not paid support. ;)


Uhm Ok
Its true that it was my fault and I shouldnt have said it like that. So for that I apologize to the whole community.
And next time I will remember that "bump" thingy ... :p


> Could be a video problem. You can try some options on the grub boot:

For UEFI machines (with a black screen grub (grub-efi) without any function key options, like the older grub-pc, edit the grub menu and add the below options on the "linux" line, then boot with F10 or ctrl-X.




Options for Video problems:


nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic
i915.i915_enable_rc6=1
video=1280x1024-24@60
video=VGA-1:1280x1024-24@60


To allow Nvidia hybrid machines to boot.
nouveau.blacklist=1


To slow SSDs to allow them to boot:
libata.force=noncq

Hey ubfan1
Thank you for giving me all this but as I am new to coding and stuffs and totally a noob..how to use that what you have told?
How can I edit the grub menu? What is grub and where can I find all that?

---

### Post by oldfred on 2014-01-06
Nomodeset is one boot option, this shows how to add it for BIOS (purple screen) and grub menu whether first boot after install or UEFI boot. Basically at grub menu you press e for edit, scroll to linux line and replace quiet splash with one or more boot options.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ubfan1 on 2014-01-06
The grub menu screen is the screen with the choice of "Try" or "Install" on it.  At the bottom you should see instructions for editing, booting etc. If the screen is black, that's the grub for uefi, which is your situation.  A purple grub screen is the older one, but it has the capability of setting some of the options from function keys.  The uefi screen has no such capability, so you have to edit the grub selection (type e to edit, then use arrow keys to move), adding the selection option(s) to the line starting with "linux".  Usually, adding the options at the "splash" word near the end of the line is OK.  
  Your machine has a new CPU, SSD, and Nvidia GTX video, so you may need several options.  Start with the video, just add one option at a time until things improve, then try the next thing which seems to be broken.  I suggested video because I saw "noveau" in your screen dump and that's a video driver.  Since I have none of your equipment, I cannot offer suggestions from direct experience, but you can search this site for a lot of applicable info.

---

### Post by shubham.twit189 on 2014-01-07
> [COLOR=#000000]Nomodeset is one boot option, this shows how to add it for BIOS (purple screen) and grub menu whether first boot after install or UEFI boot. Basically at grub menu you press e for edit, scroll to linux line and replace quiet splash with one or more boot options.[/COLOR]

[COLOR=#000000]How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) [/COLOR]
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Hey oldfred
Thank you for the links. I will try it now.



> **ubfan1 said:**
> The grub menu screen is the screen with the choice of "Try" or "Install" on it.  At the bottom you should see instructions for editing, booting etc. If the screen is black, that's the grub for uefi, which is your situation.  A purple grub screen is the older one, but it has the capability of setting some of the options from function keys.  The uefi screen has no such capability, so you have to edit the grub selection (type e to edit, then use arrow keys to move), adding the selection option(s) to the line starting with "linux".  Usually, adding the options at the "splash" word near the end of the line is OK.  
  Your machine has a new CPU, SSD, and Nvidia GTX video, so you may need several options.  Start with the video, just add one option at a time until things improve, then try the next thing which seems to be broken.  I suggested video because I saw "noveau" in your screen dump and that's a video driver.  Since I have none of your equipment, I cannot offer suggestions from direct experience, but you can search this site for a lot of applicable info.

Hey ubfan1
Thank you for the explanation. Now I know what grub means.
But there is one thing I can't understand. You said 
"adding the selection option(s) to the line starting with "linux". Usually, adding the options at the "splash" word near the end of the line is OK. "

What does this means?
Can you please please explain this.

And thank you for helping me out till now.
All of you. :D

---

### Post by oldfred on 2014-01-07
ubfan's instructions and mine are really the same. 
I suggest replacing quiet splash in linux boot line as that hides boot process. When debugging I like to see boot process, as maybe it shows warnings or errors, but can go by fast. 
ubfan just adds options next to quiet splash so boot process is still hidden.

Each time you boot you have to reedit boot stanza until you find correct parameters or install a proprietary video driver. You can make boot parameter permanent after you know what you need.

Links posted show both BIOS and a grub menu screen on where to add options like nomodeset (or others).

---

