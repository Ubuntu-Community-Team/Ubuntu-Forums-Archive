---
title: "Required to type in my password twice at login and screensaver"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Saneless on 2008-10-13
What happens is I type in my password, it says Checking... and then it blanks out and I have to type it again.  If I just hit enter the first or second time it gives an error, so it definitely wants my real password twice.

I don't have to do this for any admin-privileges like sudo or synaptic or anything like that.

I originally had Thinkfinger and the pam files changed to use it before the upgrade, and it removed some entries from pam/auth files when I upgraded.  I added them back in and noticed that not only were the fingerprint functions not working, but once I removed the lines I had these double-password issues.

Maybe I didn't change the files back properly.. is there a fresh auth/pam files I can use to see if that's the issue?  Or is this issue affecting others as well?  Again, I thought I removed any entries that I put in for Thinkfinger but I may be wrong.

---

### Post by Saneless on 2008-10-13
Really, no one?

Can I at least get some stock common-auth and such pam files so I can overwrite what I've got?  This really is quite annoying.

---

### Post by wgrant on 2008-10-13
What is the content of your common-auth?

---

### Post by Saneless on 2008-10-14
I don't know, I'm not at home at the moment :) (And the boards were down last night)

Maybe I did fix something slightly - UPDATE: It only does this behavior with the screen saver.  Logging in is fine.  Sudo functions are fine.  It's just the screensaver that gives me issues.

---

