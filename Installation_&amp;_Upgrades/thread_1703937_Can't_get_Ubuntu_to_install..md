---
title: "Can't get Ubuntu to install."
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by MagnetsNextToMotherboard on 2011-03-09
:mad: I can't get Ubuntu to reinstall on my computer... I recently reformatted and re-installed windows and I think that might be the problem because I was running Ubuntu 64-bit before I reformatted... Now the problem I am getting is when I go to boot up Ubuntu to finish the install it loads on the purple screen with the Ubuntu logo then goes into a black screen with white letters. Its the screen that tells you to reboot and go into windows a run 'chkdsk /r' and reboot again, the problem is I have followed those directions 3 times and it didn't work, I don't think the operating system really knows what the problem is.Do any of you?

---

### Post by Hedgehog1 on 2011-03-09
Magnets,

Please boot up using the LiveCD, select 'try', then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by MagnetsNextToMotherboard on 2011-03-10
Ok I'm not exactly sure what you meant, where do I enter it... I entered it at the screen where it errors and it said "Not found"
](*,)

---

