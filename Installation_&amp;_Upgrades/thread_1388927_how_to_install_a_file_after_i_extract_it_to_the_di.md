---
title: "how to install a file after i extract it to the directory i want"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by SGC622 on 2010-01-23
im trying to install a program called libdvdcss0.0.1, it was a tar,gz2 file and i already extracted it via terminal to /opt/ but now that its extracted, i read the install readme file and tried going by those directions. not working here is my results on that
> scott@Home:~$ cd /opt/libdvdcss-0.0.1/
scott@Home:/opt/libdvdcss-0.0.1$ /configure --help
bash: /configure: No such file or directory
scott@Home:/opt/libdvdcss-0.0.1$ configure --help
configure: command not found
scott@Home:/opt/libdvdcss-0.0.1$ make install
cd extras/libdvdcss && make install
make[1]: Entering directory `/opt/libdvdcss-0.0.1/extras/libdvdcss'
mkdir -p /videolan
m 644 videolan/dvdcss.h /videolan
make[1]: m: Command not found
make[1]: [install] Error 127 (ignored)
mkdir -p
mkdir: missing operand
Try `mkdir --help' for more information.
make[1]: *** [install] Error 1
make[1]: Leaving directory `/opt/libdvdcss-0.0.1/extras/libdvdcss'
make: *** [install] Error 2
scott@Home:/opt/libdvdcss-0.0.1$



i dont know if its something im doing wrong or what but everytime i try and install a file this way or by the programs readme file it always  goes wrong in someway shape or form. the only way i have installed a program successfully is through kpackagekit and i am desperately trying to learn terminal's language here, the only thing standing in my way from switching from windows to linux entirely is these damn problems, please help! thank you in advance

---

### Post by Leppie on 2010-01-23
to install dvd css, try this:
```
sudo apt-get install libdvdread4
sudo bash /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by SGC622 on 2010-01-23
thanks alot that worked awesome. if i can ask about the code you gave me, is that programs location already in source.list? is that why i could just do apt-get? how does that work?  like i mean whats to stop me from typing in say (for ex. only)  sudo apt-get install soandsoprogramthatiwant?

---

### Post by oldos2er on 2010-01-23
[https://help.ubuntu.com/9.10/add-applications/C/index.html](https://help.ubuntu.com/9.10/add-applications/C/index.html)

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by Leppie on 2010-01-24
> **SGC622 said:**
> like i mean whats to stop me from typing in say (for ex. only)  sudo apt-get install soandsoprogramthatiwant?
if you're looking for a program, use apt-cache to search:
```
apt-cache search soandsoprogramthatiwant
```
you don't need to be root to search the cache ;)

---

