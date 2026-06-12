---
title: "problems with Open Office ..."
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by Morpholinux on 2010-01-17
Hi!...
I had a few problems with Open Office...*OO ..I think was the 3.1.1 version...

in Writer while saving the document to a .doc, ...OO suddenly close and saves your document, but never does the .doc conversion
also while working with Impress...OO...suddenly (and more often than Writer)
close and also saves your data...

after a while you get tired..
so I follow the instructions here ( [http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Installing_on_Debian_based_Distros](http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Installing_on_Debian_based_Distros) ) to Install the OO sun version...
..
although the md5sum never match..
c8790102fa13ac8a4073a09b51ecf7e2 OOo_3.1.0_LinuxIntel_install_es_deb.tar.gz (I downloaded it twice and do the checksum...which was the same..but not the one in their list....)
I keep on with the installation but have problems the second time you do
   sudo dpkg -i *.deb
at the    desktop-integration folder

murphy@eva01:~/DEBS/desktop-integration$    sudo dpkg -i *.deb
Selecting previously deselected package openoffice.org-debian-menus.
dpkg: regarding openoffice.org3.1-debian-menus_3.1-9399_all.deb containing openoffice.org-debian-menus:
 openoffice.org-common conflicts with openoffice.org-debian-menus
  openoffice.org-debian-menus (version 3.1-9399) is to be installed.
dpkg: error processing openoffice.org3.1-debian-menus_3.1-9399_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org3.1-debian-menus_3.1-9399_all.deb


what I think is that..the installation went OK, but there's a problem with the links to the program...or something like that..

I can see the man pages for OO...but cannot launch any program like writer..
here...
murphy@eva01:~$ ooffice -writer
/usr/lib/openoffice/program/soffice: 214: /usr/lib/openoffice/program/../basis-link/program/pagein: not found
/usr/lib/openoffice/program/soffice: 234: /usr/lib/openoffice/program/soffice.bin: not found

murphy@eva01:~$ ooffice -impress
/usr/lib/openoffice/program/soffice: 214: /usr/lib/openoffice/program/../basis-link/program/pagein: not found
/usr/lib/openoffice/program/soffice: 234: /usr/lib/openoffice/program/soffice.bin: not found




any suggestions??



thanks in advance...



ps..by the way...everything here explained was also sent to [email]webmasters@openoffice.org[/email] so if they have a solution I will paste it here..

---

### Post by 73ckn797 on 2010-01-18
Does the OO that comes with Ubuntu not work? You could go to Synaptic Package Manager and reinstall. You may also have to completely uninstall the original version before trying to install a later version, if that is what you are doing. Is the original version in 9.04 the 3.0 OO? I cannot recall.

---

### Post by Morpholinux on 2010-01-19
I don't remember....quite well but I think ..I got problems with OO.o with my upgrade from 9.04 to 9.10....


uhmmmm....at some page..I saw a OO.o 3.2 Release Candidate 2...
could I remove everything....and then install this one?

??

or 

should I remove OO.o (completely from spm) and then reinstall OO.o also from spm???

...or...someone else have any ideas?

---

### Post by wilee-nilee on 2010-01-19
Open Office has deb releases if you continue with a direct from them download here is 3.2.
[http://download.openoffice.org/all_rc.html](http://download.openoffice.org/all_rc.html)

---

### Post by 73ckn797 on 2010-01-19
Check out this link [http://ubuntuforums.org/showthread.php?t=947924](http://ubuntuforums.org/showthread.php?t=947924)

It is from 2008 but it was how I installed OO from a deb file. The file names will differ but it might help you in this situation.

---

### Post by Morpholinux on 2010-01-20
Hi....

ummmm Within Synaptic Package Manager.., I uninstalled (completely) everything that had something to do with openoffice.


......I was careful...not removing....some language packages...but....maybe I did something wrong 

I went to the link that wilee-nilee gave
downloaded OOo_3.2.0rc3_20100118_LinuxIntel_install_es_deb.tar.gz
and do the same as 73ckn797
..

...I can see the icons of Base, Calc, Draw, Impress, Math, Printer Administration and Writer... at the Applications->office menu... 

but a few minutes ago I used Calc....and ..it suddenly close..(this time without saving your data...)...

....what can I do to solve that?
.
any info, or a way to get it..it will be appreciated 



thanks!

---

### Post by 73ckn797 on 2010-01-20
Did you upgrade Ubuntu or do a fresh install? Upgrades can tend to cause problems.

---

### Post by wilee-nilee on 2010-01-20
> **Morpholinux said:**
> Hi....

ummmm Within Synaptic Package Manager.., I uninstalled (completely) everything that had something to do with openoffice.


......I was careful...not removing....some language packages...but....maybe I did something wrong 

I went to the link that wilee-nilee gave
downloaded OOo_3.2.0rc3_20100118_LinuxIntel_install_es_deb.tar.gz
and do the same as 73ckn797
..

...I can see the icons of Base, Calc, Draw, Impress, Math, Printer Administration and Writer... at the Applications->office menu... 

but a few minutes ago I used Calc....and ..it suddenly close..(this time without saving your data...)...

....what can I do to solve that?
.
any info, or a way to get it..it will be appreciated 



thanks!

In the past I have found OO to work best when jumping distros other then regular updates; if you remove everything including the file left in home then install the new version works generally. If you use the deb for your language the pack will be installed.

I don't know if this is the problem, and I suspect help on 3.2 will be sparse, but we assume the package should basically work.

---

### Post by Hagar Delest on 2010-01-23
First try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

When you install OOo with the debs, always remove any OOo package left in Synaptic, even the OOo language packs. The Ubuntu version and the Sun version are not compatible with each others.

---

