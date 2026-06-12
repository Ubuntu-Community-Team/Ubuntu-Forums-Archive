---
title: "I/O Error When Trying To Boot Live"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by hyrothepyro on 2007-10-19
I have a problem with 7.10 trying to boot is live from cd

When ever I try to run the disc on my desktop i get this error after I tell it to run/install ubuntu from the live disc:

[ 264.677194] Buffer I/O error on device fd0, logical block 0

then after a while it goin on and the front number change and the logical block number changes from 0-7 before starting over at 0...

I've ran the live version on my laptop without issue on this same disc so I know the disc is fine...

My desktop is:
Intel P4, 2.4GHz
1.5Gb RAM
DVD Burner
ATI Radeon x1650 pro (AGP 8x)
Creative Sound Blaster

I have not had any problems booting Ubuntu live from cd before on this machine with any of the past versions...
Any ideas?

---

### Post by mystery on 2007-10-19
I have the same problem.  Splash screen starts OK then goes to a blank screen with cursor blinking in the upper RHC of the monitor.  Booting with the nosplash option shows that the boot stalls at...

Buffer IO error on device fd0, logical block 0

I get the same blank screen on an ASUS laptop but I did not check the nosplash output on this machine.

The disc seems ok (checked it with daemon tools in windows).

System boots normally from the hard disk into dapper.

---

### Post by FCM on 2007-10-19
Try to boot using verbose - I get the same error message but after about 5 or 6 retrys it continues booting - you need to wait a bit longer...Using verbose lets you see each step.

Hope this helps.

---

### Post by mystery on 2007-10-19
Thanks for the advice.  The boot did continue after five or six tries, but ended with a whole page of code which I didn't understand.

---

### Post by costakisss on 2008-03-14
I have the same problem.I let the systeb to boot many times and it keep writing the same thing.The only thing that changes is  the numbers at the start of the line...it starts with 256.xxx.something and it continiues up to 708.xxx and so....at this point the screen goes black.......
 buffer i o error on device fd0 , logical device 0 ......

what else can i try?
my system is :

intel pentium 4
1 gb ram
geforce fx 5200 agp
seagate 20gb hard disk
:confused:

---

### Post by BobvanderPoel on 2008-03-20
I just ran into the same fd0 problem with a new box with up-to-date components. 

The problem is that the boot is looking for a floppy. I have no idea why.

In my system the floppy was not connected, but the bios did have it enabled. Both of these solutions worked for me:

 - disable floppy support in the bios

or

 - leave the bios support enabled and install a floppy drive.

Hope this helps others.

---

