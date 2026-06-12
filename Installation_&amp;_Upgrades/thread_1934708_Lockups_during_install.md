---
title: "Lockups during install"
date: 2012-03-02
forum: Installation &amp; Upgrades
---

### Post by nilism on 2012-03-02
SO I have been trying to install ubuntu on one of my spare comps for the last day or two.  I seem to be getting lock-ups during formatting.

I am running a Live USB stick with a couple of gigs of persistence.  The live version of ubuntu seems to run pretty good.  I get lag and such during any read/write ops but I think that is to be expected. 

The version I am running is 11.10, gnome GUI, ubiquity installer.

The system has been stripped of most of the extra hardware.  This is the current setup:
AMD x2 64 bit dual core at 2.0 GHz
2 GB ram, memtest86 approved (o:
A8V-MX mobo with onboard video and sound (default settings)
80 GB maxtor HDD via IDE interface
OCZ 580 W PS
Dlink Xtreme N wifi (comp is too far from router to run lan)

Here is the syslog from the last attempt, starting from the launch of ubiquity. [http://pastebin.com/Ape4sUGW](http://pastebin.com/Ape4sUGW)

The lockup for that run occurred about 30% into formatting SDA1 with the ext4 fs. The lockup always happens around formatting and requires a hardboot as the system becomes totally un-responsive.

Lastly, I am 100% new to linux, so explain things like I am retarded please.

---

### Post by LinuxFan999 on 2012-03-02
> **nilism said:**
> SO I have been trying to install ubuntu on one of my spare comps for the last day or two.  I seem to be getting lock-ups during formatting.

I am running a Live USB stick with a couple of gigs of persistence.  The live version of ubuntu seems to run pretty good.  I get lag and such during any read/write ops but I think that is to be expected. 

The version I am running is 11.10, gnome GUI, ubiquity installer.

The system has been stripped of most of the extra hardware.  This is the current setup:
AMD x2 64 bit dual core at 2.0 GHz
2 GB ram, memtest86 approved (o:
A8V-MX mobo with onboard video and sound (default settings)
80 GB maxtor HDD via IDE interface
OCZ 580 W PS
Dlink Xtreme N wifi (comp is too far from router to run lan)

Here is the syslog from the last attempt, starting from the launch of ubiquity. [http://pastebin.com/Ape4sUGW](http://pastebin.com/Ape4sUGW)

**The lockup for that run occurred about 30% into formatting SDA1 with the ext4 fs.** The lockup always happens around formatting and requires a hardboot as the system becomes totally un-responsive.

Lastly, I am 100% new to linux, so explain things like I am retarded please.
I think Your computer's hard drive may be failing (Maxtors were not the most reliable drives). You should look at the SMART status of the Hard Drive. To do this, boot from the Live CD and select "Try Ubuntu" on the window that pops up. Once the desktop apears, open the dash and type "Disk Utility". Open the Disk Utility, select the Hard Drive, then select the button that says "SMART data". Look at the bad sector count, the self assessment and the overall assessment. If the bad sector count is high, or The self assessment says "Fail" or the overall assessment says "Failure is imminent", the Hard Drive is failing and will need to be replaced. Please upload a screenshot of the SMART status window if possible (press alt-printscreen, and save the screenshot to a USB flash drive, then upload it on a working computer).

---

### Post by nilism on 2012-03-02
Yes Maxtor drives are garbage!  I ended up with a couple when WD was having shortage issues (pre SSD). 

Ok, so I had a look at it.  The disk reports healthy.  I am going to run an extensive self test and post back.  Previously this system was running winXP. The only issues I had then was the video card crapped out, other then that it's been very stable in that environment.

---

### Post by nilism on 2012-03-03
OK, so I ran a few of the self tests.  None of them completed, they just sort of stalled out, no errors were thrown and yet the tests weren't completing.  SMART still reported all was well but this was enough to convince me to try new hardware. 

I bought the mobo at a time a lot of tech was changing, so it has a few redundancies.  Since the HDD's were on IDE I decided to upgrade to the SATA II interface and buy an SSD (since they are cheaper right now).

The install carried on flawlessly after this $60 upgrade, a fair trade I think.

I am not exactly sure if the issue was in the IDE controller, the cabling or the HDD....  but somewhere along that path.

I have a few other minor issues.  Using onboard VGA right now since the older AGP video card is also fried.  For some reason ubuntu pushes the onboard graphics to native display resolution, which it probably shouldn't in this case(1080p).  So I think I am getting lag and stalling a bit from the over taxed video.  I have ordered a new PCI express card though.

I also have a grounding issue to sort through...  but that's not linux related at all.  =p 

Cheers

---

