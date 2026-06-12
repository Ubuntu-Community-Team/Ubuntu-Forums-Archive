---
title: "I can get to the login screen, but when I hit enter eveything turns black...?"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by MaestroDT on 2010-11-30
I'm trying to install the latest version of Ubuntu Studio. I tried it a few months ago with my HP... a live system worked fine, but when I installed it, it would go blank after the splash screen. I assumed it was some sort of incompatible graphics driver and gave up since I don't know enough about Ubuntu yet.

Now I have a spare Dell XPS desktop sitting around and I got the latest version of Ubuntu Studio and tried it again. The install goes by perfectly, this time the welcome screen actually comes up and I can see my username. As soon as I hit enter, which I imagine should bring up the password prompt, the entire screen goes black and won't respond to anything. 

Anyone have any suggestions for me?

---

### Post by mörgæs on 2010-11-30
Does adding boot options help?

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by MaestroDT on 2010-11-30
I'm not booting from the LiveCD though... I'm booting from the installation I just made.

---

### Post by mörgæs on 2010-11-30
Yes, but still adding boot options might solve the problem.

---

### Post by MaestroDT on 2010-11-30
ok, well how do i change the boot options for my installation and not for the livecd?

---

### Post by mörgæs on 2010-12-02
There are lots of descriptions in the fora about doing so. One of them is here:
[http://ubuntuforums.org/showpost.php?p=10180833&postcount=3](http://ubuntuforums.org/showpost.php?p=10180833&postcount=3)

---

### Post by srikanth.gundaz on 2010-12-02
> **mörgæs said:**
> There are lots of descriptions in the fora about doing so. One of them is here:
[http://ubuntuforums.org/showpost.php?p=10180833&postcount=3](http://ubuntuforums.org/showpost.php?p=10180833&postcount=3)

However you have installed fresh copy of Ubuntu Studio right, go ahead and re-install and check once :)   If problem occurs again, then your .iso file of Ubuntu Studio might be corrupted.

---

### Post by BlueSpecial on 2010-12-02
Try add 

> acpi=off noapic nolapic

after

> quiet splash

on boot options.

---

