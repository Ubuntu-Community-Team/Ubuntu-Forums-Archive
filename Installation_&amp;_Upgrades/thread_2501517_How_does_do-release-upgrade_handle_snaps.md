---
title: "How does do-release-upgrade handle snaps?"
date: 2024-10-11
forum: Installation &amp; Upgrades
---

### Post by yaminb on 2024-10-11
I generally use update to get newer version of Ubuntu. I recently installed 24.10 and everything was okay.
However, I tried to check out the new 'security center' and it wasn't installed. 

background:
[LIST]
[*]I googled a bit and found I had to install the snap: desktop-security-center
[*]It was installed, but I couldn't actually turn on the security prompting.
[*]It turned out, I had to also install the snap: prompting-client
[/LIST]

What is the expectation here in terms of what do-release-upgrade or other update mechanisms have?
Should I have expected these snaps to be installed during the upgrade process?
If there is no expectation, then is it documented somewhere which snaps should be installed/removed for a particular version?

---

### Post by ian-weisser on 2024-10-11
Unable to reproduce that behavior.

I just upgraded a stock Ubuntu 24.04 system to 24.10.
Both snaps were installed automatically during the final phase of the script.

---

