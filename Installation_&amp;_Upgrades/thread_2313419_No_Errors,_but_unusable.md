---
title: "No Errors, but unusable"
date: 2016-02-12
forum: Installation &amp; Upgrades
---

### Post by pyrophorus2 on 2016-02-12
I upgraded my desktop from 15.04 to 15.10 no problem 
 
The Laptop I tried and left it. I'm not getting an error, but the splash is on constantly 
How can I resume/restart the installation or even go...

---

### Post by Nuno_Abreu on 2016-02-12
Are you talking about a live USB/DVD? You might be stuck with a driver problem. What if you try **xforcevesa nomodeset **on the booting options?
Check this thread out: [http://bit.ly/1TgbJYz](http://bit.ly/1TgbJYz)

---

### Post by grahammechanical on 2016-02-12
A little bit more explanation would be helpful. As you see. we cannot decide if you are trying to run a live session on this laptop or if this problem is happening to an installed version of Ubuntu. And because you spoke of upgrading a desktop from 15.04 to 15.10 we do not know if this is a result of an attempt to upgrade the laptop from 15.04 to 15.10.

On this laptop do you get the motherboard POST/splash screen? Do you get the Grub boot menu? What splash screen is this? A Ubuntu purple screen with 4 or 5 white dots that change colour?

Also, it is customary to tell us the hardware specifications and whether there is another OS installed. It might be useful information. It might not be useful information. But without it we cannot decide if it is useful.

Regards.

---

### Post by pyrophorus2 on 2016-02-12
> **grahammechanical said:**
> A little bit more explanation would be helpful. As you see. we cannot decide if you are trying to run a live session on this laptop or if this problem is happening to an installed version of Ubuntu. And because you spoke of upgrading a desktop from 15.04 to 15.10 we do not know if this is a result of an attempt to upgrade the laptop from 15.04 to 15.10.

On this laptop do you get the motherboard POST/splash screen? Do you get the Grub boot menu? What splash screen is this? A Ubuntu purple screen with 4 or 5 white dots that change colour?

Also, it is customary to tell us the hardware specifications and whether there is another OS installed. It might be useful information. It might not be useful information. But without it we cannot decide if it is useful.

Regards.

I'm very sorry about this.

The motherboard screen does popup, I only get the grub menu on the CD.

The boot without the CD does the following:
It usually flashes a few things, before going to the purple splash screen, with the 5 dots.
The dots do change colour, and keeps doing that.

There is no other OS on the computer, just moving from 15.04 to 15.10

---

### Post by Nuno_Abreu on 2016-02-12
> **pyrophorus2 said:**
> I'm very sorry about this.

The motherboard screen does popup, I only get the grub menu on the CD.

The boot without the CD does the following:
It usually flashes a few things, before going to the purple splash screen, with the 5 dots.
The dots do change colour, and keeps doing that.

There is no other OS on the computer, just moving from 15.04 to 15.10

Try to inform us what's the output of the running processes when the splash screen is on by clicking on F8/DEL. Like I said in my previous post, it could be a problem with the driver support - it happens a lot!

---

### Post by pyrophorus2 on 2016-02-12
I still think its something to do with 15.10 not being fully or correctly installed.

I will try it though.

---

