---
title: "ubuntu 11.10 problems right out the gate );"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by TheDevilMr666 on 2011-10-14
OK well I did the up grade and my computer said to restart to finish the up grade and now my laptop is stuck on the purple screen with a pointer natty worked fine and I was really happy that an upgrade came out now I'm just disappointed any help to get me past the purple screen so i can log in thankx. I'm on my android so I can't give you my system info but I'm running a Acer aspire 7745-5632. <snip>

---

### Post by kesara on 2011-10-15
Is your CAPSLOCK indicator blinking?
If so,
What you can do:
[LIST]
Select recovery mode and post in the information. (To get fixed)
[/LIST]
[LIST]
And selecting your previous kernel will get you out of the trouble for now.
[/LIST]

---

### Post by TheDevilMr666 on 2011-10-15
Naw like I can't even get to the login screen after it does the Ubuntu symbol on start up it freezes the only real control I have is on start up I can hit f2 or f12 and change the boot but it won't change anything cuz its all set up like it should be and when I installed natty I did it off a crazy and then for the 11.10 it did it by up grade should I try installing from a cd?

---

### Post by DisDis on 2011-10-16
I confirm.
After updating to 11.10, my laptop has become A&#1089;er 5745G freezing.
Caps lock blink.

Linux wings 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by kesara on 2011-10-16
I do have this problem.
What I did was before computer boots into Ubuntu (On grub screen) press up-down arrow keys and make Grub menu visible.
Then selected the previous kernel.
With that I can login.
Then I removed new kernel and headers.
That is the workaround until this issue get fixed.

---

### Post by kesara on 2011-10-16
Another thread on this problem: [http://ubuntuforums.org/showthread.php?t=1860298]("http://ubuntuforums.org/showthread.php?t=1860298")

---

### Post by TheDevilMr666 on 2011-10-16
Ill have to try that cuz before with 11.04 I had to hold f1 and f6 in order to log in and then I couldn't do it after the upgrade can anyone confirm this as a fix if not ill see if I can test it and ill confirm ill keep you posted

---

### Post by varunendra on 2011-10-17
> **TheDevilMr666 said:**
> Naw like I can't even get to the login screen after it does the Ubuntu symbol on start up it freezes the only real control I have is on start up I can hit f2 or f12 ...... should I try installing from a cd?Seeing Ubuntu logo means you have already passed the phase where advance grub menu can be brought up. Have you tried exactly what *kesara *suggested?-

> **kesara said:**
> ....before computer boots into Ubuntu (On grub screen) press up-down arrow keys and make Grub menu visible.
Then selected the previous kernel.
With that I can login.
Then I removed new kernel and headers.
That is the workaround until this issue get fixed.
You may also try to boot with recovery option as *kesara *pointed out earlier.

And yes, making a clean installation using a CD is always recommended while upgrading from within update manager should be avoided, since it most often causes problems afterwards due to package inconsistencies. Another important thing to do before installing is to try running a live session first from the same cd to ensure compatibility of hardware. Latest does not necessarily mean 'better'. On the contrary, it is more buggy than the slightly older ones, and takes its time to get mature.

---

### Post by TheDevilMr666 on 2011-10-17
Yes I did indeed and had no luck so what I ended up doing g was reinstalling 11.04 and I'm going to burn a crazy with 11.10 like I should have spring the first place

---

