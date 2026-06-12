---
title: "Using Ubuntu to recover Windows Files"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by gross on 2008-12-02
I have a gateway laptop that will not boot. I was able to load ubuntu 6.10 from cd, but could not figure out how to access the windows drive. 

Is there a way to mount the windows drive using the 6.10 cd?

(Could not load 8.10, received an error message saying I needed a distro for i686) ( also could not download the 32-bit distro from the ubuntu.com, kept being canceled for some reason)

Thank you for any help.
Gross

---

### Post by taurus on 2008-12-02
You need to mount it first before you can access it.  Assuming your windows in on /dev/sda1, you could do something like

Applications -> Accessories -> Terminal
```
sudo mkdir /media/widows
sudo mount -t ntfs /dev/sda1 /media/windows
df -h
```

---

### Post by gross on 2008-12-02
[COLOR="PaleGreen"]> **taurus said:**
> You need to mount it first before you can access it.  Assuming your windows in on /dev/sda1, you could do something like

Applications -> Accessories -> Terminal
```
sudo mkdir /media/widows
sudo mount -t ntfs /dev/sda1 /media/windows
df -h
```[/COLOR]

Thank you for the reply. Sorry if this is a nub question but do I hit enter after each line or type in all the code then hit enter?

Thanks again for the help!
Gross

---

### Post by mdszepher on 2008-12-02
Run each line separately.

---

### Post by gross on 2008-12-03
Thanks again for the reply. This is all new and very exciting stuff.

Would the windows drive show up in COMPUTER if I mounted correctly? 

What I would like to do is access the windows files from Ubuntu and save them to a external drive, as the windows drive is corrupt and will not boot.

Only thing at this point that is showing up in COMPUTER is the cd drive and the Ubuntu files.

Thanks again for any help
Gross

---

