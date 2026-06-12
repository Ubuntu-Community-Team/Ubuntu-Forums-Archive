---
title: "something broken that prevents update manager to install"
date: 2013-09-06
forum: Installation &amp; Upgrades
---

### Post by jpazcavazos on 2013-09-06
I'm using ubuntu 12.04 and was working fine but a month or two ago the update manager failed to install the recommended updates. Since then there's a red dot with a white dash in the middle symbol on the top right side of the desktop. When I click on it it tells me something is broken and it can't install anything with the update manager nor from the ubuntu software center. When I click on the details it tells me to get rid of third party repositories which are a common cause of trouble and to give the terminal the command: apt-get install-f. When I give this command the terminal answers "invalid command". In the update manager's settings I took off the checks on third party repositories. When I click for details in the window that tells me that something is broken it tells me that linux-headers-3.2.0-Sgeneric-pae is not installed. But I don't know how to install it. Please help!!!!!!!!!!!!!

---

### Post by Bashing-om on 2013-09-06
jpazcavazos; Hi ! help is on the way.

We need to know the exact error(s) .. from terminal post the complete outputs of terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]what is, is
[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2013-09-07
>  the command: apt-get install-f. When I give this command the terminal answers "invalid command".

That would be:

sudo apt-get install -f

---

