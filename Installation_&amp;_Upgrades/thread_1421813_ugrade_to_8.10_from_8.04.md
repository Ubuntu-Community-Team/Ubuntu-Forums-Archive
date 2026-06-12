---
title: "ugrade to 8.10 from 8.04"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by chrisk2k on 2010-03-04
received this message upon restarting laptop after upgrading "server authorization directory(daemon/servauthdir) is set to /var/lib/gdm but is not owned by user 106 and group 114. please correct ownership or gdm configuration and restart gdm.
Please advise next step.
thanks

---

### Post by mikewhatever on 2010-03-04
I don't think upgrading to 8.10 is the best idea. Intrepid's support is ending in less then two month, and at the same time, when Lucid is out, you'll be able to upgrade to it.
Just out of curiosity, what's the ownership of /var/lib/gdm?

ls -ld /var/lib/gdm

---

### Post by chrisk2k on 2010-03-05
thanks for responding.  I don' really know what the system means by "ownership".  I don't have any problem at all with upgrading to the latest stable version of ubuntu, but I was under the impression ( perhaps wrongly) that I could not do it directly from 8.04 and still retain all my current settings.  At this point I am stuck -- I can boot up and get into f2 settings but ubuntu 8.10 won't boot past the point where the screen came up asking for ownership.  Can I just down load ubuntu 9.10 and start from scratch and retain my current settings?

I very much appreciate any guidance you or anybody can give me!

---

### Post by viper250 on 2010-03-05
as long as your system supports it do a clean install of 9.10!
you will probably like it better.
in most versions of linux you can usually use the terminal app  then log in as super user (su) and use the chown command (change owner) but you have to be logged in as admin to do that

---

### Post by freeztar on 2010-03-05
I have no idea why you would want to stay with 8.04 or 8.10. Personally, a lot of trouble issues on my laptop were resolved by upgrading to 9.04. From there, an upgrade to 9.10 was easy and uneventful (always good!). 

If you want to save your settings, it's perhaps hit or miss, but you can always manually backup the folders that the settings are stored in (for example /home) and rewrite.

---

### Post by mikewhatever on 2010-03-05
> **chrisk2k said:**
> thanks for responding.  I don' really know what the system means by "ownership".  I don't have any problem at all with upgrading to the latest stable version of ubuntu, but I was under the impression ( perhaps wrongly) that I could not do it directly from 8.04 and still retain all my current settings.  At this point I am stuck -- I can boot up and get into f2 settings but ubuntu 8.10 won't boot past the point where the screen came up asking for ownership.  Can I just down load ubuntu 9.10 and start from scratch and retain my current settings?

I very much appreciate any guidance you or anybody can give me!

First, you can upgrade from one LTS to the next, in other words, from 8.04 to 10.04. Whether it goes well or not is another question. Anyway, upgrading to an OS that only has two months of support left didn't make sense to me.

You can check the ownership of /var/lib/gdm with the command I posted earlier. Try the recovery mode or live cd to get in. In karmic the ownership and permission are as follows:

drwxr-x--- 10 gdm gdm 4096 2010-02-21 11:21 /var/lib/gdm

If you need help resetting the ownership or permission, please post the output of that command.

You can always backup your home partition and important files before reinstalling.

---

