---
title: "Install won't complete"
date: 2013-11-23
forum: Installation &amp; Upgrades
---

### Post by jord1981 on 2013-11-23
I'm trying to install Lubuntu 13.10 on my old PC.  I've repartioned and formated the hard drive and scanned it with the utility on the Lubuntu CD, it says no errors.

The install crashes with the following error:

> * Starting Mount network filesystems

* Stopping Mount network filesystems

704.171817] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000007
[  704.171817]
[  704.171860] drm_kms_helper: panic occurred, switching back to text console

It hangs like this indefintely.  Prior to beginning this install for the first time yesterday, the machine was running Windows XP without incident.  I ran it last night and this morning on the Live CD without incident, including copying 12GB of files over the network to another machine.

Any tips would be appreciated.

---

### Post by Bucky Ball on 2013-11-23
What are the specs of the PC? Have you checked the disk for defects with the checksum? At what point does it hang in the install? Do you get to the option 'Try Ubuntu' prior to this?

---

### Post by jord1981 on 2013-11-23
Specs:
Asus Aspire AST180
AMD Athlon 64 3800+ CPU
1GB RAM
160GB HDD

I ran the 'Check disc for defects' from the live CD as well as the SMART utility when booted into Lubuntu - both say no errors.

I was not watching the screen when it scrashed to terminal, but it was far enough along for a second install attempt to believe that Ubuntu is already installed, but not far enough to be able to boot to the hard drive.

I did get and successfully use the 'Try Ubuntu' option prior to attempting the install and again now.

---

### Post by Bashing-om on 2013-11-23
jord1981; Hi !

I am running Lubuntu just fine on an older AMD Sempron chip ! .. You should have no problem with the Athlon chip.
However, when I did that Lubuntu install I did have to NOT enable updates and 3rd party software (check boxes at the initial install screen).
After the install one can do the updates and install any needed additional software ( also then might have to boot with the "nomodeset" option ).

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by jord1981 on 2013-11-23
Thanks for the tips Bashing.  I did have those boxes checked on my previous install attempts.  Trying again without.  Will let you know how I make out.

---

### Post by Bucky Ball on 2013-11-23
Go for the nomodset option also, as mentioned by Bashing-om, just in case. 

At the 'Try' 'Install' window when you boot from the CD, hit F6. From the pop-up list choose 'nomodset'. Proceed. ;)

---

### Post by jord1981 on 2013-11-24
Worked like a charm - thanks so much!

---

### Post by Bashing-om on 2013-11-24
jord1981; Great !

Please mark this thread as solved - 1st post thread tools- as an aid to others seeking a solution and as well help keep the forum tidy.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-11-25
Great stuff! Enjoy. ;)

---

