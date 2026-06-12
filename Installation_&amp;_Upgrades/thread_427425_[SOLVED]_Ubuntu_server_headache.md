---
title: "[SOLVED] Ubuntu server headache"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by upthelum on 2007-04-29
Can anyone help me with a problem with xubuntu server version 6.6. I am trying to install it on VMWare which is fine but just at the last part of installation i get this message: 

"Security updates on security.ubuntu.com couldn't be accessed so those options will not be made available at this time. Investigate this later. Commented out entries for security.ubuntu.com have been added to the etc/apt/sources.list file"
 
Any help would be appreciated.

---

### Post by bulldog on 2007-04-29
Well it seems it can't reach the security.ubuntu.com for some reason.
Just install and when done take a look at the /etc/apt/sources.list to see what's wrong with the entry.

---

### Post by upthelum on 2007-04-29
I'm not sure exactly what i'm supposed to be looking for. Sources.list is mostly commented out, when i run "apt-get update i get "Type 'Uncomment is not known on line 19 in sources.list.

---

### Post by bulldog on 2007-04-29
You shouldn't type uncomment.
You just put a # in front of the line you don't won't to be used by ubuntu.

---

### Post by upthelum on 2007-04-29
Ok i wasn't typing it i was getting a message telling me it. Thanks anyway man for your help i got it, the sources.list file was totally wrong, once i uncommented the correct lines it went fine.

Many thanks again...

---

