---
title: "ISO md5 issue (no previous posts)"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by sixguncynic on 2010-10-30
I am attempting to rescue/re-purpose one of my parent's desktops as a general use web/document computer with Ubuntu. I have two copies of Karmic that I've used a bunch of times that are now semi corrupt (scratched).

Using power ISO I was able to pull the iso apart and rebuild the files using the online repository to replace the individual files (there weren't many) that CRC'd. I've checked every file against the provided md5 checksums and they all match. I pulled the boot info from the original ISO and used it plus the re-built iso to burn a new image (I've done this dozens of times with trashed Windows backup disks.) 

Of course, I can't boot from it ('checksum error...sorry')

Before someone says "DOWNLOAD a new copy" keep in mind that I would if I could. Sadly my parents have a satellite connection with a bandwidth cap. Their current usage is fairly high and 600MB would put them fairly close to the cut off. I really don't want to drive all the way home, download the file, and then drive all the way back.

SO, does anyone have any ideas how I can go about figuring out exactly which part of the image is causing the checksum to fail? Alternatively, if I am satisfied that the files are correct is there any way I can force the install to ignore the checksum? (While booting off CD, I know I can do it within Windows but I have no desire to keep Windows)

---

