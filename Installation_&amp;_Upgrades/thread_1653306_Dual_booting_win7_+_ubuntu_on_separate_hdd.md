---
title: "Dual booting win7 + ubuntu on separate hdd"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by CptSnork on 2010-12-26
Hello!

I've come to a standstill with a seemingly easy problem... but I can't get it to work for the life of me. I revived a semi old machine with a new mobo and want to dual boot. I have 3 hdds:

/dev/mapper/nvidia_bebcfifh (500GB)
/dev/sda (150GB)
/dev/sdb (250GB)
/dev/sdc (250GB)

I raided and stripped the two 250's and want ubuntu to live and boot from there (currently unallocated). I have already installed win7 on the 150GB hard drive which works fine. 

I've failed a few times with the semi automated installation method  (ubuntu gui) but I just need some pointers on how to do this manually. What do I need to read/know/do to get going on this (a good grub tutorial)? I have dual booted from the same hdd with separate partitions which was easy compared to this. Any help would be appreciated.

Thanks!

---

### Post by wilee-nilee on 2010-12-26
> **CptSnork said:**
> Hello!

I've come to a standstill with a seemingly easy problem... but I can't get it to work for the life of me. I revived a semi old machine with a new mobo and want to dual boot. I have 3 hdds:

/dev/mapper/nvidia_bebcfifh (500GB)
/dev/sda (150GB)
/dev/sdb (250GB)
/dev/sdc (250GB)

I raided and stripped the two 250's and want ubuntu to live and boot from there (currently unallocated). I have already installed win7 on the 150GB hard drive which works fine. 

I've failed a few times with the semi automated installation method  (ubuntu gui) but I just need some pointers on how to do this manually. What do I need to read/know/do to get going on this (a good grub tutorial)? I have dual booted from the same hdd with separate partitions which was easy compared to this. Any help would be appreciated.

Thanks!

Do all three HD show up in the bios?

---

### Post by CptSnork on 2010-12-26
Yes. Bios is seeing all the drives.

---

### Post by wilee-nilee on 2010-12-26
> **CptSnork said:**
> Yes. Bios is seeing all the drives.

So it is hard to tell exactly what's going on do this so we can see the whole setup. So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

Should be straight forward if your seeing all 3 Hd's just a install to sdb or sdc pointing grub there from the custom install area, then making sure it is first in the boot line in bios for grub to run the boot. You have the MS bootloader in sda that is good it can be booted independently if needed.

---

### Post by CptSnork on 2010-12-26
> **wilee-nilee said:**
> So it is hard to tell exactly what's going on do this so we can see the whole setup. So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

Should be straight forward if your seeing all 3 Hd's just a install to sdb or sdc pointing grub there from the custom install area, then making sure it is first in the boot line in bios for grub to run the boot. You have the MS bootloader in sda that is good it can be booted independently if needed.

Well what do you know... I reinstalled ubuntu but this time I pre-formtated the raid array with gparted and it worked. I will post my current boot record anyways because although I can boot into both OSs just fine I still get an error message when I boot ubuntu (it does not display long enough).

---

### Post by wilee-nilee on 2010-12-26
Hard to really real tell originally if you removed or added raid. You don't need raid but post the script those that know can help I suspect.

---

