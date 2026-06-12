---
title: "[SOLVED] URGENT 8.10 - Where has g77 gone"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by zenkaon on 2008-10-31
Hello,

Just upgraded to 8.10 and it went fine....but I really do need the fortran compiler g77...as in I REALLY need it within the next few hours.

Please help.

---

### Post by zenkaon on 2008-10-31
not got an answer yet...really need to compile fortran code tonight.

Posting this just to stop me falling of the forum 1st page.

---

### Post by lavinog on 2008-10-31
does this not work?
```
sudo apt-get install g77
```

What repositories do you have enabled?

what happens when you type g77? (in hardy if it isn't installed it would tell you what package is needed.)

Sorry I don't have 8.10 installed yet...just thought I'd try and help.
As a last resort you could squeeze in a small partition (2gigs should be enough) and install hardy server on it to get g77 on that for the time being.

---

### Post by swhit on 2008-10-31
I've enabled all repositories in the preferences of synaptic, and can't find g77 either.

---

### Post by zenkaon on 2008-10-31
g77 is NOT in any Intrepid repository - This is dreadful. There is no reason why I can't write fortran forever (I do speak other languages but you show me a C++ library that does complex integration....and then re-write my big nasty formula):(

Luckily, I have a 8.04 machine around and can login it and do my work there.

What's worse is that *** network manager in 8.10 is totally fcuked and wont let me connect either wired or wireless!!! the 3G is the only thing that does work.

I CAN get a dhcp address by typing
```
sudo dhclient eth0
```
and then log into the machine which has got g77 on it.

Not using the 8.04 machine locally as I'm also watching star trek on xawtv (virgin 1), and bond is on later....

Really regretting doing the upgrade....they had better get network manager sorted FAST, and then please please please put g77 back into the repositories.

---

### Post by lavinog on 2008-10-31
Check out this thread:
[http://ubuntuforums.org/showthread.php?t=964670](http://ubuntuforums.org/showthread.php?t=964670)

---

### Post by zenkaon on 2008-10-31
Been to that thread, dependency nightmare....exactly why I switched from red hat.

Canonical need to get their act in gear and:
a) Fit network manager as it is fcuked - see a lot of people with troubles
b) put g77 in the repositories 

g77 I can cope with, but nm NEEDS to be fixed by Monday morning latest.

---

### Post by sephora on 2008-11-01
Hi!

You can use ifort instead of g77. This is the Intel Fortran compiler, you can download it from the web page, it's free (for students, I think) and the installation is easy.

I still have problems with g77. I use Raster3D, a program for molecular graphics and I can't install it because of this trouble with g77 and the repositories.

This is somehow stupid....


Greetings

---

### Post by wgrant on 2008-11-01
gfortran is the replacement for g77.

Also, please watch your language.

---

### Post by fermier on 2008-11-01
> **wgrant said:**
> gfortran is the replacement for g77.



Thank you for this information.  It has been for some time that there have been threats that g77 will be completely replaced by gfortran.  Is this now the case and has g77 been discontinued as a package in the Ubuntu set of standard packages?
Also, the reason why it has been only a threat till now is because gfortran (claiming to be a fortran 95 compiler) was never quite complete (neither was g77 actually, but that is another matter).  Is gfortran now complete, i.e. all the fortran 95 standard functions been implemented?  I guess I can look this up myself, but it would be good to have the confirmation by someone who knows.
One would need some additional libraries to go with this and I was looking at those available in the package list, but I am not sure which one's would really be required...  Sigh so much to learn and read, while old g77 was such a comfortable shoe...

l8r

---

### Post by zenkaon on 2008-11-01
Hi wgrant,

thanks for that, I can now compile my fortran code. The results appear to be similar to what I get with g77. I'm happy now.

Sorry about the language, posting when drunk again....but what I said about network manager is true, if a little non-descript.

To summarise, the solution for g77 is to use gfortran

---

### Post by horvathd on 2008-11-09
I solved this problem with adding the hardy's univese repositories to my source.list. This way I could install g77 with aptitude, while gcc was downgraded to 3.4.6-6, but now it's working.

---

### Post by jalirious on 2008-12-15
Have installed both gfortran and ifort (intel fortran, l_cprof_p_11.0.074_ia32) in intrepid, kernel 2.6.27-9.

Tip:

in your ~/.bashrc put in 

