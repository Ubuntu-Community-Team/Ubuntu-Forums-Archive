---
title: "Avoiding the 8.10 upgrade while keeping 8.04 up-to-date"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by Manz Luthor on 2008-11-02
Hi everyone.
After having tried Ubuntu 8.04.1 for a few weeks I was beginning to have all of the issues solved and I was quite happy of my new operating system.
I purchased a new HD for my laptop, and got the chance to install ubuntu 8.10 which had been released in the meanwhile.

Everything was working fine, to the exception of the ATI driver, which behaved very slow compared to its performances in 8.04.1, and so I decided to reinstall 8.04.1.

I want to keep all of my applications up to date (through synaptic/apt-get install update, if there is any difference) but I don't **absolutely** want that the kernel or something else will be replaced with 8.10 files.

Is it possible?
I apologize if the question is really that elementary.

M

---

### Post by tommcd on 2008-11-02
See this tutorial:
[http://howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server](http://howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server)
 Go to System > Administration > Software Sources; and go to the Updates tab. In the section for **Release upgrade**, if you select the **never** option, you should not be notified of new releases, including Intrepid. You will still get all the updates for Hardy.
And welcome to Ubuntu, and the Ubuntu forums!!

---

### Post by Manz Luthor on 2008-11-02
Thank you very much! I didn't notice that before. Luckily, the default option was "Long term support releases only" (thanks LTS!) so I accidentally skipped the 8.10 upgrade after going back to 8.04.

Thanks again. :popcorn:

M

---

