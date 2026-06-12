---
title: "KDE progress bars not smooth-moving"
date: 2010-01-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2010-01-16
I should have posted it here before instead of bothering devs in the mailing list :D

I noticed that the KDE 4.4 progress bars on current Kubuntu Lucid (im on x64 with nvidia's beta drivers - not those from the repos/jockey) do not have smooth increase transitions but jump from one step to the next.

I had built KDE 4.4 RC1 from source (on Arch) though and the smoothness is there.

This is in apps like dolphin, konqueror, even running kdialog through command prompt like this:

```

dcopRef=$(kdialog --title "DCOP Progress" --progressbar "Initializing . . ." 12)
qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 1
qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 5

```

Any ideas whats up?

---

