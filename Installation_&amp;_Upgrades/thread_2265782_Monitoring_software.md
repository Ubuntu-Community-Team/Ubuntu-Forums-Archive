---
title: "Monitoring software"
date: 2015-02-17
forum: Installation &amp; Upgrades
---

### Post by TitoHL on 2015-02-17
Hi guys:
I am self taught in Linux and I would be very useful program that can monitor any changes that occur during a setup or installation. Something similar to the history of Synaptic, but operate independently from Synaptic.
For example, if I change the wallpaper using a GUI application, then monitoring software throws a report as: "/etc/lightdm/lightdm-gtk-greeter.conf file has changed."
Is there something like that?
Thank you very much.

---

### Post by MAFoElffen on 2015-02-18
Lynis-- It's a Linux Auditing Tool. Capable of that, but you would have a configuration challenge ahead of you to get it to do the fine tooth kind of audit management you want in your description.

---

### Post by tgalati4 on 2015-02-18
Why do you want to monitor such details?  Perhaps there is a better way to manage these computers with a "factory reset" setting if things get messed up in a classroom environment.

What is the Use Case?

---

### Post by TitoHL on 2015-02-18
Thank you very much MAFoElffen, the Linux Auditing Tools seems to be the answer to my concerns.

Tgalati4, my goal is to "learn by doing" the relationship between configuration changes and the changes that occur in the system files. By this I do not want to fix computer problems.

---

