---
title: "unable to upgrade from 10.04 to 10.10"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by jackal_79 on 2011-04-13
Hi, Iam unable to upgrade my ubuntu from 10.04 to 10.10.I tried with update manager.It started very fine until the very end it aborted because it was unable to fetch below files.Can someone help me with this please?

Failed to fetch [http://ubuntuarchive.hnsdc.com/ubuntu/pool/main/g/gimp/gimp_2.6.10-1ubuntu3.2_i386.deb](http://ubuntuarchive.hnsdc.com/ubuntu/pool/main/g/gimp/gimp_2.6.10-1ubuntu3.2_i386.deb) 404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.10-1ubuntu3.2_i386.deb](http://ubuntuarchive.hnsdc.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.10-1ubuntu3.2_i386.deb) 404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.10-1ubuntu3.2_all.deb](http://ubuntuarchive.hnsdc.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.10-1ubuntu3.2_all.deb) 404  Not Found

---

### Post by zvacet on 2011-04-13
It look there are third party repos,so in terminal

```
gksudo gedit /etc/apt/sources.list
```

and put # sign in front of that lines.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

When you are finished with upgrade remove # sign but change version name to be sure you get packages for Maverick.

---

### Post by coffeecat on 2011-04-13
> **jackal_79 said:**
> Hi, Iam unable to upgrade my ubuntu from 10.04 to 10.10.I tried with update manager.It started very fine until the very end it aborted because it was unable to fetch below files.Can someone help me with this please?

Failed to fetch [http://ubuntuarchive.hnsdc.com/ubuntu/pool/main/g/gimp/gimp_2.6.10-1ubuntu3.2_i386.deb](http://ubuntuarchive.hnsdc.com/ubuntu/pool/main/g/gimp/gimp_2.6.10-1ubuntu3.2_i386.deb) 404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.10-1ubuntu3.2_i386.deb](http://ubuntuarchive.hnsdc.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.10-1ubuntu3.2_i386.deb) 404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.10-1ubuntu3.2_all.deb](http://ubuntuarchive.hnsdc.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.10-1ubuntu3.2_all.deb) 404  Not Found

All three of those URLs are working now. It was probably a temporary server outage. Try again and hopefully you'll be fine.

---

### Post by jackal_79 on 2011-04-15
> **coffeecat said:**
> All three of those URLs are working now. It was probably a temporary server outage. Try again and hopefully you'll be fine.
Hi, links are working now.I have upgraded by ubuntu to 10.10.Thank You!

---

