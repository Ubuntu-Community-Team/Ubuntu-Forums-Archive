---
title: "Unable to install Kubuntu 11.10 in Acer Aspire 4736."
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by vamc on 2011-11-25
I am trying to install Kubuntu 11.10 on Acer Aspire 4736. When I boot into live mode, Kubuntu screen shows up. After I select "Start Kubuntu", I got a blank screen, a display problem since 11.04. "setpci" and a torch light solved this problem. All I found is a command prompt showing some errors. The screenshot attached has the information about the error (It is a VirtualBox screenshot). I could not find a way to start GUI. "startx" returns the following error:
```
-bash: /usr/bin/startx: Input/output error
```

How can I install Kubuntu now?
Why is Kubuntu behaving this way?

---

### Post by dabl on 2011-11-25
The posted error message does not appear to have any relationship to the failure to load X.  Also, I found that Kubuntu has previously been installed successfully on that model, although a couple years ago, and with an ethernet issue that was resolved:

[http://kubuntuforums.net/forums/index.php?topic=3105338.0](http://kubuntuforums.net/forums/index.php?topic=3105338.0)

My I suggest you try installing from the "Alternate Install" CD?  I've always had better luck using that one for installation, and it also has more packages on it (but no GUI).  Once the OS is installed, Google for boot codes that might be needed for that model -- you might find this:

[http://ubuntuforums.org/showthread.php?t=1789447](http://ubuntuforums.org/showthread.php?t=1789447)

---

### Post by vamc on 2011-11-25
I've used Kubuntu 9.10 before. It worked perfectly without any issues.

---

### Post by dabl on 2011-11-25
And what about this:  [http://ubuntuforums.org/showthread.php?t=1789447](http://ubuntuforums.org/showthread.php?t=1789447)

:confused:

---

### Post by vamc on 2011-11-30
> **dabl said:**
> And what about this:  [http://ubuntuforums.org/showthread.php?t=1789447](http://ubuntuforums.org/showthread.php?t=1789447)

:confused:
Thanks, but no luck with that too.

I've installed 10.10 and upgraded it to 11.04 and that works fine. I will stick to this until the back light problem is fixed.

---

