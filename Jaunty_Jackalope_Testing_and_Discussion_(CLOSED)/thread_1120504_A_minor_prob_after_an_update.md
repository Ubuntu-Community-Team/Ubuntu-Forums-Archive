---
title: "A minor prob after an update"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Thura on 2009-04-09
After updating to Jaunty, everyth works fine. ( Acutally, it wasn't, but it is now ;) But, I have one minor problem. When I login (gdm), it displays a completely black screen around 10 seconds and only after that it loads the gnome panels, desktop, compiz ... blah blah blah ...
Any idea, why the black screen is appearing ?
Where should I check for the logs ?

---

### Post by zoldiel on 2009-04-09
That sounds normal actually, the background color for the new GDM theme is black, whereas before it was a tannish color, and you will see that after logging in before the desktop is loaded. 10 seconds seems a little lengthy, but it depends on your system. Did it seem to load more quickly before?

---

### Post by Thura on 2009-04-09
I have been using since Hardy but it never took that long and never saw gdm background that long. Besides, it is not just taking just 10 seconds, it is just showing black screen ( Yep black because gdm background was black ) for 10 second, after that it loads gnome-panels for 5 seconds then 5 seconds for compiz ... Before, it just loads gnome-panels directly ... I mean it directly shows ( load ) gnome-panels as soon as I log in ...

---

### Post by zoldiel on 2009-04-09
You can try this to see whats processes are taking the longest to load and using the most resources:

At the GDM login switch to tty1 (ctrl+f1)
run top (use shift+P to sort by processor usage)
switch back to the GDM (ctrl+f7) and log in
switch back to tty1 and watch which processes are running, look for anything using a very high cpu usage for more than a few seconds. 

If you are using compiz when you switch back to X you may only see a white screen, if that happens use alt+f2 to run compiz --replace to get your desktop back.

---

### Post by Thura on 2009-04-09
Thanks, I tried that ... it is Xorg eating 99% to 100% ...

---

### Post by Thura on 2009-04-09
After a google search, it seems nvidia is the evil.
[https://bugs.launchpad.net/ubuntu/+bug/178400](https://bugs.launchpad.net/ubuntu/+bug/178400)
[http://magazine.redhat.com/2007/11/20/tips-and-tricks-why-does-xorgs-cpu-usage-shoot-up-when-using-nvidias-driver/](http://magazine.redhat.com/2007/11/20/tips-and-tricks-why-does-xorgs-cpu-usage-shoot-up-when-using-nvidias-driver/)
I will try adding Option "UseEvents" "True" to my xorg.conf !

---

### Post by frodon on 2009-04-09
Moved to jaunty testing and discussion forum.

---

### Post by Thura on 2009-04-09
Adding Option "UseEvents" "True" to xorg.conf doesn't help, still taking too long.

---

### Post by zoldiel on 2009-04-10
Are you using the latest version of the nvidia driver, version 180? I believe this was released after the beta as it was not initially available when I did a clean 9.04 beta install.

---

### Post by Thura on 2009-04-10
Yeah, I have tried with all versions of nvidia, incluing glx-173, glx-180 from the repository ... Previously, I have been using glx-173, and have no prob, I even tried installing the latest package 180.44 manually from nvidia.com ... It makes no difference ...

---

