---
title: "An Error occured during upgrade (HELP!?)"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by HypnoSquid on 2008-11-28
i am a new convert to linux from windows. i have correctly installed ubuntu 8.10, and twice now i have attempted to upgrade my software using the update manager (pops up to tell me updates are available) both previous times my computer froze during the download or install steps when i try to open the music player or anything else at all. so i have to restart.

today i had some things to do so i was going to let the updates install, but when i start the update manager and then click install updates i get an error window that says this 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

then when i go to the terminal and run "$ sudo dpkg --configure -a" i get the following error: 

"dpkg: parse error, in file `/var/lib/dpkg/updates/0124' near line 1:
 newline in field name `"

what should i do to update my software? i am new so i dont really know my way around very well. if anyone can help me with this problem please post here. thanks.

---

### Post by HypnoSquid on 2008-11-28
also this keeps me from installing any packages at all. i tried installing thunderbird and it gives me the same error. can anyone help me out here?

---

### Post by HypnoSquid on 2008-11-28
ok i fixed it. the second message i got (from the terminal) told me there was an error in a file, so i went to that file and deleted it and the two after it. then i ran 2 commands from an error message i got from the add/remove manager and restarted and now the problem is fixed. if anyone else has this problem send me a PM and i will give you more accurate description of how i fixed mine to try to help you out.

---

