---
title: "Software Center Wont Download"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by HunterAnderson on 2010-02-16
Alright so when I go to the Ubuntu Software Installer and and I try to install software, it wont let me. I can look at the software and choose which to install. It will ask me for authentication and it accepts it but when downloading it, it never passes 0%. Does anybody have any ideas whats wrong? Thanks so much for any input.

-Hunter

btw im running Ubuntu 9.1 64-bit

---

### Post by crlang13 on 2010-02-16
A couple questions:

I assume you're connected to the internet when you attempt to download and install new programs?  It may be "yes, logically!" but a few people don't realize that the package actually needs to be DOWNLOADED.

Does your internet connection require you to run through a proxy?  

Can you download programs through the synaptic package manager? system > administration > synaptic package manager

Can you install updates? system > administration > update manager

are any of the above to programs open when you try to use the softer center?

---

### Post by HunterAnderson on 2010-02-16
-lol Yes i am connected to the internet, but there isn't any proxy that its running through.

-When i tried to run synaptic package manager an error came up and wouldn't let me continue.

-When i tried to run the update manager and check for new updates the following error came up:
[B]
--E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to --correct the problem. 
--E: _cache->open() failed, please report.[/B]

-Afterwards i ran it in terminal and it installed flash player correctly. Then after running the update manager and checking for updates the error didn't return. (but there weren't any updates either)

-I went and tried synaptic package manager one last time and it worked fine. Not sure what the matter was or how running said command in terminal could have made a difference.

-I went ahead and tried the software center one last time since synaptic manager worked and it worked fine. I'm not sure what difference was but it seems to work fine.

---

### Post by crlang13 on 2010-02-16
sweet:p

dpkg is used to manage the packages - so, if it's not set up correctly, you can't get your packages to download and install correctly!

And who said Linux was difficult to use?  There was a problem, it you were automatically told hold to fix it by the operating system!

---

### Post by HunterAnderson on 2010-02-16
haha yea. Thxs. For things like that i like linux so much more than windows but i was raised on windows so this is all so new to me. Thanks again.

---

### Post by saeedmar on 2010-02-20
Hi, thanks Man, I'm new to ubuntu and wanted to reinstall ubuntu because of this problem; but your help made it easy for me to install softwares; Really thank you, and I hope to undesrtand these commands as soon as possible
Thanks again
=======================
In the world that there is no any walls and fences; There is nor need to WINDOWS nor GATES.

---

