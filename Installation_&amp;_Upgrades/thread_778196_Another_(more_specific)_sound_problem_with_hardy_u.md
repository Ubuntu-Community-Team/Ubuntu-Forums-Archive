---
title: "Another (more specific) sound problem with hardy upgrade"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by shaviro on 2008-05-01
After upgrading to Hardy, like many people I have had problems with sound. In my case, what happened was that there was no sound when I either played a DVD, or when I played an .avi or .mov or other movie file from the harddrive. (I never had a problem with Gutsy or earlier releases).

After looking through the forums for a while, I came across the solution of using the module assistant:

> 
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

I rebooted, and the sound worked!

However, after a subsequent reboot, I again had the problem of no sound from DVDs or movie files. I ran the module-assistant sequence again -- of course it told me that everything was already installed -- then rebooted, and the sound was back. 

Now this seems to happen over and over again. After a fresh boot, the sound problem returns. After I run "sudo m-a a-i alsa" in the terminal, and reboot, the sound is back. 

Any suggestions on what I can do to make the sound permanent?

---

