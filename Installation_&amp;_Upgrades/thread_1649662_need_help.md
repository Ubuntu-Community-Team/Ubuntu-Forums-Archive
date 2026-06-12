---
title: "need help"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by ags84 on 2010-12-20
i am a newbie to ubuntu.

i was trying around with wine package. i guess i screwed it up. so now, i am not able to download/iinstall anything from software centre. it gives me following error
[B]
"E: tex-common: subprocess installed post-installation script returned error exit status 1
E: texlive-binaries: dependency problems - leaving unconfigured"[/B]

i am not sure what to do... pls help me to solve it...

thanks

---

### Post by Rubi1200 on 2010-12-20
Hi and welcome to the forums :)

Go to Applications > Accessories > Terminal

Run the following commands:

```
sudo apt-get install -f

sudo dpkg --configure -a
```

Post back if there are errors (with the error, of course)

Thanks.

---

### Post by ags84 on 2010-12-20
> **Rubi1200 said:**
> Hi and welcome to the forums :)

Go to Applications > Accessories > Terminal

Run the following commands:

```
sudo apt-get install -f

sudo dpkg --configure -a
```Post back if there are errors (with the error, of course)

Thanks.


thank u this is what i am getting after i entered those comands. i copied whole terminal for ur reference
```


adarsh@adarsh-desktop:~$ sudo apt-get install -f
[sudo] password for adarsh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsvga1 libggi-target-x libggi2 libgii1
  ttf-mscorefonts-installer libgii1-target-x cabextract
  libmpg123-0 winbind
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up tex-common (2.06) ...
Running mktexlsr. This may take some time... done.
No packages found matching texlive-base.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                Errors were encountered while processing:
 tex-common
 texlive-binaries
E: Sub-process /usr/bin/dpkg returned an error code (1)
adarsh@adarsh-desktop:~$ sudo dpkg --configure -a
Setting up tex-common (2.06) ...
Running mktexlsr. This may take some time... done.
No packages found matching texlive-base.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tex-common
 texlive-binaries
adarsh@adarsh-desktop:~$
```

Pls let me know what i have to do next

thanks

---

### Post by sikander3786 on 2010-12-20
Try,

```
sudo apt-get install texlive-base
```

```
sudo apt-get install --reinstall tex-common texlive-binaries
```

Keep on posting the outputs ;-)

Which version of Ubuntu is this? 10.04 or 10.10?

---

### Post by ags84 on 2010-12-20
> **sikander3786 said:**
> Try,

```
sudo apt-get install texlive-base
``````
sudo apt-get install --reinstall tex-common texlive-binaries
```Keep on posting the outputs ;-)

Which version of Ubuntu is this? 10.04 or 10.10?


i tried both comands. this is what appeared in terminal

