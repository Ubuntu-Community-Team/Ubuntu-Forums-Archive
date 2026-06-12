---
title: "Computer resources used by LIVE Cd version of Ubuntu"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2011-03-18
When running Ubuntu from the LIVE Cd is there any read/write activity to the computer's hard drive or does the live session strictly use only the CD drive and the computer's processor and memory ?

I am wanting to make absolutely sure that if I demonstrate Ubuntu from the LIVE Cd that it does not in anyway read from and/or write to the computer's hard drive that might in some way damage the O/S and/or data that is stored on the hard drive.

Thanks.

---

### Post by psusi on 2011-03-18
Generally, yes.  If you have a linux swap partition already on the hard drive, it will use that, and obviously if you open the hard drive from the places menu, it will be mounted and you can modify it.

---

### Post by wpshooter on 2011-03-18
> **psusi said:**
> Generally, yes.  If you have a linux swap partition already on the hard drive, it will use that, and obviously if you open the hard drive from the places menu, it will be mounted and you can modify it.

There is nothing related to Ubuntu installed on the subject computer.

Just to clarify, when you say Generally, yes, do you mean yes, no read/writes to the hard drive occur or do you mean yes, the hard drive is used ?

Thanks.

---

### Post by psusi on 2011-03-18
> **wpshooter said:**
> There is nothing related to Ubuntu installed on the subject computer.

Just to clarify, when you say Generally, yes, do you mean yes, no read/writes to the hard drive occur or do you mean yes, the hard drive is used ?

Thanks.

I mean what I said; if you open the drive then you will cause read/writes to occur.  If you don't ask it to, then it won't.

---

