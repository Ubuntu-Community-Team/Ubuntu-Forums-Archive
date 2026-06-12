---
title: "Boot selection"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by FahadMKS on 2010-08-25
I need a help to boot the XP os that I have installed.

Right now, I have the issue of getting the Kubuntu getting booted first if I do not select manually in 7 sec.

Can anyone tell me how to make that auto selection to XP so that, I can leave the computer and let it select Windows.


All the helps will be appreciated.

---

### Post by oldfred on 2010-08-25
Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even in lucid.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

---

### Post by FahadMKS on 2010-09-01
Now I have removed the XP on from my computer and now I only have the Ubuntu OS with in my computer.

But the Boot selection windows is still arriving.

I do not want to have this and want to just have the Ubuntu boot up.

Can you guys help please.

---

### Post by oldfred on 2010-09-01
sudo update-grub

that rescans system and upates grub.cfg with all the new (or removes old) systems.

If it only sees one system you then may not get menu as it will directly boot that system.

With grub2 to get the menu, you have to hold down shift key from BIOS until menu appears. Really only required for recovery mode or memory test choices in menu. Or possibly manual editing to correct something.

---

### Post by FahadMKS on 2010-09-01
Thanks for the help man.

That worked.

---

