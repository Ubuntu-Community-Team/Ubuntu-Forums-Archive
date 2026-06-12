---
title: "Upgraded to 14.04 - Gnome  Flashback (Metacity) missing top panel and taskbar"
date: 2014-07-23
forum: Installation &amp; Upgrades
---

### Post by chamira on 2014-07-23
I upgraded to 14.04 from 13.10 yesterday.

When I log in as the **main user** with the Gnome shell **GNOME Flashback (Metacity)** I see some desktop icons but both the top panel with my application icons and the task bar at the bottom of the screen are missing.

If I log in as **Guest user ** both the top and the bottom bars appear - top bar of course is blank as I am a Guest.

I have reset the Gnome panel as described here: [http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264) ( My Trusty Flashback w/Metacity tweaks and challenges ). 

Only the following code brought the panels back.But, the top panel is empty of icons AND this is not a permanent fix. When I log out and in, again the panels are missing:

```
XDG_MENU_PREFIX="gnome-flashback-" gnome-panel --replace &

```

Also, when I run that code I also get an error, I am not sure if this is relevant:
```
In pixman_region32_init_rect: Invalid rectangle passed
```

(I could not get a terminal to open using the keyboard shortcuts, so I logged in to Unity, created a desktop icon for the terminal  and logged back in to Gnome shell)

Has anyone found a permanent solution for this? Is it an Ubuntu or a Gnome Panel bug?

As much as I like Unity, I can work much faster on the Gnome shell and I would love to have this back again working.

---

### Post by ibjsb4 on 2014-07-23
> dconf reset -f /org/gnome/gnome-panel/
Should of worked.

Have you tried purging and reinstalling gnome-panel (also removing the config file in your home directory)?

The panel should be in your *Startup Applications*, is it there?  I have found at times the only way to get a startup app to work was to enter it in terminal.

One other thought, start the panels in terminal and see if you get any errors.  If terminal will not open, try console:

Ctrl Alt F1 should work and Ctrl Alt F7 should take you bace to the desktop.

---

### Post by chamira on 2014-07-24
Thank you for helping.

For some reason this code doesn't work ```
dconf reset -f /org/gnome/gnome-panel/
``` 

I will try your other suggestions and post back.

Here is what I have tried so far, since my first post:

[LIST=1]
[*]Created a brand New User with admin rights.
Gnome panel is working absolutely fine. 
But I am missing my settings &etc - some of them are tedious to set-up like Netbeans and Apache server, so I would really like my original user to work.


[*]Copied all my home drive from the Old User to the New User account, overwriting any files in the New User with the Old User files.
I made sure they are owned and had the right permissions using chown & chmod.
Now I can log in but Gnome panels are not working.
So the problem is with Gnome setting saved in my User account. Gnome setting seems to be spread throughout the home directory and I am no expert, so I can't track this error down.

I can reset using the code I mentioned in my first post. But here is the thing: when I swap between account, loging out and loging in, Gnome panels are working (after the reset). But if I Reboot/Restart, then I lose them in my Old Account.


[*]Created another New User and copied across all my home drive, but this time I SKIPPED any files that were common, preserving the New User files.
This time Gnome panels are working fine. But I am missing some settings for things like Firefox, and Apache server is missing environment variable setting &etc.
[/LIST]

---

### Post by chamira on 2014-08-05
This was a user configuration problem but I was going getting myself deeper and deeper in to a situation where I understood very little. 

I guess I could have created a new User,  copied everything across and changed ownership to the new user, deleted the old user, and renamed the new user to have the old users name!
But I would have messed up somewhere in that process.

So, I just backed up my home directory manually (copy & paste!), reinstalled 14.04, and have been copying across the application files from the backed up home directory as I install the applications I normally use.
This is working well, and the O/S is running faster too.

I didn't lose anything because I keep all my data on a separate hdd, which is backed up to an external hdd as well (an old paranoid habit from my windows user days!). 

The few extra hours installing an configuring my applications has been worth it. I have always thought the data/files we create is the most important thing, applications and OS can always be re-installed - and my problem this time proved my theory!

---

