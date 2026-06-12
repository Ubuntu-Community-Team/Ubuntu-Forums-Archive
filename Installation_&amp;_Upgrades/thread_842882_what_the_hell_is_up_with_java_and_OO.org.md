---
title: "what the hell is up with java and OO.org?"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by CC_machine on 2008-06-27
installed kubuntu 8.04 on my laptop, running flawlessly. I installed ubuntu-desktop since i like GNOME too, also ran flawlessly, until i installed the Ubuntu Studio theme. i just installed the theme and not the packages, because i like to save bandwidth.

now i notice openoffice doesnt work. i ran oowriter in a terminal and it told me it couldnt find a java runtime envionment. It was installed. What's going on? so i went into synaptic and noticed that the OpenOffice.org package was not installed, however oowriter and the other individual packages were there. So i installed it, and it reinstalled java.

and so to my second what-the-hell-is-it-doing moment: it sat there for >30 minutes telling me it was configuring java-docs. Huh? so i expand "details" and the terminal had been sitting there wasting my time telling me to MANUALLY DOWNLOAD A FILE. uh, excuse me?

```

Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

```
:lolflag:
i thought the apt package manager was supposed to manage this sort of work automatically, and so i told it no. I use Linux to get away from the installer and updater nightmare that comes with Windows. after asking me again 3 times it gave in and told me the package failed, but it was still marked as installed in synaptic. Meh. Only docs, shouldn't make any difference.

Except OOo still doesnt work. launching from the gnome menu does nothing, and in a terminal oowriter just dies (or deteches from terminal, ?) within a second, while openoffice sits there and does nothing, giving no output. I have to ^C it. no OOo window pops up :(

sorry for the offensive tone of this post but it's really surprised me that the grand Advanced Packaging Tool on the #1 used Linux distribution in the world would tell me to manually grab a file, as if i was some sort of idiot.

*edit: just noticed "sudo oowriter" works just fine, but then tells me my user already has OOo running and i should close it, even though i havent and "openoffice" nor "oowriter" is listed in gnome-system-monitor as a process. 0.o i'll try a reboot.*

any help greatly appreciated, CCmachine

---

### Post by Hagar Delest on 2008-06-28
See that thread perhaps: [[Solved] Some wizards receive defective JRE error]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=5463").

---

