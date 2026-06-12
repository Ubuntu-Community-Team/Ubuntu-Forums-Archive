---
title: "Dreaded &quot;Over Range&quot; Problem with Edgy"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by winkerbean on 2007-08-25
Hi,
    I just upgraded to Edgy from Dapper (using the switch-dapper-for-edgy-in-sources.list-call-apt-get-update-etc. method).  [BTW, I'm using Kubuntu.]  Now, when I boot up, I get an "Over Range" error for my monitor (and nothing else) unless I boot up in 'recovery mode'.  A couple of questions I do not seem able to find answers to:
[LIST=1]
[*]Do I face any capability short-fall by only running my computer in 'recovery mode'?
[*]Regardless of the answer to the prior question, how do I fix this 'over range' problem?
[/LIST]
Forgive me if there exists a simple explanation in some basic documentation I overlooked.

Thanks.

---

### Post by Pumalite on 2007-08-25
You can fix it at the command line: sudo dpkg-reconfigure xserver-xorg Choose most defaults, choose 'vesa' as your driver. Then startx

---

### Post by winkerbean on 2007-08-25
Hi, Pumalite.
    Do I really want 'vesa' as the driver?  My graphics card is ATI.

---

### Post by Pumalite on 2007-08-25
You want 'vesa' now to get IN the system. Later you can choose appropriate driver for your card. ( vesa is a generic, jack of all trades kind of driver)

---

### Post by winkerbean on 2007-08-25
Thanks!  I'll give it a try!

---

### Post by Pumalite on 2007-08-25
You are welcome.

---

### Post by winkerbean on 2007-08-25
Alas, no luck.  I even lost the ability to enter in recovery mode for a while, until I copied my original (pre-upgrade) xorg.conf file back onto the system.

Any other suggestions would be most appreciated.  (BTW, "Get a Mac" is not an option at this time.  *wink*)

---

### Post by merlinus on 2007-08-25
You will have to look up your monitor specs -- try OEM website or google.

Then edit /etc/X11/xorg.conf to reflect these values.

-merlin

---

### Post by winkerbean on 2007-08-25
Thank you, Merlinus.
    Which specs would I need?

---

### Post by Pumalite on 2007-08-25
horiz and vert refresh rates, frequency

---

### Post by winkerbean on 2007-09-06
Hi, again.
    (I really don't like being a pest.)  I tried the specs from the manufacturer, but still received the same "Over Range" message.
    Does anybody think updating from Eft to Fawn would help?

Thanks.

---

