---
title: "Cannot load my account!"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by dnccnd on 2006-06-09
I have just installed Ubuntu 6.06 from Breezy by downloading the update through the automatic update (don't know how it is called exactly, it's the red circle that pops up in the right upper side of the desktop, close to the clock, everytime that an update is available).

Everything seemed to go well. After 3 hours the installation was finished. I thought the system would restart on its own, but it didin't. Then I restarted the system manually.

Again everything was going very well, until I wrote my usual username and password. Then everything stopped!!! Nothing got loaded. Then I pushed the button to turn off the computer just for a couple of seconds, and the list of Ubuntu commands appears (the kind of DOS text). There I can read "Running local boot scripts (/etc/rc.local)" and "ok" on the right. But then two other lines with complicated numbers and text appear and the system shuts down.

I have tried to boot the other versions of Ubuntu, also the secure versions, but nothing happens.

During the installation I always chose to substitute exsisting files (those which had been edited) with the new versions.

I also clicked on the option icon in the lower left side of the Ubuntu screenshot where the account must be provided. There different kinds of systems can be chosen (i.e. Gnome and something else), but I didn't know what to choose!

I am using a IBM T23 notebook with Windows XP on another partition.

Thank you very much for any possible help!

---

### Post by user1397 on 2006-06-12
when you're at the login screen, can you press CTRL+ALT+F1? does it take you to a command-line-type screen?

---

### Post by laodan on 2006-06-13
I'm stuck in a similar situation as dnccnd.
At the difference of dnccnd, I have worked a few hours on my newly installed Ubuntu 6.06, and waa very satisfied I must say... before to close and open the system again. Everything was fine. An hour later I closed again and restarted and that is when I got stuck in a similar situation as dnccnd.

[QUOTE=dnccnd]I have just installed Ubuntu 6.06 from Breezy by downloading the update through the automatic update (don't know how it is called exactly, it's the red circle that pops up in the right upper side of the desktop, close to the clock, everytime that an update is available).

Everything seemed to go well. After 3 hours the installation was finished. I thought the system would restart on its own, but it didin't. Then I restarted the system manually.

Again everything was going very well, until ...[/QUOTE]

The loading of the system has appeared normally in the graphical GUI but the usual window with username and password don't appear. Instead I get a black screen with some Ubuntu commands  (kind of DOS text)

After input of my username at Ubuntu login I get the following:
CONFIGURATION ERROR - unknown item 'QUOTAS_ENAB' (notify administrator)
CONFIGURATION ERROR - unknown item 'NOLOGIN_STR' (notify administrator)
CONFIGURATION ERROR - unknown item 'ENV_HZ' (notify administrator)
CONFIGURATION ERROR - unknown item 'CHFN_AUTH' (notify administrator)
CONFIGURATION ERROR - unknown item 'CLOSE_SESSION' (notify administrator)

Then comes Password: I input my pass and I get the following:
"Last login: Tue 13 June ... on tty1
Linux Ubuntu 2.6.15.23.386 # PREEMT Tue May 23.. , 686 GNU/Linux"
[COLOR="Red"]
Then comes the command line:[/COLOR]
laodan@ubuntu:~$

I tried everything I could come up with as command but to no avail.

What should I input as command to open my system?
And if that works where do I need to go to change the configuration?

Thanks in advance.

---

### Post by dnccnd on 2006-06-14
I solved the problem by clicking on Options in the lower left part of the log-in screen shot and then selecting GNOME in the Select Session menu.

When I restarted the computer then, I went again in the Select Session menu and chose Last session (which then became the GNOME session).

Now everything works just fine.

I didn't get the error messages that you got laodan, but I hope this can work for you as well.

---

### Post by rcarring on 2006-06-14
This is the same problem I had when upgrading Breezy to Dapper one time -- one of the config files has redundant items in it, and should have been replaced at upgrade time.

Type startx

---

