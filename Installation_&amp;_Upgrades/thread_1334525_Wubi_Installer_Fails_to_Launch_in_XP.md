---
title: "Wubi Installer Fails to Launch in XP"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by HuckerJ on 2009-11-22
I have downloaded the most recent wubi installer and it only runs for a couple of seconds and does not bring up any installation screen.  I've checked the MD5 and it was right.  I've tried using the wubi installer on a 9.10 disc from windows and that didn't launch either. The 8.10 installer launches fine, but I was really hoping to try out 9.10.  Any ideas why the installer isn't working? 

Thanks

---

### Post by darkod on 2009-11-22
I do not remember how XP was about it, but if you right-click on wubi.exe is there option Run as Admin or similar? I think you have to do that in vista and 7 but really don't remmeber XP that good any more. :)

Also one hint about using wubi.exe: If you got it by extracting the Ubuntu ISO, double clicking wubi will try to download the whole ISO again. The way to avoid this is extracting wubi from the ISO but then also placing the ISO file itself (not extracted) into the folder where wubi is. That way it will use already downloaded ISO.

---

### Post by HuckerJ on 2009-11-22
Hmm....I tried doing run as and it spits out the following:

main.pyo
pylauncher.exe
pyrun.exe
python23.dll
version.pyo
[winboot]
[bin]
[data]
[lib]
[translations]

Then the windows error sound comes on and nothing happens after that.  Pylauncher and pyrun give errors.

---

### Post by Corbuntu on 2009-11-22
I can confirm the original problem, that is, the Wubi installer silently fails to launch at all on WIndows XP SP3 with no messages of any kind.

This thread seems to have become interested in other issues, but the original problem remains unaddressed and there is no solution posted anywhere.  

I have no card readers or other funny hardware to disable.  Running on a stock IBM ThinkPad T42, XP Pro with all latest updates.  All Wubi installers version 8.x work fine, but no Wubi installer version 9.x works at all.  

This problem needs to be addressed, it's giving Linux a bad name with Noobs (and besides, I'd like to get it running again, having removed my Wubi 8.10 installation before downloading  Wubi 9.10).

---

### Post by brikettfabrikant on 2009-12-07
Same Problem for me. IBM Thinkpad R52 + WinXP SP3. Wubi installer does not appear to cause any action. Didn´t find a solution yet. Does anyone have an idea?????

---

### Post by joes7 on 2009-12-07
Simply boot it from the LiveCD

---

### Post by brikettfabrikant on 2009-12-08
Hey Joes7! Thanks a lot for your quick reply!

Can I boot from live CD and install wubi, just as I would have under running windows?

Is this safe for the Windows installation? (Need to keep it on my disc...:()

Thanks a lot!

---

### Post by HuckerJ on 2009-12-08
The computer I tried installing on was a Thinkpad T43p. I find it interesting that all three of us have IBM Thinkpads.  Does anybody know if this is related to the problem?

---

### Post by brikettfabrikant on 2009-12-08
Interesting! That sounds pretty likely! I suppose there´s some of the IBM Software conflicting with wubi. But I have no idea, which piece it might be. Uninstalling all of the software ist not a practicable option for me at the moment, so I am thinking of going the Live CD way, that was suggested by Joes7. But I havent tried that before. Has anyone experience with that? Can I boot from the Live CD and afterwards install wubi under my existing WinXP installation???? Sounds a little scary to me...

---

### Post by HuckerJ on 2009-12-08
I remember trying the same thing, but I don't think installing from the Live CD is not the same as wubi.  I think it requires partitioning.

---

