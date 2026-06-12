---
title: "Some Bugs"
date: 2009-02-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-02-09
Looking to see if anyone else is getting these before I action in LP:

1. gnome system log viewer complains of missing logs on startup

2. The change theme GUI isnt sized right and only displays two themes per side leaving much white space.

Theres some unmet dependencies on trying to install the gstreamer multiverse bad plugins but I understand those are auto reported.

thanks

---

### Post by mdurham on 2009-02-09
not here!

---

### Post by Nullack on 2009-02-09
For both? Your on Jaunty synched to the repos?

---

### Post by Kevbert on 2009-02-09
The log file bug, you mean the errors (see attached).  This is an updated 64 bit kernel (2.6.28-6) which has just been rebooted (only once). If you raise a bug, I'll confirm it.
If you mean Themes under Appearance Preferences , they are OK for me.

---

### Post by ronacc on 2009-02-09
I' not getting the logfile error here , but I do see what you mean about change themes . It looks like the theme icons are too big or the window is too small , if you expand the window a little bit it will show 3 per row and the white space reduces .

---

### Post by Nullack on 2009-02-09
The log file error is LP 318689 and on gnomes bugzilla is 567169

---

### Post by autocrosser on 2009-02-09
Yes on the change themes GUI. Not getting problems with Log Viewer....

---

### Post by Kevbert on 2009-02-09
Left a brief comment on Launchpad for the log error and subscribed to bug.

---

### Post by tawmas on 2009-02-09
> **autocrosser said:**
> Yes on the change themes GUI. Not getting problems with Log Viewer....

Curious, here I see the contrary (Ubuntu 32bits on my eee, later I'll have a look at those on my 64bit desktop).

---

### Post by autocrosser on 2009-02-09
I bet that the reason I'm not seeing problems with Log Viewer is that I enabled quite a few logs to monitor & those are the ones I see when I start the app.

---

### Post by tawmas on 2009-02-10
> **autocrosser said:**
> I bet that the reason I'm not seeing problems with Log Viewer is that I enabled quite a few logs to monitor & those are the ones I see when I start the app.

Now that you make me think about that, I've added one custom log file on my desktop (where I don't see the bug), but I have the default logs on my eee (where I do see the bug). I didn't remove any logs, though...

---

### Post by taavikko on 2009-02-10
> **tawmas said:**
> Now that you make me think about that, I've added one custom log file on my desktop (where I don't see the bug), but I have the default logs on my eee (where I do see the bug). I didn't remove any logs, though...

Did you tweaked your eee? adviced by some [www.site](www.site)...
If you have directed your logs to RAM (edited fstab)

... Just a thought ...

---

### Post by Nullack on 2009-02-11
OK fellow testers :)

[https://bugs.launchpad.net/ubuntu/+bug/328131](https://bugs.launchpad.net/ubuntu/+bug/328131) - can someone please confirm this one its the whitespace theme issue weve been discussing.

[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/328130](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/328130) - and confirm this one too - its new, gparted doesnt know about EXT4.

[https://bugs.launchpad.net/ubuntu/+source/flightgear/+bug/311859](https://bugs.launchpad.net/ubuntu/+source/flightgear/+bug/311859) - and this one, please confirm and put wishlist as the priority, Its a packaging request.

By confirm I mean changing the status in launchpad of each one, not just saying confirmed :) Thanks

---

### Post by tawmas on 2009-02-11
> **taavikko said:**
> Did you tweaked your eee? adviced by some [www.site](www.site)...
If you have directed your logs to RAM (edited fstab)

... Just a thought ...

Ouch! How could I not think about that? Of course I did!

---

### Post by tawmas on 2009-02-11
> **Nullack said:**
> OK fellow testers :)

[https://bugs.launchpad.net/ubuntu/+bug/328131](https://bugs.launchpad.net/ubuntu/+bug/328131) - can someone please confirm this one its the whitespace theme issue weve been discussing.

[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/328130](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/328130) - and confirm this one too - its new, gparted doesnt know about EXT4.

[https://bugs.launchpad.net/ubuntu/+source/flightgear/+bug/311859](https://bugs.launchpad.net/ubuntu/+source/flightgear/+bug/311859) - and this one, please confirm and put wishlist as the priority, Its a packaging request.

By confirm I mean changing the status in launchpad of each one, not just saying confirmed :) Thanks

Ok, I confirmed #328130. I cannot reproduce here #328131 so I cannot confirm it. As for #311859, I don't have the permissions to set the bug priority, so I'd rather not touch that bug...

---

### Post by Kevbert on 2009-02-12
Nullack, do you still get the logfile error ? I no longer get it.
Can someone confirm this bug in Kubuntu:
Window to edge of screen doesn't show on second desktop Bug [COLOR="Red"][326128]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/326128")[/COLOR]
Thanks.

---

### Post by Gourgi on 2009-02-12
logfile error present here too ...
i added "affects me too" to LP bug report

[[IMG]http://img156.imageshack.us/img156/1294/screenshotlb9.th.jpg[/IMG]](http://img156.imageshack.us/my.php?image=screenshotlb9.jpg)

---

### Post by ronacc on 2009-02-13
confirmed  "whitespace"
confirmed  "flightger" , it wouldn't let me change the priority though .
also I'm now seeing the logfile error here .

---

### Post by Nullack on 2009-02-13
Thanks guys

---

