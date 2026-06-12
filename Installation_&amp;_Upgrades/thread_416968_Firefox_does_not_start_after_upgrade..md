---
title: "Firefox does not start after upgrade."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by YSH on 2007-04-21
I just upgraded to feisty, but now firefox doesnt open anymore. How to solve??

---

### Post by codingmaster on 2007-04-21
Hello!

What does:

sudo dpkg-reconfigure firefox

say?

Any errors?

Regards, Georgy Berdyshev

---

### Post by YSH on 2007-04-21
It says i should restart firefox, while the terminal is the only programm open.

---

### Post by codingmaster on 2007-04-21
Hmm.

Any firefoxes running, maybe as zombie after a crash.

What does:

ps aux | grep firefox

say?

Regards, Georgy Berdyshev

---

### Post by YSH on 2007-04-21
youssou   9047  0.0  0.3   2900   748 pts/0    D+   18:26   0:00 grep firefox

---

### Post by codingmaster on 2007-04-22
Hello!

Did you try it after a restart?

Also try again a dpkg-reconfigure!

When this will not help, make a backup of:

.mozilla in your /home/username/

and then delete .mozilla

Do you have some plugins / add-ons installed?

From time to time there are problems with installed add-ons.

Best regards, Georgy Berdyshev

---

### Post by Krams on 2008-01-13
Thank you. Deleting the .mozilla folder helped. Interestingly that folder in my $HOME was owned by user root and group root and I could not even do an ls on it. I sudo'ed and deleted the folder and firefox restarted fine. It created a new .mozilla with my name on it.

Thanks
Krams

---

### Post by scottym on 2008-03-16
Check you permissions in the .mozilla folder and enable your user name and execute as program. Should do the trick.

---

