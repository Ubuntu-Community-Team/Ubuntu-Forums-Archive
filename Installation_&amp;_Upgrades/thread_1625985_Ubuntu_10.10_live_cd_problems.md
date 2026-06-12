---
title: "Ubuntu 10.10 live cd problems"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by ChronicMetamorphosis on 2010-11-19
A few nights ago, I was trying to set up a tv tuner card and I somehow ruined my OS. When I log into Ubuntu, all I get is errors and a blank screen.

Since it was an older version, I decided to upgrade to the latest version, 10.10. So I figure that I get a live cd, transfer all my wanted files to an external drive, then install the new OS. I got the live cd and when I boot it, I get some picture at the bottom of my screen with some stick figure and what looks like a piece of film, then my monitor resets and says "Out of range"

What can I do to fix this problem? I am currently on a Knoppix 2.6 live cd.

---

### Post by mörgæs on 2010-11-21
The picture you are talking of is 'keyboard-man', though it has been interpreted as a whole lot of other symbols. It means 'press any key to get to the menu'.

Have you copied all you files using the Knoppix cd?

---

### Post by sikander3786 on 2010-11-23
You need to get into that menu by pressing any key as suggested above.

Then press F6 and enable the **nomodeset** parameter and continue booting. It should take you to the desktop this time.

See here for boot parameter details.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by ChronicMetamorphosis on 2010-11-25
Hey that worked! Thanks a lot for your input, you two.

---

### Post by mörgæs on 2010-11-26
You are welcome. Please mark the thread 'solved'.

---

