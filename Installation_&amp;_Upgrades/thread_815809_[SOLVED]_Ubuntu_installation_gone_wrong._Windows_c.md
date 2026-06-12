---
title: "[SOLVED] Ubuntu installation gone wrong. Windows completely wiped."
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by kewe86 on 2008-06-02
Please I hope I am posting in the correct thread.

Ubuntu will not let me login. It says bash:null/dev Permission denied.

Please what do I do to fix this. thank you in advance.

---

### Post by jualin on 2008-06-02
Someone in another forum suggested typing in the terminal > sudo chmod a+rw /lib/udev/devices/null. This is the link [https://launchpad.net/ubuntu/+bug/63031]("https://launchpad.net/ubuntu/+bug/63031"). Try it, and i hope it helps.

---

### Post by kewe86 on 2008-06-02
hi thanks, that worked. Now i can login.

But when ubuntu is booting up, I do not see the Ubuntu logo with the orange progress bar. 

Any idea how I can enable this. All I see is texts as before with [ok].

Thanks in advance.

---

### Post by jualin on 2008-06-02
I am glad that helped!. The orange progress bar problem I dont know how to fix, sorry about that. I recommend you to create a new thread with the new issue and mark this one as solved, so that you can get help easier. Sorry I could not help you more.

---

