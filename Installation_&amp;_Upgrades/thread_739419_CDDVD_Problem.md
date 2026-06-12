---
title: "CD/DVD Problem"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by m1n054 on 2008-03-29
I have this problem with my driver and it's very weird. When i burn an image to a Blank CD i can't read it, but when i copy the files from the ISO to the CD i can. I'm not using the same computer for burning the CD because it can barely read it! Does anyone know if I copy the files to the CD will it remain bootable? Or do i have to do something else? Because I tried to do it minutes ago, but it just wouldn't let me boot it.

Any suggestions? Thanks.

---

### Post by Pumalite on 2008-03-29
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on the iso, burn at 4x or less on CD-R, as 'image' and not as 'data', check CD integrity after burn and before install. Clean the lens in your burner just in case.

---

### Post by m1n054 on 2008-03-29
I can't read CDs that are burned from Image Files :( that's my problem. I can still open it in other PCs it's just that my drive is nuts.

---

### Post by Pumalite on 2008-03-29
Your drive needs to be changed. Otherwise consider:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
[https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd](https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd)

---

### Post by m1n054 on 2008-03-29
I know. Can you explain me more about unetbootin? I don't want to download the iso again and it seems it download the iso :( Is there a way from installing it from the HD?

---

