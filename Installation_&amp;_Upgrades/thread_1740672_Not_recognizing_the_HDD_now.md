---
title: "Not recognizing the HDD now"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by coreytrice on 2011-04-27
I am very new to Ubuntu and any help would be greatly appreciated.

So the other day I was trying to install Ubuntu 10.10 on my wife's netbook and that went horribly wrong. I tried several different things and no joy. I eventually got the netbook to the point that it would only boot to a black screen with a white cursor and I could not do anything else. So, I ordered a USB to SATA cable and took the drive out of the netbook. Then last night I used my Ubuntu 10.04 desktop to install Ubuntu 10.04 from a LiveCD onto the netbook HDD connected with the USB to SATA cable. That worked like a charm and I've got the netbook back together and working great.

One small issue with the netbook is that it has a floppy drive in the list of system resources and I cannot get rid of it. It does not seem to matter that it is there, I just wanted to get rid of it since there is no floppy on the netbook, obviously. It must have set it up from being connected to the desktop.

The real issue is that now the desktop will not boot. In the BIOS it does not even recognize the hard drives that are in the machine. There is an 80Gb drive with Ubuntu on it and there is a 20Gb drive with nothing but files as a backup. I booted from a LiveCD and thought that I could just use GParted to format the main drive and start over. GParted does not recognize the drive either.

Please help...

---

### Post by psusi on 2011-04-27
As for the floppy; you need to go into the bios and tell it you don't have one.

As for the missing hard disk; it sounds like it has gone to the great scrap heap in the sky.

---

### Post by dabl on 2011-04-27
> **coreytrice said:**
> 

 In the BIOS it does not even recognize the hard drives that are in the machine. There is an 80Gb drive with Ubuntu on it and there is a 20Gb drive with nothing but files as a backup. I booted from a LiveCD and thought that I could just use GParted to format the main drive and start over. GParted does not recognize the drive either.

Please help...

If the BIOS sees no hard drive(s), then Ubuntu won't either -- Linux gets its information about internal storage devices from BIOS.

BTW, Ubuntu has no ability to change the BIOS, so something else has been going on there.  Among other possibilities, you might want to check the CMOS battery.

---

### Post by psusi on 2011-04-27
> **dabl said:**
> If the BIOS sees no hard drive(s), then Ubuntu won't either -- Linux gets its information about internal storage devices from BIOS.


This is not true: Linux talks to the hardware directly so the bios does not matter.  There is hardware out there that the bios can not recognize but Linux will, but in this case, if neither sees it, it is probably because it is dead.

---

### Post by dabl on 2011-04-27
> **psusi said:**
> 
  There is hardware out there that the bios can not recognize but Linux will



OK -- I'll have to take your word for that, as I have not personally encountered an example of such a BIOS/hdd combo.  :)

I have encountered the converse -- hdd looks good to go in BIOS, but Linux (or a Linux installer like Ubiquity) can't see it.  That situation can usually be overcome by twiddling the SATA channel mode setting.

---

### Post by coreytrice on 2011-04-27
I figured it out. There must have been something corrupted on the drive from the install to the netbook drive. I pulled the drive and formatted it and reinstalled Ubuntu 10.04 and now it works. 

That was strange, but my new toy (USB to SATA/IDE cable $7 amazon.com) let me hook the drive up to my Mac and I used Disk Utility to format it. Once that was done I popped the drive back into the machine and then the BIOS recognized both drives (primary that I just formatted and the secondary that is just file storage for just such a case). I was then able to reinstall from the LiveCD.

Thanks for the suggestions everyone!

---

