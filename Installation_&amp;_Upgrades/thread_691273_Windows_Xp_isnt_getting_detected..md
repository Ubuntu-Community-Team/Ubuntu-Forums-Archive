---
title: "Windows Xp isnt getting detected."
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by srikar on 2008-02-08
My friend has vista and xp in his pc. He installed kubuntu over vista.The starting grubloader  
doesnt detect xp.What to do????

---

### Post by zvacet on 2008-02-08
```
sudo gedit /boot/grub/menu.lst
```

Find this lines 


# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1

and make them look like 


 title		Windows 95/98/NT/2000
 root		(hd0,0)
 makeactive
 chainloader	+1

Save and close the file.Restart and should see windows in grub.


(hd0,0)= windows are in first disc in first partition.If that is not a case (win are on second then (hd0,1) )

You can fid out where windows are by editing fstab

```
gedit /etc/fstab
```

---

