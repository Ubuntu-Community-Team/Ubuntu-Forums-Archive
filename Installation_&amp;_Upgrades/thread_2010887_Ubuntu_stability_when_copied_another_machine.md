---
title: "Ubuntu stability when copied another machine"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by pelerin21 on 2012-06-26
Hi,

I will get a backup of my ext4 parttiton which includes Ubuntu 12.04.

I will restore this backup on my second machine's empty partition which is bigger than first computer's backuped partition.

If I boot Ubuntu on the second machine, Ubuntu will work properly? I mean it will have driver or other problems?

Thanks you!

---

### Post by pelerin21 on 2012-06-26
I try it. I get a copy from VirtualBox on my desktop machine. Ubuntu booted and worked greak until now. But I am not sure if this was healty.

I need still comments about it ...

---

### Post by pelerin21 on 2012-06-27
Someone help me please? :(

---

### Post by sudodus on 2012-06-27
I am not sure about your situation and question, but I will guess and answer like this.

It is possible to move an installed Ubuntu system (or hard drive or a cloned drive) to another computer (unlike a Windows system).

-If you have not installed any proprietary drivers it should run nicely provided that the new computer will run without proprietary drivers.
- If there are proprietary drivers for example for the graphics and wifi, you may have problems until you change them.

This also means that you can make a truly portable customized system on a USB pendrive.

     -o-

If you have a virtual machine and copy/install its 'machine' file and 'drive' file properly, it should run also in another computer.

---

### Post by pelerin21 on 2012-06-27
> **sudodus said:**
> I am not sure about your situation and question, but I will guess and answer like this.

It is possible to move an installed Ubuntu system (or hard drive or a cloned drive) to another computer (unlike a Windows system).

-If you have not installed any proprietary drivers it should run nicely provided that the new computer will run without proprietary drivers.
- If there are proprietary drivers for example for the graphics and wifi, you may have problems until you change them.

This also means that you can make a truly portable customized system on a USB pendrive.

     -o-

If you have a virtual machine and copy/install its 'machine' file and 'drive' file properly, it should run also in another computer.

That was my answer :) Thank you so much!

---

### Post by sodifficult2day on 2012-07-09
How did you copy Ubuntu to the new machine?

I currently have installed Ubuntu 12.x.x to a USB drive and just about have it all set up perfectly (apart from HDMI sound (laptop speakers work fine) but that is a different matter) but as this is now rather full I will like to copy the whole thing lock stock and barrel to a larger USB drive.  I guess it is not a simple a job as cut and paste?

---

### Post by pelerin21 on 2012-07-11
> **sodifficult2day said:**
> How did you copy Ubuntu to the new machine?

I currently have installed Ubuntu 12.x.x to a USB drive and just about have it all set up perfectly (apart from HDMI sound (laptop speakers work fine) but that is a different matter) but as this is now rather full I will like to copy the whole thing lock stock and barrel to a larger USB drive.  I guess it is not a simple a job as cut and paste?

I don't know if it will work by copy-paste directly. I did not try. But I just get a backup of partition with Clonezilla and now this backup works for my all machines (virtualbox, desktop computer and my other laptop).

---

