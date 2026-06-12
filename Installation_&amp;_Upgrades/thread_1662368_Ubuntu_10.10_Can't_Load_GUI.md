---
title: "Ubuntu 10.10 Can't Load GUI"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by ugmoe2000 on 2011-01-08
After using the "nomodeset" option from the live cd I was able to get the live CD to boot to perform the install onto an SSD.

Upon the first boot I get the same screen that I was presented without the "nomodeset" option specified on the live cd and I'm pretty stumped as to how to get this machine booting now... here's a picture of the lovely screens I get.

Sorry in advance for the GIGANTIC picture... but perhaps the gibberish will stimulate your thread-answering abilities :)

[IMG]http://i.imgur.com/E4OI4.jpg[/IMG]

Any thoughts?

---

### Post by SnickerSnack on 2011-01-08
Is that two screens?  Maybe you should try getting it to work with one screen first.  That's probably not your real problem, but it's a step in the right direction.

---

### Post by Bucky Ball on 2011-01-08
Are you getting to the grub menu list at boot where you can select which kernel to start? If so, 

Hit 'e' to edit,
Find the kernel line which would probably end with 'quiet nosplash'
Add your 'nomodset' there.
Hit control+x to boot. 

Instructions are at the bottom of the edit screen for this.

There are several issues and bug reports with the current 10.10 kernel. This might not be your problem but might pay to see if you get the same results with 10.04 LTS if the above instructions don't work. More stable as been around since April (among other reasons). ;)

---

### Post by ugmoe2000 on 2011-01-08
> **Bucky Ball said:**
> Are you getting to the grub menu list at boot where you can select which kernel to start? If so, 

Hit 'e' to edit,
Find the kernel line which would probably end with 'quiet nosplash'
Add your 'nomodset' there.
Hit control+x to boot. 

Instructions are at the bottom of the edit screen for this.

There are several issues and bug reports with the current 10.10 kernel. This might not be your problem but might pay to see if you get the same results with 10.04 LTS if the above instructions don't work. More stable as been around since April (among other reasons). ;)

Bucky I thought I might be able to edit this, I couldn't remember how to make it show me the grub menu (turns out it was the ESC key) From there I made the modification you suggested. This allowed me to get into the operating system for the first boot and install an up-to-date graphics driver which is what I believed caused the problem in the first place (and other updates including a kernal update). Thanks for the suggestion it fixed my problem!

---

### Post by Bucky Ball on 2011-01-08
Excellent! and my pleasure.

Enjoy the OS and the learning curve, be sure to post in a new thread with any other probs, and mark thread as 'Solved' from 'Thread Tools'. ;)

---

