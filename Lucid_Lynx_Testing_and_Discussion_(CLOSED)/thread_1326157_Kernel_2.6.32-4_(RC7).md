---
title: "Kernel 2.6.32-4 (RC7)"
date: 2009-11-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by plun on 2009-11-14
Works just fine with my test  partition....

> linux (2.6.32-4.5) lucid; urgency=low

  [ Andy Whitcroft ]

  * [Config] SERIO_LIBPS2 and SERIO_I8042 must match
  * [B]rebase to v2.6.32-rc7
  * resync with Karmic proposed
[/B]
  [ John Johansen ]

  * SAUCE: AppArmor: Fix oops after profile removal
    - LP: #475619
  * SAUCE: AppArmor: Fix Oops when in apparmor_bprm_set_creds
    - LP: #437258
  * SAUCE: AppArmor: Fix cap audit_caching preemption disabling
    - LP: #479102
  * SAUCE: AppArmor: Fix refcounting bug causing leak of creds
    - LP: #479115
  * SAUCE: AppArmor: Fix oops there is no tracer and doing unsafe
    transition.
    - LP: #480112

  [ Ubuntu Changes ]

  * resync with Karmic proposed (ddbc670a86a3dee18541a3734149f250ff307adf)

  [ Upstream Kernel Changes ]

  * rebase to v2.6.32-rc7

[https://lists.ubuntu.com/archives/lucid-changes/2009-November/000452.html](https://lists.ubuntu.com/archives/lucid-changes/2009-November/000452.html)




About RC7

[http://lkml.org/lkml/2009/11/12/409](http://lkml.org/lkml/2009/11/12/409)

--

---

### Post by jmmL on 2009-11-14
Does the re-sync with karmic-proposed now mean that the lucid kernel has support for ureadahead?

---

### Post by plun on 2009-11-14
> **jmmL said:**
> Does the re-sync with karmic-proposed now mean that the lucid kernel has support for ureadahead?

Yes as I understands it, my xsplash is just a few seconds..

All details here:
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=summary)


--

---

### Post by scradock on 2009-11-14
> **plun said:**
> Yes as I understands it, my xsplash is just a few seconds..

All details here:
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=summary)


--
Does anyone know when ureadahead will be in the lucid repos? I have the ..32-4 (rc7) kernel, but ureadahead is not offered yet. The boot-up sequence is still a mess, so I'm eagerly awaiting the next step....

---

### Post by jppr on 2009-11-14
> **scradock said:**
> Does anyone know when ureadahead will be in the lucid repos? I have the ..32-4 (rc7) kernel, but ureadahead is not offered yet. The boot-up sequence is still a mess, so I'm eagerly awaiting the next step....

It is repos. i had just re-install karmic and update again lucid. this is now as fresh / clean installation = )

---

### Post by ranch hand on 2009-11-14
Well, I feel slighted.  It is not in my synaptic at all.

---

### Post by jppr on 2009-11-14
i dont know how but myself, that package is in the synaptic ;)
ureadahead 0.90.3-2

---

### Post by scradock on 2009-11-14
> **jppr said:**
> i dont know how but myself, that package is in the synaptic ;)
ureadahead 0.90.3-2
Did you add the ppa to your sources? I haven't....and like ranch hand I don't have ureadahead in synaptic.

---

### Post by jppr on 2009-11-14
No any PPA systems, like i said i must do re-install karmic and when i updated back lucid, it was there in repos.
there is both rheadahead and ureadahead.

---

### Post by ranch hand on 2009-11-14
Discrimination, Ubuntu hates me.

---

### Post by scradock on 2009-11-14
> **jppr said:**
> No any PPA systems, like i said i must do re-install karmic and when i updated back lucid, it was there in repos.
there is both rheadahead and ureadahead.
Ah yes, ureadahead is in the karmic repos.

Now I can repeat my question - does anyone know when it will be available in the lucid repos, so we don't only get it when upgrading from karmic?

---

### Post by wnelson on 2009-11-14
ppa:ubuntu-boot/ppa is the current PPA for ureadahead I use it with no problems at all, even with 2.6.32-4.

---

### Post by scradock on 2009-11-14
> **wnelson said:**
> ppa:ubuntu-boot/ppa is the current PPA for ureadahead I use it with no problems at all, even with 2.6.32-4.
Thanks. I tried just installing ureadahead from my karmic apt archives. It insisted that I remove sreadahead first (the real one, version 1.50 or something), but after that it installed with no problem. Now I have booted a couple of times it does seem to reduce the boot time a bit.

