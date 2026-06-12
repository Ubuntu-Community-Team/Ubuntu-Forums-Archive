---
title: "can not get live 12.10 to boot up"
date: 2013-05-28
forum: Installation &amp; Upgrades
---

### Post by millstb1 on 2013-05-28
Hello ....
    I am treying to do a fresh install of 12.10 on a Dell laptop that has 10.04 running. The Cd boots and brings up a selection menu, i select the 32 bit install and then it hangs at cmain ... for 20 minutes and then goes to the GRUB prompt. Any ideas as to what's happening.

---

### Post by fantab on 2013-05-29
It could be that your downloaded copy of 12.10 is bad, do a [MD5Sum check]("https://help.ubuntu.com/community/HowToMD5SUM") on the downloaded iso. If it does not match then redownload, preferably use a torrent download.

If the md5sum is alright then it could be a case of 'bad burn'. Burn ubuntu.iso again to a different disk.

---

### Post by millstb1 on 2013-05-30
hello... thanks Fantab ... no the DVD is OK it will boot off another machine. It's starting to look like an incompatibility problem in an older DELL BIOS... I'm going to research that now, but if anyone has had similiar problems please let me know ....
thanks and a this is a great forum ...

miller

---

### Post by fantab on 2013-05-30
If you are having trouble with 12.10, then try Ubuntu **[12.04 or 12.04.1]("http://old-releases.ubuntu.com/releases/12.04.1/")**, as these version had good support for older hardware. 12.04.2 onwards things are a bit different. Also 12.04 is LTS and supported until 2017.

If you update from 12.04.1 to 12.04.2 then you are ok and the '[Hardware enablement stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")' is not applied.

---

