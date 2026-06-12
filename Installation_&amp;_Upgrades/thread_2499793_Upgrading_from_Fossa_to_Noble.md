---
title: "Upgrading from Fossa to Noble"
date: 2024-08-10
forum: Installation &amp; Upgrades
---

### Post by sports fan Matt on 2024-08-10
OK, so I&#8217;ve been struggling trying to install Noble for about the last three days. Finally got a Clean ISO of Fossa - Question is, Should I upgrade directly to Noble, or stop at Jammy. 

Is anybody running jammy in lieu of Noble?

Matt

---

### Post by guiverc on 2024-08-10
There is no upgrade path from 20.04 (*focal*) to 24.04 (*noble*).

Ubuntu 20.04 LTS has a single upgrade path now, to Ubuntu 22.04 LTS (*jammy*) given the other non-LTS options are all EOL.  [https://help.ubuntu.com/community/JammyUpgrades](https://help.ubuntu.com/community/JammyUpgrades)

Ubuntu 22.04 LTS has no *supported* upgrade path open currently, the upgrade path to Ubuntu 24.04 LTS is expected to open very soon, but it's **not** currently a *supported* upgrade path, thus needs to be *forced* so upgrades can occur for *Quality Assurance *purposes. [https://help.ubuntu.com/community/NobleUpgrades](https://help.ubuntu.com/community/NobleUpgrades)

If you want to explore the ***upgrade blockers*** on the 22.04 to 24.04 upgrade path; you can visit [https://discourse.ubuntu.com/t/noble-numbat-24-04-1-lts-point-release-status-tracking/46972](https://discourse.ubuntu.com/t/noble-numbat-24-04-1-lts-point-release-status-tracking/46972) and watch them being *crossed off* as they're dealt with. If you open launchpad and explore, you can also see more too, as the *blocker bugs* are those that need to be addressed before 22.04 to 24.04 upgrades will officially open.

---

### Post by sports fan Matt on 2024-08-11
Thanks for that so should I upgrade or hang tight? I guess I could upgrade to jellyfish.

---

### Post by Dennis N on 2024-08-11
> **sports fan Matt said:**
> ...should I upgrade or hang tight? I guess I could upgrade to jellyfish.

If 20.04 LTS meets your needs, there is no need to upgrade. In fact, you can extend the support period from 5 to 10 years by enrolling in the Ubuntu Pro services.

On the possibility of upgrading 22.04 LTS to the latest, 24.04 LTS, I see notifications on 22.04 LTS that directly upgrading to 24.04 is now possible. See the screenshot.

---

### Post by guiverc on 2024-08-11
You've given few specifics; so I provided on *factual* data as I see it.

I have no idea if you're asking about a Server or Desktop install, as there are differences between them, nor *flavor*; which changes packages that get installed & your defaults. The release used at install sets many defaults.

You mention "*Finally got a Clean ISO of Fossa*" which implies this is a new system, without data.

Ubuntu 20.04 LTS Desktop used the `ubiquity` installer, which was available until the 23.10 release (it was the *legacy installed option for 23.04 & 23.10*) and isn't an installer available for 24.04, so attempted install(s) of 24.04 were using a different installer; if your issue was with the installer, using a 22.04 ISO with `ubiquity` makes more sense to me.

Ubuntu 20.04 LTS will have older kernel stacks installed; but as I don't know what media you used (Server? Desktop? what update level? etc) I can't know what kernel you used & installed. Ubuntu 20.04 LTS media exists with 5.4 (GA), 5.8, 5.11, 5.13 & 5.15 (HWE) kernels (*or OEM kernels too maybe possible*); and that *default* kernel stack will influence what a *release-upgrade* will have you using. Sure you can boot *live* systems to explore the effects, but as I don't know Server/Desktop detail I can't really advise here on effects.

I'll always boot *live* systems and test out the new release, especially the kernel stack options available (ie. LTS releases have kernel stack options; and you can download an ISO with a specific stack for testing on it; 22.04 Desktop media currently exists with 5.15 (GA), 5.19, 6.2, 6.5 (HWE *current*) & 6.8 (HWE *proposed*) kernels for example) and actually test it on your your actual hardware BEFORE installing anything...  but I don't know if you're using Server/Desktop, as what options exist or more particularly how easy they are differ.

Live testing would be what I'd recommend first; as it lets you test on your actual hardware; and adjust that testing to be as close as you can for your expected use-case.

---

### Post by sports fan Matt on 2024-08-11
This is a desktop. :) do I need to upgrade now would be nice to be current, yes. I kept using the ISO from the website.  Apologies for the lack of information. It was a long day at work and my brain was fried. 

Typically, I’ll look at the system that is new and play around a little bit ~ But because everything had gone flawlessly, I was like I don’t think I need to. I need to from now on I suppose. 

I’ve been  with Ubuntu since Gutsy 7.10. (Anybody remember those days?)

I’m upgrading to jellyfish But I will stop there.

---

### Post by pantazi on 2024-08-15
I'm using Ubuntu 20.04 and it has been rock solid for my needs. I thought about upgrading to 22.04 just to be current (at the time) so I installed it into a VM and had a good play around with it but couldn't find any  advantages over 20.04 to justify the upgrade.

My suggestion based on your comments would be to install 22.04, run 24.04 in a VM and test for your needs.

---

