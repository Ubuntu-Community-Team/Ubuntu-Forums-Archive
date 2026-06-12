---
title: "Easy Firewall config in Karmic +1"
date: 2009-07-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by superfoor on 2009-07-06
I'm not a fan of configuring a firewall on almost any Linux distro. However the new system-config-firewall front-end in fedora 11 makes it just too easy. I would love to see this little app default in karmic or karmic +1.
Let me know what you think.

Foor

---

### Post by ibutho on 2009-07-06
> **superfoor said:**
> I'm not a fan of configuring a firewall on almost any Linux distro. However the new system-config-firewall front-end in fedora 11 makes it just too easy. I would love to see this little app default in karmic or karmic +1.
Let me know what you think.

Foor

I also like the system-config tools in Fedora. Out of curiosity whats wrong with ufw and gufw?

---

### Post by caryb on 2009-07-06
Back in the breezy days I proposed a suggestion that we have a variant of Ubuntu called fwubuntu & have a Ubuntu server type of Ipcop Smoothwall distro. I would love to have something like this available. I believe there would be a market for this.


Cary

---

### Post by pferraro on 2009-07-06
Have you tried installing the gufw package?  It's the gtk frontend to ufw, which is already installed by default.

---

### Post by tjeremiah on 2009-07-06
theres a firewall for/in ubuntu ? lol I never knew.

---

### Post by wayne_cat on 2009-07-06
> **tjeremiah said:**
> theres a firewall for/in ubuntu ? lol I never knew.

*wayn_cat slaps tjeremiah with an iptables manual*  :biggrin:

---

### Post by tjeremiah on 2009-07-06
> **wayne_cat said:**
> *wayn_cat slaps tjeremiah with an iptables manual*  :biggrin:

I always hear how ubuntu is safe and blah blah. Didnt bother to really look into a firewall.

---

### Post by jpeddicord on 2009-07-07
> **pferraro said:**
> Have you tried installing the gufw package?  It's the gtk frontend to ufw, which is already installed by default.

I tried that a few months ago, and it seemed to take ages to update even a single allow/deny rule. I personally don't think we need a GUI for a firewall (honestly, what is easier than `sudo ufw allow 80`) but if there would be one, gufw would seem to be a logical choice as long as it was not so sluggish.

---

### Post by tjeremiah on 2009-07-07
dont mean to sound like a newb, but since I never knew, where can I get a firewall for ubuntu? If theres already one, where is it located?

---

### Post by wayne_cat on 2009-07-07
> **tjeremiah said:**
> dont mean to sound like a newb, but since I never knew, where can I get a firewall for ubuntu? If theres already one, where is it located?

the "firewall" is a (default) function of the linux kernel. you can use the command line (/sbin/iptables) or a GUI to configure it.

[https://help.ubuntu.com/9.04/serverguide/C/firewall.html](https://help.ubuntu.com/9.04/serverguide/C/firewall.html)

---

### Post by jpeddicord on 2009-07-07
> **wayne_cat said:**
> the "firewall" is a (default) function of the linux kernel. you can use the command line (/sbin/iptables) or a GUI to configure it.

[https://help.ubuntu.com/9.04/serverguide/C/firewall.html](https://help.ubuntu.com/9.04/serverguide/C/firewall.html)

Even better, Ubuntu comes with ufw installed by default.

See [https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall) for information on configuring that.

---

### Post by tjeremiah on 2009-07-07
> **jacobmp92 said:**
> Even better, Ubuntu comes with ufw installed by default.

See [https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall) for information on configuring that.

thanks, I enabled it.

---

### Post by superfoor on 2009-07-07
> **tjeremiah said:**
> dont mean to sound like a newb, but since I never knew, where can I get a firewall for ubuntu? If theres already one, where is it located?
that isn't at all a "newb" thing to ask. I think that the lack of a good default firewall front end leaves a lot of people asking the same question. Thats one of the reasons I'm pushing this.

---

### Post by tjeremiah on 2009-07-07
> **superfoor said:**
> that isn't at all a "newb" thing to ask. I think that the lack of a good default firewall front end leaves a lot of people asking the same question. Thats one of the reasons I'm pushing this.

Im all for it! Bump!

---

