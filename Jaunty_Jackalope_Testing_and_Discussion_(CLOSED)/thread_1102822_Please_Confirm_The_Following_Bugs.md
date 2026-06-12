---
title: "Please Confirm The Following Bugs"
date: 2009-03-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-03-22
Since its a no-no to confirm your own bugs, can someone please confirm the following bugs:

(this means moving the bug status to confirmed not saying its confirmed in a bug comment)

Iced Tea java plugin does not work - [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/344705](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/344705)

New Wave theme doesnt include the FireFox user chrome css to fix the pull down menus - [https://bugs.launchpad.net/anton/+bug/344692](https://bugs.launchpad.net/anton/+bug/344692)

New Wave theme doesnt correctly handle open office pull down menus - [https://bugs.launchpad.net/ubuntu/+source/gnome-themes-ubuntu/+bug/312745](https://bugs.launchpad.net/ubuntu/+source/gnome-themes-ubuntu/+bug/312745)

Thanks

---

### Post by olskar on 2009-03-22
I have confirmed the firefoxmenubug. The css file is included but it is not used. I don't know how to solve this. If you install the css file into the mozillafolder it will always be used and that is not wanted. However it has to be in that folder to give you correct menus when using newwave?

---

### Post by Nullack on 2009-03-22
Thanks :) I think the right solution is for the FF mod to be made into an installable FF theme that depends on selectng new wave, and then when a user uses another theme its removed from FF.

---

### Post by Kow on 2009-03-22
I believe I can confirm that the icedtea plugin isn't working. I have sun java (version 6) installed now and it works fine. Perhaps icedtea just needs a rebuild?

---

