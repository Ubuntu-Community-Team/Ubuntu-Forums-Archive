---
title: "GRUB/Windows BOOTLOADER"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by danielcg25 on 2010-10-17
Hello, this is my first post, so here I go:
I have a fresh install of Windows XP and Ubuntu 10.10. I have a ubuntu ONLY for when I need to fix Windows. I do not want to use GRUB or whatever, I just want the Windows bootloader to load and ask me if I want to boot Ubuntu, or XP. How do I do this? currently GRUB thingy loads, and I can load Windows, Ubuntu, or several other choices related to Ubuntu. I want the Windows BootLoader to askme if I want Ubuntu or XP and if i say Ubuntu, then show the GRUB thing.
I had this before I formatted my HDD, and installed Windows, and Ubuntu


PS: I am new to Ubuntu, and Linux in general, so please explain all terms.

---

### Post by dino99 on 2010-10-17
why do you want complicated things ? You says: "i just want ubuntu to fix xp when it need" LOL
I know how to do: remove it and you'll never fix it again, no need.

Install wine (winehq) on your ubuntu to use your exe apps, that it.

---

### Post by soldier1st on 2010-10-17
dino99: i know what you mean but he wants the windows bootloader not Grub9I like Grub too). to the op: download this utility EasyBCD at [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) and it will do what you want.

---

### Post by danielcg25 on 2010-10-17
But, if I only had Ubuntu, what if something goes wrong with Ubuntu? I would still have both OS's because I like to explore system files, and tend to muck things up LOL

---

### Post by JackNocturne on 2010-10-17
IF your concern is of the shared computer usability just use GRUB hidden-time out set to 2 seconds or something else and set **default boot** to Windoze:-k,, that way when other users boot the computer they will just see it loading to windows.

Hidden timeout can be exited with "Esc" character.

---

### Post by danielcg25 on 2010-10-17
> **JackNocturne said:**
> IF your concern is of the shared computer usability just use GRUB hidden-time out set to 2 seconds or something else and set **default boot** to Windoze:-k,, that way when other users boot the computer they will just see it loading to windows.

Hidden timeout can be exited with "Esc" character.
That is one issue, but the main issue is the Windows BootLoader looks better in my opinion, I would just like to use the Windows bootloader,(for Ubuntu and windows) and bypass the whole grub thing.
If thats NOT possible, then I would like the Windows BootLoader to ask me if I want Windows, or Ubuntu, and if I chose Ubuntu, then load grub which will be set with a 0 second delay, so it boots right into Ubuntu.

---

