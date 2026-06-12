---
title: "no keyboard after install"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by quilaho on 2006-10-29
i am trying to setup my previous work computer with ubuntu server in order to do some proof of concepts for management. the install goes beautifully but after the final reboot, i have no keyboard input. i have tried both 6.06 and 6.10 and both end up this way.

the computer's configuration is:
[LIST]
[*]dell dimension 4550
[*]p4 3.02 mgz ht processor
[*]512 mb ram
[*]2 ide hard drives. 30gb -- /boot; swap, /; 80 gb -- /home
[*]janton 2 head pci video card with nvidia mx440 chipset
[*]keyboard is a standard keyboard from an ibm pc
[/LIST]

i have tried swapping out the keyboard.

interestingly, this same thing happens on my home built dual processor p3 when i go to install the smp kernel. i've never figured out what that is all about either.

any help would be greatly appreciated.

---

### Post by quilaho on 2006-11-01
anybody?

---

### Post by mittio on 2006-11-02
I am having the same issue with 6.10 and the edgy preview release.

[This ]("http://tinyurl.com/ykbsc8")is my motherboard. I haven't spent much time trying to figure it out. I figured I'd get the alternate install disc a try next.

---

### Post by mittio on 2006-11-03
I tried using the alternate installer, and the text based installer had no trouble with my keyboard.

After the installation, I rebooted, and at the X login screen, I had no keyboard input.

I rebooted into safe mode, and from the command line I ¨sudo startx"and everything seems to be working.

I´m going to reboot and try it again normally next.

---

### Post by mittio on 2006-11-03
Well, I´m not sure I can explain the ¨why¨, but I´m up and running normally now.

---

