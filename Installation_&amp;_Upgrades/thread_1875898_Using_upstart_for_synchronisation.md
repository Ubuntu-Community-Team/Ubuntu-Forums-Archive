---
title: "Using upstart for synchronisation"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by Roeland_P on 2011-11-05
In my home network, all data is stored on a NAS.  When I boot my pc's, the shares are automatically mounted (via /etc/fstab).  However, when I use my laptop anywhere else, I have no access to these shares (and data).

I wonder if with upstart a similar functionality can be obtained as "offline folders" does in Windows.  In that sense, I think a configuration file in /etc/init/ should dicdate that when a user logs on or off a synchronisation (rsync) between a folder on the pc and the server/nas automatically occurs.

Is that correct?  And if so, how should the configuration file look like?

---

### Post by papibe on 2011-11-05
I think 'Startup Applications' would be e better place for that, however depending in your practices you may even run the script manually (that's what I do).

This are two basic examples.

To get/update your files from the server:
```
rsync -av /path/to/mounted/nas/ ~/local_nas_copy/
```
If while away you modified the data, you can push the changes to the nas like this:
```
rsync -av --delete ~/local_nas_copy/ /path/to/mounted/nas/
```
(the option --delete will also delete files on the server that you deleted on your laptop).

Does that help?
Regards.

---

### Post by Roeland_P on 2011-11-13
I also run the scripts manually.  However, I want a solution where the synchronisation occurs automatically when a user logs on or of.  In that sense, manually running scripts or even 'startup applications' is no solution.
"Init-scripts" should be a possibility, but is upstart not replacing the "init-scripts"?

---

### Post by papibe on 2011-11-13
I see.

Another simple solution would be to use a crontab job. Here's a very good [tutorial]("https://help.ubuntu.com/community/CronHowto").

Note that if you use the keyword @reboot instead of the first five time fields, you would be running the job once, at startup time.

Hope it helps,
Regards.

---

