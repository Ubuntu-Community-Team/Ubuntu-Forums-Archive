---
title: "Not sure if my system is checking for updates on startup"
date: 2016-05-22
forum: Installation &amp; Upgrades
---

### Post by zzHanks on 2016-05-22
After I did a clean install of 16.04, I'm not sure if my system is checking for updates automatically.

I checked */var/log/syslog* and saw that an update-check occurred 16 minutes after the system booted (that probably was user-called)
I did change the settings in *Software & Updates* to display security updates immediately, rather than install them in the background.
When I run *Update Manager* it often has updates ready to install, but it rarely notifies me on its own.

My Google search didn't return answers I was looking for.

Should I be looking at another log file? Where?

Help greatly appreciated.

---

### Post by grahammechanical on 2016-05-22
You would have noticed that the system is set by default to automatically check for updates daily. I have found that the check takes places a few minutes after the system has loaded and then a notification appears top right of the screen if there are any updates. And that would include security updates.

 Update manager does not load. We just get the notification. Do not expect to be notified of security updates daily. They do not occur daily. Thankfully, Linux is too secure to require daily security updates.

If we change the frequency of when the system checks for updates, then we should not expect to get any notification of even security updates until the set time has arrived for the system to check for updates.

Regards

---

### Post by Dennis N on 2016-05-24
> After I did a clean install of 16.04, I'm not sure if my system is checking for updates automatically.

Hi zzHanks,

You may be onto something - I seem to be seeing a similar problem in my Xubuntu 16.04.

I have been suspecting the update notifier, since it has yet to inform me of the last Firefox update seen 2 days ago on another machine*, and in fact, I can't recall ever seeing any update notification here. I have manually installed and upgraded packages through Synaptic package manager several times since the installation last month, and it reports no problems with the sources.

Today I got the attached notification (see attachment). When I selected "Show Updates" on this advisory, a popup from Software Updater tells me "the software on this computer is up to date". No errors are indicated.

_Settings for Updates:_
Top boxes all checked.
Automatically check for updates: daily
When there are security updates: display immediately
When there are other updates: display immediately

I could run Synaptic Package manager now, and probably will see updates (as I have in the past), including the Firefox I have been looking for. But the update-notifier does not seem to be performing as it should. I will let this go a while longer to be sure.

*also Xubuntu 16.04, but with this difference: "When there are security updates: download and install automatically". Update-notifier gave a notification 2 days ago. I wonder if its different setting makes the difference? I will continue watching this for a while longer.

Stay tuned.

_Two days later:_

Four days after getting the Firefox update on my other computer and two days after posting the first part of this post, the software updater appeared, offering 250+ mB of updates (including Firefox). See the "software updater window" screenshot attached. So this proves it is all working with these settings.

---

