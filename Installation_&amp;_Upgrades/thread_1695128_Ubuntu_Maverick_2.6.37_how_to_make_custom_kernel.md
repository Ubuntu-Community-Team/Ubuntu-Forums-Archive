---
title: "Ubuntu Maverick 2.6.37 how to make custom kernel"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by jewfromdahood on 2011-02-25
Hi I finally upgraded from 8.10 amd64 to 10.10 amd64 got everything setup, and made a custom kernel with the the sched: automated per tty task groups. Any way wondering if
I can make a stable 2.6.37 or later upgrade that's customized as I remove All unused drivers and optimize for core 2. Using the localmodinfo and the sched: automated per tty task groups patch. Please help! I've been trying to make custom kernels using every other way I can find on the net. I have made a custom kernel using git called 2.6.35-27-kosher.
Also wondering how to upgrade to the latest  stable openoffice

---

### Post by jewfromdahood on 2011-03-04
bump

---

### Post by jewfromdahood on 2011-03-07
bump

---

### Post by Frogs Hair on 2011-03-07
I ran across this a while ago but never used it. [http://www.webupd8.org/2010/12/how-to-compile-kernel-in-ubuntu-easy.html](http://www.webupd8.org/2010/12/how-to-compile-kernel-in-ubuntu-easy.html)

---

### Post by jewfromdahood on 2011-03-07
i've tried kernel check before, always gave me an issue after reboot with my fglrx driver. I'll compile now, with all that needs to be done on the custom selection and add than ~200 line patch. I love that patch it works so well... I can balance my cpu so it's not spinning the fan up when only one core is using 100% and the other is using like 10-20%, on average the performance is balanced. Well I'll compile and if the fglrx doesn't work, I'll then tell on this thread

---

### Post by jewfromdahood on 2011-03-09
wont work for some reason when i'm compiling any way to do it manually and also need fglrx to work with it. also want to get the 200 lines patch to work with it [http://www.google.com/url?sa=t&source=web&cd=3&ved=0CC0QFjAC&url=http%3A%2F%2Fwww.phoronix.com%2Fscan.php%3Fpage%3Darticle%26item%3Dlinux_2637_video&ei=ND13Tav1DMz1rAHCvPH9CQ&usg=AFQjCNFtB2DPy7YohlsKvHZyrRPf7Ww8TA](http://www.google.com/url?sa=t&source=web&cd=3&ved=0CC0QFjAC&url=http%3A%2F%2Fwww.phoronix.com%2Fscan.php%3Fpage%3Darticle%26item%3Dlinux_2637_video&ei=ND13Tav1DMz1rAHCvPH9CQ&usg=AFQjCNFtB2DPy7YohlsKvHZyrRPf7Ww8TA) and need to download the patch

---

