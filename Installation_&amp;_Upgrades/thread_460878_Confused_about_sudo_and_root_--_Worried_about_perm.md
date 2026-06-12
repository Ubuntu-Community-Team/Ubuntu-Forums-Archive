---
title: "Confused about sudo and root -- Worried about permissions"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by pcardout on 2007-06-01
I just installed *Ubuntu* for first time for my eager teenager.  It works pretty nicely  -- but there are certainly things that don't work yet ... iPods!!

At work I use  *Debian*.  On Debian, you **apt-get **as root when installing new packages.  On Ubuntu -- the custom seems to be sudo apt-get -- and rather than doing it as root, you do it as some user.   I am having 
funny installation problems on things like Banshee and audio drivers and  I am speculating they
might be permissions problems.  

I think I feel more comfortable installing all software as root -- but I've already installed some as a user.  Can someone give me some clarity on what the difference is?  When
you sudo apt-get as a user, are you really installing as root?

I understand that Ubuntu is trying to protect users from being root -- but if I just stick to my old habits can I have some confidence this will work?

Thanks a bunch

---

### Post by coxy on 2007-06-01
Using sudo is the same as being root. If you feel more confident using root it can be enabled as follows:

```

sudo passwd root

```

Please note that this is not recommended by Ubuntu.

---

### Post by dreadlord_chris on 2007-06-01
Hi there. This will help explain the **sudo security model** used by Ubuntu - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Basically, the way it breaks down: sudo = Super User Do = temporarilly assume root privilages to execute the following command.

So, if you *sudo apt-get install blah* - this will install **blah** as **root**

---

### Post by eentonig on 2007-06-01
Or,

you could extend your super user status with

> sudo -i

---

### Post by pcardout on 2007-06-01
OK -- Thanks for the advice and the link to the security model.  It's very interesting. 

I have used sudo in Red-Hat, but there if you are sudoing to do an install, you need root's password.

Ubuntu confused me by never requiring root's password even though iti is (as the several posters responding to my question  have so clearly and graciously stated)  doing rootly thing,

Thanks for all the help.

---

### Post by aysiu on 2007-06-01
sudo uses the user password, and that's the way it should be. If sudo used the root password, there'd be no point in having sudo.

sudo is designed so that you can manage privilege escalation without having a catch-all administrative password that you then have to change once a user leaves the system (for a one-user system the point is probably moot).

---

