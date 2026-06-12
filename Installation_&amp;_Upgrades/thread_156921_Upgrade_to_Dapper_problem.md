---
title: "Upgrade to Dapper problem"
date: 2006-04-08
forum: Installation &amp; Upgrades
---

### Post by lemmy999 on 2006-04-08
Think i've made all the mistakes possible. Didnt backup Home! and installed a pre-release version of the OS!!

After upgrading from Breezy to dapper flight 5 i am getting xserver error messages. As a newb is this easy to fix? My options appear to be

1. Re-install and lose anything on Home
2.try and retrieve what i need from home using a live CD, then burn to disk
3. try and resolve the xserver problem
4. install the OS on another partition and then attempt to retrieve data from Home

Any thoughts as to the best way to proceed?

---

### Post by dermotti on 2006-04-08
Whats the xserver error?

---

### Post by lemmy999 on 2006-04-08
maybe trying to glaze a greenhouse and sort out my computer at the same time wasnt such a good idea. I will try and repost later.

---

### Post by Perfect Storm on 2006-04-08
upgrading a stable distro to an unstable distro is asking for troubles. As dermotti said we need to know what's the error(s) shown.

---

### Post by eriefisher on 2006-04-08
I put /home on a seperate partition/hdd just in case. If or when I have to reinstall I can keep my files. BUT YOU MUST ALWAYS BACK UP FIRST.

eriefisher

---

### Post by RRS on 2006-04-08
"3. try and resolve the xserver problem"

 ```
sudo dpkg-reconfigure xserver-xorg
```

Also, if I understand correctly, your live CD runs with the correct xserver configuration? If so you can copy these settings into your installed system.

Run this from the live to read your known good conf. 
```
cat /etc/X11/xorg.conf
```

Then after booting back into the installed,
```
 sudo gedit /etc/X11/xorg.conf
```
Simply change as needed to match the live CD file and then reboot.

This worked for me after a similar upgrade failure when "reconfigure" didn't.

Also, I'm sure someone here could probably show us how to simply copy the file rather then a manual edit of individual lines, can't be the most efficient method.

Hope this helps.

---

