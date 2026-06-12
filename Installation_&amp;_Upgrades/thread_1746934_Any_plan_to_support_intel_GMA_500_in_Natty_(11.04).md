---
title: "Any plan to support intel GMA 500 in Natty (11.04)"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by musarraf172 on 2011-05-02
Hi all,

I have an INTEL GMA 500 based Nokia booklet 3g running ubuntu 10.10. The video playback is not upto the mark. I was thinking to upgrade it with natty 11.04 . But I am afraid of graphic support for GMA 500 (poulsbo).

Anyone found any work around??

---

### Post by fanum on 2011-05-02
> **musarraf172 said:**
> Hi all,

I have an INTEL GMA 500 based Nokia booklet 3g running ubuntu 10.10. The video playback is not upto the mark. I was thinking to upgrade it with natty 11.04 . But I am afraid of graphic support for GMA 500 (poulsbo).

Anyone found any work around??

There is some progress being made on this chipset, but natty is not supported out of the box yet. So far there are ways to run 2 of different drivers for this videocard, but both of them require some hacking, and a downgraded kernel. You can check the status here:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

you can also keep up to date on the progress on this forum thread:

[http://ubuntuforums.org/showthread.php?t=1229345&page=384](http://ubuntuforums.org/showthread.php?t=1229345&page=384)

---

### Post by hanzz on 2011-05-03
I am using a Asus EEE PC 1201 HA with intel GMA 500 graphics card.

using the poulsbo drivers as provided by this ppa:

[http://code.google.com/p/gma500/wiki/PPARepository](http://code.google.com/p/gma500/wiki/PPARepository)

worked fine on 10.10.

now I have made a fresh-clean installation of natty and tried to use
the brandnew packages for 11.04 (requires some hacking and a downgraded kernel as mentioned), but this broke video card support completely on my eee pc.

---

### Post by musarraf172 on 2011-05-03
> **fanum said:**
> There is some progress being made on this chipset, but natty is not supported out of the box yet. So far there are ways to run 2 of different drivers for this videocard, but both of them require some hacking, and a downgraded kernel. You can check the status here:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

you can also keep up to date on the progress on this forum thread:

[http://ubuntuforums.org/showthread.php?t=1229345&page=384](http://ubuntuforums.org/showthread.php?t=1229345&page=384)



Thank you very much.

I am following the threads u have mentioned. But still I am not having luck.

---

### Post by hanzz on 2011-05-18
any news on this. I am still having the video card driver support issue on my asus eee pc 1201ha (with intel gma500).

did anybody of you guys succeed?

---

### Post by mikewhatever on 2011-06-16
The old news is - Intel has no plans to support gma500.

---

