---
title: "LanguageTool on LibreOffice installing error"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by Davh on 2011-10-17
I'm ussing LibreOffice on Ubuntu Oneiric 11.10

When I try to add the LanguageTool extension, I get this error:

"an error ocurred writing or reading from a file"

Please if any one can help me?

I'm trying to add the spanish spellchecker.

Greetings.

---

### Post by leeconne on 2011-10-20
Hi. I have the same problem. I am going to file a bug report. The ubuntu packaged libreoffice is incompatible with many libreoffice and openoffice extensions (v. 2.4.3). 

One can install the libreoffice packages from libreoffice.com

download the debs. not the rpms which are automatically "detected."
choose the right architecture.

go into the libreoffice folder
and click copy on the DEBS folder
open a terminal
paste it and remove the file://

you should have /home in terminal and then the rest of the subfolders to the DEBS folder

while cd'd in the folder do

sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i *.deb

to fix theming for kde 

cd /opt/libreoffice3.4/basis-link/ure-link/lib

sudo mv libstdc++.so.6 libstdc++.so.6.orig
sudo ln -s  /usr/lib/libstdc++.so.6.0.9 libstdc++.so.6

The non-ubuntu packages of libreoffice for 3.4.3 are incompatible with the latest unity integration.

LanguageTool should work with the packages from libreoffice.com (3.4.3).

Off to file a bug report.

---

