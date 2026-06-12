---
title: "help in creating kickstart bootable image"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by jaipsharma on 2010-05-20
Hi All,
 
can anyone help me creating kickstart bootable image for Edubunto 10.4. I tried below steps but the system is failing to boot.
 
1. installed edubunto 10.4 on a pc and created a kickstart file by using the system-config-kickstart package and copied over ks.cfg
2. downloaded the edubunto 10.4 image and opened the image with poweriso
3. updated the text.cfg file under isolinux folder with ks details example ks=cdrom:/ks/ks.cfg file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet –-
4. update the image root with ks.cfg file and save the image file
5. burned the image on DVD and tried to boot my PC
6. when it boots is says isolinux: Image **checksum** error, **sorry**
 
**not sure what am i doing wrong, can any one help me please !!!:guitar:**

---

