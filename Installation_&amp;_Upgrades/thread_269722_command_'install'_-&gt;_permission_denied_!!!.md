---
title: "command 'install' -&gt; permission denied !!!"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by gletare on 2006-10-02
Hi,

I am trying to install matlab for linux and in the installation guide they say : 

> 
Run the MathWorks Installer appropriate for your platform.
  /cdrom/install* & (Sun and Linux platforms)


For ubuntu, I type the command
```

sudo /media/cdrom/install* &

```

And I get the message
> 
sudo: unable to execute /media/cdrom/install: Permission denied


Any idea ?

Thanks in advance

---

### Post by taurus on 2006-10-02
Look to see what's the permission for /media/cdrom/install!

```
ls -la /media/cdrom/install
```
Otherwise, copy it to somewhere and change the permission before you run it again...

```
mkdir ~/temp
cp /media/cdrom/install ~/temp
cd ~/temp
chmod 755 install
sudo ./install
```

---

