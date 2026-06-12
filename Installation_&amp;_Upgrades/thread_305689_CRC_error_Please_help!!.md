---
title: "CRC error: Please help!!"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by kerzane on 2006-11-23
Hey guys,

Somebody must have an idea of what this issue is:

Now I have a CRC error!!

I get to the initial menu, select boot Ubuntu, and then it begins.
As soon as the little green dots are finished running across the top of the screen I get:

"
Decompressing Linux...done.
Booting the kernel.

[ 33.936006] PCI: Cannot allocate resource region 7 of bridge 0000:00:4.0
[ 33.936049] PCI: Cannot allocate resource region 8 of bridge 0000:00:4.0
[ 34.312447] crc error
[ 34.312254] Kernel panic - not syncing: VFS: Unable to mount roots fs on unknown wn-block(1,0)
[ 34.313296]
"

I tried to see if this problem has ocurred for otheer people,
it seems related to the issues discussed at:

[http://www.colug.net/pipermail/colug...er/003467.html](http://www.colug.net/pipermail/colug...er/003467.html)

and

[http://www.ubuntuforums.org/archive/.../t-186115.html](http://www.ubuntuforums.org/archive/.../t-186115.html)

Please help me out. I can't think of what I can do. I can provide any necessary info.

Regards,
Eoin.

---

### Post by deepwave on 2006-11-23
Is this running Ubuntu off the LiveCD or an installed system?

I hope that it is the former.

---

### Post by kerzane on 2006-11-24
It is indeed the former. The LiveCD. Does that clarify anything? As I have no access to any command line, I don't know what I can do. Is it hopeless?

Thanks,
Eoin.

---

### Post by deepwave on 2006-11-24
I think that the CRC error relates to errors in the burned CD.  The CRC error probably relates to a broken init script manager or kernel, both I guess would arise from a corrupted filesystem.  Since only the CD filesystem seems affected in your case, everything should be fine with another LiveCD.

If it were the latter, then you would need to fix a corrupted installation.  Figuring why installations get broken is much more complicated.

---

### Post by kerzane on 2006-11-24
That makes perfect sense to me.

Except for the fact that I reburned the CD, at minimum burn-rate, and got the exact same result. Could the download have been corrupted? Doesn't sound likely to me.

Thanks alot for your help.

Eoin.

---

### Post by deepwave on 2006-11-24
You can check the MD5 sum of the downloaded iso against an existing MD5 hash.
I think on every iso mirror there are ubuntu-version-xxx.iso and ubuntu-version-xxx.iso.md5.  If you run a md5 summing program, like the Windows open source MD5Sumer program, of the .iso against the .iso.md5, you should know if the iso is intact.

---

