---
title: "Upgrade failed, Muno updater just quits."
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by steve723 on 2013-04-28
Kubuntu forums are down error 503.

I tried to upgrade from Kubuntu 12.10 to 13.04 64bit. Muno update manager quit while downloading packages about 63% were downloaded before the program died. There was no error message.

I hope my system didn't get hosed! :-x

I updated Muno before the upgrade so I have the upgrade patch that is supposed to fix it. Yes I rebooted after upgrading the updates, before runing the distro update.

---

### Post by steve723 on 2013-04-28
I was looking at file:///var/log/dist-upgrade/20130428-1845/main.log, and noticed the last few lines:
2013-04-28 18:25:14,565 ERROR doUpdate() failed completely
2013-04-28 18:25:20,119 DEBUG abort called
2013-04-28 18:25:20,121 DEBUG openCache()
2013-04-28 18:25:20,121 DEBUG failed to SystemUnLock() (E:Not locked) 
2013-04-28 18:25:27,468 DEBUG /openCache(), new cache size 63041
2013-04-28 18:25:27,468 DEBUG enabling apt cron job

I am using a wireless connection to do the upgrade. I was using Firefox while I was upgrading so the connection seemed fine.  I just thought that since Kubuntu forums are down then maybe you might be updating the server?

---

### Post by steve723 on 2013-04-29
I see Kubuntu forums are still down! Same error message ***Error 503 : Service Temporarily Unavailabl******e.***

---

### Post by steve723 on 2013-04-29
I don't get it how is only the Kubutu forums down but the rest of the Kubuntu site is up?

---

### Post by howefield on 2013-04-29
> **steve723 said:**
> I don't get it how is only the Kubutu forums down but the rest of the Kubuntu site is up?

Hmm, seem ok from here, and presumably for the other few currently online.

---

