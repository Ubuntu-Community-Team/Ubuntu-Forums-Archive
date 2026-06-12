---
title: "Running 22.04.3 with 6.5.0 series kernels &amp; get module build errors for drivers?"
date: 2024-01-28
forum: Installation &amp; Upgrades
---

### Post by MAFoElffen on 2024-01-28
Important: I will not mark this as Solved until it gets pushed through at LaunchPad.

Since Jammy 22.04.3 went to the 6.5.0 series kernels, there have been many Users getting driver module build errors.

The problem occurs because kernel series 6.5.0 was compiled with gcc-12 and the current ggc version in 22.04.3 is 11.4. The module build error is on a mismatch between what the current running kernel was built by, and the current installed compiler.

This started out with NVidia drivers. I came up with this work-around:
[https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164](https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164)

Since then, then it started appearing as problems for VirtualBox, and WiFi Drivers. Then more. The same work-around works for them.

I filed this Bug Report at LaunchPad to try to get gcc-12 pushed through as the current default installed, to try to get this fixed:
[https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/2051457](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/2051457)

We need people who are affected by to to go to this bug and join as "Also Affected"... To add weight to this to get it resolved through the normal updates process.

We should not have to resort to a work-around to do normal business. Ubuntu LTS has the reputation of being "Stable". We need to ensure it just works as it should.

---

### Post by ubfan1 on 2024-01-28
There may be a few issues involved here.  
1) Phasing of the Nvidia drivers.  When the hew package update to the 6.5 kernel occurred, Nvidia package(s) were held back due to phasing. The Nvidia module could not be built, so black screen.  Fall back to the older 6.2 kernel, of course still worked.
2) Source of the Nvidia modules. With only the standard repos (no graphics-drivers ppa), forcing the held-back phased Nvidia packages worked, and the Nvidia module build successfully.  Only after seeing this problem,  looking around, I see gcc-12 is installed, but not manually by me.

I presume if the Nvidia modules were not phased, and installed with the 6.5 kernel, the gcc-12 would have been downloaded too, and everything would work as expected. The only manual action I took was to   add the option to the upgrade:  sudo apt -o APT::Get::Always-Include-Phased-Updates=true upgrade

I don't see any depends or reverse depends on the kernel or Nvidia packages which would explain how the gcc-12 showed up, so maybe in some install script.

---

### Post by MAFoElffen on 2024-01-28
Maybe comment those findings in the Bug Report so that they get a wider understanding of what they face with this. This isn't a fix-all. There are other problems wrapped around this, that go along with this. It is a first step.

I see at Discourse: [https://discourse.ubuntu.com/t/introducing-kernel-6-8-for-the-24-04-noble-numbat-release/41958](https://discourse.ubuntu.com/t/introducing-kernel-6-8-for-the-24-04-noble-numbat-release/41958)
... That they have been trying to resolve this specifically for NVidia.
> 
Open issues (WIP):

 
[LIST]
[*]Fix the build of all the supported nvidia drivers (dkms) 
[/LIST]

But recently we have had Users coming here with other, similar module build issues with this same kernel series.

Yes, this only helps for recent NVidia drivers. The Legacy NVidia drivers still do not work unless you go back to the 6.2.0 series and pin it, to prevent the kernel from updating back to the 6.5.0 series. That is not a long-term solution for that.

Especially when Mark Shuttleford is hinting at extending the support for 22.04 for 12 years as he is giving to 24.04, when it releases in April. They keep moving to newer kernels series with this LTS. This is the same problems I'm having working with the upstream Intel Graphics Teams and the extended Graphics drivers for Jammy, with these newer Kernel Series.

The funny thing is, Mantic and Noble are using the newer kernels, and they do not have a problem. (???)

---

### Post by MAFoElffen on 2024-01-30
Initial response from LaunchPad says "They will not fix."

@ubfan1 ---
From their response, on that they will not change a major component of software (gcc) in an LTS release... That tells me that yours somehow getting gcc-12 was a fluke, and was not part of any of their plans. What they said conflicts with their promise to make nvidia-dkms work.

Trying to talk common sense to them or to have them share if they have a different solution.

---

### Post by ubfan1 on 2024-01-31
Checking some file dates, I see my gcc-12 was brought (by something) in last April, and has been just sitting around.  My /bin/gcc and /bin/cc links are years old.  The /lib/modules/6.5.0-14-generic/kernel/nvidia-535/bits/nvidia.o was compiled (last week) with gcc-12.3 (correct for my kernel 6.5).  It looks like if gcc-12 is installed, it will be used for building an nvidia module, without changing the system /bin/gcc default of gcc-11.  When you were trying your workaround by changing links (/bin/gcc to gcc-12), did you ever try the nvidia driver install before changing links with gcc-12 present?   If the right compiler gets used if present, that suggests a simple fix of adding a gcc-12 dependency on the hwe kernel package (to allow any modules to be build if they do what nvidia apparently does). I'll try out some jammy iso boots if I cannot find a spare partition to install to and see what happens (I've never bothered to figure out how to make my VMs use Nvidia). I'll suggest this on the bug, I can understand not wanting to change the default gcc, but simply adding one should not cause problems.

