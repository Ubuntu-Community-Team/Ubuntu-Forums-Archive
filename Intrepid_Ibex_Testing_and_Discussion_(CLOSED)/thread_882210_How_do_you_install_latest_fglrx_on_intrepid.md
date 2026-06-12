---
title: "How do you install latest fglrx on intrepid?"
date: 2008-08-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by grigio on 2008-08-06
I had no luck with any provided or generated deb.

Here some info:
amd/ati 4850
2.6.26-5-generic
ati-driver-installer-8-7-x86.x86_64.run

```
cat /usr/share/ati/fglrx-install.log
Errors during DKMS module removal
Errors during DKMS module removal
[Error] Kernel Module : Failed to add fglrx-8.512 to DKMS
```

I tried also with [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) but fglrx module is never loaded

```
sudo modprobe fglrx
FATAL: Module fglrx not found.
```

---

### Post by PmDematagoda on 2008-08-06
Did you try installing the fglrx package found in the repositories?

---

### Post by bpl07 on 2008-08-07
The repository fglrx includes the patch to make fglrx work with kernel 2.6.25 or greater.  However it still doesn't work because I think we're still waiting for Xorg 7.4 support from ATI.  Hopefully catalyst 8.8 includes it.  I'm using mesa right now.

---

### Post by grigio on 2008-08-08
@bpl07: mesa drivers freezes very often :(
what is your hardware?

---

### Post by InfinityCircuit on 2008-08-08
```
sudo m-a a-i --text-only fglrx
sudo m-a get -f fglrx-kernel-src
sudo modprobe fglrx
```

Change to fglrx in /etc/X11/xorg.conf and change your default depth to 24.

DRI2 fix is already in so this is good to go.

---

### Post by grigio on 2008-08-09
no success
```

[   15.017519] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   15.017519] Symbol init_mm is marked as UNUSED, however this module is using it.
[   15.017519] This symbol will go away in the future.
[   15.017519] Please evalute if this is the right api to use and if it really is, submit a report the linux kernel mailinglist together with submitting your code for inclusion.
[   15.033036] [fglrx]   vendor: 1002 device: 9442 count: 1
[   15.035233] [fglrx] ioport: bar 4, base 0xc000, size: 0x100
[   15.035233] [fglrx] Maximum main memory to use for locked dma buffers: 3135 MBytes.
[   15.035233] [fglrx] PAT is enabled successfully!
[   15.035233] [fglrx] module loaded - fglrx 8.51.3 [Jul  3 2008] with 1 minors

```

---

### Post by InfinityCircuit on 2008-08-09
I don't see an error in the dmesg you just posted...and I missing something obvious?

---

### Post by Mazza558 on 2008-08-09
How's the new fglrx driver coming along? Will it be vastly superior to the Hardy version?

---

### Post by InfinityCircuit on 2008-08-09
I lied.  fglrx is NOT working on RV635 ATI Radeon HD 3650.  I install fglrx, I modprobe it, I put it in xorg.conf, no errors anywhere, and...it loads vesa.  For no apparent reason.

I should have just stayed with Sid on this machine.

---

### Post by PmDematagoda on 2008-08-09
> **InfinityCircuit said:**
> I lied.  fglrx is NOT working on RV635 ATI Radeon HD 3650.  I install fglrx, I modprobe it, I put it in xorg.conf, no errors anywhere, and...it loads vesa.  For no apparent reason.

I should have just stayed with Sid on this machine.

Perhaps you could try using the radeonhd driver and see if it is any better?

---

### Post by InfinityCircuit on 2008-08-09
radeon/radeonhd both work fine for non-3D.  radeonhd is marginally better.  However, neither let me do DRI, which is a shame.

---

### Post by InfinityCircuit on 2008-08-09
FYI this is the current bug:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/247376](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/247376)

So once you get past:
1) failure of m-a to pull source without "-f"
2) failure to pull in correct xorg-driver-fglrx
3) failure to set default depth correctly

We hit a brick wall that cannot be moved.

---

### Post by grigio on 2008-08-10
I still have the same problems of InfinityCircuit.. Does Catalist 8.6 works better with the kernel present in Intrepid?

---

### Post by grigio on 2008-08-11
:confused:
Errors during DKMS module removal
Errors during DKMS module removal
[Error] Kernel Module : Failed to add fglrx-8.512 to DKMS

Any chance to install Catalyst 8.7 on Intrepid?

---

### Post by olskar on 2008-08-11
According to [Phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=NjYzNw") X.Org 7.4 is to lose DRI2 support, what does this mean?

---

### Post by BwackNinja on 2008-08-11
N...n..no DRI2? This was the one thing, beyond everything else that I was waiting for. The radeon drivers don't yet support it, but having the support in X.Org would mean only having to compile a new graphics driver, not the whole Xserver stack. I guess I'd still be able to compile for the support later, but regardless, this is the most depressing thing I've heard in a few months.

---

### Post by InfinityCircuit on 2008-08-12
> **grigio said:**
> :confused:
Errors during DKMS module removal
Errors during DKMS module removal
[Error] Kernel Module : Failed to add fglrx-8.512 to DKMS

Any chance to install Catalyst 8.7 on Intrepid?

Please try the following:

sudo m-a get -f fglrx-kernel-source
sudo apt-get install xorg-driver-fglrx

---

### Post by grigio on 2008-08-14
I got fglrx working for my 4850 on Intrepid..
I have downgraded xorg to the hardy's version and now it works (Anyway random freezes happen).

:popcorn::popcorn:
I hope Amd and Ubuntu will this before 8.10
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/247376](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/247376)
:popcorn::popcorn:

---

### Post by Rashedul on 2008-08-15
so the big question is what will happen during release time? We are still in alpha stage so we shouldn't worry too much right now other than file bugs, test and make our contributions. But will fglrx be ready in time for Ibex release? If not will we downgrade the X server to make it compatible?

---

### Post by Mazza558 on 2008-08-15
I've just got a new Fglrx through the Update Manager on Hardy (Proposed Updates) - Is this the same one that'll be in Intrepid?

---

### Post by grigio on 2008-08-19
> **Mazza558 said:**
> I've just got a new Fglrx through the Update Manager on Hardy (Proposed Updates) - Is this the same one that'll be in Intrepid?

no because Intrepid's fglrx driver doesn't support the new Xserver version

---

### Post by helliewm on 2008-10-14
How do you downgrade Xorg to the Hardy Version?

---

### Post by olskar on 2008-10-14
> **helliewm said:**
> How do you downgrade Xorg to the Hardy Version?


[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#How_to_downgrade_X_from_7.4_to_7.3](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#How_to_downgrade_X_from_7.4_to_7.3)

---

### Post by wgrant on 2008-10-14
I would advise not downgrading - we've got a new version of fglrx in the works right now. It'll be out very soon! It even seems to work.

---

### Post by mihai.ile on 2008-10-14
> **wgrant said:**
> I would advise not downgrading - we've got a new version of fglrx in the works right now. It'll be out very soon! It even seems to work.

now this is quite GREAT news.
Not that I don't like the open source drivers, but they seem a little slow when scrolling and some other things like bugs in tv-out configurations...

---

### Post by DeeZiD on 2008-10-15
[http://changelogs.ubuntu.com/changelogs/pool/multiverse/f/fglrx-installer/fglrx-installer_8.543-0ubuntu1/changelog](http://changelogs.ubuntu.com/changelogs/pool/multiverse/f/fglrx-installer/fglrx-installer_8.543-0ubuntu1/changelog)

Is this the new driver?

---

