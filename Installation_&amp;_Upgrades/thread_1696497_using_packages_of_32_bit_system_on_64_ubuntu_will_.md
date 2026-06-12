---
title: "using packages of 32 bit system on 64 ubuntu will it work"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2011-02-27
Hi,
I am having some confusion.For development work  I needed 
following packages 

> bcc bin86 gawk bridge-utils iproute libcurl3 libcurl4-openssl-dev bzip2 module-init-tools transfig tgif texinfo texlive-latex-base texlive-latex-recommended texlive-fonts-extra texlive-fonts-recommended pciutils-dev mercurial build-essential make gcc libc6-dev zlib1g-dev python python-dev python-twisted libncurses5-dev patch libvncserver-dev libsdl-dev libjpeg62-dev iasl libbz2-dev e2fslibs-dev git-core uuid-dev ocaml libx11-dev bison flex


I until now was using them on a 32 bit system.Ubuntu 10.04.
Here I am switching the computer to 64 bit and want to build same environment how ever my confusion is above packages are approximately 430 Mb and are present in /var/cache/apt/archives on my 32 bit system.Can I transfer those to my 64 bit system and use or there is a difference in packages for 32 bit and 64 bit and I should be using a fresh install on the 64 bit system.
I am not clear with this part.

---

### Post by quixote on 2011-02-28
Is there a reason why you don't want to do a fresh install of those packages?  I'd recommend it.  I don't know for a fact that using the 32-bit versions would cause problems, but I'm pretty sure they would.

---

### Post by tapas_mishra on 2011-02-28
The bandwidth I have is based on amount of data being transferred and that sums up to 800mb so 1) cost 2) the time it will take for me to download those is tremendous and I do not have that good internet connectivity to retain plus the cost will be too much by the ISP.

---

### Post by quixote on 2011-03-02
Well, while we're still waiting for someone to answer your actual question about whether you can use the 32-bit packages on a 64-bit system (I really doubt it), I have one other suggestion.  Ubuntu sends out [a free CD]("http://www.ubuntu.com/desktop/get-ubuntu/cds") (courtesy Mark Shuttleworth) if you have a slow connection.  They say it can take up to ten weeks, so it's less than ideal, but it may turn out faster than getting your question answered! :D

---

### Post by tapas_mishra on 2011-03-03
:) Well they send free CDs but the packages I am looking to install might be in different repositories which may not be present on CDs.

---

### Post by Hakunka-Matata on 2011-03-03
[http://packages.ubuntu.com/lucid/bin86]("http://packages.ubuntu.com/lucid/bin86")

I do not know the answer, but this page shows the files lists for both packages, the i386 and AMD64 architectures.  Maybe that information will help?

---

### Post by bsntech on 2011-03-03
You'll also have to install the ia32libs package so your 64-bit PC will be able to convert the 32-bit applications.

Brian S.
[http://www.bsntech.com]("http://www.bsntech.com")

---

### Post by Hakunka-Matata on 2011-03-03
[http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")

This thread may be your answer!

getlibs

---

### Post by psusi on 2011-03-03
No, you have to install the 64bit packages on the 64bit system.

---

