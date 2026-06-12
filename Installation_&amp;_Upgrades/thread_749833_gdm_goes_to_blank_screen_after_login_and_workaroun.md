---
title: "gdm goes to blank screen after login and workaround"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by Andrew Olney on 2008-04-08
It seems that after installing some cupsys updates:

cupsys (1.3.2-1ubuntu7.5) to 1.3.2-1ubuntu7.6
cupsys-bsd (1.3.2-1ubuntu7.5) to 1.3.2-1ubuntu7.6
cupsys-client (1.3.2-1ubuntu7.5) to 1.3.2-1ubuntu7.6
cupsys-common (1.3.2-1ubuntu7.5) to 1.3.2-1ubuntu7.6
libcupsimage2 (1.3.2-1ubuntu7.5) to 1.3.2-1ubuntu7.6
libcupsys2 (1.3.2-1ubuntu7.5) to 1.3.2-1ubuntu7.6

my gdm would let me log in but then send me to a blank screen.

Got some mileage with Alt-F2 and Alt-F4 and so could run programs and log out, but the lack of panel, menus, etc is annoying.

I decided to try upgrading to Hardy Heron b/c I thought (incorrectly) that it would be hard to back up these updates to the previous version. Anyways, after a Hardy install, I had the same problem. This made me think it was some weird config file problem (one that was migrated in the distribution upgrade) rather than something with cupsys.

I decided to create a new user and log in with that (after booting into the grub recovery mode). This worked fine, which again reinforced my suspicion that there is some config file difference between the two account profiles rather than a system wide issue (like video drivers).

At this point I stumbled into the workaround: logging into the new account worked. Once in that account, I could log into my original account using the "switch user" option on the shutdown dialogue. From there, I can access all of my applications with their correct settings (good job Hardy migration team).

So I can eventually get to my proper gdm desktop, going through a new fresh account.

Can anyone take these facts and come up with a diagnosis?

---

### Post by Andrew Olney on 2008-04-09
so the solution I came up with is this:

create a fresh new user with a home directory and log in as that user.

immediately log out to another user account with sudo privileges. use the sudo account to cp -r all the files in the new account to the old borked account.

this let me log in with the now unborked account and keep almost all of my settings, though there are still some to put back.

---

