---
title: "New sound volume icon in notification area, tooltip is corrupted"
date: 2009-02-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by forumache on 2009-02-03
Hi,

Since today I noticed that the Gnome Volume applet become redundant, as a new notification sound icon appeared in the notification area (next to tracker, bluetooth and network icons).

The tooltip for the new sound icon has a problem and I'll tell you how to reproduce it:
Go over the icon, a tooltip will appear:
Output: 75%
-13.85 dB
NVidia CK8S - NVidia CK8S

Now, right click the icon, select Sound Preferences, Sound Preferences dialog appears, modify the Output Volume to any value (but not to 0). Go over the tooltip again:
Output: 4%
-&#8734; dB
NVidia CK8S - NVidia CK8S

Have you noticed the problem? &#8734; decibels? A file is attached for your viewing pleasure.

I reported this as a bug, [https://bugs.launchpad.net/ubuntu/+bug/325014](https://bugs.launchpad.net/ubuntu/+bug/325014)
Please try to see if you get this on your system (fully updated), it is very easy to reproduce and subscribe to the bug. This way it will get the proper attention.

Many thanks.

Later edit: actually, it says & # 8734; but I see that it was interpreted as &#8734; by the forum software. Look at the picture. Says more than 1000 words ;)

---

### Post by biasquez on 2009-02-03
i have 2 icons about audio:
- first icon is old audio icon like style
- second icon is new volume control ( new style into jaunty)

(i attached jpeg)

---

### Post by techdude3177 on 2009-02-03
Yes i noticed that i have two sounds icons in my notification area, the first one is for the sound preferences and the second one is the output device for whatever reason.
however both my icons are the same.

---

### Post by mirhciulica on 2009-02-03
I have those two. One is the applet and can be removed.

---

### Post by forumache on 2009-02-03
> **mirhciulica said:**
> I have those two. One is the applet and can be removed.

Correct. What about the tooltip bug? Does it manifest itself on your computer if you try to reproduce it as per my description?

Thanks for testing.

---

### Post by Gourgi on 2009-02-03
> **mirhciulica said:**
> I have those two. One is the applet and can be removed.

which package is it?
or you mean removing it from the notification area?

---

### Post by forumache on 2009-02-04
> **Gourgi said:**
> which package is it?
or you mean removing it from the notification area?

You cannot remove icons from notification area. On the other hand, you can remove applets from the panel (Volume, Date and Time, etc).

You can remove the Volume applet from the panel and start using the Volume icon in the notification area.

The bug is seen in the tooltip of the new Volume icon in the notification area.

Come on friends, Alpha 4 is tomorrow, it is an easy reproducible bug, it take less then one minute to follow my instruction and posts a "Me too" here in case you are able to reproduce it (hint: do it now)

Thanks.

---

### Post by rajeev1204 on 2009-02-04
> **forumache said:**
> You cannot remove icons from notification area

.


Though not directly, you can remove it.For example i never use the Network applet and for that i go to preferences>sessions and delete it from there.Save it and it wont appear on a reboot.

If you want it back,in terminal type nm-applet , then go back to sessions and  again select save current running programs.






regards

rajeev

---

### Post by forumache on 2009-02-04
rajeev1204, you are right, but it doesn't help the bug :)

Could you reproduce it? Do you need more info, maybe I did not explain it right?

I think I'm starting to become frustrated, in the time you explained us about the nm-applet you could have tried to reproduce the bug. It happens here 100% of the time, doing the steps I described.

---

### Post by rajeev1204 on 2009-02-04
> **forumache said:**
> rajeev1204, you are right, but it doesn't help the bug :)

Could you reproduce it? Do you need more info, maybe I did not explain it right?

I think I'm starting to become frustrated, in the time you explained us about the nm-applet you could have tried to reproduce the bug. It happens here 100% of the time, doing the steps I described.



Ok,sorry but,i havent started using jaunty yet.Just thought i will  offer this small bit of information.

Tomorrow is alpha 4, so i will be installing it only then. :)




regards

rajeev

---

### Post by forumache on 2009-02-04
OK, sorry rajeev, I forgot that people browse Jaunty forums even before installing it.

See you tomorrow then with the brand new Alpha 4 :)

---

### Post by rajeev1204 on 2009-02-04
> **forumache said:**
> OK, sorry rajeev, I forgot that people browse Jaunty forums even before installing it.

See you tomorrow then with the brand new Alpha 4 :)


See u :)

---

### Post by linux6994 on 2009-02-04
I removed the old one from the panel and I am using the new one. All is working well.

---

### Post by theSpaceAmoeba on 2009-02-04
I have the two icons as described by everyone (both look the same, but one can be removed, other goes to 'Sound Preferences', etc.). However, I have not been able to reproduce the "infinity" decibel bug although I do get negative decibels which does not make much sense to me.

---

### Post by pressureman on 2009-02-04
> **theSpaceAmoeba said:**
> I have the two icons as described by everyone (both look the same, but one can be removed, other goes to 'Sound Preferences', etc.). However, I have not been able to reproduce the "infinity" decibel bug although I do get negative decibels which does not make much sense to me.

Negative dB are often used on volume scales, and are a relative measurement to some reference volume. Usually 0 dB will be the maximum volume the equipment can produce without distortion.

For every 3 dB difference, this represents a ratio of approximately 2:1. So for example, -3 dB on your volume scale would be half of the reference volume. -6 dB would be half of that again, or a quarter of the reference volume. Obviously, this scale is logarithmic.

The actual definition of a Decibel is 10 x Log10(P1/P0), where P1 and P0 are each a measurement of the same property, using the same units.

---

