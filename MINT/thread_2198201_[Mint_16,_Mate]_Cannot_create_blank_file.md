---
title: "[Mint 16, Mate] Cannot create blank file"
date: 2014-01-07
forum: MINT
---

### Post by pooopies on 2014-01-07
Hi all,

I recently did a fresh install to mint 16 from mint 14. I backed up and restored my old home folder and after some adjustments almost everything is working as intended. 

Whenever I try to make a blank file using either touch or right click -> create blank file it is not actually blank and contains many weird characters at the beginning when I open it with notepad (as it will not open with any other application). I am not sure why this is or how to fix it. Any help would be great!

One added piece of information: I did go from an encrypted home folder to unencrypted, not sure if this makes a difference.

Thanks all!

--pooopies

---

### Post by Habitual on 2014-01-07
Can you create another regular user on the system and login as that new user and then test this issue?

---

### Post by pooopies on 2014-01-07
The new user does not have the same issue. Nor does the root user.

---

### Post by tgalati4 on 2014-01-08
Sounds like you have discovered a bug or at least an edge case.  When going from encrypted to non-encryted, somehow your user files and the directories they are in have encrypt hash still attached. 

Can you describe how you performed the "restore" of your home directory?

---

### Post by pooopies on 2014-01-08
I backed up my old home folder making a tar ball then I unextracted it to the new home folder. 
I actually finally fixed the issue by resetting my mate settings as well as compiz, and deleting several plausible folders in the .config directory.
Thanks for the help guys! Was interesting, and wish I had a more precise fix.

--pooopies

---

### Post by tgalati4 on 2014-01-08
There are a lot of config files, so when going from one distro to a newer distro, all it takes is one bad config file to make your day interesting.

---

