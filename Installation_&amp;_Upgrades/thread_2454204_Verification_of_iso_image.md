---
title: "Verification of iso image"
date: 2020-11-24
forum: Installation &amp; Upgrades
---

### Post by lordgallen on 2020-11-24
Maybe I am missing something in the aspect security in regards to verifying the download. The site (releases.ubuntu.com) where you download the signature file and the hash file needed for verification does not appear to use any type of encryption. Doesn't this subject the site to a Man in the Middle Attack? Can someone explain this to me so I have an understanding or am I wrong here to suggest the site is not secure? Thank-you for your understanding of my ignorance.

---

### Post by deadflowr on 2020-11-24
You use the sha256sum.gpg file to verify the authenticity of the sha256sum checksum for the ISO.
[https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview]("https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview")

---

### Post by lordgallen on 2020-11-24
> **deadflowr said:**
> You use the sha256sum.gpg file to verify the authenticity of the sha256sum checksum for the ISO.
[https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview)

[COLOR=#111111][FONT=Ubuntu]Note - some people question that if the site they are downloading from is not secure (many archive mirrors do not use SSL), how can they trust the signatures? The gpg fingerprint is checked against the Ubuntu keyserver, so if the signature matches, you know it is authentic no matter where/how it was downloaded!

[/FONT][/COLOR]:)

thank-you

---

