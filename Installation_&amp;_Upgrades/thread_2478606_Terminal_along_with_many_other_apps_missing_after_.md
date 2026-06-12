---
title: "Terminal along with many other apps missing after 20.04.1 Upgrade"
date: 2022-08-30
forum: Installation &amp; Upgrades
---

### Post by daithi_dearg on 2022-08-30
Unfortunately I rushed into this upgrade and am missing Terminal along with many other application.

When I launch I get spinning icon but nothing else.

To make matters worse the File Explorer does similar which makes it very difficult.

Can go into recovery mode but have no network connection.

Happy to revert back if that is an option but difficult with missing terminal

---

### Post by tea for one on 2022-08-31
Do you have a data backup?
Ubuntu flavour?
Alternative terminal via [COLOR="#0000FF"]Alt + F2[/COLOR] and enter [COLOR="#0000FF"]xterm[/COLOR].

From your short description, my instinct tells me backup and clean install?

---

### Post by ajgreeny on 2022-08-31
A 20.04.1 upgrade to, or from, what? Or was this simply using sudo at update/upgrade?

We need to know a lot more before we can help you properly.

---

### Post by yancek on 2022-08-31
Did you do it with the GUI Software Updater or in a terminal?  Did you see any errors reported during the upgrade?  Did the upgrade seem to complete successfully?  Were you having any problems with Ubuntu prior to the upgrade?  Could you post some info on your hardware?

---

### Post by daithi_dearg on 2022-09-02
Sorry i misstated the version in the original post. It was 22.04.1 and I got a popup which I think came via software updater.

Magically the icons have now returned and I can now open terminal again. Weird.

Looking at "lsb_release -a" it appears I'm still at 20.04.5. People seem to be having a few issues so I think I'll stay on this release for the time being.

To apply updates I have always preferred to apply them via the terminal as I thought snapd gives less control and had considered it bloaty. Apply updates with this syntax:
sudo apt-get update && sudo apt-get dist-upgrade

Do you think I'm ok doing it this way or should I be doing this with software updater?

---

### Post by ActionParsnip on 2022-09-02
Can you launch xterm OK. If you press CTRL + ALT + T does the terminal load OK?

---

### Post by daithi_dearg on 2022-09-02
That loads fine with ctrl-alt-t

---

### Post by ActionParsnip on 2022-09-02
Cool. It's a fab way to get a terminal &#128526;

---

