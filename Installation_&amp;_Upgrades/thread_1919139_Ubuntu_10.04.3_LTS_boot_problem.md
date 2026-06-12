---
title: "Ubuntu 10.04.3 LTS boot problem"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by hitman2k9 on 2012-02-02
Hello guys am facing a strange issue lately .I had a stable 10.04 setup about a month back suddenly one fine day the GRUB refused to boot . So I ran live CD and did a fresh install and again faced the same problem i.e after installation I do a restart and then GRUB refuses to start . Any solutions?

---

### Post by TheFu on 2012-02-02
A few questions:
* exact version of grub?
* exact error messages you are seeing? 
* Have you confirmed the hardware is fine?

Without a little more accurate information, it is hard to help.

---

### Post by hitman2k9 on 2012-02-02
Well GRUB version is the one packed along with the DVD of 10.04.3 . And I cant specify the error as GRUB screen doesn't load at all . The PC boots and stays at the black screen as if no boot loader is there . Hardware used to work with 10.04.3 before and even on live CD it works fine. When I install the latest Ubuntu 11.10 it works fine with GRUB . Only one thing changed i.e I updated BIOS of my Motherboard ,will that affect GRUB?

---

### Post by Penguinnerd on 2012-02-02
What you describe sounds like a BIOS issue. Try fiddling with settings in the BIOS. If it doesn't even get to GRUB, there's probably something else wrong.

It's also possible that the BIOS update didn't work right. That's a common and sometimes disastrous problem.

---

### Post by hitman2k9 on 2012-02-03
well as of now the latest GRUB that comes with 11.10 works so is there a way I can implement it to run 10.04.3 ?

---

### Post by hitman2k9 on 2012-02-04
any help?

---

### Post by westie457 on 2012-02-04
> **hitman2k9 said:**
> well as of now the latest GRUB that comes with 11.10 works so is there a way I can implement it to run 10.04.3 ?

Probably not which is not what you want to hear.

However this might be the solution for you. [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Read through at least twice to understand what you will be doing and then follow each instruction as it comes up. Failure to do this correctly will bork your system.

---

### Post by Penguinnerd on 2012-02-06
Disregard my original comment here.

I temporarily misunderstood the last few posts.

Did you ever get it working?

---

### Post by hitman2k9 on 2012-02-08
I had a xubuntu 11.10 installed already .. so after uinstall ubuntu 10.04.3 I did a update grub on XUbuntuIt read ubuntu 10.04.3 and 10.04.3 worked fine . So is there a way to replace the GRUB ?
Technically this is not working as I cant control grub via 10.04.3

---

### Post by hitman2k9 on 2012-02-12
OK . I again flashed the same BIOS and this time I did reset it to factory settings and then did my tweaking and now GRUB loads and Ubuntu 10.04.3 LTS works :) .Strangely before I did reset the BIOS to default but that didn't help but anyhow its SOLVED now :) . Thanks for all the input guys .

---

