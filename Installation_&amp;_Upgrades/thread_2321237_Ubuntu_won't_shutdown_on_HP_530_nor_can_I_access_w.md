---
title: "Ubuntu won't shutdown on HP 530 nor can I access wifi"
date: 2016-04-21
forum: Installation &amp; Upgrades
---

### Post by NickStruggling on 2016-04-21
Hi ladies and gents,
I have just installed 16.04 on an old HP530 laptop with a Celeron M processor. The laptop will not turn off by selecting shutdown from the dropdown menu in the top left corner. It just gets to the Ubuntu shutdown screen with the little red and white dots and Ubuntu name/logo.

It also does not show any Wifi networks as available. I can connect to the internet via ethernet cable but I really need wifi access.

Please can someone help me? I tried several solutions as posted by people on these forums but none worked for me. Because I have no files to keep and I had made changes in the terminal I figured I would re-do the install again! So I have just done a fresh 16.04 install and come here begging for help! I have a totally clean 16.04 install ready.

Any and all help appreciated! Thanks in advance!
Nick

---

### Post by slickymaster on 2016-04-21
*Moved to the ***Installation & Upgrades*** sub-forum*

---

### Post by NickStruggling on 2016-04-21
Bump on this! Anybody got any help for me?

---

### Post by slickymaster on 2016-04-21
Understand that this is a forum populated by VOLUNTEER users (including the Staff) from every time zone around the world, people with real lives. That means that some questions may go unnoticed by the person with the perfect answer. In such cases, it is appropriate to bump a thread if you do not get a reply in a reasonable amount of time.

We have relaxed the 24 hour restriction on bumping. A 12 hour bump will expose your thread to a different group of people somewhere in the world.

---

### Post by dFlyer on 2016-04-21
Had a similar problem on a newer HP. Computer would not shut down, after about 5 minutes at the blinking dots it would reboot. I went to my /tmp folder and removed all files and did a hard shut down, with the power switch. On reboot when I reached the login screen I tried to shut down which worked. After I booted again I signed in this time and tried the shut down which worked. I don't have a wifi problem so can't be any help there. The command I used to wipe all files in the /tmp was I changed to /tmp with cd /tmp, that as root used sudo rm -rf * .* , that is * space .* . Word to the wise be very careful using the rm command as root.

---

### Post by NickStruggling on 2016-04-22
> **dFlyer said:**
> Had a similar problem on a newer HP. Computer would not shut down, after about 5 minutes at the blinking dots it would reboot. I went to my /tmp folder and removed all files and did a hard shut down, with the power switch. On reboot when I reached the login screen I tried to shut down which worked. After I booted again I signed in this time and tried the shut down which worked. I don't have a wifi problem so can't be any help there. The command I used to wipe all files in the /tmp was I changed to /tmp with cd /tmp, that as root used sudo rm -rf * .* , that is * space .* . Word to the wise be very careful using the rm command as root.

Thanks for your help dude! Much appreciated! My problem has been solved by folks over at a different Linux forum! Genuine thanks though! Seems like a legit solution.

---