```
adarsh@adarsh-desktop:~$ **sudo apt-get install texlive-base**
[sudo] password for adarsh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsvga1 libggi-target-x libggi2 libgii1
  ttf-mscorefonts-installer libgii1-target-x
  cabextract libmpg123-0 winbind
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  lmodern luatex texlive-common texlive-doc-base
  texlive-luatex
Suggested packages:
  perl-tk
The following NEW packages will be installed:
  lmodern luatex texlive-base texlive-common
  texlive-doc-base texlive-luatex
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 37.1MB of archives.
After this operation, 87.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://in.archive.ubuntu.com/ubuntu/ lucid/main lmodern 2.004.1-3 [17.8MB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ lucid/main luatex 0.50.0-1 [2,198kB]
Get:3 http://in.archive.ubuntu.com/ubuntu/ lucid/main texlive-common 2009-7 [99.0kB]
Get:4 http://in.archive.ubuntu.com/ubuntu/ lucid/main texlive-doc-base 2009-2 [1,339kB]
Get:5 http://in.archive.ubuntu.com/ubuntu/ lucid/main texlive-base 2009-7 [14.7MB]
Get:6 http://in.archive.ubuntu.com/ubuntu/ lucid/main texlive-luatex 2009-7 [984kB]
Fetched 37.1MB in 10min 14s (60.4kB/s)           
Selecting previously deselected package lmodern.
(Reading database ... 177133 files and directories currently installed.)
Unpacking lmodern (from .../lmodern_2.004.1-3_all.deb) ...
Selecting previously deselected package luatex.
Unpacking luatex (from .../luatex_0.50.0-1_i386.deb) ...
Selecting previously deselected package texlive-common.
Unpacking texlive-common (from .../texlive-common_2009-7_all.deb) ...
Selecting previously deselected package texlive-doc-base.
Unpacking texlive-doc-base (from .../texlive-doc-base_2009-2_all.deb) ...
Selecting previously deselected package texlive-base.
Unpacking texlive-base (from .../texlive-base_2009-7_all.deb) ...
Selecting previously deselected package texlive-luatex.
Unpacking texlive-luatex (from .../texlive-luatex_2009-7_all.deb) ...
Processing triggers for fontconfig ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for install-info ...
Setting up tex-common (2.06) ...
Running mktexlsr. This may take some time... done.
texlive-base is not ready, delaying updmap-sys call
texlive-base is not ready, skipping fmtutil-sys --all call

Setting up texlive-binaries (2009-5ubuntu0.2) ...
update-alternatives: using /usr/bin/xdvi-xaw to provide /usr/bin/xdvi.bin (xdvi.bin) in auto mode.
update-alternatives: using /usr/bin/bibtex.original to provide /usr/bin/bibtex (bibtex) in auto mode.
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Building format(s) --refresh.
    This may take some time... done.

Setting up lmodern (2.004.1-3) ...
Running mktexlsr. This may take some time... done.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
Updating fontconfig cache for /usr/share/texmf/fonts/type1/public/lm

Setting up luatex (0.50.0-1) ...
texlive-base is not ready, cannot create formats

Setting up texlive-common (2009-7) ...

Setting up texlive-doc-base (2009-2) ...

Processing triggers for tex-common ...
Running mktexlsr. This may take some time... done.
texlive-base is not ready, delaying updmap-sys call
Setting up texlive-base (2009-7) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-base.cnf.
    This may take some time... done.

Processing triggers for tex-common ...
Running updmap-sys. This may take some time... done.
Building formats --byhyphen /var/lib/texmf/tex/generic/config/language.def.
    This may take some time... done.
Setting up texlive-luatex (2009-7) ...

Processing triggers for tex-common ...
Running mktexlsr. This may take some time... done.
adarsh@adarsh-desktop:~$ **sudo apt-get install --reinstall tex-common texlive-binaries**
[sudo] password for adarsh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsvga1 libggi-target-x libggi2 libgii1
  ttf-mscorefonts-installer libgii1-target-x
  cabextract libmpg123-0 winbind
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/8,162kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 180415 files and directories currently installed.)
Preparing to replace tex-common 2.06 (using .../tex-common_2.06_all.deb) ...
Unpacking replacement tex-common ...
Preparing to replace texlive-binaries 2009-5ubuntu0.2 (using .../texlive-binaries_2009-5ubuntu0.2_i386.deb) ...
Unpacking replacement texlive-binaries ...
Processing triggers for doc-base ...
Processing 2 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up tex-common (2.06) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Building format(s) --all.
    This may take some time... done.

Setting up texlive-binaries (2009-5ubuntu0.2) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Building format(s) --refresh.
    This may take some time... done.

adarsh@adarsh-desktop:~$ 
```[B]
Version of my ubuntu :  Ubuntu 10.04 LTS - the Lucid Lynx [/B]

now, i am able to install application from software centre. thanks a lot 

if there anything else i should do, pls let me know...

1 more question... is there way i can back up my OS completely? i am asking this because if i screw it up again, all i have to do is to restore back up... can this be done?

thanks once again.

---

### Post by sikander3786 on 2010-12-21
Yep that output tells us that your issue has been solved. Congrats.

Regarding Backup, re-installing Ubuntu from scratch is a matter of half hour only. So I prefer that way. Never needed though.

If you are interested in backing up your downloaded packages so you don't need to re-download them every time, use APTonCD.

[http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)

If you want a complete backup of everything, try Clonezilla.

[http://www.clonezilla.org](http://www.clonezilla.org)

For the moment, you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by ags84 on 2010-12-21
done...

thanks a lot mate.. thanks a lot.

---

