---
title: "DELL Precision 7720 laptop upgrade to 24.04 now bad keyboard output"
date: 2024-07-16
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2024-07-16
Laptop ran fine until upgrade to 24.04.  Now typing "book", for example, into LibreOffice Writer or Evolution, gives something like bbboookkk. When PC is run under Win 11 Pro [I]nsider Build, everything works fine.  All my other PCs ungraded to 24.04 work fine.

What is going on and how do I fix it.

Thank you,

John

---

### Post by ActionParsnip on 2024-07-17
If you reboot to an older kernel, is it OK?
Are you using Wayland or Xorg?

---

### Post by cigtoxdoc on 2024-07-17
Thank you for your reply.  I am replying to you using another one of my PCs.  On the PC in question, once i enter the Ubuntu 24.04 password and 24.04 boots to completion, all other keyboard entries are gibberish, for example the password for Synaptic.  The same for any terminal commands.  I suspect PC is XOrg.

John

---

### Post by currentshaft on 2024-07-18
Is key repeat on in accessibility settings (search for "repeat")?

---

### Post by cigtoxdoc on 2024-07-18
Thank you very much.  REPEAT keys were set to ON.  Now working fine.  John

---

