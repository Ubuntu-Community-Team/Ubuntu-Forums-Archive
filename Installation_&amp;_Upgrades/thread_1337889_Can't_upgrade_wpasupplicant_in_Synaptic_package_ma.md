---
title: "Can't upgrade wpasupplicant in Synaptic package manager"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by dlkcomputer on 2009-11-25
I am trying to re-install Network Manager(stupid to remove it), and it requires 
wpasupplicant to be upgraded. wpasupplicant(0.6.4.1) in turn 
"depends: libpcslite1(>=1.4.99)  but it is not installable"

Where in the world is libpcslite1?
I find maybe 4 google matches for this thing, and none indicate where I 
could find this.

---

### Post by dlkcomputer on 2009-11-26
Ok, I figured it out. I needed to add a Dell "main universe multiverse" link into the third party software repository. After adding it,  the link doesn't actually show up in the 3rd party list, but it 
downloaded the necessary software. I lost the Ubuntu Software tab during this process,  
maybe that is where is would show up? I have no idea how to get that back, but I have Network Manager running now, so I am thrilled since I went to bed last night thinking there was no way out of this situation, and this stuff is all new to me.

---

