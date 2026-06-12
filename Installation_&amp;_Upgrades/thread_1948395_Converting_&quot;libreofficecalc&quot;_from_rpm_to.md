---
title: "Converting &quot;libreofficecalc&quot; from rpm to .deb"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by razedafear on 2012-03-28
Hi 

I am trying to install"libreofficecalc". I got a tar.gz file from here [http://www.libreoffice.org/download/](http://www.libreoffice.org/download/), When i extracted it, i has two folder viz readmes and RPMS (with whole bunch of .rpm packages.), under RPMS their is a sub folder named desktop integeration folder(again with 3 .rpm package) I know i can get them converted through alien but the question is which package do i have to convert. Do i need to convert them one buy one to .deb and if i do that, i think i would still need one single .deb installer package to install. I am using Ubuntu 10.04 amdx64
Attaching the screenshots. Please help

Thanks

---

### Post by zombifier25 on 2012-03-28
You can do that, but... isn't it easier to just download the .tar.gz which provides .deb?
FYI, you have to install ALL OF THOSE PACKAGES.

---

### Post by razedafear on 2012-03-28
> **zombifier25 said:**
> You can do that, but... isn't it easier to just download the .tar.gz which provides .deb?
FYI, you have to install ALL OF THOSE PACKAGES.
Do you have any link for a .tar.gz providing .deb,??? I could'nt find any.

---

### Post by razedafear on 2012-03-28
[http://packages.debian.org/sid/libreoffice-calc](http://packages.debian.org/sid/libreoffice-calc)
[http://packages.debian.org/search?keywords=libreoffice-calc](http://packages.debian.org/search?keywords=libreoffice-calc)

Got these, but which one to pick?

---

### Post by zombifier25 on 2012-03-28
[http://download.documentfoundation.org/libreoffice/stable/3.5.1/deb/x86/LibO_3.5.1_Linux_x86_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/stable/3.5.1/deb/x86/LibO_3.5.1_Linux_x86_install-deb_en-US.tar.gz)

---

### Post by razedafear on 2012-03-28
\m/ cheers mate..this should work. Thankssss

---

### Post by razedafear on 2012-03-28
> **zombifier25 said:**
> [http://download.documentfoundation.org/libreoffice/stable/3.5.1/deb/x86/LibO_3.5.1_Linux_x86_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/stable/3.5.1/deb/x86/LibO_3.5.1_Linux_x86_install-deb_en-US.tar.gz)
oops.. this gave an error for wrong architecture. mine is x64bit. this one is for x32, any links for x64bit.

---

### Post by cmcanulty on 2012-03-28
why not just use the software center?

---

### Post by razedafear on 2012-03-28
> **cmcanulty said:**
> why not just use the software center?
i cant find this in software center, nor in the synaptic manager..

---

### Post by spcwingo on 2012-03-28
> **razedafear said:**
> oops.. this gave an error for wrong architecture. mine is x64bit. this one is for x32, any links for x64bit.

[http://download.documentfoundation.org/libreoffice/stable/3.5.1/deb/x86_64/LibO-SDK_3.5_Linux_x86-64_install-deb_en-US.tar.gz]("http://download.documentfoundation.org/libreoffice/stable/3.5.1/deb/x86_64/LibO-SDK_3.5_Linux_x86-64_install-deb_en-US.tar.gz")

After extracting open a terminal and issue these commands:

```
cd /path/to/extracted/debs
```

replacing "path/to/extracted/debs" with the actual path to that folder containing the debs.

```
sudo dpkg -i ./*.deb
```

```
cd desktop-integration
```

```
sudo dpkg -i ./*.deb
```

---

### Post by spcwingo on 2012-03-28
Oh, you can also use the tuxfamily repository.  If you would rather do that follow the instructions below:

```
echo 'deb http://download.tuxfamily.org/gericom/libreoffice /' | sudo tee -a /etc/apt/sources.list && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 890E7A26 && sudo apt-get update
```

You should now be able to find the latest LibreOffice in the software center or synaptic.  :)

EDIT: Scratch that, I just noticed that the repo above only contains i386 debs.  :(

---

### Post by rewyllys on 2012-03-28
I suggest a direct approach, viz., going to the following URL:

[http://www.libreoffice.org/download/?type=deb-x86_64]("http://www.libreoffice.org/download/?type=deb-x86_64")

---

### Post by razedafear on 2012-03-29
> **spcwingo said:**
> [http://download.documentfoundation.org/libreoffice/stable/3.5.1/deb/x86_64/LibO-SDK_3.5_Linux_x86-64_install-deb_en-US.tar.gz]("http://download.documentfoundation.org/libreoffice/stable/3.5.1/deb/x86_64/LibO-SDK_3.5_Linux_x86-64_install-deb_en-US.tar.gz")

After extracting open a terminal and issue these commands:

```
cd /path/to/extracted/debs
```

replacing "path/to/extracted/debs" with the actual path to that folder containing the debs.

```
sudo dpkg -i ./*.deb
```

```
cd desktop-integration
```

```
sudo dpkg -i ./*.deb
```


I think the issue is with the architecture, It will not allow a x86 package on x64 for some reasons. Check this output from dpkg -i 

```
dpkg: error processing ./libobasis3.5-base_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-binfilter_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-calc_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-core01_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-core02_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-core03_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-core04_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-core05_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-core06_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-core07_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-draw_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-en-us_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-en-us-base_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-en-us-calc_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-en-us-math_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-en-us-res_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-en-us-writer_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-extension-beanshell-script-provider_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-extension-javascript-script-provider_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-extension-mediawiki-publisher_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-extension-nlpsolver_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-extension-pdf-import_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-extension-presentation-minimizer_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-extension-presenter-screen_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-extension-python-script-provider_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-extension-report-builder_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-gnome-integration_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-graphicfilter_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-images_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-impress_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-javafilter_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-kde-integration_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-math_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-ogltrans_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-onlineupdate_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-ooofonts_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-ooolinguistic_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-postgresql-sdbc_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-pyuno_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-writer_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libobasis3.5-xsltfilter_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libreoffice3.5_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libreoffice3.5-base_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libreoffice3.5-calc_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libreoffice3.5-dict-en_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libreoffice3.5-dict-es_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libreoffice3.5-dict-fr_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libreoffice3.5-draw_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libreoffice3.5-en-us_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libreoffice3.5-impress_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ./libreoffice3.5-math_3.5.1-102_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: too many errors, stopping
Errors were encountered while processing:
 ./libobasis3.5-base_3.5.1-102_i386.deb
 ./libobasis3.5-binfilter_3.5.1-102_i386.deb
 ./libobasis3.5-calc_3.5.1-102_i386.deb
 ./libobasis3.5-core01_3.5.1-102_i386.deb
 ./libobasis3.5-core02_3.5.1-102_i386.deb
 ./libobasis3.5-core03_3.5.1-102_i386.deb
 ./libobasis3.5-core04_3.5.1-102_i386.deb
 ./libobasis3.5-core05_3.5.1-102_i386.deb
 ./libobasis3.5-core06_3.5.1-102_i386.deb
 ./libobasis3.5-core07_3.5.1-102_i386.deb
 ./libobasis3.5-draw_3.5.1-102_i386.deb
 ./libobasis3.5-en-us_3.5.1-102_i386.deb
 ./libobasis3.5-en-us-base_3.5.1-102_i386.deb
 ./libobasis3.5-en-us-calc_3.5.1-102_i386.deb
 ./libobasis3.5-en-us-math_3.5.1-102_i386.deb
 ./libobasis3.5-en-us-res_3.5.1-102_i386.deb
 ./libobasis3.5-en-us-writer_3.5.1-102_i386.deb
 ./libobasis3.5-extension-beanshell-script-provider_3.5.1-102_i386.deb
 ./libobasis3.5-extension-javascript-script-provider_3.5.1-102_i386.deb
 ./libobasis3.5-extension-mediawiki-publisher_3.5.1-102_i386.deb
 ./libobasis3.5-extension-nlpsolver_3.5.1-102_i386.deb
 ./libobasis3.5-extension-pdf-import_3.5.1-102_i386.deb
 ./libobasis3.5-extension-presentation-minimizer_3.5.1-102_i386.deb
 ./libobasis3.5-extension-presenter-screen_3.5.1-102_i386.deb
 ./libobasis3.5-extension-python-script-provider_3.5.1-102_i386.deb
 ./libobasis3.5-extension-report-builder_3.5.1-102_i386.deb
 ./libobasis3.5-gnome-integration_3.5.1-102_i386.deb
 ./libobasis3.5-graphicfilter_3.5.1-102_i386.deb
 ./libobasis3.5-images_3.5.1-102_i386.deb
 ./libobasis3.5-impress_3.5.1-102_i386.deb
 ./libobasis3.5-javafilter_3.5.1-102_i386.deb
 ./libobasis3.5-kde-integration_3.5.1-102_i386.deb
 ./libobasis3.5-math_3.5.1-102_i386.deb
 ./libobasis3.5-ogltrans_3.5.1-102_i386.deb
 ./libobasis3.5-onlineupdate_3.5.1-102_i386.deb
 ./libobasis3.5-ooofonts_3.5.1-102_i386.deb
 ./libobasis3.5-ooolinguistic_3.5.1-102_i386.deb
 ./libobasis3.5-postgresql-sdbc_3.5.1-102_i386.deb
 ./libobasis3.5-pyuno_3.5.1-102_i386.deb
 ./libobasis3.5-writer_3.5.1-102_i386.deb
 ./libobasis3.5-xsltfilter_3.5.1-102_i386.deb
 ./libreoffice3.5_3.5.1-102_i386.deb
 ./libreoffice3.5-base_3.5.1-102_i386.deb
 ./libreoffice3.5-calc_3.5.1-102_i386.deb
 ./libreoffice3.5-dict-en_3.5.1-102_i386.deb
 ./libreoffice3.5-dict-es_3.5.1-102_i386.deb
 ./libreoffice3.5-dict-fr_3.5.1-102_i386.deb
 ./libreoffice3.5-draw_3.5.1-102_i386.deb
 ./libreoffice3.5-en-us_3.5.1-102_i386.deb
 ./libreoffice3.5-impress_3.5.1-102_i386.deb
 ./libreoffice3.5-math_3.5.1-102_i386.deb
Processing was halted because there were too many errors.
```

---

### Post by razedafear on 2012-03-29
downloading this one  Linux - deb (x86_64), version 3.5.1, English (US)

Hope this has x64 .debs and not .rpm's

---

### Post by razedafear on 2012-03-29
> **razedafear said:**
> downloading this one  Linux - deb (x86_64), version 3.5.1, English (US)

Hope this has x64 .debs and not .rpm's
Thanks A ton guys..this worked... Thanks for the commands @spcwingo. 
SOLVED \m/

---

### Post by spcwingo on 2012-03-30
> **razedafear said:**
> Thanks A ton guys..this worked... Thanks for the commands @spcwingo. 
SOLVED \m/

I'm glad you got it going.  Have fun!  :)

---

