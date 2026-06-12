---
title: "can't get past boot sequence"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by ehcualp on 2008-07-18
I just installed xubuntu 8.04.1 on my (old) laptop. I had tried installing via the live cd, but it stops booting after diplaying "*Running Local Boot scripts (/etc/rc.local)        [ok]".
I couldn't get this to work, so i opted to get the alternate install disk. This installed xubuntu, But when i tried to boot up into it it gives me the same message as before, "*Running Local boot....".
I have searched this forum for any answers, and have found many, but none solve the problem. 

I tried changing the boot scripts, as seen in this topic,
[http://ubuntuforums.org/showthread.php?t=587499&highlight=past+local+boot+scripts]("http://ubuntuforums.org/showthread.php?t=587499&highlight=past+local+boot+scripts")

I tried ```
sudo dpkg-reconfigure xserver-xorg
```, as seen in this topic, [http://ubuntuforums.org/showthread.php?t=692381&highlight=past+local+boot+scripts]("http://ubuntuforums.org/showthread.php?t=692381&highlight=past+local+boot+scripts").  All that did was configure the keyboard, and nothing else.

From [http://ubuntuforums.org/showthread.php?t=416516&highlight=past+local+boot+scripts]("http://ubuntuforums.org/showthread.php?t=416516&highlight=past+local+boot+scripts"), i checked /var/log/messages, and /var/log/Xorg.0.log for any errors. The only error i found was on Xorg.0.log, It said ```
Fatal Server Error: no screens found
```.

The laptop im working with is an avertec 3200 series. Piece of junk, but it was free. OS is Xubuntu 8.04.1 installed via alternate install disk.

Thanks for the help in advance!

---

### Post by ehcualp on 2008-07-19
Bump.
 Isn't there anyone who can help me?

---

### Post by wpshooter on 2008-07-19
Have you checked the integrity of your Xubuntu CD by running the verification function that is found on the initial Xubuntu boot screen menu ?

How much memory does your laptop have ?

---

### Post by ehcualp on 2008-07-19
Thanks for your reply.
I did a bit more searching, and i found this answer, [https://answers.edge.launchpad.net//ubuntu/+question/8351]("https://answers.edge.launchpad.net//ubuntu/+question/8351"). By putting in the monitor section I was able to boot into it.

---

