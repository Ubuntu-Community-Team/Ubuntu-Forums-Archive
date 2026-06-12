---
title: "sun-java5-doc errors"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by jpl80 on 2008-07-04
Getting a weird error for the last month. Every update seems to be dependent on sun-java5-doc:

```

Setting up sun-java5-doc (1.5.0-15-0ubuntu1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/j2se/1.5.0/download.html

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

```

This is starting to cause problems with my display and synaptic.

---

### Post by Partyboi2 on 2008-07-04
If you are wanting to remove or abort sun java development documentation from your system you can open a terminal (Applications>Accessories>Terminal)
```
sudo apt-get remove --purge sun-java5-doc
```
If you are still wanting to install  the sun java development documentation then
Go [[COLOR=Blue]here[/COLOR]]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter;pgid=yYdgaHqkkjVSR0EUPIQsoQ3D0000_2cK-xyD;sid=Ata8YrffRuS8YP-x3-_0Z1h3IJwsvHqaVzRzo6rBWoiwVQ==") and download the file to your Desktop. Once it is downloaded move it to /tmp
```
cd ~/Desktop
```
```
mv GDM-SharpGDM.tar.gz /tmp
```
change permissions
```
sudo chown root:root jdk-1_5_0-doc.zip
```
then install
```
 sudo apt-get install sun-java5-doc
```

---

