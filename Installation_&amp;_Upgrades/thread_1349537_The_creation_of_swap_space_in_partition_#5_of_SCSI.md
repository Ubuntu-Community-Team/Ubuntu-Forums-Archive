---
title: "The creation of swap space in partition #5 of SCSI2(0,0,0)(sda) failed"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by sseng_123 on 2009-12-08
I received an error message on my screen during installation. The error was as follows
 
The creation of swap space in partition #5 of SCSI2(0,0,0)(sda) failed.
 
Please help me rectify this

---

### Post by raymondh on 2009-12-08
> **sseng_123 said:**
> I received an error message on my screen during installation. The error was as follows
 
The creation of swap space in partition #5 of SCSI2(0,0,0)(sda) failed.
 
Please help me rectify this

Can you tell us how many partitions you have existing?  If in Ubuntu, access gparted (system > admin > partition editor) and take a screenshot (either use prntscrn key or access the camera thru applications > accessories) ... and attach/upload in your next post.

How important is swap for you?  Do you hibernate your system as a standard practice?  How much RAM do you have?  I ask because depending on your habits, you may not need swap at all.  Even if you do, you can create a swap file also (instead of a swap partition).  Google/search swap file for reference.

Let's see how many partitions you have?  Your HD may be full already.  Or, your install may have borked.

Regards,

---

### Post by sseng_123 on 2009-12-09
Hullo,
 
Please look at the attached screen print.
I dont need the swap that much.
The laptop im using is a brand new Toshiba Satellite L500- 1EN

---

### Post by raymondh on 2009-12-09
> **sseng_123 said:**
> Hullo,
 
Please look at the attached screen print.
I dont need the swap that much.
The laptop im using is a brand new Toshiba Satellite L500- 1EN

sseng ... you do have swap (5.3GB) which you also wrapped around an extended partition (no problems there).

Regards,

---

### Post by sseng_123 on 2009-12-11
Hullo,
 
Raymond.
 
I didnt get you. You mean I shouldnt do the swap at all

---

### Post by raymondh on 2009-12-11
> **sseng_123 said:**
> Hullo,
 
Raymond.
 
I didnt get you. You mean I shouldnt do the swap at all

Sseng,

Sorry for the confusion.  You're thread title suggested that you did not have swap.  You do have swap as shown by your attachment.

Regards,

---

### Post by sseng_123 on 2009-12-12
Hi
 
My installation still stalls at 15% with an error that reads as follows:
Input/Output error during read on /dev/sda.
 
Could this be because my CD drive is SATA and not IDE.
 
Or could be it that the permissions on /dev/sda dont allow read operations.
Im still figuring out the solution to this problem.

---

### Post by Bartender on 2009-12-12
sseng -
I have a question for you.  I've looked at dozens of GParted screenshots and home-made pictures such as yours but don't recall ever seeing the Linux OS mounted as "/target".  Can you explain that?  How come it's not "/"?

I have no idea what target means...:(

Also, that description of the hard drive as SCSI2**(0,0,0)**(sda) seems odd.  Maybe the two are related?

---

### Post by presence1960 on 2009-12-12
> **Bartender said:**
> sseng -
I have a question for you.  I've looked at dozens of GParted screenshots and home-made pictures such as yours but don't recall ever seeing the Linux OS mounted as "/target".  Can you explain that?  How come it's not "/"?

I have no idea what target means...:(

Also, that description of the hard drive as SCSI2**(0,0,0)**(sda) seems odd.  Maybe the two are related?

+1 

That is the first thing I noticed.

---

