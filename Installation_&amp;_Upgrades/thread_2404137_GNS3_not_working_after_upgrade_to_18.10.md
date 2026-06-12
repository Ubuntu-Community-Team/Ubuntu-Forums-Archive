---
title: "GNS3 not working after upgrade to 18.10"
date: 2018-10-20
forum: Installation &amp; Upgrades
---

### Post by kaustuv on 2018-10-20
I have just updated my OS to 18.10. When i tried to open GNS3 application it didn't open through GUI. When i tried with terminal it first shows[B] Can't import Qt modules, PyQt is probably not installed.
[/B]Then i tried [HTML]sudo apt-get install python3-pip python3-pyqt5 python3-pyqt5-dbg PyQt5.QtSvg[/HTML]
command found at [https://gns3.com/discussions/getting-gns4-1-4beta1-gui-runnin](https://gns3.com/discussions/getting-gns4-1-4beta1-gui-runnin)
This doesn't solve the problem.

After that i uninstall GNS3 and tried to reinstall it.
On official website GNS3 was only available for up to 18.04.


Do i need to re-install ubuntu 18.04 to use GNS3 or is there any way to make GNS3 work in ubuntu 18.10 ?

---

### Post by dino99 on 2018-10-20
ppa [https://launchpad.net/ubuntu/+ppas?name_filter=gns3](https://launchpad.net/ubuntu/+ppas?name_filter=gns3) is also limited to Bionic, and no snap package found too sadly.

So you might need a Bionic install to continue using gns3.  Problem is due to packages versions . If you know the working dependencies version into bionic, then maybe you can install them (no garanty, possible conflict)

[https://launchpad.net/ubuntu/+source/packagename](https://launchpad.net/ubuntu/+source/packagename)

---

### Post by jschurman on 2018-10-21
Hey kaustuv,  I was able to get GNS3 to install by dropping the -gui from the installation steps.

#sudo apt-get install gns3

*launch
#gns3

---

### Post by svanfridur on 2018-10-21
Hi,
I've updated (or I should say completly reinstall Ubuntu to new 18.10) too. And yes official repositories are empty yet for cosmic release.
We should wait a little bit or install gns from sources. GNS3 team has a very good guide here [https://docs.gns3.com/1QXVIihk7dsOL7Xr7Bmz4zRzTsJ02wklfImGuHwTlaA4/index.html#h.gxybzkr97f48](https://docs.gns3.com/1QXVIihk7dsOL7Xr7Bmz4zRzTsJ02wklfImGuHwTlaA4/index.html#h.gxybzkr97f48) which I was using past times on previous ubuntu versions.
Installing from sources is really easy but in future you will need to update app manually which of course a bit harder than run apt update/upgrade.
Maybe if they don't build GNS3 for new release I'll build by myself. :)

---

