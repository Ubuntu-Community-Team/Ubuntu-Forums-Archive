---
title: "How do I add to my network to access shared drives?"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by Leo45036 on 2010-01-26
So, it took me a few years to come back to Linux. Had used it MANY years ago, and have been meaning to revisit it for some time now and finally have. Tried a couple other OSs that were just, frankly, garbage. But, not Ubuntu! So far, I haven't had any of the issues I've seen posted here. I decided to use my worst system as a test environment - an old Jetta Jetbook 9450. Loaded up with no problems, most noted none of the "searching for drivers" issue that I ran into with other OSs!
 All that being said, I do have one question - how do I get the laptop to join my network so that I can view my shared drives? In Windows, it's simply change WORKGROUP to my network name. Been flipping through the options, and I'm sure I may have overlooked it.
 Other than that - so far, so good!

---

### Post by djchandler on 2010-01-27
Samba will let you share on a windows network. If you go to **Ubuntu Software Center>System Tools>Samba** at the bottom of your **Applications** menu, you'll be able to install system-config-samba, a GUI utility for configuring your network, and all its dependencies.

You'll find a new entry under you **System>Administration** menu called **Samba**. It's just as simple as any Windows network configuration utility I've used.

---

### Post by Leo45036 on 2010-01-27
Awesome! Now, do you recommend any one in particular? I see Smb4K, GADMIN-SAMBA, and Samba...

---

### Post by Leo45036 on 2010-01-27
Got it working! And, for other NOOBS out there with the same issue: what worked in my instance was: first, install Samba. Then, install Smb4K. Works perfectly!

---

