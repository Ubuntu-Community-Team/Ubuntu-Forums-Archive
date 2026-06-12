---
title: "Netbook remix freezes during install"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by pillar007 on 2009-11-23
I have been trying to install netbook remix for a while now.  Usually it freezes during the partition screen or right before that with the gray unbuntu logo.

It will boot into the live CD 90% of the time.

Here is what I have tried:

[LIST]
[*]format hard drive with gpart
[*]delete all partitions with disk manager
[*]install with USB (used unetbootin)
[*]OEM install
[*]install from live CD after booting into ubuntu
[/LIST]

None of these things worked.  Can anyone help me?

---

### Post by snowpine on 2009-11-23
Hi Pillar,

Welcome to the forums!

Two recommendations:

1) We can't guess which hardware you're using... what kind of netbook do you have?
2) Your "Here is what I have tried" does not match the official instructions for installing Ubuntu Netbook Remix, so I am not surprised it's not working. [Please follow these steps]("http://www.ubuntu.com/getubuntu/download-netbook") and report back with any errors. Good luck!

---

### Post by julianb on 2009-11-23
If you have less than 384MB of RAM, then you probably just don't have enough memory to install the standard way. 

That would mean it's still possible to install the netbook remix IF you start with an Ubuntu minimal install and then find out what packages need to be added to set your system up as Ubuntu Netbook Remix. This shouldn't be hard to figure out but you'll have to use apt-get or aptitude on the command line. 

(you'd use the "CLI" option from an ubuntu minimal CD image; you may do this off of a USB that you can make with uNetBootin)

Even if your problem is something other than lack of memory, this method might sidestep the problem you are getting. (especially if your machine has already proven itself capable of running a standard Ubuntu). 

If you've never used Ubuntu 9.10 before on that machine, it seems possible that your hardware doesn't get along with 9.10. Consider using 9.04, which is a great piece of software.

---

### Post by snowpine on 2009-11-23
Please don't use Unetbootin; it is not part of the Ubuntu project and can be very flaky. Use the [official instructions]("https://help.ubuntu.com/community/Installation/FromUSBStick") and you'll be fine. 

If you're still having problems, I also reccommend [checking the integrity]("https://help.ubuntu.com/community/HowToMD5SUM") to rule out any errors in Ubuntu .iso itself.

Julianb has an interesting theory about low-memory systems, however, I can't think of any netbooks with less than 384mb of ram (even the original Asus eee had 512mb). But again, you will get better advice if you tell us which hardware you're using rather than letting us speculate. :)

---

### Post by pillar007 on 2009-11-23
I was under the impression that using the burned ISO in an external drive was ok too.  I will try the recommended way.

My hardware is an EEE 701 8G with 1 gb of ram.

I should also note that I had ubuntu 9.04 (non-netbook) installed on it and it worked OK, but had some issues with the sound drivers.  Using netbook remix as live CD proved that the sound will work so that is what prompted me to install it.

---

