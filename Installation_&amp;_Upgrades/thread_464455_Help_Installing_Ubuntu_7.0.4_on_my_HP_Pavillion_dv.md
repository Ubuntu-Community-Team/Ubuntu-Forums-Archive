---
title: "Help Installing Ubuntu 7.0.4 on my HP Pavillion dv6258se laptop. (NOT A NOOB)"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by xerxes1986 on 2007-06-04
Hey everyone!

I have recently been trying to install linux alongside Vista on my new laptop but have had nothing but problems. I used vista to shring the "C:\" partition so that my hard drive would have 10GB of unallocated space. Then I first tried to install Fedora 7, since that is the distro used by my school and I am familiar with it. I downloaded the 64bit iso and burned it to a disk, then installed. The installation went fine and it booted into Gnome. The only thing was that it didn't support my wireless card or fully support my video card. So I downloaded the linux drivers from NVidea and installed them. Then when I rebooted it wouldn't boot into the GUI stating the error "X Server not found". I didn't feel like fussing with it so I just went back to vista, deleted the linux partitions to make them unallocated space again, and downloaded the Ubuntu 7.0.4 64bit live/install cd. Burned that, and booted it. I saw the menu and chose "Start/Install Ubuntu", then it went thru some console output and froze. I tried rebooting and re starting the process several times and it froze at different points every time. So I downloaded the 32bit "alternate" install cd and used that to install Ubuntu. Now when I boot my computer into Ubuntu, it shows the Ubuntu logo and the loading bar. After the loading bar is done the screen just goes blank. Nothing. What is going on?! I am getting so fed up with this right now!

---

### Post by xerxes1986 on 2007-06-04
bump

Anyone out there?!

---

### Post by homunq on 2007-06-04
blank screen = bad video drivers

Unfortunately, if you already tried downloading drivers, albeit in another distro, and it didn't work, then I don't know what to say. Maybe you'll have to use some "safe mode" vanilla VGA drivers...

---

### Post by rlee23 on 2007-06-05
**xerxes1986:**  I've got a new Pavilion dv9000z and everytime I try to run the install/Live CD I get the same thing.  I've tried different video settings but to no avail.  It will get to the Ubuntu logo with the scrolling bar but after 30 seconds or so it goes blank or freezes.

I haven't tried any other release yet but I think that'll probably be my next step.

---

### Post by Element921 on 2007-06-05
I've heard of people having problems installing Ubuntu on these laptops, although I didn't have them myself. When you boot into the live CD, try to use [QUOTE=]noapic[/QUOTE] as a kernel paramater and it should work. That's what I did.

---

### Post by jcaveman on 2007-06-06
You probably need to hit F6 when you get to the startup screen and add the following bootup parameters:

noapic irqpoll noirqdebug

Linux has problems withe the way APIC is implemented in the HP BIOS.  Probably has something to do with using the Microsoft compiler instead of Intel's.

---

### Post by nivaca on 2007-07-13
It worked fine for me! Thanks!

---

