---
title: "Problem with 8.04 grub"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by thschiavo on 2008-06-13
I wasn`t able to find this question here, in Ubuntu Forum. Sorry if it was already posted.

I have instaled ubuntu 8.04, using dual boot with another OS (XP). The first time I reboot the PC, it was evrything ok... but when the first update were instaled and I had to reboot the PC, on the boot screen I had the ubuntu selection repeated 2 times (with different kernel versions). It means that I`d have now installed on my PC two versions of linux kernel (is it?...). So I was not worried, until I update more and more times: since I installed 8.04, I updated my system four times. Now, in my Grub, I have four versions of the Kernel.

I don`t know if it is actually a problem, I know people with the same situation. So I just wanna know if it`s a problem. If it`s not a problemm, can I just delete these lines from my grub file?

(Sorry if I did something wrong, this is the first time I post here...)

---

### Post by logos34 on 2008-06-13
change ['howmany= ']("http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall") option in menu.lst to '1'.  Then run **sudo update-grub**.

Or manually comment out the older kernel entries in the 'automagic' section by putting a hash mark (**#**) at the beginning of each line

---

### Post by Ponhovo on 2008-06-13
even there's no problems with the kernel itself, keep acumulating itens in the grub screen sucks x(
i would:
test if the older kernel version is avaiable and working
if not, i'd just delete the item from the list
else, i'd delete it anyway xD
not before asking x.x

---

### Post by Ponhovo on 2008-06-13
> **logos34 said:**
> change ['howmany= ']("http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall") option in menu.lst to '1'.  Then run **sudo update-grub**.

even with ubuntu and winxp? and the mem test and safe boot?

---

### Post by logos34 on 2008-06-13
> **Ponhovo said:**
> even with ubuntu and winxp? and the mem test and safe boot?

yep.  You'll be left with the current kernel along with the recovery, plus memtest86+.  So three lines in all.  Windows stanza will remain at bottom

---

### Post by thschiavo on 2008-06-14
Thanks for replies! I could not test yet your solutions (i´m in UNI now)... But I can answer that even my XP and my memtest are in GRUB, just below the 4 Ubuntu's... hehehe

And more... All the kernels are running ok... I was wondering... Isn't it using my HD memory with no use?...

Thanks again! : )

---

### Post by logos34 on 2008-06-14
> **thschiavo said:**
> All the kernels are running ok... I was wondering... Isn't it using my HD memory with no use?...

not sure I understand.  You're only running one kernel at a time.  And the other kernels take up hardly any disk space.

---

### Post by thschiavo on 2008-06-14
> **logos34 said:**
> not sure I understand.

Sure, sure... I do run only one at each time... but if I try to boot using other Kernel, it works...

> **logos34 said:**
>  (...) the other kernels take up hardly any disk space.
Uh, good information : ) So I will comment out the older kernel entries...

---

