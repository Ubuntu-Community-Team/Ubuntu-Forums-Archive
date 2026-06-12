---
title: "Lucid Lynx Not Properly Installing"
date: 2009-12-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mikeac72 on 2009-12-01
Details=
Using Ubuntu 9.10 amd64 LiveCD
Using Ubuntu 10.04 amd64 for installation
Dual boot setup w/Vista
Compaq Presario computer


(Using GParted with 9.10 LiveCD)
Made 2GB Swap Space
Made 25GB EXT4
(Boot from 10.04 CD)
Click install now, follow the prompts
Select ext4 partition as root
More prompts
Click Install
Blah blah blah, 85% Installing Lanuguage Packs
Wait for 30 mins, not working.
Hard reset, can't boot into Windows or Ubuntu.
Why?
I removed the Ubuntu partition, and it still fails.

I did a disk check, and it passed, maybe it's just scratched?
Also, I have Windows Vista x86, but a x64 bit capable processor, is that the issue?
I have not used Vista for a while, and it's still on SP1, which I know is sad.

I have my Vista repair disk ready, thankfully.  Neosmart.net was smart to provide it...

---

### Post by linux6994 on 2009-12-01
Same here 85%, I need to get Ubuntu back with wireless working, will have to change distros if not.

---

### Post by Gina on 2009-12-02
If you install an earlier version of Ubuntu (into a separate partition) that will fix the MBR and give you that version of Ubuntu and Windows (and any other OS installed).

---

### Post by kansasnoob on 2009-12-02
It would not be at all surprising at this point to have a Lucid daily build live cd fail.

So goes the development process :)

BTW if you're multi-booting with another Ubuntu OS you can just restore that OS's grub.

---

### Post by SunnyRabbiera on 2009-12-02
its not even in alpha yet, expect errors

---

### Post by Zoot7 on 2009-12-03
I enabled the Lucid toolchain a while back on a testing hard drive and it won't boot with the implemtation of Kernel 2.6.32 it installed.

Oh well.. it's the nature of development releases. Don't expect them to work smoothly. ;)

---

### Post by cariboo on 2009-12-03
I just installed today's, 12/03/09, daily build in vbox, it installed with no problems.

---

### Post by TKbuntu on 2009-12-03
I had the same problem (livecd install hung at 85%) using the 30 Nov build.  Today I stepped up to the 3 Dec build (via zsync) and the install completed as expected.

---

