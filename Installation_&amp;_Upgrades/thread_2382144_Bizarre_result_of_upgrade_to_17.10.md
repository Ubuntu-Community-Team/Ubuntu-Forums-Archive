---
title: "Bizarre result of upgrade to 17.10"
date: 2018-01-09
forum: Installation &amp; Upgrades
---

### Post by fred66 on 2018-01-09
I upgraded my old faithful PCeee from 17.4 to 17.10 , as I have done several versions in the past, but ended up with a split screen 3/4 of the screen are like a black console, with a line of gibberish on top, the rest is the right 1/4 of the regular Lubuntu desktop. It's obviously unusable. I am attaching a picture. I never saw something like this. Re-installing Lubuntu from a DVD did not change anything - still the same screen. I could do a full install from scratch, but I wonder if anybody had an idea how/if this could be fixed without it (or, for that matter, if a total install would not solve the problem anyway).

Thank you
Fred

---

### Post by RobGoss on 2018-01-09
How does the live desktop run on this machine?

It's hard to say what maybe causing this issue with out knowing what the spec are for this machine

---

### Post by fred66 on 2018-01-09
Yes, I know - it's a (by now very old) Asus Eee PC. By the way, the live desktop from the DVD was fine. After the installation I had that odd screen, same as after I first tried an upgrade. However, I am marking this thread as resolved, since right now, a few hours after I made that shot, the desktop is suddenly all right. I have no idea why it started that way, and even less why it is now working fine, which is frustrating, but I doubt it would be easy or worthwhile to dig deeper...

---

### Post by fred66 on 2018-01-09
Oops. After updating the installation, the system went back to the split unusable screen. This is an Asus Eee PC 901. It has a 64G SSD (my upgrade, since the original 20G SSD went South very early). It should have 1G SDRAM at 667MHz,  1024X600 WSVGA display, an Atom 1.6 GHz CPU, as I gathered from the web.

---

### Post by sudodus on 2018-01-10
How is 'good old' 16.04 LTS working on your eeePC? It could be worthwhile testing it (and it has longer support time than the version 17.10). Are you running standard Ubuntu or one of the community flavours. Lubuntu, Ubuntu Budgie, Ubuntu MATE and Xubuntu have lighter desktop environments (and come with some lighter application programs too).

See the following link (and links from it),

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by fred66 on 2018-01-11
It's been running Lubuntu (it's a 32 bit and pretty slow machine after all). I guess, I'll follow your advice, and try 16.04 (it was running 17.04 just fine before the botched upgrade). Thanks for you comments.

---

### Post by mörgæs on 2018-01-13
[https://ubuntuforums.org/showthread.php?t=2376580](https://ubuntuforums.org/showthread.php?t=2376580)

---

### Post by fred66 on 2018-01-17
Thank you, as I am still waiting to update my desktop. The Asus is really old, so no UEFI. It still comes up with the unusable split screen, even after a completely clean install. Could it have something to do with the switch away from Mir to Wayland (or whatever is in 17.10)?

---

### Post by mörgæs on 2018-01-18
No, as Lubuntu uses neither of them. It still runs Xorg and I haven't heard of plans to change that. 

Did you try the fix in my link?

---

### Post by fred66 on 2018-02-11
Thanks. So, no installation of 17.10 worked. I had to stop working on this to attend more pressing business, and today I went back to this and followed the suggestion to try installing 16.04, and that is now working without any problem. I could say that the issue is resolved, but there is a nagging question: what changed in 17.10 to create this problem? It doesn't show up in 16.04, and it never happened before, including with 17.04.

---

### Post by fred66 on 2018-02-11
OH, NO! I spoke too soon. Things seemed to be fine, but then Lubuntu offered to download the updates available since it was launched, and asked for a reboot after downloading. As it came back, I got again the split screen with 1/4 desktop and the rest black with white "powder" at the top! What has happened lately that is throwing this old-timer off? I am afraid will have to try some other distribution, hoping that it is a (L)ubuntu newfangled feature that kills it. Anybody know of some "new and improved" feature that could be causing this mess?

---

### Post by wildmanne39 on 2018-02-11
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by sudodus on 2018-02-12
I suggest that you try the version **16.04.[COLOR="#CC0000"]1[/COLOR]** LTS, the first point release. It will stay with the xenial kernel (linux 4.4 series) and the corresponding hardware enablement stack with graphics drivers etc. I think it is more likely to continue to work with your computer than the later point releases.

This version of standard Ubuntu has long time support until April 2021 and Lubuntu 16.04.1 LTS is supported until April 2019. There is more information at this link,

[How to select the version and flavour of Ubuntu](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865)

You find the Lubuntu iso files via the following link (scroll down ...),

[cdimage.ubuntu.com/lubuntu/releases/16.04.1/release](http://cdimage.ubuntu.com/lubuntu/releases/16.04.1/release)

---

### Post by mörgæs on 2018-02-12
After reading your post I'm still not sure if you tried this or not:

[https://ubuntuforums.org/showthread.php?t=2376580&p=13709972&viewfull=1#post13709972](https://ubuntuforums.org/showthread.php?t=2376580&p=13709972&viewfull=1#post13709972)

---

### Post by fred66 on 2018-02-18
I am not sure why my replies do not post. I tried to say that after 17.10 did not work, no matter how I installed it, 16.04 had the same issue, as soon as I downloaded the upgrades. I even tried Peppermint (based on 16.04), and exactly the same happened. Maybe it's the latest kernel... A Debian based distro does not seem to have this, but I had  no opportunity to "download upgrades", so I can't be sure it will stay that way (it's also not very convenient, as the repos don't have many of the smaller programs I rely on, so I will have to work around that).

---

### Post by sudodus on 2018-02-19
If you start from a 16.04.1 iso file, the kernel will stay within the 4.4 series, 'xenial', and it may work better than if you try with the default 16.04.3 iso file, which brings the 4.10 kernel series, 'zesty'. See my previous post, Post #13.

If you have already tried starting from a 16.04.1 iso file, and it fails after upgrading too, please describe with as many details as possible, what is happening, when the system fails to work. Are there any differences (maybe small) between the versions of Lubuntu?

---

