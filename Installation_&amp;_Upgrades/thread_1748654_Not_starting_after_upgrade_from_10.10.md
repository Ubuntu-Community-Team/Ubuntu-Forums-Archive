---
title: "Not starting after upgrade from 10.10"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by loopingz on 2011-05-03
Hi there,
I launched 11.04 upgrade from a 10.10 ubuntu.
Now default linux does not boot it blocks on the ubuntu screen with dot not moving. Dot come back alive when I shut down system. Commands does not work. I can launch an older kernel but it is a pain, and I cant change boot order too, which is a big WAF issue.
What can I check or do?
Thanks for your support.

---

### Post by resutnubu on 2011-05-03
I have a similar issue, after updating to 11.04 from 10.10. Just see a blank screen, no cursor, no boot menu

I think the machine got corrupted after going to sleep, not sure if the system finished updating completely

Tried to boot from CD and USB, no such luck

10.10 worked fine after I installed over Win 7 maybe a month ago (contracted a trojan/virus that made it get the deadly blue screen [kernal dump] every half hour or so, just said the hell with it)

---

### Post by loopingz on 2011-05-04
I tried that: [http://zeeis.me/ubuntu-error-gave-up-waiting-for-root-device/](http://zeeis.me/ubuntu-error-gave-up-waiting-for-root-device/) passed all step and i am still suck at the same frozen ubuntu screen.

---

### Post by loopingz on 2011-05-04
I fixed it.
Not sure exactly what was the blocking point but here is what I did:
Recovery mode, look at the log: should be a graphic driver issue.
Start in recovery mode. Activate graphic driver (nvidia recommended one). I also installed available updates.
As for boot order, startup-manager is not up to date with the new grub listing. But you can fix default system easily. On startup check the position line of your default os (starting at 1, every line count), I will call it "n". On startup manager active the "n"th line even if it does not look at what you want. If you choose a line that is superior to the number of line shown at startup then first line will be default.
I hope that helps

---

