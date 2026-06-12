---
title: "after mablab installation, xsetup, can't run"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by kevinwl on 2006-06-03
I use root to install Matlab 7. jre installation OKey.
the install of matlab to final stage, show install successful, but in the terminal show message below:
-------------------------------------------------------------------

    The following messages were written to standard error
    while running 'xsetup' the X Window System version
    of 'install'.

        sh: /media/cdrom0/update/install/backend: /bin/sh: bad interpreter: Perm ission denied

-------------------------------------------------------------------
/tmp/12214tmwinstall/update/install/main.sh: /media/cdrom0/install: /bin/sh: bad  interpreter: Permission denied
/tmp/12214tmwinstall/update/install/main.sh: line 308: /media/cdrom0/install: Su ccess


and when type in terminal : matlab   show message below:
bash: matlab: command not found


may anyone give me an solution?

KWL:confused: ](*,)

---

### Post by BaffledMollusc on 2006-06-03
[QUOTE=kevinwl]I use root to install Matlab 7. jre installation OKey.
the install of matlab to final stage, show install successful, but in the terminal show message below:
-------------------------------------------------------------------

    The following messages were written to standard error
    while running 'xsetup' the X Window System version
    of 'install'.

        sh: /media/cdrom0/update/install/backend: /bin/sh: bad interpreter: Perm ission denied

-------------------------------------------------------------------
/tmp/12214tmwinstall/update/install/main.sh: /media/cdrom0/install: /bin/sh: bad  interpreter: Permission denied
/tmp/12214tmwinstall/update/install/main.sh: line 308: /media/cdrom0/install: Su ccess


and when type in terminal : matlab   show message below:
bash: matlab: command not found


may anyone give me an solution?

KWL:confused: ](*,)[/QUOTE]
I'm also struggling to install matlab. I think those errors you got are just part of the clean up script complaining it can't delete some temporary files. I think. I just ignored them.

After installing matlab you have to go to your matlab directory and run a script. I'm not on my computer with matlab at the moment, but I think the script is in the  matlab/bin directory, and is called "install_matlab" or "matlab_install" or something like that. If you run it by typing "sh install_matlab" and answer the questions it should set everything up.

After that was done, I got another problem, and that is that when I tried to run matlab I got an error about memory corruption. I still haven't fixed that error.

If you do manage to get matlab working, please let me know what you did!

---

### Post by kevinwl on 2006-06-03
I fixed my problem with your suggestion exactly, nothing happened with memory crush.
 maybe your need to make sure your java is right, because the default java is not the one from Sun. check it with 'java -version', should be 
java version "1.5.0_07"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_07-b03)
Java HotSpot(TM) Client VM (build 1.5.0_07-b03, mixed mode, sharing)


there is one poster in this forum talking about how install this

thanks so much
 enjoy your ubuntu

KWL

---

### Post by BaffledMollusc on 2006-06-04
[QUOTE=kevinwl]I fixed my problem with your suggestion exactly, nothing happened with memory crush.
 maybe your need to make sure your java is right, because the default java is not the one from Sun. check it with 'java -version', should be 
java version "1.5.0_07"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_07-b03)
Java HotSpot(TM) Client VM (build 1.5.0_07-b03, mixed mode, sharing)


there is one poster in this forum talking about how install this

thanks so much
 enjoy your ubuntu

KWL[/QUOTE]
Thanks, I'll check this out tomorrow. I suspect it's not a Java problem, but it's worth a shot.

---

### Post by gregfrank on 2006-06-04
You need to copy the whole Matlab CD to a temporary directory, and install it from there.  You can't run the install script from the CD in Ubuntu.  Device /media/cdrom0 has limited permissions and that's likely the source of your errors.  See the Ubuntu wiki on Matlab for detailed instructions if you're not sure how: [http://wiki.ubuntu.com/MATLAB](http://wiki.ubuntu.com/MATLAB)

---

### Post by kevinwl on 2006-06-04
However, I install matlab from CD. it works perfectly

---

### Post by BaffledMollusc on 2006-06-05
[QUOTE=gregfrank]You need to copy the whole Matlab CD to a temporary directory, and install it from there.  You can't run the install script from the CD in Ubuntu.  Device /media/cdrom0 has limited permissions and that's likely the source of your errors.  See the Ubuntu wiki on Matlab for detailed instructions if you're not sure how: [http://wiki.ubuntu.com/MATLAB](http://wiki.ubuntu.com/MATLAB)[/QUOTE]
Yeah, I was doing that. The problem I had seems to be something to do with the fact that I was using a 64-bit version of Ubuntu. I solved the problem by installing with the -glnx86 option, installing the 32 bit version of matlab, and then running matlab each time with the -glnx86 option at the command line.

This means I have a 32 bit version of Matlab rather than the 64-bit version, but at least it works.

---

