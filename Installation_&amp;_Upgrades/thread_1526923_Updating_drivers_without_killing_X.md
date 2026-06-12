---
title: "Updating drivers without killing X?"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by Hero_Lief on 2010-07-08
Hello. I've had Ubuntu 9.10 for awhile, and recently updated to 10.04. However, I'm unable to update drivers. The newest drivers for Ubuntu are specified as "195.36.24", however NVidia's site shows 256.35 as the most recent version. I'd like to update, so I downloaded the new drivers, and ran them. It told me to kill off X server, and so I did. However, in 9.10 when I did, it gave me a form of fullscreen command-line interface. Ever since I've updated to 10.04, it gives me some randomly arranged glitched up white and red pixels on the top of the screen, and doesn't respond to anything. What might be the problem? If it's unfixable, can I install the new drivers WITHOUT killing X, and instead just rebooting once the drivers are installed?

---

### Post by Hero_Lief on 2010-07-08
Bump... Someone help, I need to get this fixed by tonight!

---

### Post by buddyd16 on 2010-07-08
have you gone through this thread:
[http://ubuntuforums.org/showthread.php?t=990978]("http://ubuntuforums.org/showthread.php?t=990978")

---

### Post by Hero_Lief on 2010-07-08
Yeah, I went through that, and now the right line works. However, I need to kill the x server. I've done ctrl alt backspace, however when I kill it, it restarts it. Any idea on how to stop it?

---

### Post by buddyd16 on 2010-07-08
ctrl-alt-backspace is the command to restart the xserver not stop it. I don't think I quite understand what you are asking though. If you followed the guide in my previous post step 4. tells you how to stop X.org/GDM.

It may be helpful for you to either print out that post or write down the directions given by Kosimo before you go through the process.

Also before going through that process make sure you uninstall all of your other install attempts and disable the proprietary drivers in ubuntu.

If you have any other questions may I suggest posting in the thread I linked as you may have a better chance of getting replies.

---

