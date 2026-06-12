---
title: "Blank Screen -Only mouse pointer"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Zero7 on 2008-10-01
I freshly installed 8.10 Alpha 6 4 days ago on a Compaq Laptop,(Presario 2103US) with Athlon M Processor with integrated graphics card. It was working great until today's update.

Today, while updating it crashed and on reboot I had to run fsck to check the /dev/sda2, where it has been installed. I had to say yes 1000 times and it fixed the errors. On reboot, it went normal up to showing up wireless key screen, it accepts the key in after that I get only blank screen with a mouse pointer. Window selector pops up with ctr+alt+arrow or scroll wheel.

If I logout using ctrl+alt+backspace, I get the login window, but I can't do anything as "Authentication Failed" window does not go away.

I tried update, upgrade in terminal (ctr+alt+F2). Any number of reboots etc. same situation. TIA for any help.

---

### Post by jerrylamos on 2008-10-01
Alpha 6 Ubuntu gets blank screen, only mouse pointer on IBM Thinkpad R31, 1 gHz Intel Celeron, Intel Graphics.  Early Alpha 5 worked.

Xubuntu & Kubuntu work O.K. (for Alpha's).  It's the combination of Alpha 6 and Gnome 2 that don't.

The 20080930 build gets a little closer.  If I quick do Ctrl-Alt-F1 when X fires up, i.e. brown screen and pointer, I get the expected terminal command line.  Wait until all activity ceases, do Ctrl-Alt-F7 to switch to full screen mode and there is the Gnome desktop, top, bottom lines, proposed Intrepid background, the whole bit - for about a second.  Then black screen.  Dead again.

Jerry

---

### Post by Zero7 on 2008-10-02
I reinstalled Alpha6 and got the latest updates. Issue solved, but lost audio in Youtube.

---

