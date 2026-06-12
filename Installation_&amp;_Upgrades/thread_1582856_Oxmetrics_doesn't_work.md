---
title: "Oxmetrics doesn't work"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by rakelspektakel on 2010-09-27
Hi, 

I'm desperate, I have week only to go through alot of exercises, and need to sit at nights too, so eventhough I gave the installation up at the start of the semester, I really need to get this to work now.

I have Lucid. At my department the download version of Oxmetrics is 6.00-0.i386.rpm

I have converted the file with alien first with alien -d, then with alien -i -c. oxmetrics starts but wont model, 'error cant start pcgive13'. /wrote pcgive12 first, wrongly/

i uninstalled and tried again, same error message with alien: error unknown format incorrect tag (or something very similar). but it does deliver a .deb-file, and it does  install.

now i tried  installing oxpro also and got the following:

------------
rakel@AdaNikolaj:~/Downloads$ sudo alien -i -c oxpro-6.00-0.i386.rpm
error: incorrect format: unknown tag
    dpkg --no-force-overwrite -i oxpro_6.00-1_i386.deb
Selecting previously deselected package oxpro.
(Reading database ... 
dpkg: warning: files list file for package `pips-snx100' missing, assuming package has no files currently installed.
(Reading database ... 134310 files and directories currently installed.)
Unpacking oxpro (from oxpro_6.00-1_i386.deb) ...
dpkg: error processing oxpro_6.00-1_i386.deb (--install):
 trying to overwrite '/usr/share/OxMetrics6/doc/oxmetrics_index.html', which is also in package oxmetrics 0:6.00-1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 oxpro_6.00-1_i386.deb
Unable to install at /usr/share/perl5/Alien/Package/Deb.pm line 92, <GETPERMS> line 680.
    find oxpro-6.00 -type d -exec chmod 755 {} ;
    rm -rf oxpro-6.00
------------

I know i should probably remove everything and start from scratch, but how do i do it, and what is wrong to start with? Pleeeease help?

---

