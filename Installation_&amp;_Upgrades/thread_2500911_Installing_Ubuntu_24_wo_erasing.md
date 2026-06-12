---
title: "Installing Ubuntu 24 w/o erasing???"
date: 2024-09-15
forum: Installation &amp; Upgrades
---

### Post by spencer2 on 2024-09-15
So; long time Ubuntu user who has installed multiple Ubuntus over nearly 20ish years.

I did the dist-upgrade from U22, got a message that there was an error on the install & I've been stuck since.

 I've tried multiple recovery modes & multiple old option in the boot menu & every time I just get the loading screen -- even when booting old versions that should be U22 & not U24.  I do have other Ubuntu OS'es on other partitions; so I went to other partitions to try & find a few key files to save -- and while gpartd does see the primary partition; it does not have an icon in my system menu.

So, I've made a Ubuntu 24 boot USB & am trying to install it on my primary partition & for some reason I don't feel like I see the option to install the OS on top of the current partition w/o erasing the disk. I feel like in the past, there has been an option to install on top of what is already present: essentially like a dist upgrade.

If I had to choose between a fresh OS that doesn't erase the files or fixing whatever went wrong w/ my distribution upgrade; I'd rather just use the USB for the fresh install -- but either is fine. My keepas database is on the gunked up partition that failed to upgrade correctly (as well as a handful of other files that I'd really rather not lose).

Pretty please; what am I missing in either my installation that wants to erase data instead of upgrading distribution OR how can I fix whatever went wrong w/ my upgrade.

*** Edit: when going through the install process, I'm only getting 2 options (erase & manual); I don't have the "install ubuntu alongside" option in the set up. I'm pretty sure that option is the one that I'm used to seeing in most USB install. ***

---

### Post by spencer2 on 2024-09-15
Long story short: my laptop's primary partition won't load ever since I upgraded to U24 from U22.

I've created an install USB to try & fix the issue; but its not working. On all the videos of U24 USB installs, 1 of the 3 options is 'install along side': which I really feel like I've used in past ubuntu usb versions to install new versions w/o erasing my current data.

This 'install alongside' option is not showing up for me currently. All I have is erase & manual.

Why doesn't my install usb have an "install alongside" option??

I really don't want to delete my whole primary partition because of a failed upgrade.


** I do have a slightly more thorough post about trying to fix the problem; but now I don't know why the 'install along side' option isn't present.

---

### Post by QIII on 2024-09-16
Threads merged.  Near duplicates, but slightly different information given.

---

### Post by tea for one on 2024-09-16
> **spencer2 said:**
> I've created an install USB to try & fix the issue; but its not working. 
There have been some recent posts where the install session did not behave as expected.
Possibly linked to the software used to create the USB.

If the installer fails/stops/crashes/misbehaves, create the USB with one of the following:-
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://www.ventoy.net/en/doc_start.html](https://www.ventoy.net/en/doc_start.html)
[https://rufus.ie/en/](https://rufus.ie/en/)
Startup Disk Creator (included in Ubuntu iso)

---

### Post by guiverc on 2024-09-16
It's helpful if you're specific with details.

I see mention of Ubuntu 24; so this is a Ubuntu Core 24 install??  Sorry I'm not familiar with the 24 or *year* product, as I use the *year.month* system such as 24.04.

There isn't mention of Desktop or Server either, as they use different installers; but given reference to 24 it's likely a server install...  though unclear.

The `ubuntu-desktop-installer` of 24.04 can have a forced format issue; which can prevent a *non-destructive* re-install, so I'll provide a link to a *askubu* answer where I mention it.

[https://askubuntu.com/questions/1515275/cant-uncheck-format-checkbox-on-manual-partitioning-screen-when-trying-to-r/1515281#1515281](https://askubuntu.com/questions/1515275/cant-uncheck-format-checkbox-on-manual-partitioning-screen-when-trying-to-r/1515281#1515281)

This only impacts the `/` partition, so if you have data in a separate `/home` directory; you won't be forced to re-format the data directory.

To my knowledge though, this ONLY impacts ISOs using the `ubuntu-desktop-installer`, which is not used by Ubuntu Core 24.

---

### Post by spencer2 on 2024-09-16
I am trying to install normal desktop Ubuntu 24.04 LTS. I upgraded from Ubuntu Studio 22 using terminal 'sudo apt dist-upgrade'; at the end of the upgrade, laptop said something didn't complete correctly & from then on, whenever I try to boot U24.04, the loading circle just spins & never boots up.

I did go in to multiple recovery modes; used various permutations of '--fix-broken install' on multiple recovery mode options & none of that has fixed the issue by either fixing the U24 issue or reverting back to the Ubuntu Studio 22 that should be in past recovery modes.

I then made a Ubuntu Desktop 24.04 USB to do the install; I just dl'ed from the normal Ubuntu website to download the installer:

([https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#2-requirements](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#2-requirements)
&
[https://ubuntu.com/download?_ga=2.4971315.187729850.1726484066-1506851759.1725819494](https://ubuntu.com/download?_ga=2.4971315.187729850.1726484066-1506851759.1725819494)).

I know that in the past, I tend to upgrade along side my current distros & am not usually stuck either upgrading or losing all my data. Also, I know that most installers have the 'alongside' option, because I've seen that choice in many of the YouTube videos discussing installing Ubuntu desktop 24.04 & that option is not in my install. Its also not a lack of space on the partition as there is 60 gigs of space on my primary partition (several posts have suggested needing at least 30-ish gigs of extra space).

Do I just need to use this Ubuntu Studio 24.04 installer?

[https://ubuntustudio.org/2024/04/ubuntu-studio-24-04-lts-released/](https://ubuntustudio.org/2024/04/ubuntu-studio-24-04-lts-released/)

---

### Post by spencer2 on 2024-09-16
mkusb's website says it erases the data: that's what I'm trying to avoid.
I did use rufus at first & for some reason, either the boot .iso wasn't saving as an .iso or rufus wasn't able to see the ISO w/o the .iso suffix.
Ventoy doesn't really sound like it'd do anything & I have been using start up disk creator to make my last several usbs.

---

### Post by spencer2 on 2024-09-16
Update:

I did make an Ubuntu Studio 24 USB & got the .iso file from UStudio's official website. When I did the install process; I got the same 2 'erase or manual' options. I know the 3rd 'install alongside' option is part of UStudio 24's install as the YouTube tutorials do have the 3rd option in their videos.

So again: for some reason, my installs are not providing the 3 options (along side, erase & manual): I am only getting the same 2 -- erase & manual.

I appreciate the help: sorry about being grouchy. Its just that I have work files on my partition that I really need to get to & its very frustrating that there still seem to be so many problems w/ the installers -- combined w/, for some reason, not being able to access the partition from other partitions or just do a recovery mode return to a previous version: because the upgrade messed up.

Thank you again

---

### Post by guiverc on 2024-09-16
> **spencer2 said:**
> I am trying to install normal desktop Ubuntu 24.04 LTS. I upgraded from Ubuntu Studio 22 using terminal 'sudo apt dist-upgrade'; at the end of the upgrade, laptop said something didn't complete correctly & from then on, whenever I try to boot U24.04, the loading circle just spins & never boots up.

Do I just need to use this Ubuntu Studio 24.04 installer?

[https://ubuntustudio.org/2024/04/ubuntu-studio-24-04-lts-released/](https://ubuntustudio.org/2024/04/ubuntu-studio-24-04-lts-released/)

Ubuntu 24.04 LTS Desktop uses *ubuntu-desktop-installer*, which has been the *primary* installed used by desktop since Ubuntu 23.04 Desktop. No installer is perfect, and it can potentially have issues with some hardware setups; it can't do everything the prior *ubiquity* installer did (*some because its been intentionally prevented*) but has many benefits too.

Ubuntu Studio 22.04 LTS used the *calamares *installer, so it used a different installer; at 24.04 the *calamares *installer is used by Lubuntu, Kubuntu and Ubuntu Unity.  At 24.04 the Ubuntu Studio 24.04 LTS ISO uses the *ubuntu-desktop-installer* which is the same installer used by Ubuntu Desktop 24.04 LTS.

You ended your question mentioning the *Ubuntu Studio Installer* which is a rather different thing, it'll add the Ubuntu Studio system to an existing Ubuntu installation, ie. you need to have Ubuntu installed before you use it.  For details of that you can visit 

[https://ubuntustudio.org/ubuntu-studio-installer/](https://ubuntustudio.org/ubuntu-studio-installer/)

The Ubuntu Studio Installer isn't found on Ubuntu Studio ISOs, as there is no need; it cannot install a system, just adds/converts an existing installation to a Ubuntu Studio system; the Ubuntu Studio DVD (ISO) already contains Ubuntu Studio.

Ubuntu 24.04 LTS is using the 6.8 kernel, where the kernel and specifically kernel modules (aka *drivers*) can have issues with certain hardware, meaning if your box (GPU or graphics usually) has issues with the 6.8 kernel, you'll find all Ubuntu systems (or any GNU/Linux using the 6.8 kernel) will have the same issue...  Ubuntu 22.04.5 LTS Desktop ISOs are now available using that 6.8 kernel (*Ubuntu 22.04 Server & older media used older kernels*), so you could try seeing if that helps, but issues with kernel modules usually appear when you boot, and not as install issues. The Ubuntu 22.04.5 LTS ISO will use the *ubiquity* installer so its a different installer.


You also mention (*I've quoted it*) using `apt dist-upgrade` to upgrade a system; that will upgrade packages as doesn't have the restrictions that exist on the `apt upgrade`, but it will NOT change your release; the `do-release-upgrade` command does that. The instruction page/doc for *22.04 to 24.04 *upgrades is [https://help.ubuntu.com/community/NobleUpgrades](https://help.ubuntu.com/community/NobleUpgrades) where you'll find no reference to `apt dist-upgrade` so I could be missing something; or your details are incorrect.  FYI:  I use the command `apt full-upgrade` on this box three+ times per day as I rarely use `apt upgrade`, but I do read the packages to be upgraded/removed (*which is where apt upgrade is safer for those less careful*).

---

### Post by spencer2 on 2024-09-21
I don't remember the exact order of the terminal commands that I entered when I did the original upgrade: hence some of the 'dist-upgrade vs. do-release-uprgade': I think i did the 'dist-upgrade' & then 'do-release'. That sounds familiar.

I did just try running through recovery mode again (Sat, 9/21) & while I'll have to add a couple images in a second post, I did take pictures of the responses that I got from going through recovery mode & using the commands from this page:

[https://www.tutorialspoint.com/how-to-fix-broken-ubuntu-os-without-reinstalling-it](https://www.tutorialspoint.com/how-to-fix-broken-ubuntu-os-without-reinstalling-it)


I apologize that I lack the knowledge of others; but I have had Ubuntu for a long time & have upgraded many a distribution. I've also been using Ubuntu Studio since like at least Ubuntu Studio 14 or so. I did not upgrade to Ubuntu Studio 23 as I tend to only upgrade the LTSes, so I don't know if the issue/change that is described about Ubuntu 23 would apply to my laptop.

After going through the recovery mode today & following the directions that terminal kicked out; upon reboot, my laptop is just loading still -- so I'm curious if I'm having the 6.8 kernel issue that is described. If it is the kernel issue; does that just mean that I can't upgrade to U24? What is being done for kernel issues?

If a lot of others are having issues with the U24 installer; is there a plan to fix that & how long would I need to wait to get a fixed installer?





[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294274&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294275&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294276&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294277&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294278&stc=1[/IMG]

---

### Post by spencer2 on 2024-09-21
In terms of the recovery process: I have done the same 

apt-get:

update
upgrade

--fix-broken install

The 2 things that concern me most is that going through recovery mode even in the two kernel-5 modes that are on my recovery option list, I'm still getting the same constant loading screen (ubuntu studio design at the bottom of the screen & the little spinning loading circle keeps spinning coninuously) when I reboot & I try to load which ever kernel-5 version that I'd just 'recovery moded': -- so that makes me think its not the kernel-6 booting issue.

So, I have a 1TB hard drive; with the original Windows in 1 partition; my main Ubuntu Studio partition, then there are 2 smaller old Ubuntu partitions (both are U18; that's why I roughly know when I originally set everything up). Even when I go into the back up Ubuntu partitions: I can't access my main partition. If there is a way to access that so that I can transfer over a handful of work files; I'd be fine with just doing a complete reinstall of the primary partition.

I have added add more pics of the responses I'm getting from recovery mode.

Hopefully, where some of my competence fails me in describing this, the pictures will help fill in some blanks.

thank you, again: I do appreciate the assistance

---

### Post by spencer2 on 2024-09-21
Interesting update:

I did a distribution upgrade on one of my Ubuntu 18 partitions & I followed these instructions, because they specify having to upgrade multiple times to get through multiple distros (such as myself going from 18 > 20 > 22):

[https://ubuntu.com/server/docs/how-to-upgrade-your-release](https://ubuntu.com/server/docs/how-to-upgrade-your-release)

However, it seems as though these directions did a direct upgrade to U24 & now another partition is just loading (spinning circle on Ubuntu Studio) boot up screen. At the end of the upgrade process, when asked to reboot to finalize install; chose "Y" & upon reboot, I'm in the same spot & I'm pretty sure the directions just did a direct U24 upgrade.

I did upload a few pics from the upgrade process & it can be seen the 2 other Ubuntu partitions (U24 is primary & U18 is, what seems to be my last standing & functioning Ubuntu partition).

I didn't do anything not on the directions from that website or that I the terminal process didn't ask me to do. I am beyond frustrated that U24 seems to be breaking my laptop.

I'm not a computer genius, but I have used Ubuntu for recording music, editing videos, running websites, making & publishing podcasts -- And over that more than a decade of working with & fixing various Ubuntu issues, I am extremely frustrated that U24 seems to have now nuked 2 of my partitions.

what is going on, Ubuntu?

---

### Post by guiverc on 2024-09-21
Your messages show (*many times*) temporary internet problems; which can be as the error message implies a *temporary* condition, and just waiting a bit and trying again is usually the fix.

The cause maybe many things, for me at home, power-brownouts are somewhat common and some cheap router/switches I have just die on brownout & need to be power-cycled.. It can also be my ISP is *dropping* my connection & I have to wait until I get a new connection using DHCP, but I don't have great internet, but very rarely there can be other network issues that aren't local too...

If I see *temporary internet issues or temporary failure resolving* I'll go back to basics.. Ensure my internet is up (`ip link`) that I have an ip address (`ip addr`) then I usually try and ping a few locations in the house (*underhouse comms cupboard, **garage where my servers are, external router*) where I'm checking my internal house network (*if I can't get to my comms cupboard; I'll likely get nowhere else as that's central; then I ping the 'arms' such as garage in this example AND a different 'arm' which is the router connected to my ISP* *or internet provider*).

`ping black` is how I'd confirm my router can be reached; but that's because I have local names defined; if they weren't I'd `ping 192.168.15.4`.   Assuming I had no issues to this point, I've confirmed my local networking (*my home*) is functional, so I test outside of the home. Note: I'm using my local network as example only; I don't know how yours is setup & hope you know. In my case almost all IP addresses are *static* and I know them; and not using DHCP or *dynamic *addresses.

On pinging external, I firstly ping my ISP using simple addresses (`ping 203.0.178.191` which I happen to know), then I ping google (`ping 8.8.8.8`).  You may note I'm not using *human.addresses*, as I'm keeping it simple firstly & using addresses that don't require translation, sort of testing only the cable connections.   If both those responded, I usually then try and ping them again using DNS or *domain name service* to ensure that is working, eg. `ping iinet.net.au` and `ping google.com` (not identical but close enough).   If you get this far, I'd expect most internet to be working, and return & try again.

In my case, in your position, I'd firstly run `sudo apt update` and ensure all lines look correct,  no warnings or missing lines etc.   I may also scan my sources (ie. `/etc/apt/sources.list` and `/etc/apt/sources.list.d/ubuntu-sources` and other files in `/etc/apt/sources.list.d/`) then if all looked good, try a `sudo apt -f install` and/or `sudo apt full-upgrade`.

Your messages showed a check for a file that I see available for *noble* or 24.04

```

 libglib2.0-0t64 | 2.80.0-6ubuntu1   | noble          | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
 libglib2.0-0t64 | 2.80.0-6ubuntu3.1 | noble-security | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
 libglib2.0-0t64 | 2.80.0-6ubuntu3.1 | noble-updates  | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x

```

thus if your sources are correct; I'd expect that package to be found; and you'll note it meets the requirement I noted in your screenshot message.

As for kernels, if you get 5.15 working (*you didn't specify what you've got, details can be useful*) as you'd expect when selected at GRUB; you have useful knowledge.

Can you use a text terminal; ie. let the system boot, and when it appears 'stuck', can you switch to a text terminal using Ctrl+Alt+F4 for example?

If booting an older 5.15 kernel however responds the same as your 6.8 kernel; I'd try and boot the system only to runlevel 1 (ie. I'll edit grub line and add a ' 1 ' to the linux kernel line) and manually boot system from there (I'd also likely remove 'quiet splash' too, so I'm seeing more messages that may provide clues). What I'm looking for here is that the system boots; I'd also try this on the newer 6.8 kernel... as if it looks good from here, especially if you're getting text terminal logins - your issue is GUI only related... and package commands from text terminal is likely how I'd fix that.

Sorry this won't be easy to follow I realize, hopefully you've gained something useful anyway.

---

### Post by oldfred on 2024-09-21
Ubuntu 18.04LTS (Bionic Beaver) became unsupported in April, 2023.
So unless you have extended support, your updates to 18.04 will not find repositories and never work.

For LTS to LTS versions, the current LTS has to be totally updated, all ppa's removed as they may not be available in newer version, and proprietary drivers removed. You can then reinstall ppas & drivers in new install once updated, if required.

Often then easier to just do a new install of 24.04.1 and restore from your normal backup of your data, /home & list of installed apps.

There is "dirty" install or install without formatting. Any of your data should be preserved, but if you changed any system settings, they all will get overwritten with then new installs defaults. You need good backups, first.

Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) & 
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)
[https://ubuntuforums.org/showthread.php?t=2496620](https://ubuntuforums.org/showthread.php?t=2496620)

---