### Post by snowpine on 2009-11-23
[According to the wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20701-SD%20/%20702"), your Asus eee 701 is fairly well supported by Ubuntu, apart from some minor issues that are mostly due to the screen size.

Good luck!

---

### Post by pillar007 on 2009-11-23
I am a little confused by these instructions.  I am trying to use the usb-creator.exe to make a bootable usb stick but "make startup disk" is faded out.

When I click Other... i select the ISO but nothing happens.

Thanks

Edit:  I restarted it and it seems to be working.  Sorry about the linux n00biness.

---

### Post by snowpine on 2009-11-23
> **pillar007 said:**
> I am a little confused by these instructions.  I am trying to use the usb-creator.exe to make a bootable usb stick but "make startup disk" is faded out.

When I click Other... i select the ISO but nothing happens.

Thanks

Edit:  I restarted it and it seems to be working.  Sorry about the linux n00biness.

Hmmm, looking at the instructions, it appears they have changed significantly since I last installed Ubuntu Netbook Remix (9.04). I am sorry I can't be of further assistance with the new method; I've not personally used it. :(

---

### Post by pillar007 on 2009-11-23
It seemed to be working, but now it is frozen on "starting up the partitioner" at 70%.

---

### Post by snowpine on 2009-11-23
It really sounds like a "bad burn" to me... is there a "Check Disk Integrity" option when you first boot from the Live CD or USB?

---

### Post by pillar007 on 2009-11-23
Yes, that option is present.  I tried it but it jammed up (when I was using the CD) now that I am using the USB i haven't tried it yet.

Edit: it made it furthest yet when I tried to install it last time, and generated the error "the attempt to mount a file system with type ext4 in SCSI2 (0,0,0), partition #1 (sda) at / failed."

Note that I tried the manual partition option to see if that would work and am not 100% sure if the settings I choose are correct.

---

### Post by snowpine on 2009-11-23
If the CD/USB will not pass the integrity check, it is corrupt and cannot be used to install a working system.

You need to re-download the image (bit torrent is more reliable than a regular direct download), burn a new CD (or USB), and check its integrity.

---

### Post by pillar007 on 2009-11-23
I just ran the check and there were no errors.

---

### Post by snowpine on 2009-11-23
> **pillar007 said:**
> I just ran the check and there were no errors.

That is good news! But unfortunately it also means I am out of suggestions. Hopefully another user with actual experience with UNR 9.10 and/or the EEE 701 can take over. Good luck!

---

### Post by pillar007 on 2009-11-23
> **snowpine said:**
> That is good news! But unfortunately it also means I am out of suggestions. Hopefully another user with actual experience with UNR 9.10 and/or the EEE 701 can take over. Good luck!

I hope so.  If I can't make it work then I will have to go crawling back to Microsoft.

---

### Post by snowpine on 2009-11-23
> **pillar007 said:**
> I hope so.  If I can't make it work then I will have to go crawling back to Microsoft.

Not exactly; if you can't get Ubuntu Netbook Remix working (for whatever reason), there's still: Ubuntu, Xubuntu, Kubuntu, Debian, Mandriva, Fedora, OpenSUSE etc. etc. etc. There are also many EEE-specific distros, like Easy Peasy, EEEbuntu, EEEdora, etc. (though I personally do not recommend them) :)

You might also look for answers on [these excellent forums]("http://forum.eeeuser.com/").

Good luck and sorry I wasn't able to come up with a solution.

---

### Post by pillar007 on 2009-11-23
Thanks for your help!

May I ask why you don't recommend those eee specific distros?

---

### Post by snowpine on 2009-11-23
> **pillar007 said:**
> Thanks for your help!

May I ask why you don't recommend those eee specific distros?

That is an excellent question!

My answer is twofold:

1) The main "claim to fame" for most netbook-specifc distros is that they support all the eee hardware "out of the box." But, once you learn about your hardware (I know that my Dell Mini requires the Broadcom STA driver), you can make any Linux distro work on your netbook. Then, you can choose the distro on other factors (do I like the user interface? is the software up to date? is it stable? is the community large and friendly?).

2) Most of the eee-distros are small (often one person) "labors of love". These projects sometimes fizzle out, or take unexpected twists (eeebuntu is switching from Ubuntu to Debian Testing for example). Or maybe a new model of EEE comes on the market... will an updated version come out to support it? Sticking with one of the major distros (like Ubuntu) means a bigger community and more support over the long haul.

Just my personal opinions, of course. :) Full disclosure: my EEE 900ha is currently running Fedora, and my Dell Mini's running Arch.

---

### Post by pillar007 on 2009-11-23
I did some googling and found this thread: [http://forum.eeeuser.com/viewtopic.php?id=79468](http://forum.eeeuser.com/viewtopic.php?id=79468)

he says that he had to do something to make it work...i don't know what he is referring to, do you?

---

### Post by pillar007 on 2009-11-23
I thought i found a solution.  I left about 256 MB of unallocated space before the partition for uBuntu...it mounted correctly but then crashed right at 99%, giving a fatal grub error.

Is there a way for me to salvage it?  The OS is installed, I just need to have grub configured properly so it boots.

---

