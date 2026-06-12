---
title: "Installing acroread."
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by davoudi on 2012-04-02
Hi everybody,

 I just recently tried to install acrobat read but I am facing the following error message:> 
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 acroread : Depends: nspluginwrapper but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


Any help is highly appreciated.

---

### Post by raja.genupula on 2012-04-03
what you got after doing as 
```
sudo apt-get install -f
```

in your terminal

---

### Post by davoudi on 2012-04-03
This is what I get:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev libxrandr-dev libexpat1-dev libxdamage-dev
  libpthread-stubs0 libxfixes-dev libgl1-mesa-dev x11proto-xinerama-dev
  x11proto-render-dev libxi-dev libgcr-3-0 libpixman-1-dev libcryptui0a
  libfontconfig1-dev x11proto-kb-dev x11proto-randr-dev libxinerama-dev
  libedata-cal-1.2-11 mesa-common-dev xtrans-dev libatk1.0-dev
  libedata-book-1.2-9 libgdk-pixbuf2.0-dev x11proto-input-dev
  x11proto-fixes-dev libcairo-script-interpreter2 libgtkglext1-dev
  libglu1-mesa-dev libdrm-dev x11proto-xext-dev libxt-dev libxmu-dev
  libxext-dev x11proto-damage-dev libglib2.0-dev lesstif2 libxcb-shm0-dev
  libcairo2-dev libpango1.0-dev libxau-dev libpng12-0:i386 libxcomposite-dev
  libxcb-render0-dev libxmu-headers libxrender-dev xorg-sgml-doctools
  libxft-dev libx11-dev x11proto-composite-dev libkms1 libxcb1-dev
  libgtk2.0-dev x11proto-core-dev libxdmcp-dev libpthread-stubs0-dev
  libxcursor-dev libssl1.0.0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


So apparently there is no broken package.

---

### Post by Lars Noodén on 2012-04-03
Have you tried Okular or Evince?  They are much better than Acroread so if there's not a special reason why you have to use specificially Acroread, you might try one of the better options.

---

### Post by davoudi on 2012-04-03
> **Lars Noodén said:**
> Have you tried Okular or Evince?  They are much better than Acroread so if there's not a special reason why you have to use specificially Acroread, you might try one of the better options.
I use the and they very good. They just don't completely handle and show comments and changes made with acrobat writer.

---

### Post by davoudi on 2012-04-03
Okular does show the edited file completely. Thanks.

---

