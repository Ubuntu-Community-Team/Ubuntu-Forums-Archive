---
title: "lucid netbook won't go beyond unetbootin"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by f1champ on 2010-04-30
I boot up lucid final netbook version on acer aspire one 250, it gets stuck at unetbootin.
automatic start in 10 sec, countdown to zero then it restart countdown...

---

### Post by hackworth on 2010-05-02
i have this same issue. prepared usb stick using unetbootin on fedora 12. is there a better way to write the .iso to usb on this platform?

---

### Post by snowpine on 2010-05-02
Ubuntu has its own usb-creator that is more reliable than Unetbootin:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by hackworth on 2010-05-02
well, that is great, but as i said, i am not running ubuntu. yet.

---

### Post by snowpine on 2010-05-02
> **hackworth said:**
> well, that is great, but as i said, i am not running ubuntu. yet.

Keep reading... :)

[https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows)

---

### Post by hackworth on 2010-05-02
sorry, not on windows, either._ like i said, i'm running fedora 12, which does not have an implementation of usb-creator_, from what i can tell. trying to write the iso to usb using unetbootin, dd or LiveUSB creator does not work, which is why i specifically asked if there was another method for my platform, fedora 12. or any generic, non-ubuntu linux distro.

---

### Post by snowpine on 2010-05-02
Sorry, I confused you with the OP. :)

---

### Post by tuxcantfly on 2010-05-03
> **f1champ said:**
> I boot up lucid final netbook version on acer aspire one 250, it gets stuck at unetbootin.
automatic start in 10 sec, countdown to zero then it restart countdown...

Hi, I'm the developer of UNetbootin. This is an issue related with the syslinux version on your computer being outdated; if you're not already using it, could you try again with the latest upstream binary (not distribution package), ie [http://unetbootin.sourceforge.net/unetbootin-linux-latest](http://unetbootin.sourceforge.net/unetbootin-linux-latest)

---

### Post by f1champ on 2010-05-04
I've tried with the latest unetbootin binary with the same result. It keeps looping.

The lucid desktop iso works fine however. That leads me to believe there's something wrong with the netbook remix?

---

### Post by allaboutmike on 2010-08-05
Did we ever find a resolution for this? I have struck the same issue. Netbook version loops, desktop works. I'd really like to try the netbook version on my eee pc if I can figure this out.
Mike

---

