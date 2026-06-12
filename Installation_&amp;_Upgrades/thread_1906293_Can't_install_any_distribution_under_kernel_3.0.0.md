---
title: "Can't install any distribution under kernel 3.0.0"
date: 2012-01-08
forum: Installation &amp; Upgrades
---

### Post by NiteiaTt on 2012-01-08
The first time I tried to move to Ubuntu, from Windows, I downloaded Ubuntu Oneiric. I created a bootable USB drive, and rebooted. When I booted into the USB, it started loading drives (I saw it in the screen) bun when it loaded the kernel, the screen shut down. I know the installation kept running, because later on, I ran ubuntu from the usb, and actually listened the login sound.
I got some suggestions, one of which was to go back to previous Ubuntu versions, which I did.
But now, I actually got bored of being behind the actual releases, and want to try Gnome 3.2 very bad!
I knew I couldn't install Oneiric, so I went and downloaded Fedora 16.
Same problem: screen shuts down.
Downloaded openSUSE 12.1: same problem
Downloaded Arch Linux: same problem
Kubuntu 11.10 (Which is silly, because it's the same as ubuntu): Same problem.

It'd be stupid to say it's a kernel issue, because it's obvious. (unless it's not and I'm  stupid)
But, my question is: 
Why does that happen?
Should I wait until Ubuntu PP (Precise Pangolin)?
Is there a way to fix my problem?
Would anything change if I connect another monitor through VGA connection?

I'm currently under Kubuntu 11.04 because I was trying to install GNOME 3 on Ubuntu 11.04 without having it to mess with Unity or GNOME 2 (I tried to update to G3, but something happened that G3 session was all messy) [Maybe I shouldn't have done that in the first place]

Anyone that can solve anyone of my doubts will have me as a slave for 1 week...
OK, I'm kidding.
But you can tell how appreciated would I be :P
___________________________________________
AMD A8-3510MX APU (Quad: 1.8GHz) with ATI Radeon 6620G
6GB RAM
750 HDD

---

### Post by jerrrys on 2012-01-10
"Kubuntu 11.10 (Which is silly, because it's the same as ubuntu)"
Nope, not the same, big difference.

"It'd be stupid to say it's a kernel issue"
Maybe, maybe not.  One thread I have read thinks the kernel is the problem.  Can you drop back to an older kernel?
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ATI+Radeon+6620&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ATI+Radeon+6620&sa=Search&cof=FORID:9)

---

### Post by NiteiaTt on 2012-01-10
@jerrrys I couldn't, it was a fresh installation, hence, only one kernel. Thanks for replying though! =D.
But I solved my problem with a page I'm having trouble to find...
I'm posting it in the moment I find it, for those who have the same problem as I did! :D

---

### Post by NiteiaTt on 2012-01-10
Well... Big troubles trying to find it. But... I know exactly what I did so:
1. Downloaded the alternate install Ubuntu 11.10 x64 ISO. (This installs ubuntu from a text-based installer that doesn't make use of the X server)
2. Used "Startup Disk Creator" inside Ubuntu 12.04 (an alpha Daily Release), but I worked
3. Booted and installed
4. Finished Installing and rebooted
5. In the GRUB menu, I edited the entry for ubuntu 11.10 and added the famous "nomodeset" parameter between "quiet splash" and the thing next to it.
6.This would unsuccessfully boot, but this unsuccessful boot was intended
7. Fell into consle by pressing Ctrl+Alt+F1 (My splash screen stopped loading at some point)
8. Did the login from the console
9. Wrote into console: sudo apt-get update && sudo apt-get install fglrx (this is the Catalyst driver for ATI graphics cards)
10. Finished installing the driver and reboot

This solved my problem, and didn't have to edit the grub configuration file

---

### Post by jerrrys on 2012-01-10
Good going

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by NiteiaTt on 2012-01-11
@jerrrys Thanks for the interest, btw.
I forgot to mark it, when I recalled I just wanted to sleep :P
And... I got curious... what's the difference between Kubuntu and Ubuntu, other than the KDE and it's respective apps?

---

### Post by jerrrys on 2012-01-11
the never ending story

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=kde+kubuntu+vs+gnome+ubuntu&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=kde+kubuntu+vs+gnome+ubuntu&sa=Search&cof=FORID:9)

---

