---
title: "Ubuntu Upgrades/Updates"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by srvfan74 on 2012-11-07
Over the years I have used ubuntu's software in its various releases. I still consider myself a relative noob. However, my question and problem pertains to the ongoing software updates and eventual version upgrades. Through each version of the Ubuntu system I have always enjoyed using the software until boom! I do an upgrade and it will not boot. This happens to me on different machines and different scenarios including dual boot systems and single boot systems where linux was the only OS. I always find myself having to start from scratch with a fresh install after an 'upgrade' trashes something. I have not been using Ubuntu/Linux for the last year or so because of this problem.

So, I suppose what I want to understand is the proper way to approach the whole upgrade/update deal. I wish I could understand better what the OS is trying to do that always causes this problem for me. Should I never do an 'upgrade' and simply do fresh install instead with each new release?  What is it about the upgrade process that I have to be careful of?

---

### Post by Sonsum on 2012-11-07
They have always gone flawlessly for me. Do you happen to have a dedicated (such as Nvidia or AMD/ATI) video card? I know that can be problematic when installing a new kernel (which happens on most version updates).

---

### Post by 2F4U on 2012-11-07
You need to try to understand how complex the task of upgrading a whole operating system is. Then consider the sheer number of different hardware constellations and software installations and you know why upgrading fails so often. This is not a problem of Ubuntu alone and there are Linux versions where upgrading is not supported due to the risk.
If you want the least disturbance, my advice is:
- choose a LTS release
- stick with it as long as you can; with 12.04 this is up to 5 years
- when you see the need for a newer release, download LTS
- make a backup of your data and do a fresh installation

By doing this, you will spend less time upgrading - a fresh installation is faster - and less time troubleshooting a failed upgrade.

---

### Post by oldfred on 2012-11-07
Welcome to the forums.

Some do have good success with upgrades, but it seems to depend on your hardware and if you have done a lot of customization. Sometimes those settings or if you have added ppa's will cause issues.

I upgraded from 6.06 thru 9.04. But had to do a clean install with 9.10 when I converted to 64 bit. My upgrades always had issues, usually related to nVidia and related settings. The clean install I did for 9.10 converted me to clean installs. But I changed to leave all data in a separate data partition and just install the system in a 25GB / partition. Then I had my new install to verify it worked before erasing my old install, since root was small. Since had a new hard drive at that time with lots of room I still have all my "new" installs. But it is time to houseclean. :)

---

### Post by snowpine on 2012-11-07
Upgrading is fully recommended/supported by Ubuntu's developers, so if you have a problem with the upgrade it is a **BUG** and you should test and report it through the proper channels.

The apologists will tell you to do a fresh reinstall instead...

---

### Post by mrfreen on 2012-11-15
The OP describes my experience as well. Perhaps the release cycle is the reason. Perhaps they are forcing out buggy software.

Because of the long history of botched "upgrades", this time I've chosen the LTS release. However, this morning I updated all the software only to find that it's trashed my nvidia drivers.
It was working fine, I ran the recommended update, and now the system doesn't work.

I understand that it's a complicated process, but that's kind of beside the point. If the Ubuntu devs aren't up to the task, they shouldn't make promises.

---

### Post by mastablasta on 2012-11-15
> **snowpine said:**
>  
The apologists will tell you to do a fresh reinstall instead...
 
i will tell you to do fresh install since it is way faster than upgrade. even on fast intrnet connections.
 
> **mrfreen said:**
>  
Because of the long history of botched "upgrades", this time I've chosen the LTS release. However, this morning I updated all the software only to find that it's trashed my nvidia drivers.
It was working fine, I ran the recommended update, and now the system doesn't work.
 .
first off on upgrade you need to uninstall drivers before doing the upgrade.
 
second if we are really talking about software update:
- if you are using proprietary drivers then it's nvidias "fault" 
- if you are using opensoruce drivers then it's ubuntu's "fault", however you cna just boto into older kernel and it should work.
 
and third for the least hastle use security updates only. ofcourse this won't update any software's new features as i udnerstand but only patch security holes.

---

### Post by Mark Phelps on 2012-11-16
Well, for the first time in a LONG time (years of upgrading!), I encountered the "upgrade-go-boom" problem myself. Fortunately, I was able to modify the kernel parms and get 12.10 booting OK.

Version upgrades are severely complicated by the fact that STILL, Canonical has failed to provide any roll-back capability; that is, if something goes wrong after the upgrade -- you are stuck!  You either have to fix it (which is not always possible since features sometimes get REMOVED with upgrades), or you have to reinstall your previous version -- from scratch.

So, I always advise folks to either (1) do a clean-install on a new partition (so the old version remains available), of (2) image off the old version using Clonezilla -- so you restore it if the upgrade goes bad.

---

### Post by Frogs Hair on 2012-11-16
A quick forum search will yield thousands of problems related to version upgrades. I tried once (9.10 to 10.04) and didn't like result because of mix of old and new versions and I had had other problems which lead me to a clean installation of 10.04. I apologize for no one but I will never upgrade again as long as I have the choice.

---

### Post by srvfan74 on 2013-04-23
Thanks everyone for your helpful posts. I have jumped back in with 12.04LTS and will avoid the upgrades and instead do clean installs after backups. Note that I did try to boot to different kernels with no success...it was a mess...and I think display drivers is the culprit for many problems.

---

