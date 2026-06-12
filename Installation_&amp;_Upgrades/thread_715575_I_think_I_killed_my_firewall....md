---
title: "I think I killed my firewall..."
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by Mythical on 2008-03-05
Today, I installed Firestarter and everything went fine.

I did however, try to configure it to launch on startup using this guide:

[http://www.howtoadvice.com/AutoFirestarter](http://www.howtoadvice.com/AutoFirestarter)

My problem is, now that I have made the changes mentioned in the guide, when I go to System--Administration--Firestarter, a minimized window comes up, but just disappears after a few seconds of loading. It is unclickable. Nothing happens afterward; it's just like I never opened Firestarter at all!

Next, I tried restoring my settings to how they were before. Firestarter still won't show up. I  really need help. Does anybody know what is wrong, and what I should do?

((I hope this is the right forum for this question.))

---

### Post by zvacet on 2008-03-05
Maybe there are some other ways to do it,but I will do this:

1.uninstall Firestarter in synaptic

2. in home directory>view>show hidden files>delete .firestarter folder

Now you can install Firestarter again if you want to.

---

### Post by hyper_ch on 2008-03-05
(1) Firestarter is not a firewall

(2) The firewall is called iptables and it is run by default at boot up

(3) Firestarter is a front-end for iptables

(4) In Firestarter you can set basic rules on filtering... those are effective even when firestarter isn't running because, as said before, firestarter is no firewall

---

### Post by Mythical on 2008-03-05
Thanks. Firestarter is working again, I think.

Sorry for confusing my terms; I'm still pretty new at this. Is firestarter useless without iptables?

---

### Post by hyper_ch on 2008-03-05
it's not only you... it's a lot of "experienced" people that keep calling firestarter a firewall...

well, as said, firestarter only is capable of adding basic rules to iptables... without iptables firestarter can't add anything ;)

---

### Post by zvacet on 2008-03-06
> Is firestarter useless without iptables?

Yes,bacause Firestarter is just front end (GUI) for iptables.Having GUI make easyer to you to make changes if you want to,but you make changes to **iptables**.

---

