---
title: "Edgy starts slow"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by _deXter on 2007-02-15
Hi!

I've upgraded to Edgy a few weeks ago, but my edgy takes above 3 mins to go since the boot menu till the login screen. 
I've a:
P4 3.2 G
1 gb de ram
radeon 1250, 125 MB

I dont understand why this takes so long. Anyone have an idea to help me?

Thanks.

---

### Post by louis_nichols on 2007-02-15
You can check which services hang using a simple change at boot time, to prevent usplash from starting. This will let you see all details of the boot process. When you see grub with the list of OS's to boot, choose the line with Ubuntu and press "E", then press "E" again on the line with "kernel" and remove the word ***splash*** at the end. Then press ENTER and then "B" to boot.

Next, it will be pretty obvious to notice which service hangs at boot. I would place my bet on fsck. I get that too when I have a DVD in one of my optical drives. Unfortunatelly, if it is indeed fsck, I must admit I can't recommend a way to disable it. I'm looking fot one myself.

If it is not fsck, then post the name of the service here and we'll see what can be done.

---

### Post by _deXter on 2007-02-15
Thanks a lot. The problema has been solved.

I did what you said, and removing the word "splash" it makes the boot very faster.

Thanks. Problem solved. ;)

---

### Post by louis_nichols on 2007-02-15
You're welcome. But it wasn't the removal of SPLASH that solved the problem. :) It must have been something else. splash just controls whether the boot process should be in graphical mode or text mode and doesn't take time.

Maybe you had the same problem I do, with the cd in the tray.

---

### Post by _deXter on 2007-02-15
I've thought the same. The problem was not solved, but just hided. :P

Anyway, there's going great now, thats what I want.
But, what I understand was that you dont know how solve, doesn't you? I'm still newbie at linux. :P

If you think that you have some solution, tell me, and I will try it.

One mor time, thanks. :D

---

### Post by louis_nichols on 2007-02-15
Well, I might know how to solve the problem, but the thing is we don't have enough data to know what is actually the cause of the problem. That why I told you to disable usplash in the first place: so we see which application slows the boot process.

Now, I think it's a coincidence that after disabling usplash your system boots faster. But if the slow boot comes back, then you'd have to post here at which point in the process it hangs. Then I might know what you need to do. Or someone else might. It is true though that I don't know how to disable fsck at boot. :)

---

