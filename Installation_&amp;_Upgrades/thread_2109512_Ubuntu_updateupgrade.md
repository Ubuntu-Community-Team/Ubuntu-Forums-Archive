---
title: "Ubuntu update/upgrade"
date: 2013-01-27
forum: Installation &amp; Upgrades
---

### Post by thegutterpoet on 2013-01-27
I have recently returned to using Ubuntu and want to get it as shipshape as possible...the update manager finds problems whenever it tries to update, and when I run the command in the terminal i get this-
[B]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E585066A30C18A2B

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.[/B]

Should I be updating? upgrading? or installing a new ubuntu? I'd rather not have to wipe the current ubuntu off then start afresh///

---

### Post by Sef on 2013-01-27
What version of Ubuntu do you have installed?

---

### Post by thegutterpoet on 2013-01-27
Ubuntu 12.04 LTS

Update Manager says 631 updates have been selected. 13.2MB will be downloaded/

When I click INSTALL...I get an error message-
Check your internet connection
Failed to fetch [http://deb.opera.com/opera/pool/non-free/o/opera/opera_12.02.1629_amd64.deb](http://deb.opera.com/opera/pool/non-free/o/opera/opera_12.02.1629_amd64.deb) 404  Not Found

My internet connection is fine. the wireless cuts in and out, but the ethernet cable gives a solid, constant connection.

The information I showed in the firts post was after trying the sudo update command in the terminal.

---

### Post by Bucky Ball on 2013-01-27
The Opera repository (third party) seems to be broken. Could be down or dead for some reason.

Go to Software Sources and untick anything with Opera in the title and try again (should be in the 'Other Software' tab).

---

