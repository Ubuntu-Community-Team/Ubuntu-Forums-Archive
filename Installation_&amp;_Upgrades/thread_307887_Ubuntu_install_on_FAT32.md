---
title: "Ubuntu install on FAT32"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by Shin_Gouki2501 on 2006-11-27
Hello i just wanted to ask if it is possible to install ubuntu onto the FAT32 File system and if it is possible , then how?

I have a 400GB SATA/USB HD which is devided into 2x200GB FAT 32.

How can i put Ubuntu on these?
BTW: Strangly when i tried to install ubuntu the "usual" way using desktop CD it failed. The Error said that partion manager was unable to create ext3 partion.

So i want to check out ubuntu! could u help me?

about 170GB of the secound partion are still free either i want to install ubuntu right onto the remaing FAT32 or on a new ext3. My data is very precious to me so im a bit afraid since the failure of the first install. Any ideas?

wbr Shin Gouki

---

### Post by angryfirelord on 2006-11-27
It's impossible to install Linux onto a hard drive that's already been partitioned. You must first get rid of the old partition and then create a new partition. In this case, get rid of the second partition and create an ext3 for / and a swap.

While it is possible to install Linux on FAT32, it is not recommended. Use ext3 instead. 

I'm assuming you have Windows on the first partition and want to keep the data on that.

---

### Post by Shin_Gouki2501 on 2006-11-27
i dont have windows on the 1st or 2nd partion.
If it is possible to install Linux on Fat32 then i should be able to use the 2nd partion?
I guess the disadvantages would be that i would be rather slow...

I have another question: i think about to install ubuntu onto a 4GB  USB stick.

Do i have to use the alternative install CD to customize the instllation so that it fits on the stick?

Would a pen drive installation be much slower then a HD install?

wbr Shin Gouki

---

### Post by angryfirelord on 2006-11-27
Yes, you can use Fat32, but ext3 is much better because it has journaling capabilities. Like I said, just delete it and re-format it as ext3.

A pen drive is MUCH slower than a hard drive install because the USB bus can't provide that much bandwidth unless you need to take your Linux with you. I know that Puppy Linux has its own special installer for USB drives. I don't know how or wouldn't recommend installing Ubuntu on a USB drive. If you have to, use a more minimalistic distribution.

---

### Post by Shin_Gouki2501 on 2006-11-28
1. thx for replying again!
2.My HD only provides 16MB /s
i think if i get an an pendriver faster then this it should be alright, not?
There are some(buffalo) which get 20MB/s and more. So i think it should work
wbr Shin Gouki

---

### Post by Johnsie on 2006-11-30
You can install Linux on fat32. The first Linux distro I ever used was Phatlinux which was a red hat based distro that installed into  c:\phat


I think it probably worked somthing similar to how you can create virtual paritions in VMWARE with out actually parititioning your disk.

I wouldn't know how to install Ubuntu this way but it may well be possible.

---

### Post by Shin_Gouki2501 on 2006-12-01
Thats sounds nice :D
I still thinking about the pen drive , i decided for buffalo sticks which are qutie fast:
r: 32 MB/s
w: 20 MB/s
The question now is just the size, i read Xubuntu "just" needs 1,5 GB free disk Space so a 2GB Stick would be enghough , which is about 35&#8364;.
4 Gb are far more expensive... ubuntu should take about 5 GB when installed
but the 8GB Pendrive costs 142 &#8364;, so thats too much.

i wanna plug the stick into diffrent PCs... lets see how well this works..

I think before X.Org 7.3 this wont be that easily possible.

wbr Shin Gouki

---

### Post by think2ice on 2007-05-07
I want to install Ubuntu on Fat32 too, and ....

1. what is the loss/disadvantage if install on fat32 ?

2. I assume that if it can be installed on fat32, i can switch to another primary partition just with 'pqboot.exe' (partition magic DOS executable), and Ubuntu just modify BootRecord on active partition and it doesn't modify MBR.

Thanks and sorry my poor english :), i'm indonesian.

best regard,
Think2Ice

---

