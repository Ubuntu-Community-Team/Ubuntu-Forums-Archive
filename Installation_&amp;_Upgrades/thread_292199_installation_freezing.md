---
title: "installation freezing"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by nach0 on 2006-11-03
I've been trying to install Ubuntu on my laptop (IBM Thinkpad) which is currently running XP and I've experienced the installation process freezing with both the Live installation CD Send It! sent me and the more recent 6.10 release that I burnt to disc myself. It will only get so far in the installation and then just freeze up and stop doing anything at all. All I get is a blank screen and no options.

Help?

Thanks.

---

### Post by wpshooter on 2006-11-03
Did you check the integrity of the CDs by running the verification test found on the Ubuntu CD initial boot screen menu ?

---

### Post by Walldorf2000 on 2006-11-03
On the first screen use F6 to enter a boot option.

ide=nodma did the trick for me.

But there are others like noapic, nolapic and acpi=off.

Try one after the other until you found the problem.

Good luck

---

### Post by nach0 on 2006-11-03
> **wpshooter said:**
> Did you check the integrity of the CDs by running the verification test found on the Ubuntu CD initial boot screen menu ?

Yes I have tried on both CDs and neither have returned any errors.


> **Walldorf2000 said:**
> On the first screen use F6 to enter a boot option.

ide=nodma did the trick for me.

But there are others like noapic, nolapic and acpi=off.

Try one after the other until you found the problem.

Good luck

I will try this now, thanks ;)

---

### Post by nach0 on 2006-11-03
None of these boot options worked for me.

Still need help! ](*,)

---

### Post by wpshooter on 2006-11-03
Try the **ALTERNATE** CD.

---

### Post by nach0 on 2006-11-03
> **wpshooter said:**
> Try the **ALTERNATE** CD.

Still nothing :-?

---

### Post by twsnnva on 2006-11-03
Hey Nach0,
Try using the boot option 'vga=791', this solved the problem on my HP dv9047.

---

### Post by nach0 on 2006-11-03
Nope.

I've tried the vga=791 boot option alone and combined with the other suggested boot options and nothing has worked so far. Any more suggestions? Anyone?

I really want my ubuntu back :(

---

### Post by nach0 on 2006-11-04
bump.

---

### Post by spandon on 2006-11-04
Hi,
Try the following (which has worked for me on a laptop and also a desktop:
Using a live cd (6.06 or 6.10)
reboot with disk in machine
when the first screen appears, press escape
the enter the following line
boot: vga 771 napic nolapic
then return
If this works with live cd then that&#347; what you require to install, I used the alternative cd for 6.10 (edgy) worked perfectly
Hope it works for you
Don

---

