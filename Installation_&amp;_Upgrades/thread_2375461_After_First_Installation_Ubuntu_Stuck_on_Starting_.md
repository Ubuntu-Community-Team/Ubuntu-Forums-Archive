---
title: "After First Installation Ubuntu Stuck on Starting and Shut Down Screen"
date: 2017-10-24
forum: Installation &amp; Upgrades
---

### Post by ltknk on 2017-10-24
I have installed Ubuntu by following the steps;


 1. I burn ubuntu-16.04.3-desktop-amd64.iso to an flash drive by
    using Rufus 
 2. I have installed Ubuntu as dual boot with Windows 10. (My Computer's Features are below.)
 3. I have allowed to install updates during installion.
 4. After installion when  I pressed restart button system stuck and I forced to shut down by power button.
 5. When I restart computer it opened without any issues but when I try to reboot or shut down it stucked again.
 6. I tried to reboot or shut down by GNOME Terminal but I got same results.
 7. I tried to use TTY but it didn't open TTY and stucked.
 
I have found a solution for shut down problem but it worked one time and now Ubuntu doesn't start.
```


    sudo service cups-browsed stop

```

System Features

   CPU: i7 6700-HQ
   GPUs: Intel HD Graphics 530, NVIDIA GTX 950M
   Manufacturer: MONSTER (It's a local Turkish manufacturer)
   Model: ABRA A7 V5.4
   BIOS: 1.05.09
   SSD: NVMe INTEL SSDPEKKW25

---

### Post by abinthomas744 on 2018-10-07
I have the exact same issue on my msi GV62 7RE 
i7 7700HQ nVidia GTX 1050Ti
I've tried a lot of trouble shooting nothing works

---

