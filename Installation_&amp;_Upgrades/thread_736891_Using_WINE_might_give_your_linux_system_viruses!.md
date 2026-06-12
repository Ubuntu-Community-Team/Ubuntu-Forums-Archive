---
title: "Using WINE might give your linux system viruses?!?"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by wandalalakers on 2008-03-27
I wasn't sure where to post this.  Have you guys seen this info?

Using WINE might give you viruses?
(This really disgusts me!)

I wonder if the same thing can happen using vmware?
I guess this means maybe I only need to run linux programs and no windows stuff?
I really hate Micro$oft now!

Viruses in Wine?
[http://wearenixed.blogspot.com/2008/03/you-only-know-good-when-youve-seen-bad.html](http://wearenixed.blogspot.com/2008/03/you-only-know-good-when-youve-seen-bad.html)

"I had set her up with a perfect Wine install. She had a bit of software that needed to run under wine and I had shown her how to install within that environment. Apparently, I wasn't specific enough. It never occurred to Paula that the .exe programs she had used on her XP machine were the vehicles for many of her present viruses. To her, it was perfectly fine to use those same .exe's...after all, she was in Linux, right?

I got there within the same hour and checked her machine. Yep...Windows viruses will reside and create the same havoc within a Wine environment. Now, I've seen it with my own eyes. This time I reinstalled for her and made sure I found all the infected .exe's on the Windows side and deleted them."

There was then some interesting discussion on the mailing list about how to keep wine secure, about the interesting fact that viruses _should_ work in Wine. Its best for compatibility of Wine emulates as many of the bugs from Windows as possible. As far as security goes the verdict was that running Wine as a normal user for normal applications is fine. However if you are intentionally bench-testing something malicious a virtual machine is the safest route. Again, never run Wine as root!"

---

### Post by KhaaL on 2008-03-27
there is a thread on these forums which discussed (and experimented!) the possibilities of running wine viruses [here]("http://ubuntuforums.org/showthread.php?t=72598").

Though in VMware you're quite protected since the programs there are running in a isolated enviorment - your VM machine dosen't share any of the real files with your host machine. Unless you have a shared folder!

Anyway you should always be careful and consider, what do you value most? your personal data or your system files? Remember, wine can write to your home directory and a virus run in wine will most propably write to it too.

EDIT: had to correct myself: it writes to the drives you've linked. that is, if you only have c: drive and it's linked to ~./wine/drive_c then you should be pretty safe since it's only that directory and its subdirectories that will be affected.

---

### Post by wandalalakers on 2008-03-27
Thanks so much for this info.   I was hoping to do some tweaking with some old Macromedia software but I'm not so sure now.

---

### Post by KhaaL on 2008-03-27
> **pcdoctor said:**
> Thanks so much for this info.   I was hoping to do some tweaking with some old Macromedia software but I'm not so sure now.

If you want to be utterly sure, run them in QEMU, Virtualbox or VMware since they'll be running in isolated eviorments :)

---

