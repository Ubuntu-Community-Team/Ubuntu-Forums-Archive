---
title: "Installation errors"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by Sax Salute on 2011-02-09
I am installing Ubuntu for the first time as a result of my Programming teacher starting me on a webserver project that will not work on windows. I dug up an older Dell, about 5 years old, and I keep getting install errors Just under halfway through. The OS will completely freeze for a few minutes then say 'errno 5'. Anybody have an idea?

---

### Post by tommcd on 2011-02-09
When you first boot the Ubuntu live CD, be sure to run the option "*Check CD for defects*". If the CD integrity check passes with out errors, then the disc is good: [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
If it reports bad files, then you have a corrupted disc.

If you are burning the Ubuntu CD from Windows, try using Iso Recorder or Infra Recorder, and be sure to burn the CD at the slowest possible speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Sax Salute on 2011-02-09
Just put in the new CD burnt at lowest speed. Well see... How did you get to that menu shown in the first link you provided? I'm using 10.10 by the way, maybe that's a previous version's boot menu?

---

### Post by Sax Salute on 2011-02-09
Didn't burn correctly )= I'll give it a shot tomorrow.

---

### Post by tommcd on 2011-02-10
> **Sax Salute said:**
>  How did you get to that menu shown in the first link you provided?
It used to be the first page you saw when you booted the Ubuntu live CD. This was very convenient, so the Ubuntu devs apparently decided to "fix" that.
 I am not sure if it still is there on the first page since I always use the alternate install (text based) CD to install Ubuntu. If you don't see the option to check for defects when you first boot Ubuntu, try hitting the space bar to get the option to check the CD: [http://askubuntu.com/questions/5996/unable-to-mount-dev-loop0-during-install](http://askubuntu.com/questions/5996/unable-to-mount-dev-loop0-during-install)
Or you may need to hit F6 or some key to get the option to check for defects.
> **Sax Salute said:**
> 
 I'm using 10.10 by the way, maybe that's a previous version's boot menu?
Yes it is. The option to check the CD for defects is still there somewhere though.
> **Sax Salute said:**
> 
Didn't burn correctly )= I'll give it a shot tomorrow.
If you are burning the CD from Windows, try using Iso Recorder or Infra Recorder, as per the second link in my last post.

It is also a good idea to check the md5sum of the iso image you downloaded to be sure it is not corrupted: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by P4man on 2011-02-11
> **tommcd said:**
> It used to be the first page you saw when you booted the Ubuntu live CD. This was very convenient, so the Ubuntu devs apparently decided to "fix" that.
 I am not sure if it still is there on the first page since I always use the alternate install 

The option is still there. Ubuntu devs in their infinite wisdom assume everyone understands that this icon:
[IMG]http://img829.imageshack.us/img829/3509/dgfdgrunningoraclevmvir.png[/IMG]

is not there to look shiny, it really means "If you want to see a hugely useful menu, press spacebar *NOW* - and hurry up because you have about 2 seconds, even if this logo remains visible for much longer". Cant argue against such logic, can you :(

---

### Post by kansasnoob on 2011-02-11
> **P4man said:**
> The option is still there. Ubuntu devs in their infinite wisdom assume everyone understands that this icon:
[IMG]http://img829.imageshack.us/img829/3509/dgfdgrunningoraclevmvir.png[/IMG]

is not there to look shiny, it really means "If you want to see a hugely useful menu, press spacebar *NOW* - and hurry up because you have about 2 seconds, even if this logo remains visible for much longer". **[COLOR="Red"]Cant argue against such logic, can you[/COLOR]** :(

I tried:

[https://lists.launchpad.net/ayatana/msg02038.html](https://lists.launchpad.net/ayatana/msg02038.html)

---

### Post by P4man on 2011-02-11
And you even got a (sort of) reply from his Holiness himself :). I find it hard to navigate the web mailing list though, did you get some kind of argument to support this change?

---

