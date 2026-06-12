---
title: "Cannot boot Windows!"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by Node1 on 2006-08-24
I installed Ubuntu, then wanted to boot to Windows XP Home OEM, once the Windows XP loading screen has finished it goes into another screen and then suddenly restarts and back to the boot menu :confused: 
Can anyone help me?

---

### Post by adds2one on 2006-08-24
Could you explain a bit more. Did you have Windows installed first and then did an install of Ubuntu?

---

### Post by Node1 on 2006-08-24
I had windows xp installed before ubuntu, I made partitions with Partition Magic, and modified them when I was installing ubuntu. When I try to boot xp, it loads but then as I said before it doesnt go into the logon screen but into another screen where it says
xmnt2002 notfound
autochk not found
then it goes to the blue screen and restarts and Im back at the boot menu :confused:

---

### Post by Greycloak on 2006-08-25
It looks like a problem created by Partition Magic.  Have a look here:

[http://service1.symantec.com/SUPPORT/powerquest.nsf/56d21993ad4e6baa88256e91005066ad/b0316214f90fadd888256e9f00607ba5?OpenDocument&prod=PartitionMagic&ver=8.0&src=sg&pcode=pmagic&svy=&csm=no](http://service1.symantec.com/SUPPORT/powerquest.nsf/56d21993ad4e6baa88256e91005066ad/b0316214f90fadd888256e9f00607ba5?OpenDocument&prod=PartitionMagic&ver=8.0&src=sg&pcode=pmagic&svy=&csm=no)

Start windows in safe-mode by pressing F8 a few times immediately after selecting windows from the grub boot menu.  Select 'safe mode with networking' and see if that allows you to login.  If it does, either make the recommended changes in regedit or download this utility to fix the problem:

[ftp://ftp.symantec.com/public/english_us_canada/tools/pq/utilities/BootExecute.zip](ftp://ftp.symantec.com/public/english_us_canada/tools/pq/utilities/BootExecute.zip)

---

### Post by Cairna on 2007-01-12
I realize that this is an old topic, but this is my exact situation and I was wondering...

What should be done if it can't be started in safe mode?

---

