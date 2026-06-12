---
title: "does nvidia driver 173 work in karmic amd64?"
date: 2009-08-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bluesscream on 2009-08-23
I have an old passive cooled fx5200 and since I'm no hc-gamer and it does it's job noiseless I'd like to use it further in karmic. Does anybody know if there is a driver of the nvidia 173 series which works in ubuntu 9.10 amd64?
best regards Gerhard

---

### Post by randywilharm on 2009-08-23
This will lead you to the Nvidia driver page:

[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

If you don't get a better answer from someone else, this may help.

---

### Post by bluesscream on 2009-08-23
tx, i know this page well and didn't find anything to this theme in their forums. I'll wait some days and if I don't get any concretes I'll try it myself in a virginized partition.

---

### Post by cyberkilla on 2009-08-24
No, it doesn't work at the moment.

That's what everybody has been telling me. 173 won't compile on this kernel yet. They said it would be rectified; that's all I know.

I'm no authority on the subject.

---

### Post by dinxter on 2009-08-24
have a look at 
[http://ubuntuforums.org/showthread.php?t=1244488](http://ubuntuforums.org/showthread.php?t=1244488)
and 
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/398893](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/398893)
to get 173 support working

---

### Post by bluesscream on 2009-08-29
download last driver [http://www.nvidia.de/object/linux_display_amd64_173.14.20_de.html]("http://www.nvidia.de/object/linux_display_amd64_173.14.20_de.html")
remove nvidia 173.14.16 using synaptic
delete /etc/X11/xorg.conf
reboot into recovery mode, open a root-shell
```
cd /"where the driver is"
```
```
NVIDIA-Linux-x86_64-173.14.20-pkg2.run

```
follow the instructions.
I don't know how to make this a part of automatic dkms, so maybe I'll have to reinstall after each kernel update - but that's easy because the commands now are in the root terminal memory

!This does not work with kernel 2.6.31-3-rt!

---

