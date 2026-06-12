---
title: "Trouble Making Home Directory"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by jimalan on 2007-01-09
I'm a new user and have read many posts that recommend having a separate Home directory.  When I tried to create one during my first install, the program wouldn't let me make it anything but a Primary, so I didn't bother with it and just let the CD perform a normal install on its own.  Later, I tried to modify the humongous Primary partition using the excellent instructions I found on psychocats.net.  Once again, when I shrank the big partition down to 10Gb and tried to create a Home partition with what was left, the only option I was allowed to choose was to make it another Primary.  The screenshot in the instructions showed it should be a Logical one, but that was grayed out.  FYI, I made sure it was Ext3 first, but no difference.

Am I doing something wrong, or is the Home partition supposed to be Primary?  When I tried to separate this into a Home partition, part of the data was copied to it from the original Primary.  Is that supposed to happen?  I had the feeling all the basic data should stay in the Boot partition.  Is that right?  Thanks for all the help and great posts.  This forum is a gold mine of information.

---

### Post by taurus on 2007-01-09
Are you trying to resize / while in Ubuntu?  You cannot resize the partition while it's in used so you need to use the LiveCD to do that.

---

### Post by jimalan on 2007-01-09
I used the LiveCD and followed the instructions to download GParted and work from there.  That's when I couldn't change the partition from Primary to Logical, so I quit and left it alone.

---

