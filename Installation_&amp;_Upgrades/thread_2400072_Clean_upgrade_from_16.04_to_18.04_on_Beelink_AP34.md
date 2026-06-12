---
title: "Clean upgrade from 16.04 to 18.04 on Beelink AP34"
date: 2018-09-02
forum: Installation &amp; Upgrades
---

### Post by martin_h on 2018-09-02
I have a Beelink AP34 fanless PC currently running a dual boot Windows 10 and Ubuntu 16.04LTS. I used it to experiment with some docker applications and when I tried to upgrade one of those it forced me to purge docker entirely. This done it rebooted properly and I reinstalled the docker + postreSQL and mayan-EDMS from  scratch. Though the installation went fine, it does not run and I suspect that is because there are bits and pieces of docker everywhere. 

I believe that the best way forward would be to do a clean installation but this is a huge challenge as installing it in the first place requires  jumping through all kinds of hoops like described in [https://gist.github.com/pjobson/e0b0c99f5d9affb28c1a2f33503c27c7](https://gist.github.com/pjobson/e0b0c99f5d9affb28c1a2f33503c27c7) and [https://www.youtube.com/watch?v=SwDE_eFchhY](https://www.youtube.com/watch?v=SwDE_eFchhY) . 

I wonder if, assuming that I can get it to boot from the standard USB stick, I could just install it over the existing 16.04 and allow it to update grub as it goes forward. It already has a ubuntu entry in the boot menu that seems to be persistent. 

Is there anyone who has some previous experience with this ? 

Thank you in advance

Martin

---

