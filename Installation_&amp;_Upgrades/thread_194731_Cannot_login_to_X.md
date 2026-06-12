---
title: "Cannot login to X"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by dgermann on 2006-06-11
Hi--

Have just upgraded to 6.06 LTS from 5.10, using the Update Manager. (This is my second machine to upgrade--have two more to go after this is up and running. The first one went without any problems.)

All went smoothly. On reboot, there was one item failed, having to do with PCMCIA services (there are no such devices on this desktop machine).

The login screen came up. I logged in as the user. It went to a black command line screen giving the Ubuntu version and what looked like a login prompt. About 20 seconds later, it gave me another X login screen.

I did this about 3 times, but cannot login. However, I can ssh into the machine.

/var/log/messages reports that bios handoff failed and cdrom: open failed.

If I login at that command line that I get between X login screens, I can perform command line work--until the X login screen decides to pop back up! Then I login again and am taken back to the process that I was in the middle of, like less /var/log/messages. Strange.

Any ideas what a fix might be?

Thanks!

---

### Post by Alcibiades Mystery on 2006-06-11
[QUOTE=dgermann]Hi--

Have just upgraded to 6.06 LTS from 5.10, using the Update Manager. (This is my second machine to upgrade--have two more to go after this is up and running. The first one went without any problems.)

All went smoothly. On reboot, there was one item failed, having to do with PCMCIA services (there are no such devices on this desktop machine).

The login screen came up. I logged in as the user. It went to a black command line screen giving the Ubuntu version and what looked like a login prompt. About 20 seconds later, it gave me another X login screen.

I did this about 3 times, but cannot login. However, I can ssh into the machine.

/var/log/messages reports that bios handoff failed and cdrom: open failed.

If I login at that command line that I get between X login screens, I can perform command line work--until the X login screen decides to pop back up! Then I login again and am taken back to the process that I was in the middle of, like less /var/log/messages. Strange.

Any ideas what a fix might be?

Thanks![/QUOTE]

Read "Dealing with problems with the X Server, posted at the top of this forum. Cheers.

---

### Post by dgermann on 2006-06-12
Alcibiades Mystery--

Thanks!

Will check it out and report back!

---

