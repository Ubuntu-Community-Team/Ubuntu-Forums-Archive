---
title: "Freezing--New AMD Computer (Dual O/S)"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by Ben_G_9C9 on 2011-03-24
I recently purchased and built a new computer. I have put Ubuntu Desktop on one of the partitions. It keeps freezing at random times with all different programs running (including no programs). It happens usually within twenty minutes of starting. I'll post some of the details of the system. Let me know if you need more.


MOTHERBOARD: Asus M4A785 
PROCESSOR: AMD Phenom II x4 920
RAM: Corsair DDR2 4GB (2GB x2)
VIDEO CARD: Sparkle GeForce 210
O/S INSTALLED: Windows 7 Pro & Ubuntu Desktop 10.10 (64-bit)

---

### Post by Dutch70 on 2011-03-24
You can set desktop effects to "none", Or....

Try post #22 of the "system freeze" link in my sig. It's not specifically for the Intel card, that's just the name the OP chose for the thread.

Let us know if it works.

---

### Post by Ben_G_9C9 on 2011-03-24
This did not resolve the problem. The system still freezes randomly.

---

### Post by Dutch70 on 2011-03-25
Sorry it didn't work for you. Maybe someone else will have a solution or more input on the situation.
However they will probably need more details.

---

### Post by Ben_G_9C9 on 2011-03-25
Bump:: I have some new info on the symptoms. 

I just tried to reinstall Ubuntu 10.10 with the hopes that it was just a bad install. While I was in the partitioning menu, the exact same failure happened. 

Should I go back further and adjust something in the BIOS? If so, I can't think of anything that would be obstructing the good operation of Ubuntu.

---

### Post by MooPi on 2011-03-25
You need to run some tests to see what may be causing the issue. First and foremost run memtest from the grub menu to insure that your ram is up to spec. Just after the bios splash depress the shift key to enter the grub menu. Scroll down to the memtest selection and hit enter. Now if all your ram tests out fine proceed to download prime95 to stress test your CPU.Download from this link [ftp://mersenne.org/gimps/p64v265.zip]("ftp://mersenne.org/gimps/p64v265.zip")
Unpack the archive to a new folder and name "prime95". Open a terminal and navigate to the prime95 folder. To start the application just type in terminal ```
./mprime
``` It will proceed to ask you what you want to do. Just stress test. Now this will stress your cpu and ram very hard and if either is not performing you'll receive an error message. You should let this run for a least a couple of hours to see if it can handle extended heavy loads. Good luck and post back your results to help us determine what advice to give next.

---

