---
title: "Emergency: Please, Help me. I think I ruined my computer."
date: 2005-03-23
forum: Installation &amp; Upgrades
---

### Post by Thief- on 2005-03-23
I was trying to be able to compile files from source, when I accidently uninstalled cpp, and the rest of my OS along with it. I tried to reinstall the OS, but it would not boot from the CD, it just went straight into GRUB. So, I went into windows, and deleted the partitions, and made new ones> Rebooted, and everything was going fine, and the partitions were made. Then, when it rebooted again, GRUB tried to load, but I got and error. It was error 17. Please, someone, help me. i need help desperately.

---

### Post by Thief- on 2005-03-23
Please, this is very, very bad. 

I cannot boot from a cd at all. I tried a live CD, and it wont work either.

---

### Post by Thief- on 2005-03-23
Someone, please, reply.

---

### Post by StacyWebb on 2005-03-23
your going to have to remove the GRUB.lst file (located on the MBR) or make a windows boot disk (floppy) and then format MBR (master boot record) doing it this way you will lose the ability to start windows but when you reinstall Ubuntu it should find then windows partition and remake a connnection to it. Hope this helps.

Also make sure your bios is set to boot from cd

---

### Post by Buffalo Soldier on 2005-03-23
Duration between your first post and your yelling is 16 minutes? Come on :)

Have you actually checked what error 17 actually is? [http://www.google.com/search?hl=en&lr=&q=grub+manual+error+17&btnG=Search](http://www.google.com/search?hl=en&lr=&q=grub+manual+error+17&btnG=Search)

Anyway, what StacyWebb told you is what I would have done.

---

### Post by Thief- on 2005-03-23
[QUOTE=Buffalo Soldier]Duration between your first post and your yelling is 16 minutes? Come on :)

[/QUOTE]

The in between time was panicking. And, that worked. You guys rule hard.

---

### Post by Buffalo Soldier on 2005-03-23
Proven physic law. Time runs slower when in panic :) we've all been thru it.. I've had my fair share of idiotic mistakes too :p

---

