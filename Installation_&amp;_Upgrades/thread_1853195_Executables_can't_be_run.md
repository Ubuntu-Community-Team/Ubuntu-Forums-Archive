---
title: "Executables can't be run?"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by xtracool_protik on 2011-10-01
Hi,
 I've downloaded games from HIB4 when I try to run them
 for e.g.:

```
chmod +x frozensynapse-1-linux-bin
./frozensynapse-1-linux-bin

```

It gives an error:
```

bash: ./frozensynapse-1-linux-bin: No such file or directory

```

Any ideas?
BTW its fresh installation of Ubuntu11.10 64 bit

---

### Post by MAFoElffen on 2011-10-01
> **xtracool_protik said:**
> Hi,
 I've downloaded games from HIB4 when I try to run them
 for e.g.:

```
chmod +x frozensynapse-1-linux-bin
./frozensynapse-1-linux-bin

```It gives an error:
```

bash: ./frozensynapse-1-linux-bin: No such file or directory

```Any ideas?
BTW its fresh installation of Ubuntu11.10 64 bit
Look in nautilus > properties and see "if" it is marked as "executable." or:
```

ls -l ./frozensynapse-1-linux-bin

```

---

### Post by Hakunka-Matata on 2011-10-01
I'm on Debian Squeeze 32-bit.
Thanks in advance.                                                                [jampe]("http://forums.mode7games.com/memberlist.php?mode=viewprofile&u=12280&sid=f76aed8edcbb284a0c4abc4f8bc9f2f8")              **Posts:** 2**Joined:** Thu Sep 29, 2011 9:50 am               [Top]("http://forums.mode7games.com/viewtopic.php?t=3645#wrap")
                                                                         **[Re: Linux binary cannot execute]("http://forums.mode7games.com/viewtopic.php?t=3645#p14214")**

             [[IMG]http://forums.mode7games.com/styles/prosilver/imageset/icon_post_target.gif[/IMG]]("http://forums.mode7games.com/viewtopic.php?p=14214&sid=f76aed8edcbb284a0c4abc4f8bc9f2f8#p14214")by **[sebek]("http://forums.mode7games.com/memberlist.php?mode=viewprofile&u=12281&sid=f76aed8edcbb284a0c4abc4f8bc9f2f8")** » Thu Sep 29, 2011 10:39 am 
                            $ chmod +x ./frozensynapse-1-linux-bin
$ ./frozensynapse-1-linux-bin
                        
                                        [sebek]("http://forums.mode7games.com/memberlist.php?mode=viewprofile&u=12281&sid=f76aed8edcbb284a0c4abc4f8bc9f2f8")              **Posts:** 1**Joined:** Thu Sep 29, 2011 10:37 am               [Top]("http://forums.mode7games.com/viewtopic.php?t=3645#wrap")
          
     
                                                          **[Re: Linux binary cannot execute]("http://forums.mode7games.com/viewtopic.php?t=3645#p14216")**

             [[IMG]http://forums.mode7games.com/styles/prosilver/imageset/icon_post_target.gif[/IMG]]("http://forums.mode7games.com/viewtopic.php?p=14216&sid=f76aed8edcbb284a0c4abc4f8bc9f2f8#p14216")by **[Gigadoc 2]("http://forums.mode7games.com/memberlist.php?mode=viewprofile&u=12264&sid=f76aed8edcbb284a0c4abc4f8bc9f2f8")** » Thu Sep 29, 2011 11:20 am 
                            The commands sebek posted will first grant you  the right to run the executable, and than starts it. (Sebek: you should  add this information, in case a newbie reads this and doesn't know what  it does)
                        
                                        [Gigadoc 2]("http://forums.mode7games.com/memberlist.php?mode=viewprofile&u=12264&sid=f76aed8edcbb284a0c4abc4f8bc9f2f8")              **Posts:** 8**Joined:** Wed Sep 28, 2011 8:14 pm                                               [Top]("http://forums.mode7games.com/viewtopic.php?t=3645#wrap")
          
     
                                                          **[Re: Linux binary cannot execute]("http://forums.mode7games.com/viewtopic.php?t=3645#p14218")**

             [[IMG]http://forums.mode7games.com/styles/prosilver/imageset/icon_post_target.gif[/IMG]]("http://forums.mode7games.com/viewtopic.php?p=14218&sid=f76aed8edcbb284a0c4abc4f8bc9f2f8#p14218")by **[jampe]("http://forums.mode7games.com/memberlist.php?mode=viewprofile&u=12280&sid=f76aed8edcbb284a0c4abc4f8bc9f2f8")** » Thu Sep 29, 2011 11:26 am [INDENT]sebek wrote:$ chmod +x ./frozensynapse-1-linux-bin
$ ./frozensynapse-1-linux-bin
[/INDENT]D'oh. Of course. I must have subconsciously huffed a bucket of arsenic before posting that thread.

---

### Post by xtracool_protik on 2011-10-01
Thanks for replies guys,
 But if you have not seen I've the file marked executable with chmod +x.

 Anyways I've narrowed down the issue:

 I'm using 64bit Ubuntu 11.10 and the game is 32 bit.

 I used ia-32 libs package to get installation started.
 But it aborts saying libglade.2.0.so.0: ELFCLASS64.

 So I installed getlibs and got required 32 bit library though I had to copy it to /usr/lib instead of /usr/lib32 manually.

 That installs the game. But now there are way too many dependencies as it seems (same ELFCLASS64). I tried using getlibs on game binary itself but didn't return anything useful.

 So yea at the end I got game installed but can't run as of now

---

### Post by MAFoElffen on 2011-10-01
> **xtracool_protik said:**
> Thanks for replies guys,
 But if you have not seen I've the file marked executable with chmod +x.

 Anyways I've narrowed down the issue:

 I'm using 64bit Ubuntu 11.10 and the game is 32 bit.

 I used ia-32 libs package to get installation started.
 But it aborts saying libglade.2.0.so.0: ELFCLASS64.

 So I installed getlibs and got required 32 bit library though I had to copy it to /usr/lib instead of /usr/lib32 manually.

 That installs the game. But now there are way too many dependencies as it seems (same ELFCLASS64). I tried using getlibs on game binary itself but didn't return anything useful.

 So yeah at the end I got game installed but can't run as of nowSo it was a binary instead of a .deb package? If it was a .deb, there's ways to force a 32bit install on 64bit sys... I've installed games that way. But I never tried a 32bit binary on 64bit.  I'm lost on that one.

---

### Post by xtracool_protik on 2011-10-01
umm yes that is the error that I got
so I installed ia32 libs
Well after that installation aborted saying libglade:ELFCLASS64
so I installed getlibs and installed libglade.2.0.so.0
by default it was installed under /usr/lib32, I had to move it to /usr/lib to get installation completely working.

However thought installation is complete game can't start as there are plenty of ELFCLASS64 errors

---

### Post by MAFoElffen on 2011-10-01
> **xtracool_protik said:**
> Thanks for replies guys,
 But if you have not seen I've the file marked executable with chmod +x.

 Anyways I've narrowed down the issue:

 I'm using 64bit Ubuntu 11.10 and the game is 32 bit.

 I used ia-32 libs package to get installation started.
 But it aborts saying libglade.2.0.so.0: ELFCLASS64.

 So I installed getlibs and got required 32 bit library though I had to copy it to /usr/lib instead of /usr/lib32 manually.

 That installs the game. But now there are way too many dependencies as it seems (same ELFCLASS64). I tried using getlibs on game binary itself but didn't return anything useful.

 So yea at the end I got game installed but can't run as of nowso it was a binary in stead of a .deb package... If it was a .deb, there's ways to force a 32bit install on 64bit sys... But I never tried a 32bit binary on 32bit.  I'm lost on that one.  The error that gets me is that is says:
> ```
bash: ./frozensynapse-1-linux-bin: No such file or directory
```As if it could not find that file...
On researching this:
> Ubuntu x86-64 does not install the 32 bit compatible libraries, and fah5 is a 32 bit application. Installing the ia32-libs corrected the problem.> **ia32 shared libraries for use on amd64 and ia64 systems**
 
This package contains runtime libraries for the ia32/i386
architecture, configured for use on an amd64 or ia64 Debian system running
a 64-bit kernel.

EDIT-- I was late on this one...

---

### Post by MAFoElffen on 2011-10-01
> **xtracool_protik said:**
> umm yes that is the error that I got
so I installed ia32 libs
Well after that installation aborted saying libglade:ELFCLASS64
so I installed getlibs and installed libglade.2.0.so.0
by default it was installed under /usr/lib32, I had to move it to /usr/lib to get installation completely working.

However thought installation is complete game can't start as there are plenty of ELFCLASS64 errors
Wow... Well maybe someone else who knows how to debug elfclass32 and elfclass64 errors could jump in here to help.  I've never done that between the two.

---

### Post by xtracool_protik on 2011-10-02
ahh ok, I was wondering about the replies.
Anyways in any case thanks a bunch for quick responses :)

Hope someone have more experience installing 32bit stuff on 64bit systems or wait for game to be release in 64bit version.

---

