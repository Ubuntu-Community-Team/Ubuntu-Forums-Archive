---
title: "Lubuntu 16.10 Live gives OK sound, but installation to HDD gives no sound."
date: 2017-11-28
forum: Installation &amp; Upgrades
---

### Post by melcomub on 2017-11-28
Lubuntu 16.10.  Live running from booting USB stick gives perfect sound, but there's no sound when installed (from the same live source), to HDD.  I get this behaviour consistently on two Lenovo notebooks - G40-45  (AMD CPU) and G560 (Intel CPU).

I've tried a number of the things that others have suggested - removing/reinstalling Alsa and/or Pulse audio, etc, checking audio group,  checking audio  settings (to the extent that I understand them - I'm not very experienced with Linux) - all to no avail.

I've now come to wonder whether  the live system uses generic sound drivers etc and that the  HDD installation cleverly (but in this case, unhelpfully) has applied  ones more specific to the particular hardware?  If this is the case, it seems that forcing the generic ones to be always used might solve the problem.

I'd greatly appreciate any thoughts about this and especially any help to find whatever config or other files are involved.  I could then compare the live OS versions with the HDD ones and hopefully persistently change the latter to the former.  Thanks in anticipation.

---

### Post by mörgæs on 2017-11-29
Hi, welcome to the fora.
Lubuntu 16.10 is deprecated. First please begin with a fresh install of 17.10.

When that works feel free to post again and we can try to get the sound working.

---

### Post by melcomub on 2017-11-30
> **mörgæs said:**
> Hi, welcome to the fora.
Lubuntu 16.10 is deprecated. First please begin with a fresh install of 17.10.

When that works feel free to post again and we can try to get the sound working.

Many thanks mörgæs. Will do as soon as our thunerstorms here pass.

---

### Post by melcomub on 2017-12-05
> **melcomub said:**
> Many thanks mörgæs. Will do as soon as our thunerstorms here pass.

[B]Sound now works with fresh live install of Lubuntu 17.10 (AMD64) on the G40-45.
Thanks again mörgæs.  Will try on the G560 after the next full backup.  [/B]

---

### Post by mörgæs on 2017-12-06
Good, please mark the thread solved if it also works for the other computer.

---

### Post by melcomub on 2017-12-13
> **mörgæs said:**
> Good, please mark the thread solved if it also works for the other computer.

Yes - 17.10 gives sound and FN volume control keys on the G560. Thanks for the help.

---

