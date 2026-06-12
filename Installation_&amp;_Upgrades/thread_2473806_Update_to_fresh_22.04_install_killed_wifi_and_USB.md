---
title: "Update to fresh 22.04 install killed wifi and USB"
date: 2022-04-14
forum: Installation &amp; Upgrades
---

### Post by danieleaton on 2022-04-14
So I'm pretty new to Ubuntu.  Been years since I used it to see what it was like (2013). Last night I installed 20.04 (***NOT*** 22.04 as the subject line mistakenly says) on a 15" HP Envy laptop and things were working great. I connected to wifi and looked some things up on the web and downloaded some apps from the store.  But I had turned on the process where it would check for updates automatically during the install process and it later told me I needed to reboot to install some.  Being familiar with that process from Windows, I did as instructed.  But when the system came back, the function key to turn on the wifi no longer works and there is no wifi listed in the network connections.  Also, the whole purpose of this was to have a computer to control LaserGRBL for a small laser engraver for my 80 year old father-in-law.  I was going to install the app under Wine when I got that figured out.  But when I put in the thumb drive with the software and drivers, no external drives show up.



What can I do to fix this if I can't access the internet or external drives?  I'm at a loss and really need this to get up and running in the next couple of days.

---

### Post by TheFu on 2022-04-14
22.04 isn't released. It is still a beta and not suitable for normal use. **You, as a new Ubuntu user, shouldn't be touching it before it is released. **I've been running Linux over 25 yrs and prefer to wait a few months AFTER a release before I start looking at it.  I still haven't moved most of my servers to 20.04 ... that's 2 yrs old already and I'm not on it, yet.  I won't install 22.04 on a "production" system until August, at the earliest.  All releases have bugs that take a few months to be solved.
New is the enemy of stable.  Always remember that.

Sorry if that ruins you plans.

WINE isn't really a solution for 80% of Windows programs. Don't expect it to work. There are a few niche areas (gaming) where it can work, but only if there is an obsessed based of fans for that program AND for running it on Linux.  **Niche programs are extremely unlikely to work under WINE.**  Even when I was able to get a fairly popular program working under WINE, only about 90% of the program worked. Some seldom used parts never worked.  That was fine for a few years, then I got a new version of the Windows program and was never able to get it working in WINE.  Further, after an Ubuntu upgrade - which brought a newer version of WINE - the old version AND the new version of that Windows program stopped working completely.

If you need to run MS-Windows programs, expect to use MS-Windows.  Almost any computer made in the last 8 yrs can easily support Windows running inside a virtual machine.  That's how I run that last program I still need MS-Windows to run.

I wish it wasn't true, but that's the reality.

BTW, this thread really belongs in the Development Version sub-forum for a few more weeks until 22.04 is actually released.

---

### Post by danieleaton on 2022-04-14
Sorry.  My bad.  I saw the pre-release of something and didn't download that one.  I downloaded the "release" LTS below that.  It was ubuntu-20.04.4-desktop-amd64.iso.  So 2020, not 2022.  I'll see if I can edit my post and correct that.  The software that I want to run on it comes with linux drivers, according to a video I watched, so I want to see if that will work before going to the expense of trying to get a copy of Windows set up on it.

---

### Post by TheFu on 2022-04-14
Ok, that's good news.  Using the 20.04 LTS release **is** smart and what you want today.

Another suggestion to save you from issues - don't let it check for updates daily.  Only allow updates weekly.  Getting the first update can mean getting a broken update.  By delaying a few days to a week, any bonehead early package mistakes can be fixed before your system gets them and something bad happens.

Linux isn't Windows.  On the surface, things may appear similar, but they are not.  Always remember that.  Linux is much more like OSX than Windows. They have the same parentage.

Also, the GUI is just another program, not the OS.  The OS is something that GUI uses seldom actually interact with.  GUIs are at least 3 levels above the OS.

Get this script and run it: [https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info)
Post the results and either provide a link to those results back here or upload the file as an attachment.

