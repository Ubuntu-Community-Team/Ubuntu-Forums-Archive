---
title: "Removing Wubi after deleting 'ubuntu' folder in C:\"
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by meijin3 on 2013-04-08
I moved to a true dual-boot with Windows 8 and Ubuntu after having used Wubi on my new laptop. Then from Ubuntu I deleted C:\ubuntu in the Windows partition. When I booted up into Windows, it still had the Wubi boot menu so I tried uninstalling Wubi, which I could not do because it was no longer there. I then tried re-installing and uninstalling it to no avail.

I looked around for a fix but Windows 8 does not have a boot.ini file that I can edit which is the only method I've seen that fixes this problem. Please help!

---

### Post by bcbc on 2013-04-08
You should have gone to the Control Panel, Add/remove programs... and double clicked on "Ubuntu". Or run C:\ubuntu\uninstall-wubi.exe

This is how you remove the boot entry: [http://askubuntu.com/a/145605/14916](http://askubuntu.com/a/145605/14916)

To remove the registry entries if you care: [https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

---

### Post by meijin3 on 2013-04-08
You, sir, rock. Thank you so much :)

---

### Post by bcbc on 2013-04-08
You're welcome! :)

---

### Post by Bouvet on 2013-04-11
THANK YOU as well BCBC. The dual-boot with Vista-Ubuntu had been working great, then suddenly it wouldn't let me log on to Ubuntu, so I researched how to remove the dual boot. 
That part work fine, but upon rebooting, I was still getting the screen asking to select a system. I happened across this thread and saw your tip, followed it and VIOLA', it worked fine!
Thanks again!!

---

### Post by bcbc on 2013-04-11
You're welcome too! :)

---

