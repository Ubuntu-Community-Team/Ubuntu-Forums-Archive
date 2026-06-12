---
title: "Upgraded from 14.04 to 16.04, broke everything (relocation error)"
date: 2016-08-18
forum: Installation &amp; Upgrades
---

### Post by beatme101 on 2016-08-18
the PC is able to boot and wine programs can be run, along with the terminal and a file manager, but that's about it. You'll have to forgive my method of screenshots because I can't get a view for you any other way:

[http://imgur.com/a/gXprX](http://imgur.com/a/gXprX)

As you can see I can't open text editors, web browsers, or anything else that might be useful in debugging this.

---

### Post by beatme101 on 2016-08-18
I have found the solution, for anyone else with this problem:

Run in a terminal:
 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1

This enables the next step:
Open the ubuntu software center, it will ask to do a repair, let it. It will take a while, and when it is done everything should run properly. You may want to restart so that service we ran in a  terminal earlier will run in the background properly.

---

