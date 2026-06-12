---
title: "Installation probs. What does this mean?"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Orographic on 2010-03-23
My install of Lucid Lynx Beta 1 went fine until reboot:

I got this message:

'I/O error dev sr0 sector 457116' and a number of other numbers in that series 457xxx. 

And a 'broken pipe' message as I shutdown as well. 

Starting up Lucid takes about a minute with a FSCK at the beginning as well.

I got these same messages from three attempted installs of Beta 1, the last install was via a good quality CD where an MD5SUM was done.

I should add that Karmic is rock solid on this same machine.

My system:

Gigabyte 945GZM-S2 motherboard with integrated graphics
2G of DDR2 ram

---

### Post by VMC on 2010-03-23
Do you have a disk in your cdrom? If so remove it and see if those errors go away. Also, is this a SATA cdrom? There have been problems in the past using sata.

---

### Post by Orographic on 2010-03-23
Thanks for your help.

Yes, the CD is in the drive as it has just finished installing Lynx Beta 1, then those errors come up before I can remove the install CD for a reboot. 

Yes, it is a sata CD bay, the same one that has worked fine with Karmic and earlier Ubuntu versions.

---

### Post by VMC on 2010-03-23
Here's an [**_old_**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266951") bug report that someone just reported a very similar error message. You might have to open a new bug report, using "ubuntu-bug storage".

It may have worked on a previous release and it now could be something new. Maybe kernel related. I don't know.

---

### Post by Orographic on 2010-03-23
Thanks, I re-installed for the fourth time (I burn CDs at slowest speeds always) and got lots of errors after reboot again. And now wired ethernet isn't working either although it worked well during the install process.

Lucid is very buggy for me on a machine that runs Karmic so very well. I'm hoping these problems will be resolved by release or not long after.

Also, the video drivers for my onboard intel are far worse than in Karmic, very blocky video.

---

