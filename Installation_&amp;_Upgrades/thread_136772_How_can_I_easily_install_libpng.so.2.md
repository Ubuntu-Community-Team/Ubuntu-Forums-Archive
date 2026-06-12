---
title: "How can I easily install libpng.so.2 ??"
date: 2006-02-26
forum: Installation &amp; Upgrades
---

### Post by patrick295767 on 2006-02-26
How can I easily install libpng.so.2 ??
  
Thank you very much, 

Patrick

---

### Post by hw-tph on 2006-02-26
**sudo apt-get install libpng2** should do it.


Håkan

---

### Post by patrick295767 on 2006-02-27
Right ...I finally found it with google, page 15 maybe .... 

 Thank you very much for your help !! Nice Ubuntu Forum community !
  
So to install xvidcap ...by the way

 How to Install It xvidcap:
===========

(via script)
1/ First, download the file : xvidcap_1.1.3-1_i386.deb and copy it to /root

2/just run the following script:

```
#!/bin/bash
echo "  " >> /etc/apt/sources.list
echo "## libavcodec1 " >> /etc/apt/sources.list
echo "deb ftp://ftp.nerim.net/debian-marillat/ sarge main" >> /etc/apt/sources.list
apt-get update
##apt-get upgrade   # I consider you upgraded ur linux
apt-get -f -y install imagemagick
apt-get -f -y install libpng2
cd /root
dpkg -i xvidcap_1.1.3-1_i386.deb
echo "#!/bin/bash" > "/root/xvid.sh"
chmod +x /root/xvid.sh
chmod 777 /root/xvid.sh
echo "xvidcap --gui no --compress 9 --file ~/myvideo.mpeg --frames 0 --fps 10 --cap_geometry 1024x768+0+0" >> "/root/xvid.sh"
echo "if you wanna make a avi file of ur screen, run sh /root/xvid.sh" 
echo "u can move this little script, where you want & need"
echo "** Greetz' **"
```

Greetigns

---

### Post by cutOff on 2006-02-27
Thanks for the tips patrick! I've managed to record video of my desktop.

Thanks again.

---

