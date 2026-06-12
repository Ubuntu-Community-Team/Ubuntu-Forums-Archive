---
title: "Image failed *ACCESS DENIED* installing on lenovo"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by sodaa on 2012-12-17
I just received an x1 carbon in the mail and have been trying to install ubuntu on it today. Whenever I try to boot from my usb image of ubuntu-12.04.1-desktop-amd64, I get a message saying "image failed to verify with **ACCESS DENIED**..". I tried disabling UEFI boot in bios with no luck.

My usb image works fine on my pc and my other laptop. What is going on with my thinkpad?

PS. if it helps, I noticed on the main tab of my bios it says "UEFI Secure Boot       On". Do I need to change something in the security tab?

---

### Post by sodaa on 2012-12-17
Problem solved. I had to disable secure boot in the bios security tab.

---

### Post by vancouverpaddy on 2013-04-26
Thanks for replying with your solution.

I got the same error on a Lenovo Ideapad U410 trying to boot off USB CD. When I went into the BIOS, Secure Boot was greyed out in the Security tab.

Fortunately another fix works - I went into the Boot settings and changed the Boot Mode to "Legacy Support". I could then boot off my USB CD drive.

---