Running this script isn't actually what I'd do, but it is the shortest way to post the info somewhere (I think).  If the location where it posts it requires a login, someone else will need to pick up this thread to help.  When it comes to wifi and Ubuntu, I'm not the best help.

I'd prefer that you had 2 commands that are not pre-installed and use those to provide the wifi chip and driver information. Those commands are:
```
inxi -Nxx
```
and
```
lshw -C network
```
But there's a chicken-egg issue right now.  I assume you've rebooted and that didn't fix the wifi issue?

BTW, installing updates needs rebooting only if the kernel or libc are updated.  On 20.04, that happens only 1-2 times a month.  On Unix systems, a reboot is seldom the fix for most issues, including some hardware issues. The idea that rebooting fixes all issues just doesn't apply. In some situations, rebooting is exactly what you do NOT want to do, if updates are in a bad state.  That seldom happens, perhaps once every 8 yrs.

---

### Post by grahammechanical on 2022-04-14
Is this a dual boot with Windows? It used to be the case and may be it still is the case, that if WiFi was turned off in Windows then WiFi would remain switched of in Ubuntu when it loaded. Have you entered system settings>WiFi and made sure that the WiFi slider is activated? There is also an airplane mode slider that will turn off WiFi, Bluetooth and mobile broadband. If the machine is a laptop then in system settings>power there is a slider to switch off WiFi if battery power is low. 

Regards

---

### Post by danieleaton on 2022-04-14
If I cannot get to the internet and cannot access the USB drives, how do I get and run that script?  I'm thinking I'm going to just have to do a re-install to get back to a working system.  Once that get up and running again, can you tell me how to get those two commands you are talking about so I can run them and how to save the output?  I'll also run the script as well at that point.  And then how do I keep it from installing whatever update causes this problem?  

Am I better off going with 21.10 instead of 20.04 LTS?

---

### Post by danieleaton on 2022-04-14
> **grahammechanical said:**
> Is this a dual boot with Windows? It used to be the case and may be it still is the case, that if WiFi was turned off in Windows then WiFi would remain switched of in Ubuntu when it loaded. Have you entered system settings>WiFi and made sure that the WiFi slider is activated? There is also an airplane mode slider that will turn off WiFi, Bluetooth and mobile broadband. If the machine is a laptop then in system settings>power there is a slider to switch off WiFi if battery power is low.
There are no wifi switches or settings anywhere in the settings tabs.  It's as if the laptop doesn't even have wifi.  And it's not dual-boot.  I erased the prior partition and did a clean, full install of Ubuntu.  I didn't notice  the airplane mode.  It was probably there, but I wasn't looking for it.  I'm about to install 21.10 instead of 20.04 and see if I have any better luck with that.  Once that comes up, I'll look for those options.

---

### Post by TheFu on 2022-04-14
21.10 isn't LTS. Beware.  There will be many more issues with it.

Also, drivers are back ported to the current LTS every 6 months with a new kernel.  20.03 is on 5.13.x kernel, so it is pretty new. If you install 20.04.4 from an ISO downloaded the last few weeks, you'll get that kernel and driver support is basically the same as for 21.10. Do what you feel is best, but don't expect it to actually be better.

Newer isn't always better.  New is the enemy of stable.

If you can't access the internet, you cannot install packages to access USB drives. Either they work or they don't.

BTW, Linux supports 30+ different file systems. As a Windows user, you are probably use to 3 - NTFS, FAT32 and perhaps exFAT.  If you use native Linux file systems, like ext4 on your USB storage, then mounting is easier.  Using foreign file systems means that Ubuntu has to insert a conversion layer for file systems that don't support standard Unix permissions.  It is sorta like how a Ferrari uses different tires than a Honda, except that your Ferrari (Linux) has a conversion tool that let's us use Honda-sized tires.

You can use the *Try Ubuntu* flash drive to get information and access the internal storage on the system.

---

