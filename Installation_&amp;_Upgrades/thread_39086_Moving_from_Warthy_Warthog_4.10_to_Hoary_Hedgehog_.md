---
title: "Moving from Warthy Warthog 4.10 to Hoary Hedgehog 5.04"
date: 2005-06-03
forum: Installation &amp; Upgrades
---

### Post by makimonaco1 on 2005-06-03
What do I have to do to upgrade my Warthy Warthog 4.10 system to Hoary Hedgehog 5.04? What are the benefits/dangers of doing so?

---

### Post by christooss on 2005-06-03
[QUOTE=makimonaco1]What do I have to do to upgrade my Warthy Warthog 4.10 system to Hoary Hedgehog 5.04? What are the benefits/dangers of doing so?[/QUOTE]
There are new programs including update manager and many others.

Just open terminal
[B]
*sudo gedit /etc/apt/sources.list*[/B]
Copy/paste repositories from

ubuntuguide.org

Then in terminal

***sudo apt-get dist-upgrade***

---

### Post by wulf on 2005-06-03
Dangers? It's worth doing a backup of your data (in case something goes disastrously wrong) and  also any config files you've changed (probably in /etc) or other scripts you've altered. I've done three Warty -> Hoary upgrades with only minor hiccups (like the customised version of the pop3browser script I was using... fortunately I had a copy in my home directory as the one in /usr/bin got overwritten!).

Should be pretty smooth though!

Wulf

---

### Post by makimonaco1 on 2005-06-03
I pasted the repositories list for 5.04 from the site you indicated, did the 

apt-get dist-upgrade

 and I keep on getting error messages for every line saying:

W: Can not read the package list source http........ 

and then, at the end, end saying 

W: Maybe you want to do an 'apt-get update' to correct this problem.

What shall I do?

---

### Post by bored2k on 2005-06-03
[http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)

---

### Post by christooss on 2005-06-03
[QUOTE=makimonaco1]I pasted the repositories list for 5.04 from the site you indicated, did the 

apt-get dist-upgrade

 and I keep on getting error messages for every line saying:

W: Can not read the package list source http........ 

and then, at the end, end saying 

W: Maybe you want to do an 'apt-get update' to correct this problem.

What shall I do?[/QUOTE]

Sorry I forgoten

you have to sudo apt-get update first

I am so sorry

---

### Post by bored2k on 2005-06-03
[QUOTE=makimonaco1]W: Maybe you want to do an 'apt-get update' to correct this problem.

What shall I do?[/QUOTE]

Tip >> Unlike other systems, Linux tends to be very friendly and verbose. Get used to reading the last lines displayed as they tend to give the user very useful information, like that one you skipped ;).

---

