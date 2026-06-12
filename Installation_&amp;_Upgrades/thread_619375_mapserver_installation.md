---
title: "mapserver installation"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by Andra on 2007-11-21
please, how to know if I have wms client, wfs client/server features when MapServer is installed using apt-get install? Or, if by default these faetures are disabled, how to enable them in the current installation?

---

### Post by Andra on 2007-11-22
something I have got:

$ /usr/lib/cgi-bin/mapserv -v

MapServer version 4.10.0 OUTPUT=GIF OUTPUT=PNG OUTPUT=JPEG OUTPUT=WBMP OUTPUT=SVG SUPPORTS=PROJ SUPPORTS=FREETYPE SUPPORTS=WMS_SERVER SUPPORTS=WMS_CLIENT SUPPORTS=WFS_SERVER SUPPORTS=WFS_CLIENT SUPPORTS=WCS_SERVER SUPPORTS=THREADS SUPPORTS=GEOS INPUT=EPPL7 INPUT=POSTGIS INPUT=OGR INPUT=GDAL INPUT=SHAPEFILE DEBUG=MSDEBUG

---

