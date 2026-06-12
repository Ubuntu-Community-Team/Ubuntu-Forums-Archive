---
title: "Amsn 0.95-1"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by jdavis on 2006-06-01
Hello,

After upgrading to Dapper my AMSN has been upgraded to 0.95-1 (from 0.95 on Breezy) and I can no longer use it. I receive the message "segmentation fault". If I return to 0.95 AMSN it works ok but the update manager keeps telling me to update to the latest version! I have currently locked the version in synaptic so it stops reminding me, although i would prefer a fix...

Can anyone explain the errors AMSN 0.95-1 has when launching? and whether this is because 0.95-1 is not yet supported in dapper?


thanks, Jonathan :)

---

### Post by Wenakko on 2006-06-02
same happens for me ](*,)

---

### Post by aysiu on 2006-06-02
Two people have experienced this? Sounds like a [bug report](https://launchpad.net/malone) to me.

---

### Post by panurge77 on 2006-06-02
[http://www.ubuntuforums.org/showthread.php?t=87001&highlight=amsn](http://www.ubuntuforums.org/showthread.php?t=87001&highlight=amsn)

You can find debs for the new tcl/tk and amsn with truetype fonts on this thread. It makes it all more pleasant (not that ugly anymore). Only one thing: the dapper debs are outdated, you can use the new breezy debs and they should work on dapper too.

---

### Post by panurge77 on 2006-06-02
News: now amsn is bugging me down too, I tried several versions, offical and non official and all fall in some kind of bug. I'll probably compile it as in old days when I find some patience

---

### Post by Neo40 on 2006-06-03
Hi,

Someone can tell me where I can find a "working" HOW-TO to install amsn (with the nice fonts)  in Dapper?

Thanks

---

### Post by jdavis on 2006-06-04
Upgraded to Dapper on 2 more PC's and got the same amsn problems.... 
Although I think I now have a fix to the "segmentation fault" error!

While having another play around I somehow figured out
that if you remove the tk8.5 and tcl8.5 packages:

```

sudo apt-get remove tcl8.5 tk8.5

```

then amsn starts working again!....

Jonathan

---

### Post by GQed76 on 2006-06-04
yup that worked

---

### Post by panurge77 on 2006-06-04
Amsn wiki tells amsn hangs is a known issue with kernel 2.6.
This happens when amsn try to play sounds and the sound card is in use by other program. Suggested fix is disabling sounds or loading amsn with : 
export LD_ASSUME_KERNEL=2.2.5 && msn/amsn

I disabled sounds and changed amsn sound configuration to use esdplay (just in case...) It looks stable now...


NEO40: check this thread  	[http://www.ubuntuforums.org/showthre...highlight=amsn](http://www.ubuntuforums.org/showthre...highlight=amsn)

jdavis: from which repo did you get tcl/tk8.5? I downloaded the debs from the thread above. Tcl/tk sould be compiled WITHOUT --enable-threads for amsn to run properly...
(Removing tcl/tk 8.5 would make amsn ugly again)

---

### Post by jdavis on 2006-06-04
[QUOTE=panurge77]
jdavis: from which repo did you get tcl/tk8.5? I downloaded the debs from the thread above. Tcl/tk sould be compiled WITHOUT --enable-threads for amsn to run properly...
(Removing tcl/tk 8.5 would make amsn ugly again)[/QUOTE]

I used the TCL/TK from the [forum thread]("http://www.ubuntuforums.org/showthread.php?t=87001&highlight=amsn") as suggested (tcl8.5_8.5.0-1~neto3_i386.deb **&** tk8.5_8.5.0-1~neto3_i386.deb) and installed amsn (amsn_0.95-1~neto1_i386.deb) just as it was documented...

I did get it working on one machine with the packages in that thread, but synaptic kept bugging me to upgrade as the version in the dapper repo's is newer!  I'm not too bothered about the uglyness, but i might give it another shot when i have some spare time.

---

### Post by panurge77 on 2006-06-04
I dont see any versions of tcl 8.5 in the repos and I've enabled them all. So my synaptic never asked to update it. This might come from another repo you are using?

also, neto's debs are already 95-2 for dapper. did you downloaded the dapper deb?
[http://201.220.118.143:8080/Ubuntu%20-%20Dapper/amsn/amsn_0.95-2~neto1_i386.deb](http://201.220.118.143:8080/Ubuntu%20-%20Dapper/amsn/amsn_0.95-2~neto1_i386.deb)

it's running fine here since I disabled sounds and changed the play command to esdplay

---

### Post by jdavis on 2006-06-04
[QUOTE=panurge77]I dont see any versions of tcl 8.5 in the repos and I've enabled them all. So my synaptic never asked to update it. This might come from another repo you are using?[/QUOTE]


Not sure, I disabled all non-official repo's when i upgraded and haven't uncommented them yet... the only thing i can think of is that Automatix might have installed a strange version as i used that originally to install 0.95 on breezy, although that still doesnt explain why the versions of tcl/tk 8.5 in the forum thread aren't working...

I think i'll just stick with the official debs for now to avoid confusion and perhaps give tcl/tk a go at a later date, perhaps when the official repo's catch up to a newer version of amsn...

---

### Post by panurge77 on 2006-06-04
tcl8.5 is still alpha. those debs are alpha3. current version is alpha4. it should work fine, though, except for that sound problem with kernel 2.6

---

### Post by jamespi on 2006-06-04
I couldnt get asmn to launch after upgrading to dapper, and uninstalled tcl like it was suggested in here, that fixed it.

i seem to remember following an arnieboy howto to install amsn 0.95 manually, so thats probably why it didnt stay in synch with everything when i upgraded.

on a slight tangent, why the heck is amsn so horrifically ugly? it looks like a workbench 3 application. yuck.

if gaim would just let you video chat with msn users, that'd be much better. cant someone just lift the code out of amsn and splodge it into gaim? (i know thats a bit of a simplification)

---

### Post by panurge77 on 2006-06-04
It should not be so ugly if you have tcl/tk 8.5 and amsn from this deb here:
[http://201.220.118.143:8080/Ubuntu%2...neto1_i386.deb](http://201.220.118.143:8080/Ubuntu%2...neto1_i386.deb)
I think ubuntu's official deb use tcl/tk8.4 and as that, its really ugly.

---

### Post by jdavis on 2006-06-05
[QUOTE=panurge77]It should not be so ugly if you have tcl/tk 8.5 and amsn from this deb here:
[http://201.220.118.143:8080/Ubuntu%20-%20Dapper/amsn/amsn_0.95-2~neto1_i386.deb](http://201.220.118.143:8080/Ubuntu%20-%20Dapper/amsn/amsn_0.95-2~neto1_i386.deb)
I think ubuntu's official deb use tcl/tk8.4 and as that, its really ugly.[/QUOTE]

Yup, I can confirm Amsn works fine with tk/tcl 8.5 and the Deb above... and no uglyness!!! :D 
It was definately the 0.95-1 in the Dapper repo's that was incompatible with tk/tcl 8.5.

Cheers panurge77!

Jonathan

---

### Post by panurge77 on 2006-06-05
The cheers go to neto, who built the debs :p 
Now I only wish amsn .96 won't take long to be released :-\"

---

### Post by NeTo on 2006-06-07
University assigments have kept me out of all the Dapper fun :mad: Now is my time for revenge though, as I'm finally dist-upgrading. I will hopefully then package the newer Tcl/Tk versions, along with a proper guide for aMsn in Dapper.

I'm looking forward to set up a repository this time though, as I will soon have Breezy and Dapper packages of all sorts scattered everywhere. I wonder how a debian repo is set up; well at least that should keep me entertained during the upgrade process :p

---

### Post by panurge77 on 2006-06-07
I'm glad to hear all that, neto. Welcome back

---

### Post by Garyu on 2006-06-09
humm... link broken? I can't download amsn from the link you provided last for tcl/tk 8.5?

EDIT:
No worries, the 0.95-3 version for Ubuntu can be found from the aMSN site:
[http://prdownloads.sourceforge.net/amsn/amsn_0.95-3.ubuntu.deb](http://prdownloads.sourceforge.net/amsn/amsn_0.95-3.ubuntu.deb)

---

### Post by OrganicPanda on 2006-06-09
how come 95-3 still doesent include support for personal messages, is there a guide availble for doing this svn stylee so i can regain that feature??

---

