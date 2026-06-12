---
title: "Partition problem"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by TonyP on 2005-04-09
The installation only detects one partition when I have two ntfs and several linux partitions so there's no other option than format the whole harddrive. Warty worked without any problems.

The harddrive is a maxtor 120gb SATA.


Thanks

---

### Post by trapik on 2005-04-09
i get the same problem...it seems partman don't see my warty 's partitions and my mandrake's partitions     ](*,)

---

### Post by Xian on 2005-04-09
[QUOTE=TonyP]The installation only detects one partition when I have two ntfs and several linux partitions so there's no other option than format the whole harddrive. Warty worked without any problems.[/QUOTE]
Have you made any changes to your partition scheme since Warty? Run the program parted in a terminal session from one of your other linux installs and look for any error messages that might appear. As Ubuntu uses parted this might help to localize the problem.

---

### Post by TonyP on 2005-04-09
I seems warty has the same problem when I tried it again and parted didn't find any devices. I reinstalled WinXP a while ago and maybe that is the source of the problem :P

Any ideas?

---

### Post by Xian on 2005-04-09
[QUOTE=TonyP]I reinstalled WinXP a while ago and maybe that is the source of the problem [/QUOTE]
Yes, this could very well be the issue. You'll need to verfiy your partition scheme via some method, and then make changes as needed. You can do this with some windows applications like Partition Magic, Acronis, and so forth. Or, you can just download a LiveCD like Knoppix  and use that for this purpose. If you do end up having to start from scratch then it would be easiest to use the Ubuntu installer to set your partitions.

---

