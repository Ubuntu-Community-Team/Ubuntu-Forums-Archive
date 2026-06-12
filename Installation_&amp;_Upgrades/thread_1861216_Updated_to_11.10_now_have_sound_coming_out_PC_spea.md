---
title: "Updated to 11.10 now have sound coming out PC speaker &amp; Stereo speakers!"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by solorize on 2011-10-15
Hi,

I have just updated my Ubuntu from 11.04 to 11.10.

After re-started my PC I now have sound coming out
of my PC speaker and my main stereo speakers at 
the same time!

Does anyone know how I can turn off the PC speaker
and just have the audio come out of my main stereo
speakers?

I have had a brief look in the Sound settings but
can not seem to see a way of doing this.

Regards

Mark

---

### Post by Kirix on 2011-10-15
I would also know how to disable/enable audio devices on Ubuntu. Audio has defaulted to HDMI output on vid card and I wanna use onboard.

---

### Post by solorize on 2011-10-16
bump

---

### Post by solorize on 2011-10-19
I managed to resolve this problem on another forum; [click here]("http://www.linuxquestions.org/questions/showthread.php?p=4502467#post4502467")

---

### Post by grahammechanical on 2011-10-19
My motherboard has a connector to connect to a speaker in the case but I do not have a speaker in the case. No problem. Everything works fine.

Could you not open the case and disconnect the PC speaker? Or go into the BIOS and make sure that there is not a setting that links audio output from the motherboard with the PC speaker when all you need is audio output from the audio connectors?

Regards.

---

### Post by clever on 2011-10-21
> **solorize said:**
> I managed to resolve this problem on another forum; [click here]("http://www.linuxquestions.org/questions/showthread.php?p=4502467#post4502467")

I had the same issue on 11.04: one day, it started playing sound out of the motherboard PC speaker as well as my external speakers.  I swear it didn't do it right after my (fresh) install but rather just started happening one day.  I never tried to track it down til today.

My solution turned out to be to use alsamixer.  There was an entry for "Mono" which was turned part-way up.  I turned that all the way down and now the motherboard speaker is quiet again.

For me at least, I didn't have to modify any system files like alsa-base.conf as described in OP's linked solution.

Hope that helps somebody!

---

