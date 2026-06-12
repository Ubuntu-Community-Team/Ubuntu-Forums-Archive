---
title: "Sound problem [[karmic]]"
date: 2009-08-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by XKCD64 on 2009-08-08
I am using an Acer Aspire 4730z.  Ubuntu 9.10 Alpha 3.  I can get sound out of the speakers, but not through earphones.  The earphones work with my iPod, so it's not an earphone problem.  Help?

---

### Post by Mike_IronFist on 2009-08-08
> **XKCD64 said:**
> I am using an Acer Aspire 4730z.  Ubuntu 9.10 Alpha 3.  I can get sound out of the speakers, but not through earphones.  The earphones work with my iPod, so it's not an earphone problem.  Help?

The answer to your problem is, Karmic is still in its Alpha stages and you shouldn't expect it to work properly at all. It's not finished yet.

Please consider staying with Jaunty until the official release of Ubuntu 9.10. It's the best thing to do since Alpha and Beta builds do not typically get help or support of any kind on the forums or from Canonical.

---

### Post by taavikko on 2009-08-08
Please post the output of "aplay -l"
Also check via "alsamixer" & "alsamixer -Dhw" that levels aren't muted or set to low levels.

---

### Post by ranch hand on 2009-08-09
And you may want to try gnome-alsamixer.  Why this works better for me than alsamixer is beyond me.

---

### Post by psyke83 on 2009-08-09
It would be wise to get into the habit of doing searches before posting new threads.

See: [http://ubuntuforums.org/showthread.php?t=1232342](http://ubuntuforums.org/showthread.php?t=1232342)

Specifically: [http://ubuntuforums.org/showpost.php?p=7739984&postcount=17](http://ubuntuforums.org/showpost.php?p=7739984&postcount=17)

You need to set "Analog Headphones" on Output Devices tab of PulseAudio Volume Control. This is not ideal, but we are using a test version of PulseAudio on an alpha release - if you're not interested in testing, Jaunty may serve you better.

---

