---
title: "[SOLVED] Downloading and Installing"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by LonelyTraveler on 2008-09-05
Does using this command ```
wget http://www.kegel.com/wine/winetricks
```
download and install this program or do I have to do it manually after this action finish?

Thanks

---

### Post by iaculallad on 2008-09-05
> **LonelyTraveler said:**
> Does using this command ```
wget http://www.kegel.com/wine/winetricks
```
download and install this program or do I have to do it manually after this action finish?

Thanks

It only downloads the desired file. Installation would be done manually.

---

### Post by LonelyTraveler on 2008-09-05
Cool, thanks. how do I install a file like that though?

---

### Post by iaculallad on 2008-09-05
> **LonelyTraveler said:**
> Cool, thanks. how do I install a file like that though?

It's a script file. You can install/execute it by (Assuming you downloaded it in your Desktop):

-Change directory to your download location:
```
cd ~/Desktop
```
-Give the script an executable property:
```
chmod a+x winetricks
```
-Execute it
```
./winetricks
```

---

