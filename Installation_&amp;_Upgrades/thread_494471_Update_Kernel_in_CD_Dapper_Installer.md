---
title: "Update Kernel in CD Dapper Installer"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by marco.catunda on 2007-07-06
I would like to make new iso CD Install image for Dapper with new Kernel. Does anyone how could I do it?
I've searched a lot of document, but I haven't found any howto explaing update kernel in cd image. 

I want to do it because de new production server has a diferent scsi raid board and the driver of this board is on new kernel 2.6.20. The Ubuntu Feisty release was installed without problem, but I wouldn't like to use it in production environment.

---

### Post by kagashe on 2007-07-06
> **marco.catunda said:**
> I would like to make new iso CD Install image for Dapper with new Kernel. Does anyone how could I do it?
I've searched a lot of document, but I haven't found any howto explaing update kernel in cd image. 

I want to do it because de new production server has a diferent scsi raid board and the driver of this board is on new kernel 2.6.20. The Ubuntu Feisty release was installed without problem, but I wouldn't like to use it in production environment.You need to remaster the CD.

Try [reconstructor.]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1")

kagashe

---

