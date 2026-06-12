---
title: "Open office"
date: 2005-05-09
forum: Installation &amp; Upgrades
---

### Post by Me_Titus on 2005-05-09
Hi there

I am trying to install the last build of openOffice. I am fallowing this hints.

1.) Download native .rpms
2.) "tar xzf" to extract RPMS/ subdir; cd RPMS/
3.) Run su to become root and run 'alien -k *.i586.rpm' to produce .deb 
packages
4.) Install via "dpkg -i --force-overwrite *.deb" (--force-overwrite 
needed to correct spurious file conflicts in .debs produced by alien)
5.) Edit /opt/openoffice1.9.51/share/config/javavendors.xml to remove 
references to IBM and Blackdown vendors
6.) As root, run by hand postinst commands to complete configuration:
   # /opt/openoffice1.9.51/program/pkgchk --shared (you get 'pkgchk done.')
   # /opt/openoffice1.9.51/program/configimport --spool (you get success msgs)
   # /opt/openoffice1.9.51/program/update-mime-data "openoffice1.9"
7.) Exit su shell via 'exit'
8.) Run '/opt/openoffice1.9.51/program/soffice'


I did everything till number 5, but when i tryied do to the number 6, i got into problems, coz i reveive i messeger saying that the command is not found.


Any help would be apretiated.
Thanks,
Marco

---

### Post by defkewl on 2005-05-10
Why didn't you use apt-get instead?

---

