---
title: "30 sec Grub Loading!!!"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ToxinPowe on 2009-10-07
Hello people, I have Win-XP, Jaunty-32, and now Karmic-64 in  the same machine (3 hard disks). 
 
My problem is with GRUB, it's takes 30 sec!! :confused: before I can see the menu. Any help or clue please?

Thanks.

---

### Post by sc3252 on 2009-10-07
I am having this same problem.  It takes around 25-30 seconds before grub even shows up.  It just sits there on loading grub.  I have 2 hard drives vista on the boot drive and ubuntu on the other.  They are both sata.

PS: Any type of log files needed?

edit:
using amd64 build with the latest updates installed

core 2 duo
P35 motherboard
6GiB of ram
and no floppy if that matters
Also it doesnt matter if its a cold boot or a reboot.

---

### Post by autocrosser on 2009-10-07
Take a look at my bug report & add to it---it's a known issue with multi-disk systems:  [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)

Colin is working on it--he just needs more reports to spend more time in it.

---

### Post by dino99 on 2009-10-07
> **ToxinPowe said:**
> Hello people, I have Win-XP, Jaunty-32, and now Karmic-64 in  the same machine (3 hard disks). 
 
My problem is with GRUB, it's takes 30 sec!! :confused: before I can see the menu. Any help or clue please?

Thanks.

the problem seem to be: where is grub2 installed ? mbr or pbr (partition)

3 hd = 3 grub ?

grub2 work better on mbr ( only on 1 hd, if not it loose time finding the other grub & have to take decision to know which of them is the master)

---

### Post by seamuso on 2009-10-07
Chances are that grub has installed itself to the first hdd in your system which is probably something other than the karmic drive.

If grub is picking up all of your other installed OS's correctly, set your boot drive as the karmic drive and things should speed up again.

You'll also find that any time grub is getting an update (through update manager, not update-grub), it will write itself to the first hdd in your system again.


An easy way to restore your windows mbr ..

[http://www.sysint.no/products/Download/tabid/536/ItemID/2/language/nb-NO/Default.aspx](http://www.sysint.no/products/Download/tabid/536/ItemID/2/language/nb-NO/Default.aspx)

[http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)


The Vista mbr fix works for win7 also

---

### Post by VMC on 2009-10-07
> **dino99 said:**
> the problem seem to be: where is grub2 installed ? mbr or pbr (partition)

3 hd = 3 grub ?

grub2 work better on mbr ( only on 1 hd, if not it loose time finding the other grub & have to take decision to know which of them is the master)

I think Dino has hit the nail on the head here. I have grub2 on mbr and using only one hard drive. Mine boots grub in 2 seconds max.

---

### Post by Podex on 2009-10-07
This is exactly the problem I had and setting the boot drive in the BIOS as the one that has grub2 installed fixed it.
I'm wondering if the new grub2 1.97 beta4 will fix this issue without people having to change their boot priority.

---

