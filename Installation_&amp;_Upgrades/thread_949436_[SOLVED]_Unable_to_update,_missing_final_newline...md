---
title: "[SOLVED] Unable to update, missing final newline..."
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by CUJimmy on 2008-10-16
Hi,

I am relatively new to linux, and was wondering if you can help. I had a system crash yesterday (I am running Gutsy), but the computer restarted ok and I thought everything was fine. However, today when I attempted to install the avant windows navigator, I was met with the error:

E: /var/cache/apt/archives/kpf_4%3a3.5.8-0ubuntu2_i386.deb: files list file for package `kpf' is missing final newline

Upon checking, I get this error when I try to complete any updates. Reading around, I wonder if the file has become corrupted. However, I couldn't find anybody who has had the exact same problem. Can anybody help please?

Cheers, Jim

---

### Post by Pumalite on 2008-10-16
sudo apt get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by CUJimmy on 2008-10-16
> **Pumalite said:**
> sudo apt get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade

Hi,

Thanks for the suggestion. However, in trying that the final command was met with:

. . . 

Fetched 8214kB in 1s (8100kB/s)    
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/tzdata_2008g-0ubuntu0.7.10_all.deb (--unpack):
 files list file for package `kpf' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2008g-0ubuntu0.7.10_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas?

Jim

---

### Post by CUJimmy on 2008-10-16
Thanks to some friendly advice, this problem has now been solved. The problem was in the directory:

/var/lib/dpkg/info

The file kpf.list had become corrupted. Essentially, all this file contained was a list of all *kpf* files within this directory, so we rebuilt the file on this premise. We did the following:

cd /var/lib/dpkg/info
sudo mv kpf.list kpf.list.bork
locate kpf > ./kpf.list

Then open up kpf.list in a text editor, append a blank line to the end and save. If successful (as this was) updates should now work and kpf.list.bork may be removed.

Cheers, Jim

---

