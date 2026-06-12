---
title: "Cannot install JGR (R) because cannot install png (R)"
date: 2015-07-17
forum: Installation &amp; Upgrades
---

### Post by kuragari on 2015-07-17
Dear all,

I'm trying to install Deducer's packages. Hence I'm following this guide [here]("http://r-interface.blogspot.com.es/2012/04/install-r-jgr-and-deducer-in-ubuntu.html"). During the installation of the required packages I got:

```

[...]
** R
** inst
** preparing package for lazy loading
** help
*** installing help indices
** building package indices
** testing if installed package can be loaded
* DONE (JavaGD)
ERROR: dependency ‘png’ is not available for package ‘iplots’
* removing ‘/home/kuragari/R/x86_64-pc-linux-gnu-library/3.2/iplots’
ERROR: dependency ‘iplots’ is not available for package ‘JGR’
* removing ‘/home/kuragari/R/x86_64-pc-linux-gnu-library/3.2/JGR’
```

Do I tried to install, directly, the png package. In this I got:
```

Error in dyn.load(file, DLLpath = DLLpath, ...) : 
  unable to load shared object '/home/kuragari/R/x86_64-pc-linux-gnu-library/3.2/png/libs/png.so':
  libpng15.so.15: cannot open shared object file: No such file or directory
Error: loading failed
Execution halted
ERROR: loading failed
* removing ‘/home/kuragari/R/x86_64-pc-linux-gnu-library/3.2/png’

The downloaded source packages are in
	‘/tmp/Rtmp5XdiOl/downloaded_packages’
Warning message:
In install.packages("png") :
  installation of package ‘png’ had non-zero exit status
```

I checked if I got the libpng installed:

```
kuragari@trenzalore:~$ dpkg --get-selections | grep png
libpng12-0:amd64				install
libpng12-dev					install
libpng3:amd64					install
```

So... how I can solve this? How can I install the png R package in order to install Deducer?

---

### Post by stuckinsd on 2015-09-26
Hi Kuragari,

   I found your post months later because I am having a similar problem. I get the same error when installing the EBImage R package from Bioconductor. Here is my solution, I created a directory and copied the libraries into it. My libpng is on version 16 (libpng16.so.16) whereas yours was 15 (libpng15.so.15)

>  # This fixed it for me!mkdir /home/[COLOR=#000000][FONT=Ubuntu Mono]kuragari[/FONT][/COLOR]/R/x86_64-pc-linux-gnu-library/3.2/png/
mkdir /home/[COLOR=#000000][FONT=Ubuntu Mono]kuragari[/FONT][/COLOR]/R/x86_64-pc-linux-gnu-library/3.2/png/libs/
ln -s /usr/[COLOR=#000000][FONT=Ubuntu Mono]kuragari[/FONT][/COLOR]/x86_64-linux-gnu/imlib2/loaders/png.so /home/tlu/R/x86_64-pc-linux-gnu-library/3.2/png/libs/
ln -s /home/[COLOR=#000000][FONT=Ubuntu Mono]kuragari[/FONT][/COLOR]/anaconda/lib/libpng16.so.16 /home/tlu/R/x86_64-pc-linux-gnu-library/3.2/png/libs/
ln -s /home/[COLOR=#000000][FONT=Ubuntu Mono]kuragari[/FONT][/COLOR]/anaconda/lib/libpng16.so.16.17.0 /home/tlu/R/x86_64-pc-linux-gnu-library/3.2/png/libs/




 I hope this can save someone some pain someday.

---

