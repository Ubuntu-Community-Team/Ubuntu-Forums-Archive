---
title: "Trouble with Adept"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by magic-chef on 2008-04-04
When I try to update via Adept I get the following message.  I have tried several ties with the same result:

Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).
Would you like to attempt to resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself.

The above is copied from the error window.

Thanks

---

### Post by nikki on 2008-04-04
I am having the same issue. I just installed Kubuntu on my computer and the first thing I did was update it. I then get the above error.
The crash handler does not fix the issue.

---

### Post by nikki on 2008-04-04
After doing further searching on the forums, I believe running

dpkg --configure -a

in the terminal fixes the issue. It fixed it for me.

---

### Post by magic-chef on 2008-04-05
I posted on Kubuntu also.  Please find the solution recommended by a dibl.

[http://kubuntuforums.net/forums/index.php?topic=3092977.0](http://kubuntuforums.net/forums/index.php?topic=3092977.0)

Thanks for the help!

---

