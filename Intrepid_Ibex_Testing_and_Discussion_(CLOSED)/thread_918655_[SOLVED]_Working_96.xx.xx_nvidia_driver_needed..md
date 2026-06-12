---
title: "[SOLVED] Working 96.xx.xx nvidia driver needed."
date: 2008-09-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by alienexplorers on 2008-09-13
When is nvidia going to finally release a 96.xx.xx driver that works.  I want to setup 3D graphics and compiz.

---

### Post by Steveway on 2008-09-13
With a FX-5200 you can use the 173... driver. It's also a legacy-driver (not developed anymore, thank you nvidia ;() but it's better than 96... .
If you don't really need the 3D-capabilities of your card for now then I would advise you to try the open-source nouveau driver.

---

### Post by cdtech on 2008-09-13
I used "envyng-gtk" to install the 173.., works great.

---

### Post by alienexplorers on 2008-09-13
I try to load the 173 drivers and it tells me my processor cannot handle some commands and reverts to 2D mode wwith no way of running compiz.  It just does not like my AMD K6-III CPU.

---

### Post by dawynn on 2008-09-13
I feel your frustration.  I want working nVidia drivers also.  But you've now created 5 new threads asking about how to get legacy nVidia drivers working -- all within a scope of 2 days.  This activity just clutters the forums.

The answer keeps coming back the same: The Ubuntu folks do not write the nVidia drivers.  The nVidia drivers are closed source software outside of Ubuntu / Linux control.  If you want a better answer, contact nVidia.  Once nVidia provides a solution, then make sure to update any launchpad bugs related to this issue that the solution exists.  At that time, if no bug exists, create one (and only one).

nVidia email for addressing linux bugs: [email]linux-bugs@nvidia.com[/email]
nVidia forums: [http://forums.nvidia.com/](http://forums.nvidia.com/)

Meanwhile, you're using a product that is in Beta status.  Every page documenting Intrepid Ibex (including these very forums -- read the stickys) indicates that you can expect things to be broken.  Hardy Heron is the current release, not II.  And the 96* drivers work perfectly fine on Hardy.

Unless you're using Kubuntu, HH is also a long-term-service release.  Meaning that they intend to support it for a few years.  So, even if nVidia doesn't get things fixed in time for II's release (or JJ, KK, LL, MM, NN), Hardy should stay actively working with all necessary security updates through April 2011.  (Note: Features are frozen for Hardy, but security issues will be addressed throughout its lifetime)

I'm hoping that either nVidia or [nouveau]("http://nouveau.freedesktop.org/wiki/") will have a solution by the time Hardy's lifetime ends.  We'll see who wins the race.

---

### Post by dawynn on 2008-09-13
What you're talking about with the 173* series not working is SSE instructions.

Here's the main wikipedia entry: [Streaming SIMD Extensions]("http://en.wikipedia.org/wiki/Streaming_SIMD_Extensions")

Contrast this with: [3DNow!]("http://en.wikipedia.org/wiki/3DNow!")

Note that the ultimate winner of the contest was SSE, and the comment in the 3DNow! article about 3DNow! instructions being incompatible with SSE.

The Athlon Classics used 3DNow!  As you noted, your problems with 3D and the 173* series are not with your video card, but with your CPU.  I feel your pain.  I'm in the same boat.

---

### Post by alienexplorers on 2008-09-13
I know I have started alot of threads.  I recently had brain surgery and I have a hard time remembering things, but I am so agrivated that I can't get 3D working.  I read where some prople that are runing a graphic card like mine a fx5200 havee used 173, but 173 causes this error:
> [   41.259203] nvidia 0000:00:09.0: found PCI INT A -> IRQ 11
[   41.259259] nvidia 0000:00:09.0: sharing IRQ 11 with 0000:00:08.1
[   41.287785] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
[   41.288103] NVRM: CPU does not support the PAT, falling back to MTRRs.

From what I can tell is that I can only run 2D graphics.  I wish nvidia would work with Ubuntu more in developing the drivers.  I don't know why nvidia does not release the code out so others could write the drivers if they don't want to.  I am trying to finally do something for Ubuntu by testing this build and I feel I can not do that if I can not run the right graphics that works.

Donnie

---

### Post by alienexplorers on 2008-09-13
Where do you get the open-source nouveau driver.  How do you set it up?  I added the repositories and when I click on the driver to load it, it tells me that it is missing a part needed to run.:
> xserver-xorg-video-nouveau:
 Depends: linux-nouveau-modules  but it is not installable
Where would I get that file?

---

### Post by Steveway on 2008-09-13
> **alienexplorers said:**
> Where do you get the open-source nouveau driver.  How do you set it up?  I added the repositories and when I click on the driver to load it, it tells me that it is missing a part needed to run.:

Where would I get that file?

You should be able to do this with:
sudo module-assistant auto-install drm-modules-source

---

### Post by alienexplorers on 2008-09-13
I get this error:
> terminator@ubuntu:~$ sudo module-assistant auto-install drm-modules-source
[sudo] password for terminator: 
sudo: module-assistant: command not found


---

### Post by Steveway on 2008-09-13
> **alienexplorers said:**
> I get this error:

Of course you need to install module-assistant first.

---

### Post by alienexplorers on 2008-09-13
It's working now.
Thank You,

Donnie

---

### Post by alienexplorers on 2008-09-13
I loaded the nouveau video driver from the repositories.  Now what do I do?

Donnie

---

