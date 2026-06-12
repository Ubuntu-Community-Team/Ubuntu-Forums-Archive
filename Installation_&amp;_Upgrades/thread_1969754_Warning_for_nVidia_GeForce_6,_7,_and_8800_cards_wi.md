---
title: "Warning for nVidia GeForce 6, 7, and 8800 cards with 12.04 Precise"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by Tanker Bob on 2012-04-30
nVidia has posted a warning on their Linux forum [here](http://www.nvnews.net/vbulletin/showthread.php?t=178460) about a serious issue with the GeForce 6, 7, and 8800 GTS/GTX cards, K/Ubuntu 12.04, and their latest 295.40 driver. The 295.40 driver is the default installation in Ubuntu 12.04 as I write this.

Until a fix is released, you can run Precise in Ubuntu 2D mode as is, then uninstall the 295.40 driver and install the 295.33 driver which can be downloaded [here](ftp://download.nvidia.com/XFree86/Linux-x86_64/295.33/). Be sure to follow the instructions in the readme located in the 295.33 download directory.

I'm successfully running Precise in 3D mode with the 295.33 driver, getting ~8000 fps on my 8800 GTS card. I troubleshot 12.04 for about 7 hours before discovering the nVidia driver issue. nVidia is actively working a fix.

Someone may want to make this post sticky until the fix is released and incorporated into 12.04.

---

### Post by rtalcott on 2012-04-30
I had what I believe was this problem with having to run nVidia in 2d but the latest updates finally allowed me to install nVidia current and all is now well at least for me.
rt

---

### Post by Tanker Bob on 2012-05-02
nVidia has published an [updated beta driver](http://www.nvnews.net/vbulletin/showthread.php?t=179882) here that addresses these issues. I have not had a chance to test it yet.

---

### Post by Tanker Bob on 2012-05-02
nVidia's new beta 302.07 driver fixed all the video issues from my upgrade to 12.04. I'm marking this thread as solved.

---

### Post by Pablo Pablovski on 2012-05-03
Nvidia certified driver **295.49** released. Seems to resolve the issues that we've seen over the last few weeks. But it's not in the repos yet, so it's a manual install for now.

[http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html)

---

### Post by VMC on 2012-05-03
> **Pablo Pablovski said:**
> Nvidia certified driver **295.49** released. Seems to resolve the issues that we've seen over the last few weeks. But it's not in the repos yet, so it's a manual install for now.

[http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html)

I just installed 295.49. I still get the lost of focus for a couple of seconds. Same as 295.20 or 40.

---

### Post by Newkastle on 2012-09-13
Thanks for the suggestions.  I should mention this is my first foray into a non Windows OS.  Hopefully there are some stickies or threads on how to install non graphical version and update the drivers.  Let the fun begin!  The PC I'm installing this on does not currently have an OS installed on it.

---

### Post by oldfred on 2012-09-13
Closed, necromancy.

Current  nVidia driver versions are downloaded as part of the Ubuntu restricted driver updates.

nVidia versions have long past this issue and you have to check the nVidia site for latest info on legacy drivers.

---

