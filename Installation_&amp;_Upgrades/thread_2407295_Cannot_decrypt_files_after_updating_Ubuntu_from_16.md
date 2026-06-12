---
title: "Cannot decrypt files after updating Ubuntu from 16.04LTS to 18.10"
date: 2018-12-02
forum: Installation &amp; Upgrades
---

### Post by denis14 on 2018-12-02
I've decided to finally move from 16.04LTS to the latest version and among many other issues I find that I cannot decrypt files that are created/encrypted before. The GPA (GNU Privacy Assistant) is rejecting decryption displaying the following error message:

[IMG]https://i.imgur.com/hnygMQ6.png[/IMG]

If I tried command line, gpg is reporting the following error message at the end:

[FONT=courier new]gpg: WARNING: message was not integrity protected
gpg: Hint: If this message was created before the year 2003 it is
     likely that this message is legitimate.  This is because back
     then integrity protection was not widely used.
gpg: Use the option '--ignore-mdc-error' to decrypt anyway.
gpg: decryption forced to fail![/FONT]

The suggested hint '--ignore-mdc-error' allows me to decrypt and if I try to encrypt back that file in 18.10 I can decrypt it without problem. Why is that? The original file wasn't created before 2003 but few weeks ago.

---

