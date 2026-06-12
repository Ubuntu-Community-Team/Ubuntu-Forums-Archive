---
title: "problem install on sun t2000"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by hadi on 2006-06-25
Dear All , 
          I just try install ubuntu on new box sun machine (sparc procesor), start from boot cd until configure ip working fine , but after that all instalation cannot continu ( like hang) .
         With same cd also , i try install on sun U5 with ide disk , there no problem  
until finish instalation ( very fast)
         [COLOR="Blue"]FYI , sun t2000 use sata disk[/COLOR] , is it possible problem the ubuntu cd instalation dont have the driver for sata disk ?
        Please Advise me when anyone have solution for my case .


thanks

hadi

---

### Post by Kelerion on 2006-06-28
[QUOTE=hadi]Dear All , 
          I just try install ubuntu on new box sun machine (sparc procesor), start from boot cd until configure ip working fine , but after that all instalation cannot continu ( like hang) .
         With same cd also , i try install on sun U5 with ide disk , there no problem  
until finish instalation ( very fast)
         [COLOR="Blue"]FYI , sun t2000 use sata disk[/COLOR] , is it possible problem the ubuntu cd instalation dont have the driver for sata disk ?
        Please Advise me when anyone have solution for my case .


thanks

hadi[/QUOTE]

Hi there..

Did you get around this? I just recieved a T2000 yesterday and am having the same problem.

The installer gets through the first initial stages and then freezes when you get to the partition part of the install.

Anyone any ideas on how to proceed?

Thanks

Kel

---

### Post by peterjenkins on 2006-08-14
I spent several days on this one :-(

I think it happens because the installer can't find any suitable kernel modules to detect the disk contoller. Having looked at the logs it does find some kernel modules but seems to fail when checking the signatures because it can't connect to the internet.

So ... you need to make sure the installer can connect to the internet even if you've downloaded the CD image and shared it from a local machine. I hadn't realised the proxy config needs an http:// in front of it, once I'd done that the installer got a little bit further then starting complaining about missing packages. In the end I just decided to do a full install over the net. Its not ideal, but it got it working.

In general the Ubuntu distibution seems rather too home user focused (no supprise really being its based on Debian). I've spent way to long trying to set up netboot environment, and I do this sort of thing with Redhat, SUsE and Solaris fairly often.

Pete.

---

### Post by dirkw on 2006-10-25
Hi there,

as far as your installation problems are concerned: The internal disks are SAS disk, on newer h/w revisions the controller moved onboard. Perhaps Sun and Ubuntu should have talked about it, made an update of the kernel, document it and just not let run people into their misery.

I do not understand why Ubuntu says Dapper Drake is "certified" on T2000. Daper Drake runs fine on x86, but on the T2000 it appeared to me not even having beta status. I was under the impression that my loaner was a brand new system, but as I learnt in this forum the new hardware must have been available in June already. What has gone wrong here?

Sorry for my harsh words, but I've wasted^Wspent too much time for the install and it was just aggravating. The second worst bug is that Dapper Drake doesn't seem to know nothing about ZFS. It just presented the pool I created before under Solaris as free disk space. This is asking for trouble!

More on my experience is at [http://drwetter.org/coolthreads/t2000.Ubuntu_vs_Solaris10.html](http://drwetter.org/coolthreads/t2000.Ubuntu_vs_Solaris10.html)

I've not personally tested it but it is said, that the soon-to-be-released Edgy Eft is better and at least addresses the problem regarding the disk controller's new version.


Cheers,
       Dirk

---

