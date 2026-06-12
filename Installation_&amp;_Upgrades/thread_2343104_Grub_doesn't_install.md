---
title: "Grub doesn't install"
date: 2016-11-13
forum: Installation &amp; Upgrades
---

### Post by luizmedeiros87 on 2016-11-13
Hello everyone,

I'm trying to install Lubuntu on my GF's notebook because it's fairly old and the hardware can't handle "heavy" stuff.

Anyways, the problem is everytime i install the OS everything goes fine, but at the end of the installation it keep showing an error message that states that the Grub couldn't be installed and i need to hard reset the notebook (because it will be stuck at this error).

Anybody knows what i can do to solve this?

PS: I'm new to the Linux community, so i don't know much.

---

### Post by Bucky Ball on 2016-11-13
*Thread moved to **Installation and Upgrades***.

More specific support here. 

Welcome. Are you dual-booting with Windows? If so, which number? Which release of Lubuntu? The exact error you are getting at the end of the install would be helpful. Any other details you can think of, post them. ;)

---

### Post by luizmedeiros87 on 2016-11-13
> **Bucky Ball said:**
> *Thread moved to **Installation and Upgrades***.

More specific support here. 

Welcome. Are you dual-booting with Windows? If so, which number? Which release of Lubuntu? The exact error you are getting at the end of the install would be helpful. Any other details you can think of, post them. ;)

Thanks for moving the thread to the correct section.

No dual booting, i'm trying to wipe the HD and do a clean install. It's the latest Lubuntu version (16.10). And the error says something about it could not install the Grub on /target/ something like that. The installation goes just fine, but just at the closure it shows this message and ask to select another local to install the Grub, but doesn't matter if i try to change the location it'll be stuck at this error window. I'll try to take a picture if possible and post it here.

---

### Post by Bucky Ball on 2016-11-13
Well, you need to install grub to sda, not sda1 or sda2 or anything with a number. They are partitions. sda is the drive. If you can not install to sda, then that's a problem. 

If you're posting pictures, please attach them by clicking 'Adv Reply' or 'Go Advanced' when posting and attach the pic with the paperclip icon in the taskbar there. Thanks. ;)

To wipe the drive first, go to 'Try Ubuntu', launch Gparted, right click and unmount each partition then right click and delete. Once all partitions are deleted, Device> Create partition table. Back to the desktop and click the 'Install Lubuntu' icon and see what happens.

---

### Post by luizmedeiros87 on 2016-11-13
It installed just fine right now... WTH?!

Thanks for the help anyways. But everything is working right now.

---

### Post by Bucky Ball on 2016-11-13
Great news. ;)

Please mark the thread as SOLVED from 'Thread Tools' at the top right of the page or see the last link in my signature at the bottom of this post.

Enjoy and don't hesitate to post a new thread with any other questions/issues you have.

---