Still seeing the mish-mash of grub loading | grub menu | console boot messages | switch to usplash | fall out of usplash with console messages again | black screen while xsplash starts | xsplash | at last the desktop starts to load bit by bit. I set gdm to login automatically, so there's no shuffling about for the greeter. It's still a mess, as far as I'm concerned.

The part that seemed shorter was indeed the xsplash section.

---

### Post by MacUntu on 2009-11-14
-- deleted --

---

### Post by scradock on 2009-11-14
> **MacUntu said:**
> You still need to boot the kernel from the PPA to generate the pack file which you then can use with newer kernels.
That's what I was afraid of - does anyone know when the whole caboodle (ureadahead and a kernel that does the pack-file generation) will be available in the lucid repos?

---

### Post by Starks on 2009-11-14
Quick question. Will Lucid be 2.6.33 or 2.6.34?

---

### Post by baizon on 2009-11-15
> **Starks said:**
> Quick question. Will Lucid be 2.6.33 or 2.6.34?

It will be the 2.6.34 kernel.
Source: [http://wiki.ubuntuusers.de/Lucid_Lynx]("http://wiki.ubuntuusers.de/Lucid_Lynx")
...or [http://www.phoronix.com/scan.php?page=news_item&px=NzU0NQ]("http://www.phoronix.com/scan.php?page=news_item&px=NzU0NQ")

---

### Post by MacUntu on 2009-11-15
> **baizon said:**
> It will be

Not yet decided so that's plain wrong.

> **baizon said:**
> the 2.6.34 kernel.

I bet not, because a. kernel freeze is mid-march, and b. it's not even mentioned here: [https://wiki.ubuntu.com/specs/KernelLucidKernelDecision](https://wiki.ubuntu.com/specs/KernelLucidKernelDecision)

---

### Post by jmmL on 2009-11-15
> **MacUntu said:**
> I bet not, because a. kernel freeze is mid-march, and b. it's not even mentioned here: [https://wiki.ubuntu.com/specs/KernelLucidKernelDecision](https://wiki.ubuntu.com/specs/KernelLucidKernelDecision)

That page suggests that 2.6.33 will be out by the end of Feb2010, which seems reasonable. That would put the first -rc of .34 arriving just as the kernel freeze comes up on 11th March - there's no way 2.6.34 will be in lucid.

---

### Post by hikaricore on 2009-11-15
Anyone besides me having NFS trouble even with the latest kernel?

---

### Post by scradock on 2009-11-15
> **MacUntu said:**
> You still need to boot the kernel from the PPA to generate the pack file which you then can use with newer kernels.
Actually it seems this is no longer correct, though I believe it was until the new kernel came out. I have a valid pack file (in /var/lib/ureadahead, as specified by "man ureadahead"), and it appears to be generated from the first boot with the ..32-4 (rc7) kernel. I have never used the kernel from the ubuntu-boot ppa.

So we can switch to using ureadahead simply by removing sreadahead and installing ureadahead from the karmic repo (or a karmic apt cache), as I have done.

BTW, the output of "ureadahead --dump" shows the list of files loaded by ureadahead and the memort blocks allocated for them. Most impressive - thanks a lot, James Scott Remnant!

---

### Post by MacUntu on 2009-11-15
You are right, I didn't get a new pack file because I somehow managed to remove ureadahead. *facepalm*

---

### Post by ranch hand on 2009-11-15
This is interesting because I most certainly do not have a /var/lib/ureadahead at all.  I am not hooked to any ppa.  I am up to date.

---

### Post by scradock on 2009-11-15
> **ranch hand said:**
> This is interesting because I most certainly do not have a /var/lib/ureadahead at all.  I am not hooked to any ppa.  I am up to date.
That would be correct. You will have to remove sreadahead and install ureadahead, then boot once using rc7 kernel. After that, the /var/lib/ureadahead/pack file should be present and ureadahead can do its magic......

---

### Post by xtoudi on 2009-11-16
> **scradock said:**
> That would be correct. You will have to remove sreadahead and install ureadahead, then boot once using rc7 kernel. After that, the /var/lib/ureadahead/pack file should be present and ureadahead can do its magic......

OK - what about if I still need an older kernels (2.6.31.x_generic, 2.6.31.some_my_versions)?? Should I permanently remove sreadahead in thaht case?? If ureadahead completely replecaces sreadahead?

And if I'm trying remove sreadahead apt-get is also removing ubuntu-dekstop :-)

---

### Post by jppr on 2009-11-16
I have 2.6.32-4.5 kernel and both sreadahead and ureadahead without any problem

 cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)"

---

### Post by xtoudi on 2009-11-16
> **jppr said:**
> I have 2.6.32-4.5 kernel and both sreadahead and ureadahead without any problem

 cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)"

