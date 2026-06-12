---
title: "[SOLVED] How do i inatall Flash"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by on4now4 on 2008-08-22
I used Ubuntu a while ago and than stopped but now im trying it again and i just cant remember how to install the flash player i know it is a complete noob player but what do i do i go to the site [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) but which one do i dl and how do i install it i completely forgot. i think it is because i just completely forgot how to use terminal.

---

### Post by jakupl on 2008-08-22
firefox should tell you what to do automatically.
Does this not happen?

otherwise, ubuntu-restricted-extras should do the trick.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by on4now4 on 2008-08-22
no that does not happen and this is what happens when i enter that code

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by jakupl on 2008-08-22
Yes. you need to exit synaptic package manager and Add/Remove.

you can only use one installation-method or program at a time.

---

### Post by on4now4 on 2008-08-22
thanks that worked i forgot that i had the other installer open now i just need to get my audio to work if u have any ideas how to do that i have a ht omega claro sound card

---

### Post by jakupl on 2008-08-22
I would make a new thread about that if I were you.
It makes it easier for everyone.

---

