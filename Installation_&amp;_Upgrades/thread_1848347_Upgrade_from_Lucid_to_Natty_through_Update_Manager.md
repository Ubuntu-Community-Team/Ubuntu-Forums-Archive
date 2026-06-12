---
title: "Upgrade from Lucid to Natty through Update Manager Failed"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by shuukazedojo on 2011-09-22
Hello all. I've been running Lucid successfully for a while now but felt the need to update. I went through the Update manager and installed Meerkat. This was fine. Following the same procedure I attempted an install of 11.04 but am getting an error.

When I boot, I get a purple Ubuntu screen followed by flashes of black. Eventually this loads into some kind of terminal-like screen where the last bit of dialogue is:

/dev/sda7: clean, 350190/9076736 files, 31186556/36276762 blocks
*Stopping Userspace bootsplash  [OK]
*Stopping Flush boot log to disk [OK]
*Enabling additional executable binary formats binfmt-support  [OK] 
No apache MPM package installed
*Checking battery state...   [OK]


How do I fix this??? I am unfamiliar with the commands from here. I would like to either restore the previous update or fix Natty. What are the solutions?

THANK YOU in advance!!!

---

### Post by zvacet on 2011-09-23
Boot in recovery mode and then run these commands

```
sudo dpkg --reconfigure -a
sudo apt-get -f install
```

and see if that help.

---

### Post by shuukazedojo on 2011-09-27
I decided to just format and reinstall Lucid. Everything is right with the world once again!

---

