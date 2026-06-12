---
title: "Why does LTS v22.04.2 not have the same packages as on server as are on desktop?"
date: 2023-02-24
forum: Installation &amp; Upgrades
---

### Post by breusshe2 on 2023-02-24
Hey, folks;

I've been running Ubuntu Server LTS v22.04.1.  Today, I ran updates (including dist-upgrade and do-release-upgrade) to get me onto LTS v22.04.2.  do-release-upgrade said there were no new LTS versions to install.  But, after dist-upgrade, and a logoff and on, I saw that the banner did say it was LTS v22.04.2.  I then looked at the kernel and apache2 versions and saw they were v5.15 and v2.4.52, respectively.  I was expecting v5.19 and v2.4.54, (again, respectively).  I'm hearing these newer versions were released with the Desktop ISO so I'm wondering why I'm not seeing them on the Server flavor.

Can anyone shed some light?

---

### Post by ubfan1 on 2023-02-24
Your 22.04 LTS will stick with the 515 kernel unless you have installed the hwe packages to get the newer 5.19 releases.

---

### Post by Impavidus on 2023-02-25
Going from 22.04.1 to 22.04.2 is no release upgrade. It's just a regular upgrade. Around the same time, the kernel may be upgraded from 5.15 to 5.19, but only if you use the hwe kernels. Regular Ubuntu defaults to those kernels, but Ubuntu server doesn't. Servers need more stability and don't need the latest drivers for graphics hardware.

---

### Post by ajgreeny on 2023-02-25
You are currently running the most recent LTS version so there is no point running that **do-release-upgrade** command as there will be  no newer LTS version to be found.

If you are not wanting to remain on LTS versions only, and your Updates settings are to show all available versions, not just LTS versions, you might have found that the command had upgraded your system to 22.10.

Your choice; many of us choose to use the LTS versions only, though I do look at every version when it appears using a virtual install in KVM/QEMU.

---

