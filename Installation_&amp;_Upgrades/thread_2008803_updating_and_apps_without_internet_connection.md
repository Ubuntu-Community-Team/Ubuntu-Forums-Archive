---
title: "updating and apps without internet connection"
date: 2012-06-23
forum: Installation &amp; Upgrades
---

### Post by sidewalkcynic on 2012-06-23
I came upon an old Dell tower with no wifi and I do not want to hook it up to the internet anyway.

But what I do want to do is install the 12.04 updates and some applications from synaptic, or however. I have a netbook with wifi and synaptic, and I downloaded the update packages only, but now I am stuck - I do not know where the packages are so I can save them to a USB and install them on the Dell tower. i thought when I selected the "download only" dialog it would allow me to choose where I wanted to put the packages, but it did not allow me to.

---

### Post by David Andersson on 2012-06-23
> **sidewalkcynic said:**
> 
i thought when I selected the "download only" dialog it would allow me to choose where I wanted to put the packages, but it did not allow me to.

It's so you can "apply" the updates later.

Normally .deb packages are stored in /var/cache/apt/archives
See if you find them there.

---

### Post by d.atanasov on 2012-06-23
Try for fast search in Terminal :

```
locate *.deb 
```

---

### Post by sidewalkcynic on 2012-06-23
> **David Andersson said:**
> It's so you can "apply" the updates later.

Normally .deb packages are stored in /var/cache/apt/archives
See if you find them there.

That looks like what I am looking for - I'll try it thanks.

So, how do I install them - debi package manager???

---

### Post by d.atanasov on 2012-06-23
> **sidewalkcynic said:**
> That looks like what I am looking for - I'll try it thanks.

So, how do I install them - debi package manager???

you just run in Terminal: 

```
sudo dpkg -i *.deb
``` 

In the folder/usb flash where all .deb files are.

---

### Post by David Andersson on 2012-06-23
> **d.atanasov said:**
> 
```
sudo dpkg -i *.deb
``` 


Or **double click** the .deb file with the mouse.

---

### Post by sidewalkcynic on 2012-06-23
> **d.atanasov said:**
> you just run in Terminal: 

```
sudo dpkg -i *.deb
``` 

In the folder/usb flash where all .deb files are.

That would be for when I install the packages on the isolated Dell tower - thanks.

---

