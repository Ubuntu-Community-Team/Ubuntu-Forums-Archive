---
title: "Errors during installation"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by coco779 on 2008-02-06
Hi
I get the following error messages during installation of new programs:

Setting up capplets-data (2.18.1-0ubuntu2.1) ...
/usr/share/gconf/schemas/apps_gnome_settings_daemon_screensaver.schemas:102: parser error : Premature end of data in tag long line 102
                <long>&#1575;&#1580;&#1585;&#1575;&#1740; &#1605;&#1581;&#1575;&#1601;&#1592; &#1589;&#1601;&#1581;&#1607;*&#1606;&#1605;&#1575;
                                                             ^
/usr/share/gconf/schemas/apps_gnome_settings_daemon_screensaver.schemas:102: parser error : Premature end of data in tag locale line 100
                <long>&#1575;&#1580;&#1585;&#1575;&#1740; &#1605;&#1581;&#1575;&#1601;&#1592; &#1589;&#1601;&#1581;&#1607;*&#1606;&#1605;&#1575;
                                                             ^
/usr/share/gconf/schemas/apps_gnome_settings_daemon_screensaver.schemas:102: parser error : Premature end of data in tag schema line 4
                <long>&#1575;&#1580;&#1585;&#1575;&#1740; &#1605;&#1581;&#1575;&#1601;&#1592; &#1589;&#1601;&#1581;&#1607;*&#1606;&#1605;&#1575;
                                                             ^
/usr/share/gconf/schemas/apps_gnome_settings_daemon_screensaver.schemas:102: parser error : Premature end of data in tag schemalist line 3
                <long>&#1575;&#1580;&#1585;&#1575;&#1740; &#1605;&#1581;&#1575;&#1601;&#1592; &#1589;&#1601;&#1581;&#1607;*&#1606;&#1605;&#1575;
                                                             ^
/usr/share/gconf/schemas/apps_gnome_settings_daemon_screensaver.schemas:102: parser error : Premature end of data in tag gconfschemafile line 2
                <long>&#1575;&#1580;&#1585;&#1575;&#1740; &#1605;&#1581;&#1575;&#1601;&#1592; &#1589;&#1601;&#1581;&#1607;*&#1606;&#1605;&#1575;
                                                             ^
Failed to open `/usr/share/gconf/schemas/apps_gnome_settings_daemon_screensaver.schemas': Input/output error
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.18); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.19); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
^[[A^[[A^[[A^[[AErrors were encountered while processing:
 capplets-data
 gnome-control-center
 gnome-panel
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please Help
COCO

---

### Post by zvacet on 2008-02-06
```
sudo apt-get install capplets-data gnome-control-center gnome-panel
```

---

### Post by coco779 on 2008-02-06
No luck....same error message pops out
I had even tried with the synaptic package manager but again no luck
Can anybody help, please?
cheers
COCO

---

### Post by zvacet on 2008-02-06
```
sudo dpkg --configure -a
```

or 

```
sudo apt-get -f install
```

---

### Post by coco779 on 2008-05-07
fixed it manually by removing caplett and reinstalling the older version 
thanks for the help
coco

---

