---
title: "All repositories in synaptic remain unticked"
date: 2014-09-17
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2014-09-17
What could be the cause of all my repositories being unticked? I click on the repositiory and the tick shows and then disappears leaving the box blank.

I have just copied over the /etc/apt directory from a backup and still the repositories show as unticked. Could it be anything to do with a the gnome theme I am using?

Robin

---

### Post by Robbyx on 2014-09-17
I also note that the server always changes  to the main server and not a local one, and I can not tick any of the other software sources. The tick does not show at all.

---

### Post by ian-weisser on 2014-09-17
It could be permissions:

Are you using an account with sudo access?
Are you prompted for a password at the first change?

---

### Post by Robbyx on 2014-09-18
I have to give my password when I first go into synaptic. So whilst it may be permissions I do not know why and etc/apt is always root.

Robin

---

### Post by ian-weisser on 2014-09-18
> **Robbyx said:**
> I have to give my password when I first go into synaptic. So whilst it may be permissions I do not know why and etc/apt is always root.

Well, then it sure does not seem like permissions.

---

### Post by Robbyx on 2014-09-18
That is what I thought, but I am stuck with not being able to tick any of the options in Synaptic! For example on the Ubuntu Software tab I should be able to tick each source but I can not. Instead the tick appears and immediately disappears leaving none of the options ticked. Same for the all the other tabs.

Upon coming out of the Repositories setting tab it asks permission to upgrade the software. I clicked on the detail and loads are failing to be found.

---

### Post by Robbyx on 2014-09-18
I have found the apparent cause. It was the theme set up. I loaded the live cd and noted down the settings from Gnome tweak. I then went back to the installed version and changed them to the noted setup. This helped with removing another problem that was white print on a white background but I found it also sorted out the synaptic problem. It shouldn't but it did as I can now tick the boxes by clicking and the tick stays there. Thanks for trying to help.

---

