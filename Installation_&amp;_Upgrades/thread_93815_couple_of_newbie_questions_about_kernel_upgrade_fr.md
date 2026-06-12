---
title: "couple of newbie questions about kernel upgrade from 2.6.10 to 2.6.12"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by towsonu2003 on 2005-11-22
Hi,

This is going to be my first kernel upgrade in Ubuntu/Debian... I have a couple of questions, as I'm panicked by this 55MB (dial up) kernel security upgrade... 

1. If I do the upgrade, will my old kernels (2.6.10-386 and 2.6.10-686) stay in GRUB so that I can boot from them in case something goes wrong? This threat (post #1) [http://www.ubuntuforums.org/showthread.php?p=513019#post513019](http://www.ubuntuforums.org/showthread.php?p=513019#post513019) suggests they will stay there, but it's kind of not clear...

2. Is there a maximum number of entries that GRUB can handle. Right now, I have 7 entries: 3 for 386, 3 for 686, 1 for Windows... The new one (if it keeps the old entires intact) will add another 3, to a total of 10... If there is a maximum, I will have to clean up I guess?

3. How can I make sure that I am getting each and every kernel part I need to boot (like modules + image + headers + anything else)? I won't need nvidia as I have ati (not cool)...

I will REALLY appreciate any help on this. Am I getting too old for this kind of adventure or what? I can hear my heart beating from here... pof-hard to be newbie!

Thanks in advance :)

---

### Post by SavageBeginner on 2005-11-22
1.  Yes, if you upgrade, the old kernel will still be available in the grub menu.

2.  I don't think there is a maximum number of entries on the grub menu.  I have 13 now with no problems.

3.  You've got it right - image, modules and headers.

---

### Post by maubp on 2005-11-23
Is there any plan for ubuntu to automatically "prune" the really old kernels from the GRUB list? (and the hard disk)

Suppose you had kernels 5 ("old") and 6 ("active), and update to kernel 7.

At the moment you would be left with 5 ("really old"), 6 ("old") and 7 ("active") on GRUB.

Repeat this a few times and there will be a nice long list (especially if using 686 kernels with the 386 ones also installed just in case) as pointed out above.

It would make some sense after a kernel update to remove the "really old" kernels from the system...

If using a package management system like apt-get, could this be done by having "Kernel 7" in my example mark any really old kernels (e.g. kernel 5) as recommended to be removed?

---

### Post by markr on 2005-11-23
If you go int synaptic and remove the old kernels it will also remove them from the GRUB list.

Just make sure your new kernels work before doing this!!!

Mark.

---

### Post by yesplease on 2005-11-23
Perhaps this howto helps [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917) . I used Synaptic for the kernel upgrade. Synaptic will show which dependent packages you need and will keep track of what you have got already.

Dont worry so much :) , you have the old kernels to fall back to, that is why they are not removed automatically.

---

