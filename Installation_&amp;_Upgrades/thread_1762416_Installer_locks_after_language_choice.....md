---
title: "Installer locks after language choice...."
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by piston9 on 2011-05-19
I have Ubuntu 11.04 live media on a USB stick. It can boot just fine, and I can use it. It detects my video, sound and wireless networks just fine.

If I run the installer though, I choose 'English', and no matter what I choose on the next screen (ie, mp3 yes no, updates yes, no, whether connected to internet or not), when I click next it just locks. I've tried choosing 'install' direct from boot and also from running in live mode, fails the same both ways. 

By 'locks' the system is still running - but the installer goes no futher, just twirls away. 

Dell d830 with Windows 7. 500G HDD. Rest is stock standard. I had 10.04 on this machine last year with no changes, so it's not a driver thing.

Checked MD5SUM - ok. rebuilt USB key three times. As I said, it boots and uses fine, just the installer no worky.

Any ideas?

---

### Post by Rubi1200 on 2011-05-20
Hi and welcome to the forums :-)

There could be a number of reasons why this is not "worky" for you.

Start with this guide and see if it helps at all:
[https://help.ubuntu.com/8.04/installation-guide/i386/boot-troubleshooting.html](https://help.ubuntu.com/8.04/installation-guide/i386/boot-troubleshooting.html)

---

### Post by atomicspin on 2011-05-20
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

There could be a number of reasons why this is not "worky" for you.

Start with this guide and see if it helps at all:
[https://help.ubuntu.com/8.04/installation-guide/i386/boot-troubleshooting.html](https://help.ubuntu.com/8.04/installation-guide/i386/boot-troubleshooting.html)

I'm having the same problem on a Gateway 500X with a new hard drive.  Went through the troubleshooting and none of it worked.  

I've tried using a LiveCD and a USB boot created on a working system.  It happens at that spot whether I do "Try Ubuntu" or "Install Ubuntu."

Thanks in advance for any help!

---

### Post by atomicspin on 2011-05-20
To add a bit more to it, I can click on the menu items up top (Power, etc) and they still work.  It's not frozen, the installer is just stopped.

---

### Post by Rubi1200 on 2011-05-20
If you are comfortable using a text-based installer, it might be worth trying the Alternate CD. 

You can find the download for the release you want a little further down the page than the regular desktop image:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

As it starts up press F6 and choose Expert mode to give you more fine-grained control and then Esc to get back to the menu and Enter to continue.

The instructions are pretty much self-explanatory. 

But, if you want to install 11.04, first read the release notes and hardware requirements for Unity:
[https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes](https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes)
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

---

### Post by atomicspin on 2011-05-20
> **Rubi1200 said:**
> If you are comfortable using a text-based installer, it might be worth trying the Alternate CD. 

You can find the download for the release you want a little further down the page than the regular desktop image:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

As it starts up press F6 and choose Expert mode to give you more fine-grained control and then Esc to get back to the menu and Enter to continue.

The instructions are pretty much self-explanatory. 

But, if you want to install 11.04, first read the release notes and hardware requirements for Unity:
[https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes](https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes)
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

aahhhh!  F6 was the key and I switched to NoModeSet, then things went just fine.

Thanks for the help!

---

### Post by Rubi1200 on 2011-05-20
> **atomicspin said:**
> aahhhh!  F6 was the key and I switched to NoModeSet, then things went just fine.

Thanks for the help!
No problem, you are more than welcome :-) 
Glad you got it sorted out.

---

### Post by piston9 on 2011-05-20
Problem solved - I burnt to CD, installed fine. Would boot and run liveCS from the key - just refused to install. Not sure if this is a bug in installer or just my brand of USB, as I tried the USB on three computers and failed the same way on each.

---

### Post by Rubi1200 on 2011-05-20
> **piston9 said:**
> Problem solved - I burnt to CD, installed fine. Would boot and run liveCS from the key - just refused to install. Not sure if this is a bug in installer or just my brand of USB, as I tried the USB on three computers and failed the same way on each.
Excellent, I am really glad you got it installed :-)

As the thread starter, please mark this Solved using the Thread Tools near the top of the page.

Enjoy!

---

