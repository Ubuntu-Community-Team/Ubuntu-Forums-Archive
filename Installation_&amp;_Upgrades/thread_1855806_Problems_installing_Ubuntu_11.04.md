---
title: "Problems installing Ubuntu 11.04"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by The Weather Man on 2011-10-06
Hi all

I recently finished downloading ubuntu 11.04 on to my XP machine. I used the "run it with windows" option and waited for the 700MB download to complete which it did. It asked me to reboot to finish installation, however when I reboot I see no option to run ubuntu?

Should boot manager pop up automatically or do I have to enable it somehow?

Any help appreciated and I will provide further information if requested.

Thank you.

---

### Post by oldfred on 2011-10-06
Welcome to the forums.

Did you install with wubi or inside the Windows NTFS partition. Then it uses Windows to boot and should have edited Windows boot.ini so you get a choice on which to boot. Check you boot.ini. Perhaps timeout is too short to see choices?

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by The Weather Man on 2011-10-07
> **oldfred said:**
> Welcome to the forums.

Did you install with wubi or inside the Windows NTFS partition. Then it uses Windows to boot and should have edited Windows boot.ini so you get a choice on which to boot. Check you boot.ini. Perhaps timeout is too short to see choices?

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Hi Oldfred

I installed using wubi. I'm not sure about the boot.ini but boot manager does not appear at all not even for an instant. All that comes up is the black screen that has always been there with "start xp" or "recovery console"

I will follow the guides you provided and hopefully I can find a resolution, thank you

---

### Post by The Weather Man on 2011-10-07
When I go to control panel and click "system" then "advanced" and finally "start up and recovery" it does not show ubuntu there at all...

It shows "windows xp home edition" - "do not select this/debug" - "microsoft windows recovery console"

I uninstalled ubuntu and am reinstalling it now using wubi again so see if anything changes

---

### Post by The Weather Man on 2011-10-07
I have tried downloading 11.04 again using wubi but it ends in the same result. No boot manager on start up and no way to run ubuntu :(

I have looked at the guides oldfred has provided but cannot find a resolution to the problem.

Maybe there are other options for me to try?

---

### Post by dino99 on 2011-10-07
how i do it:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by The Weather Man on 2011-10-07
Thanks Dino 

I'll give it a shot.

Seeing as though this thread is no longer about wubi I will mark it solved.

---

