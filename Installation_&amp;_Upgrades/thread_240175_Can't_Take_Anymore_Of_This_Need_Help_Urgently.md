---
title: "Can't Take Anymore Of This Need Help Urgently"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by xybermaster on 2006-08-20
[IMG]http://i21.photobucket.com/albums/b271/kerlan/Screenshot.png[/IMG]
[IMG]http://i21.photobucket.com/albums/b271/kerlan/frag2.png[/IMG]

As you see the pictures speak for itself AGAIN FOR THE THIRD TIME.](*,)  You all told me to "defrag defrag defrag". Well guess what, I "defrag defrag defrag" until it cannot defrag anymore. I also used perfect disk 7 as recomended by you all and thats the best it can do. Its the first option of installation by the way and the only one I want to choose. Ive used other linux OS and i never had to do this. Just create a swap and ext3 partion and install. Why is ubuntu trying to make things so difficult](*,) . No wonder why the linux community is so small compared to windows. We need user friendlyness!:) The largest continuous freespace is 11.23GB

---

### Post by Qrk on 2006-08-20
I'm afraid you are trying to do it backwards. You don't have enough free space on hda1 to reduce it to 7.5 GB. The slider shows the space of the remaining partition, not the expanded free space. So, you should resize hda1 to be, say, 30 GB to make room for ubuntu.

---

### Post by xybermaster on 2006-08-20
> **Qrk said:**
> I'm afraid you are trying to do it backwards. You don't have enough free space on hda1 to reduce it to 7.5 GB. The slider shows the space of the remaining partition, not the expanded free space. So, you should resize hda1 to be, say, 30 GB to make room for ubuntu.

Ok! Thank you! Ill do it again. If it doesn't work then ill have to get another hard drive or try another linux.

---

### Post by Irony on 2006-08-20
Yes you need to resize to +63%, actually more like 80% - note if you have too little space on XP you will find that the defragmentation process won't have enough room to work.

---

