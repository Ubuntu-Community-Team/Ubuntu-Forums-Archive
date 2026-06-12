---
title: "Empty trash on HDD from Ubuntu Live on USB"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by cajunlibra on 2010-03-02
I have to make room on my hard drive because I cannot log in. I cannot even log into the terminal. I am using the Ubuntu Live on a USB drive to access my hard drive. I deleted files but now they are in the trash folder and I cannot empty the trash or delete files from this folder. I tried the #ubuntu channel on IRC but got no response.

THanks to anyone who can help me.


I solved this by opening Nautilus with root permissions (sudo nautilus). Then I changed the permissions for the trash folder (.Trash-0) to allow everyone to create, read, write, and delete and also "Apply Permissions to Enclosed Files". Then in the terminal, I was able to remove the files.

---

