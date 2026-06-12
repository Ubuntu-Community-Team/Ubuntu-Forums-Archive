---
title: "Small testing request"
date: 2009-05-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Stunts on 2009-05-16
Hi all Karmic testers!

I have a small request for you:

I have noticed that Karmic uses Gconf 2.26.2
This package broke Hardware-monitor on my ArchLinux install.
Since I don't have a broadband connection where I am right now, I can't download karmic alpha to make the test myself.

My request is simple - can you install hardware-monitor from the repos and let me know if it works?

I have reported a bug to arch, but if it causes breakage in Ubuntu too, the bug should be files to gnome.

Thank you for your time.

---

### Post by linux6994 on 2009-05-16
The application installed but the monitor applet would not work.

---

### Post by plun on 2009-05-16
Crashes directly when I try to add it to the panel.

---

### Post by ronacc on 2009-05-16
hardware-monitor fails here on karmic amd64 .

---

### Post by Stunts on 2009-05-16
Thanks guys, for your feedback.

The problem doesn't seem to be Arch specific then.

You guys rock. =-)

---

### Post by Didius Falco on 2009-05-16
It installed, but crashed when adding to a panel. I rebooted and it promptly crashed on startup. I was offered the option to delete it from the panel and did so.

There were no options to file a bug report offered.

Regards,

Didius

---

### Post by Stunts on 2009-05-16
I'll just report the bug to gnome directly.

---

### Post by Stunts on 2009-05-16
Bug reported here:
[http://bugzilla.gnome.org/show_bug.cgi?id=582865](http://bugzilla.gnome.org/show_bug.cgi?id=582865)

If you'd like to help me get it fixed, those of you who tested it can go there and help to confirm it.

Thank you very much once again.

---

