---
title: "synaptics doesn't show everything."
date: 2005-06-03
forum: Installation &amp; Upgrades
---

### Post by chen_tso on 2005-06-03
hi, i just installed ubuntu using the pressed cd's i received (thanks). but i don't see all available packages as i have seen before with the version of ubuntu i downloaded. what should i do?

---

### Post by mingus on 2005-06-03
check this . . .

[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)

---

### Post by Xerampelinae on 2005-06-03
Most likely the contents of the file /etc/apt/sources.list are different between the two machines.  This file lists repositories that the machine uses to install software.  You could make sure the contents of this file is the same on both machines in order to have the same software available.

Also, ubuntuguide.org has some information on setting up some extra repositories.  There's also backports.ubuntuforums.org that includes useful extra software.

---

### Post by chen_tso on 2005-06-04
[QUOTE=Xerampelinae]Most likely the contents of the file /etc/apt/sources.list are different between the two machines.  This file lists repositories that the machine uses to install software.  You could make sure the contents of this file is the same on both machines in order to have the same software available.

Also, ubuntuguide.org has some information on setting up some extra repositories.  There's also backports.ubuntuforums.org that includes useful extra software.[/QUOTE]
 thanks, i see the universe repositories now. i think the reason is because when i installed Ubuntu, internet connection wasn't set up.

---

