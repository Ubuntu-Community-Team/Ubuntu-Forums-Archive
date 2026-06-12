---
title: "Installing Softwares offline"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by possible181 on 2010-02-01
Hi Guys,
How can i download software and then install then offline because my internet is MAN (windows VPN). How can download the vpn client from an internet-enabled pc and then install it to my No-Internet PC having Ubuntu?

---

### Post by gnack on 2010-02-01
There might be a more graceful way to do this (I'm searching now), but a quick and dirty way is to download the packages from packages.ubuntu.com (i.e. deb files like "abiword-common_2.6.8-5ubuntu2_all.deb"), copy these files to the no-internet PC, and install them with:

$ dpkg -i something.deb

Be sure to download dependent packages as well.

---

### Post by possible181 on 2010-02-01
That's what making me worried! i keep digging and digging into dependencies of each package.

Isn't there a solution from ubuntu which ask or inform me to download all required files?

I have plan to switch completely to Ubuntu but if this remains the case then Ubuntu is disappointing me. and i am in love with Ubuntu now!

Please help!

---

### Post by mac9416 on 2010-02-02
Howdy, possible181,

> i keep digging and digging into dependencies of each package.

You should take a look at [Keryx]("http://keryxproject.org"). Keryx works much like Synaptic, but you can install packages for an offline machine from any online computer. It runs in Windows and Linux.

Let me know how that works!

---

### Post by possible181 on 2010-02-08
im doing jst fine mac!
u r a life saver!
im jst trying it.

let u know, ok.
yea thats should be a myth by now! 
cheers

---

