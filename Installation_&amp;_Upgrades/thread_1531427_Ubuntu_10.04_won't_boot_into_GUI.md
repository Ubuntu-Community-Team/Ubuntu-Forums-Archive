---
title: "Ubuntu 10.04 won't boot into GUI"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by wcdsugpy on 2010-07-15
Ubuntu 10.04 was installed successfully on 8 PCs intended to introduce students to Linux.
However we found that the password box keeps prompting even after the correct password is typed in when we boot up. Thus we are unable to get into the GUI. This happens on 7 PCs.

With single PC where we are able to login in fully to the GUI, we find that the terminal stalls, freezing the mouse and the keyboard. The PC has to be reset to start again.

All the PCs have Windows XP on them previously and have been partitioned to make space for Ubuntu 10.04. We are thinking of downgrading to 9.10 or 8.04 as we suspect that the hardware might be old and not supported by 10.04. The issue of removing the Ubuntu partition also comes up and there are already a number of posts regarding this which we will try out.

Is there a way to solve the 10.04 problems encountered?

wcdsugpy

---

### Post by stlsaint on 2010-07-15
few questions:
1. How did you install these systems?
2. Are all these systems the exact same model/type etc. If so then you may want to consider either just getting one of the computers up and fully running and using something like clonezilla to copy the drive over to the other systems. Also you can look into [Disklessinstalls]("https://help.ubuntu.com/community/DisklessUbuntuHowto") or even a [LTSP]("https://help.ubuntu.com/community/UbuntuLTSP#General Information") setup.

---

