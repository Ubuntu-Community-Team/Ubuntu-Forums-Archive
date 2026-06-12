---
title: "[SOLVED] burned install disks have an install error"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by luckymoonboy1 on 2008-05-21
ok i downloaded the ubuntu 7.10 and 8.04 ISO's from the OSUOSL and i put them on my flash drive and took them home to burn. i burned them to cd's via power ISO. so when i go to install them they say something about disk read error that it is either my hard drive, or  a damaged install disk. the disks are new, and my hard drive is fine. does power ISO have a problem with burning ubuntu ISO's? does anybody else know what to do?

---

### Post by VMC on 2008-05-21
> **luckymoonboy1 said:**
> ok i downloaded the ubuntu 7.10 and 8.04 ISO's from the OSUOSL and i put them on my flash drive and took them home to burn. i burned them to cd's via power ISO. so when i go to install them they say something about disk read error that it is either my hard drive, or  a damaged install disk. the disks are new, and my hard drive is fine. does power ISO have a problem with burning ubuntu ISO's? does anybody else know what to do?

Is power ISO a Windows program? I don't recognize that name. If you are using Windows you can burn with a fine program called [ImgBurn]("http://www.imgburn.com/index.php?act=download") and its free.

Also do you have any programs to look inside that ISO just to check if its structure is intact. 7zip will do that, and its free as well.

---

### Post by iaculallad on 2008-05-22
What VMC is talking about on checking ISO's structure is checking it's MD5 signature if it corresponds to the original hash. Usually this is printed on a file which comes along with the ISO file itself or you could look at the webpage to where you downloaded the ISO file. If you got the correct MD5 has, try to burn it at a lower speed (4x).

If you're burning it on windoze, try downloading this [MD5 utility]("http://www.fourmilab.ch/md5/") first and use it to check your ISO file.

PowerISO is executes both on [windoze]("http://www.download.com/PowerISO/3000-2646_4-10439118.html?part=dl-10439118&subj=dl&tag=button") and [Linux]("http://www.poweriso.com/poweriso-1.2.tar.gz").

---

### Post by luckymoonboy1 on 2008-06-10
burning at a lower speed helped. thank you for all the help.

---

