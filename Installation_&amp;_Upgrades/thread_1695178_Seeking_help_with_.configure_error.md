---
title: "Seeking help with ./configure error"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by Uintij on 2011-02-25
Hi, I hope someone can help me with my problem... any help would be greatly appreciated.

Last week I downloaded the OpenOffice SDK from Synaptic.  The SDK was downloaded into the correct subdirectory under usr/lib/openoffice/Basis3.2/sdk.  The basic problem I have is that running ./configure from within the sdk folder does not work.  Here is the list of current files within sdk:
> 
[code]michael@michael-desktop:/usr/lib/openoffice/basis3.2/sdk$ ls
bin[COLOR=Blue]           configure.pl[/COLOR]  include         setsdkenv_unix.csh     settings
classes       docs          index.html      setsdkenv_unix.csh.in
config.guess  examples      lib             setsdkenv_unix.sh
config.sub    idl           setsdkenv_unix  setsdkenv_unix.sh.in
[code]

When I type ./configure from within the directory,  it states:  

> [code]michael@michael-desktop:/usr/lib/openoffice/basis3.2/sdk$ ./configure
bash: ./configure: No such file or directory
[code]

I realize that the only configure file in there is a Perl file... but what am I missing?  I am relatively new to this, sorry if this was a question that belonged in Beginner Talk.

Thanks in advance for any help,

---

### Post by Uintij on 2011-02-25
Never mind, I cat-ed the  setsdkenvunix.csh file.  Found the answer... just needed to run setsdkenvunix.  Thanks anyway!

---

