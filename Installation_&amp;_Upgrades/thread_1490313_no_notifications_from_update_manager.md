---
title: "no notifications from update manager"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by manubbo on 2010-05-22
Hello,

I set the update manager to notify about available upgrades and checking daily, but for 3-4 days if I don't run the manager I don't receive any notifications. Of course, if I run it I see at least 10-12 updates. I'm running Ubuntu 10.04. Any suggestions?

---

### Post by pr0t3g3 on 2010-05-22
It shouldn't matter if you recieve any update notifications you should always check to see if All of your programs are up to date especially the ones ubuntu doesn't support.

You can take care of that by opening your terminal and individually typing the programs in or just updating them all at once.

You can find the terminal by going to applications>accessories>terminal

once you have loaded the terminal type in:

sudo apt-get update

and when it prompts for your password type it in and press enter

if there are any available updates they should all be taken care of.

Now if you want to update an individual program type in

sudo apt-get upgrade (name of program)

---

### Post by kerry_s on 2010-05-22
> **manubbo said:**
> Hello,

I set the update manager to notify about available upgrades and checking daily, but for 3-4 days if I don't run the manager I don't receive any notifications. Of course, if I run it I see at least 10-12 updates. I'm running Ubuntu 10.04. Any suggestions?

check your system monitor see if update-notifier is running.
if you have it set to install security it won't notify you, as it says "without confirmation".

---

### Post by Peter Bell on 2010-05-22
I experience the same problem ... updates aren't notified since upgrading to Lucid - I have to invoke the Update Manager manually.

The update-notifier is running, set to 'Check for updates' - 'Daily', and 'Only notify about available updates'.

It seems to me that this is just one of many little problems introduced in Lucid.

---

### Post by sburris on 2010-05-24
My problem is centered around updates but is different. When I try to check for updates in Update Manager, I get the following message after I upgraded from 9.10 to 10.04 and try to get updates.
GPG error: [http://apt.last.fm](http://apt.last.fm) debian Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2F29191CA62DDDFFailed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by alco75 on 2010-05-25
Same here, no update notifications, despite it being set to check daily and to include security and recommended.

---

### Post by ..::| Dave89 |::.. on 2010-05-25
Same here, I have it set to notify daily, but I still have to manually check for updates.

---

### Post by cajunlibra on 2010-05-26
Same here, I'm getting no notifications when updates are available. Running "sudo apt-get update" doesn't upgrade packages either. I have to manually upgrade in Synaptic or run "apt-get upgrade" in order to update installed packages.

EDIT: I did a clean install about a week or so before 10.04 went live.

---

### Post by strydervtx on 2010-05-26
I have a similar problem. Since installing 10.04 (clean) about a month ago, I have never seen the "update-notifier" that I was used to in 8.04 (the orange star-like symbol that would appear in the top panel near the date/time and logout icons). I went into the gconf-editor and changed regular_auto_launch_interval to 0 just to see if it would start, but it doesn't. However, the update-manager automatically starts minimized, which is hard to catch if I already have a number of windows open. Obviously, updates are detected because the manager runs, but it would be nice if the notifier would run, too.

EDIT: I recently discovered that the 'auto-launch' setting for the 'update-notifier' controls the auto launch of the 'update-manager', not the notifier that appears on the top panel. By deselecting the 'auto-launch' I get the desired behavior: an update notification icon that I can click to run the update manager.

---

### Post by jcourcel on 2010-07-15
Hello

To get the red icon alert when you have update available, you need to configure the "auto_launch" parameter of the update-notifier to false.  To do that, just start gconf-editor and goto apps/update-notifier.  you will found the "auto_launch" parameters.

If you do not want to have the red icon alert and you want the update manager to start instead, then put the "auto_launch" = true.

Last thing to do, be sure to have the "Update Notifier" check in the "Startup Applications".  You could verify this by doing the following command in a shell: ps auxw | grep -i notifier
if you do not see it, than you could start it manually by doing the command: update-notifier in a shell.

Hope this little clarification will help people.

Regards

---

