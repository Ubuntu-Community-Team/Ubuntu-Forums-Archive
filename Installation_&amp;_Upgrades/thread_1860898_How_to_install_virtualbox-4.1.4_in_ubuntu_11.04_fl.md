---
title: "How to install virtualbox-4.1.4 in ubuntu 11.04 fluently?"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by william2011 on 2011-10-15
How to install virtualbox-4.1.4 in ubuntu 11.04 fluently?

  when apt-get install libqt* unmet dependency. there is a long list of unmet dependency. Where start first and any command to install virtualbox fluently?

You might want to run 'apt-get -f install' to correct these: The following packages have unmet dependencies:  virtualbox-4.1 : Depends: libcurl3 (>= 7.16.2-1) but it is not going to be installed                   Depends: libqt4-network (>= 4:4.5.3) but it is not going to be installed                   Depends: libqt4-opengl (>= 4:4.7.0~rc1) but it is not going to be installed                   Depends: libqtcore4 (>= 4:4.7.0~beta1) but it is not going to be installed                   Depends: libqtgui4 (>= 4:4.7.0~beta1) but it is not going to be installed                   Recommends: libsdl-ttf2.0-0 but it is not going to be installed                   Recommends: dkms but it is not going to be installed                   Recommends: libhal1 (>= 0.5) but it is not going to be installed E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a sol

---

