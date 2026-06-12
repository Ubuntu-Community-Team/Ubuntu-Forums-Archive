---
title: "install cd doesn't recognize usb keyboard"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by dbclinton on 2008-05-01
Hi,
I tried installing Hardy desktop but the install program won't recognize my usb keyboard. Any ideas?

---

### Post by Aearenda on 2008-05-01
I assume this is happening at the first screen after booting from the CD - can you use that keyboard to get into the BIOS settings of the computer?
If not, try setting USB to 'Legacy' mode in BIOS - the wording varies from BIOS to BIOS. BUT, you would need to use an old-style keyboard to be able to set that option.

Or, just plug an old-style keyboard in and reboot to get past this point - the USB keyboard will be recognised as Ubuntu starts up, assuming it works!

---

### Post by dbclinton on 2008-05-01
Yup.
That was the trick: setting the BIOS to legacy (DOS) mode!
Thanks!

---

