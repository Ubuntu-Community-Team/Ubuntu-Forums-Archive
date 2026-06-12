---
title: "Question about implications of upgrading TPM"
date: 2018-06-18
forum: Installation &amp; Upgrades
---

### Post by ranloe on 2018-06-18
I'm successfully running a dual boot laptop with full system encryption for the ubuntu disk (separate disks for each OS). I finally received the update from the laptop manufacturer to upgrade the TPM. I am using a guide online to assist me in the process. In the guide is written the following warning:

"Before proceeding, make sure you are not using BitLocker and your drives  are not encrypted. This guide will reset your encryption  keys/drives/fingerprint/etc!!!"

(the entire guide can be found here: [http://forum.notebookreview.com/threads/tpm-security-update.813300/](http://forum.notebookreview.com/threads/tpm-security-update.813300/))

I am hesistant to proceed, because i don't completely understand how the TPM works and what processes involve it, so i'm scared that if I upgrade the TPM, i'll lock myself out of my fully encrypted ubuntu system. Thank you for your time and consideration.
Respectfully

---

### Post by TheFu on 2018-06-18
You should be afraid.  Make a full backup, unencrypted, do whatever you want, then restore that backup to a freshly installed OS as needed.
Backups solve 1000+ issues and are always mandatory for encrypted storage.  ALWAYS!

---

