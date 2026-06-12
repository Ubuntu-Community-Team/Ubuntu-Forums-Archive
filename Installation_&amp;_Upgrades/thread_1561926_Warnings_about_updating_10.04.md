---
title: "Warnings about updating 10.04"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by CShaum on 2010-08-26
My computer gives me a warning about updating.  Linux headers 2.6.32-24 and Linux headers 2.6.32-24 generic and Linux image 2.6.32-24 and Linux-libc-dev Can anyone tell me if these are safe to update? It tell me not authenticated. I hate to see my computer turn upside down when it run so nice.  Thanks

---

### Post by oldos2er on 2010-08-26
Can you run ```
sudo apt-key update
``` in a terminal, and if there are any errors please post the output here.

---

### Post by CShaum on 2010-08-27
This what the terminal told me, it all greek to me:
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2

Any input??

---

### Post by AlphaLexman on 2010-08-27
Look at:
```
man apt-key
```

---

### Post by wojox on 2010-08-27
When you upgrade you will still have access to the kernel your running now to fall back on.

That's what I'm using on two different computers and everything is running fine here.

---

### Post by CShaum on 2010-08-27
I typed the suggested man apt-key. I got lost what to do? You going to have to explain a bit more I'm lost. Sorry, somewhat a newbie Still learning this linux thing.

---

### Post by AlphaLexman on 2010-08-28
There are 'sources' you can get software from. The parent company of ubuntu is Canonical, they provide many programs and updates. Sometimes, users will build software or update it before it becomes 'mainstream', these are often called beta-packages. These packages are not 100% ready for public use, but usually work for the majority of users (there is always exceptions). Programmers often put their work on the internet for people to test, this is usually done via a 'PPA' (**p**ersonal **p**ackage **a**rchive)

You will need to install a password 'key' for each PPA you add to your /etc/apt/sources.list

The key should be found on the same web-page the 'source' file was downloaded from.

---

### Post by oldos2er on 2010-08-28
CShaum, can you run **sudo apt-get update** and post the output here?

---

### Post by CShaum on 2010-08-28
That's what I did last night. Did the get-apt update command to see what would happen. And sure enough it detected the very one that it was warning about. I launch off and updated and so far so it has been good. Apparently they can be trusted. Computer even booted a touch faster. :-)

---

