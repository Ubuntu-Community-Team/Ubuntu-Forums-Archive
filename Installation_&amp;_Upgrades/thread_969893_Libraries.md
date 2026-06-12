---
title: "Libraries"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by DrSeptapus on 2008-11-03
Hey everybody, i am fairly new to this whole linux thing and am in need of some assistance. I have the new Ubuntu intrepid ibex. I have a Nomad Jukebox Zen Xtra and i want to upload my music from it to amarok. The problem is that my computer won't recognize it, it does not even acknowledge that there is a device connected. So after some googling i downloaded "libnjb-2.2.6" the description said it would allow amarok to recognize the nomad jukebox player. so i have this thing on my desktop... now what?

---

### Post by Partyboi2 on 2008-11-03
What is the file extension at the end of it eg .deb .tar.gz etc...

Edit:
You should be able to install it by searching synaptic (System>Admin>Synaptic Package Mananger) or open a terminal (Applications>Accessoires>Terminal)
and install with
```
sudo apt-get install libnjb5
```

---

### Post by DrSeptapus on 2008-11-03
it is a .tar.gz.

---

### Post by Partyboi2 on 2008-11-03
You would need to compile it from source. The easier way is to try installing the one in the ubuntu repos. See my Edit in above post.

---

