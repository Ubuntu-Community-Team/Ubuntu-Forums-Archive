---
title: "Country Flags could not be shown properly in amule and deluge"
date: 2008-07-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by 3togo on 2008-07-01
Country Flags could not be shown properly in amule and deluge. Both programs use 
geoip.dat which is included in libgeoip1 to determine the country flag based on IP. However, the geoip.dat is very outdated and seemingly never updated.

Below is how I update it manually. I wonder is there any chance that Intrepid will update it automatically for us.

1.  [http://www.maxmind.com/download/geoip/database/GeoLiteCity.dat.gz](http://www.maxmind.com/download/geoip/database/GeoLiteCity.dat.gz)
2.  gunzip GeoLiteCity.dat.gz
3.  sudo cp GeoLiteCity.dat /usr/share/GeoIP/GeoIP.dat

---

### Post by smbm on 2008-07-01
You should probably file a bug against libgeoip1 in Launchpad.

---

