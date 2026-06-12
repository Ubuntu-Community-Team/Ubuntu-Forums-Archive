---
title: "Keep loosing desktop effects...."
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by exploder on 2009-10-03
On and off all day today my desktop effects will stop working when I boot up or re-boot. This occurs at random and it takes a few times of re-booting before the system will let me enable desktop effects again. 

When this happens I get errors at boot in really huge fonts. I have Intel 8x onboard graphics. What is causing this?

---

### Post by vredley on 2009-10-04
Just a guess - do you think it might be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694)? If so, there's a workaround in comment #2.

---

### Post by ft_ on 2009-10-04
I confirm (via non-quiet splash boot) that there are some DRM bug lines. (My vc is intel 4500.)

Same issue with desktop effects. Working fine though on my current session...

---

### Post by exploder on 2009-10-04
vredley, thank you! Your guess was exactly what the problem was and although I do not have Intel 915 graphics, the fix you pointed me to did the trick. 

ft_, Compiz worked randomly for me but is now working consistently with the above mentioned work around. 

Thanks to both of you for the help and confirming this bug. I really appreciate it! This is a nice release and it really looses something when Compiz is not working. I will try and add to the bug report. Thanks again for your help.:)

---

### Post by exploder on 2009-10-04
Well, it seems the work around is not consistent. I keep loosing desktop effects on and off. I added to the bug report and hope they resolve this because this kind of bug ruins the release for Intel users. I know this issue can be resolved because it is fixed in other distributions.

---

