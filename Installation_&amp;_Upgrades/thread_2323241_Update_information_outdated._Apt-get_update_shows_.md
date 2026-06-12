---
title: "Update information outdated. Apt-get update shows no errors. No automatic updates"
date: 2016-05-03
forum: Installation &amp; Upgrades
---

### Post by hey2 on 2016-05-03
Hi.

Every week or so i get a red triangle in the menu bar warning me that the update information is outdated.

Apt-get update and the Ubuntu software updater (gui) shows no errors and make the notification go away.

I don't have the automatic updates enabled so i don't understand why this warning still appears.

It’s not a problem with my computer since it also happens on my laptop 

Does anybody know what could be wrong?

I'm using 14.04.

Thanks.

---

### Post by T.J. on 2016-05-04
> **hey2 said:**
> Hi.

Every week or so i get a red triangle in the menu bar warning me that the update information is outdated.

Apt-get update and the Ubuntu software updater (gui) shows no errors and make the notification go away.

I don't have the automatic updates enabled so i don't understand why this warning still appears.

It&#8217;s not a problem with my computer since it also happens on my laptop 

Does anybody know what could be wrong?

I'm using 14.04.

Thanks.

I am assuming that this is happening **after** you perform a manual *sudo apt-get update* and then reset the machine? If that is so, then as a next step, you should check where you are getting your updates from.  Please post the contents of your /etc/apt/sources.list file for us to see.  Don't worry, it doesn't contain anything personal, just lists of update servers.

Thanks!

---

### Post by hey2 on 2016-05-04
> **T.J. said:**
> I am assuming that this is happening **after** you perform a manual *sudo apt-get update* and then reset the machine? If that is so, then as a next step, you should check where you are getting your updates from.  Please post the contents of your /etc/apt/sources.list file for us to see.  Don't worry, it doesn't contain anything personal, just lists of update servers.

Thanks!

Hi.

Thanks for your reply.

I'm sorry if i didn't explain it correctly. My English is not very good.

This is the order:

- Red triangle appears.

- I click on the software updater, it checks for updates, it shows the updates available and i press cancel.

- After one minute the red triangle goes away.

- I click on the software updater and i do the the software updates.

- After 8 days or so the red triangle comes back again.

When the red triangle appears, if i do a apt-get update to check if there is any errors, it shows no errors and like the software updater, it makes the red triangle disappear.

Thanks again.

---

### Post by T.J. on 2016-05-04
> **hey2 said:**
> Hi.

Thanks for your reply.

I'm sorry if i didn't explain it correctly. My English is not very good.

This is the order:

- Red triangle appears.

- I click on the software updater, it checks for updates, it shows the updates available and i press cancel.

- After one minute the red triangle goes away.

- I click on the software updater and i do the the software updates.

- After 8 days or so the red triangle comes back again.

When the red triangle appears, if i do a apt-get update to check if there is any errors, it shows no errors and like the software updater, it makes the red triangle disappear.

Thanks again.

No worries.  As a matter of opinion, I do not consider the updater that Ubuntu uses to do popups as very reliable. 

You can perform a forced update in a terminal in the following way:

```
sudo apt-get update
sudo apt-get upgrade
```

That should solve your issue, assuming there is not a bug in the GUI updater software.  The first command will update the package database to current.  The second will perform the actual upgrade.  It will not upgrade you to the new Ubuntu.  It will only update you to the latest version of 14.04

---

### Post by hey2 on 2016-05-05
> **T.J. said:**
> No worries.  As a matter of opinion, I do not consider the updater that Ubuntu uses to do popups as very reliable. 

You can perform a forced update in a terminal in the following way:

```
sudo apt-get update
sudo apt-get upgrade
```

That should solve your issue, assuming there is not a bug in the GUI updater software.  The first command will update the package database to current.  The second will perform the actual upgrade.  It will not upgrade you to the new Ubuntu.  It will only update you to the latest version of 14.04

Hi.

Once again thank you very much for your reply.

I will try to update using the terminal and see if it makes any difference.

The part that i don't understand is that i have automatic updates turned off. Even if it had errors, it shouldn't be searching for any updates.

---

### Post by hey2 on 2016-05-12
Hi.

Unfortunately it didn't work.

I updated using the terminal, but after 8 days the red triangle is back.

sudo apt-get update shows no errors.

