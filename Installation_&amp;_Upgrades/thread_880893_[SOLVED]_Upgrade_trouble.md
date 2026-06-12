---
title: "[SOLVED] Upgrade trouble"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by chuky on 2008-08-05
Hi to all
After several months of tinking, I took the plunge and upgraded from gutsy to hardy, I chose the internet route, because it looked the best, but it turned into a nightmare, first the download took 20 hours !!!, and after that it was worse, once the installation began,  it got stuck in "generating locale.... en_AU.UTF-8" and it was locked solid.  not only the process was frozen also the pc was

in desesperation I shutdown it, restarted, and the desktop was unconfigured, no menus no launchers no nothing!!! 

Since then I had been  using the recovery console but is allways the same , I run dpkg --configure -a, and get stuck in "Generating Locales... en_AU.UTF-8"

had somebody the same problem?, can anybody help me?

Thanks in advance

Carlos Pacheco

---

### Post by georgc on 2008-08-05
Hi Carlos,

I have exactly the same problem as you (except it didn't take 20 hours to download). Got stuck in the same place, same symtoms, nothing works.

Sorry I can't help, but I sure would like a solution from the experts.

Best Regards
Cliff

---

### Post by snowpine on 2008-08-05
It is a known bug with high priority: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959)

(scroll down to Facttech's post from 7-16)

---

### Post by metalk9 on 2008-08-05
This is exactly what happened to my Dads ubuntu desktop yesterday. He is in England and I live in Denmark. 
I installed Hardy for him while I was over last year and he has been using it happily ever since. I personally would never attempt to upgrade using apt as I know how flaky it can be. He claims it was the update manager that prompted him to do the upgrade and as I had told him that updates were good he thought that an upgrade would be even better! 
Can it be true that the update manager prompts for dist-upgrades? I haven't used ubuntu for a while, but I don't seem to recall this being the case. I can't imagine how else he would have done it though. Imho it's a pretty bad idea to encourage people to upgrade like this without warning them of the risks involved. 
I'm going to attempt to resolve the problem via ssh tommorow, I'm thinking that if I can remove the locales packages and get a base system configured then I might be able to sort it out from there. Doesn't hurt to be optimistic does it?:KS

---

### Post by chuky on 2008-08-05
Hi cliff
waiting for an answer, I trird a different aproach, on chosing the recovery mode, I allwais chose the las kernel i have (2.6.22-15 i tink), this time I chose the oldest (2.6.20-15) It worked!!!, the locale configuration finised, and upgrade proceded thil it aborted later, try this Cliff and let´s see what hapens

Carlos

---

### Post by chuky on 2008-08-05
Hi cliff
waiting for an answer, I trird a different aproach, on chosing the recovery mode, I allwais chose the las kernel i have (2.6.22-15 i tink), this time I chose the oldest (2.6.20-15) It worked!!!, the locale configuration finised, and upgrade proceded thil it aborted later, try this Cliff and let´s see what hapens

Carlos

---

### Post by chuky on 2008-08-06
Well, finaly I got my pc up and running, this is what happened, I hope it help someone.

after booting the pc with a older kernel, (2.6.20-15) the locales were generated in sort time, and coninued the installation of the remainig packages,  after a while, dpkg complained that some library was mising, and that several pacages could not be configured, and aborted the installation. I tried booting with a newer kernel, to no avail, te process aborted every time. 

Tired of fighting the upgrade, I did what I should have done from the begining, downloaded the install cd, booted from it, chose "repair a broken system, and after chosing a console, run "dpkg --configure -a", voila! 15 minutes later, it finised, I rebooted and my desktop showed up, as usual. 

There is still some rough ends in my machine, I had just configured the WiFi card, Vmware still no run, had to get multimedia codecs, but finaly my pc is working, and the lesson is learned, next time I will get the instal cd FIRST!!!

P.S. Tanks to ali_1 for his help in configurin the WiFi card

---

