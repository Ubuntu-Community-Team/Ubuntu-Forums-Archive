---
title: "automatic installation (PXE, preseed, Cfengine)"
date: 2004-11-10
forum: Installation &amp; Upgrades
---

### Post by arnhemcr on 2004-11-10
Folks

I look after around 300 workstations currently running Red Hat 9. I'm considering replacing with Ubuntu (I'm also considering Debian Testing). The Red Hat install is automated using Kickstart and Cfengine - boot from media, wait and hour, user logs in. To use Ubuntu I need the same level of automation.
                                                                                
As Ubuntu is based on Debian I thought their Automated Installation might do the trick
[http://d-i.alioth.debian.org/manual/en.i386/ch04s07.html#automatic-install](http://d-i.alioth.debian.org/manual/en.i386/ch04s07.html#automatic-install)
PXE booting Unbuntu works fine but the kernel doesn't seem to take any notice of the
preseed/url option that tells it where the file containing answers to the installation questions are.
So the install is interactive (:-( Give the same preseed/url option to a Debian kernel and it installs automatically.
                                                                                
So does Ubuntu support preseeded installation? If so, any idea where am I going wrong? If not, are there any plans to?
                                                                                
P.S. I've also tried setting DEBIAN_FRONTEND=noninteractive which breaks the installation completely (something about missing libnoninteractive)

---

### Post by arnhemcr on 2004-11-11
> So does Ubuntu support preseeded installation?

no! preseed/url is handled by stuff in the Linux RAM disk (initrd). Using initrd-util (from 
  [http://sial.org/howto/linux/initrd/](http://sial.org/howto/linux/initrd/)) I unpacked the Ubuntu 4.10 netboot initrd.gz and the Debian equivalent. The Debian version was full of preseed stuff (see below). Ubuntu wasn't.

find <Debian initrd.gz unpacked>/ -type f -exec grep -l 'preseed' {} \;
./bin/preseed_command
./lib/preseed/preseed.sh
./usr/lib/prebaseconfig.d/05preseed
./var/lib/dpkg/info/network-preseed.isinstallable
./var/lib/dpkg/info/network-preseed.templates
./var/lib/dpkg/info/network-preseed.postinst
./var/lib/dpkg/info/rootskel.templates
./var/lib/dpkg/status

It should be possible to create an Ubuntu initrd.gz containing the preseed support from Debian...

---

