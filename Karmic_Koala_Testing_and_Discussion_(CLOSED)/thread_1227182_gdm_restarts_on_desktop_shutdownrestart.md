---
title: "gdm restarts on desktop shutdown/restart"
date: 2009-07-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinxter on 2009-07-30
anyone else have this bug or has reported it?
- boot to desktop with usplash enabled
- select shutdown or restart from desktop  menu
- gdm respawns before being killed by the shutdown process

gdm:
  Installed: 2.27.4-0ubuntu6
  Candidate: 2.27.4-0ubuntu6
  Version table:
 *** 2.27.4-0ubuntu6 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status

---

### Post by dinxter on 2009-07-30
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/406962](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/406962)

may be a duplicated but i couldnt find the same thing on a 2.27 gdm bug

---

### Post by wayne_cat on 2009-07-30
I don't see this problem on my system. Restart from the menu stops Gnome and switches
to the splash screen ... after a view seconds the system reboots.


- no GDM AutomaticLoginEnable
- usplash-theme-ubuntu

I'm still using the old grub version ...

```
/boot/vmlinuz-2.6.31-4-generic root=/dev/sda3 ro quiet splash security=apparmor
```/var/log/gdm attached ...

edit:

Hint: Try do disable AutomaticLoginEnable ... problem still there?

---

### Post by wayne_cat on 2009-07-30
even if I enable AutomaticLoginEnable:

```
root@macbook:~# cat /etc/gdm/custom.conf 
# GDM configuration storage
[daemon]

AutomaticLoginEnable=true

AutomaticLogin=rschmitt

[xdmcp]

[chooser]

[security]

[debug]

root@macbook:~#
```I don't see GDM after selecting "Restart" from the menu.

---

### Post by dinxter on 2009-07-30
i might give it a crack with the nouveau driver instead of nvidia later, see if thats an issue, just thinking how i dont get any usplash on shutdown with the nvidia one (fine on startup though)

---

### Post by wayne_cat on 2009-07-30
> **dinxter said:**
> i might give it a crack with the nouveau driver instead of nvidia later, see if thats an issue, just thinking how i dont get any usplash on shutdown with the nvidia one (fine on startup though)

My system has an ATI x1600 ... driven by the radeon module. Maybe another NVIDIA
user could test this behavior.

---

### Post by dinxter on 2009-07-30
no difference with either nvidia or nouveau, only disabling usplash seems to cure it (how many times have i said that :) ).

---

### Post by wayne_cat on 2009-07-30
> **dinxter said:**
> no difference with either nvidia or nouveau, only disabling usplash seems to cure it (how many times have i said that :) ).

You said:

"gdm respawns before being killed by the shutdown process"

Do you see a "respawn message" on the TTY while the system reboots?

(if you just see a gdm screen ... maybe it comes from the fame buffer?)

Should I add the information to your bug report, that I don't have this problem with my ATI adapter?

---

### Post by dinxter on 2009-07-30
to be more exact,
- on boot, system messages are on tty1, X on tty7 as normal
- on shutdown, system messages now appear on tty7 with gdm respawning on tty1

i'd say theres no need to add anything to the bug report unless you experience the problem

---

### Post by dinxter on 2009-07-30
sounds like some sort of competition between usplash and gdm with the main tty, there was a similar problem before with the "i type in X for minutes then when i press enter gdm respawns" bug that was dealt with a few weeks ago

---

### Post by wayne_cat on 2009-07-30
I remember this ... :

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396226](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396226)

They fixed the problem with gdm 2.26.1-0ubuntu5 ... but now we have
gdm 2.27.4-0ubuntu6 ... not sure if this version also has some of these
"ugly hacks"

Your problem started today? Or have you just changed something (re-enabled usplash)

---

### Post by dinxter on 2009-07-30
yep 05_initial_server_on_vt7.patch which was used to fix that bug is still in the package for the latest gdm. i normally dont have usplash enabled so its difficult to be sure exactly which set of updates might have caused this bug. its not #[396226]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396226") though, i had that one at the time :) might have a similar sort of cause though

---

### Post by amontiel69 on 2009-09-01
Hi, 

I have a similar problem with gdm restarting on my laptop. I installed Karmic Alpha 4 and it went just fine, but then the update manager popped up and prompted me to update, which I did. Upon rebooting the system, it got all the way to the login screen, so I chose my username and entered my password. The screen blinked three times and I was presented with the login screen again. Once again, I logged on and the same thing happened. I thought it could be related to a new kernel having been installed along with the updates, so I tried to boot with the previous one, but the same behavior occurred. I then decided to download the daily build for today and just finished installing it clean and the same behavior is still happenning.

It looks like xorg is crashing upon getting started or something. I have a Mobility Radeon HD2600 and this worked previously on 8.10 and 9.04. If anybody has a clue, I would be more than happy to provide any additional info necessary to try to solve this problem.

Thank you very much.

Alex

---

### Post by taavikko on 2009-09-02
> **amontiel69 said:**
> Hi, 

I have a similar problem with gdm restarting on my laptop. I installed Karmic Alpha 4 and it went just fine, but then the update manager popped up and prompted me to update, which I did. Upon rebooting the system, it got all the way to the login screen, so I chose my username and entered my password. The screen blinked three times and I was presented with the login screen again. Once again, I logged on and the same thing happened. I thought it could be related to a new kernel having been installed along with the updates, so I tried to boot with the previous one, but the same behavior occurred. I then decided to download the daily build for today and just finished installing it clean and the same behavior is still happenning.

It looks like xorg is crashing upon getting started or something. I have a Mobility Radeon HD2600 and this worked previously on 8.10 and 9.04. If anybody has a clue, I would be more than happy to provide any additional info necessary to try to solve this problem.

Thank you very much.

Alex

Your issue is a different one that this thread is all about
look: [https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126)

---

