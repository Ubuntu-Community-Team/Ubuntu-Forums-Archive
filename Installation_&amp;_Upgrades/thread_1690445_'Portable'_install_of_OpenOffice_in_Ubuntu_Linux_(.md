---
title: "'Portable' install of OpenOffice in Ubuntu Linux (via .deb)"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by sdaau on 2011-02-18
Hi all, 

I have just installed LibreOffice via ppa on Lucid, and it automatically removes OpenOffice. As I also wanted an OpenOffice copy, I thought it would be nice if it is possible to install it in a 'portable' manner, i.e. in its own folder (so it doesn't conflict with LibreOffice in dpkg/apt-get/Synaptic). 

Well - actually, it is not that bad to do it at all - first, download your installation from [http://download.openoffice.org/other.html#tested-full](http://download.openoffice.org/other.html#tested-full) (I used Linux 32-bit Intel DEB), and unpack:

```

$ wget http://download.services.openoffice.org/files/stable/3.3.0/OOo_3.3.0_Linux_x86_install-deb_en-US.tar.gz
...
2011-02-18 18:33:10 (502 KB/s) - `OOo_3.3.0_Linux_x86_install-deb_en-US.tar.gz' saved [154223002/154223002]

$ tar xzvf OOo_3.3.0_Linux_x86_install-deb_en-US.tar.gz

```Go into the unpacked directory, then in DEBS dir, and create a temporary folder there: 
```

$ cd OOO330_m20_native_packed-1_en-US.9567/DEBS/
$ mkdir tmp

```Finally, 'loop' through all the *.deb files in the DEBS dir, and use 'dpkg -x' to unpack all of them in the temporary folder:
```

$ for ix in *.deb; do echo $ix; dpkg -x $ix tmp/ ; done
...

$ ls tmp/opt/openoffice.org
openoffice.org/  openoffice.org3/ 

```Finally, navigate to the 'openoffice.org3/program' directory (or fuller name, as per the process above, would be: **OOO330_m20_native_packed-1_en-US.9567/DEBS/tmp/opt/openoffice.org3/program**) in Nautilus, and double-click the '**soffice**' script icon there; at that point, I was asked for registration - and after that was finished, OpenOffice is working :) 

Finally, you can then move that opt folder (your portable binary folder, so to speak) to anywhere you please - and OpenOffice will still run OK: 
```

$ mv OOO330_m20_native_packed-1_en-US.9567/DEBS/tmp/opt /media/MYDRIVE/OOO-opt
$ /media/MYDRIVE/OOO-opt/openoffice.org3/program/soffice   # run the program 

```
Hope this helps someone, 
Cheers!

PS: If you need the icons, they are in a .deb in the 'desktop-integration' folder, in this case '**DEBS/desktop-integration/openoffice.org3.3-debian-menus_3.3-9556_all.deb**' - this .deb is not handled by the above procedure, so you'd have to unpack it separately; it unpacks as a 'data' folder with subdirs 'etc' and 'usr' subfolders, which you could then copy to the 'portable' folder, if you should so choose (and then point icon links in desktop launchers to that folder).

---

