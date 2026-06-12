---
title: "GRUB Error when dual booting - Please Help !"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by Jugglerbry on 2009-12-08
Hi all

I'm new to the forums, and am really hoping someone can help me out on this one.

I've previously installed Ubuntu 9.04 using Wubi, from within Vista.  This worked great for me, and when I'd decided Ubuntu was for me, I installed Karmic as a proper dual boot.

Have had no issues whatsoever using either Jaunty nor Karmic.  (Jaunty has now been uninstalled, Vista totally cleaned up and only ever used for some software I cant yet find in Ubuntu)

However, my problem is this.  Ive installed Karmic on my father-in-laws laptop using the wubi installer.  Purely for him to try it out and see if it's for him.  All has been going really well for the past 5 or 6 weeks, up until now.  

What's happening now is he selects Ubuntu from the dual boot menu, the grub menu then appears, as normal, but then gets the following error

(GNUGRUB version 1.97 beta4, "minimal" BASH -like line editing is supported.  for the first word, TAB list possible command completion.  Anywhere else TAB list possible device /file completion.) this is then followed by ssh: grub

I've no idea what any of this means, and could really do with some help in sorting it out for him, as i think he was more than happy with it up until now.

He's reluctantly been having to boot into Vista but from what he's said is that's been locking up occasionally since this error has occured.

Not really overly bothered about Vista, just want to get Ubuntu to work again.

If anyone can help, it'd be really appreciated.

Thanks in advance everyone

Bryan
Jugglerbry

---

### Post by darkod on 2009-12-08
Known issue with wubi, read post number #10 here:
[http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)

Be careful in the instructions for XP there is typing error in third command, 26.31 should be 2.6.31.
Depending on which partition you installed wubi you might need to replave /dev/sda1 with /dev/sda2, or what ever (first, second, third partition on the drive). That will get you up and running.

---

### Post by Jugglerbry on 2009-12-08
thanks for the quick reply darkod.

I think it's safe for me to assume it's all installed on sda1 as it's on the same partition as Vista.  Or at least i think it is.  Hard drive isn't partitioned, so unless Wubi does it....

I'll give that a try.

Will the relevant commands need to be typed each time on booting ?
Do i type them at the prompt on boot  ? (where the error ends)

Thanks again for the reply

Bryan
Jugglerbry

---

### Post by darkod on 2009-12-08
Yeah, just type them at the sh: grub prompt or whatever it is. Look in the instructions it says to run
sudo update-grub2

in terminal after you manage to boot it. This problem occured after kernel updates but only in wubi (so you might consider proper dual boot instead but that's another topic). Don't know if selecting updates again can repeat it. Personally I never use wubi.

---