Yes I've got both of them too - my question is "Should I ...??" because **scradock** wrote: "You will have to remove sreadahead and install ureadahead ...".

I've got both of them - when I boot 2.6.31-14-generic (taken from boot PPA) then I've got /var/lib/ureadahead/pack.
When I boot any other kernel (including 2.6.32.rc7) there is no such pack file.

In other words:
 * booting from 2.6.31-14-generic (taken from boot PPA) generates pack file and uses ureadahead
 * booting from any other kernel uses sreadahead

So....should I remove sreadahead??

System: U9.10 x64

---

### Post by afv on 2009-11-16
> **xtoudi said:**
> Yes I've got both of them too - my question is "Should I ...??" because **scradock** wrote: "You will have to remove sreadahead and install ureadahead ...".

I've got both of them - when I boot 2.6.31-14-generic (taken from boot PPA) then I've got /var/lib/ureadahead/pack.
When I boot any other kernel (including 2.6.32.rc7) there is no such pack file.

In other words:
 * booting from 2.6.31-14-generic (taken from boot PPA) generates pack file and uses ureadahead
 * booting from any other kernel uses sreadahead

So....should I remove sreadahead??

System: U9.10 x64


The sreadahead package description [at lucid, at least] says:

"**Transitional package for ureadahead**
sreadahead has been replaced by ureadahead, this package ensures
that you are transitioned over and may be safely removed."

---

### Post by zika on 2009-11-16
> **afv said:**
> The sreadahead package description [at lucid, at least] says:

"**Transitional package for ureadahead**
sreadahead has been replaced by ureadahead, this package ensures
that you are transitioned over and may be safely removed."On my Lucid, upgraded a minute ago:```
sreadahead is a daemon that reads data sequential by use from
disk.  It does this by retrieving the read order (in timestamp
format) from an actual boot sequence and storing a list of data that
was read during that boot sequence in a flat database.

On the next boot this file can be used to load all the data described
in the database into memory and in order of use.

sreadahead requires a kernel patch included in the Ubuntu kernel.
```
Ureadahead is not visible in synaptic. I do not have ppa:ubuntu-boot enabled.

---

### Post by scradock on 2009-11-16
> **zika said:**
> On my Lucid, upgraded a minute ago:```
sreadahead is a daemon that reads data sequential by use from
disk.  It does this by retrieving the read order (in timestamp
format) from an actual boot sequence and storing a list of data that
was read during that boot sequence in a flat database.

On the next boot this file can be used to load all the data described
in the database into memory and in order of use.

