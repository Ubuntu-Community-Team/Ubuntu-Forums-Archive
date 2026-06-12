---
title: "Newbie -Install failures"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by grayeagle on 2008-09-13
Friend d/l'd Ubuntu 8.04 to Kingston flashdrive, mailed to me. Following instructions on the Ubuntu site, I used Infrarecorder to burn the image to a CD-R (Memorex), three separate times, speed set to 10x, verifying the burn with Ubuntu, twice for each burn. All presented zero errors. At least five install attempts, so far, to an AMD Athlon, 1.1mhz, 512 mb, AMIbios 7.0, in an older Gateway, ex-XP box. Set the first install attempt to "Guide" full Ubuntu partition for the disk, which presumably, cleaned out the XP install. First install was to default settings (hd0), following were changed to sda (as I recall) in the Advanced setting. 

Though Ubuntu runs apparently flawlessly from the CD (the first option on the intro screen), it will not install correctly. I've gotten a couple of 'clean the lens/replace the HD' messages ... and a couple of specific Open Office install failure notes. 

IF the CD/CD drive is at fault, why is it that the software runs so well from it? The hard drive and remainder of the hardware was working flawlessly in XP, till I started the first Linux install this morning. So unless the Ubuntu installer screwed up the HD, it ought to be okay. It is properly registered, along with the CD drive in the BIOS boot/status screens. 

The only thing I can think of, that's left, might be that the original download was corrupted. But, again, if that were true why is Ubuntu continuing to run perfectly from the CD. By the way, I've tried Open Office apps, and they run fine as well. Is there a way to do a belated checksum on the ISO file, as it was downloaded? 

I am super eager to move away from M.S. But, this has not been a very encouraging start, guys. 

Suggestions?  

gray

---

### Post by Pumalite on 2008-09-14
Download an iso from here:
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by wpshooter on 2008-09-14
I would first clean CD drive.

I would then check to make sure that FIRMWARE of CD drive is on the very latest available version.

I would the make sure that I checked the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu.

---

### Post by grayeagle on 2008-09-15
Guys:

Okay ... I solved my problem. 

And in so doing, have some thoughts to offer to the volunteers who help so much here. 

The problem I had turned out to be a batch of bad CDs. I narrowed it down to that because:
1) Contrary to kind 'suggestions' offered here, the CD drive was working just fine -- after posting my plea for help here last night, I ended up doing not one, but TWO separate Windows (ME, and XP) installs from the same CD drive I was using for the Ubuntu installs. 
2) The original download was *not* corrupted. Which I determing by using the checksum software recommended here on the Ubuntu website.
3) That left ONLY the CDs themselves. And, after opening a new package (Memorex CD-R's) of a 100, and pulling one from the cent, then re-burning the install ISO image, the install went perfectly. 

No one anywhere, could be more enthusiastic, or supportive of the Open Source/Ubuntu/Linux efforts, and all concerned. 

But, I wonder if it might not be a bit 'counter-productive' to continue to offer 711 Mb downloads to the public. Many, if not most, (though I know many have cable/broadband inet connections and can download that large a file easily) of us would be better served, and the Linux community, if the software was available only on 'hard copy' CDs etc. The installs and setups are problematical enough without, it seems to me, injecting another uncertainty in the equation. I know CDs are offered free, and sold for cost, but the download, 'quickfix' thing, is just too much of a temptation for most of us, and can lead to enormous variances, is a source of errors, and problems for new users ... and worst of all, can create a very bad image for Linux, in the long run--though Linux/Ubuntu is not at all at fault. 

Reading the posts here, it's clear that some pretty bad things are happening to folks wanting to, and trying to install Ubuntu. And those people, will be broadcasting to the world 'what a crappy piece of junk Linux is' ... etc. etc. They're even, some of them, saying that here. And, it could be nothing more than bad or cheap CDs ... not Ubuntu! To offer kinda 'canned', too simple responses may not be in the best interests of any of us wanting to see Linux really fly. I noticed users having install problems on brand new computers, were told to 'clean the CD lenses/drives' or that their hard drives might be failing. Believe me, I sincerely respect those experts who must be working tirelessly, around the clock almost, and who devote some of their precious time here trying to help us dummies ... but perhaps a bit more effort would be productive and beneficial for all of us, beyond put a new hard drive in and clean the 'old' CD lenses. That is absolutely *not* intended to sound catty or negative, guys. Just a gut instinct I have about all this.  

One last comment ... and a possible buggy report-ish, kind of thing. 

Over FIVE separate CD burns, with only the fifth one apparently being not corrupted ... Ubuntu reported ALL five of the CDs with "No Errors Found" There clearly were errors, corrupted data on the disks. During the aborted installs, the install ran for anything from about 15% to as high as 38% before various read, and disk errors occurred. I can't recall the exact wording, but all were related to the installer not being able to obtain data from the CD. So why didn't the 'CD Integrity Checker' report a faulty CD??

That's all. Am now going to get into Linux and enjoy working with it. 

Best to all
Gray

---

### Post by xap13 on 2008-09-15
nice work grayeagle...!  cool comments too...!

_pAx_

---

### Post by Pumalite on 2008-09-15
Change the burner first

---

