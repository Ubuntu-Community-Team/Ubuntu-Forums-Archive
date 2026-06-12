---
title: "Cannot update to GRand Unified Bootloader version 2."
date: 2024-11-18
forum: Installation &amp; Upgrades
---

### Post by blingublingu on 2024-11-18
Hello,

I am running Ubuntu 24.10 and I am trying to upgrade to GRand Unified Bootloader version 2. 

I get the error:
grub-efi-amd64-signed: Depends: grub2-common (>= 2.02+dfsg1-5) aber 2.12-5ubuntu5.1 soll installiert werden.

Any ideas what to do?

---

### Post by grahammechanical on 2024-11-18
I am running Ubuntu 24.04.1 LTS and it has Grub 2.12 version. I would be very surprised if Ubuntu 24.10 had a lower version.

Edit: I just loaded into Ubuntu 24.10 it has Grub 2.12 version. So, why do you need to upgrade to Grub version 2 when you should already have it?

Regards

---

### Post by Rubi1200 on 2024-11-18
What issue are you trying to resolve?

The more you tell us, the easier it will be to offer solutions.

---

### Post by blingublingu on 2024-11-19
Thank yo. I am running the update manager and it says one of the updates is GRand Unified Bootloader version 2. When I hit "install now" I get the error that i mentioned before.

---

### Post by Rubi1200 on 2024-11-19
Open a terminal with Ctrl+Alt+T and run the following commands in order:

```
sudo apt update

sudo apt upgrade
```

If there are errors or anything else at the end of the second command, then post it back here for review.

To post using code tags for the output click on Go Advanced and then paste and highlight the text, then click on the # icon.

---

### Post by blingublingu on 2024-11-19
Thanks a lot Rubi!  That did it.

---

### Post by Rubi1200 on 2024-11-19
Problem solved?

Good to hear.

Running apt update and apt upgrade will often fix most issues.

Please mark the thread Solved by using the Thread Tools at the top of your first post.

---

