---
title: "How to add iso to the synaptic"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by zvacet on 2008-04-03
I think this can be interesting and helpful to somebody,so I decide to write this little how to.First of all we need some tools to make this easier.You can use 

1.nautilus scripts for mount and umount iso which you can find [here](http://ubuntuforums.org/showthread.php?t=590005&highlight=iso)

2.gmountiso using [this](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html) guide.

After installing one of these tools type in terminal

```
sudo mkdir /media/iso
```

Now you can mount iso with tool of your choice.When iso is mounted type in terminal


```
sudo synaptic --add-cdrom /media/iso/
```


Your iso is added to synaptic.Enjoy.

EDIT: If you use gmountiso mountpoint doesn´t have to be /media/iso .You can for example make folder in your home directory and name it **mount**(or whatever you like).In that case command will be 

```
sudo synaptic --add-cdrom /home/username/mount
```

---

