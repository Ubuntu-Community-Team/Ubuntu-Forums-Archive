---
title: "After Xubuntu 16.04 upgrade software-center will not install apps"
date: 2016-08-19
forum: Installation &amp; Upgrades
---

### Post by lou6 on 2016-08-19
Upgraded to 16.04 two weeks ago. Software-center has install buttons grayed out and gnome-software will not run at all. I've reinstalled both with Synaptic but no joy. According to some posts this has been fixed upstream for a while - any ideas about when this will filter down to us?

Tried running gnome-software in terminal. Nothing happens - no error message, no window opens - nothing. Installed version is gnome-software (3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1) 

Thanks for any help.

---

### Post by sudodus on 2016-08-20
If you have the same problem as described in this thread: [ubuntu software will not intall apps](https://ubuntuforums.org/showthread.php?t=2334433),

please visit the bug report and confirm the bug by marking that it 'affects you too': [ubuntu-software will not install or remove apps.](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1615223)

***Edit:*** While waiting for debugging, you can try to install and use synaptic

[sudo apt-get install synaptic](sudo apt-get install synaptic)

---

### Post by lou6 on 2016-08-20
I confirmed the bug as suggested. In the meantime I ran sudo apt-get remove --purge gnome-software followed by sudo apt-get autoremove then reinstalled gnome-software with no change in behavior.

I have synaptic installed and use it often.

---

### Post by lou6 on 2016-08-20
I just discovered that entering gksudo gnome-terminal in terminal will start the app normally. Is there something I can do to make gnome-software start without privileges?

---

### Post by sudodus on 2016-08-21
I think it needs elevated permissions, but you should be prompted for it via the menu system. I think you have identified the bug, and thanks for the new comment in the bug report describing your work-around :-)

---

