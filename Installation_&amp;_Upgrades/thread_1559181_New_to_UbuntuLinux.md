---
title: "New to Ubuntu/Linux?"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by heaumanepunk on 2010-08-23
Recently I tried installing Ubuntu via CD, I burned the Image like the website said, It booted then it gave a black screen saying init was not found or something in that nature. I tried a few more times with no luck. I am making another CD to see if it works, hopefully it will,. Its a relatively old HDD. It has Win 98 on it. 9.18 GB space.Quantum Fireball lct 10 3.5" series. Pls help.

---

### Post by lechien73 on 2010-08-23
Could you try and catch the exact text of the init error message, please? There are several messages similar to the one you mentioned.

Apart from the hard disk, what is the specification of the machine? Processor, memory, graphics card etc?

---

### Post by mörgæs on 2010-08-23
Welcome to the free world. 

How much memory is in this machine? Most likely this is the problem.

---

### Post by heaumanepunk on 2010-08-23
Ok i solved that problem, It was an issue with the CD itself, now it installs but stops at 62%. Ty for your replies. The error is Errno 5 input output error. Im looking into it still, I will try Kubuntu and see how that works, It has 10 gb of free space, video cards and everything works really well with XP (on another hard drive). Thnx again for the replies. Pls try and help with this new prob.

---

### Post by mörgæs on 2010-08-23
I _am_ trying to help. Again: How much memory is in the machine?

When you boot the CD, do you get an option of 'test CD for defects'?

---

### Post by lechien73 on 2010-08-24
> **heaumanepunk said:**
> Ok i solved that problem, It was an issue with the CD itself, now it installs but stops at 62%. Ty for your replies. The error is Errno 5 input output error. Im looking into it still, I will try Kubuntu and see how that works, It has 10 gb of free space, video cards and everything works really well with XP (on another hard drive). Thnx again for the replies. Pls try and help with this new prob.

Ok - Errno 5 can indicate that there's still a problem with the CD. I would try re-burning the CD at 1x or 2x speed. Try a different CD-ROM drive as well, if you can.

It could also indicate that some of the RAM is faulty, so try removing and re-seating the chips, or running a memory test.

Finally, if your CD-ROM drive is an IDE drive (which is likely), is it running on its own IDE channel as Master? Or is it on the same IDE channel as the hard disk as Slave? If it is a slave device, then try connecting it to its own channel as Master.

Funny how installing a new operating system can highlight hardware problems you never knew you had :)

---

