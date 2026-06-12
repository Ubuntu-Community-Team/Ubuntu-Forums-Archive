---
title: "install grub"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by arunkmohan18 on 2009-12-19
i want to know how to install grub manually when i type grub in terminal it shows grub currently not installed can i install grub throw live cd please tell me how to do this

---

### Post by darkod on 2009-12-19
Are you sure it's not installed? How are you booting ubuntu to get to terminal without grub?
In terminal execute:
sudo grub-install -v

That will show you the version of grub if it's installed.

Otherwise, instructions how to reinstall grub1 for 9.04 or before, and grub2 for 9.10 are here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by arunkmohan18 on 2009-12-19
the message grub is not installed shows first time that installed but when i reboot it shows
grub>
what i want to do now?

---

### Post by darkod on 2009-12-19
It seems you have selected grub not to be installed when installing ubuntu. It is automatically installed unless you select otherwise.
Did you install ubuntu 9.10 from its cd? Or another version of ubuntu?

---

### Post by arunkmohan18 on 2009-12-19
i installed ubuntu complete remix 9.10 end of installing it shows grub cannot install fatal error

---

### Post by dynamo2 on 2010-01-06
The solution to this problem has been posted on the official UCR web site [http://www.ubuntucomplete.co.uk/node/25](http://www.ubuntucomplete.co.uk/node/25)

---

### Post by dynamo2 on 2010-01-10
The latest UCR version has fixed the problem. Get it at [http://www.ubuntucomplete.co.uk](http://www.ubuntucomplete.co.uk)

---

