---
title: "Unbuntu 10.10 Install on Raid"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by KwanX on 2011-04-02
Hello - New to Ubuntu, have read many guides on installation.
 
I have a server w/:
-300G single drive
-5x 300G Drives as Raid 5
 
The installer recognizes both.
 
I would like to install all (ideally on the Raid drives) or the basics on the single drive and as much as possible on the Raid drives. I have made many installs, but have not been successful.
 
I am installing Ubuntu Desktop Edition.
 
 
-Default install on 300G - everything is fine
-Default insatll on Raid only - server hangs on boot with only cursor
-Many combinations of partitions/directory unsuccessful - server hangs on boot with only cursor
 
 
Ideally I want to have(or at least I think I want to have based of what I have read):
 
_300G single drive:_
-/
-/boot
-swap
 
_5x300G Raid5:_
-/var/log
-/home
-/usr/local
-/tmp
-/opt
-/storage
 
 
Basically I want to boot off of the 300G, and have everything else on the 5x300G Raid 5.
 
 
 
 
Any help/advice is greatly appreciated - thank you for reading!

---

### Post by ronparent on 2011-04-02
Go to this site: [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)
You will be prompted to download the BootInfoScript. After downloading it running it should post the results on your desktop. Re-post the result here and give us a look at it.

What kind of software raid are you using? If fakeRAID, it may not be supported by dmraid for all chipsets.

---

