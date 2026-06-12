---
title: "graphics died after upgrade to 3.13.0-41-generic"
date: 2014-12-11
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2014-12-11
Machine is an ASUS UX32-A noteboook, with Intel 4000 graphics card.  This morning I used apt-get to upgrade to kernel 3.13.0-41-generic and it also loaded a whole bunch of rubbish from nvidia, 338 drivers or something.  Why I have no idea, don't use them or need them.  Anyway now all I get is a blank screen.  Run in failsafe graphic mode of recovery system does not work, nor does booting to two previous installed kernels work either.  

Is it possible to roll the system back to exactly the way it was prior to this upgrade?  Alternatively what is the best way to diagnose/fix the graphics problem.

Thanks

J

---

### Post by jamaas on 2014-12-11
I did find a solution, went into the command line and ran 

sudo apt-get purge nvidia*

Let it do its thing and rebooted .... all seems fine.

---

