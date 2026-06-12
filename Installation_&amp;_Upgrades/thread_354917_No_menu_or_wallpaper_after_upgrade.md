---
title: "No menu or wallpaper after upgrade"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by flangemonkey on 2007-02-06
Hello,

1st post for me, so sorry if I miss out key info

I use xfce4 as my window manager

I upgraded (apt-get upgrade) and the next time I restarted X my wallpaper has disappeared, my desktop right-click menu no longer appears and my desktop icons have reappeared. (you can guess from my indignation, this is not the default ;))

the last package installed before the issue started was libpq4, in a single upgrade, I can't remember if I restarted X between updates (looking at the log file, it doesn't look like it)

[My dpkg.log file]("http://www.agrona.co.uk/dpkg.log.txt")

I have been through the settings in xfce4 settings-manager but they all appear correct :confused: 

Any more info, I will post; otherwise any help will be appreciated.

And if it helps, even though it is publicly humiliating (but the only way we learn) I did also recently remove myself from every group on the system and have to readd myself to all of the relevant groups. (not being able to open a CD drive is quite shocking, I even rebooted).

Thanks in advance

---

### Post by flangemonkey on 2007-02-07
yay, solved! well sort of.

It was a corrupt session file, creating a new session gave me the ability to change the settings back to where they belonged.

Thanks again ;)

---

