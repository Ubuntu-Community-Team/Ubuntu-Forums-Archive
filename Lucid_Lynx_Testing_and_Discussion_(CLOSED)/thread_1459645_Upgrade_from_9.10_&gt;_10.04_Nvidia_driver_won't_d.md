---
title: "Upgrade from 9.10 &gt; 10.04: Nvidia driver won't detect &amp; set 1920x1200"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Rizlaw on 2010-04-21
This afternoon I performed an upgrade from 9.10 x64 to 10.04 x64. After the upgrade I had a garbled 1280x1024 screen (not my native 1920x1200). I was able to deactivate the Nvidia driver and reboot to the new open source 2D video driver and get the correct 1920x1200. The open source 2D Nuveau driver works fine, but I prefer the Nvidia 3D driver.

While running with the 2D driver, I reinstalled & activated the proprietary Nvidia driver and rebooted, but the system only comes up in 1280 resolution with Nvidia.

Running "sudo nvidia-settings" allows me to successfully change to the correct 1920x1200 resolution, but after saving that setting and restarting X or rebooting the setting is lost and I'm back to 1280.

Seems like a bug to me. Any ideas?

---

### Post by Deadite81 on 2010-04-21
Hi.  Just saw your post in a feed and thought I might be able to help.
We have drastically different systems (Athalon X2 @2.5, onboard nvidia graphics, 32bit OS, etc.) but I think the problem is pretty universal.
I updated to Lucid at the beta 1 stage, which is when the Jockey 3rd party hardware driver update was not working at all.  I had to set up my nvidia driver manually. I used the newest (195.36.15) from the nvidia website, [here]("http://www.nvidia.com/Download/index5.aspx?lang=en-us").
But as of now, Jockey seems to be working.  Try is this simple command in a terminal window, which will automatically update your X server settings```
sudo nvidia-xconfig
```

Also, I had the same problem on Karmic, that is, not being able to update my X server settings using the nvidia-settings gui.  I don't remember how I fixed it, but I was getting an error message and you are apparently not.

And finally, I've noticed that while running Lucid a lot of my settings are not being saved.  I mean for all kinds of stuff: Nautilus Actions, Nautilus File Manager as superuser, Simple Backup tool, and so on.  Even altering some settings in the actual config files doesn't seem to help.  The next time I open the program it's settings are back to default.  But only some settings.  It's wierd, and I chalk it up to it being a beta release.

Sorry if this sounds rambly, but it's been a long day with too much coffee involved:)

---

### Post by Deadite81 on 2010-04-21
Also, as a side-note, to even get my nvidia driver to work at all, I had to disable the nouveau module completely in etc/modprobe.d/blacklist.conf.  I assume they're past the need to do that now, since your driver seems to function, but I left it disabled anyhow.  I'd rather see what's loading than a purple screen.

---

### Post by sdowney717 on 2010-04-21
When I change xorg.conf, I use gedit and manually save the new file.
When you change the settings using nvidia, click the preview, select all the text, then open gedit as sudo and save it.

---

