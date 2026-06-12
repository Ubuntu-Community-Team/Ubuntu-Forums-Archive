---
title: "How to upgrade old 12.04 i686 router to 18.04 x64"
date: 2018-12-20
forum: Installation &amp; Upgrades
---

### Post by oldgraf on 2018-12-20
Hello,

My current home router is pc with 2 network interfaces. Ubuntu is 12.04 i386. My ISP uses PPP with user and pass to connect. On this PC i have several 32bit software. I want to install new SSD with Ubuntu 18.04 x64 on it and move(recompile) 32bit softs. 

I have concerns about network card names, this PPP protocol and packages and its settings at 18.04 without internet connection if there is a problem.
Is there a way to install 18.04 on SSD without putting a monitor, keyboard and USB flash drive.
Where to make GRUB, the old harddisk will not be removed for now. Will remain for data on the new server.

Thanks

---

### Post by Tadaen_Sylvermane on 2018-12-20
> [COLOR=#000000]Is there a way to install 18.04 on SSD without putting a monitor, keyboard and USB flash drive.[/COLOR][COLOR=#000000]

I don't see how that would work. Maybe with a preseed file and a pxe server. But still need a way to interact with it.

Do you plan on building or getting a new server to replace the above box? If so then the proper way of doing this would be to install and configure the new server, then switch over to it.[/COLOR]

---

### Post by oldgraf on 2018-12-20
Thanks for idea of pxe server.
I do not want to change my computer, just add new disk and install on it 18.04 x64. 
This machine is in an uncomfortable place and that's why I was asking for another way of installing.

---

### Post by Tadaen_Sylvermane on 2018-12-20
Another idea, if you are willing to forgo x64 is upgrade straight through. Might be troublesome with some things to fix as you go, but it would be all doable over ssh. 14.04 repos are still online so it should just be a matter of running ```
do-release-upgrade
``` right on through to 18.04.

Normally I would advise against this knowing how Ubuntu upgrades tend to go according to the forums. But the reality is that for every person that complains about a problematic upgrade there are probably a few thousand that go fine and you never hear about them. Why post about something doing what it is supposed to do.

*EDIT* If you do end up doing it with a monitor & keyboard I might suggest an LVM filesystem. That way in the future you can move the volumes to a different disk without a full fresh installation. Also allows snapshots to revert in case an upgrade goes south.

---

