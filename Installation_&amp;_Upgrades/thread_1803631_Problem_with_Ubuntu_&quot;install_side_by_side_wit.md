---
title: "Problem with Ubuntu &quot;install side by side with Windows&quot;"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by fontis on 2011-07-13
Hey!
I just tried to install 11.04 on my other laptop which I'd like to run as dual boot. The laptop already has Win7 installed on it, so when I popped in the USB with the install for 64-bit Ubuntu and went for install, the option to "Install side by side with Windows 7" doesn't appear.

I can only "wipe HDD and install Ubuntu" or the other option. What am I doing wrong?

---

### Post by Quackers on 2011-07-13
Is this on an HP machine?
You may already have the maximum of 4 primary partitions in use.
Check this in Windows Disk Management screen.

---

### Post by fontis on 2011-07-13
Yea this is on a HP machine.
How do I fix (circumvent) this?

---

### Post by Quackers on 2011-07-13
Normally on a new HP computer with Windows 7 installed they use all 4 primary partitions, which is silly, but they do.
Other in the same position as you have deleted the HP TOOLS partition (as the tools can be downloaded, if needed, from the HP website) then after defragmenting the C: partition, it can be shrunk from the Windows Disk Management screen, to create some free space for Ubuntu to install into.
When this is done the "install alongside" option will appear in the Ubuntu installer.

---

### Post by fontis on 2011-07-13
> **Quackers said:**
> Normally on a new HP computer with Windows 7 installed they use all 4 primary partitions, which is silly, but they do.
Other in the same position as you have deleted the HP TOOLS partition (as the tools can be downloaded, if needed, from the HP website) then after defragmenting the C: partition, it can be shrunk from the Windows Disk Management screen, to create some free space for Ubuntu to install into.
When this is done the "install alongside" option will appear in the Ubuntu installer.

Cool, thanks. 
May I ask what the HP Tools partition contains? Will deleting it mess up the HP Support Assistant mumbo jumbo?

---

### Post by Quackers on 2011-07-13
Others have not mentioned anything about that.
The partition contains some diagnostic tools, as I understand it.
Alternatively contact HP and thank them for clogging up your system and ask them what they advise :wink:  Good luck with that! They'll probably tell you it can't be done :-)

---

### Post by Mark Phelps on 2011-07-13
> **fontis said:**
> Cool, thanks. 
May I ask what the HP Tools partition contains? Will deleting it mess up the HP Support Assistant mumbo jumbo?

Most probably, yes.

However, I've found the HP Support Assistant to be more trouble than help.  It's great if you really WANT to grant remote access to HP so they can (supposedly) fix your machine, or otherwise, "improve" it.  But it nags constantly for update that are, otherwise, not really needed.

---

### Post by fontis on 2011-07-14
Well the solution worked. I deleted the HP Tools partition and merged it with the recovery partition in Windows. The "Install alongside Windows" option appeared!

And btw, so far no hiccups felt in Windows 7.

---

### Post by Quackers on 2011-07-14
Excellent, that's good to hear!
Please mark the thread as solved, using the Thread Tools near the top of the page.

---

### Post by rreyes3713 on 2011-07-14
... don't mean to hi-jack your thread, do yourself a favor and purchase those USB dual fan to cool down your HP laptop.

I had my HP G71-340US for a year and two weeks (two weeks after the warranty expired) and the motherboard kaput on me. The computer repair-shop claimed it was not feasible to have the motherboard replace and it is notorious of having problems. 

Then I read many other rants of HP laptops of overheating. Should have listen, and consideration a poll of most satisfied customers of laptop brands, HP was near the bottom.

HP do make good desktop, excellent printers, and other peripherals but laptops ...

---

### Post by fontis on 2011-07-14
> **rreyes3713 said:**
> ... don't mean to hi-jack your thread, do yourself a favor and purchase those USB dual fan to cool down your HP laptop.

I had my HP G71-340US for a year and two weeks (two weeks after the warranty expired) and the motherboard kaput on me. The computer repair-shop claimed it was not feasible to have the motherboard replace and it is notorious of having problems. 

Then I read many other rants of HP laptops of overheating. Should have listen, and consideration a poll of most satisfied customers of laptop brands, HP was near the bottom.

HP do make good desktop, excellent printers, and other peripherals but laptops ...

Yea I've heard some have had issues with overheating. But I wouldn't say it's primarily a HP issue. But I guess since I haven't had any problems I don't know how the support is.
Personally, this is my 2nd HP laptop (dv6 3142so) whereas the first hp laptop I had was dv6699. The first laptop still works without issues and it's nearly 5 years old.
But as I said.. guess I've been lucky with that. 

I do however notice that the laptops do get extremely hot. That's why I always try to "elevate" the vents so the laptop can get better circulation going. I just use some random box or something to slightly elevate it at the back and it does the trick. Otherwise I can cook eggs on it :D

---

