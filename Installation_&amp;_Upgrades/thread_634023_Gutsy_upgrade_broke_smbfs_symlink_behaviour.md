---
title: "Gutsy upgrade broke smbfs symlink behaviour"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by shinyblue on 2007-12-07
[LIST]
[*]Existing, not-altered samba server has a **symlink** (filename intranet) from a **samba share** to somewhere else on the drive (/var/www/intranet).

[*]When mounted on other machines, /path/to/mount/point/intranet used to access the correct place, but now fails because it is looking for /var/www/intranet on the LOCAL machine instead.

[*]There are various related smb.conf options (follow symlinks -- defaults to yes; wide symlinks also set to yes; unix extentions set to yes) but** I am not able to change the server**. 

[*]Using the kioslave smb://server/share/intranet **does still work** as expected.

[*]So seems to be a problem with smbfs?

[/LIST]

**This means I cannot access data anymore.**

Meanwhile I've downgraded samba back to Feisty, but has anyone found a solution? Should I report a bug?

Support much apprecaited!

Thanks,
Rich.

---

