---
title: "4070 Super - How can I install the driver?"
date: 2024-01-20
forum: Installation &amp; Upgrades
---

### Post by nikanor88 on 2024-01-20
Question in the Title.

I am fairly new to Ubuntu. Got a 4070 Super yesterday and reinstalled ubuntu. "Additional Drivers" shows no additional drivers are availible.

I tried the [https://ubuntu.com/server/docs/nvidia-drivers-installation](https://ubuntu.com/server/docs/nvidia-drivers-installation) UDA drivers, the Latest Production Branch Version: [535.154.05]("https://www.nvidia.com/Download/driverResults.aspx/217147/en-us/") says it has support for the 4070 Super, but I dont know how to properly install this driver as it mentions something about kernel-source, kernel-headers, or kernel-devel package. when I sh the .run driver package, I get an error message which points me to the nvidia-installer.log I attached this file 
 
Hopefully someone can help me

---

### Post by MAFoElffen on 2024-01-20
Open a terminal:
```

sudo apt update
sudo at remove --purge --yes nvidia* libnividia*
sudo apt install --yes nvidia-driver-535 nvidia-dkms-535

```

---

### Post by nikanor88 on 2024-01-20
Thank you!

---

