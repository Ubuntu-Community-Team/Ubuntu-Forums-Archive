---
title: "Changing boot order for Ubuntu and XP"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by heyman123 on 2007-12-20
Hello everyone, I'm new to the forum as well as being a total n00b at Ubuntu. Suppose the reason I'm here is because I've been wanting to learn Ubuntu for quite a while now. I finally took the initiative yesterday and installed a version of ubuntu (7.10 I believe it was). Everyone installed fine and dandy, as well as keeping my XP installation in tact. 

Now comes a common issue that I'm facing and hopefully some of you experts can help enlighten me with your knowledge. I want to keep XP as my default boot. I did a quick search and came upon this old topic --> [http://ubuntuforums.org/showthread.php?t=77024](http://ubuntuforums.org/showthread.php?t=77024), tried it and ran into an issue after changing the default to 5... and 6, saved the file, which prompted this message :mad:

"**Could not save the file /boot/grub/menu.lst.**
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."


I've used both "su" and "sudo".... keep in mind, I am a TOTAL NOOB... thanks for being patient with me and for all the help in advance!

---

### Post by logos34 on 2007-12-20
need to open it as root:

gksudo gedit /boot/grub/menu.lst

---

### Post by heyman123 on 2007-12-20
> **logos34 said:**
> need to open it as root:

gksudo gedit /boot/grub/menu.lst




That did the trick... Thanks alot!

---

