---
title: "Problems updating Ubuntu 18.04"
date: 2020-06-03
forum: Installation &amp; Upgrades
---

### Post by giuliano1 on 2020-06-03
Running a partial update I ran into a problem with GRUB boot loader, it looks like I should install GRUB on all the disks, I have only one disk because I am using a dual boot with Windows 7, this is the message that I get from the system: [https://i.stack.imgur.com/b30Yp.png](https://i.stack.imgur.com/b30Yp.png)

How can I fix this?

---

### Post by DuckHook on 2020-06-03
Please don't post large graphics to the forums. This is very problematic for helpers with low speeds, who are on limited data plans, or are viewing from smartphones or small screens.

If you must post resource-intensive images, please post them as attachments using the paperclip icon in the *Adv Reply* toolbar.

Also refrain from using non-standard fonts and styles for the same reasons.

---

### Post by yancek on 2020-06-03
The image you posted indicates that Grub was previously installed to another disk or that the UUID ha changed for some reason.   If you have only one hard drive, you should be able to simply install Grub.  If you have windows 7, is it the default Legacy install?  If so, just install Grub to the MBR of the drive which should be sda.  I'm not sure why the UUID would change with a simple update?

---

### Post by giuliano1 on 2020-06-03
Sorry I did not know about the large image!

---

### Post by giuliano1 on 2020-06-03
[ATTACH=CONFIG]286088[/ATTACH]

I would certainly reinstall it but I got to this second screen and when I select either options on the next screen I will get the message that I have selected not to install GRUB....sorry for my ignorance but is there a way inside the terminal to select both options at the same time? Thank you

---

### Post by CelticWarrior on 2020-06-03
Should install to sda only, not in a partition.

Use SPACE to select then TAB to highlight OK and finally ENTER to commit.

---

### Post by giuliano1 on 2020-06-03
It worked, thank you!

---

