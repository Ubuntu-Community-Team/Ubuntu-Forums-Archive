---
title: "Trying to upgrade to Edgy, completely froze twice"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by User2323 on 2007-01-27
Hello. I have Dapper installed and I'm trying to upgrade to Edgy. First, I followed the instructions and ran gksu "update-manager -c". After it downloaded the upgrade files and I clicked Start Upgrade, it gave me the error "Failed to lock /var/cache/apt/archives/lock" and failed. I tried it again and the same thing happened. So I looked in the /var/cache/apt/archives folder and I noticed some packages were being downloaded to partial.

I had the update utility set to automatically download updates but not install them, so I thought maybe this was causing some conflict. It turns out it was actually downloading Edgy packages so I thought maybe something got mixed up. I went to the Software Properties utility to turn off the auto downloading. After I did this, I clicked on one of the tabs at the top and the computer literally froze. I couldn't get to another screen or do anything. So I did a hard reboot and tried to upgrade to Edgy again. It had already downloaded some packages so when it asked me to confirm the upgrade it showed less files had to be downloaded. I clicked Start Upgrade and waited. In the middle of downloading it froze completely again. So I rebooted again and came to post this.

I was shocked to see any Linux, especially the LTS "stable" release of Ubuntu completely freeze like that. And it did it twice! Wow.

Also while downloading it drops to very low speeds like 4 KB/sec sometimes, but I don't think this is related.

This is on a Dell laptop, but is this related to hardware? I haven't had any problems like this until now.

---

### Post by an.echte.trilingue on 2007-01-27
It should not be shocking: updating an OS is very risky no matter what the OS.  The vast majority of OSs (red hat, windows)won't even allow you to do this, you simply have to reinstall when you want a new version.  That is why my advice is to never update from a system that you know works to one that might not work unless there is a specific reason you need/want to.

Anyway, the update manager is buggy for some people, I don't know why.

Just do this:

```
sudo gedit /etc/apt/sources.list
```

and change all of the instances of dapper to edgy

and then 
```
sudo aptitude update
sudo aptitude dist-upgrade
```

Take care
-mat

---

### Post by User2323 on 2007-01-27
This is unbelievable. I opened GAIM to try joining #ubuntu. Right after joining I tried to maximize the channel window, and the system locked up again. I don't know what's happened here, this wasn't happening at all before and now it's happening even when I'm not trying to upgrade. I really didn't expect this from a stable LTS release.
[B]
Edit: [/B]Thanks for your help an.echte.trilingue. I didn't want to try that because I think in the wiki it said not to, but I guess I will try it now.[URL="http://www.ubuntuforums.org/member.php?u=111395"]
[/URL]

---

### Post by an.echte.trilingue on 2007-01-27
> **User2323 said:**
> This is unbelievable. I opened GAIM to try joining #ubuntu. Right after joining I tried to maximize the channel window, and the system locked up again. I don't know what's happened here, this wasn't happening at all before and now it's happening even when I'm not trying to upgrade. I really didn't expect this from a stable LTS release.


I would bet euros against dollars that the problem is in your video card driver.  For some reason, some of the ubuntu patches seem break Xorg, especially on older/eccelectic hardware.  For all its talk about stability, ubuntu leans more toward newer software, warts and all.  If the dist-upgrade does not fix this, drop me a line.

I have one computer with a Savage S3 card, and I updated one day, and boom, anything requiring lots of memory or graphics would hard crash the box, and the only fix for it was to switch to etch.

Take care,
-mat

---

### Post by User2323 on 2007-01-27
Before I tried the dist-upgrade, update-notifier told me about 471 new updates. It turns out the upgrade utility had already changed the repositories. I decided to try a regular upgrade one last time, and this time it actually finished. After rebooting everything seemed fine but there was some error in the sources.list file that prevented apt-get from working. It was an extra line that I guess was caused by the upgrade program running twice, so I just removed it. Everything seems to be fine now. 

I'm using the open source ATI driver if that helps. The strange thing about this is how it crashed three times in a short period but was fine before and after. Oh well, I'm just glad it's working now.

---

