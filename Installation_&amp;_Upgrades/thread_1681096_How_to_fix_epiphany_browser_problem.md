---
title: "How to fix epiphany browser problem"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by jiex on 2011-02-03
Hello
I have an issue with Epihpany browser. I tried it but did not much like it so I removed it in a clean up. I mucked that up and now when I do upgrades, I receive an error message that epiphany could not be upgraded. I've tried fixing this and the various fixes do not work. I would be most grateful for an assistance.

This is the output from the terminal:
~$ sudo dpkg -P epiphany-browser
(Reading database ... 325373 files and directories currently installed.)
Removing epiphany-browser ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing epiphany-browser (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 epiphany-browser

---

### Post by Mat11 on 2011-06-05
Hi i'm having awful time concerning problems trying to get rid of files left behing after Epiphany-browser deletion and removal. Have tried the lot you name it using terminal commands , synaptic checks for left overs and checking it was fully removed in software center. Tried to install one other Unix based browser only to find out i've lost control over my bookmarks.!--  Could not install my bookmarks to the new browser.

How can i take control as an administrator and get rid of the unwanted Epiphany browser files.

Hope someone can help

Matt (matt11)

 I have just tried sudo dpkg -P epiphany-browser--- the purge clearly showed it worked but the files and folders are still there why ???

---

