---
title: "texlive install"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by tituspurdin on 2010-12-23
I have TeX (actually texlive) running on three of my Ubuntu installs.
However on this laptop I have NOT been able to get it to install.  I
have used the Package Manager.  I have used apt-get.  I have even used
apt-get to do apt-get install texlive-full!

It hangs up late in the process and tells me that I have "dependency
problems".  I have explored the log files; but without any luck.  It
is clean though that it is failing on the installation of tex-common.

Help would be appreciated.  "Go use one of the machines on which the
install worked" is NOT a good answer.  Thanks.


Titus sends

---

### Post by mikewhatever on 2010-12-23
You could try running **sudo apt-get install -f** in case there are broken packages. Other then that, post the actual output of the installation command to give people something to look at.

---

### Post by tituspurdin on 2010-12-24
Tried "apt-get install -f".  Got the following error:

Building formats --byhyphen .
	This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.wH31nszp


The contents of that log file are:

fmtutil: no format depends on hyphen file `//'.


Thanks for any insight into this problem.


Titus sends

---

