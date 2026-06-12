---
title: "No luck installing Lubuntu on an Asus X55u"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by M_Mynaardt on 2013-06-30
Hi there!

I just bought an Asus X55u because it was a demo model on sale cheap.  I wanted to get rid of Windows 8 and install Lubuntu in its place.

HOWEVER, I cannot seem to install Lubuntu on it to save my life! The installer will not connect to my WiFi (home router) at all, unless I disable the password protection.  And even then, the GRUB won't install properly and the installer gives me a crash message at the end. The installer did manage to torch Windows 8, though.  Which means it's now a laptop bereft of any OS right now.

Has anyone had any success installing an Ubuntu-based distro on one of these ASUS X55U laptops?  I've tried 32 and 64 bit versions, they look okay, at first, but the actuall install always crashes at the end.

Near as I can tell part of the problem is that this laptop has one of those UEFI things instead of the usal BIOS.  You're supposed to be able to disable that UEFI (or whatever it's called) and have a regular BIOS instead, but I have no idea how to do that.

Anyway, if someone could tell me how one can go about installing Lubuntu (or Xubunut or Ubuntu) on this laptop, it would be much appreciated.

Thanks!

---

### Post by TenPlus1 on 2013-06-30
During boot press whatever key lets you into the bios (usually F2) and check around the settings until you find the EFI or UEFI section, from there disable and save bios then reboot and try installation again...  Also you could try Linux Mint 15 XFCE edition which comes with more network drivers for your wifi...

---

### Post by M_Mynaardt on 2013-06-30
> **TenPlus1 said:**
> During boot press whatever key lets you into the bios (usually F2) and check around the settings until you find the EFI or UEFI section, from there disable and save bios then reboot and try installation again...  Also you could try Linux Mint 15 XFCE edition which comes with more network drivers for your wifi...

Hi there...

I just had a look at the X55U BIOS menu and could find nothing that looked like a EFI or UEFI section; is it buried in there somewhere?

The various menus and such I found were:
[LIST]
[*]Main
[LIST]
[*]Date
[*]Time
[/LIST]

[*]Advanced
[LIST]
[*]Legacy usb support
[*]internal pointing device
[*]wake up lid open
[*]power off energy saving
[*]start easy flash
[LIST]
[*]This _might_ be it; was prompted to plug in AC power and got a message about "wont' permit flashing bios" and then prompted me for a file (that was not located) on my flash drive.  So, I couldn't really _do_ anything here either
[/LIST]

[*]asus usb charger +
[*]sata configure (AHCI or IDE)
[*]network stack (enabled/disabled)
[/LIST]

[*]Boot
[LIST]
[*]boot config; fast boot, launch csm
[*]boot option priorities (flash, dvd, or hdd)
[*]add new boot option
[*]delete boot option
[/LIST]

[*]security
[LIST]
[*]admin password
[*]user password
[*]i/o interface security (lock or unlock)
[*]secure boot controlled (disabled or enabled)
[/LIST]

[*]Save and Exit
[/LIST]

Any idea where in that mess I could find disable efi/uefi?  I couldn't find anything explicitly saying that in that list of stuff.  Closest I came to, I think, was the advanced/start-easy-flash bit, but I didn't get far with that either.

Thanks!

---

### Post by amjjawad on 2013-06-30
Hi,

Thank you for choosing Lubuntu!

I'd suggest to use Lubuntu 13.04 amd64 version - [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

And please, have a read: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Thank you!

P.S.
You did not mention which release of Lubuntu you have used.

---

### Post by oldfred on 2013-06-30
Some use the new name and do not reference that CSM is BIOS. May be BIOS/CSM/Legacy/AHCI or perhaps something else, but not UEFI or UEFI secure boot on.
 UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by M_Mynaardt on 2013-06-30
> **amjjawad said:**
> Hi,

Thank you for choosing Lubuntu!

I'd suggest to use Lubuntu 13.04 amd64 version - [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

And please, have a read: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Thank you!

P.S.
You did not mention which release of Lubuntu you have used.

Hi there!

I was trying to use Lubuntu 13.04 amd64; sorry I forgot to mention that.

I'll try it again and see if I can't disable that EFI (rubbish) properly; it's all new to me!  :confused:

I'll let you know what happens!

Thanks!

---

### Post by M_Mynaardt on 2013-06-30
> **oldfred said:**
> Some use the new name and do not reference that CSM is BIOS. May be BIOS/CSM/Legacy/AHCI or perhaps something else, but not UEFI or UEFI secure boot on.
 UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

Do you mean the UEFI/EFI thing might be caleld CSM, Legacy or AHCI in the bios menu thing?

Thanks!

---

### Post by M_Mynaardt on 2013-06-30
Still no luck!  :p

 I thought it was going to start from the live install on my flash drive.  As soon as the boot started, though, all I got was "empty security header" or some such message, and the booting process just stopped.

I did make a note of the BIOS information in the screen: Version 2.1.1277, 2012, by American Megatrends.  I don't know if that's any help or not.

---

### Post by oldfred on 2013-06-30
If it mentions security that sounds like UEFI as only UEFI has the secure boot mode. BIOS/CSM/Legacy does not have any secure boot mode and is just for compatibility to the older BIOS mode. 

Lots of info but longer.
 Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)

---

### Post by M_Mynaardt on 2013-06-30
HANG ON!

I _do_ have an ethernet connector on the side of this laptop!  I don't know what possessed me to think I did not!  ](*,)
Anyway, what self-respecting computer user would actually bother *reading the directions* that come with a computer, eh?

I also stumbled on this useful site; [http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html](http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html) which made it possible for me to easily boot up from a flash drive with out as much trouble...

I'll try an install again and see if I can get my s*** together here...

---

### Post by M_Mynaardt on 2013-06-30
Hi Again!

Okay... it's *sort of* working now.

First thing I did, per that [http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html](http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html) link was the following BIOS changes:
[LIST]
[*]Under the Boot section, I enabled "Launch CSM"
[*]Under Security, I disabled "Secure Boot Control
[/LIST]

Then I plugged it into my modem with an ethernet cable and all was well for the time being.  Everything is installed and all that fun stuff.

**However** the connection speed on the wireless on that computer is absolutely ***pa-thet-ic!***  The laptop has to basically be right beside a router to get a wifi signal.  And even then, the transfer rate is under 2 kB a second; usually a lot lower than that.  So, I tried to plug in a rocket stick (broadband wireless) connection on one of the USB ports.  Well, that wasn't a huge improvement.  While it did connect, the connection would inexplicably disconnect in less than three minutes, even when the signal was good and strong and transfer rates were quite good.

I'm guessing that there's a driver/hardware clash in that computer somewhere.  I didn't have any luck trying to find Linux drivers for it yet.  Does anyone know where I could find any?

Thanks!

---

### Post by M_Mynaardt on 2013-07-01
Right!  It's working proper!
:guitar:

My tech buddy popped by and had a look.  Turns out the network card wasn't agreeing with this laptop one little bit.  So, he swapped it with one he knew works well with Linux.  And ... voila!  It works properly now.

Thanks for all the patience, everyone!

---

### Post by amjjawad on 2013-07-01
I'm very glad it works now :)

Enjoy ;)

---

### Post by M_Mynaardt on 2013-07-01
> **amjjawad said:**
> I'm very glad it works now :)

Enjoy ;)

Thanks!

Good thing a buddy of mine is good with electronics; it was a simple fix once he figured it out.

---

