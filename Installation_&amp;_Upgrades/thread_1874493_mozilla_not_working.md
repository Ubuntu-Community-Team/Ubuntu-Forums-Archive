---
title: "mozilla not working"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by president2 on 2011-11-03
I installed Ubuntu on a windows7 and accessed the internet with Mozilla the first time. Then I shut down came back up with windows and connected with chrome to the internet. Then I shut down and started Ubuntu and now I can not access the internet with Mozilla or updates etc.  I have checked the work offline and it is not checked.  I have wireless connection working but it will not find sever. I am absolutely new to Ubuntu so I know there is something I am not seeing here. Thanks for any help.

---

### Post by president2 on 2011-11-03
where do i click a quick response?

---

### Post by president2 on 2011-11-03
where do i click a quick response?

---

### Post by ballantony on 2011-11-03
This happened to me.  Try deleting the config folders in your home directory.  Open Nautilus and press ctrl+H to show hidden folders.  I can't remember if they're called .firefox or .mozilla Get rid of these and try again.

---

### Post by pavi_elex on 2011-11-03
Are you facing problem to access internet in firefox only or in all browsers of ubuntu?
Try seamonkey.
If you are facing in all browsers.
type ifconfig in terminal and see the output
output will be eth0, eth1, eth2 or eth4 like this
now type dhclient and your eth like following example. i have taken eth4.
$ dhclient eth4

---

### Post by president2 on 2011-11-03
I have not tried any other browsers yet. do not know what other broweser are there. Thanks for telling me about this new one. Will try little later at work now.

---

### Post by tokinho on 2012-09-27
> **ballantony said:**
> This happened to me.  Try deleting the config folders in your home directory.  Open Nautilus and press ctrl+H to show hidden folders.  I can't remember if they're called .firefox or .mozilla Get rid of these and try again.

Hey Thanks!!! I deleted the hidden folder .mozilla in the /home/bwat/.mozilla (my users folder is bwat) and firefox works again!!! XDXD

---

