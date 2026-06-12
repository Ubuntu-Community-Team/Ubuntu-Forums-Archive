---
title: "quick fix for dell 1390 / bcm43xx users"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by syadnom on 2006-06-03
here is the temporary solution to the bcm43xx problem.

i had a tough time getting this solution so i thought id pass it on

first, blacklist the bcm43xx module
```
echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
```

next. download the newest ndiswrapper
[from here-sourceforge]("http://sourceforge.net/projects/ndiswrapper/")

remember to remove the original ndiswrapper
```
sudo aptitude remove ndiswrapper-utils
```

now untar
```
tar zxvf ndis*.tar.tz
```
cd into that directory and do a 
```
make install
```

now find your bcmwl5 driver.  ill let you find this.  maybe in windows/system32/drivers or maybe windows/system32/ReinstallBackups/0012/DriverFiles, or maybe you need to download it.

now 
```
ndiswrapper -i /path/to/bcmwl5.inf
modprobe ndiswrapper

```
now you should be able to configure it through System->Admin->Networking

good luck.

additionally, i did do a 
```
ifconfig wlan0 up
iwconfig wlan0 essid *networkname*
dhclient wlan0
```

but the gui should work well also.

---

### Post by robgue on 2006-06-03
this guide isn't working for me. not sure if it's specific to me but i get fro the 1st step:bash: /etc/modprobe.d/blacklist: Permission denied

then for your command:tar zxvf ndis*.tar.tz
should be:tar zxvf ndis*.tar.gz

i also get this error after i cd into the ndiswrapper dir and make install:
roberto@roberto-laptop:~/ndiswrapper-1.17rc2$ make install make -C driver install
make[1]: Entering directory `/home/roberto/ndiswrapper-1.17rc2/driver'
Can't find kernel build files in /lib/modules/2.6.15-23-686/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/roberto/ndiswrapper-1.17rc2/driver'
make: *** [install] Error 2


those were my results at least. i appreciate your guide though as i can't quite figure it out myself right now. am i doing something wrong? any help would be appreciated. thanks

---

### Post by syadnom on 2006-06-20
ok, just put 'sudo' in front of the commands to get root access so you can write the files.

then get the kernel headers for your running kernel

apt-get install linux-headers-*your arch*

run
uname -r
and you can see if you have a 686 or 386 or k6 etc kernel and use that


> **robgue]this guide isn't working for me. not sure if it's specific to me but i get fro the 1st step:bash: /etc/modprobe.d/blacklist: Permission denied

then for your command:tar zxvf ndis*.tar.tz
should be:tar zxvf ndis*.tar.gz

i also get this error after i cd into the ndiswrapper dir and make install:
roberto@roberto-laptop:~/ndiswrapper-1.17rc2$ make install make -C driver install
make[1]: Entering directory `/home/roberto/ndiswrapper-1.17rc2/driver'
Can't find kernel build files in /lib/modules/2.6.15-23-686/build said:**
> : *** [prereq_check] Error 1
make[1]: Leaving directory `/home/roberto/ndiswrapper-1.17rc2/driver'
make: *** [install] Error 2


those were my results at least. i appreciate your guide though as i can't quite figure it out myself right now. am i doing something wrong? any help would be appreciated. thanks

---

### Post by discord on 2006-07-07
thanks syadnom,

I also tried the bcm43xx driver but didnt have any luck. If you are able to get network-manager working with the ndiswrapper let me know.

---

### Post by discord on 2006-07-24
For some reason network-manager is having trouble setting the ssid. I might try to file a bug report.

---

