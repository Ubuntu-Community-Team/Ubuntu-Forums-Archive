---
title: "Trying out 10.04 downloaded today"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by A_Nonny_Moose on 2010-04-11
I had need of a new CD to I went to the main site.  I found that 10.04 beta 2 was on offer and make the following comments:

[LIST=1]
[*]I have an nvidia geforce2 card and couldn't the nvidia-96 driver to load despite several attempts.
[*]The new decor has mouse positioning problems.  Wants the mouse to be slightly above the item.  This also applies to the installer.
[*]Could not modify the root password.  Probably due to ignorance, but there was need to get onto root.  The default root password needs to be published.
[*]The new user properties editor was the cause of 3.  I don't like it.
[*]The new decor was interesting, but I don't like moving the windows controls from the upper right to the upper left, especially when the mouse is off.
[*]I eventually locked out my own ID, and gave up.  I formatted the partition I had put this on as it had become useless.
[*]If you only have a week or so to go to the LTS release, you need to test this a lot more.
[/LIST]

---

### Post by uRock on 2010-04-11
Did you file bug reports?

To move the buttons to the left, open appearance and select a different theme.

---

### Post by A_Nonny_Moose on 2010-04-15
Where there was a discernable bug, yes.

Latest adventure:  I pulled necessary data onto my copy of 9.10 from mail inadvertently received during testing then re-installed from the disk.  After a complete update, everything seems to be working including nvidia-96.
There was one exception:  I did a log out to change to another id, and the previously described gdm loop occurred.  A restart sort of solved this.

---

### Post by spcwingo on 2010-04-15
> **A_Nonny_Moose said:**
> 
3. The default root password needs to be published.


Ubuntu does not have a root password...the root account is locked by default.  You can still gain temporary root privileges with the sudo command (or gksu/gksudo on GUI apps).

---

### Post by Slim Odds on 2010-04-15
> **A_Nonny_Moose said:**
> ...
Could not modify the root password.  Probably due to ignorance, but there was need to get onto root.  The default root password needs to be published.

LMBO, cmon ... you're joking.... right?

Publish a default root password...... har de har har

---

