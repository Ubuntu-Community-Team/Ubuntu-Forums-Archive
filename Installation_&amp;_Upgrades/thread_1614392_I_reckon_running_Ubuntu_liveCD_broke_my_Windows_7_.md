---
title: "I reckon running Ubuntu liveCD broke my Windows 7 installation"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by neil.scott on 2010-11-05
Hi folks. Please prove me wrong but I ran Ubuntu LiveCD 10.10 once, and since then I am having problems with my Windows 7 installation. I saw a thread which indicated this might once have happened in 2007 otherwise I would say it was illogical. The only other possibilty is one of the 4 Windows updates which happened at around the same time. I am looking into them also.

Computer: Sony Vaio VGN-Z21VN with Vista, Windows 7 and Presto installed.
I only wanted to boot once from the Ubuntu Live CD to prove it was bootable as I was about to install Ubuntu on a Netbook.
Since then Windows 7 take 10 minutes to boot. Looking in the event log tells me "problem communicating with a device" Status 0xc00000e9, and mentions \Dev\Ide\iastor0 which is something to do with the Intel AHCI controller. After that the system is unusable. It's not hardware as Vista boots fine after it has run CHKDISK to repair damage from the latest failed Windows 7 boot attempt. Does this indicate the AHCI driver is corrupt?

Any suggestions how to deal with this would be appreciated. I didn't have a restore point as Windows 7 was relatively new. I guess I will just need to do a fresh install.


Thanks.
Neil

---

### Post by Herman on 2010-11-05
It sounds like something is either missing or corrupted in your Windows installation and the file system check is almost fixing it for some reason isn't able to make the repair permanent.

The standard CHKDSK is only CHKDSK /F, which is quick but doesn't always fix everything. When CHKDSK /F doesn't fix your problem, try running a more thorough file system check, (CHKDSK /R).

In a running Windows system, go to 'My Computer', and right-click on Drive C, click on the 'Tools' tab, and schedule a file system check for next time you restart your computer, and make sure both check boxes are ticked for a thorough file system check, (in other words, get it to schedule a run of CHKDSK /R for you).

If you have your own Windows Installation DVD,  CHKDSK /R  can be run from a Windows Recovery Console in the DVD.
Sometimes it helps to run CHKDSK /R  two or three times in a row to make sure it really fixes everything.

---

### Post by Herman on 2010-11-05
If CHKDSK/R doesn't fix it, try looking in Device Manager for a 'banged out' driver, which is represented by a yellow and black symbol.
Try updating or re-installing the driver in question.
You may need to go to your motherboard manufacturer's website or to Windows Update to look for the driver(s) you need.

---

### Post by neil.scott on 2010-11-06
Thanks for the suggestions Herman.

It's starting to look like the drive is at fault. Vista is starting to play up too, similar symptoms. Makes a lot more sense than me accusing Ubuntu LiveCD of corrupting something.

I booted into Vista and ran chkdisk \R (or rather selected "Scan for and attempt recovery of bad sectors") on the W7 partition, it hung at "927 files processed".

I am going to look for some drive diagnostic tools. I will close this thread once I am sure it was nothing to do with Ubuntu and just co-incidence. Sorry about the false accusation!

Thanks.
Neil

---

### Post by coffeecat on 2010-11-06
> **neil.scott said:**
> I am going to look for some drive diagnostic tools.

There is one on the Ubuntu 10.10 live CD, if you don't mind risking booting up the live CD again! :wink:

Once in the live desktop, go to System > Administration > Disk Utility. Select the internal hard drive in the left pane and look for SMART test on the right. This should give you some indication of the health or otherwise of the drive. There's also an option to do a self-test but this might not be a good idea with a possibly failing drive.

---

### Post by neil.scott on 2010-11-06
As the Hitachi Drive Fitness Test fails to load I tried the Ubuntu diagnostics :-).

Live CD didn't work, presumably because it needs to write something to the broken disk?

Ubuntu Live on a USB stick did work.

However when I run the disk utility it says "SMART Status: Not supported", even though according to the doc. the Hitachi Travelstar 7K320 is a SMART drive.

Instead I ran the Read-only benchmark, which also failed with "error occurred while performing an operation", presumably another indication that the drive is on the blink.

Ran the "Check filesytem" in the Disk Utility which said it was clean, but it said so suspiciously quickly, instantaneously actually.

Will keept looking and trying.

Neil

---

### Post by Herman on 2010-11-06
:) It wouldn't be in Ubuntu's interest to make a Live CD that could   possibly cause any harm to people's computers and I don't think hardware   can be damaged by software since it's hardwired to only do what it can   safely do. The Ubuntu Live CD is designed to allow people to try out Ubuntu without  touching the hard disk or making any permanent changes to any other  part of the computer. 
When the computer is shut down and the CD is removed from the optical  drive, and the computers memory modules are empty the computer will be  in exactly the same state it was before. Of course, it is possible to use it to write changes to your hard disk if we want to do that, but there are warnings to make sure we know when we're about to do that.
We're all ears and keenly interested if you can find out otherwise, and  by trying you will be helping everyone, so you're welcome to try, nobody  here will object, especially as you seem to be remaining objective and  sticking to facts, and that's very decent of you, thank you for that.

Ubuntu's 'Disk Manager' is good, but the hard disk manufacturer's own specific diagnostic utility should be the most reliable and accurate you can get. It's a little suspicious if that doesn't work. I don't know if the CD for that needs to write anything to your hard disk. It should be initially at least, dealing with information stored in the hard disk's logs which are stored in the hard disk's flash memory chip. If you are trying to perform some kind test or scan on the hard disk's surface then it might need to write to some part of the hard disk, but I imagine and test like that would come with warnings if it might risk and of your data, as a write test likely would. 

You might need to enable the SMART capabilities of your hard disk drive to get access to the drive's logs. 

The file system check in ntfsprogs isn't yet effective for an NTFS file system. 
As far as I know. It simply places the 'dirty' flag in the file system to induce Windows to run a file system check the next time you boot Windows. :)

---

### Post by neil.scott on 2010-11-07
I set up another CHKDISK /R /F on reboot, it hung again. I´m pretty sure it is the disk. I don know what else could cause that behaviour. As it was happening in both Vista and W7 I conclude the driver is not corrupted.

I can´t explain why the Hitachi diagnostics won´t load.

I have reported it to Sony, it´s still under guarantee.

My apologies, it wasn´t Ubuntu, but one tends to look at the last thing one did as the culprit.

Thanks for the help Herman and coffeecat.

I will mark this thread as solved.

Bye for now, I´m going to try to get wireless working with Ubuntu on the HP Mini 1000 laptop so you might see me back here soon :-) though I see there´s a thread answering that problem already).
Neil

---

