---
title: "Upgrade Ubuntu 9.10 -&gt; 10.04 Too many errors your computer may now be unusable."
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by StarChaser93 on 2010-05-18
This morning I decided to finally upgrade from 9.10 to 10.04. It downloaded all the packages fine etc. etc. however when it got to the actual install/upgrade process it died.

The only real error I remember occurring was that it was unable to install upgrade 'apt' since after that the whole terminal window was full of errors.

I then got the error message mentioned in the title of this post. So I tried to do the same upgrade again. The window wouldn't open. I tried several different programs however I couldn't get any new GTK windows.

My next idea was to restart X and work from any errors I get from there however I was dumped in the command line so I logged in and ran `startx` which blanked the screen for several minutes but then crashed.

I thought "That's cool. I can just re-install 9.10." So I rebooted into the LiveCD, went to go copy my home directory... Oh, it's encrypted. I guess I'll boot back into the original install and try and decrypt it there.
It didn't decrypt it automatically and I the command in the readme also failed to work.

So, now you have the story I'll give you my question. How can I decrypt my home folder for backup? Did I miss my chance by rebooting while it was already decrypted.

The startx and ecrypt-mount-private errors are repeatable if required.


Thanks for taking the time to read this and any help would greatly be appreciated.

~SC

EDIT: Bonus question!

My system files are home directory are on separate partitions. If I do an advanced install and overwrite just the system files, can I reuse that home partition without overwriting it AND can I just make another user called the same with the same password and thus decrypt the home folder? Or will I just bork the whole thing?

---

