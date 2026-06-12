---
title: "Installing adobe-flashplugin with Synaptic Package Manager"
date: 2012-09-20
forum: Installation &amp; Upgrades
---

### Post by unckybob on 2012-09-20
Pandora won't work on my computer.

I have installed "adobe-flashplugin" version 11 with Synaptic Package Manager. Under "Installed Version" it says "11.2.202.238-0natty1". But in the "Add-ons Manager" in Firefox it says I have "Shockwave Flash 10.1 r999 the GNU SWF Player" player installed.

Can someone please tell me how to get it working with Synaptic?

---

### Post by GeForce 9500GT on 2012-09-21
For Flash support it is best to install the ubuntu-restricted-esxtras package since this package contains a Flash plugin as well. [Adobe abandoned Flash on Linux]("http://www.omgubuntu.co.uk/2012/02/adobe-adandons-flash-on-linux"), so no future updates will be available for Flash for Linux, just security patches. 
 
And check if you have **swfdec** and **gnash** installed. These 2 packages might interfere with Adobe Flash Player.

---

