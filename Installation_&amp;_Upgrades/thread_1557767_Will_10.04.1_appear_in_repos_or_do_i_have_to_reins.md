---
title: "Will 10.04.1 appear in repos or do i have to reinstall myself?"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by maddbaron on 2010-08-21
Never used a LTS Ubuntu before, how do I get from 10.04 to 10.04.1 ? Burn a cd then update myself or does it come into the repos & I update like I do normally for applications?

---

### Post by dwbsr on 2010-08-21
> **maddbaron said:**
> Never used a LTS Ubuntu before, how do I get from 10.04 to 10.04.1 ? Burn a cd then update myself or does it come into the repos & I update like I do normally for applications?

For Ubuntu 10.04 LTS users just run update manager and you'll have Ubuntu 10.04.1 with all the security updates and corrections!

You can check by running in the terminal ```
**uname -a**
```It should say > 2.6.32-24-generic-pae. Also you can see the verion number by running ```
**lsb_release -a**
``` and you should see > Description:    Ubuntu 10.04.1 LTS

---

### Post by maddbaron on 2010-08-21
> **dwbsr said:**
> For Ubuntu 10.04 LTS users just run update manager and you'll have Ubuntu 10.04.1 with all the security updates and corrections!

You can check by running in the terminal ```
**uname -a**
```It should say . Also you can see the verion number by running ```
**lsb_release -a**
``` and you should see

I got 

> 
2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux


I'll run update manager.

---

### Post by dwbsr on 2010-08-21
> **maddbaron said:**
> I got 

I'll run update manager.

After it updates you should see this full line:
> 2.6.32-24-generic-pae #41-Ubuntu SMP Thu Aug 19 02:43:57 UTC 2010 i686 GNU/Linux

HTH

---

### Post by maddbaron on 2010-08-21
> **dwbsr said:**
> After it updates you should see this full line:


HTH

i saw and updated the security updates that included a new linux image but i am still getting the 39... would rebooting help? I haven't reboot in a few days...

---

### Post by u1106 on 2010-08-21
> **maddbaron said:**
>  how do I get from 10.04 to 10.04.1 ? 

I have also found these point releases somewhat confusing. Not sure where their meaning is documented.

Anyway if you continously follow security updates and recommended updates you will go slowly towards the next point release. At some point they will update the package base-files and then you are at the next point release.

base-files was updated from 5.0.0ubuntu20.10.04 to 5.0.0ubuntu20.10.04.1 on July 26 (well that was when I installed it, it might have been available a couple of days earlier)

The change log says:

```
base-files (5.0.0ubuntu20.10.04.1) lucid-proposed; urgency=low

  * /etc/lsb-release, /etc/issue, /etc/issue.net: Bump version number to
    10.04.1 in preparation for the point release.
```
Please note that the version of the base-files package is not necessarily in sync with the release. Currently base-files is at 5.0.0ubuntu20.10.04.2, but the release is still Ubuntu 10.04.1 LTS.

I guess they just produce new CD images each time they have reached a new point release. So somebody who installs LTS at a later time after its first release doesn't need to install several hundred of updates immediately after installation.

Of course if you for some reason or another don't want to install updates continuously, you could just do it when the point release is complete. But there is no need to make a fresh installation.

---

### Post by howefield on 2010-08-21
> **maddbaron said:**
> would rebooting help? I haven't reboot in a few days...

A reboot won't hurt, but you are already running the latest kernel for Lucid which is 2.6.32.24

dwbsr seems to be under the impression that you are running a PAE kernel, which you are not. So you won't see exactly the same line (s)he does when running the proffered commands.

---

### Post by u1106 on 2010-08-21
> **maddbaron said:**
> i saw and updated the security updates that included a new linux image but i am still getting the 39... would rebooting help? I haven't reboot in a few days...

A kernel update becomes never effective before a reboot. The kernel is always running and it cannot be changed on the fly. When the kernel is updated the new version is just written to disk, but it will not be used before rebooting.

There is a popup on the desktop that a reboot is required (it's exact form and location depends on whether you use Ubuntu, Kubuntu or Xubuntu)

---

### Post by maddbaron on 2010-08-21
oh ok, so just wait and before long the needed patches and updates will appear...ok cool, i thought it was something I had to do myself.  the linux image is up to date so everything else is fine. cool beans.
Thanks for the help.

---

### Post by maddbaron on 2010-08-21
> **u1106 said:**
> A kernel update becomes never effective before a reboot. The kernel is always running and it cannot be changed on the fly. When the kernel is updated the new version is just written to disk, but it will not be used before rebooting.

There is a popup on the desktop that a reboot is required (it's exact form and location depends on whether you use Ubuntu, Kubuntu or Xubuntu)

oh ok...then off to reboot I go.

---

### Post by u1106 on 2010-08-21
> **howefield said:**
> A reboot won't hurt, but you are already running the latest kernel for Lucid which is 2.6.32.24



2.6.32.24 is not an exact kernel version number. It's only the Ubuntu kernel ABI version number. (Different kernel with the same ABI version can use the same modules. When the ABI version number changes, modules need to be rebuilt.)

The current kernel is 2.6.32-24-generic #41.

So if maddbaron says he has #39, he is still running the previous one. (I didn't see #40. Either it was not published at all or it was available only for a short time and I never picked it up)


N.B. this is the "normal" i386 32 bit generic kernel. Have not checked whether the numbers of 64 bit, PAE, server and whatever other kernel are in sync

---

### Post by maddbaron on 2010-08-21
rebooted now i'm running #41

---

### Post by jocko on 2010-08-21
> **maddbaron said:**
> oh ok, so just wait and before long the needed patches and updates will appear...ok cool, i thought it was something I had to do myself.  the linux image is up to date so everything else is fine. cool beans.
Thanks for the help.

Not sure what you expect from the point release.

The **only** significant thing that happens with a point release is  that they release new install media (live CDs, alternate CDs etc.) for those that wish to install an LTS  version without having to install all the updates (imagine the amount  of updates needed to get up to date if you install 10.04 from the  original CD two years from now, and how much less it will be if you  install from a 10.04.4 CD).

The updates are already in the repos (and most have been there for weeks or months) so as long as you have installed all updates whenever they have appeared in update-manager, you have the same versions of everything as in the 10.04.1 release.

In another way: It doesn't matter which release we talk about, it could be a milestone release during development (alpha, beta, RC), final release when development is complete, or a point release of an LTS version. The "release" is just a **snapshot of what's already in the repos** when it is decided it is time to release it, at which point the various install isos are made (from the packages that are already in the repos, and already installed on all systems that have installed earlier), tested, and finally officially released.

---

