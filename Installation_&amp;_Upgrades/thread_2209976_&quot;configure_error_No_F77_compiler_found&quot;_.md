---
title: "&quot;configure: error: No F77 compiler found&quot; during R installation"
date: 2014-03-08
forum: Installation &amp; Upgrades
---

### Post by radhika arava on 2014-03-08
Hello,
I have ubuntu installation maverick (ubuntu 10.10) on my laptop. 
When I try to configure 'R-3.0.2' on my laptop, it exits giving an error of " configure: error: No F77 compiler found". 
I looked for fortran installations on my machine. I found none.
I tried to install fortran, using apt-get, but it could not find the packages.
I downloaded the gfortran package from the website and tried to install it, but it says some dependency related to gcc is missing.
What should I be doing now. I badly need R installed on my machine.
Please help me.
Thanks.

---

### Post by steeldriver on 2014-03-08
Hello and welcome to the forums

Unfortunately, the Maverick release has reached EOL and is no longer supported. You *may* be able to install a compatible version of R from the old-releases repository archive - see [How to install software or upgrade from old unsupported release?]("http://askubuntu.com/a/91821/178692"). If you absolutely need R-3.x you will likely need to upgrade to a supported release.

---

### Post by radhika arava on 2014-03-08
Thank you sir. 
I changes the sources list in etc folder and I installed fortran, just now and I could install R on my machine. however, now the error of "the inconsolata.sty file and zi4.sty are not found" comes up. I think that too can be fixed. So, I will clear this thread. Very thankful for your headsup and your reply. :)

---

