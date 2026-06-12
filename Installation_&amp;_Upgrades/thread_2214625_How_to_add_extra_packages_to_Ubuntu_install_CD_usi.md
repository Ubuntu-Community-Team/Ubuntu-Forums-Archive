---
title: "How to add extra packages to Ubuntu install CD using kickstart"
date: 2014-04-02
forum: Installation &amp; Upgrades
---

### Post by satheesh3 on 2014-04-02
Hai,
I used kickstart to automate Ubuntu12.04 alternate iso installation. I  am able to automate the installation. Now I want to install some extra  packages such as teamviewer during OS installation. But the problem is  that it cannot be installed online. I want to add these packages to  install CD and install those packages during installation itself.

  Does anyone know how to do this?Any help is appreciated.

Thank you

---

### Post by su:bhatta on 2014-04-02
Have a look here :
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

and maybe here: [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

---

### Post by satheesh3 on 2014-04-02
Hai,
Thank you for the reply.
But, I've already referred this link and was unable to find a solution for my problem.
My packages cannot be installed using apt-get(example:if I want to install Teamviewer, I've to download it manually and then install it using dpkg). I like to add the package to install CD (if possible) and install it during or after OS installation.

---

### Post by nachoarsuaga on 2014-10-24
Hi,

You can execute scripts after the installation on the "postinstall" section of the kickstart file:
[COLOR=#000000][FONT=Verdana]
%post[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]echo "Now performing post-KickStart installation tasks"
[/FONT][/COLOR]
Regards,

---

