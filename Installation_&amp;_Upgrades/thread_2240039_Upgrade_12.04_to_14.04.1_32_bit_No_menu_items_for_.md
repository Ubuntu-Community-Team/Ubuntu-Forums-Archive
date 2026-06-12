---
title: "Upgrade 12.04 to 14.04.1 32 bit No menu items for any app in task bar"
date: 2014-08-17
forum: Installation &amp; Upgrades
---

### Post by roger_1960 on 2014-08-17
Hi

Just did online upgrade of 12.04 with latest updates to 14.04.1 and all seemed to go well except:

When I boot up I get a "error malformed file.." press any key appearing in the top left corner.  Pressing any key makes it continue OK.

Once booted, for _all_ applications, mousing over the task bar causes the application title to disappear, but no menu items appear, just the three buttons at the left. I do have settings set for the menu items to be in the task bar rather than in the window.

Any ideas/solutions.

Roger

---

### Post by kansasnoob on 2014-08-17
>  When I boot up I get a "error malformed file.." press any key appearing in the top left corner. Pressing any key makes it continue OK.

Sounds like this bug:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247)

> Once booted, for all applications, mousing over the task bar causes the application title to disappear, but no menu items appear, just the three buttons at the left. I do have settings set for the menu items to be in the task bar rather than in the window.

It's not clear to me what desktop environment you're running, is it Unity?

---

### Post by roger_1960 on 2014-08-17
Yes, standard unity as installed. I have it installed on another machine which runs it as expected with the menu items appearing in the task bar.

---

### Post by roger_1960 on 2014-08-17
Just changed the install to use gnome metacity and all applications have their menus EXCEPT "files" which does not.  I think I'm going to buy a dvd and do a fresh install (the laptop doesn't boot from usb).  Still open to ideas..

Roger

---

