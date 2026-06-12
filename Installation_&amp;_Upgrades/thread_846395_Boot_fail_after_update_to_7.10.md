---
title: "Boot fail after update to 7.10"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by DigitalHelix on 2008-07-01
Hi
I am a total noob to linux/ubuntu, but a long time dos/windows user.

Apologies for this post but I trawled for other boot problems in the forums and they didn't describe or solve my problem.

I have installed Ubuntu 7 on my Sony Viao laptop (clean install, all default options).

Boots and runs no problem. Very nice.

However, it recommends a whole raft of updates to download and install, which I just go ahead and let it do it's thing. It says it is updating to version 7.10 and asks for a reboot.

During boot up it goes through the grub screen and passed the logo/loading screen, but just as the brown 'gui' screen begins to appear (ie before the login screen) the system halts. The little timer/animation thing simply freezes.

It will not respond to any keyboard commands at this point (CTRL, ALT, F2 or CTRL, ALT DEL). Power off is the only option.

Selecting the previous kernel from the Grub menu gets exactly the same result.

Any help appreciated!
Jason

---

### Post by avtolle on 2008-07-01
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) Take a look at that, it may be you need one or more of the boot options listed. Good luck.

---

### Post by Rallg on 2008-07-01
Try booting to recovery mode. When you get to the command line,

sudo apt-get update && sudo apt-get dist-upgrade

When it finishes, re-boot. That might help, or not; but it is easy to do.

---

### Post by DigitalHelix on 2008-07-02
Hi
Thanks for the suggestions, but I haven't managed to get to the bottom of the problem. I have tried installing Ubuntu Studio, but I get to 85% of the install and it simply halts.

I am beginning tot think my laptop just won't run Ubuntu even though it is well over the spec, but 7.01 installs and runs no problem.

Any thoughts?
Jason

---

### Post by DigitalHelix on 2008-07-02
Hi
Thanks for the suggestions, but I haven't managed to get to the bottom of the problem. I have tried installing Ubuntu Studio, but I get to 85% of the install and it simply halts.

I am beginning to think my laptop just won't run Ubuntu even though it is well over the spec, but 7.01 installs and runs no problem.

Any thoughts?
Jason

---

### Post by DigitalHelix on 2008-07-06
Having not been bowled over with offers of helps or useful suggestions I have abandoned Ubuntu and gone for Mandriva. Installed and ran just fine.

---

