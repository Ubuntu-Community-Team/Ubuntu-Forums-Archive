---
title: "frequent application crashes following Ubuntu upgrade"
date: 2014-06-15
forum: Installation &amp; Upgrades
---

### Post by ChrisC on 2014-06-15
I'm writing this report of my problem somewhat piecemeal, coming back and editing it to flesh it out.  The browser keeps crashing on me and I lose my typing.

I updated my Ubuntu installation a couple nights ago, and since then the machine has been quite unstable. 

Firefox: clicking on anything in menubar (e.g. "File", "Edit") crashes app; sometime just mousing over the menubar crashes it
Firefox: right click on back button crashes app
Firefox: flash seems to crash app (Youtube does instantly, CNN within seconds)
Thuderbird: toggle To:/Cc: button crashes app
Ubuntu:  sound prefs app crashed
more symptoms to be edited in

After force quit of Firefox, system monitor shows plugin-container processes in stuck states ("futex_wait_queue_me").

I wanted to try disabling flash in Firefox, but I can't get to the Addon menu, because clicking the menubar crashes Firefox :)

The system monitor shows the process "canberra_gtk_play" in the state "rt_mutex_timed_lock".   Constantly.  Is that normal?

Similarly, process "gvfs_fuse_daemon" is in state "futex_wait_queue_me".  Normal?

Suspecting sound problem, I tried a "ping -a", which is supposed to beep on every ping, and that locked up the OS windowing system (e.g. couldn't grab title bars and move windows around) so clearly something is very wrong.

In case this is just a problem with sound, I'd like to completely disable it, hence the sound prefs app, which is also crashing per above.  How to disable sound without sound prefs app?

Now, here's the tough part.  I'm running 10.04 Lucid.  I realize it's old, and past the LTS period, but I had been continuing to get system updates (just security, I guess) so I'd been continuing with it.  I guess I need to go ahead and upgrade the OS to a newer LTS, but that's a majro undertaking for me.  I'll need to prepare the machine for that, and clear a spot in my calendar, which in short means I can't do it this instant.

So for now I'm just trying get things usable again.  And I'm hoping that this update has been causing trouble for others, that the Ubuntu team is on it, and that there will be some sort of fix within days, or at least a workaround like disabling sound or flash.

Any help is greatly appreciated!

---

### Post by sudodus on 2014-06-15
There are full updates for Ubuntu Server version 10.04 LTS until April 2015, but since April 2013 (more than a year ago) there are not even security updates for Ubuntu desktop version 10.04 LTS. This means that there are no updates for the desktop specific program packages and you are strongly recommended to stop running this version, at least when connected to the internet. You can fix it temporarily by switching to a previous kernel, but ...

We do not support Ubuntu desktop 10.04 LTS. See this link.

[Forums Staff recommendations on 10.04 desktop release.]("http://ubuntuforums.org/showthread.php?t=2229730")[URL="http://ubuntuforums.org/showthread.php?t=2229730"]
[/URL]
If you have no luck with any of the recommended tips in the link, please create a new thread and ask for help to make a fresh installation to replace 10.04 LTS. In that case please specify the computer hardware. Run the following commands and post the content of the file **lshw.txt**.

```
sudo -s
lshw -sanitize > lshw.txt
exit
```

---

