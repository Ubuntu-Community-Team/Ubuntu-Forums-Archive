---
title: "Minor Suspend/Hibernate and Resume issue"
date: 2008-08-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by beercz on 2008-08-27
Hello guys.

I have just upgraded from Hardy to Intrepid, as I could not get my Lenovo 3000 N200 laptop to hibernate properly in Hardy.

I am running kernel 2.6.26-5-generic and am now able to suspend or hibernate, and resume OK.

However, when I resume, a small dialog box appears containing the message:
> Failed to open device 'v4l:/dev/video0'
Invalid Argument./dev/video0 is my built in webcam and it works even after I resume, at least it works in cheese and skype.

Any ideas as to why this dialog appears when I resume, and how I prevent it from appearing?

Thanks in advance.

---

### Post by beercz on 2008-08-28
Hmmm - this issue seems to have been fixed after recent (kernel?) updates which is nice, thanks devs.

Supsend/hibernate works great now.  And when the shutdown/reboot bug is sorted I will be even happier.

Should the situation regarding the apparently errant dialog box change, I will post my findings here.

---

