---
title: "Default OS load"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by dodgingspam on 2008-06-27
I installed Ubuntu in addition to XP. Currently when I boot I'm presented with a box to select from several Ubuntu kernel and XP at the bottom.

I'd like to set it up in such a way where XP will load by default, but have an option to call this OS select box or, if possible, hold some key to load Ubuntu.

Is it possible and if yes, how?

Thanks

---

### Post by Gallienus on 2008-06-28
Yes, it's possible.

1) Restart your system, and look at that box with the operating system options menu. Count which line the XP option appears on. (On my system it's the 8th line, but I customised my menu - yours may be different) While counting, you should also count the line that says "Other operating systems:".

2) As you're restarting anyway, log in as a user with administrative rights.

3) Open the terminal and type 'sudo gedit /boot/grub/menu.lst' to allow you to edit the menu. Before you are allowed to edit, you will have to type in your password.

4) Find the line that says 'default 0'. Replace that 0 with the line number of your XP option minus 1.  For example, if I wanted to boot XP by default, I would replace that 0 with a 7. (XP is option 8 on my menu, but numbering starts at 0, so I would type 7 instead of 8.)

5) Save your changes and reboot. XP should now be your default OS.

While you're editing the menu options, you may also like to make some other changes. Look for the 'timeout' and 'hiddenmenu' options, they may be of interest to you. Explanations are included right there in the menu.lst file.

---

### Post by dodgingspam on 2008-06-28
Perfect! Exactly was I was looking for. Thanks!

---

