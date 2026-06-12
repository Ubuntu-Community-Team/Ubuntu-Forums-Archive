---
title: "Installing Ubuntu on Nvidia Raid 0"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by NextGenHen on 2011-04-03
I am trying to install Ubuntu 10.10 desktop alongside windows 7 on my 2TB Nvidia Raid 0 HDD's but when i select where to install the OS on the ubuntu installation it sees through the raid and only shows the HDD's and no partitions. is there any way to install ubuntu without having to take off Raid? 

Thanks in advance.

---

### Post by ronparent on 2011-04-03
Boot to a live session on cd or usb stick and install kpartx to the session. This usually permits the raid to be seen by the installer and a normal install to a raid partition. Post how you make out.

---

### Post by NextGenHen on 2011-04-04
Thanks for the reply. just tried it and it only shows both of the hard drives and a third blank drive?

---

### Post by ronparent on 2011-04-04
In a live cd terminal type **'sudo dmraid -ay'** and post the results. If the raid is discoverable the results should also appear in /dev/mapper.

---

### Post by NextGenHen on 2011-04-05
Ok just tried and i get 'no raid disks'

---

### Post by ronparent on 2011-04-05
Bad news - although dmraid generally supports nvidia raid it is apparently not finding yours! If dmraid can't discover the raid you won't be able to install Ubuntu to it.

---

### Post by NextGenHen on 2011-04-06
Ok thanks for your help. i remember when i was on the disk utility and i remember seeing NVIDIA Raid and then two HDD's? does this mean that it is seeing it as something seperate?

---

### Post by ronparent on 2011-04-06
Yes, when working properly both the utility and gparted show any component disks separately as unallocated along with the raid partitions. You have to be aware as well as careful not to do anything to the unallocated raid component disks. To do any formatting on them would break the raid.

---

### Post by NextGenHen on 2011-04-06
Ok Thanks. i think ill have another go when i get rid of my raid array in the future :)

---

### Post by ronparent on 2011-04-06
In that case, make sure you delete the raid meta data on the drives that were formerly used as FakeRAID. That data is persistent and has to be explicitly erased or it will plague you in the future. Each drive that was formerly a raid componet has to be treated thus so: ie **sudo dmraid -rE /dev/sda**

---

