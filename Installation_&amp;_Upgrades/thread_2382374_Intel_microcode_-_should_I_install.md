---
title: "Intel microcode - should I install?"
date: 2018-01-12
forum: Installation &amp; Upgrades
---

### Post by paul-taniwha on 2018-01-12
There seems to be general problems with Intel's 2018018 microcode update, it just showed up as security fix under Ubuntu.

Should I install it? wait?

---

### Post by missmoondog on 2018-01-12
i just did a bit ago. no problems here. :)

did read on another site that intel's fix also has bugs though, but that was a windows site, if that means anything?

[https://newsroom.intel.com/news/intel-security-issue-update-addressing-reboot-issues/](https://newsroom.intel.com/news/intel-security-issue-update-addressing-reboot-issues/)

---

### Post by kostkon on 2018-01-12
Looks like [it affects some Broadwell and Haswell based systems]("https://newsroom.intel.com/news/intel-security-issue-update-addressing-reboot-issues/"). Install/apply the update at your own discretion. Best course of action though would be to wait for the updated package that fixes the problem.

---

### Post by missmoondog on 2018-01-12
> **kostkon said:**
> Looks like [it affects some Broadwell and Haswell based systems]("https://newsroom.intel.com/news/intel-security-issue-update-addressing-reboot-issues/"). Install/apply the update at your own discretion. Best course of action though would be to wait for the updated package that fixes the problem.

at the rate this cluster mess is going, it may be a LONG time before they and every one else gets the updated package right!!

---

### Post by paul-taniwha on 2018-01-12
> **kostkon said:**
> Looks like [it affects some Broadwell and Haswell based systems]("https://newsroom.intel.com/news/intel-security-issue-update-addressing-reboot-issues/"). Install/apply the update at your own discretion. Best course of action though would be to wait for the updated package that fixes the problem.

yeah that was my basic thought - hey Canonical: could you please remove that update from circulation until you know it's safe

---

### Post by rbmorse on 2018-01-13
No problems so far on my Haswell machine.

---

### Post by grahammechanical on 2018-01-13
The Intel microcode update is a security fix from Intel as part of the response to the Meltdown & Spectre vulnerabilities in Intel chips. I always install the Intel microcode driver on my Intel Core 2 Duo. It gets updates from time to time. The update that I did a few minutes ago brought in the expected update to the Intel microcode driver. The system boots just fine.

[https://ubuntuforums.org/showthread.php?t=2381801](https://ubuntuforums.org/showthread.php?t=2381801)

> 2018 Jan 11: Updates to the intel-microcode package were released, see [USN-3531-1]("https://usn.ubuntu.com/usn/usn-3531-1/")

[URL="https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown"]https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdow
[/URL]
Regards.

---

