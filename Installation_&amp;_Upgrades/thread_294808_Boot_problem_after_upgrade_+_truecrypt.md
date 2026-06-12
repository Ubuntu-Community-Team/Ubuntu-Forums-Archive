---
title: "Boot problem after upgrade + truecrypt"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by frolle on 2006-11-07
After i upgraded from Dapper to Edgy, it seemed to work just fine, but then i tried using truecrypt. I followed the guide perfectly and it was workning. I could mount and dismount without any problem. 

Then i tried one reboot and now my computer couldnt boot. I come to the login screen. I write my username and password, it seems to start up, but just goes back to the login screen.

Then i removed my nvidia drivers and now i only get black screen.

Anyone who can help?

Regards and thanks in advance

---

### Post by wieman01 on 2006-11-07
The harddisk may be full... Seen a similar problem a few hours ago. 

You can delete old Debian packages in this folder to create more space:
> cd /var/cache/apt/archives/

---

### Post by frolle on 2006-11-07
Do you think i made the part for the mount tooo big? I made it 136GB and i have 3gb's left.

Maybe i should delete the mount point completly?

---

### Post by wieman01 on 2006-11-07
I remeber that there is an issue if the space is less than a certain percentage (10% ?)... But I am not 100% sure. You can resize the partition/file and check it out....

---

### Post by frolle on 2006-11-07
Can i do that with truecrypt?

---

### Post by wieman01 on 2006-11-08
I am afraid you'll have to create a new, smaller volume while removing the old one. I could not find a "resize" option.

---