---

### Post by ActionParsnip on 2024-01-31
Where did you get the 6.5.0 kernel from?

---

### Post by ubfan1 on 2024-01-31
I got the 6.5 kernel from the standard hwe download.  My Nvidia drivers are from the standard repos, not the graphics-drivers PPA or Nvidia directly.

---

### Post by ubfan1 on 2024-01-31
I added some tests to the bug 2051457.  Booting off the Ubuntu 22.04.1 ISO, running the 5.15 kernel, adding the gcc-12 and generic hwe packages, then the Nvidia 535 driver selection in Software & Updates succeeds and uses the gcc-12 compiler to build the nvidia.ko module.
Seems that's all it takes, having the gcc-12 present when you select the Nvidia driver when a 6.5 kernel is present.

---

### Post by MAFoElffen on 2024-01-31
> **ubfan1 said:**
>  When you were trying your workaround by changing links (/bin/gcc to gcc-12), did you ever try the nvidia driver install before changing links with gcc-12 present?   If the right compiler gets used if present, that suggests a simple fix of adding a gcc-12 dependency on the hwe kernel package (to allow any modules to be build if they do what nvidia apparently does). I'll try out some jammy iso boots if I cannot find a spare partition to install to and see what happens (I've never bothered to figure out how to make my VMs use Nvidia). I'll suggest this on the bug, I can understand not wanting to change the default gcc, but simply adding one should not cause problems.
Kernel 6.5.0 can via updates. During the updates, nvidia-dkms failed on building a module for 6.5.0. I retried on few times, same error. I uninstall nvidia-driver-525 & nvidia-dms, then installed them again. Failed. I started checking the 'make' error out. I had gcc-11 install. gcc-12 was not.

I manually installed gcc-12 and g++-12.

Retried installign evrything again. The nvidiadriver525 & nvidia-dmks driver installs succeeded.

So yes it was broke. The normal NVidia driver update tricks failed for me. Installing gcc-12 did fix that for me.

---

### Post by MAFoElffen on 2024-01-31
> **ubfan1 said:**
> I added some tests to the bug 2051457.  Booting off the Ubuntu 22.04.1 ISO, running the 5.15 kernel, adding the gcc-12 and generic hwe packages, then the Nvidia 535 driver selection in Software & Updates succeeds and uses the gcc-12 compiler to build the nvidia.ko module.
Seems that's all it takes, having the gcc-12 present when you select the Nvidia driver when a 6.5 kernel is present.

When you install from the Desktop Edition 22.04.3 installer, the HWE stack is installed by default with the install. It's been that way since 20.04...

Then only way it does not install, is if you install from the Server Edition ISO. Or if you installed previous to it being a default on the installers, and do a do-release-upgrade.

So most Users, if they have Desktop, are on the HWE Stack.

---

### Post by ubfan1 on 2024-01-31
Ha, didn't notice that the kernel version wasn't frozen in the xx.04.1 releases.  Makes sense if Canonical's thinking of 12 year support -- they're working towards that.  So if I were doing this, I'd put a compiler dependency on the hwe headers (gcc-12 for linux-hwe-6.5-headers-6.5.0-14...).  That way, when a new kernel release gets pulled in via hwe, the new headers and a new compiler get pulled in too.  Any number of compilers can be installed without problem, just don't change the original system default (these days -- looks like another thing to think about for a 12 year support cycle! ;^)
  Anyway, the detail steps in the bug report can have the explicit install of the three hwe packages dropped if you just do an apt upgrade (getting 500+ unwanted packages upgraded too and at least doubling the testing time).

---

### Post by ubfan1 on 2024-02-05
Just ran an install of the Ubuntu 22.04.1 Desktop and the gcc-12 now is downloaded automatically (and used successfully to build the kernel 6.5 nvidia 545  modules).  Added to the bug report.

---

### Post by MAFoElffen on 2024-02-06
Funny that they said they were not going to do that... We pleaded with them to change their minds (because it fixed this issue), to no avail. (Or so we thought so.) 

You read that right?

But without saying anything different: Now they are? LOL.

---

