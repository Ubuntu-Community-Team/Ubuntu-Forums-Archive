---
title: "OpenFOAM 1.6 installation in Ubuntu 9.1"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by jsmanian on 2009-12-31
Hi,

   I tried to install 32bit openfoam 1.6 in my computer. I downloaded the software files (gt.gz extension files). I copied these files to "HOME/OpenFOAM/" and tried to extract the files. During extraction, I got this error. I could not understand how to solve this. 

OpenFOAM-1.6/doc/Doxygen/html/diagonalPreconditioner_8H_source.html
OpenFOAM-1.6/doc/Doxygen/html/primitiveFacePatch_8H.html
OpenFOAM-1.6/doc/Doxygen/html/dir_6bd9c8b0b053b81811bdf66e82663953_dep.map
OpenFOAM-1.6/doc/Doxygen/html/inherit__graph__685.map
OpenFOAM-1.6/doc/Doxygen/html/faceZoneToCell_8C.html

gzip: stdin: unexpected end of file
OpenFOAM-1.6/doc/Doxygen/html/dir_3c6846df93171e75921dc3b3743012bd.html
OpenFOAM-1.6/doc/Doxygen/html/classFoam_1_1IOobject_e2d24c54065f40a5308aae0a35de1788_icgraph.png
OpenFOAM-1.6/doc/Doxygen/html/dir_4e1895e970d33ca4d9340a1aa8a32503.html
OpenFOAM-1.6/doc/Doxygen/html/dir_d3ef7119cc431c4741126c63bab62bd0_dep.map
OpenFOAM-1.6/doc/Doxygen/html/inherit__graph__547.md5
OpenFOAM-1.6/doc/Doxygen/html/stitchMesh_8C.html
OpenFOAM-1.6/doc/Doxygen/html/inherit__graph__384.png
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now


Could anybody give suggestions to install openfoam correctly?

---

### Post by phillw on 2009-12-31
Hi & welcome to the forums,

OpenFoam is not a regular package (well, not to me) 

The fact that **tar** is complaining about unexpected end of package is tar saying the bund;e you down loaded is not complete. i.e. only x% of the downloaded file actually landed on your computer & there's a part of it missing.

So, that is that error out of the way.

This thread may help you

[http://www.cfd-online.com/Forums/openfoam-installation/71354-installing-openfoam-1-6-ubuntu-9-10-a.html](http://www.cfd-online.com/Forums/openfoam-installation/71354-installing-openfoam-1-6-ubuntu-9-10-a.html)

nabeels seems to have posted every where - which is making my trying to find a sane answer very difficult.

There is a solution for v1.5 and ubuntu 9.10 over here --> [http://www.cfd-online.com/Forums/openfoam-installation/65039-openfoam-1-5-solaris-compilation-problem-calling-octreedatapoint-constructor.html#post240760](http://www.cfd-online.com/Forums/openfoam-installation/65039-openfoam-1-5-solaris-compilation-problem-calling-octreedatapoint-constructor.html#post240760)

the cfd area does seem to be the best support for that package.

Regards,

Phill.

---

### Post by jsmanian on 2010-01-01
Hi Phill,

      I gone through the threads pointed out by you. But I could not find solution for my error. From your suggestion, it may be error due to incomplete download. I will once again download and check it out. If I face any difficulty, I come back to you.

     Thanks for your kind help:)

---

### Post by jsmanian on 2010-01-03
Hi Phill,

Yes. You are correct. It is the issue with downloading the package. I downloaded once again and installed successfully. :P

---

### Post by meharts on 2010-01-11
Hi guys:)

Look I am a bit of a Linux geek (have my own company building computers, general support, etc) but I am no maths wiz...

I have built a lovely computer for a engineer who wants to use OpenFOAM but I haven't been able to get it installed....

Been chasing down info but many replies to differn't threads ...don't give all relevant info and assume that the person reading is up on all they are explaining....

I would like to get this working for my customer and really need some start to finish advice..... 

I have installed the latest version of Ubuntu Karmic 64bit

I then updated all my files that were available and that went OK and I now have the following kernel 2.6.31.17-generic.

I then created my OpenFOAM directory in home and downloaded the appropiate packages ...unpacking the general ones first and then unpacking the other ones in the appropiate directories as explained at OpenFoam....

I then followed derjames advice as shown in this thread:

