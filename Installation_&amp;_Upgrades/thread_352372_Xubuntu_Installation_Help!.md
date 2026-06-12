---
title: "Xubuntu Installation Help!"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by Pranthan on 2007-02-03
I am trying to install Xubuntu 6.10 Edgy Eft

When i partitioned my harddisk like this

hda6 / ext3 7.2GB
hda7 /home ext3 3GB
hda8 swap swap 272MB

It shows an error like this


```

SYSTEM~I_Rp43chnge~1.2 is 1K but it has 2 clusters(16k) ERROR!!
```


When i pressed it show 2 more errors like this...i tried to contue the installation but it get stucked!
what is the problem of my pc?
do i need to increase the size of /home??

---

### Post by kerry_s on 2007-02-03
You need to format those partions again, it looks like they weren't created right. Also alot of linux distro's don't like extended partions.

---

### Post by Pranthan on 2007-02-03
i tried it...when the select & install software installation process becomes 85% the system get stucked
My RAM is 128 MB
so i selected Xubuntu..plz help:confused:

---

### Post by kerry_s on 2007-02-03
Whats all your specs? Sometimes xubuntu takes a while to install cause the repos slow. It grabs some updated stuff from the internet.

---

### Post by Pranthan on 2007-02-03
i have 40GB RAM and contains 2 os win98 & winxp
128 RAM

i have 14 GB free space 

i waited about 20 minutes when the software installation becomes 85% it showed pls wait.....should i wait more time?:confused:

---

### Post by theseeker on 2007-02-06
I noticed what is mentioned above, that the installation gets stuck at 85% ("selecting and installing software). But I notice that my network switch as well as the network card of the pc is on full duty. So my estimation is that it does an apt upgrade silently. My question is, why isn't there any on-screen info about the progress of it, so that ppl don't start wondering if it's really stuck or not? 
My system is Pentium III 650MHz, 128MB ram, 10GB HDD. I guess it's the reason of the delay anyway...! :)

---

