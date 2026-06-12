---
title: "Flash issues after recent update"
date: 2012-04-01
forum: Installation &amp; Upgrades
---

### Post by tommyss4l on 2012-04-01
I just ran the latest flash update through the update manager and my flash is going crazy all over the place. Videos on youtube are not loading properly, and embedded videos aren't loading at all. Google music refuses to play at all saying flash is not working or disabled and goes into an endless refresh cycle. 

Anyone have any ideas about what happened or how to fix it?

---

### Post by lovinglinux on 2012-04-01
You could try the Beta version which is older than the one from the repositories. You can install it with 
[Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/).

If that doesn't help, try to disable hardware acceleration in flash settings. More info at [http://ubuntuforums.org/showthread.php?t=1949137](http://ubuntuforums.org/showthread.php?t=1949137)

---

### Post by tommyss4l on 2012-04-02
Ok so will installing flash-aid help Chrome?
Also, my issue isn't with all flash, just embedded videos and google music. My issue doesn't seem to be like that on the thread at all. Also the thread isn't exactly clear on where to find the hardware acceleration work around. I'll do more work on this tomorrow, but if you have any other ideas before then I'd gladly take them.

Thanks for the direction!

---

### Post by tommyss4l on 2012-04-02
OK, I have attempted the Flash-aid option, and no change with my issue, Firefox or otherwise

---

### Post by lovinglinux on 2012-04-02
> **tommyss4l said:**
> Ok so will installing flash-aid help Chrome?
Also, my issue isn't with all flash, just embedded videos and google music. My issue doesn't seem to be like that on the thread at all. Also the thread isn't exactly clear on where to find the hardware acceleration work around. I'll do more work on this tomorrow, but if you have any other ideas before then I'd gladly take them.

Thanks for the direction!

Although Flash-Aid just install on Firefox, it helps if you are also using Chrome 64bit or Chromium 32/64bit. However, if you are using Chrome 32bit, then you need to disable the plugin bundled with Chrome. You can do that by typing [noparse]about:plugins[/noparse] in the address bar.

To disable hardware acceleration, visit a video on YouTube, right-click on it and select Settings.

Although you issue is not described in that thread, I believe it can be fixed by disabling hardware acceleration. If not, then try clearing the cache and deleting flash cookies.


> **tommyss4l said:**
> OK, I have attempted the Flash-aid option, and no change with my issue, Firefox or otherwise

Did you run the Wizard successfully?

---

### Post by tommyss4l on 2012-04-02
OK running the wizard made everything work.
Thanks for the help!

---

### Post by lovinglinux on 2012-04-02
> **tommyss4l said:**
> OK running the wizard made everything work.
Thanks for the help!

You are welcome.

---

