---
title: "Duelboot|Ran chkdsk on Windows, now Ubuntu loads Grub commandline"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by rationalthinker1 on 2012-05-31
Hello, I have duel-boot Windows 7 and Ubuntu 12.04. When I chose Windows, it told me to run chkdsk before loading Windows, I did. Now when I choose Ubuntu, all I get is a GRUB command line prompt. How do I fix this?

Thank You.

---

### Post by rationalthinker1 on 2012-05-31
Please help.
Thank You.

---

### Post by oldfred on 2012-06-01
A chkdsk in Windows should not change grub. Are you running wubi which is just a file inside the windows NTFS partition? Then chkdsk may move root.disk and cause issues.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

From Ubuntu liveCD, terminal post this if unsure what you have.

sudo fdisk -lu

That will just show partitions, but if only NTFS then we know you do not have a full partitioned install.

If not wubi, this may work or you can run the bootinfo report.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by rationalthinker1 on 2012-06-03
> **oldfred said:**
> A chkdsk in Windows should not change grub. Are you running wubi which is just a file inside the windows NTFS partition? Then chkdsk may move root.disk and cause issues.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

From Ubuntu liveCD, terminal post this if unsure what you have.

sudo fdisk -lu

That will just show partitions, but if only NTFS then we know you do not have a full partitioned install.

If not wubi, this may work or you can run the bootinfo report.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

Thank you for the reply. I do have WUBI installed. I do see root.disk in its proper location, also. Still, the problem persists. Please help. I had this same problem with my labtop and my main desktop computer. 

Thank you.

---

### Post by oldfred on 2012-06-03
Do you have a Ubuntu liveCD or USB? You can download this into that and run it or download it as a full liveCD. post the link it creates so we can suggest repairs. I am not real knowledgeable on wubi.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

