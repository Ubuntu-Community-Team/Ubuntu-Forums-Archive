---
title: "[SOLVED] Strange window opening"
date: 2008-09-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2008-09-04
Using Intrepid. No matter what browser I open ( Swiftfox, Swiftweasel, Firefox) a strange little window is opening in the upper left corner and it is blank. when i close it, it closes the browser also. 
Any one else have this happening?

---

### Post by _oOMOo_ on 2008-09-04
Are you using the 64bit version of Intrepid?

---

### Post by Slug71 on 2008-09-04
Its Flash/npviewer causing this. I believe it happens with 32 and 64bit. Hopefully this will be resolved soon.

---

### Post by DougieFresh4U on 2008-09-04
> **_oOMOo_ said:**
> Are you using the 64bit version of Intrepid?

32-bit
thanks for reply

---

### Post by ronacc on 2008-09-04
I wondered what that was , I saw it while I was downloading Opera which is the only thing I use firefox for.

---

### Post by _oOMOo_ on 2008-09-05
> **ronacc said:**
> I wondered what that was , I saw it while I was downloading Opera which is the only thing I use firefox for.

Lol :)

DougieFresh4U I wasn't aware this was happening on 32bit also, I thought it was more an nsplugginwrapper problem as removing that and reinstalling flash seems to fix it (sort of). I don't have access to a 32bit version of Ubuntu.

Does removing and reinstalling flash work for 32bit?

```

sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

---

### Post by Gina on 2008-09-05
Strange - not seen it myself with either Hardy or Intrepid on any of my machines.  I have seen pop-up windows though but they aren't empty.

---

### Post by DougieFresh4U on 2008-09-05
> **_oOMOo_ said:**
> Lol :)

DougieFresh4U I wasn't aware this was happening on 32bit also, I thought it was more an nsplugginwrapper problem as removing that and reinstalling flash seems to fix it (sort of). I don't have access to a 32bit version of Ubuntu.

Does removing and reinstalling flash work for 32bit?

```

sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

Thanks, but still have the window :(

---

### Post by Slug71 on 2008-09-05
Ive tried a few fixes Dougie and they only seem to be temporary. At least on my machine anyways. Im using 64bit though. Apparently FF 3.0.2 and Flash 10 RC is coming soon which contain fixes for this issue and others.

That code did work for me for a short time though.
I tried removing FF and Flashpluggin-nonfree from the repos too and then reinstalling and that also worked for a short time.
Now i'm using Flash 10 B2 which seems to fix the issues for some, but not me:(

---

### Post by Nullack on 2008-09-05
Its a known bug in LP, Ill dig the number up in a bit I cant right now.

EDIT: [https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/250769](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/250769)

---

