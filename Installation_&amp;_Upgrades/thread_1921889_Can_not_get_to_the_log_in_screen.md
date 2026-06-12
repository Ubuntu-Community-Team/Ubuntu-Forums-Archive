---
title: "Can not get to the log in screen"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by lohith on 2012-02-07
Dear Ubuntu geeks,
I installed the latest kernel update(3.0.0-12-generic I think it appeared last week or so) and restarted my system only to find that whenever I move my mouse, the system logs me off. I thought it might be a problem with the graphics card so, purged and reinstalled the nvidia-current package. Did not work. I removed compiz and nvidia again and reinstalled them and that too did not work. I also reinstalled Unity and Unity2d and it was not better. 
I remember I changed the xorg.conf file to change the drivers from "nouveau" to "nvidia" and restarted. That did not work so, I allowed the system to recreate its own xorg.conf file. I have dual monitors and I see them in the xorg.conf with drivers as "nvidia". 

I tried different options in the kernel line while rebooting and none of them gave back the screen. I see that the system loads the nvidia drivers (I see the greenish logo at the start) and it gets stuck at the screen that gives dots (progress of start) and says Ubuntu 11.10. When I fall back to terminal with Ctl+Alt+F1, I see "mountall disconnected from Plymouth [ok]" and then the terminal.
With some other kernel options I see the following:
with quiet splash removed, "loading fallback graphics devices [fail] and Starting K display manager [fail] 
With nomodeset in addition to quiet splash removed, "touch:cannot touch /var/lock/subsys/nxserver': no such file or directory" and the cursor keeps blinking forever after this.

I tried Ubuntu live CD and I can't go to the screen that says try or install Ubuntu. The system shows a pink screen with a logo at the bottom and falls back to blank screen.

I can SSH, map folders as I used to do before and all other stuff from a terminal but I am not getting back the Unity environment or the log in screen. Have been struggling with this since Friday looking up some solutions from the community and doing as suggested but none of them really worked.

Any help to bring my system back is highly appreciated. I can post back with any more information if required.

Thank you very much!

---

### Post by lohith on 2012-02-08
I got the system back by upgrading the 11.10 to 12.04 alpha 2 version. The upgrade was not completed and returned an error after installing and upgrading various packages including the nvidia, xorg, xserver and the other graphics related libraries. This must have fixed it. And the good thing is, I was greeted with 11.10 logo instead of 12.04 which I think means I am currently running the stable version! Everything went well and all the services are working except virtual box but I can reinstall when I need it again. I hope the struggle is over :)

---

### Post by lohith on 2012-02-08
I checked the system's current version of OS and am surprised to see it is 12.04 alpha version and is stable!!
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"

Ubuntu rocks :D

---

### Post by bajaking on 2012-02-08
Wow, congratulations!  Except you suffered a week of downtime and the stress shortened your life by at least one year.  So I do not second your assertion that "Ubuntu Rocks!".  
May I suggest "Linux is a pain in the ***, but at least Ubuntu is the 3rd least painful (after Centos and OpenSuse)".

---

### Post by lohith on 2012-02-08
Your suggestion is well taken ADAM. There are always down times when one uses an open source platform but never to forget, it also saves a lot more time with the wonderful things it can do! I might have taken a look at Centos or OpenSuse if I was building a server but only after trying Ubuntu server! People have different tastes and I like Ubuntu! Now, get your car working and see you tomorrow Mr.bajaking :)

---

### Post by jerrrys on 2012-02-08
I wonder if "gdm" would of played nice with that kernel.  No matter, just a thought.

---

