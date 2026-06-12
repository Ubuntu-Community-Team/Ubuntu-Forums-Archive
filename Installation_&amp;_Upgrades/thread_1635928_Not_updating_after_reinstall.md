---
title: "Not updating after reinstall"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by Coach_Mark on 2010-12-02
i just did a reinstall of 9.10 and am having a few problems.

1.  hardware drivers for the wireless modem are updated, but not functioning.  the driver screen says it's activated, though.

2.  when i do to install java (following the instructions at [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)), i get the following error:  "mv:  cannot stat"<file info and move to directory>"

what happened?  and how do i fix it?

---

### Post by sikander3786 on 2010-12-02
Please post the output of this command from Applications > Accessories > Terminal.

```
sudo apt-get update
```

**[COLOR="Red"]Edit:[/COLOR]** I just had a look on the page you linked in your above post. Why don't you just install java from repositories i.e, System > Administration > Software Sources?

You need to activate the Multiverse Repos and then search Software Center for that or run this command.

```
sudo apt-get install sun-java6-jre
```

---

### Post by Coach_Mark on 2010-12-02
i think i have java installed now.  but, that still doesn't explain why the wireless modem driver not recognize anything?  new problem, too.  no matter what website i go to, i get a prompt for missing plugins.  always the same three plugins.  but, i have installed them.  why is the installation not recognized?

---

### Post by sikander3786 on 2010-12-02
Which plugins does it say missing?

Type this in your browser address bar and see what is installed and what not...

```
about:plugins
```

Not sure about wireless modem though. Better to start a new thread in Networking & Wireless sub-forum.

---

### Post by Coach_Mark on 2010-12-02
screen shot attached...


i have installed the plugins at least twice, but i still get that window at many websites.  as you can see from the software driver window, it says the driver is installed and functioning., but the connections icon at the top lists no wireless connections and doesn't allow me to engage any.

and i'll start a thread in the wireless forum.  thanks for that idea.

---

### Post by sikander3786 on 2010-12-02
Try Flash-aid.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Coach_Mark on 2010-12-02
i think that fixed.  first thing it said was it was changing the installation to a 32-bit version.  not sure how that happened.  had 32-bit CD...downloaded the 32-bit Java...<sigh>...ah well...

THANKS!

(i think i got the wireless thing figured out too)

---

### Post by wilee-nilee on 2010-12-02
You might also consider that the end of life of support is about May 2011 with this distro.

---

### Post by Coach_Mark on 2010-12-03
yeah.  but it was on hand...and i needed to re-install for various reasons.  i'll be moving on up soon.  :)

---

