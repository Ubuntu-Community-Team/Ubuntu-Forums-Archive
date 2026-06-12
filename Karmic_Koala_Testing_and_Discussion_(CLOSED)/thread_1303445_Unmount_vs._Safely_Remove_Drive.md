---
title: "Unmount vs. Safely Remove Drive"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by _sAm_ on 2009-10-28
When I right click on a USB drive with fat32 (icon on my Karmic desktop) I can choose "Unmount"(as before) and also "Safely Remove Drive". What is the different?


And two comments;
"Browse bookmarked and local network locations" via Places>Network(Nautilus) now works as it should - nice:-) For me this didn't work in Jaunty. 

When I right click on a USB drive(icon on my Karmic desktop) I can see a new option called "Format..". I have not tried it yet(only used gparted to do this). I know Windows gives you the same options but I don't like it. Those few times you format the drive you can use gparted, no need to add it to the menu - perhaps most people from Windows like it.

---

### Post by mcduck on 2009-10-28
If the drive has many partitions, "Safely Remove Drive" unmounts them all, while "Unmount" only unmounts the partition that you had selected.

---

### Post by _sAm_ on 2009-10-28
Thank you:-)

---

### Post by forumache on 2009-10-28
> **mcduck said:**
> If the drive has many partitions, "Safely Remove Drive" unmounts them all, while "Unmount" only unmounts the partition that you had selected.

3 options:
Eject
Unmount
Safely Remove Drive

Thanks mcduck, for the explanation of the difference between "Unmount" and "Safely Remove Drive"

Which brings us to the other option: Eject.

I presume Eject does a "Safely Remove Drive" followed by an USB eject?

After Eject the USB drive should not be seen in "Places|Computer", we need to physically remove and insert it again.
"Safely remove drive" will leave it in "Places|Computer" so we can click on it (or one of the partition if partitioned) in order for them to mount.

Is it correct? Anyway I'll test when I get back from work.

---

### Post by VMC on 2009-10-28
This [LINK]("http://www.linuxquestions.org/questions/linux-hardware-18/usb-pen-drive-flash-drive-unmounted-but-the-power-is-there-503208/") has a good discussion on this matter that would concern me. Namely the power being left on.

 Can it safely be removed and also data still flowing prior to removing the flash drive. The link discusses how Windows removes the drive and even a script to emulate removal. 

I don't have any led light left on when I remove my flash drive. Older distros use too. I'm don't sure what precaution karmic takes when you "safely remove" the drive.

---

