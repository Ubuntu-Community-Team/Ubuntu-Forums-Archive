---
title: "Install latest kernel.deb in 16.04 LTS"
date: 2016-12-23
forum: Installation &amp; Upgrades
---

### Post by cc31296 on 2016-12-23
Hi,
Does some-one how to run latest kernel deb-file in Kubuntu 16.04 LTS 64bit?

---

### Post by ian-weisser on 2016-12-23
What do you mean by 'latest'?

Do you wish to test new, unreleased kernels? If so, join the Ubuntu Kernel Team. If I recall correctly, they use a git-update distribution model.

Are you trying to solve some kind of hardware problem? If so, please tell us about the issue. There may be a less radical fix available.

Beyond those two cases, I generally recommend LTS users stick with their supported, secure LTS kernel. LTS is all about avoiding big changes to your system.

For a supported method of getting newer (but not 'latest') kernels, see [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack) (Available Jan 2017)

For a supported method of live kernel updates (again, not 'latest' kernels), you can subscribe to Canonical's free LivePatch service: [https://www.ubuntu.com/server/livepatch](https://www.ubuntu.com/server/livepatch)

---

### Post by cc31296 on 2016-12-24
By latest i mean a .deb package like this:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.9/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.9/)

however, i follow up your advice, and will stick by the kernel offered for my LTS version.

---

### Post by ian-weisser on 2016-12-24
That particular kernal PPA is for testing.
Advanced stuff. Use only if you like to find breakage and file bugs. Not recommended for production.
See [https://wiki.ubuntu.com/KernelTeam](https://wiki.ubuntu.com/KernelTeam) for the owning Team.

...of course, the best bugs have patches attached. In that case, [run the git version instead]("https://wiki.ubuntu.com/Kernel/Dev/KernelGitGuide") and push your patches directly.

---

