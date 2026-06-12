---
title: "Failed to fetch file"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by VideoAddicted on 2011-08-12
When I recently attempted to install Wine onto my computer from the Software Center, after the download bar had filled completely, I received the following error.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.5.4~dfsg-1ubuntu8.4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.5.4~dfsg-1ubuntu8.4_amd64.deb) 404  Not Found [IP: 91.189.88.45 80]

Any insight as to the nature of this error would be extremely useful, and I'd greatly appreciate any suggestions as to a resolution.

Am running Ubuntu 10.10 w/ most current updates.

---

### Post by dino99 on 2011-08-12
open synaptic to use the "main" server instead of actual "us", and be sure to use only 10.10 repos then update again.

---

### Post by varunendra on 2011-08-12
Besides what dino suggested, I also noticed that the error you posted has "1ubuntu" in it. It's numeric '1' in the message, while the correct URL would have 'lubuntu' (small 'L', not numeric '1'). Either it is a typo on your part or a bad package info.

Also, the referred page doesn't have version 8.4. Currently, there is version 8.5 available on the referred page: [http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/](http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/)
You may try downloading and installing it manually and see if the next attempt to install wine succeeds.

---

### Post by VideoAddicted on 2011-08-12
Thanks guys, changing to the main repo server fixed the problem.

---

