---
title: "Next update to Wireshark package for Ubuntu?"
date: 2014-07-21
forum: Installation &amp; Upgrades
---

### Post by mrjadeo on 2014-07-21
Hi all

I run Ubuntu 14.0.4 and came across a bug in Wireshark that has apparently been fixed in Wireshark 1.10.8+.
The latest version for Ubuntu is 1.10.6, in Debian (Jessie & Sid) it's 1.10.8-1.

Does anyone know (or can tell me how to find out) when this package will be brought into line with Debian?
Should I register my "interest" in getting this updated somewhere?

For the moment I guess I will have to install from source, or not use the broken feature.

Thanks!

James

---

### Post by monkeybrain20122 on 2014-07-21
The .debs are here [https://launchpad.net/ubuntu/+source/wireshark/1.10.8-1/+build/6108373](https://launchpad.net/ubuntu/+source/wireshark/1.10.8-1/+build/6108373)
However some dependencies are not satisfied. I think you can get those in 14.10's archives as well but I don't have time to hunt them down and mess with them. If you figure it out post back please.

---

### Post by grahammechanical on 2014-07-21
The Utopic Unicorn Software Centre has Wireshark 1.10.7-4

It is possible that this upgraded version will come with the release of 14.04.1 on July 24th.

Regards.

---

### Post by monkeybrain20122 on 2014-07-21
Well it turns out to be very easy to compilefrom source (I was expecting some dependency issues, but the dependency problems apparently only arise with debian's build)

```
sudo apt-get build-dep wireshark 
sudo apt-get install checkinstall

```
Down load the source code tar ball from [http://www.wireshark.org/download.html](http://www.wireshark.org/download.html)
untar, cd into the source folder (say ~/Downloads/wireshark-1.10.8)
```

cd Downloads/wireshark-1.10.8
./configure --prefix=/usr
make -j4
sudo checkinstall

```

That's it. "make -j4" uses 4 threads, change "4" to the number of threads you use
checkinstall would prompt you for different info, just follow the steps, in the end it will create a .deb file and install it. You can remove it from the package manager (e.g synaptic) if need to.

wireshark installed this way has no .desktop file, you have to start it from the terminal by typing "wireshark" (without quotations) I haven't checked if everything works yet, I have only done the installation and have started successfully.

---

### Post by mrjadeo on 2014-07-22
Thanks Monkeybrain!

I've been offline for a bit, but  installed the 14.10 proposed package (with broken dependencies) and my problem (starting flow graphs causes Wireshark to exit)  disappeared.
I uninstalled it again though, because otherwise apt complains and it's not the right solution.

I'll have a go at installing from source "soon".

---

