---
title: "Failed to download repository information: 16.04"
date: 2018-08-26
forum: Installation &amp; Upgrades
---

### Post by ray42 on 2018-08-26
```
Failed to download repository information: 16.04
```

My Gnome won't update, I get the above message.

When I click OK it then offers upgrade to 18.04.01 LTS

Is it ok with the following errors to upgrade?

```

W: The repository 'http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Also new software is not visible, and my installed apps won't show in software center, all but 3 of them. See pics.

[https://www.dropbox.com/s/hqtg2droqo6cwnx/Screenshot%20from%202018-08-26%2014-38-47.png?dl=0](https://www.dropbox.com/s/hqtg2droqo6cwnx/Screenshot%20from%202018-08-26%2014-38-47.png?dl=0)

[https://www.dropbox.com/s/fgic5dtjsakn4bm/Screenshot%20from%202018-08-26%2014-39-07.png?dl=0](https://www.dropbox.com/s/fgic5dtjsakn4bm/Screenshot%20from%202018-08-26%2014-39-07.png?dl=0)

---

### Post by deadflowr on 2018-08-26
Simple.
remove the cairo-dock ppa as it's no longer being updated for new releases.

---

### Post by ray42 on 2018-08-26
That is done, but still leaves the big issue

---

### Post by deadflowr on 2018-08-26
> **ray42 said:**
> That is done, but still leaves the big issue

What issue?

Edit:
If you mean the Software is still not showing all apps, then kill it and restart it.
gnome-software is always running in the background.
so try a simple *killall gnome-software* to kill it and then simply click on the Software icon to restart.
That should reload all properly.

(It can take sometime to reload; it's one of the reasons it's set as an always on app.)

---

### Post by ray42 on 2018-08-27
Thanks but unfortunately it made no difference, see the links to images previously posted.

---

### Post by ray42 on 2018-08-27
I upgraded oh dear oh dear black screen. I can get to grub menu but 18.04 LTS doesn't boot.

I did see one or two errors speeding past as it booted network manager didn't load, if that is important.

Helllpppp!!!

I now started a new request see link:

[https://ubuntuforums.org/showthread.php?t=2399581&p=13795565#post13795565](https://ubuntuforums.org/showthread.php?t=2399581&p=13795565#post13795565)

---

