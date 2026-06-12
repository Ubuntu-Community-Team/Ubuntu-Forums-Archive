---
title: "Maverick Meerkat CD Install Failure"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by caffeinated blood on 2010-10-12
I've just downloaded Ubuntu 10.10(final release), burned the ISO to CD using Brasero. The md5sum matched Ubuntu Hashes list. So I attempted a clean install with the CD. It will run with the Ubuntu logo for a minute then I either get a full "graphical disaster" screen or a partial screen with a cancellation choice-window prompt and a complete crash. I have to reset for a reboot. I've tried this multiple times and each time the same results. Anyone else having a problem installing this new distro and does anyone have an answer why this is happening?

---

### Post by mörgæs on 2010-10-12
Can you install using the alternate CD?

---

### Post by caffeinated blood on 2010-10-13
Sorry for the delay in response to your suggestion of trying the Alternate download/CD to install Ubuntu 10.10. Please forgive any ignorance on my part, but your suggestion makes me question how safe are peer-to-peer downloads? Should I have any concern for rootkit(s), or the like, or any unwanted access to my computer?

---

### Post by mörgæs on 2010-10-14
By all means, use torrents if possible. You can do a MD5SUM 'fingerprint' test of the downloaded ISO to confirm that the file has not been changed. 

Here is the MD5 list:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by caffeinated blood on 2010-10-18
After seeing that there are multiple issues with the new Ubuntu distro from other posters on the web I've decided to wait a couple or more weeks and try again or maybe give the alternate download a shot. Thank you for your help!

---

### Post by psusi on 2010-10-18
> **mörgæs said:**
> By all means, use torrents if possible. You can do a MD5SUM 'fingerprint' test of the downloaded ISO to confirm that the file has not been changed. 

Here is the MD5 list:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Bittorrent inherently validates the hash of every chunk of the file that you receive.

---

### Post by caffeinated blood on 2012-03-28
Sorry for not marking this thread as solved sooner, but the solution for my issue was to use the boot options at the start up of the Live CD and select 'Nomodeset' and boot. Also, edited Grub to permanently boot this way.

---

