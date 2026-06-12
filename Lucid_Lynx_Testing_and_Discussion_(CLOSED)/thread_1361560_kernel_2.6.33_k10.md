---
title: "kernel 2.6.33 k10"
date: 2009-12-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pulpo69 on 2009-12-22
i read, that kernel 2.6.33 supports k10. so it's possible to see temperature of amd phenom cpu and fan rotation. is that true?

---

### Post by phillw on 2009-12-22
> **pulpo69 said:**
> i read, that kernel 2.6.33 supports k10. so it's possible to see temperature of amd phenom cpu and fan rotation. is that true?

> Hi Clemens, 
 On Tue, 24 Nov 2009 09:43:39 +0100, Clemens Ladisch wrote: 
 > This adds a driver for the internal temperature sensor of AMD Family 10h 
 > and 11h CPUs. 
 > Signed-off-by: Clemens Ladisch <clem[...]("http://groups.google.com/groups/unlock?_done=/group/linux.kernel/browse_thread/thread/cadbcb576e338fa3/51fa0897a95393cf%3Flnk%3Draot&msg=aa1b69638320fa76")@ladisch.de> 
 > --- 
 > v3: added 'force' parameter for CPUs with buggy sensor; more documentation 
 > v4: added max/crit values, other changes suggested by Jean Delvare 
 
>  Documentation/hwmon/k10temp |   60 +++++++++ 
 >  drivers/hwmon/Kconfig       |   12 + 
 >  drivers/hwmon/Makefile      |    1 
 >  drivers/hwmon/k10temp.c     |  197 ++++++++++++++++++++++++++++++++ 
 >  4 files changed, 270 insertions(+) 
 


Looks alright to me. 
 Acked-by: Jean Delvare <kh[...]("http://groups.google.com/groups/unlock?_done=/group/linux.kernel/browse_thread/thread/cadbcb576e338fa3/51fa0897a95393cf%3Flnk%3Draot&msg=aa1b69638320fa76")@linux-fr.org> 
 
If this is OK with you, I can add this patch to my hwmon tree and 
 schedule it for merge in kernel 2.6.33. 
 


> On Fri, 27 Nov 2009 16:43:33 +0100 Jean Delvare <kh[...]("http://groups.google.com/groups/unlock?_done=/group/linux.kernel/browse_thread/thread/cadbcb576e338fa3/51fa0897a95393cf%3Flnk%3Draot&msg=51fa0897a95393cf")@linux-fr.org> wrote: 
 [URL="http://groups.google.com/group/linux.kernel/browse_thread/thread/cadbcb576e338fa3/51fa0897a95393cf?hide_quotes=no#msg_51fa0897a95393cf"]- Hide quoted text -
- Show quoted text -
[/URL]
> Hi Clemens, 
 > On Tue, 24 Nov 2009 09:43:39 +0100, Clemens Ladisch wrote: 
 > > This adds a driver for the internal temperature sensor of AMD Family 10h 
 > > and 11h CPUs. 
 
> > Signed-off-by: Clemens Ladisch <clem[...]("http://groups.google.com/groups/unlock?_done=/group/linux.kernel/browse_thread/thread/cadbcb576e338fa3/51fa0897a95393cf%3Flnk%3Draot&msg=51fa0897a95393cf")@ladisch.de> 
 > > --- 
 > > v3: added 'force' parameter for CPUs with buggy sensor; more documentation 
 > > v4: added max/crit values, other changes suggested by Jean Delvare 
 
> >  Documentation/hwmon/k10temp |   60 +++++++++ 
 > >  drivers/hwmon/Kconfig       |   12 + 
 > >  drivers/hwmon/Makefile      |    1 
 > >  drivers/hwmon/k10temp.c     |  197 ++++++++++++++++++++++++++++++++ 
 > >  4 files changed, 270 insertions(+) 
 
> Looks alright to me. 
 
> Acked-by: Jean Delvare <kh[...]("http://groups.google.com/groups/unlock?_done=/group/linux.kernel/browse_thread/thread/cadbcb576e338fa3/51fa0897a95393cf%3Flnk%3Draot&msg=51fa0897a95393cf")@linux-fr.org> 
 
> If this is OK with you, I can add this patch to my hwmon tree and 
 > schedule it for merge in kernel 2.6.33. 
 


Sounds good, thanks. 
 

I'd say that has been added :-)

