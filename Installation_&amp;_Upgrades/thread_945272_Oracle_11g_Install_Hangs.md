---
title: "Oracle 11g Install Hangs"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by lynwode on 2008-10-12
Hey,
I trying to install Oracle 11g (64bit) on Ubuntu 8.04 (64bit). 
I have followed the tutorial at [http://www.pythian.com/blogs/968/installing-oracle-11g-on-ubuntu-804-lts-hardy-heron](http://www.pythian.com/blogs/968/installing-oracle-11g-on-ubuntu-804-lts-hardy-heron) and all goes well until the coping of files happens where it hangs at 2%. the last few lies of the log file are:

INFO: *** Install Page***
INFO: FastCopy : File Version is Compatible
INFO: Install mode is fastcopy mode for component 'oracle.server' with Install type 'EE'.
INFO: Link phase has been specified as needed
INFO: Setup phase has been specified as needed
INFO: HomeSetup JRE files in Scratch :0
INFO: Setting variable 'ROOTSH_LOCATION' to '/u01/oracle/app/oracle/product/11.1.0/db_1/root.sh'. Received the value from a code block.
INFO: Setting variable 'ROOTSH_LOCATION' to '/u01/oracle/app/oracle/product/11.1.0/db_1/root.sh'. Received the value from a code block.
INFO: Performing fastcopy operations based on the information in the file 'oracle.server_EE_exp_1.xml'.
INFO: Performing fastcopy operations based on the information in the file 'racfiles.jar'.
INFO: Performing fastcopy operations based on the information in the file 'oracle.server_EE_dirs.lst'.
INFO: Performing fastcopy operations based on the information in the file 'oracle.server_EE_filemap.jar'.
INFO: Performing fastcopy operations based on the information in the file 'oracle.server_EE_1.xml'.
INFO: Performing fastcopy operations based on the information in the file 'setperms1.sh'.
INFO: Number of threads for fast copy :1
WARNING: Do you really want to exit?
INFO: User Selected: Yes/OK


I also noticed that in the terminal window where I ran the installer from the following is repeated numerous times:

ulimit: 1: Illegal option -u

Has anyone seen this before or have any ideas of where too look?

cheers,
Tim.

---

### Post by lynwode on 2009-03-16
Solved: Corrupt download.

---

