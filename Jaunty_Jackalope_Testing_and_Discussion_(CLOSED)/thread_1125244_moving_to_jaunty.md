---
title: "moving to jaunty"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Eniac on 2009-04-14
ok, i was reading this thread
[http://ubuntuforums.org/showthread.php?t=1123373](http://ubuntuforums.org/showthread.php?t=1123373)

thinking i was now converted enough to ubuntu to know what the hell i was doing

but reading it, i realize i dont know a darn thing about partioning in ubuntu and how to control so i quickly hop back into the absolute beginner circle for instructions...with shame :(

ive been happily running 8.10 with pride, enough to never go back to windows.

but apparently 9.04 introduces a lot of fun stuff that requires some fancypants works when converting from 8.10

so my question is this:

should i just wait for the release, backup all my personal files and do a fresh install from 9.04 ?

is there a way i can not lose my programs and configuration? because i can backup my home folder pretty easily but im not so sure for the rest.

---

### Post by binbash on 2009-04-14
No, update will work fine.If you want to convert your filesystem to ext4 you can do that easily without losing data.

---

### Post by Jakey_TheSnake on 2009-04-14
Run: "update-manager -d" from a terminal to upgrade to jaunty :)

---

### Post by BDNiner on 2009-04-14
> **binbash said:**
> No, update will work fine.If you want to convert your filesystem to ext4 you can do that easily without losing data.

I would create a backup of your information first. changing a file system is not a simple task no matter how simple the instructions make it out to be. There is a very big chance that data can be corrupted. So make a backup of your home directory first. Any other programs can easily be reinstalled.

---

### Post by LowSky on 2009-04-14
you dont need to reformat or create new partitions for 9.04, i do suggest you do back up important files. but upgrading wil be very easy from 8.10

---

