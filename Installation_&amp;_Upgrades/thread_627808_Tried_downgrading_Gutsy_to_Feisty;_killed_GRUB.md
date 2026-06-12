---
title: "Tried downgrading Gutsy to Feisty; killed GRUB"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by Bob Todd on 2007-11-30
I have a dual-boot machine with Ubuntu and XP, and use GRUB to choose an OS on boot. 

I tried to downgrade by using my live cd to to a clean reinstall of Feisty over Gutsy. Now my machine won't boot from hard disk; all I get is an error. I can still boot from CD or USB drive, thankfully. I can use the Feisty live cd to boot, and then choose 'boot from first hard disk', which shows me GRUB offering both Ubuntu and XP, and I can access either fine -- my machine just won't boot and show GRUB of its own accord. It's not practical to use the cd every time I boot, so I need to fix GRUB. I've no idea where to begin, though. Where should I be looking for errors?

I have the Ubuntu alternate installer, but I wouldn't know what to do with the 'rescue a broken hard disk' option.

---

### Post by Pumalite on 2007-11-30
What is the error message at boot?

---

### Post by Bob Todd on 2007-11-30
I can't recall the exact wording -- it's something along the lines of 'hard disk boot sector invalid'.

---

### Post by Pumalite on 2007-11-30
[http://ubuntuforums.org/showthread.php?t=532783](http://ubuntuforums.org/showthread.php?t=532783)

---

### Post by Bob Todd on 2007-11-30
Thanks; I'll give that a try.

---

### Post by Pumalite on 2007-11-30
Good luck!

---

### Post by vampire622003 on 2007-12-10
Load your xp cd and start recovery console, log into your windows installation and type fixmbr, that will restore your original bootloader for windows.

---

