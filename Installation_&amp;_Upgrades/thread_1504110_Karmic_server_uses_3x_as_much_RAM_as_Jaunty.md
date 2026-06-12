---
title: "Karmic server uses 3x as much RAM as Jaunty"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by SabreWolfy on 2010-06-07
Ubuntu Jaunty i386 server used 8% of the available 2GB RAM. After upgrading to Karmic, usage is now at 30%. Any ideas? Seems many more mysqld instances running ... ?

---

### Post by SabreWolfy on 2010-06-07
Two restarts later and it's now down to 5% :)

---

### Post by SabreWolfy on 2010-06-07
Back to 30% after another reboot. How can memory usage fluctuate so much between reboots of a server?

---

### Post by tgalati4 on 2010-06-07
When you set up a new system, there are several databases that need to be initialized.  They take CPU cycles and RAM.  How else would you find a file using the locate command?

locate which
which locate
apropos which

The only time you really need to worry about RAM is when /swap starts filling.  Use the free command:

free

If you reboot one more time, your server will bite you.

---

### Post by SabreWolfy on 2010-06-07
A headless no-X/GUI server idling should NOT be using over 600MB of RAM under Lucid, when it used 20% of that under Karmic.

---

### Post by tgalati4 on 2010-06-07
Are you running any Landscape monitoring stuff?

apropos landscape

---

### Post by SabreWolfy on 2010-06-08
> **tgalati4 said:**
> Are you running any Landscape monitoring stuff?

apropos landscape

Nope. I've restarted and it's back to 7%, which is fine. I'll have to see how much it uses after the next restart.

[Others]("http://ubuntuforums.org/showthread.php?t=1494054") are experiencing this too. LaunchPad bug search has been timing out for two days, so I can't check there.

---

### Post by SabreWolfy on 2010-06-21
Threads [here]("http://guide.ubuntuforums.org/showthread.php?t=1494054") and [here]("http://ubuntuforums.org/showthread.php?t=1490677") for reference.

---

### Post by SabreWolfy on 2010-06-21
See [here]("http://guide.ubuntuforums.org/showpost.php?p=9491797&postcount=16").

---

