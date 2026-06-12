---
title: "jDownloader 'server busy' — is there a problem with my installation?"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by Sicadastra on 2012-06-22
I recently reformatted my laptop to use 12.04 64-bit so I had to install everything again. When I installed jDownloader (via terminal, ppa), I'm always stuck with this 'server busy' message (please see attached image). I never had this problem when I installed it a week ago before I switched to 64-bit (I was using 32-bit then).

I'm wondering if there is a problem with my installation that's keeping me from downloading from the server? Or is this solely a jDownloader server problem? 

I tried installing jDownloader via script based on the program's website but I'm still stuck with the 'server busy'.

I hope someone can help me. :(

---

### Post by Enigmapond on 2012-06-22
If it says that it's probably the server you are attempting to download from and not jd. I would uninstall what you have now, delete the ~/.jdownloader file, reinstall using the proper ppa, (this only because you will get updates) and then try another download from somewhere else.

---

### Post by Sicadastra on 2012-06-22
> **Enigmapond said:**
> If it says that it's probably the server you are attempting to download from and not jd. I would uninstall what you have now, delete the ~/.jdownloader file, reinstall using the proper ppa, (this only because you will get updates) and then try another download from somewhere else.

I have installed and uninstalled jDownloader several times today already but with the same result although I did not delete that jdownloader file which could have affected the following re-installation. May I know how would I find the ~/.jdownloader file? I'm sorry, I'm really not familiar on troubleshooting Ubuntu. I'm doing a search of it through the file system search bar, but there's no result.

As for trying another download from somewhere else, may I know where could I get it? I only know the proper ppa of jdownlaoder ( sudo add-apt-repository ppa:jd-team/jdownloader).

Thank you for the quick reply.

---

### Post by Enigmapond on 2012-06-22
Your PPA is correct. The file is in your home file and is hidden. (CTRL + h to reveal) The errors you are getting actually are not from your destination for download but are the main jd server for updates. I have opened mine and there is no problem getting updates ...so try the reinstall.

---

### Post by Sicadastra on 2012-06-22
> **Enigmapond said:**
> Your PPA is correct. The file is in your home file and is hidden. (CTRL + h to reveal) The errors you are getting actually are not from your destination for download but are the main jd server for updates. I have opened mine and there is no problem getting updates ...so try the reinstall.

Thank you for this. I did as you recommended but I'm still stuck with the 'server busy' message. Would it be considered progress that it stopped at 1% instead of 0%? Perhaps my poor internet connection is at fault too. I'll try to download when the traffic is lighter. 

But may I know is there an alternative solution if ever that still won't work? I'd really prefer not to switch to another download manager if there's still a possibility.

---

### Post by Enigmapond on 2012-06-22
Could very well be your connection. Actually JD is the best IMHO...you may consider telling it it not to look for updates when started...this is in the settings tab. If all else fails, install FatRat...not bad but not Jdownloader....Good Luck!

---

### Post by Sicadastra on 2012-06-22
> **Enigmapond said:**
> Could very well be your connection. Actually JD is the best IMHO...you may consider telling it it not to look for updates when started...this is in the settings tab. If all else fails, install FatRat...not bad but not Jdownloader....Good Luck!

Thank you for the alternative. Sadly, I won't be able to see the main window until I get past the update. :(

---

### Post by Sicadastra on 2012-06-23
The problem was with the router I was using:  D-Link DIR-600 wireless router. I tried using our old wired router,  updated jDownloader and it worked. I'm not sure what is the settings  with my wireless router that blocked the updating since the settings are  all in default except for securing the net access.


  Also, I updated my Java version from 6 to 7. I'm not sure if it  contributed so I'm including this part too since I did this while trying  to work out a solution.

---

