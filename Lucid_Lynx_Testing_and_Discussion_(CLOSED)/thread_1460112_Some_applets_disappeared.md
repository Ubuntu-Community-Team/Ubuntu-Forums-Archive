---
title: "Some applets disappeared"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Phentis on 2010-04-22
After the latest update (pre-RC), my language and Network applets have disappeared:

[IMG]http://s50.radikal.ru/i130/1004/4e/92e1921397b9.png[/IMG]

How can this be fixed?

Thanks in advance!

---

### Post by 23meg on 2010-04-22
Make sure you have "Notification Area" added to your panel. If it's not, right click empty space on your panel, click "Add to Panel" and choose "Notification Area".

---

### Post by ajgreeny on 2010-04-22
For the time being at least, you must have both **notification area** and **indicator applet** in the panel to show all the icons you are used to seeing.

---

### Post by Phentis on 2010-04-23
Thanks, solved :)

---

### Post by xeddog on 2010-04-24
I have read several things about network manager not appearing in the notification area, but none of the work-arounds have help me.  I cannot get the network manager applet in my upper panel, and have not been able to for quite some time (meaning months).  The volume is not there either, but I can at least get that one if I add the Indicator applet to the panel.  Problem there is that if I add the indicator applet I get things I don't want like mail.  

The things I have tried so far:
[LIST=1]
[*]Remove and re-add the notification area.
[*]Remove and re-add the indicator applet.  Both with and without the notification area in place.
[*]I saw one thread that said to comment a line in /etc/networks/interfaces but I did not have that particular line.
[*]Tried opening a terminal and running "sudo networkmanager &" which doesn't seem to have done anything at all.
[*]Also tried that with nm-applet to no avail.
[/LIST]

anything else I can try??

xeddog

By the way, I am running Lucid with the latest updates as of 4/24 using wired network only.  As I said, I have not had the network manager applet in the notification area for a long time.  I was just waiting for it to be fixed, but perhaps it isn't going to be.  At least for me.

---

### Post by zurien on 2010-04-24
had the same thing happen to me (answering xeddog)
tried many things, only thing that fixed (reset) it was doing the following:

# rm -r ~/.gconf/apps/panel or just move the folder elsewhere if you want to back it up.
# Log out of Gnome, then back in.

your panels should have reset back to original state.

---

### Post by xeddog on 2010-04-24
Thanks zurien, but it didn't work.  The panels were reset back to defaults, but I was still not able to get networkmanager in the notification area.   ](*,)](*,)

xeddog

---

### Post by xeddog on 2010-04-24
Ok.  I got it.  I had to edit /etc/network/interfaces and comment everything except the "auto eth0" and reboot.  When the system came back up it was using dhcp to obtain an IP address so I had to go to the networkmanager applet and edit back in all of my static ip information.

I am assuming that networkmanager now keeps it's information somewhere else because the contents of /etc/network/interfaces has not changed to reflect the fact that I entered a new interface called "Default" and deleted the "auto eth0".  It still has the old info.

xeddog

---

### Post by Brian Vaughan on 2010-04-24
> **zurien said:**
> had the same thing happen to me (answering xeddog)
tried many things, only thing that fixed (reset) it was doing the following:

# rm -r ~/.gconf/apps/panel or just move the folder elsewhere if you want to back it up.
# Log out of Gnome, then back in.

your panels should have reset back to original state.

I'd been wondering what the simplest way was to do that.

---

