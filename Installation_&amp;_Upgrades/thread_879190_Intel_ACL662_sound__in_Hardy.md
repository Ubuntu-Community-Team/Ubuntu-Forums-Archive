---
title: "Intel ACL662 sound  in Hardy"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by smi402 on 2008-08-03
I have been running a Mythbuntu frontend on a motherboard that has an Intel ALC662 sound chip. I have a SPDIF optical output attached to the ALC662 header on the motherboard that serves as the optical input into my Home Theatre 5.1 amplifier. However, although the analog outputs on the ALC662 work fine I can't get the optical digital output to work under Hardy 8.04 with the 2.6.24-19 kernel. After "Googling around" I note that there is a bug in the 2.6.24 kernel that results in the IEC958 device from being displayed with *aplay -L* and appearing in *alsamixer* so this device can't be unmuted in order to activate the SPDIF port. Apparently this bug (#475441) has been fixed in the 2.6.25 kernel, which I guess will be released as 2.6.26 once its stability has been confirmed.

I would be grateful if someone could inform us ALC662 SPDIF users when a suitable 2.6.26 kernel may appear in the repositories. In the meantime can someone point me to a site for a stable version of 2.6.25 or 2.6.26 that I can test.

Frank :(

---

### Post by smi402 on 2008-08-03
Sorry, a little dislectic this early in the morning. The thread heading should read ALC662 not ACL662.

Frank

---

