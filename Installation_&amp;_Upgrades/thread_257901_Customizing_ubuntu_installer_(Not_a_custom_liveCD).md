---
title: "Customizing ubuntu installer (Not a custom liveCD)"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by selva on 2006-09-15
Hi,
I've looked around the forum for any discussion on how to customize the ubuntu installer (note that I am not trying to create a custom liveCD. If I were, this thread [[http://www.ubuntuforums.org/archive/index.php/t-5981.html]](http://www.ubuntuforums.org/archive/index.php/t-5981.html]) would greatly help). Essentially, I want to create an installer that installs a slightly more customized set of software than what is provided in the Dapper Drake release. This is for my parents back in India who need a fairly simple set of software (Firefox with Flash to see flickr pages, Evolution for gmail access, Skype, gaim, tamil language fonts). For remote support I'd go with FreeNX, which I have tested in my current ubuntu test install. 

I could potentially customize ubuntu post-installation but I suspect I would need to install ubuntu for a lot many relatives and a customized installer is probably what I need. In my case, a custom LiveCD is not as useful as a harddrive install.

I'am just getting started with Ubuntu and I think it's one of the most thoughfully packaged distros available anywhere. 

Thanks for all the tips and pointers.

---

### Post by wkulecz on 2006-09-15
Ubuntu may be thoughtfully packaged but what you (and I) want to do seems not to have been given much thought.

Unless you've done: apt-get clean,
all the packages you've installed are still stored in: /var/cache/apt/archives

Easy enough to copy these to a USB drive or alternate CD but a bacth install of all the packages in a sub-directory doesn't seem to be part of apt/dpkg.

Best I've found yet is: [http://ubuntuforums.org/showthread.php?t=42862](http://ubuntuforums.org/showthread.php?t=42862)

where presumably you'd make your packages into a local CD repository, configure Synaptic to show only its packages, and then do "Mark all" and "Apply".

I haven't had a chance to try yet because I got hammered yesterday by the defective kernel update pushed out yesterday morning.

I need to set up six identical systems now and more later, so I'd like to know if this works.  Since I'm now short of time I'll probably use Norton's Ghost 2003 to clone the drives from a DVDROM made with Ghost of the master system.  But this only works if you stick with ext3, other Linux filesystems are not supported.

--wally.

---

### Post by linear on 2006-09-16
I think you may want the [InstallCD customization]("https://help.ubuntu.com/community/InstallCDCustomization") instructions. (Haven't tried them myself, so no guarantees.)

---

### Post by selva on 2006-09-17
Thank you, linear. I'll update here if I get something working (May not be immediate.)

---

