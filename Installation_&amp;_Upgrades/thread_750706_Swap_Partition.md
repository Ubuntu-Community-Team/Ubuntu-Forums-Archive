---
title: "Swap Partition"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by DocHolliday2006 on 2008-04-09
Hi. I'm partitioning my hard drive. I've created my 6000mb mount point "/" directory. I've created my 160055 /home directory, I know i need to create a swap partition with my remaining 3000 mb, but I can't figure out how. What mount point should I use? I can't find anyone explaining how to do it. Anyone?

Thanks.

---

### Post by ibutho on 2008-04-09
Swap is used like virtual memory, so does not need a mount point. Unless you are running a server or apps that are heavy on memory 3GB of swap is too much in my opinion. 512MB to 1GB is probably sufficient for most users.

---

### Post by DocHolliday2006 on 2008-04-09
So I just leave it as free space? How does Ubuntu know it's swap?

---

### Post by mikewhatever on 2008-04-09
You have to specify it is in the mount point section. You don't need to format it, but choose 'swap' from the drop down menu.

---

### Post by ibutho on 2008-04-09
You don't leave it as free space. You follow the same steps that you did to setup / and /home, but when it comes to selecting the partition type, choose swap instead of ext3, reiserfs etc.

---