[http://ubuntuforums.org/showthread.php?t=156298&highlight=open+foam](http://ubuntuforums.org/showthread.php?t=156298&highlight=open+foam)



> 



Code:

. $HOME/OpenFOAM/OpenFOAM-1.5/etc/bashrc

now 'source' the variables with

Code:

source ~/.bashrc

(5)Navigate to OpenFOAM-1.5/bin and execute the foamIntallationTest script

Code:

./foamInstallationTest






I even edited the etc/settings.sh file as shown in this thread by ICL


[http://www.cfd-online.com/Forums/openfoam-installation/69761-problem-installing-1-6-ubuntu-9-10-64-bit-how-use-gcc-4-4-1-a.html](http://www.cfd-online.com/Forums/openfoam-installation/69761-problem-installing-1-6-ubuntu-9-10-64-bit-how-use-gcc-4-4-1-a.html)

But I still get the following fault:



```


Executing /home/ruben/OpenFOAM/OpenFOAM-1.6/bin/foamInstallationTest:


Checking basic setup...
-------------------------------------------------------------------------------
Shell:              bash
Host:               ruben-desktop
OS:                 Linux version 2.6.31-17-generic
-------------------------------------------------------------------------------


Checking main OpenFOAM env variables...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid      Crit
-------------------------------------------------------------------------------
$WM_PROJECT_INST_DIR /home/ruben/OpenFOAM                     yes       yes
$WM_PROJECT_USER_DIR /home/ruben/OpenFOAM/ruben-1.6           no        no
$WM_THIRD_PARTY_DIR  /home/ruben/OpenFOAM/ThirdParty-1.6      yes       yes
-------------------------------------------------------------------------------


Checking the OpenFOAM env variables set on the PATH...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid Path Crit
-------------------------------------------------------------------------------
$WM_PROJECT_DIR      /home/ruben/OpenFOAM/OpenFOAM-1.6        yes  yes  yes

$FOAM_APPBIN         ...1.6/applications/bin/linux64GccDPOpt  no        yes
$FOAM_SITE_APPBIN    ...penFOAM/site/1.6/bin/linux64GccDPOpt  no        no
$FOAM_USER_APPBIN    ...1.6/applications/bin/linux64GccDPOpt  no        no
$WM_DIR              /home/ruben/OpenFOAM/OpenFOAM-1.6/wmake  yes  yes  yes
-------------------------------------------------------------------------------


Checking the OpenFOAM env variables set on the LD_LIBRARY_PATH...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid Path Crit
-------------------------------------------------------------------------------
$FOAM_LIBBIN         ...OAM/OpenFOAM-1.6/lib/linux64GccDPOpt  yes  yes  yes
$FOAM_SITE_LIBBIN    ...penFOAM/site/1.6/lib/linux64GccDPOpt  no        no
$FOAM_USER_LIBBIN    ...enFOAM/ruben-1.6/lib/linux64GccDPOpt  no        no
$MPI_ARCH_PATH       ...nmpi-1.3.3/platforms/linux64GccDPOpt  no        yes
-------------------------------------------------------------------------------


Third party software
-------------------------------------------------------------------------------
Software Version   Location 
-------------------------------------------------------------------------------
WARNING: gcc version does not match gcc supplied with this release of OpenFOAM
         Supplied version: 4.3.3
         User version    : 4.4.1
         Minimum required: 4.3.1

gcc      4.4.1    
WARNING:  Conflicting installations:
          OpenFOAM settings        : /home/ruben/OpenFOAM/ThirdParty-1.6/gcc-4.3.3/platforms/linux64/bin/gcc
          current path             : /usr/bin/gcc
          CRITICAL ERROR

gzip     1.3.12    /bin/gzip                                                
tar      1.22      /bin/tar                                                 
icoFoam           
WARNING:  Conflicting installations:
          OpenFOAM settings        : /home/ruben/OpenFOAM/OpenFOAM-1.6/applications/bin/linux64GccDPOpt/icoFoam
          current path             : 
          CRITICAL ERROR

-------------------------------------------------------------------------------


Summary
-------------------------------------------------------------------------------
Base configuration ok.

The foam installation contains 2 critical error(s).

Review the output for warning messages and consult 
the installation guide for trouble shooting.

done.


```

I really could do with some help on this matter PLEASE!

Thanks a lot as always!

meharts

---

### Post by llawwehttam on 2010-01-11
Just to resolve one of the problems you need to update gcc.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by meharts on 2010-01-11
Hi llawwehttam:)

I ran your code....but as I pointed out...already updated everything, so it came back nothing to do.

Thanks anyway!

meharts

---

### Post by ub_dee on 2010-02-28
Hi Meharts
I had the same problem with the gcc "Conflicting Installation" as well
I found a nice little solution somewhere that basically you add

```
export WM_64=on
```

in your .bashrc in your home directory BEFORE you source the bashrc file in the Openfoam directory.  Of course this is assuming you're using a 64-bit machine, but if you're running CFD, you probably should be using a 64-bit comp.

As for the icofoam "Conflicting Installation" ...I'm looking for a solution myself

---

### Post by ub_dee on 2010-02-28
I see what happened.  Because I didn't have the "export WM_64=on" when I compiled the program, the applications including icoFoam didn't correctly compile

So you need to add that line "export WM_64=on" into your ~/.bashrc then in $FOAM_APP, recompile the applications by running ./Allwmake

Once that's done, do a 
```
ls $FOAM_APPBIN/icoFoam
```
to verify that icoFoam was correctly compiled.

Now if you run the
```
$WM_PROJECT_DIR/bin/foamInstallationTest
```

You should have no more errors....hopefully.  Hope this works for you!

---

### Post by Canesin on 2010-04-20
You could also just use the automatic installer script for ubuntu...
It is a opensource project and can be found in: [http://code.google.com/p/openfoam-ubuntu](http://code.google.com/p/openfoam-ubuntu)[]("http://code.gooogle.com/p/openfoam-ubuntu")

---

