---
title: "how can you properly install ubuntu with windows 7 in a dual boot system?"
date: 2015-12-27
forum: Installation &amp; Upgrades
---

### Post by cyryder7 on 2015-12-27
how can you properly install ubuntu with windows 7 in a dual boot system? I'm having some issues [http://paste.ubuntu.com/14226454/](http://paste.ubuntu.com/14226454/)

i installed windows 7 and reallocated space for ubuntu while installing windows 7. then I installed ubuntu alongside windows 7 but now I cannot get windows 7 to boot

> **sudodus said:**
> I'm glad it works for you with wubi and 12.04.5 LTS, but next time, when you want to upgrade to a new version of Ubuntu I suggest that you consider another method to install Ubuntu.

Wubi does not work with the new versions of Windows in UEFI mode. It is no longer developed which means that there is really no support for it. See this link

[Forums Staff recommendations on WUBI]("http://ubuntuforums.org/showthread.php?t=2229766")

Instead you should either make

1. a dual boot system or

2. run Windows as a guest operating system in a virtual machine (for example VirtualBox) in an Ubuntu host operating system, or the opposite, run Ubuntu as a guest operating system in a virtual machine (for example VirtualBox) in a Windows host operating system.

3. or run two separate machines as suggested by Skaperen.

Each of these options are used by many people.

---

### Post by sudodus on 2015-12-27
Moved to an own thread.

Please do not hi-jack another persons thread! It is better for both of you to have your own threads, because your problems and possible solutions are almost always different, and it makes it confusing to help and to receive help in the same thread.

---

### Post by sudodus on 2015-12-27
I have looked at the boot-info summary at pastebin. I can see that Boot Repair has done it's job and seems successful. I cannot see what is wrong, but I use Windows seldom nowadays, and don't know all the details. ***Let us hope someone else with more experience of reading the boot-info summary and of booting Windows will read this thread and suggest what you should do.*** :-)

Until then, please describe with as much details as possible, the different steps of your installation. It will make it easier for us to help you.

- When was the last time Windows worked? How did it work before you started to install Ubuntu?
- What can you see and hear, when you try to boot Windows now?
- Is there a backup of your Windows system?
- Are your personal data (documents, pictures, ...) backed up?
- Have you got Windows recovery disks or Windows installation disks?

- Is Ubuntu booting and working well? If not, please describe what is happening.

---

### Post by yancek on 2015-12-27
You have two entries for windows 7 in the boot menu.  Describe what happens when you select each from the menu.

---

### Post by cyryder7 on 2015-12-27
- When was the last time Windows worked? How did it work before you started to install Ubuntu? **Windows 7 worked fine before I installed Ubuntu**
- What can you see and hear, when you try to boot Windows now? **I see a purple screen and I hear the windows bootup sound**
- Is there a backup of your Windows system? **no**
- Are your personal data (documents, pictures, ...) backed up? **yes**
- Have you got Windows recovery disks or Windows installation disks? **yes, Windows 7 professional**

- Is Ubuntu booting and working well? If not, please describe what is happening. [B]ubuntu boots normally and works fine


Windows has two options sda1 and sda2. Both give purple screens[/B]

---

### Post by oldfred on 2015-12-27
@cyryder7 forum rules are only one thread per topic. And you have two on same install/boot issue. I can either merge or will close one of these threads, your choice. But will not keep two threads going.

User already has his own thread. And has done several total reinstalls.
Not quite sure why Windows does not boot from grub as installs do look normal.

[http://ubuntuforums.org/showthread.php?t=2306634](http://ubuntuforums.org/showthread.php?t=2306634)

---

### Post by cyryder7 on 2015-12-27
yes, please close this thread.

---

