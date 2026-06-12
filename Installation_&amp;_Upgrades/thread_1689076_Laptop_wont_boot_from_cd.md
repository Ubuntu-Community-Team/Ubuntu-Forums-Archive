---
title: "Laptop wont boot from cd"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by Reduced_Oxygen on 2011-02-16
Toshiba satellite

Solved: Use the slowest burning speed when making your disk

---

### Post by Koffeehaus on 2011-02-16
How old is your laptop?

If your laptop is older than 2 years maybe you're using wrong architecture. When you downloaded Live CD was it 32bit (i386) or 64bit?

32bit should work on any work station.

---

### Post by Koffeehaus on 2011-02-16
P.S. If you describe your problem in more detail then more people will be able to help you. If it's not architecture problem, explain the output, error messages etc.

---

### Post by Reduced_Oxygen on 2011-02-16
> **Koffeehaus said:**
> How old is your laptop?

If your laptop is older than 2 years maybe you're using wrong architecture. When you downloaded Live CD was it 32bit (i386) or 64bit?

32bit should work on any work station.

i always download the 32 bit and yes its older than 2 years

---

### Post by Reduced_Oxygen on 2011-02-16
> **Koffeehaus said:**
> P.S. If you describe your problem in more detail then more people will be able to help you. If it's not architecture problem, explain the output, error messages etc.

there are no error msg no matter what i do it just boots straight to windows

---

### Post by Reduced_Oxygen on 2011-02-16
> **Koffeehaus said:**
> P.S. If you describe your problem in more detail then more people will be able to help you. If it's not architecture problem, explain the output, error messages etc.

also i dont realy know what else there is to say

---

### Post by Zimmer on 2011-02-16
If BIOS is set to boot from CD first then I can only conclude:
1. CD drive has developed fault.
2. The CD you are trying to boot is faulty..... 

Test by substitution sounds a fair way to go...

---

### Post by Reduced_Oxygen on 2011-02-16
> **Zimmer said:**
> If BIOS is set to boot from CD first then I can only conclude:
1. CD drive has developed fault.
2. The CD you are trying to boot is faulty..... 

Test by substitution sounds a fair way to go...

iv tryed booting from usb but no luck (not supported) and hard drice but then i cant install it because ubuntu mistakes the hard drive as a cd and doesnt let me creat a partition on it (the partitioning menu cant find it at all)

---

### Post by Koffeehaus on 2011-02-16
Oh yes I just remembered! That happened to me a few times.

1. Make sure you burn the CD at slowest possible speed. On Windows I used PowerISO.

2. Make sure your CD's are of reasonable quality, and not Bangladeshi junk from a Poundshop :) Those buggers gave me a lot of trouble when I was starting in IT.

---

### Post by Koffeehaus on 2011-02-16
> **Reduced_Oxygen said:**
> there are no error msg no matter what i do it just boots straight to windows

Yet another suggestion. Since no error messages pop up and you load to Windows straight away, then probably your BIOS is not set up to boot from CD.

Usually at startup you would see two BIOS options

F2 - BIOS Menu

F10 or F12 - Boot menu

Go to boot menu and select boot from CD.
Alternatively go to BIOS menu and change boot hierarchy to CD/DVD being first in the list.

Try this before making a new CD

---

### Post by Reduced_Oxygen on 2011-02-17
> **Koffeehaus said:**
> Yet another suggestion. Since no error messages pop up and you load to Windows straight away, then probably your BIOS is not set up to boot from CD.
 
Usually at startup you would see two BIOS options
 
F2 - BIOS Menu
 
F10 or F12 - Boot menu
 
Go to boot menu and select boot from CD.
Alternatively go to BIOS menu and change boot hierarchy to CD/DVD being first in the list.
 
Try this before making a new CD
 
I have Done all this but same result, however when i go to boot menu at tell it to boot from cd it says unable to boot from cd
 
however your advice on burning sounds pretty good think ill try that

---

### Post by Reduced_Oxygen on 2011-02-21
> **Koffeehaus said:**
> Oh yes I just remembered! That happened to me a few times.

1. Make sure you burn the CD at slowest possible speed. On Windows I used PowerISO.

2. Make sure your CD's are of reasonable quality, and not Bangladeshi junk from a Poundshop :) Those buggers gave me a lot of trouble when I was starting in IT.

THANK YOU this worked a treat :)

---

