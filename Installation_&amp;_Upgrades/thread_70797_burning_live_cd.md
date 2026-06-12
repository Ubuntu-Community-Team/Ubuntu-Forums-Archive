---
title: "burning live cd???"
date: 2005-10-01
forum: Installation &amp; Upgrades
---

### Post by kabanta on 2005-10-01
I just downloaded the Breezy Live CD ISO. The link is:
[http://se.releases.ubuntu.com/5.10/ubuntu-5.10-preview-live-i386.iso](http://se.releases.ubuntu.com/5.10/ubuntu-5.10-preview-live-i386.iso)
But the resulting FILE on my machine is:
ubuntu-5.10-preview-live-i386.iso.bin
The "bin" extension is not mentioned in any of the Ubuntu documentation I can find. Burning the file to disk as it is does not seem to result in a bootable CD. Am I supposed to remove the "bin" extension before writing the image to disk? If so, how?
Is this information posted somewhere obvious and I'm just missing it?
Sigh.

---

### Post by lisje on 2005-10-01
[QUOTE=kabanta]Am I supposed to remove the "bin" extension before writing the image to disk? If so, how?[/QUOTE]
Yes, you're supposed to remove the "bin" extension.
It's probably the browser which you've used to download the file, who added the additional ".bin" to the filename. 

Simply renaming the file should do the trick just fine.

---

### Post by kabanta on 2005-10-01
[QUOTE=lisje]It's probably the browser which you've used to download the file, who added the additional ".bin" to the filename. Simply renaming the file should do the trick just fine.[/QUOTE]
Ah, ok. I thought perhaps the "bin" indicated something specific about the ISO image as a binary for use on Live CD versus on an install-CD.
thanks!

---