if [ -f /opt/intel/Compiler/11.0/074/bin/ia32/ifortvars_ia32.sh ]; then
    . /opt/intel/Compiler/11.0/074/bin/ia32/ifortvars_ia32.sh
fi


************

Anyway, I find that gfortran can run some code that only intel fortran (not g77) could previously run, so despite change = arrgh for some, it's a step in the right direction.

If you still need intel fortran then I had to add

[for sure]
libstdc++5  {symbolic link to later version didn't work}

[maybe as well(?)]
f2c,gfortran4.3-multilib,fort77,libf2c2

---

### Post by zelrikriando on 2009-01-21
I cannot make ifort work, gfortran is not the answer for me. I want g77.

---

### Post by santana on 2009-01-30
> **wgrant said:**
> gfortran is the replacement for g77.

g77 will no longer be needed when gfortran can compile successfully g77 code, which is not currently the case. Anyone reading this post should make noise because it's not acceptable to take g77 out of the package repo.

---

### Post by mwparis on 2009-02-05
> **santana said:**
> g77 will no longer be needed when gfortran can compile successfully g77 code, which is not currently the case. Anyone reading this post should make noise because it's not acceptable to take g77 out of the package repo.

I'll echo this sentiment. There's a lot of legacy code out there which relies on g77. Is gfortran back compatible?

Why is this marked [SOLVED]?

---

### Post by AWittyUserName on 2009-02-21
> **santana said:**
> g77 will no longer be needed when gfortran can compile successfully g77 code, which is not currently the case. Anyone reading this post should make noise because it's not acceptable to take g77 out of the package repo.

Add me to the list of users inconvenienced by this.
I got it working by following the instructions here (adding Gutsy repo, downgrading several packages, locking versions).  Now I cannot take advantage of "Mark All Updrades" in Synaptic because it will undo some of my work.

I need g77.  Just in case it is not clear: there are still software projects in Fortran77 that are in their maintenance phase.  g77 and gfortran are not interchangeable, and ifort has a different license.

---

### Post by cariboo on 2009-02-21
I would suggest creating a bug [here]("http://bugs.launchpad.net/"). There were plans to drop aptitude from the Intrepid, I created a bug and after much deliberation, it was included in the next alpha release. 

I see it is still available in debian etch, so there should be no reason not to include it.

Jim

---

### Post by guayca on 2009-03-20
[QUOTE=wgrant;6078532]gfortran is the replacement for g77.

Unfortunately, gfortran doesn't compile fortran77 with block data. I've been looking for a fortran77 compiler that actually works in intrepid and I'm about to install 8.04. 

I totally understand the salty language use. I cannot do my work either now because of this. 

I found an interesting thread here :
[http://www.fluka.org/FLUKA/web_archive/earchive/new-fluka-discuss/2091.html](http://www.fluka.org/FLUKA/web_archive/earchive/new-fluka-discuss/2091.html)
But doesn't work for me: I get an error when adding the repositories.

---

### Post by karim.rahim on 2009-05-11
Hi,

First to WGRANT. 

If I may say gfortran does not fully replace g77. One can develop code for gfortran but what about the legacy code? Does everyone have to go through it all to get it to compile. That is not a realistic senario. I suspect people will use g77 for some time to come. 

I ask humbly that g77 continue to be supported in Ubuntu. It can co exist with newer versions of gfortran.

Hardy will be supported for a while so there is no imediate problem, but I ask that you reconsider supporting legacy g77 in your next long term release.

I am able to run g77 in Intrepid using hardy packages--g77 coexists with gfortran 

I added the following to /etc/apt/sources.list:

## added for g77 and g++-4.3
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates main universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates main universe

then
sudo aptitude update
sudo aptitude install g++-3.4 g77

I'm assuming this will work in jackalope but I haven't tried it. 

I used package manager to keep the following 4 packages back (hardy versions) with the package manager (This may not be required?)
cpp-3.4
gcc-3.4
gcc-3.4-base
libg2c0

I've done the above in a 64 bit and a 32 bit chroot environment.

Thanks,
Karim

---

### Post by lavinog on 2009-05-11
> **cariboo907 said:**
> There were plans to drop aptitude from the Intrepid, I created a bug and after much deliberation, it was included in the next alpha release. 

I see it is still available in debian etch, so there should be no reason not to include it.

Jim

Wow, I recently started getting in the habit of using aptitude instead of apt-get.
Why get rid of it anyway? It doesn't take much space.

---