Source: [http://groups.google.com/group/linux.kernel/browse_thread/thread/cadbcb576e338fa3/51fa0897a95393cf?lnk=raot](http://groups.google.com/group/linux.kernel/browse_thread/thread/cadbcb576e338fa3/51fa0897a95393cf?lnk=raot)

Phill.

---

### Post by pulpo69 on 2009-12-22
thanks phillw. i hope this make it into kernel 2.6.33 and in lucid.

---

### Post by RAOF on 2009-12-23
> **pulpo69 said:**
> thanks phillw. i hope this make it into kernel 2.6.33 and in lucid.

Well, it's not going to make it into Lucid without someone doing something; Lucid's going to have a 2.6.32 based kernel.

Filing a bug against the 'linux' package might be productive; more so if you can check how much needs to change to support k10 temperature sensors - it looks like it's just added code, which may be easy to just drop into our current kernel.

---

### Post by lean on 2009-12-23
The 2.6.33 is already RC1, why wouldn't it make it for lucid? Any change in policy regarding kernels for a LTS?
The schedule says february 18th. for feature freeze, plenty of time to get 2.6.33 released.

Update: 2.6.32 it is... [https://wiki.ubuntu.com/specs/KernelLucidKernelDecision](https://wiki.ubuntu.com/specs/KernelLucidKernelDecision)

---

### Post by pulpo69 on 2009-12-24
i filed a bug report today, i hope i did it the right way.

---

### Post by eyelessfade on 2009-12-24
2.6.33-rc2 as of today. Can't see any problems to get .33 into lucid, other then just be stubborn :) ~4 months must be plenty of time to have it LTS stable




On the other side 2.6.32 did go all the way to -rc6, so it might be to late. If it stalls beyond January I would also stick with .32 perhaps with a few backports from 2.6.33?

---

### Post by Eclipse. on 2009-12-24
> **eyelessfade said:**
> 2.6.33-rc2 as of today. Can't see any problems to get .33 into lucid, other then just be stubborn :) ~4 months must be plenty of time to have it LTS stable




On the other side 2.6.32 did go all the way to -rc6, so it might be to late. If it stalls beyond January I would also stick with .32 perhaps with a few backports from 2.6.33?

The devs know best, its not thing to do with them being stubborn.2.6.32 is the correct decision, in the past late kernel changes have been made and its caused major regressions in releases.We can backport code from .33 into .32 as we want and there is plans to backport later kernels into lucid in the future.A stable kernel that just works and that id as bug free as possible is extremely important for lucid.

---

### Post by falconindy on 2009-12-24
> **eyelessfade said:**
> 2.6.33-rc2 as of today. Can't see any problems to get .33 into lucid, other then just be stubborn :) ~4 months must be plenty of time to have it LTS stable




On the other side 2.6.32 did go all the way to -rc6, so it might be to late. If it stalls beyond January I would also stick with .32 perhaps with a few backports from 2.6.33?
rc8, actually. An RC in kernel land isn't the same persay as an RC of Ubuntu. Consider the early RCs to be the alphas and betas, if you will.

[http://lkml.org/lkml/2009/12/3/11](http://lkml.org/lkml/2009/12/3/11)

Even using 2.6.32 is a gutsy move, given the regressions with Ext4 performance and network driver anomalies cropping up. 2.6.33 doesn't look to be all that huge as far as new features aside from nouveau and take 2 at radeon support.

---

### Post by InfinityCircuit on 2009-12-25
> **eyelessfade said:**
> 2.6.33-rc2 as of today. Can't see any problems to get .33 into lucid, other then just be stubborn :) ~4 months must be plenty of time to have it LTS stable




On the other side 2.6.32 did go all the way to -rc6, so it might be to late. If it stalls beyond January I would also stick with .32 perhaps with a few backports from 2.6.33?

It's not about being stubborn, it's about being smart.

[http://lists.debian.org/debian-devel/2009/12/msg00649.html](http://lists.debian.org/debian-devel/2009/12/msg00649.html)

[https://wiki.ubuntu.com/specs/KernelLucidKernelDecision](https://wiki.ubuntu.com/specs/KernelLucidKernelDecision)

---

### Post by pulpo69 on 2009-12-27
how to install this driver for k10 thermal sensors?

[http://khali.linux-fr.org/devel/misc/k10temp/](http://khali.linux-fr.org/devel/misc/k10temp/)

found on this page [http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices)

---

### Post by CHaoSlayeR on 2010-03-06
This is really sad:

I'm just using the Lucid Alpha 3 with the 2.6.33 mainline kernel which finally (should) have all I need:

- k10temp kernel module
- IT8720F sensors support
- AMD Radeon HD4770 (RV740) fix

So I just installed it and everything was fine but the k10temp (although included in the source) is not built into the mainline kernel. So to get this you will have to download the source and compile it yourself.

C]-[aoZ

---

