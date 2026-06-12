---
title: "HOW TO: Fix wireless problem from Sept 24 update"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Rallg on 2009-09-24
Problem: You updated karmic on the morning of September 24. After the update, your wireless no longer works. You could connect via cable and fix it from the later update. But you only have wireless!

Cause: File /lib/libnm-glib-vpn.so.0 is missing.

Solution: Go into /lib using sudo nautilus. Find a likely file, copy it, re-name the copy libnm-glib-vpn.so.0 then re-boot. Worked for me!

It might make a difference which file you copy. I picked one at random (about 13K file size) and forgot which one I used. You might need to play with your network settings via System Preferences.

After re-boot gets you online, update again for the real fix.

---

### Post by jfernyhough on 2009-09-24
Go back a step; what file are you copying? Does it matter which one, or is it just looking for any file with that name? Surely a 'touch' would be safer than inserting random code that whatever process is looking for the file is not expecting?

---

### Post by Rallg on 2009-09-24
I admit that copying a random file (from the same folder, similar kind of file) is risky and a miracle if it works. But, in fact, it worked first time for me. Lucky guess! I knew which file was missing by trying to launch nm-connection-editor from Terminal. That gave me the error message.

It might have made a difference if I used VPN.

Actually, I first tried using an empty file with that name. But apparently there must be some minimum file size, so an empty file did not work.

Karmic, alpha testing: Results not guaranteed! Since I have another system, and have no personal files in Karmic yet, I can afford to experiment.

---

### Post by kansasnoob on 2009-09-24
> **Rallg said:**
> I admit that copying a random file (from the same folder, similar kind of file) is risky and a miracle if it works. But, in fact, it worked first time for me. Lucky guess! I knew which file was missing by trying to launch nm-connection-editor from Terminal. That gave me the error message.

It might have made a difference if I used VPN.

Actually, I first tried using an empty file with that name. But apparently there must be some minimum file size, so an empty file did not work.

Karmic, alpha testing: Results not guaranteed! Since I have another system, and have no personal files in Karmic yet, I can afford to experiment.

This:

**Karmic, alpha testing: Results not guaranteed! Since I have another system, and have no personal files in Karmic yet, I can afford to experiment.**

Should be etched in stone!

I appreciate your input, but words like "random" scare me. I'd personally not rename any "random" lib (library).

That aside your input is helpful and welcome:)

I was earlier looking for a way to work around this situation from the command line.

---

### Post by Rallg on 2009-09-24
Of course, I re-named the COPY of the lib file, not the original lib file! I picked a lib at "random" because I don't have enough knowledge.

If the copied file had made Karmic un-bootable, I could delete it from outside Karmic, using another system.

---

### Post by kansasnoob on 2009-09-24
> **Rallg said:**
> Of course, I re-named the COPY of the lib file, not the original lib file! I picked a lib at "random" because I don't have enough knowledge.

If the copied file had made Karmic un-bootable, I could delete it from outside Karmic, using another system.

If it's a multi-boot I'd be tempted to copy and paste an existing /lib/libnm-glib-vpn.so.0 from one OS to the other. (If that's possible.)

I wonder, if the live CD connects to the internet via wireless if such a file exists in the live CD environment?

It's an interesting situation. I think you did good figuring it out.

---

### Post by !nkubus on 2009-09-24
I just plugged a cable and typed

```

sudo /etc/init.d/networking restart
sudo apt-get update && sudo apt-get upgrade

```

and rebooted, problem was solved

---

### Post by hanzomon4 on 2009-09-24
how about this (note this issue should be fixed already) ```
 sudo ln -s /usr/lib/libnm-glib-vpn.so.1 /usr/lib/libnm-glib-vpn.so.0

```

---

### Post by forumache on 2009-09-25
```
sudo -s
cd /usr/lib
ln -s libnm_glib_vpn.so.0 libnm-glib-vpn.so.0
exit
nm-applet
```

That's it. No reboot, after fixing the link you just start Network Manager applet which didn't start before, click your wireless network and then update. The bug is fixed, so with the last updates you should be ok.

Don't forget to delete the link you created.

---

### Post by dadedo123 on 2009-09-25
My network manager freezes and quits if I left-click on it.

---

### Post by meborc on 2009-09-25
EDIT: sorry... misread post

---

### Post by AVakil on 2009-09-25
> **forumache said:**
> ```
sudo -s
cd /usr/lib
ln -s libnm_glib_vpn.so.0 libnm-glib-vpn.so.0
exit
nm-applet
```

That's it. No reboot, after fixing the link you just start Network Manager applet which didn't start before, click your wireless network and then update. The bug is fixed, so with the last updates you should be ok.

Don't forget to delete the link you created.


Worked for me.  Thank you.  I guess this is what happens when I decide to run an alpha version. :-)  The last major issue I had was when the GUI wouldn't start, now that was bad.

---

