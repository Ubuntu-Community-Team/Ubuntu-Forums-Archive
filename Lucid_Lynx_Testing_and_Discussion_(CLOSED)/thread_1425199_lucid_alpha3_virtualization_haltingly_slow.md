---
title: "lucid alpha3 virtualization haltingly slow"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by victor.zamanian on 2010-03-08
I'm extremely excited about upgrading to Lucid because of its pretty new themes and junk, but I'm not too keen on installing the alphas/betas, so I thought I'd do some virtualization to get a sneak peek.

I downloaded the alpha 3 ISO, and I very quickly get to the splash boot screen where you can select to install ubuntu or try it without installing anything and check CD for defects and stuff. After that, however, the virtualization just comes to a virtually complete halt. It doesn't matter which option I choose either.

What happens in VirtualBox I haven't had the patience to wait for, because nothing happens. I just get a black screen. With qemu though, I get a progress bar divided three-fold into a white, a light-blue and a darker blue segment. These progress bar segments reach their completion, and I see the mouse pointer of ubuntu that symbolizes that I need to wait for something (a round, spinning little number if you know what I'm referring to). This is where my patience again leads me to exit the virtualization. (OPP! I just now got the desktop background, but nothing more, but seriously, I'm exiting now. I will probably get to a fully loaded desktop *eventually*, but man... I'm closing it now. Yeah.)

At first I thought there might be something wrong with VirtualBox, so I tried qemu instead, but that gives me the same slow behavior. Is anyone else experiencing this? Is there anything to be done about it? I doubt it has to do with a corrupt ISO, because I've downloaded this thing like 5 times now. Could it just be that this *is* alpha software and it's a little... so so (I doubt this as well since other people are getting it to work!)? Or is it just my host system that is at fault?

Any help appreciated! :)

---

### Post by lavinog on 2010-03-20
I am getting the slow behavior in qemu recently.
It was fine about a month ago.  I started up the vm today, and did over 300M of updates, and got the slow behavior.
I thought maybe it was because I have been just upgrading from the beginning, so I tried a fresh install with the recent daily image, and got the same thing.

I notice just moving the mouse will cause one core on my host cpu to spike.

I tested out a Karmic image, and everything works fine...so it has something to do with the lucid kernel.

---

### Post by victor.zamanian on 2010-03-20
> **lavinog said:**
> I am getting the slow behavior in qemu recently.
It was fine about a month ago.  I started up the vm today, and did over 300M of updates, and got the slow behavior.
I thought maybe it was because I have been just upgrading from the beginning, so I tried a fresh install with the recent daily image, and got the same thing.

I notice just moving the mouse will cause one core on my host cpu to spike.

I tested out a Karmic image, and everything works fine...so it has something to do with the lucid kernel.

I also tested it with a Karmic image and it gave me the same results. Super slow, never starts. I'm giving the virtual machine a quarter of my RAM (512 out of 2048 MB).

Since beta 1 came out the other day, I was super excited to try it, so I thought since none of my virtual machines are working, I would just burn it to a CD and boot up the Live environment and play around, but not even that works. :O I get to this aubergine screen where the Ubuntu logo is showing along with 5 dots underneath it that blink, alternating between white and orange dots. This goes on for an unreasonable amount of time (especially considering the time it takes for the karmic images).

I finally gave up and booted into Windows 7 on my other partition, installed virtualbox there, and THERE it worked. Very odd. At least I got a look at lucid beta 1, but I'm worried about whether the CD will boot at all when it comes to installing the new release later. (I like to do a fresh install with new releases.)

---

### Post by corn13read on 2010-03-20
Had issues in Virtualbox being extremely slow and pausing every X seconds turned out to be the kernel timeing being 10 hz. Upped it to 1000hz and issues are resolved.

---

