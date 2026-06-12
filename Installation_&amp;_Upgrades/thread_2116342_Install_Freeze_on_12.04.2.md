---
title: "Install Freeze on 12.04.2"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by WillliamShadowruby on 2013-02-15
When I select the region during install the system hangs and does not allow me to continue. My system specifications will be attached. I'm trying to get ubuntu 12.04.2 64x to dual boot along side windows 8 pro 64x. With windows partions being C: G: H: and D: having the ubuntu install.

---

### Post by grahammechanical on 2013-02-15
The first thing that you should understand is that we cannot install Ubuntu 12.04 on a machine with Windows 8 installed and secure boot Enabled. We need to use Ubuntu 12.10.

The second thing, is that even with 12.10 some people experience difficulties with these machines. Look though some of the recent threads on this subject. There is advice there.

Regards.

---

### Post by cjwatson on 2013-02-15
> **WillliamShadowruby said:**
> When I select the region during install the system hangs and does not allow me to continue. My system specifications will be attached. I'm trying to get ubuntu 12.04.2 64x to dual boot along side windows 8 pro 64x. With windows partions being C: G: H: and D: having the ubuntu install.

I'm not sure this is particularly related to Windows 8 or UEFI or Secure Boot or anything like that - it's an odd place for a hang related to any of those.  The installer logs (in /var/log/syslog and /var/log/partman after the hang - use ctrl-alt-f1 to get at them, or launch the installer from a "Try Ubuntu" session so that you can start other applications as well) might be helpful in spotting what's going on.

---

### Post by WillliamShadowruby on 2013-02-16
Thanks,

I'll try that and post back with results.

EDIT:

It's something to do with grub it throws errors about a potentially invalid drive map.

Kind of a noob here so i'm not sure.

EDIT:

I'm also going to try installing 12.10 and see how that goes I'll report back if there is any difference.

---

### Post by WillliamShadowruby on 2013-02-16
And... no change

---

