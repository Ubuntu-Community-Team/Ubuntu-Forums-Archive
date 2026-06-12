---
title: "No network connection in 10.04"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Neezer on 2010-03-17
Up until the update last night my 10.04 install has worked pretty well. I haven't had any problems at all with network connections. Now I cannot figure out how to sign in to my wireless. I guess I haven't tried wired, but when I click on my network thing in the upper right, I just get that it is disabled. 

Can I just enable it via command line?

---

### Post by Peter09 on 2010-03-18
I booted this morning and my network was disabled, required a right click on the network icon and a tick the the 'enable' box.

---

### Post by go2dell on 2010-03-18
This could possibly be [Bug #497533]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/497533")?

---

### Post by Neezer on 2010-03-18
> **Peter09 said:**
> I booted this morning and my network was disabled, required a right click on the network icon and a tick the the 'enable' box.

Man do I feel like an idiot...I thought I had tried that, but apparently I didn't.

Everything is working great now. Thanks!

quick question....if I am just doing upgrades each day on alpha, will I pretty much have the beta installed by now, or would I just need to go get the beta ISO?

---

### Post by dino99 on 2010-03-19
> **Peter09 said:**
> I booted this morning and my network was disabled, required a right click on the network icon and a tick the the 'enable' box.

i'm still looking at that missing icon, how to show it ?

---

### Post by Chupalav on 2010-04-11
I`ve just installed Kubuntu,everything works well except network connection. I have a standart wired connection trough the router. Win7 works well. Wired connection on other computer with 10.04 also works well. Do you have any suggestions what problem it could be?

---

### Post by recluce on 2010-04-11
I have had the issue for a few days: "Networking enabled" is not checked on startup of the system, you would need to right-click and check it before any networking (wireless, wired) would be activated. This was persistent across reboots.

While I cannot say when that problem was introduced (I don't restart the machine every day), it seems to be solved after applying today's updates (Lucid x64 / Gnome).

---

### Post by bigpup on 2010-04-16
I updated 10.04 over a week ago, and since then I cannot get a network connection. I have tried all the choices I get from clicking or right-clicking the network icon in the taskbar, and repeatedly configured a new wired network connection, but it never gets enabled. Choosing earlier kernels with GRUB gives same results. Dual-booted Windows 7 has no problems, so hardware is not failing. Without network how could I update to a fix?

EDIT: Now, 2 days later, without making any changes to the Ubuntu configuration, I logged into Ubuntu again and networking had no problems. I updated the 12-day-old distro, and networking still works.

(This is on a Sony VAIO CW notebook -- some new hardware that Linux had not seen before January 2010. Ubuntu reps at Southern California Linux Expo ran a suite of tests on it and found a number of issues that they wanted to see addressed in 10.04, but networking was not one of them.)

---

### Post by Chupalav on 2010-04-22
2.6.33 and later kernel versions have correct ethernrt drivers

---

