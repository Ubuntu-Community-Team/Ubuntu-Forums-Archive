---
title: "Issue with reading CD installing 12.04 server"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by darilon on 2012-05-08
EDIT: I solved the problem.  After burning about 10 different linux distros and having each one fail a pattern emerged.  For some reason, it could read the installers up till the point where a kernel was loaded and then there was a problem finding modules after that.  Swapping the optical drive was the solution.  Whether it's hardware or a buggy optical driver, I don't know, but at least the problem's solved.

I'm pretty sure this is an issue with drivers or something for the optical drive on an HP/Compaq Proliant ML570 server that was donated to our school.
 
Here's the situation:
 
I have the above computer (2 Xeon 1.7ghz/512k L2/3Mb L3 - 32bit) about 5gb RAM, 11 15k rpm ultra 320 scsi hdd's (5 72.8 Gb, 6 36.4 gb). When I try to install 12.04 Server, I get as far as "Loading installer components from CD and it gives a nice big error window stating "No kernel modules were found. This probably is due to a mismatch between the kernel used by this version of the installer and the kernel version available in the archive" - the message continues, but not much point in typing it all here. Syslog shows errors mostly relating to "I/O error, dev sr0, sector" and a different sector error for each. I've verified the CD on several other machines, so it's a good burn (I know how to burn an ISO). The optical drive in the box looks like it's connected by an IDE cable so it's likely not a scsi driver issue. 
 
Does anyone have any ideas how to proceed with this? I'm pulling my hair out right now. It's a nice piece of equipment and I'd like to set it up with my information systems class before the end of the school year.

---

