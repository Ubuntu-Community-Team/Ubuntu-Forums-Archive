---
title: "Unity UI"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by TuskBilly on 2011-06-10
I have installed Ubuntu 11.04 on a Win7 Virtual PC. I gave it 1.5GB memory and 16GB disk. The underlying hardware is a Dell E6520 w/4GB, 64 bit Win7 Enterprise. On first boot of the VM after install I received the message: "It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment."
 
 

Couple of questions:
[LIST]
[*]What hardware could I be missing?
[*]How do I tell if I'm running the Unity UI vs. the Classic UI? (I'm new to the Linux community....)
[/LIST]Thanks

---

### Post by sikander3786 on 2011-06-10
Unity needs 3D supported graphic card and most of the Virtual Machine software don't support those. The latest that supports Unity is VirtualBox 4.

[http://www.virtualbox.org](http://www.virtualbox.org)

You'll need to install guest additions as well as enable 3D for the guest OS before you can see Unity.

And the most easily spotted difference between Unity and Classic Gnome is that Unity has got a top panel and a side panel (on the left) whereas Classic has got one at the top and one at the bottom.

Feel free to ask if you need instructions on VirtualBox configuration.

---

### Post by Purplerob on 2011-06-10
Unity is just ubuntu's new UI/shell. You can't get it because you are running ubuntu in a virtual machine and the default unity needs graphics. Unity has a launcher on the side and a panel with global menu on top. The ubuntu classic (which is the default gnome 2) just has two panels top and bottom the you can configure and move around. YOu can get unity 2d to work by installing it from the ubuntu software centre and choosing it before you login in.

---

### Post by TuskBilly on 2011-06-10
Thanks! I have learned something, therefore it has been a good day...

---

### Post by thepocketdrummer on 2011-06-10
I just installed ubuntu via VirtualBox and I'm already having problems. I tried to update and it only allowed me to do a "partial update". Then, after it finished, I was presenting with the following problem...

[IMG]http://img.photobucket.com/albums/v209/SpikeyHead00/VirtualCrap.png[/IMG]

Does anyone know how to fix it? I've tried doing the dist-upgrade and apt-get update a few times, but I have no idea what I'm doing, so it obviously didn't fix the problem.

---

### Post by wildmanne39 on 2011-06-10
> **thepocketdrummer said:**
> I just installed ubuntu via VirtualBox and I'm already having problems. I tried to update and it only allowed me to do a "partial update". Then, after it finished, I was presenting with the following problem...

[IMG]http://img.photobucket.com/albums/v209/SpikeyHead00/VirtualCrap.png[/IMG]

Does anyone know how to fix it? I've tried doing the dist-upgrade and apt-get update a few times, but I have no idea what I'm doing, so it obviously didn't fix the problem.Hi, a partial upgrade is almost always a bad idea. Have installed guess additions? Also you can try this to fix the upgrade issue.
```
sudo rm /var/lib/apt/lists/partial/*
```
```
sudo apt-get update

```

---

### Post by thepocketdrummer on 2011-06-11
> **wildmanne39 said:**
> Hi, a partial upgrade is almost always a bad idea. Have installed guess additions? Also you can try this to fix the upgrade issue.
```
sudo rm /var/lib/apt/lists/partial/*
```
```
sudo apt-get update

```

Tried sudo rm /var/lib/apt/lists/partial/* but it said "No such file or directory"

---

### Post by thepocketdrummer on 2011-06-13
does anyone know how to fix this?

---

