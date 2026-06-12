---
title: "[SOLVED]Vokoscreen don't work with &quot;ffmpeg&quot; installed in ubuntu 14.04."
date: 2014-10-09
forum: Installation &amp; Upgrades
---

### Post by hectorsales on 2014-10-09
Hello, I have the next issue, if i install** "ffmpeg" from the ppa ppa: mc3man/trusty****-media** when I open **Vokoscreen**  gives me a error:


> The process could not be started. Either the is called program is not installed, or the ffmpeg or avconv call Faulty or you 
have not over sufficient permissions to to the program. 

I think the problem is that vokoscreen runs **livab-tools (avconv****)** **fork of ffmpeg**. Is there any way to run vokoscreen without removing ffmpeg package ?

My distro is Ubuntu 14.04 (Unity).

**Edit :** I found the solution.

I create a symlink (simbolik link).

```

sudo mv /usr/bin/ffmpeg /usr/bin/ffmpeg_backup

sudo ln -s /usr/bin/avconv /usr/bin/ffmpeg


```

Best regards.

---

### Post by tissatussa on 2015-04-03
this solution works for me : this way, any call to ffmpeg is directed to avconv !  however, i wonder .. does it work for all programs which use ffmpeg? is the avconv options-format the same?

---

