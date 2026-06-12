---
title: "&quot;apache 2 configuration is broken&quot;"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by edhawk2 on 2009-12-04
I've been tryiing to set up Medibunutu on a Dell Latitude laptop (P-3)  

I run the script "sudo apt-get install w32codecs" in the terminal window.  It returns the following:
"Your apache2 configuration is broken, so we're not restarting it for you"

How to fix apache2??

I've just renistalled 8.01 Ibex and online video is not working properly.  
I thought Medibuntu would help but it doesn't want to cooperate.

---

### Post by phillw on 2009-12-04
Hi,

How did you install Apache2 ?

And, how many alterations (like mod-security, new sites etc) have you made to it ?

Phill.

---

### Post by edhawk2 on 2009-12-04
I'm not a programmer.  I assume apache2 came off the CD when I installed Ibex.  After the installation there numerous upgrades from the web through Firefox.  Also, I installed SM Player through Synaptic and I installed "Java Runtime" from the "Add/Remove" under Applications.  

I got the complaint about Apache2 when loading the Medibuntu stuff.

---

### Post by phillw on 2009-12-04
> **edhawk2 said:**
> I'm not a programmer.  I assume apache2 came off the CD when I installed Ibex.  After the installation there numerous upgrades from the web through Firefox.  Also, I installed SM Player through Synaptic and I installed "Java Runtime" from the "Add/Remove" under Applications.  

I got the complaint about Apache2 when loading the Medibuntu stuff.

If you're not hosting web-pages, you can just remove Apache2 from Synaptics Package manager. If the system then complains that apache2 isn't there - You'll have to ask someone else. I'm not familiar with any players or browsers requiring apache2.
System --> Administration --> Synaptic Package Manager  -- type in apache2, then mark it for complete removal, then click on apply.

Regards,

Phill.

---