sreadahead requires a kernel patch included in the Ubuntu kernel.
```
Ureadahead is not visible in synaptic. I do not have ppa:ubuntu-boot enabled.
That's why I asked my original question: Does anyone know when we shall get a package in lucid with the new ureadahead, and the sreadahead transitional package? At the moment ureadahead is only available in the karmic repos, or in the apt cache archive of a karmic install.

ubuntu-desktop is a fairly harmless meta-package - let it go and it will come back when something needs it. But make sure you have access to a ureadahead deb so that you can install that after removing sreadahead, before trying to boot again. I don't know what might happen (or not happen) if neither sreadahead or ureadahead was installed on boot - but even that should be possible. They are only there to speed up the boot process, and if neither is there there should be timeouts to allow the process to continue to completion......

---

### Post by scradock on 2009-11-16
> **xtoudi said:**
> Yes I've got both of them too - my question is "Should I ...??" because **scradock** wrote: "You will have to remove sreadahead and install ureadahead ...".

I've got both of them - when I boot 2.6.31-14-generic (taken from boot PPA) then I've got /var/lib/ureadahead/pack.
When I boot any other kernel (including 2.6.32.rc7) there is no such pack file.

In other words:
 * booting from 2.6.31-14-generic (taken from boot PPA) generates pack file and uses ureadahead
 * booting from any other kernel uses sreadahead

So....should I remove sreadahead??

System: U9.10 x64
What is the version number of sreadahead? The "old", working version is 0.5, or something; the new transitional version is 1:0.90.3-2 or something similar, like ureadahead. I had understood that if you once generated the pack file (using the ppa kernel) and then booted any kernel with the ureadahead patch in it (like ...32-4 (rc7)) it would pick up on the pack file and use it.

Or do you mean you are booting two different partitions with the different kernels?

---

### Post by xtoudi on 2009-11-16
> **scradock said:**
> What is the version number of sreadahead? The "old", working version is 0.5, or something; the new transitional version is 1:0.90.3-2 or something similar, like ureadahead. I had understood that if you once generated the pack file (using the ppa kernel) and then booted any kernel with the ureadahead patch in it (like ...32-4 (rc7)) it would pick up on the pack file and use it.

Or do you mean you are booting two different partitions with the different kernels?

sreadahead 1:0.90.3-1
ureadahead 0.90.3-1

I'm just not sure which kernel uses this pack file. This is one partition. One kernel is original Ubuntu 9.10 generic, one is mine, one is taken from bootPPA, and one is 2.6.32.rc7 .... and there are some my versions 2.6.32.rc7 (kernel.org with config taken from Ubuntu 2.6.32.rc7).
I know that this one from bootPPA uses /var/lib/ureadahead/pack. This is what I'm sure.

---

### Post by scradock on 2009-11-17
> **xtoudi said:**
> sreadahead 1:0.90.3-1
ureadahead 0.90.3-1

I'm just not sure which kernel uses this pack file. This is one partition. One kernel is original Ubuntu 9.10 generic, one is mine, one is taken from bootPPA, and one is 2.6.32.rc7 .... and there are some my versions 2.6.32.rc7 (kernel.org with config taken from Ubuntu 2.6.32.rc7).
I know that this one from bootPPA uses /var/lib/ureadahead/pack. This is what I'm sure.
OK, then all I can say is that with Lucid I have ureadahead 0.90.3-2, and no sreadahead installed. So it's possible to boot kernel 2.6.32-4 (rc7) that way. I have a pack file in /var/lib/ureadahead, and it seems to be used during boot. I'll try booting Lucid using an older kernel (2.6.31-14) and see what happens. It should NOT use ureadahead, and without sreadahead it may be slow to boot...

LATER.. Lucid boots fine with the 2.6.31-14 kernel, and /var/lib/ureadahead/pack is still present. 

"sudo ureadahead --dump" still gives the listing of files and memory blocks allocated as before. 

I don't see any reason why the pack file would be absent just because you boot with a different kernel - /var doesn't get wiped on each boot like /tmp does.

---

### Post by xtoudi on 2009-11-17
> **scradock said:**
> OK, then all I can say is that with Lucid I have ureadahead 0.90.3-2, and no sreadahead installed. So it's possible to boot kernel 2.6.32-4 (rc7) that way. I have a pack file in /var/lib/ureadahead, and it seems to be used during boot. I'll try booting Lucid using an older kernel (2.6.31-16) and see what happens. It should NOT use ureadahead, and without sreadahead it may be slow to boot...

But still removing sreadahead also removes ubuntu-desktop.

About "ubuntu-desktop" (Ubuntu 9.10):
[I]This package depends on all of the packages in the Ubuntu desktop system
It is also used to help ensure proper upgrades, so it is recommended that it not be removed.[/I]

EDIT:
pack file still present with booting other kernels- my mistake

---

### Post by afv on 2009-11-17
> **xtoudi said:**
> But still removing sreadahead also removes ubuntu-desktop.

About "ubuntu-desktop" (Ubuntu 9.10):
[I]This package depends on all of the packages in the Ubuntu desktop system
It is also used to help ensure proper upgrades, so it is recommended that it not be removed.[/I]

EDIT:
pack file still present with booting other kernels- my mistake


That's because ubuntu-desktop has sreadahead as dependency. You can remove it if you want, or stay with sreadahead that's just a transitional package.

If you remove ubuntu-desktop just check, time to time if, when you "want" to install it again, it wants to install new packages that you might need.

---

### Post by knarf on 2009-11-18
> **hikaricore said:**
> Anyone besides me having NFS trouble even with the latest kernel?

You're not the only one. I'm using nfs4 which simply does not work in these kernels. I don't know whether nfs3 works as I do not use that but for nfs4 current Lucid is no go...

---

### Post by darco on 2009-11-20
Can someone who has rc7 post the output to uname -a please?

thxs

d

---

### Post by scradock on 2009-11-20
> **darco said:**
> Can someone who has rc7 post the output to uname -a please?

thxs

d
Here it is: ```
 uname -a
Linux sc-laptop 2.6.32-4-generic #5-Ubuntu SMP Fri Nov 13 13:37:41 UTC 2009 x86_64 GNU/Linux 
```

---

### Post by fackamato on 2009-11-23
There's no "correct" way of running 2.6.32 on Karmic, right?

Unless I compile everything manually and add entries to the GRUB configuration file?

The best bet would probably be to build against Lucid Lynx 2.6.32 git version, and try to use that on Karmic.

Would that work?

---

