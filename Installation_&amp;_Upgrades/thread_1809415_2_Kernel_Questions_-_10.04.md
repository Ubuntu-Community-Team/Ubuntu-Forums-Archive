---
title: "2 Kernel Questions - 10.04"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by sydbat on 2011-07-21
2 quick questions about 10.04 and kernels found in Synaptic...

1) Is it safe to install and boot 2.6.31? (need for one thing only)

2) Is it safe, or even wise, to install and boot 2.6.38? Other than a problem I saw in another thread about nVidia drivers?

Thanks!

---

### Post by sydbat on 2011-07-22
Lots of views, no answers. I understand. Perhaps it is because no one has done this and, therefore, no one feels comfortable giving advice.

Anyway...bump...

---

### Post by georgemc on 2011-07-22
IMHO
 
 Some version of 2.6.31 was running in a earlier version of U10.04, I think it was in U9.10.
 
 The version 2.6.38 is or was running in U10.10 AFAIK.
 
 Is it safe to put on your hardware? Most likely.
 
You can try it and if it doesn't work you can always fall back to a good version by selecting a different version in the grub menu.  You might have to look into the how-tos for grub.
 
 I am currently using U10.04.2 LTS on my Laptop with a custom kernel 2.6.39.2 I compiled with help of &#8220;kernel check&#8221;.  I still get the Ubuntu updates I just don't get any kernel updates, need to do those myself.
 
 I suggest that you check out the links below and see if that works for you.
 
Links:
[https://help.ubuntu.com/community/Kernel/Compile#head-8587f42b684c3694ba72bdcc89e461ec289cbf02](https://help.ubuntu.com/community/Kernel/Compile#head-8587f42b684c3694ba72bdcc89e461ec289cbf02)
 
[http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563)
 
[http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)
 
Hope this helps.
 
George

---

### Post by beew on 2011-07-22
I think it is safe for both questions,--of course it is safe doesn't mean it will work :). If the new kernel doesn't work just boot into the current one and delete it from synaptic. Since Ubuntu uses grub2 I don't think there is anything else you need to do. The grub menu will automatically update. If not or in doubt just  run in the terminal after the new kernel is deleted ```
 sudo update-grub
```I have installed and removed a whole bunch of kernels in 10.10. 2.6.38 worked, 2.6.39 didn't boot so I booted into 2.6.38 or 2.6.35  and removed that.. etc.

---

### Post by sydbat on 2011-07-22
Thanks. :D

I figured there wouldn't be too much harm in installing different kernel versions, but it's always good to get a second (third? forth? billionth?) opinion! 

I'll give them both a try and post results back here.

---

