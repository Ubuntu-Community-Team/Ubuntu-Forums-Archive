---
title: "GUI for driver management?"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by fr4gm0nk3y on 2008-01-16
Hey guys!

I just installed Ubuntu on an old IBM T-42 laptop, It's my first time back on a linux distro in a while. I'm having problems managing and upgrading device drivers (graphics in particular). I'm planning on starting a seperate thread regarding my specific driver problem, but I couldn't help but notice that there's no gui offered for driver management?!?!

 Are there any packages that add a gui to driver management?

---

### Post by luisromangz on 2008-01-16
Usually, driver management is automatic, supported hardware is detected automatically and most drivers are shipped with the kernel, so there is no need to setup anything. Video cards from ATI and Nvidia are problematic, as they are very complex so there is no opensource version that have all the features that closed source ones have, and these can't be shipped with a distro if you want to keep it free.

But Ubuntu has the Restricted Driver Manager, which should help you in those cases.

---

### Post by fr4gm0nk3y on 2008-01-16
> **luisromangz said:**
> But Ubuntu has the Restricted Driver Manager, which should help you in those cases.

That's the problem I'm having =/ When I enable the restricted drivers in driver management it gets messed up. I'll create a seperate post for it like I said, it's just a lot to type out.

---

### Post by Hoaxe on 2008-02-21
> **luisromangz said:**
> Usually, driver management is automatic, supported hardware is detected automatically and most drivers are shipped with the kernel, so there is no need to setup anything. Video cards from ATI and Nvidia are problematic, as they are very complex so there is no opensource version that have all the features that closed source ones have, and these can't be shipped with a distro if you want to keep it free.

But Ubuntu has the Restricted Driver Manager, which should help you in those cases.

but that's the problem now isn't it? how does ubuntu know which driver I want to use? Maybe I feel like using another driver, or modifying and changing an existing driver before compiling it? Maybe there is another open driver out there that I would like to try.

no, a driver manager is a very legitimate thing to demand. But i am not a coder, i do not develop, i simply use but i know enough that it's the code that counts, not the complaining, not the suggesting, but the code that's written there, because at the end of the day it's the code that's being run, not the complaints. so sometimes, i get lucky, and i see this:

[https://blueprints.launchpad.net/ubuntu/+spec/driver-device-manager](https://blueprints.launchpad.net/ubuntu/+spec/driver-device-manager)

and that's always nice.

---

