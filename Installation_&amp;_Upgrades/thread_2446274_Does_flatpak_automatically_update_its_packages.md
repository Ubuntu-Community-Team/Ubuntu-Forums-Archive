---
title: "Does flatpak automatically update its packages?"
date: 2020-06-27
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2020-06-27
I've learning to use snaps and flatpak.

Snaps are easy as can be, even easier than PPAs, and its manual is helpful. Flatpak&#8230; not so much. However, some packages (e.g. OpenShot) are available on flatpak but not snaps, so I need to use it.

I've discovered that snaps are automatically refreshed four times daily.

But, I can't find out if flatpak packages are automatically updated. Are they updated automatically? If not, how do I set flatpak to automatically update the installed packages?

Thanks

---

### Post by &amp;KyT$0P# on 2020-06-27
From [https://blogs.gnome.org/mclasen/2019/10/03/some-flatpak-updates/#comment-20089]("https://blogs.gnome.org/mclasen/2019/10/03/some-flatpak-updates/#comment-20089") -
> Automatic updates are not a concept that flatpak itself has. App stores like GNOME Software can (and do) implement auto-updates, together with a user setting to disable them.

---

### Post by deadflowr on 2020-06-27
No.
You need to update them manually, either using the flatpak command line or through the Ubuntu software program, 
but through the software program requires the flatpak plugin gnome-software-plugin-flatpak to be installed.

Ubuntu 20.04 ships with snap-store as the software app and it doesn't support flatpak, so in order to use the flatpak plugin the gnome-software deb version needs to be installed.
(gnome-software will show as Software in the apps menus.)

---

### Post by Dennis N on 2020-06-27
> I can't find out if flatpak packages are automatically updated. Are  they updated automatically? If not, how do I set flatpak to  automatically update the installed packages?
A few of them do update automatically*. Gimp is one that does. You will get a popup notification that the update has been done. See attached screenshot.

* You may need gnome-software (Software) installed with its Flatpak plugin.

---

### Post by Paddy Landau on 2020-09-06
Sorry for the late reply. For some reason, I didn't receive a notification for this thread.

Thank you for your responses. I've installed gnome-software and gnome-software-plugin-flatpak, and I'll check occasionally for updates.

---

### Post by vanadium on 2020-09-06
I am indeed surprised to learn that flatpaks do not auto-update. However, [here]("https://www.reddit.com/r/flatpak/comments/b47w2a/can_flatpaks_update_themselves/") I learn that gnome-software is what takes care of the updates. So there would be no need to check yourself if you have gnome-software and gnome-software-plugin-flatpak (via APT). I do, and I regularly receive a notification of an updated application.

---

### Post by Paddy Landau on 2020-09-06
> **vanadium said:**
> … I regularly receive a notification of an updated application.
Thanks for the extra info.
You're right that it's bizarre for flatpak not to have automatic updates built-in.
I'll look out for the notifications on my computer.

---

### Post by Paddy Landau on 2020-09-13
I've been following flatpak's updates, and it looks as though they aren't being updated.

Everything that I've read says that flatpak is automatically updated, and the only timescale that I've found is that it's updated ten minutes after booting. Well, I've booted a few times since the 11th (even though it's only a couple of days since then), but the packages haven't been updated.

The only instructions that I've found is that you can disable automatic updates by removing them from Startup Applications. I don't want to disable them, but interestingly, Startup Applications doesn't mention flatpak.

I also don't find any mention of flatpak in crontab (mine or root's), /etc/anacrontab, or any of the files in /etc/cron*.

I have installed both gnome-software and gnome-software-plugin-flatpak.

Dropbox is a case in point. My installed version is 104.4.175, but the [current version]("https://flathub.org/apps/details/com.dropbox.Client") (updated 11 September) is 105.4.651.

So, it seems, flatpak is **not** updated automatically.

I shall add "flatpak update" to /etc/cron.daily and see what happens — unless you have a better idea!

---

### Post by Paddy Landau on 2020-09-13
Oh…

This is interesting!

Searching for more information, I discovered that Ubuntu 20.04 has **two** software apps: "Ubuntu Software" and "Software".

They look identical.

But.

"Ubuntu Software" (which I was using) shows that everything is up to date.
"Software" shows me the pending updates, including Dropbox.

So.

"Ubuntu Software" seems to ignore flatpaks.
"Software" seems to take them into account.

If I go to my apps and right-click on "Ubuntu Software" > "Show Details", I get an error saying that there are no details for that application.
If I go to my apps and right-click on "Software" > "Show Details", it shows me the installed Software app, as well as showing that the plugins for flatpak and snaps are installed.

In addition, "Ubuntu Software" has limited options, whereas "Software" lets me set automatic updates. That option was already turned on, so I don't know why the flatpaks haven't been updated.

I'm going to post a new question about the two software packages on Ask Ubuntu.

---

### Post by Dennis N on 2020-09-13
> So, it seems, flatpak is not updated automatically.
My observations from using Flatpak for a while:

The automatic updating only happens for-sure in Ubuntu 20.04 and depends on the flatpak plugin for Software. I'm not certain it works with Ubuntu Software (which is a snap package) - I do have one such system, and will have to look and see. Earlier releases perhaps back to Ubuntu 18.04 gave a notification (screenshot 1 attached), but as I recall, didn't automatically update any Flapak applications. 

In Ubuntu 20.04, you will only see a notification when updates have completed (screenshot 2 attached).

The updating of support Platforms (such as 'KDE Application Platform') is not that clear. I'm sure of one case where one did, but it doesn't seem to always happen.

Also, unneeded support Platforms will not be removed unless you do it yourself.

I don't have knowledge how other desktop environments like XFCE behave with Flatpak.

UPDATE:
Here's an article mentioning [Flatpaks updating automatically]("https://www.phoronix.com/scan.php?page=news_item&px=GNOME-3.30-Auto-Updates-Flatpak"). According to this, automatic updating for Flatpak requires gnome 3.30 or above. Ubuntu 19.10 has gnome 3.30 (and gnome-software 3.30), so it must have worked there as well.

---

### Post by Dennis N on 2020-09-13
Here's some information on Ubuntu Software and Flatpaks excerpted from [this article]("https://medium.com/@uncertainquark/how-to-install-flatpak-apps-on-ubuntu-20-04-lts-6c3f632cc605"):

> In 20.04 LTS, Ubuntu&#8217;s Software Center was switched from being a .deb version of GNOME Software to a snap app. The new snap store can handle management of snap applications and traditional .deb applications. **But it can&#8217;t install or remove Flatpak applications as the .deb version could**. In all, it&#8217;s a step back.

Suggestion:
There might be some conflict between Software and Ubuntu Software on updates - I would remove Ubuntu Software (snap) and see if the Flatpaks will update as they should.

---

### Post by Paddy Landau on 2020-09-15
> **Dennis N said:**
> The automatic updating only happens for-sure in Ubuntu 20.04 and depends on the flatpak plugin for Software.
… automatic updating for Flatpak requires gnome 3.30 or above.
This is a fresh installation of Ubuntu 20.04, I have the plugins, and my Gnome version is 3.36.3.
I have had no notifications whatsoever about updates (not just flatpak) since I installed it ten days ago.
> **Dennis N said:**
> I would remove Ubuntu Software (snap) and see if the Flatpaks will update as they should.
Thanks. I removed the Ubuntu Software snap yesterday, so we'll see what happens.

---

### Post by Paddy Landau on 2020-09-15
Update: I've just received a notification from Software, which automatically opened in the background. So, that's cool.

It doesn't automatically update (except for security updates, I believe), but at least it lets me know, and it allows me to update with a single click of the mouse.

---

