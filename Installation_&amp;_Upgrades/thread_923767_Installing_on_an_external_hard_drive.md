---
title: "Installing on an external hard drive"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by Brennagan on 2008-09-18
I have burned the ubuntu iso to the disc and boot up the installer and such and then when it asks where to install to I select manual because i dont want it to install on my internal hard drive. Then the partition manager comes up and shows me all of my partitions and i tried every format it and they all say its missing a boot sector or something how do i fix this? 

Extra info: its an 80gb external hard drive, and it has mac leopard on 40gb of it and free space for the other 40gb ish so that should be plenty of space.

Thanks in advance for the help guys.

---

### Post by oilchangeguy on 2008-09-18
> **Brennagan said:**
> I have burned the ubuntu iso to the disc and boot up the installer and such and then when it asks where to install to I select manual because i dont want it to install on my internal hard drive. Then the partition manager comes up and shows me all of my partitions and i tried every format it and they all say its missing a boot sector or something how do i fix this? 

Extra info: its an 80gb external hard drive, and it has mac leopard on 40gb of it and free space for the other 40gb ish so that should be plenty of space.

Thanks in advance for the help guys.

there is an option to install it inside of windows, just as you would any other software. while you're in windows, load the cd, and this option will appear.

---

### Post by Brennagan on 2008-09-18
I did that now when i try to boot it says 

/
NTLDR is missing
Press Ctrl+Alt+Del to restart

and when i press it it just restarts and has the same error?

---

### Post by oilchangeguy on 2008-09-18
> **Brennagan said:**
> I did that now when i try to boot it says 

/
NTLDR is missing
Press Ctrl+Alt+Del to restart

and when i press it it just restarts and has the same error?

not sure why that would happen if you installed it as a program in windows. but to fix your problem you'll need your windows cd. boot the computer from the cd, when it loads follow the prompts to enter the repair console. then enter the admin password, if none press enter to bypass the prompt. then type fixboot and press enter, type fixmbr and press enter, then type exit and press enter.

---

### Post by Brennagan on 2008-09-18
My vista boots fine (internal hard drive). But i understand what i did wrong i installed it as a program but onto my external hard drive so when i boot up it will ask me vista or linux, but doesnt give me the option of booting Leopard which is also on my external hard drive is there anyway to fix this?

---

### Post by Brennagan on 2008-09-18
I can now find no way to boot Leopad. Also is there anyway to install Ubuntu on the external hard drive so it can be used on multiple computers instead of just that one? Thanks in advance

---

### Post by Brennagan on 2008-09-19
Anyone have any ideas how to fix this? Thanks in advance

---

### Post by caljohnsmith on 2008-09-19
Before you installed Ubuntu, which HDD was first in the boot order, and what happened on start up? Did you get the Vista boot menu? And how were you booting Leopard before?

---

### Post by Brennagan on 2008-09-19
Before you installed Ubuntu, which HDD was first in the boot order, and what happened on start up? Did you get the Vista boot menu? And how were you booting Leopard before?

When I installed Ubuntu the external was first in the boot order but i installed it from vista (on internal) onto my external like the guy above said. When i start up it gives me the option to run ubuntu or linux like usual im guessing and if i dont have the external one plugged in and select ubuntu i get an error. But to boot leopard i would just have my external hard drive 1st in order and it would run the darwin loader and load it. I was just wondering if there was a way to make it any easier like a choice between all 3. And if i select my external hard drive as first and try to load ubuntu through darwin loader i get a weird error.

---

### Post by Brennagan on 2008-09-19
Any ideas anyone? Thanks so far for the help I can boot them all i just cant make it easy to boot them all lol it makes me change my bios anytime i want to boot leopard or boot non leopard

---

