---
title: "No Unity UI and dpkg: error: parsing file '/var/lib/dpkg/status' error after upgrade"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by Mad-Halfling on 2012-10-19
Hi folks, ran my upgrade which did pop up a couple of errors (unfortunately, until I get a usable UI, I can't get to the record of them right now) and I now boot to a empty desktop with only my installed bottom bar (an extra I added to replace the missing task bar) and no sign of any Unity panels.

Running sudo apt-get update and sudo apt-get -f upgrade I get an error:-

dpkg: error: parsing file '/var/lib/dpkg/status' near line 2638 package 'skype':

 mixed non-coinstallable and coinstallable package instances present
E: Sub-process /usr/bin/dpkg returned an error code (2)

I've tried running apt-get clean first, and also resetting my sources.list file (per the sticky, on this forum area) and it still seems that the dpkg status file is screwed.  I can't atp-get remove skype, either.  I've tried copying the status-old file over, plus the /var/back/dpkg.status.0 file, and I've also unzipped the dpkg.status.1.gz and .1.gz files in there (which are pre the upgrade) and copying them in, but I still get this same error.  Is there a way I completely regenerate this file, as it seems to be at the root of the problem, and as I've had skype on there for ages I think all of the /var/backup files will have this same issue?

Any help would be extremely gratefully received as my system is completely fracked at the moment, and this is a real pain.
Thanks MH

---

### Post by Mad-Halfling on 2012-10-19
I had a few mins to look at this more closely and in there (I now understand/get the impression the status file seems to be a system created one, rather than a supplied one) was a Skype section for both 32 and 64 bit architecture, removing the 32 bit one generated a similar error for librtmp0 which again had both versions.  Doing the same for that now seems to have removed the errors and things are chugging away (wish I'd waited until I got home to run the apt-get -f upgrade though, haha/aaaaarrrrrggggh).  I'll report back once it's done and I've had time to look to see if it's fixed things, and what package desolation it's wreaked on the system (there were lots of removed packages, I just hope they were removed to be replaced).

---

### Post by broomie on 2012-10-20
I have exactly this problem too -pleae let me know if you fix it and what youremoved to do so.

thanks

Paul

---

### Post by francos3 on 2012-10-25
Same problem here, I am getting the same error but for a different package: 
dpkg: error: parsing file '/var/lib/dpkg/status' near line 8068 package 'cnijfilter-common

Also 9 packages are broken according to synaptic:
ia32-libs
kde-workspace-bin
libc6-dev
libc6-i386
libpoppler28
skype
texlive-base
texlive-binaries
wine1.5

The package manager can not do anything, it is completely stuck.  Any help would be greatly appreciated as I really like Ubuntu but this is quite a nasty bug!

---

### Post by francos3 on 2012-10-25
Hi, just a bit more info:

I edited manually the status file(/var/lib/dpkg/status) to remove the packages on which both the i386 and the amd64 architecture were both present. Do not forget to back up the file if you try this!  This worked great, for me the problem was the scangear packages (which are simply cannon drivers for their printers).  They were listed as both i386 and amd64. After this the installation removed lots of i386 packages and replaced them by their amd64 version.  I assume that this is a new feature of 12.10? I believe this is arguable because even though amd64 can be faster(and of course use more than 4GB memory per process) it also can require a considerable more amount of memory to run the same code using the same data.  Perhaps the user should decide which packages to have in 32 bits and which in 64 bits?

Anyway, sudo apt-get install -f "worked" after this.  After this I ran synaptic update and I get a request to run a partial upgrade.  When I do this I get the messsage: "An upgrade from 'quantal' to 'precise' is not supported with this tool."  

If you get the same problem run sudo apt-get upgrade, it did all the necessary updates (Downloaded 1.9Gb) and now it seems everything is OK, fingers crossed!

> **francos3 said:**
> Same problem here, I am getting the same error but for a different package: 
dpkg: error: parsing file '/var/lib/dpkg/status' near line 8068 package 'cnijfilter-common

Also 9 packages are broken according to synaptic:
ia32-libs
kde-workspace-bin
libc6-dev
libc6-i386
libpoppler28
skype
texlive-base
texlive-binaries
wine1.5

The package manager can not do anything, it is completely stuck.  Any help would be greatly appreciated as I really like Ubuntu but this is quite a nasty bug!

---

### Post by ph3arr3t on 2012-11-19
I also am having the same issue;
:confused::confused:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  caribou evolution-webcal fonts-horai-umefont frostwire-data gir1.2-folks-0.6 gir1.2-gee-1.0
  libalgorithm-c3-perl libapp-nopaste-perl libattica0.3 libb-hooks-endofscope-perl libboost-signals1.46.1
  libbrowser-open-perl libclass-autouse-perl libclass-c3-perl libclass-c3-xs-perl libclass-load-perl
  libclass-load-xs-perl libcss-minifier-xs-perl libdata-optlist-perl libdevel-globaldestruction-perl
  libdevel-partialdump-perl libeval-closure-perl libextutils-autoinstall-perl
  libgetopt-long-descriptive-perl libhtml-lint-perl libhtml-tidy-perl libjavascript-beautifier-perl
  libjavascript-minifier-xs-perl libje-perl libllvm3.0 libmath-basecnv-perl libmodule-runtime-perl
  libmoose-perl libmoosex-getopt-perl libmoosex-role-parameterized-perl libmro-compat-perl                    
  libnamespace-clean-perl libopal3.10.2 libpackage-deprecationmanager-perl libpackage-stash-perl              
  libpackage-stash-xs-perl libparams-classify-perl libparams-validate-perl libprefork-perl libpt2.10.2        
  libsub-exporter-perl libsub-identify-perl libsub-install-perl libtie-refhash-weak-perl                      
  libvariable-magic-perl libwebservice-validator-css-w3c-perl libwebservice-validator-html-w3c-perl
  libxml-tidy-perl libxml-xpath-perl nemo-data ttf-droid ttf-umefont wine-gecko1.4 winetricks
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  context gir1.2-dbusmenu-glib-0.4 jadetex libc-bin libc6 libc6-dbg libc6-i386 libdbusmenu-glib4 libice6
  luatex tex-common texlive texlive-bibtex-extra texlive-common texlive-doc-base texlive-extra-utils
  texlive-font-utils texlive-fonts-recommended texlive-fonts-recommended-doc texlive-generic-recommended
  texlive-latex-base texlive-latex-base-doc texlive-latex-extra texlive-latex-extra-doc
  texlive-latex-recommended texlive-latex-recommended-doc texlive-luatex texlive-math-extra texlive-metapost
  texlive-metapost-doc texlive-pictures texlive-pictures-doc texlive-pstricks texlive-pstricks-doc
  texlive-xetex tipa
Suggested packages:
  context-doc-nonfree texlive-doc-en purifyeps latexmk xindy dvidvi fragmaster latexdiff t1utils dot2tex
The following packages will be REMOVED:
  frostwire google-earth-stable ia32-libs playonlinux q4wine wine wine1.3 wine1.4 wine1.4-amd64
  wine1.4-common
The following packages will be upgraded:
  context gir1.2-dbusmenu-glib-0.4 jadetex libc-bin libc6 libc6-dbg libc6-i386 libdbusmenu-glib4 libice6
  luatex tex-common texlive texlive-bibtex-extra texlive-common texlive-doc-base texlive-extra-utils
  texlive-font-utils texlive-fonts-recommended texlive-fonts-recommended-doc texlive-generic-recommended
  texlive-latex-base texlive-latex-base-doc texlive-latex-extra texlive-latex-extra-doc
  texlive-latex-recommended texlive-latex-recommended-doc texlive-luatex texlive-math-extra texlive-metapost
  texlive-metapost-doc texlive-pictures texlive-pictures-doc texlive-pstricks texlive-pstricks-doc
  texlive-xetex tipa
36 upgraded, 0 newly installed, 10 to remove and 2409 not upgraded.
722 not fully installed or removed.

apt-get -f upgrade yielded:

2095 upgraded, 0 newly installed, 10 to remove and 350 not upgraded.
722 not fully installed or removed.
and unable to lock the directory.
:(:(
I was getting other errors, and copied the dpkg.backup files into dpkg to trry and reload the list. If I tried to manually edit the file to remove the issue with 'rar' then it stopped loading the file altogether.

---

### Post by ph3arr3t on 2012-11-19
I think I might have found a way to fix this error..
I ran apt-get -f install in terminal, got the error....
then opened synaptic and found the package that's giving the error, it's marked as due for update. I de-selected it. and any other errors. 
synaptic is now running the update as I type this, I will know after the reboot if this resolved the issue or not. if it does for me I will confirm it worked.

---

### Post by ph3arr3t on 2012-11-20
It did download the needed updates, and partially update.
 However it still halted at the same place ... line 42260 'rar'
:confused::confused:

---

