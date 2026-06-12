---
title: "Did system updates break my video/sound/wireless?"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by csum77 on 2008-05-10
Couple of quick disclaimers...I've used Ubuntu intermittenly for about two years now...only recently (about 5 months ago) did I fully switch over. I've gotten my hands dirty a bit getting it to work on different setups, but I'd still say I'm a amateur.

On to the problem. Dell Vostro 1400 w/NVidia graphics and the Intel a/b/g/n wireless. Installed Gutsy five or so months ago. All was great. Upgraded to Hardy via system update, all continued to be fine. Earlier this week I got a notice for system updates. I had been uninstalling VirtualBox (it hadn't worked since the Hardy update), and my system said it needed a reboot, so I thought I'd install the updates, then reboot. Not sure what the updates were (how can you see what was recently installed? Logs, I guess?), but they took a while to download & install. Anyway, when the updates finished I rebooted, and my video was all messed up (not using NVidia drivers, displaying 800x600 resolution, low color depth, etc), audio was gone, and wireless didn't work. Did some quick searching, rebooted to the recovery kernel(?), had it repair the X-Windows (I think...it was X something), then rebooted, and my display was at least back to 1440x900 resolution, but still no sound and no wifi. It looks as if the system doesn't even see the wireless card now. Additionally, I have an icon up by the "system tray" area that, when clicked on, says "SIOCGIFFLAGS error: No such device."

So, I don't know if the updates broke things, if uninstalling VirtualBox broke it (not sure how that would), or if not rebooting before performing the updates is what did it.

I've searched around a little bit trying to find some help, but the only thing I've found anything on is the SIOCGIFFLAGS error on older versions of Ubuntu.

Perhaps someone elsewhere has already run into this same problem and solved this...if so if you could point me to the solution that'd be great.

Due to my rookiness, I'm not exactly sure how to troubleshoot this. Should I try to uninstall the updates that were installed? If so I need to figure out what was installed...where would I find that?

Anyway, before I mess stuff up I wanted to consult with the community so I could learn proper troubleshooting techniques in Linux/Ubuntu, and so I can get this back up and working ASAP.

Thanks in advance for any help you can offer...I really appreciate it.

-Charlie

---

### Post by Pumalite on 2008-05-10
It's not clear if you upgraded to Hardy sometime in the past.

---

### Post by csum77 on 2008-05-10
I'm sorry...I thought I had included that. I did upgrade to Hardy via the system update alert received.

---

### Post by Pumalite on 2008-05-10
Post:
cat /etc/apt/sources.list

---

### Post by csum77 on 2008-05-10
Here's my sources.list...thanks again for your help!

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by Pumalite on 2008-05-10
Looks OK.

---

### Post by csum77 on 2008-05-12
After lots of messing/stumbling around I finally got things resolved. I was trying to manually install the wireless drivers for my Intel 4965 AGN wireless adapter, which required the build sources (?) to compile. So, in the process of trying to get the proper sources installed, I ended up installing these:

linux-386 (2.6.24.16.18)
linux-headers-386 (2.6.24.16.18)
linux-image-386 (2.6.24.16.18)
linux-restricted-modules-2.6.24-16-386 (2.6.24.12-16.34)
linux-restricted-modules-386 (2.6.24.16.18)

After installing those items I noticed I had the NVidia restricted drivers option back, so I enabled that, which required a reboot, and upon rebooting sound, graphics & wifi were all back to normal.

Like I'd said earlier, everything was working fine before the combination VirtualBox uninstall & system updates, so something got messed up through that process (and probably something I did wrong).

Anyway, thanks Pumalite for your posts and trying to help. Luckily I stumbled through this one and got things working.

Hopefully this will be helpful to someone in the future. Otherwise, it'll just cement my amateur status...

-Charlie

---

### Post by unipsycho on 2008-05-18
Just wanted to share my story. It looks like I've been having similar problems with Hardy Heron and broken wifi/audio after upgrades.

I originally installed 8.04 (kubuntu) shortly after it came out (and the traffic at the torrents died down) and got it up and running just fine. I tried to install the Microsoft TT Core Fonts. Dpkg complained but would not let me abort. After reboot, wifi was broken.

I reinstalled 8.04. This time, no core fonts. (I don't really need them)

Today, I jumped through some hoops to install VirtualBox (using Sun's installation package for 8.04). After rebooting, wifi (Atheros) as well as audio (emu10k) were broken.

lspci shows both devices attached to the system.
lsmod showed the emu10k module installed, but I couldn't recall what to look for with madwifi ('madwifi' did not list).

Going to the K Menu, System Settings showed no devices attached to the computer for wifi (didn't bother checking audio).

Ended up booting up the laptop (uses the same wifi card, so I know the card works!) and searching around. Looks like other folks have had similar problems. Although, I haven't found concrete solutions. I ended up booting into a previous kernel (a -generic instead of a -386 which installed for some reason with VBox) and things have been working fine.

Now, I'm suspicious that the first time I had this problem may have been caused by a kernel update. I can't be sure because I wasn't able or willing to research it much. What really concerns me, however, is when the next kernel comes out, will the wifi/audio break again? I know I'm using beta software, but this scared me a bit. I've only been using [k,x,u]buntu since 6.06 and I've been very pleased so far.

---

