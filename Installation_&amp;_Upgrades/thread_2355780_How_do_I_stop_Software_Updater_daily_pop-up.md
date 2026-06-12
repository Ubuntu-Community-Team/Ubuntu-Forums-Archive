---
title: "How do I stop Software Updater daily pop-up"
date: 2017-03-16
forum: Installation &amp; Upgrades
---

### Post by belltown on 2017-03-16
I'm using Ubuntu 16.10 Desktop. Every day, I get the Software Updater pop-up that tells me that "Updated software is updated for this computer. Do you want to install it now?" I want to stop that from happening.

I went into Settings and selected 'Never' for 'Automatically check for updates', and 'Display every two weeks' for ''When there are other updates'. There's no 'never' setting for security updates.

I want to be able to control myself when I check for, download and install any new updates. Usually, I'll have some point during the day when I don't have to get actual work done and I'll run```
 sudo apt update && sudo apt dist-upgrade -y
``` I do not want the Software Updater to do this for me automatically -- EVER. I don't want to see the Software Updater pop-up box -- EVER. 

I've tried un-checking all the check boxes under 'Install updates from'. However, while this does stop the Software Updater from popping up, it also seems to prevent apt dist-upgrade from working.

The main reason I recently switched from using Windows 10 to Ubuntu, was because I was annoyed at how Windows gave me very little control over the update process, forcing me to work the way they wanted me to. I was hoping that with Ubuntu, I'd be able to take control over the process of checking for and installing updates, but so far it seems very Windows-like in that respect.

Does anyone know how to stop the Software Update pop-up box from appearing, so that I can do my own update checks with apt update and dist-upgrade? I don't need to get rid of Software Updater. I just don't want it automatically popping up telling me there are updates.

---

### Post by TheFu on 2017-03-16
You need to be current when you toggle the "never bother me" switch - at least with 16.04.  Don't know about 16.10. Sorry.

There is the update-notifier-common package that can be removed too. It is a metapackage, so removing it might remove some other things you may want.

---

### Post by deadflowr on 2017-03-16
Try
```
gsettings set com.ubuntu.update-notifier no-show-notifications true
 
```

---

### Post by Autodave on 2017-03-16
Settings -> Session & Start-up. Uncheck the Update Notifier.

---

### Post by belltown on 2017-03-16
> **deadflowr said:**
> Try
```
gsettings set com.ubuntu.update-notifier no-show-notifications true
 
```
That sounds like exactly what I was looking for. I'll give it a try. Thanks for your help.

---

### Post by belltown on 2017-03-16
> **Autodave said:**
> Settings -> Session & Start-up. Uncheck the Update Notifier.

Where do I find the "Session & Start-up" Settings. I have a 'System Settings' icon on the launching thing that only gives me Personal, Hardware, and System settings; none of those settings contain "Session & Start-up".

---

### Post by Impavidus on 2017-03-16
If you set it to never check for updates it will never find them, so it shouldn't bother you with a popup to install them. Unless you decide not to install the available updates.

But if you run```
 sudo apt update && sudo apt dist-upgrade -y
```you tell your system to check for available upgrades and install all of them, no further questions asked, even if that means uninstalling some packages. That's not what I call control over installation of upgrades.

This morning I had a small glitch. I ran ```
sudo apt update
sudo apt upgrade
```and saw some packages were held back. Further investigation revealed kernel 4.8.0-42 was available, pulled in by a new version of linux-generic, which could not be upgraded without uninstalling snapd. I cancelled the upgrade. This evening (UTC+1) the glitch was gone and I upgraded my software (without a kernel upgrade). If I had executed your command, snapd would have been uninstalled.

---

