---
title: "Help with Wily Upgrade"
date: 2016-01-11
forum: Installation &amp; Upgrades
---

### Post by mlnease on 2016-01-11
I've just upgraded to 15.10 and can only boot into Wily using the 'Recovery' GRUB option.  If I boot normally, then enter my username and password in the login screen, the screen goes black and the system ceases to respond.

If at the login screen, I enter my username and password manually, I can boot normally.

Any advice would be greatly appreciated--thanks in advance.

---

### Post by Bucky Ball on 2016-01-11
When you boot the machine, get to the list of kernels, highlight the first kernel and hit 'e' to edit it.

Look for the line that ends in 'quiet' or 'splash' or both. At the end of that line, add 'nomodeset'. It should look like this:

```
quiet splash nomodeset
```

Follow the instructions at the bottom of the screen to save changes and continue. Any luck?

---

### Post by mlnease on 2016-01-12
> **Bucky Ball said:**
> When you boot the machine, get to the list of kernels, highlight the first kernel and hit 'e' to edit it.

Look for the line that ends in 'quiet' or 'splash' or both. At the end of that line, add 'nomodeset'. It should look like this:

```
quiet splash nomodeset
```

Follow the instructions at the bottom of the screen to save changes and continue. Any luck?
Thanks for the speedy response!  So just to double check, I should replace ```
$vt_handoff
``` at the end of that line with ```
nomodeset
``` --correct?

---

### Post by Bucky Ball on 2016-01-12
Incorrect. Don't do that. 

Look for the line that ends in 'quiet splash' or either one of those words.

Add 'nomodeset' at the end of that line after a space. So it should look like:

quiet splash nomodeset

Follow instructions at the bottom of the screen to save the changes and proceed. If the line doesn't end in 'quiet' or 'splash' or both, don't change it. Look for it there.

---

### Post by mlnease on 2016-01-12
> **Bucky Ball said:**
> Incorrect. Don't do that. 

Look for the line that ends in 'quiet splash' or either one of those words.

Add 'nomodeset' at the end of that line after a space. So it should look like:

quiet splash nomodeset

Follow instructions at the bottom of the screen to save the changes and proceed. If the line doesn't end in 'quiet' or 'splash' or both, don't change it. Look for it there.

Thanks again--the only line I found containing 'quiet splash' is followed by '$vt_handoff'.  I'll go back and double check and get right back to you.

---

### Post by mlnease on 2016-01-12
I did double check--the only place 'quiet splash' appears on the screen, it is immediately followed on the same line by '$vt_handoff'.

Thanks for your time and patience.

---

### Post by Bucky Ball on 2016-01-12
It's probably just the way it is formatting in there. Don't worry about the handoff part. As long as you get the cursor directly after 'splash', insert a space then 'nomodeset', that will do it. Save and exit.

PS: This change is not permanent so will only work for this boot. In other words, if you screw up, don't panic. Simply reboot and the changes are gone and you can try again. If it works we can make it permanent.

---

### Post by mlnease on 2016-01-12
> **Bucky Ball said:**
> It's probably just the way it is formatting in there. Don't worry about the handoff part. As long as you get the cursor after 'splash', insert a space then 'nomodeset', that will do it. Save and exit.

Will do--can you please tell me how to save and exit?

---

### Post by Bucky Ball on 2016-01-12
The instructions are at the bottom of that screen. I think it is control+b or something. Or maybe just 'b'. I haven't done it in awhile. It's all there.

Very late here so off to bed. Good luck. ;)

---

### Post by mlnease on 2016-01-12
> **Bucky Ball said:**
> The instructions are at the bottom of that screen. I think it is control+b or something. Or maybe just 'b'. I haven't done it in awhile. It's all there.

Very late here so off to bed. Good luck. ;)

Pleasant dreams--problem solved with your advice and more from [this thread]("http://ubuntuforums.org/showthread.php?t=2309688&page=2").  Thanks again!

---

