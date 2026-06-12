---
title: "Ubuntu upgrade from 13.04 to 13.10 cant shutdown or suspend from top menu bar!"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by adec2 on 2013-10-17
Hi, AS the title says the upgrade went relatively smoothly except i cant shutdown or suspend the computer from the top menu bar. It just doesnt do anything when clicked. I can shutdown/restart from terminal but the menu bar just does a blank :/ All searches eem to point to people saying its either fixed in an update or its been like that for ages. I mean come on Carnonical! LOL Seriously they borked the shutdown button thats something Microsoft do not you!;)

Fully updated, BORKED :/ Has anyone got a solution please?

---

### Post by adec2 on 2013-10-18
Just an update, there must be a serious bug somewhere in 13.10 when doing an upgrade..

I have found that editing with dconf the location

/apps/indicator-session/suppress-logout-restart-shutdown

 and unticking this makes the restart option disappear even if the next option (suppress-restart-menuitem) is unchecked. Ticking it (suppress-logout-restart-shutdown) makes it reappear again and when clicking the restart makes it restart straight away without any options popping up (which presume is what it is supposed to do.
Anyway i got shutdown functionality working again albeit with what seems to me a silly way of doing it. Surely the suppress-logout-restart-shutdown option should just stop the pop up items from appearing on the desktop and not make the restart option in the menu disappear whilst the suppress-restart-menuitem is unchecked?

---

### Post by rawcoder on 2013-10-19
Hi, I am facing the same problem!
I have posted a question in launchpad regarding this [https://answers.launchpad.net/ubuntu/+question/237625](https://answers.launchpad.net/ubuntu/+question/237625)
If you are able to solve the problem please post the solution.

---

### Post by adec2 on 2013-10-19
i already have got a solution in my above post :) Even though it sounds like a bug too...

open dconf and tick this key /apps/indicator-session/suppress-logout-restart-shutdown

This seemed to re-enable the ability to shutdown or restart albeit without the confirmation pop up

worked for me although someone at carnonical has been tinkering in this area i think ;)

edit i have added a comment to the bug request you filed in your link so lets hope the ubuntu boffins sort this out. While i can shutdown/restart now from the top menu i too would like the confirmation dialogue back :)

---

### Post by adec2 on 2013-10-19
It appears the problem is associated with cairo dock when set to autostart. Added a bug on the cairo dock bugs page

[https://bugs.launchpad.net/cairo-dock-core/+bug/1242112](https://bugs.launchpad.net/cairo-dock-core/+bug/1242112)

---

### Post by adec2 on 2013-10-19
editing the command line in the startup applications for cairo dock to

 sh -c "sleep 5 && cairo-dock -o"

  seems to work well for me. If i put anything less than 5 it seems to go back to not being able to restart/shutdown again from the menu panel. 5 seems fine (for me)

---

### Post by rawcoder on 2013-10-22
BIG THANKS!!
Works perfect!!

BTW, 5 is fine!!

---

### Post by jan-catalin on 2013-11-03
Yes..it work's for me also...:) The idea is to delay the start of Cairo Dock, in order to "preserve" the settings of shut down /restart/ of buttons from the main panel.
Great idea...:)

---

### Post by halfbeing on 2013-11-08
Doesn't work for me. My problem is that I can do one suspend-resume cycle, but something goes wrong during that cycle that prevents me from suspending or shutting down again (except from the terminal without screen locking, which isn't much use). Whatever it is that causes this also causes networking support to break after resume (which can be temporarily fixed by doing "sudo restart network-manager" from the terminal).

I agree with those who think this is a major balls-up. This bug, combined with the one that means that several times a day I find my computer unusable for several minutes due to disk thrashing, make me really want to get a Mac.

---

### Post by adec2 on 2013-11-13
a blatant copy/past from the cairo dock bugs page but editing this file has worked for me and doesnt require the sleep 5 in autostart now

edit /usr/lib/x86_64-linux-gnu/cairo-dock/cairo-dock-launcher-API-daemon as root
 add the following line at line 33:
 from time import sleep
 and the following line at line 241 (just before ULWatcher()):
 sleep(5)

then restart the session

if you're using 32bit Ubuntu the file will probably be in
/usr/lib/cairo-dock/cairo-dock-launcher-API-daemon

[https://bugs.launchpad.net/cairo-dock-core/+bug/1242112](https://bugs.launchpad.net/cairo-dock-core/+bug/1242112)

---

### Post by stevenjrees on 2013-11-16
This worked for me on three separate machines...........
Only need to be able to get suspend working when the machine has not been logged in now.

---

### Post by ddraper2 on 2013-11-30
Modifying the cairo-dock-launcher-API_daemon as described above did not work for me however modifying the command line in the startup application did.

---

### Post by Rahabib on 2014-02-03
Sorry to necro but I felt I should post this.

This also fixes the issue for Plank, not just Cairo.

Thanks,

I assume this means that its more on Canonical's end to fix than any launcher's part.

---

### Post by md2406 on 2014-04-24
> **adec2 said:**
> a blatant copy/past from the cairo dock bugs page but editing this file has worked for me and doesnt require the sleep 5 in autostart now

edit /usr/lib/x86_64-linux-gnu/cairo-dock/cairo-dock-launcher-API-daemon as root
 add the following line at line 33:
 from time import sleep
 and the following line at line 241 (just before ULWatcher()):
 sleep(5)

then restart the session

if you're using 32bit Ubuntu the file will probably be in
/usr/lib/cairo-dock/cairo-dock-launcher-API-daemon

[https://bugs.launchpad.net/cairo-dock-core/+bug/1242112](https://bugs.launchpad.net/cairo-dock-core/+bug/1242112)


This worked like a charm for me, I am using Ubuntu 14.04 x64

---

