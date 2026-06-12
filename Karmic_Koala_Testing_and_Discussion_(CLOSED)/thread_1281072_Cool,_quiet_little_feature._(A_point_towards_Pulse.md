---
title: "Cool, quiet little feature. (A point towards PulseAudio)"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mr. Picklesworth on 2009-10-02
I noticed a pretty cool feature the other day :)

I'm sure everyone is aware of the sorry way sound works in most operating systems. There are at least 3 different volume controls influencing any given stream. For example, with a media player application you have the volume control in the app itself (which performs any kind of magic behind the scenes), the system's master volume, the volume control for the app's audio stream and the volume control on your hardware device. Now, try diagnosing what is at fault when the sound is too quiet. Kind of crazy. The fix people tend to apply is just not to touch any volume control except the master one.

Okay, on with the future! In Karmic, you'll notice that the volume control inside an application such as Rhythmbox or Totem is now directly tied to the volume of its PulseAudio stream. (Right click the volume applet, head to sound preferences and head to the applications tab to see).
This means all volume levels (except the hardware one) can be accessed from one place and the volume level displayed in the application reflects reality.

Yay, integration!

---

### Post by SoftwareExplorer on 2009-10-02
Cool, I'll have to try that out when the beta finishes downloading. :)

---

### Post by Compintuit on 2009-10-02
> **SoftwareExplorer said:**
> Cool, I'll have to try that out when the beta finishes downloading. :)

It's also possible to make it really, really loud, from the command line.

---

