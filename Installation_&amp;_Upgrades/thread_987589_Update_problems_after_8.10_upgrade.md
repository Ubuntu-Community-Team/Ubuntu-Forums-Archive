---
title: "Update problems after 8.10 upgrade"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by kaptain1 on 2008-11-19
Hello All,

I"m having a few problems after upgrading to 8.10. I'm hoping for any help as i'm getting very desperate with these problems.

Problems:

#1. In order to update to 8.10, i had to modify something in "Software Sources" window (so it checks more sources for updates i guess). My 8.10 update hanged at the final stage, and didn't finish installing. After i restarted, the "Update Manager" now offers me to install 600+ available updates.
           - I can't access 'Software Sources' menu anymore, whenever i click on the button, i enter the password, then nothing happens.
           - I tried downloading all offered updates, but after installing about 300 of them, it asked me to restart, and displayed this error message: 
"Can not upgrade An upgrade from 'intrepid' to 'hardy' is not supported with this tool."

Any way to set it back to normal?

#2. I tried this command: sudo apt-get -f install to fix things, but it made it worse - i'm now missing the cross that's used to close windows (maximize,minimize,cross toolbar). So now i have to go File,Close to close windows...

#3. I tried installing MySQL using: sudo apt-get install mysql-server , but it doesn't install it and displays this error message:
"kap1@Linpc:~$ sudo apt-get install mysql-server
[sudo] password for kap1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxi6: Breaks: gnome-settings-daemon (<= 2.24.0-0ubuntu1) but 2.22.1-0ubuntu2 is to be installed
E: Broken packages"



Would it be reasonably possible to fix these, or should i just do a clean re-install of 8.10? I kinda have a lot of stuff installed ... so it would take like the whole day. :(

Thank You!

---

### Post by kaptain1 on 2008-11-20
bump :(

---

### Post by kaptain1 on 2008-11-21
Are these problems THAT complicated? How come nobody is willing to help a Linux newbie? I love Ubuntu, but if somebody would suggest a thing or two, i would be very grateful!

Thanks.

---

### Post by adamant715 on 2008-11-21
If nobody posted in this topic they're probably just as clueless as you . Stop bumping it.

---

### Post by kaptain1 on 2008-11-22
Thanks you for your reply.

Any other ideas?

Thanks.

---

### Post by trendyabinash on 2008-11-22
This is a hell of problem.
I don't know what should be done.

---

