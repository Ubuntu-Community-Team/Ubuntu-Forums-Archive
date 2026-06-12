---
title: "Custom launchers (location) stop working after Hardy upgrade"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by oniichan on 2008-05-02
I use the custom application launcher to locations as toolbar shortcuts to various folders used alot at work. After the Hardy upgrade from Gutsy, launchers now give the following error: "Could not show <location>. The specified location is invalid." Newly created launchers produce the same result Could not find a bug directly applicable though there are threads reporting issues with custom launchers on Hardy. Any ideas?

---

### Post by Vermind on 2008-05-02
Hello,
how do You create the launchers? How about just opening nautilus, and dragging a folder to the panel?

---

### Post by oniichan on 2008-05-03
I had used the custom application launcher and picked Type = Location. After entering the location, the launcher would open the desired directory in nautilus. So now you have to specify the command and location in the launcher, i.e. 'nautilus --browser /home/user/perl/bak'. So I guess the launcher Type: Location no longer works as it did.

---

### Post by Vermind on 2008-05-03
Hello,
I just tried this. It works if You add the file:// in the beginning of the location.
for example file:///home/user

---

### Post by oniichan on 2008-05-03
thanks, vermind. of course. damn, i feel like an bloody idiot. thakns again. jim

---

