---
title: "Screen Resolution - How Can I Fix this??"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by imari2542 on 2008-10-13
Hi all,

I installed Intrepid, prior to that I was using Hardy.  I was able to fix my resolution before through ALT + F2 but I see that option is no longer available with Intrepid.

Well I have been reading and reading for hours through the forums and trying out what I can but am getting nowhere with my resolution which was a 800 x 600.

I just installed the NVidia Drivers and now my resolution is even worse, now I'm at 640 x 480.

Please help me with fixing this. I really appreciate it.  Thanks.

---

### Post by philinux on 2008-10-13
how did you install the drivers. Did you use System>Admin>Hardware drivers.

What card is it?

---

### Post by imari2542 on 2008-10-13
I went into Preferences.. Appearances..Visual Effects, clicked on Normal and was prompted that way to install the drivers.  I was just able to get back to the 800 x 600 resolution.  I need a higher resolution then that.

My Card is a Nvidia GE Force 6150 SE

Thanks for your help

---

### Post by nikgare on 2008-10-13
> I was just able to get back to the 800 x 600 resolution.

What do youu mean by that?
What did you do?

Can't you use **System->Prefences->Screen Resolution** to change the resolution?

---

### Post by imari2542 on 2008-10-13
When I try to change my resolution that way, the highest choice I have is 800 x 600. There are no higher options.

What can I do so I have higher options?

---

### Post by nikgare on 2008-10-13
Is the monitor being detected properly?
Maybe you need to specify exactly which monitor you have using Nvidia X Server Settings app

---

### Post by imari2542 on 2008-10-19
Hello again.

1st I have to apologize for taking SO LONG to reply.  I unexpectedly went into the hospital for a couple of days.  After I got home, I needed to regroup..etc, etc.  Anyway all is fine now.

Thank you so much for your help it did steer me towards the final solution of fixing this problem.  Part of the problem was that the monitor was not being detected correctly and part of it had to do with the Nvidia Driver.

I wanted to document the steps I took to fix my problem in hopes of helping anyone else with the same problem.

I did the following: 

1.  [COLOR="Red"]Click on System, Administration, Hardware Drivers[/COLOR]....A box will pop up with the available Nvidia Drivers.  I selected the Nvidia Accelerated Graphic Drivers (Version 177) Recommended and then clicked on the "Activate" button.

* Note I had downloaded this driver earlier but obviously had not installed it properly.  Whenever I did click on the Nvidia XServer settings, it would tell me that I was not using the Nvidia Driver.

2.  Reboot the Computer

3.  Log back into Ubuntu

4.  [COLOR="Red"]Click System, Administration, Nvidia XServer Settings[/COLOR]

5.  [COLOR="Red"]Click on Xserver Display Configuration[/COLOR]

6. [COLOR="Red"]Click on Select Resolution[/COLOR] You can then select the proper resolution

Hopefully this works for others. I also read on this link [http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver]("http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver")
which helped point me in the right direction.


Thanks again I really appreciate the time others took to help me.:KS

:guitar:

---

