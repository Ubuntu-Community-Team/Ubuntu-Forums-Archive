---
title: "Can't unlock panel in UNE"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dave1403 on 2010-02-26
I've just installed the Alpha3 UNE version on my Netbook.
Now i have the problem that the top panel seems to be locked completely. I can't rearrange/add or delete any icons.
The text for unlocking them is greyed out and unclickable.
In karmic I managed to change up the panel but lucid just doesn't seem to let me do that...
Is there anything I'm missing here? (probably there is ;) )
If you know what's wrong please help!

---

### Post by gmoore777 on 2010-03-13
I have same problem. (Dell Inspiron Mini10. It came with HardyHeron, but I clobbered that with the Netbook remix for LucidLynx)
I tried to `sudo gconf-editor` and unclicked Locked for the notification applet and one or two others, then logged out and back in and that did nothing. I was trying to follow the very excellent posting here
[http://swiss.ubuntuforums.org/showthread.php?t=1312335&page=3](http://swiss.ubuntuforums.org/showthread.php?t=1312335&page=3)
by tom4jean, but none of panel manipulation was possible. Very frustrating. This posting is the only one about this problem of the panels all being locked and grayed out and no free space in the menu bar to begin to squeeze in any more.
Anyways, I am clobbering my Netbook installation with the regular 32-bit version of LucidLynx, since i can't wait for an answer and I really don't want a different interface than the ones I'm using on home desktop and on all the machines at work.

---

### Post by cariboo on 2010-03-13
You can select the regular desktop from the login screen, no need to reinstall.

---

### Post by rudy.b on 2010-03-20
I have the same issue on my netbook.  I found a bug report in launchpad regarding this, and it basically says that the locked panels in UNE is by design for some technical reason I don't understand.  It does also describes a workaround that is available, but there are some tradeoffs:  apparently you won't have the regular Gnome session available any longer in GDM.

The bug report: [can't  add, move, unlock applets & no clock]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/519583")
The workaround: [UbuntuNetbookEditionConvertGnomeSession]("https://help.ubuntu.com/community/UbuntuNetbookEdition/ConvertGnomeSession")

Note: I haven't tried the workaround yet, so I can't offer an opinion on it's results.

---

### Post by cariboo on 2010-03-20
I'm running Lucid UNR fully up-to-date, and have the choice of:

[list]
[*] Failsafe Gnome
[*] Gnome
[*] Ubuntu Netbook Edition
[*] Ubuntu Netbook Edition 2D
[*] Xterm
[/list]

At the GDM Login screen

---

### Post by victor9098 on 2010-03-20
Hey I started a thread on this issue, if you want to take a look [Click Here]("http://ubuntuforums.org/showthread.php?t=1429426").

I found out the reason why and a few options for unlocking the panels!

Hope it helps :)

---

### Post by rudy.b on 2010-03-21
> **cariboo907 said:**
> I'm running Lucid UNR fully up-to-date, and have the choice of:

[LIST]
[*] Failsafe Gnome
[*] Gnome
[*] Ubuntu Netbook Edition
[*] Ubuntu Netbook Edition 2D
[*] Xterm
[/LIST]

At the GDM Login screen

Ok, so I've been playing with the "Gnome" session and the panel is changeable in there.  So what exactly are the differences between UNE and Gnome sessions (other than the fact we can't change the panel in UNE)?  They look almost identical on my system (after I modify the panel to add the go-home-applet to bring up the netbook-style desktop/launcher).

---

### Post by cariboo on 2010-03-21
I believe it's maximus that controls what can and can't be done.

---

