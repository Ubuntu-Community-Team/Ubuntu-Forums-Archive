---
title: "X fails to load on 7.04 desktop CD"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by web250 on 2007-04-21
I'm trying to install Feisty (I'm on dapper right now)...but X fails to load in both standard and safe graphics install.

I have a Dell e1505 with an ATI x1300. How can I remedy this?

---

### Post by spin2cool on 2007-04-21
I have similar problems on my dell desktop with an added video card.  What I always end up doing is going into the BIOS and choosing the onboard video.  The install CD picks that one up fine.  Then I do my install, install the appropriate drivers using Envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html))  and reboot.  Change the BIOS back to your ideo card, and you should be in business.

---

### Post by web250 on 2007-04-21
I found this solution, and am now in Feisty:

sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx

---

### Post by Sjun on 2007-04-22
> **web250 said:**
> I found this solution, and am now in Feisty:

sudo apt-get install xorg-driver-fglrx
sudo sepmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx

Worked for me too, except that 'sudo sepmod -a' was an unknown command. (so I skipped it)

---

### Post by web250 on 2007-04-22
> **Sjun said:**
> Worked for me too, except that 'sudo sepmod -a' was an unknown command. (so I skipped it)

Whoops! That should be depmod

---

### Post by lesio on 2007-04-23
> **Sjun said:**
> Worked for me too, except that 'sudo sepmod -a' was an unknown command. (so I skipped it)

It solved the problem at my laptop too. I have Dell Inspiron 6400 with Ati x1400.
First I installed Feisty from alternate CD. Than used the above commands (except of course the incorrect line). X started but without DRI. 
Than I found this tutorial: [ATI Installation Guide On Ubuntu Edgy]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide").
After disabling Composite acceleration works fine.

---

