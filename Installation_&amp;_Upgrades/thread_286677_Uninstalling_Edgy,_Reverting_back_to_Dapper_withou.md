---
title: "Uninstalling Edgy, Reverting back to Dapper without reformating?"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by roguenoir on 2006-10-28
Is it possible to uninstall Edgy and restore Dapper to roughly what it was before you installed Edgy without reformating?  Everywhere I look, there are instructions to overcome hurdles in upgrading to Edgy but nowhere can I find how to go back to Dapper again (OK, I'll admit I may be a bit idealistic in my expectations here.)

---

### Post by Johnsie on 2006-10-28
If you dont mind me asking, why do you need to go back?

---

### Post by roguenoir on 2006-10-28
- World of Warcraft was working fine from Cedega for many months and with different patches while I was on Dapper.  Once I upgraded to Edgy, it crashes after 5 minutes on average.  I've tried reinstalling my video drivers, using the minimum settings, using different versions of Cedega, etc. to no avail.

- Various applications that use Python also started behaving funny and perform slowly and/or crash.

---

### Post by Johnsie on 2006-10-28
Hmmm... I'm sorry I was hoping it would be something I could help you with rather than you having do to back. I hope someone else with more knowledge can help you out. I asked in #ubuntu in xchat and someone said you have to back up your files and then just re-install from scratch but I'm sure that's not very helpful.

Maybe you could try uninstalling and then re-installing cedega and the python files.

---

### Post by nimrod_abing on 2006-10-28
> **roguenoir said:**
> - World of Warcraft was working fine from Cedega for many months and with different patches while I was on Dapper.  Once I upgraded to Edgy, it crashes after 5 minutes on average.  I've tried reinstalling my video drivers, using the minimum settings, using different versions of Cedega, etc. to no avail.


Is your video card an ATI Radeon? Upgrade to Edgy from Dapper broke hardware accelerated 3D on my setup. I'm stuck with a Radeon 9250 (RV280) and I can't recall the exact version where it started but it seems driver support for these cards are broken up until the latest driver releases. On Dapper I managed to fix my gfx card issues by using an old libGL.so.1.2 file from an older driver package.

The issue on Edgy right now is that the kernel DRM module fails to load if you have fglrx already loaded. This results in an unusable DRI setup leading to hardware accelerated 3D being disabled by the driver.

With the Open Source ATI drivers, the kernel DRM module loads fine but X locks up with even the simplest OpenGL program (like glxgears).

---

### Post by roguenoir on 2006-10-28
> **nimrod_abing said:**
> Is your video card an ATI Radeon? Upgrade to Edgy from Dapper broke hardware accelerated 3D on my setup. I'm stuck with a Radeon 9250 (RV280) and I can't recall the exact version where it started but it seems driver support for these cards are broken up until the latest driver releases. On Dapper I managed to fix my gfx card issues by using an old libGL.so.1.2 file from an older driver package.

The issue on Edgy right now is that the kernel DRM module fails to load if you have fglrx already loaded. This results in an unusable DRI setup leading to hardware accelerated 3D being disabled by the driver.

With the Open Source ATI drivers, the kernel DRM module loads fine but X locks up with even the simplest OpenGL program (like glxgears).

No, I'm using Nvidia.  Geforce 4 440 MX to be exact.

Edit: WoW works fine using Wine now though my framerates are considerably slower but liveable.  I guess I'll stick around with Edgy for now..  Is there any way I can revert back to the versions of Python used by Dapper while still keeping Edgy?

---

### Post by shelterpaw on 2006-12-07
I'd also like to revert back to Dapper on a couple machines. I don't mind the occasional crash, but I find several applications crashing under edgy. I think for my girlfriend, who's not savvy at all, Dapper would be better. My mistake ](*,)  for putting on Edgy, but I'd really like to find a simpler way then a reinstall to put her back on Dapper.

---

