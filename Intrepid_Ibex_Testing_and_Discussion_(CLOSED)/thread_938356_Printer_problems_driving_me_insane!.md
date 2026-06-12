---
title: "Printer problems driving me insane!"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2008-10-04
Well, not really. I was already insane! And this is on a test partition anyway so all I have to do is restart and get back into Hardy to do my work.

But I've had my Deskjet 5440 working out-of-box in both Gutsy and Hardy, and when I first installed Intrepid it worked! I even praised the HPLIP face-lift!

Then it started printing gibberish. I removed hplip and got it working through cups - then it didn't:confused:

So I reinstalled hplip and it just prints random crap!

My point is to find out if this is something that others are experiencing, or if I've just hosed something.

The printer still works perfectly in Hardy.

---

### Post by rbmorse on 2008-10-04
Here is a science project, if you want to experiment a bit. This is based on my experience with an HP 2605DN.

From your hardy installation, copy the file /etc/cups/ppd/*nameof driverfile.ppd* to the corresponding location in your Intrepid installation, thereby replacing the file installed by Intrepid.

Restart the CUPS system by opening a terminal and entering:

sudo /etc/init.d/cups restart<enter>

then test the printer.

---

### Post by Nullack on 2008-10-05
You could consider engaging in bug work and further diagnosing the issue. This would be preferable to coming up with a hack that puts back old revision of configuration items as fixing it in Ubuntu would help everyone :) Have a look on the Ubuntu wiki about diagnosing printing problems.

---

### Post by rbmorse on 2008-10-05
Have a look at bug 277404

Different model printer, though, and I thought I would see if it really is the same problem before adding it to launchpad.

Besides, what's wrong with offering a work-around that might get the OP printing until the bug is formally resolved?

---

### Post by kansasnoob on 2008-10-05
> **rbmorse said:**
> Here is a science project, if you want to experiment a bit. This is based on my experience with an HP 2605DN.

From your hardy installation, copy the file /etc/cups/ppd/*nameof driverfile.ppd* to the corresponding location in your Intrepid installation, thereby replacing the file installed by Intrepid.

Restart the CUPS system by opening a terminal and entering:

sudo /etc/init.d/cups restart<enter>

then test the printer.

Just got back to this.

That worked!

Now, I'm not ready to report this as a bug. Why? Well I was just fiddling around on a test hard drive and did an upgrade from 8.04, all went well and the printer just worked!

I'll soon try a fresh install and see if the situation persists. If so then I'll report it as a bug.

In the meanwhile I'm fiddling with dual-boot scenarios with Fedora which really drives me insane!

---

### Post by rbmorse on 2008-10-05
I've already opened the problem as bug 277404, but if you think it warranted I'd appreciate it if you could add a comment confirming the problem and listing your printer model as affected as well.

---

### Post by kansasnoob on 2008-10-05
> **rbmorse said:**
> I've already opened the problem as bug 277404, but if you think it warranted I'd appreciate it if you could add a comment confirming the problem and listing your printer model as affected as well.

I will because it just recurred!

---

### Post by brm on 2008-10-06
I have reported another infuriating problem with a much older HP printer:
[http://ubuntuforums.org/showthread.php?t=895778](http://ubuntuforums.org/showthread.php?t=895778)

This experience might not be relevant to you, but the problem did go away with a fresh install of Kubuntu Intrepid Ibex beta.

---

### Post by rbmorse on 2008-10-06
I had to do a reinstall for a different reason, but it didn't help with the printer .ppd problem in this case.

---

