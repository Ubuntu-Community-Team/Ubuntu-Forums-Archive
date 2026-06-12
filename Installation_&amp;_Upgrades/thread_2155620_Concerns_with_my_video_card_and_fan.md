---
title: "Concerns with my video card and fan"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by eakDev on 2013-06-18
Hello,

I just bought a new samsung series 5 laptop. It comes with a prebuilt windows 8. The first thing I did was to install Ubuntu together with it.

Concerns when I'm using Ubuntu:
[LIST=1]
[*]The CPU fan is noisy, I believe it's always at max. (This is not the case when I am in W8)
[*]Ubuntu is not using my AMD Radeon HD 8750M card, instead it's using the Intel HD Graphics 4000. Ubuntu additional driver says. "Activated but not in use"
[/LIST]

Here are the specs of my laptops if it helps:
[LIST]
[*]OS - Dual boot (W8, Ubuntu 12.0.4.2)
[*]Motherboard - SAMSUNG ELECTRONICS CO., LTD. NP510R5E-S01PH
[/LIST]

Thank you for your time!

---

### Post by QIII on 2013-06-18
Hello!

Unfortunately, you are in for a rough time. The OEMs have nor been kind to the Linux community in terms of support for hybrid graphics like yours.

I'm on my cell phone right now so I can't add a link, but look for a thread called "Hybrid Intel/ATI graphics works!" for a good place to start.

There used to be a product called Jupiter to help with this, but I don't think it is actively developed any longer.

Best wishes.  You are headed for some work.

---

### Post by eakDev on 2013-06-18
QIII,

Yeah one tutorial i read mentioned to download Jupiter on software center but i guess they removed it already. I also read few blogs saying that the AMD driver in ubuntu still does not support the AMD version im using. Having said that what would you suggest i do to control my fan speed because my CPU, hard drive and motherboard temperatures are on normal temps but the fan still seems to run at max.

---

### Post by QIII on 2013-06-18
Don't do anything to slow that fan down.  Systems like yours run hot under Linux and your fan is running that hard just to maintain a normal temp.

Unfortunately you will have to live with it, or install Ubuntu in a virtual machine with Windows as the host.  Graphics performance is terrible in virtualization, but at least you won't destroy your new machine.

---

### Post by eakDev on 2013-06-18
That's sad considering ubuntu has been running just fine on my very old laptop. But you're right i just have to deal with it. It's noisy only during the night anyway. Using a virtual machine is not an option for me. I tried it and i just don't feel comfortable with it. 

I'm pretty sure a solution would be given in the next few months, thank you so much for your help! :)

---

### Post by QIII on 2013-06-19
I sure hope someone in the open source world can come up with a workable solution.  I don't think the OEMs are going to be in a great hurry to spend a lot of resources on such a small segment of the market.

---

