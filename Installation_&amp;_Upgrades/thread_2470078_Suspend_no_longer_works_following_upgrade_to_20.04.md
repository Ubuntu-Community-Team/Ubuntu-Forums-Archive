---
title: "Suspend no longer works following upgrade to 20.04"
date: 2021-12-19
forum: Installation &amp; Upgrades
---

### Post by michael351 on 2021-12-19
I just did a clean install of 20.04 replacing 18.04.

I notice that $sudo systemctl suspend - no longer works. the system will suspend for a second (all windows close, RDP closes, etc.) and then the system resumes operation a second or two later on its own.
Normally I would resume from suspend using a magic packet (i.e. 'wake-on-Lan') when I am ready.

help is appreciated - I haven't done anything except install 20.04 from the distribution - set up my accounts and then noticed I can't suspend operation like I used to.
Thanks

Update: I tried :
echo mem | sudo tee /sys/power/state

which sort of worked but now I can no longer open a remote desktop (RDP) or use PuTTY and open a SSH terminal.
I can't resume where I left off. The main screen (home theater) works fine, but shutting down, unplugging and re-starting does not restore my system (Ubuntu 20) as before.

I'm stuck on what to do to get this working.

---

### Post by michael351 on 2021-12-19
Strange issue, but it is solved.

When I put the system to sleep using the /sys/power/state method, upon awakening, my IP address was changed by the router. It has never done this before. Even though IP addr's are assigned by DHCP, the mac address on my Ubuntu desktop always was assigned the name IP address. But no this time. The only way I knew is that after years seeing the same number through many Ubuntu upgrades (from 12 through 20), it suddenly was different. I may just change the settings and make it static. I am so use to that number.

---

