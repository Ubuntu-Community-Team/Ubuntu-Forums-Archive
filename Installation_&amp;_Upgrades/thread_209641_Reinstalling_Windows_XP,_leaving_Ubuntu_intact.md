---
title: "Reinstalling Windows XP, leaving Ubuntu intact"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by haddad on 2006-07-05
Hello

I have a dual boot system of XP and dapper, I want to wipe my XP installation clean and do a fresh installation. However I recall XP overwrites MBR by default.

I'd like to leave GRUB handling my boot menu as it is, is there a simple trick to get this done?

Thanks

---

### Post by Dr. Nick on 2006-07-05
Nope, Xp will not let you not overwrite the mbr :( 

Not a huge problem though. When you install XP again just make sure to only erase you xp partition, leave the others alone,

Once XP is installed it will be the only os you can boot into until you get your ubuntu cd and repair grub

look here
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

It may be helpful to look at your current menu.lst to see where the root partiton is. You can see this by runnig this from a terminal
cat /boot/grub/menu.lst, not the phrase similar to this      root     (hd0,2)

---

### Post by tonyr on 2006-07-05
I'm not sure there is a way to avoid having Windows install it's own bootloader,  but there
are ways to easily re-install GRUB afterwards.  Read [RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-3a896b43d621c1410ab4281ba25857b2e6720b5c")

---

### Post by haddad on 2006-07-05
Thanks for the responses

---

