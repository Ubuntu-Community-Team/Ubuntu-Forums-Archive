---
title: "dpkg error using automatix"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by NirvanaRush2112 on 2006-12-30
dpkg error using automatix
well this just happend a couple of mins ago and i searched the forums and found this... sudo dpkg --configure -a .. then i did it but this is what i get...

matt@ubuntu:~$ sudo dpkg --configure -a
Setting up flashplugin-nonfree (9.0.21.78.2ubuntu1~dapper1) ...
Downloading...

then i leave it and it doesint do anything...ive had this problem getting flash and it's probly why i have the error...so what do i do to fix this error?

---

### Post by arnieboy on 2006-12-31
> **NirvanaRush2112 said:**
> dpkg error using automatix
well this just happend a couple of mins ago and i searched the forums and found this... sudo dpkg --configure -a .. then i did it but this is what i get...

matt@ubuntu:~$ sudo dpkg --configure -a
Setting up flashplugin-nonfree (9.0.21.78.2ubuntu1~dapper1) ...
Downloading...

then i leave it and it doesint do anything...ive had this problem getting flash and it's probly why i have the error...so what do i do to fix this error?

try
```
sudo apt-get -f install
```

---

