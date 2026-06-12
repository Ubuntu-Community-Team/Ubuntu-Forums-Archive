---
title: "Prompting to install new release after a successful upgrade"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by zutme on 2013-04-25
I just updated to Ubuntu 13.04 on a server install by using do-release-upgrade. It seemed to go fine, but when I log in it still prompts me:
Welcome to Ubuntu 13.04 (GNU/Linux 3.8.0-19-generic x86_64)
...
New release '13.04' available.
Run 'do-release-upgrade' to upgrade to it.

When I do a lsbrelease -r it returns:
Release:        13.04

Does anyone know why it is still prompting me?

Thanks in advance for any help.

---

### Post by segede on 2013-04-26
Same problem here. 
Can't figure out how to get rid of it.

---

### Post by fragtion on 2013-04-26
Same problem here...
For now I've just removed /var/lib/ubuntu-release-upgrader/release-upgrade-available and the message goes away

---

### Post by Witiko on 2013-04-26
Same here.

---

### Post by zutme on 2013-04-26
bump

---

### Post by Witiko on 2013-04-27
So, I dived a bit into the ubuntu ssh motd code and came up with the following solution:
> sudo rm /var/lib/ubuntu-release-upgrader/release-upgrade-available
sudo /usr/lib/ubuntu-release-upgrader/release-upgrade-motd

The question why this happens stands, though. The problem didn't occur on my notebook upon update, which makes the entire affair all the more baffling.

---

### Post by Zta on 2013-04-27
Same problem here. Not a very satisfactory workaround, but it's better than that annoying message after upgrade.  

Thanks for the tip =)

---

### Post by badbod on 2013-05-10
not sure why either but deleting the contents of  /var/lib/ubuntu-release-upgrader/release-upgrade-available did the trick for me.

---

