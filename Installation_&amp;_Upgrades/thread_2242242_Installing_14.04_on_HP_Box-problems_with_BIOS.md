---
title: "Installing 14.04 on HP Box-problems with BIOS?"
date: 2014-08-31
forum: Installation &amp; Upgrades
---

### Post by mark allyn on 2014-08-31
Hello everyone,

I realized too late that this is probably the correct forum for my issue, and not "general help".  I hope I haven't violated a UBUNTU behavior code.  

Here's my story.  I installed 14.04 on an HP box originally having Win 7 as the OS.  The installation was from a CD/ROM and proceeded smoothly.  However, when I attempt to boot up I wait for exactly 10 minutes before the screen comes up.  Once up, everything functions properly.  However, if I attempt to suspend the system, it suspends more or less permanently.

I took a look at /var/log/syslog and discovered that there were errors right off the bat with APCI BOS command.  There were others as well, but I'm guessing that these are sequelae of the original BIOS problem.  After doing a lshw command I discovered that the BIOS dates back to 2008 (It's manufacturer is HP).  So, here are several questions that I need to resolve or I will revert back to 12.04.

1.  Is the BIOS actually the reason I'm having problems?  If so, is there something I can do with GRUB 2.0 to avoid the problem.  One site I visited suggested that APCI=off as a GRUB option might work.  I've tried this and not been successful, but then I might have done the GRUB editing incorrectly.
2.  If the BIOS is the problem and there is no GRUB solution, how do I upgrade to a more recent BIOS version?  In researching this one, I have come to discover that HP only supports upgrading via windows.  I don't have windows on this machine.  Further research shows that Freedos might work, but I'm not comfortable with fooling around with the BIOS without a good straightforward guide.
3.  Is there a list of BIOS requirements that 14.04 must satisfy?  I've hunted for one, but not found it.

I don't want to go back to 12.04, but it may come to pass that I either do that, and/or buy a new machine with a newer bios.  But, which one?  That is why I'm asking question 3 above.

Thanks for any help you folks can provide.

Regards.

Mark Allyn

---

### Post by ubfan1 on 2014-08-31
1) Probably not a BIOS problem, but if you can figure out how to update, I'd advise it.  Read the BIOS release notes to see if anything giving you problems has been addressed, like fan control, etc.
2)Yup, HP's windows exes are a pain.  I have heard that you can get a usb or CD windows to boot, but don't know any details.  From that, you should be able to run the update.
3)None that I know of.  Long delays might indicate wireless timeouts.  Ever try booting with some F6 options from the boot screen?  If you have nvidia video, I'd use nomodeset.  
I'm running a much older HP (orig XP), so you machine should work once you figure out the boot options.

---

### Post by mark allyn on 2014-09-01
Hi Ubfan1 and anyone else,

1.  You indicate that you don't think the problem is due to outdated BIOS.  Could you say more about why you think it's something else other than stale BIOS.

2.  I'm game to trying to update the BIOS despite HP's unwillingness to help.  Somewhere I ran across a UBUNTU tech note that suggested Freedos was a way to do this.  I've had no experience with Freedos. ** Can someone else give me some guidance on how to do this based on their experience?**

3.  The F6 option.  Nvidia doesn't show up after issuing sudo lshw.  Almost the entire ensemble of hardware is Intel.  Only the hard drive (Western Digital) seems to be OEM device.  

Thanks for your help.

Mrk

---

### Post by ubfan1 on 2014-09-01
1)The few basic BIOS functions used by Linux typically aren't the ones broken which the vendor needs to fix with updates.  
2)DOS is not Windows.  If you have a Windows executable (like HP supplies), then you cannot run it under DOS.
There might be some way to use other flashing tools with some extracted part of the .exe, but that's too chancy for me.

---

### Post by mark allyn on 2014-09-01
Hi Ubfan,

Thanks for hanging on this thread.  

Thanks also for the info on the BIOS.  In a way, I suppose, it indirectly indicates why discussions of upgrades to UBUNTU don't seem to mention BIOS upgrades very often...none in my limited experience.

So something else is amiss...

I don't have a Windows executable on this machine.  I wish I did.  But, if the BIOS isn't the problem, then it doesn't matter.   

Regards,
Mark

---

### Post by d-cosner on 2014-09-01
I have a Compaq Presario SR5410F desktop PC, it was also made in 2008. I tried updating the BIOS with the instructions provided by HP with this result.

```

HP Update Error: Your system does not meet the minimum requirements for this update. Update has been canceled (9998)
```

I installed Windows Vista and tried the update following HP's instructions. I installed all of the Windows updates, HP drivers and tried the install as administrator. I spent hours trying to figure out what was wrong. I wanted the most recent BIOS update to fix a thermal issue, my processor fan runs full speed all the time... I searched and found others with the same issue but no solution.

I finally gave up and plugged my hard drive with Ubuntu 14.04 back in. I ordered a quiet, long life processor fan and called it a day. HP's method of updating the BIOS is the worst I have ever seen! I have updated the BIOS on plenty of computers and have never had a problem. 

Here is the help page from HP.

[http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01504950](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01504950)

My system met the requirements as far as I can tell. I have version 5.01 and the update is 5.22, so it was not a matter of my system not needing the update either. 

You can not use DOS, you have to have the supported version of Windows installed.

---

### Post by mark allyn on 2014-09-02
Good morning d-cosner,

Your saga is exactly what I fear and wish to avoid.  You never really say, but did you ever get the update accomplished?  Was the fan sufficient to do the job?

Just a small technical point.  According to sudo lshw the version of HP's BIOS installed on my HP Microtower is version: 786F2 v01.53 and it was installed in 2008. You mention versions 5.01 and 5.22.  These numbers look quite different.  Do you know why?

So, as a veteran of the update wars, what would you recommend?  Get a new box?  Grin and bear it for 10 minutes?  Perhaps it isn't a BIOS problem (although I get three ACPI error messages--they may be errors but they may not be the problem).

Lastly, thanks for the tip on DOS.  The Ubuntu tech page to which I alluded makes it appear that installing Freedos and using it to run a HP .exe to do the installation would work.  

Regards,
Mark Allyn

---

