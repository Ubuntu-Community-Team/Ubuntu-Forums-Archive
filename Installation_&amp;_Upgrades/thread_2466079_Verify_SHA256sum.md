---
title: "Verify SHA256sum"
date: 2021-08-19
forum: Installation &amp; Upgrades
---

### Post by drrummer on 2021-08-19
Hi

I had decided to go with Linux Mint.  However, I can't get past the Verification stage of the Installation process.

Would it be easier to verify Ubuntu ?

---

### Post by sudodus on 2021-08-19
1. Download the iso file, for example Ubuntu Desktop 20.04.2.0 LTS

2. Look up the file with the sha256sum for the iso file and compare the result with the content of the file

3a. Run and check with your eyes

```

$ [COLOR="#000064"]**sha256sum ubuntu-20.04.2.0-desktop-amd64.iso**[/COLOR]
93bdab204067321ff131f560879db46bee3b994bf24836bb78538640f689e58f  ubuntu-20.04.2.0-desktop-amd64.iso

```

3b. Or use the file SHA256SUMS and let the computer do it for you

```

$ [COLOR="#000064"]**sha256sum -c SHA256SUMS**[/COLOR]
sha256sum: ubuntu-20.04.2-live-server-amd64.iso: No such file or directory
ubuntu-20.04.2-live-server-amd64.iso: FAILED open or read
ubuntu-20.04.2.0-desktop-amd64.iso: [COLOR="#006400"]**OK**[/COLOR]
sha256sum: WARNING: 1 listed file could not be read

```

In this case there is also a line for Ubuntu Live Server, and there will be a complaint, if there is no server iso file in the current directory. But the important thing for you is the '[COLOR="#006400"]**OK**[/COLOR]' verifying that the download was successful for the Ubuntu Desktop file.

[hr][/hr]
If you want a higher degree of security you can also use the gpg signature file, so download SHA256SUMS.gpg and run

```

$ [COLOR="#000064"]**gpg --verify SHA256SUMS.gpg SHA256SUMS**[/COLOR]
gpg: Signature made tor 11 feb 2021 20:07:58 CET
gpg:                using RSA key 843938DF228D22F7B3742BC0D94AA3F0EFE21092
gpg: [COLOR="#006400"]**Good signature from "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" [unknown]**[/COLOR]
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8439 38DF 228D 22F7 B374  2BC0 D94A A3F0 EFE2 1092

```

Look for '[COLOR="#006400"]Good signature from "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>"[/COLOR]'

---