It's like every 8 days it tries to update automatically (even if automatic updates are disabled), but instead of searching for updates, it uses an update information from the past. 

Does anybody have any idea what could be happening?

Thanks.

---

### Post by hey2 on 2016-05-27
Hi.

Sorry for the bump.

When the update manager tries to update the system, does it check all the packages or just the ones that have a repository?

I'm asking this because i have the 32-bil Chrome installed even though i removed the repository.

Could this be the cause of the problem? 

If i hold the chrome package (dpkg --set-selections), would this resolve the Help? Can i still use chrome even if is hold?

Thanks.

---

### Post by Bashing-om on 2016-05-27
hey2; Hello;

Yeah could be:
> 
I'm asking this because i have the 32-bil Chrome installed

could be that snake in the grass.

When you say "chrome" what is the context ? 
chrome as an operating system ?
chrome as the browser chromium ?
chrome as the browser google-chrome ?


In this context, google has discontinued support for 32 bit softwares and has removed the 32 bit support from their servers.

It would help a lot to show us what the terminal outputs are:
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```

With the anticipation next of looking at the sources.

[INDENT][INDENT]a mystery
[INDENT][INDENT][INDENT]then we know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Impavidus on 2016-05-27
The red triangle indicates that the update information is old. If you set the system to not check automatically for updates and don't check manually either, this will happen after a number of days. By running **sudo apt-get update** or by opening the update manager, even when canceling the updates, the update information is refreshed and the triangle goes away. The notifier showing the red triangle is not involved in the updates, it only checks the age of the update information.

Note that running an unmaintained web browser is generally not recommended. In fact, it's typically best to install all upgrades available, but you may skip some of the less important ones if your bandwidth is limited or expensive.

---

### Post by hey2 on 2016-05-27
> **Bashing-om said:**
> hey2; Hello;

Yeah could be:

could be that snake in the grass.

When you say "chrome" what is the context ? 
chrome as an operating system ?
chrome as the browser chromium ?
chrome as the browser google-chrome ?


In this context, google has discontinued support for 32 bit softwares and has removed the 32 bit support from their servers.

It would help a lot to show us what the terminal outputs are:
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```

With the anticipation next of looking at the sources.[INDENT][INDENT]a mystery[INDENT][INDENT][INDENT]then we know
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Hi.

Sorry if i didn't explain it well enough.

I'm talking about chrome the browser. I only have the application installed because the 32-bit repository was discontinued. So i removed it.

This is my apt-get update ouput:

```
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65,9 kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease [65,9 kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [129 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages [361 kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [454 kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [736 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [5168 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12,7 kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [264 kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13,6 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [15,6 kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en [384 kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [2570 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [3206 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [76,0 kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en [7227 B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en [3699 B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en [188 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en
Fetched 2788 kB in 9s (290 kB/s)
Reading package lists... Done
```

Thanks

---

### Post by hey2 on 2016-05-27
> **Impavidus said:**
> The red triangle indicates that the update information is old. If you set the system to not check automatically for updates and don't check manually either, this will happen after a number of days. By running **sudo apt-get update** or by opening the update manager, even when canceling the updates, the update information is refreshed and the triangle goes away. The notifier showing the red triangle is not involved in the updates, it only checks the age of the update information.

Note that running an unmaintained web browser is generally not recommended. In fact, it's typically best to install all upgrades available, but you may skip some of the less important ones if your bandwidth is limited or expensive.

Hi.

Thank you very much for you reply.

I thought that this problem also happened on my laptop, but the last time i checked the triangle didn't appear for 20+ days. I will try to update again and see what happens

When the triangle appears, if i click on check for updates (red triangle menu), it says that the computer is up to date, even if that is not true.

Your explanation makes sense, but i don't understand why would they include a check for updates option if it doesn't do anything.

Maybe this is a bug, but i think this is one of those features that doesn't makes much sense. If you say that you don't want automatic updates. You should not have things in the background checking for updates.

The automatic updates should have only two options: Disabled and enabled ( Daily, Weekly, etc...). When it was time to make an update, it would simply make an apt-get update in the background and notice you of the available updates.

Thanks once again.

---

### Post by mörgæs on 2016-05-27
If the problem is solved please mark the thread so.

Also remember the **sudo apt-get dist-upgrade** command.

---

