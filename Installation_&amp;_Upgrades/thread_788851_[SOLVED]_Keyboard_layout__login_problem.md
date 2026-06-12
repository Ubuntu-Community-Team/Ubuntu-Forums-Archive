---
title: "[SOLVED] Keyboard layout / login problem"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by aethralis on 2008-05-10
I did an upgrade from 7.10 to 8.04 and had strangest of problems. I couldn't login via the normal login screen as the characters displayed there were not latin ones but reminded me of Thai language (can't tell for sure). I did (via Ctr+Alt+F1, where the keyboard worked just fine) dpkg-reconfigure xserver-xorg and there everything seemd ok. In xorg.conf I tried both "us" keyboard layout and my native "et" layout. Both were pc105 keyboards. Results were the same. Via the graphical login screen I couldn't access my computer! I did several reboots and then just in case I booted to 2.6.24-14 generic kernel - suprisingly there I could login. I disabled all keyboards in SCIM and now the login problem for both kernels has gone. Has anyone had similar experiences or could comment, what actally happened? Because it would seem stange as the kernel versions should have nothing to do with the keyboard layout (or SCIM) in my opinion...

---

### Post by mikulka on 2008-05-10
I just updated from 7.10 to 8.04 and have exactly the same problem and I'm also using "et" (estonian) keyboard layout.

If I change in /etc/X11/xorg.conf "XkbLayout" to "us" and reboot then I can input latin characters at login screen (but still not some estonian specific characters like "õäöü").

If I change in xorg.conf "XkbLayout" to "et" and reboot then I get this weird characters problem again at login screen.

Then I remembered that in some programs "et" is used for ethiopian/ethiopic language and "ee" is used for estonian language.

I googled for ethiopian keyboard and found this picture:
[http://wiki.laptop.org/images/thumb/8/8f/Ethiopic-B3.png/800px-Ethiopic-B3.png](http://wiki.laptop.org/images/thumb/8/8f/Ethiopic-B3.png/800px-Ethiopic-B3.png)
(and these are exactly the characters that I was getting)

So I **changed xorg.conf "XkbLayout" to "ee" and rebooted** and got estonian keyboard layout.


Looks like other people using estonian keyboard layout are experiencing the same problem:
[http://ubuntuforums.org/showthread.php?t=636612](http://ubuntuforums.org/showthread.php?t=636612)
[http://ubuntuforums.org/showthread.php?t=779749](http://ubuntuforums.org/showthread.php?t=779749)

So starting from ubuntu 8.04 "et" is ethiopian and not estonian anymore??? :confused:

---

### Post by aethralis on 2008-05-11
Filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/kbd-chooser/+bug/229305](https://bugs.launchpad.net/ubuntu/+source/kbd-chooser/+bug/229305)

Though I'm not quite sure whether it is the right package.

---

### Post by dilidon on 2008-10-03
> **aethralis said:**
> Filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/kbd-chooser/+bug/229305](https://bugs.launchpad.net/ubuntu/+source/kbd-chooser/+bug/229305)


Thanks for filing this bug. It is still an issue. The issue is NOT "solved". Manually editing xorg.conf and setting the keyboard to "ee" (thank you for mentioning this approach, I also found the same solution by trial-and-error) is a temporary fix, and is not always easily applicable for new users we want to recruit/attract. The underlying issue remains the suddent change from et to ee which leads autodetection to misidentify the keyboards of people.

I have a fresh install of Hardy on my Acer Aspire One (I have used the "fix" on all other machines so far) and I confirm the problem. The gnome keyboard chooser settings dont really matter, they are ingored, and in my new install, I cant even "switch" other keyboards "on" in a satisfactory manner once xorg.conf has defined the Ethiopian  layout, and the automatic detection has detected the keyboard as Ethiopian, i.e. et, which usually has meant Estonian. If that has become Ethiopian now - fine. But that means the autodetection and everything else needs to be modified according to this. Even if we were to accept the point brought out by Colin at launchpad [https://bugs.launchpad.net/ubuntu/+source/kbd-chooser/+bug/229305/comments/1](https://bugs.launchpad.net/ubuntu/+source/kbd-chooser/+bug/229305/comments/1) that language codes in xorg do not always comply with ISO standards it is NOT ok to consider this issue solved. The solution is an ok temporary fix for those willing to go for editing the xorg.conf file, but it is NOT an option for people uncomfortable with this solution especially after they get locked out of their system because they become unable to enter latin symbols all of the sudden (happened to me a couple of times).

---

