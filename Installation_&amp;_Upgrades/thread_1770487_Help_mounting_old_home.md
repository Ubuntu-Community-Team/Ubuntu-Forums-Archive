---
title: "Help mounting old /home"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by ratcheer on 2011-05-29
Oops. I just dis a fresh install of Natty, but I neglected to tell the installer to use my existing /home partition, so it created a new one on the / partition. I want to go back to my old /home.

I have a general plan, but I may need advice on the specifics. 1) Create a new user with admin privileges. 2) Logon as the new user. 3) Rename the main user's current /home. 4) Run blkid to determine the UUID of the old /home partition. 5) Edit /etc/fstab to mount the old /home partition at bootup. 6) Reboot.

Step 5 is the only thing I really have questions about. Any advice on the specifics of what to put would be appreciated.

Does this sound like a good plan? Or would I be better off just reinstalling again and telling the installer to use the old partition?

Thanks,
Tim

---

### Post by ratcheer on 2011-05-29
Never mind. It was much easier than all that. I decided to take a more direct approach since, if I messed up, I could just reinstall anyway.

1) Ran blkid
2) Copied the / line in /etc/fstab and modified it for the old /home partition
3) mv /home /home_new
4) reboot

It worked like a charm.

Tim

---

