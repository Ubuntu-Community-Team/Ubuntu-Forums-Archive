---
title: "problems with Feisty &amp; Gutsy installs"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2007-08-10
I am having a problem when I attempt to install either Feisty or Gutsy on 2 of my machines.  Both of these machines install and run both Dapper & Edgy just fine.

Both of these machines are using ATI Radeon 9600 video cards and both are basically the same ASUS motherboards of the same model except one of them is the enhanced version.  Both machines support and I have installed ECC memory.  One machine has 1gb and the other has 512mb.  Both machines test fine on memtest.

Any time I attempt to do either a run of the live CD or a direct install or an upgrade to either the Feisty or Gutsy O/Ss on these 2 computers, I start getting a constant BEEPING of the system speaker (**NOT** the audio card system) until the O/S is shutdown.  This BEEPING plus a constantly repetitive/scrollling listing of system log error messages also occurs any time I open the terminal screen and continues as long as the terminal is open and also there after from whatever the initial problem is.

Has anyone else seen this speaker BEEPING behavior ?

Also, someone else suggested to me that perhaps if I blacklisted EDAC, that that might cure this problem.  I have not had a chance to try this yet.  Any thoughts as to whether this might be a possible cure ?

It sort of appears by the looks of the error messages that are being displayed when the BEEPING starts during boot process and those that are being displayed in the terminal that this may be somehow related to a MEMORY problem/incompatibility with the Linux kernel.  Is this possible ?  I do not know how to capture these error messages.  

Thanks.

---

### Post by wpshooter on 2007-08-10
Just to let you know that blacklisting edac did not solve this problem.

Anyone have any ideas ?

Thanks.

---

### Post by wpshooter on 2007-08-11
O.K. I decided to go into BIOS and disable the ECC memory function and just as soon as I did the problem with the constant BEEPING was resolved.

Now what I don't understand is why this would be necessary.  Unless it might have something to do with the fact that the memory in these 2 computers is DUAL CHANNEL.  Because my other 2 computers which do not exhibit this BEEPING problem also have ECC memory and it is enabled in the BIOS **BUT** they do **not** utilize dual channel.

Do you think this is something that is a bug in the O/S that needs to be adjusted by the developers ?

I don't really see why I should be forced to turn off the ECC memory function to use this O/S.

Thanks.

---

### Post by punkybouy on 2007-08-13
I don't think there is such an animal as dual channel ecc memory.  It would either be one or the other.  I could be wrong.  Your bios should detect and configure memory properly but maybe not.  If you enabled dual channel memory in your bios but did not install dual channel memory modules your system might beep as you described.

---

### Post by wpshooter on 2007-08-14
> **punkybouy said:**
> I don't think there is such an animal as dual channel ecc memory.  It would either be one or the other.  I could be wrong.  Your bios should detect and configure memory properly but maybe not.  If you enabled dual channel memory in your bios but did not install dual channel memory modules your system might beep as you described.

You are wrong. 

There **is** dual channel ECC memory.  I have Kingston dual channel ECC memory in both of the computers I am having the BEEPING problem with.

---

