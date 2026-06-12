---
title: "Install K3B in Hardy via other computer's internet connection."
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by jeremywitt on 2008-10-08
I want to install K3B on my laptop while I am at work. I am not allowed to connect the laptop to the network to gain internet access, but I have internet access on my work computer and I also have a USB memory stick (1GB).
Can I use the work computer to download a file (tar.gz?), transfer the file via USB stick and install from there?

I'm about 98% sure it's possible but I'm clueless on how to install from tar.gz and also where to get the file for K3B. Any help would be appreciated.

---

### Post by .nedberg on 2008-10-08
You can get the .deb here:
[http://packages.ubuntu.com/hardy/k3b](http://packages.ubuntu.com/hardy/k3b)

make sure you get the dependencies!

You might use apt-get with the -d option also, but I am not sure how that works.

---

### Post by jeremywitt on 2008-10-08
> **.nedberg said:**
> You can get the .deb here:
[http://packages.ubuntu.com/hardy/k3b](http://packages.ubuntu.com/hardy/k3b)

make sure you get the dependencies!

You might use apt-get with the -d option also, but I am not sure how that works.

Thanks for the info, but I don't know how to install via the .deb file.

Also, how can I obtain dependencies without linux connecting to the net? I guess I neglected to mention that my work computer runs WinXP (I figured that was a given) and as I stated before I can't connect my laptop to the internet directly.

---

### Post by .nedberg on 2008-10-08
The dependencies are listed on the page with a red "dot". Some are probably installed already. DL the ones you need

On your ubuntu machine open synaptic and mark k3b for installation, it will list what you need to get (even without network). DL these packages and install them with a doubleclick. You will have to install them one by one or with 'sudo dpkg -i <package.deb>'. Probably in the right order...

---

### Post by jeremywitt on 2008-10-08
I drove home for lunch and installed via synaptic... I don't know how to close/erase this thread, if someone could do it that would be great. Thanks!
Also, if you feel like letting me know how to do that myself, that would be appreciated too.

---

