---
title: "Ubuntu 9.10 35 seconds boot"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by amirage on 2009-10-22
Hi all

As the topic suggested, don't you think the boot time for Ubuntu 9.10 is a bit too long? Ubuntu 9.04 used to boot in 15 seconds or so. I know I can't really compare the two OSs since 9.10 is still in the beta phase. However, I'd love get your views on how I can improve the boot speed. Fyi, I upgraded my 9.04 installation to 9.10 rather than do a fresh install of 9.10.

I have a Dell XPS 1730 laptop on which the OS is installed.

Let me know your views.

Amit

---

### Post by beastrace91 on 2009-10-22
Fresh install of Karmic 9.10 beta with all current updates to it boots in around 15 seconds on my EEE with a high speed SSD. This is down from around 30ish on Jaunty.

Maybe try a fresh install? I always find upgrades with any OS to be messy...

~Jeff

---

### Post by amirage on 2009-10-22
Hey Jeff

Thanks for your insights. In fact, I'm tired of doing a fresh install of Ubuntu 9.10. I normally install Ubuntu inside Windows via Wubi. It's such an ingenious way of installing the OS of course with the side effects. Installation of 9.04 went like a breeze and always did so, but when I tried doing the same with 9.10 it installed the OS etc and at the time of rebooting I see coloured deaths - green, blue, yellow and the the PC reboots. When the PC reboots, I select Ubuntu from the Windows MBR...then Grub crashes with no recovery insight. Hence, I decided to install Ubuntu 9.10 through the upgrade option in 9.04.

Did you install 9.10 through Wubi? I don't want to install 9.10 through the Live Cd for the reason that I might replace Windows MBR with Grub, And since Grub 2.0 is still in its nascent stages, corruption of the same could make my PC unusable until I do a fresh painful install of Windows...

Please help me with your suggestions.

Amit

---

### Post by P4man on 2009-10-22
Is that 35 seconds from grub to desktop ? If so, wow. On mine it takes about 2x longer on either jaunty or karmic.

If instead you're looking at bootchart, then realize the old bootchart only measured until log in screen, the new one keeps running until you have logged in and the system becomes iddle.

---

### Post by amirage on 2009-10-22
Oops Sorry my bad...

I should've mentioned that..It's 35 seconds from Grub to Login screen. Login to desktop is 2 seconds. 

Please let me know your views.

Amit

---

### Post by scouser73 on 2009-10-22
Before I upgraded to the beta of Karmic my boot time was 21 seconds, now with a fresh install of Karmic I get a boot time of 1.09 minutes.  I'm hoping once the finished version of Karmic comes out that the boot times will increase but saying that, I leave my PC on for days at a time so it's not that important for me.

---

### Post by P4man on 2009-10-22
My view is I think I want your laptop lol. From login to idle desktop is closer to 20s here (granted, I do load a ton of stuff, from compiz, to docky, an IM, gmail notifier and what not). I also noticed Virtualbox kernel drivers slow my boot considerably.

Anyway, on my setup jaunty and karmic beta boot times are about the same, karmic alpha was noticeably slower.

---

### Post by amirage on 2009-10-22
Thanks for the comment..Phew...at least I'm not alone..

---

### Post by amirage on 2009-10-22
Hey P4man..

Thanks for the comment. I also load a ton of stuff after logging such as compiz, empathy, bluetooth, network, background switcher, nvidia powermizer disabler, gmail notifier etc etc...I guess Karmic really saves this time as opposed to Jaunty that used to take a lot of time post login.

Anyway, let's hope Canonical irons out the issues and brings out a spanking OS...

Amit

---

### Post by beastrace91 on 2009-10-22
@amirage No I just installed 9.10 via the CD. I'm all Ubuntu/Linux on my computers. Don't even own a Windows license anymore hehehe.

~Jeff

---

### Post by amirage on 2009-10-22
Jeff...

I would have been in the same place as you are now..if it were not for my office accounts package...Confounded thing is Oracle based and the only way to run it is on a windows system. Hence, I have Virtualbox running most of the time.


Amit...

---

### Post by tarps87 on 2009-10-22
> **amirage said:**
> Hey Jeff

Thanks for your insights. In fact, I'm tired of doing a fresh install of Ubuntu 9.10. I normally install Ubuntu inside Windows via Wubi. It's such an ingenious way of installing the OS of course with the side effects...

One side effect being it is running of a ntfs partition not ext as it was designed for, bare in mine that is can have strange effects, even if both installs are running from ntfs partitions.

---

### Post by phillw on 2009-10-22
Unless you need to often switch OS's, then installing ubuntu side by side with your windows install may be a better option. I too have some accounts s/ware that is mac / windows only - so i keep my vista partition.

I'm waiting for 9.10 install to settle down a bit - I'm also nervous of the new grub upsetting my windows partition - and a new install upsetting my web-server, mysql server etc ..... I may be sticking with 9.04 for a while yet !!

Boot time - well, with a mail server, mysql server, web server, clamAV etc... all i'll say is it's still faster than windows without any of those services on it & doesn't need the 2GB RAM-BOOST that Vista does !!

Phill.

---

