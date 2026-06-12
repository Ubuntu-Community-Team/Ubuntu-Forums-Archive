---
title: "System crash during update."
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by karczyk on 2011-09-25
Hey,
I'm new here. I'm having a hard time trying to fix my Ubuntu 11.04. Computer crashed while Update Manager was performing installations. Since then I can't update/install/uninstall anything because this error keeps coming up:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

After running 'sudo dpkg --configure -a' I get this:

> : error: error opening configuration directory '/etc/dpkg/e functions
 *
 * Copyright (C) 2009 ST Microelectronics
 * Rajeev Kumar<rajeev-dlh.kumar@st.com>
 *
 * This file is licensed under the terms of the GNU General Public
 * License version 2. This program is licensed "as is" without any
 * warranty of any kind, whether express or implied.
 */

#ifndef __MACH_SYSTEM_H
#define __MACH_SYSTEM_H

#include <plat/system.h>

#endif	/* __MACH_SYSTEM_H */
.cfg.d': Za d&#322;uga nazwa pliku


I've been looking for a solution all over the internet but nothing works. Hope you guys will be able to help me.

---

### Post by dino99 on 2011-09-25
from a terminal:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a

if that still fail:
reboot in recovery mode (hold "shift" key down at bios end process to get the grub menu, and select the 2d line: recovery mode)
then select "repair packages"

---

### Post by karczyk on 2011-09-25
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get install -f

Those 4 commands return:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

sudo apt-get update

Update is performed but at the end message "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem." shows up. (same thing happens with selecting "repair packages" in recovery mode.

sudo dpkg-reconfigure -phigh -a

Returns the same message as 'sudo dpkg --configure -a'.

---

### Post by karczyk on 2011-10-01
I'm still not able to fix this problem. Any other ideas how to solve this?

---

### Post by mörgæs on 2011-10-01
You have already received a good idea: Boot into recovery mode as Dino suggested.

---

### Post by karczyk on 2011-10-01
I got it fixed. Thanks for the help.

I followed the steps under "What to do if the dpkg command is broken" on this website: [http://www.debianhelp.co.uk/debianproblem.htm](http://www.debianhelp.co.uk/debianproblem.htm)
Worked like a charm.

---

