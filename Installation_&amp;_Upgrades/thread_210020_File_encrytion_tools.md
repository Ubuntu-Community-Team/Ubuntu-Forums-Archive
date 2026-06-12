---
title: "File encrytion tools"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by wifiabc on 2006-07-06
What would be a good easy to use tool to encrypt confidential files or directories in Ubuntu?

---

### Post by orb9220 on 2006-07-06
Seahorse is in the synaptic pakage installer.

True Crypt is the most powerful. But no gui and it has been compiled for the new 
kernal .25 yet

---

### Post by wifiabc on 2006-07-07
Thanks. Seahorse uses GPG keys and could be a bit of overkill for me. I'm looking for something that I can use to encrypt some files using simple password.

---

### Post by unclben on 2006-07-22
> **wifiabc said:**
> Thanks. Seahorse uses GPG keys and could be a bit of overkill for me. I'm looking for something that I can use to encrypt some files using simple password. That's exactly what I'm looking for! I have tried GPG (via various front ends, and the CLI tool), but all are overkill for me. I don't need keys, I don't need signatures. All I want to do is strongly encrypt my offsite backups (made only once a month or so) with a passphrase.

---

### Post by Greg2 on 2006-07-22
> **wifiabc said:**
> Thanks. Seahorse uses GPG keys and could be a bit of overkill for me. I'm looking for something that I can use to encrypt some files using simple password.
This works very well for me:
[http://doc.gwos.org/index.php/Encrypter_Decrypter_Script](http://doc.gwos.org/index.php/Encrypter_Decrypter_Script)

---

### Post by Brocco on 2006-07-23
> **unclben said:**
> That's exactly what I'm looking for! I have tried GPG (via various front ends, and the CLI tool), but all are overkill for me. I don't need keys, I don't need signatures. All I want to do is strongly encrypt my offsite backups (made only once a month or so) with a passphrase.
GnuPG is the gold standard for file encryption.  It's true it has lots of options, but you may ignore them.  To use it as you want with a passphrase to encrypt a file named **plaintext**:

[INDENT]**gpg --symmetric plaintext**[/INDENT]

It will ask you for a passphrase and then produce an encrypted file named **plaintext.gpg**.

Brocco

---

### Post by unclben on 2006-07-23
> **Brocco said:**
> GnuPG is the gold standard for file encryption.  It's true it has lots of options, but you may ignore them.  To use it as you want with a passphrase to encrypt a file named **plaintext**:

[INDENT]**gpg --symmetric plaintext**[/INDENT]

It will ask you for a passphrase and then produce an encrypted file named **plaintext.gpg**.

BroccoThanks, Brocco. I had a feeling that, despite my previous troubles with it, GPG would be the best turnkey option... So, yesterday I went digging through a bunch of documention linked from the GPG homepage.

It turns out, I'd been messing up my option flags when I had tried to do symmetric encryption the last time. You're absolutely right, GPG's symmetric encryption is exactly the functionality I've been looking for.

---

### Post by jimmah6786 on 2008-01-19
Is there a way to add this to the Seahorse frontend, so I dont have to opena terminal everytime I want to encrypt something using symmetric option.

Thanks

---

