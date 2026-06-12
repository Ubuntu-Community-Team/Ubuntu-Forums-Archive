---
title: "Strange ICEauthority - tried other fixes already, but still doesn't work..."
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by lifelike27 on 2011-04-28
I'm getting this error message after I login saying "Could not update ICEauthority file /home/jon/.ICEauthority" Loading then takes longer than usual and the audio indicator doesn't work. I'm running ubuntu on my laptop so the Volume button doesn't work.

I've tried changing the ownership of the files as mentioned in one thread([http://ubuntuforums.org/showthread.php?t=949750]("http://ubuntuforums.org/showthread.php?t=949750"))

I've also tried deleting the file (kept a back up) and then restarting, but that failed as well.([http://computers-linux.blogspot.com/2008/08/server-manager-unable-to-read-file.html]("http://computers-linux.blogspot.com/2008/08/server-manager-unable-to-read-file.html"))

Another reason I wanted to start a new thread is because I noticed, that there wasn't any post with people getting this error in newer versions of Ubuntu.

If I can get this fixed it saves me the time instead of doing a fresh install of 11.04 since final release! :D

---

### Post by Edu115 on 2011-04-30
I had exactly the same problems, but after doing [this](http://ubuntuforums.org/showpost.php?p=9147845&postcount=12) and rebooting the error disappeared and the audio indicator worked again.

---

### Post by lifelike27 on 2011-04-30
> **Edu115 said:**
> I had exactly the same problems, but after doing [this](http://ubuntuforums.org/showpost.php?p=9147845&postcount=12) and rebooting the error disappeared and the audio indicator worked again.

Hey, thanks for the help! When I run that command in the terminal (after changing 'user' to my username) I get the errors ```
chown: cannot access `/home/jon/./.gvfs': Permission denied
chown: cannot access `/home/jon/../jon/.gvfs': Permission denied
chown: cannot access `/home/jon/.gvfs': Permission denied

```

EDIT: I don't think I should worry about that though, I just restarted and the error went. =)

Thanks!

---

