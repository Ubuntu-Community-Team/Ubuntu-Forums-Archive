---
title: "Karmic in VirtualBox changed my Jaunty settings"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by timgood on 2009-10-19
Here is something strange. I installed the Karmic Beta on VirtualBox running on my 64 bit Jaunty machine. I started Karmic and had some problems with the display resolution which led to corruption of gnome-panel. I eventually changed gnome-panel back to default by running 'rm -r ~/.gconf/apps/panel' in terminal which successfully restored gnome-panel after a log-out. 

When I exited VirtualBox I powered my machine down for a while. When I turned it back on I found that my Jaunty gnome-panel had also been set to default, losing all my settings. I had been experiencing problems with VirtualBox, compiz and transparency, with the Karmic window losing focus everytime a Rhythmbox or Skype notification popped up, and I was wondering if this may have caused the problem. If it did - major security implications. Has anyone else had this problem or similar?

Later: also found out that my Evolution Mail account settings were lost, as were my Compiz settings.

Even later: Found that someone else has had this problem running Karmic Alpha with Jaunty host: [http://ubuntuforums.org/showthread.php?t=1281189](http://ubuntuforums.org/showthread.php?t=1281189)

This must be a major security issue.

---

### Post by marshmallow1304 on 2009-10-19
Did you set up any folder sharing?

---

### Post by timgood on 2009-10-19
No, I did not.

---

### Post by marshmallow1304 on 2009-10-19
Then I'm at a loss.  I would not think such a thing would be possible. :confused:

---

### Post by timgood on 2009-10-20
Having checked bash history on the host I found a command which I assumed had been typed in a guest terminal. Here is what I think happened:

Went to launch a terminal in Karmic (guest) and Rhythmbox on Jaunty (host) popped up a notification causing the Karmic window to lose focus and the Jaunty taskbar to grab it. Terminal was launched in Jaunty and showed above the Karmic desktop as if it was a Karmic terminal, leading to the mistake. 

If you have these problems with Compiz and VirtualBox, beware! You may not be launching the application you think you are launching!

---

### Post by marshmallow1304 on 2009-10-20
Makes sense.  Maybe use different themes for the host and the guest so you can tell them apart.

---

