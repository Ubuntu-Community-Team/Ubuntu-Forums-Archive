---
title: "New machine..."
date: 2017-08-22
forum: Installation &amp; Upgrades
---

### Post by alabamatoy2 on 2017-08-22
Well....its new to me.

I have a working Ubuntu 16.04 workstation which is really doing server work, and Im ready to upgrade the underlying hardware, its just too slow with all I have thrown at it.  It has not gotten slower so much as I have just gotten less patient.  I have a nice new disk on the old machine on which the Ubuntu is installed.  Can I just swap that disk into the new PC (they are both SATA), boot him up and have a faster version of my old familiar workhorse?

If the answer is no, what is the best way to bring up the same OS on the new(er) hardware?

---

### Post by RobGoss on 2017-08-22
Hello alabamatoy2, If it's the same drive as in the older machine you might be able to just swap it out and install the new drive, Question? why not do a fresh installation of Ubuntu server instead

---

### Post by Bucky Ball on 2017-08-22
Yes, you can simply swap them over. As most of the drivers are in the Ubuntu kernel itself, when you first boot the install on your disk will pick up the hardware in the new machine and use the appropriate drivers, with the caveat that they're in the kernel in the first place.

One thing to remember is that if you have Ubuntu installed using UEFI mode on the old disk, you will probably need to go to BIOS on the new machine and make sure that is booting the disk in UEFI. You may need more expert help on that, but swapping the drives over is certainly do-able (I've swapped them with no issue and it is not uncommon to do straight swaps with no issue).

When buying a new machine, more important to make sure it has a graphics card and wireless card that is not going to cause a headache, and possibly an insurmountable problem. Do some research for GPU and wireless compatibility before purchasing any new Ubuntu machine.

Good luck. ;)

---

### Post by gordintoronto on 2017-08-23
Ubuntu Server might improve the performance enough to satisfy you. However, it means doing all setup tasks from the command line. 

Most people running Ubuntu Server leave it as "headless," and do everything by an SSH connection from another computer.

Another option might be to simply replace the hard drive with an SSD. I put an SSD into an elderly laptop, and the apparent performance is fabulous.

---

### Post by Bucky Ball on 2017-08-24
Why would you use the server? That will install a whole lot of server stuff you may never use or need. :-k

The minimal iso is just fine. Install, first boot open a terminal, install a desktop environment, a web browser, package manager (if you want any of this stuff, of course), reboot and you're good to go. You can install the rest through your package manager. I used to use something like this on first boot of a mini install:

```
sudo apt install xfce4 firefox synaptic
```

Done. A basic system that will get you started and avoid bloat (including unwanted server stuff).

The mini install also offers a wide range of machine profiles you can choose during the 'tasksel' section of the install. xfce4 desktop? Xubuntu-core? Lubuntu-core? Ubuntu server even? Whatever. If you don't want to select a default profile (and if you're going for minimal as poss, don't) then skip that section and continue.

On first boot you will be confronted with a command prompt after logging in. Issue 'sudo apt install ...' from here and add what you want.

Good luck, whatever you do. ;)

---

