---
title: "Resolution too high"
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by HubertFarnsworth on 2005-08-10
Hi everyone!

I've tried understanding this problem for hours now and I'm just getting nowhere.

I've installed kubuntu on my dell 500m and it seemed to work fine. But the resolution of 1280x1024 is too high because I only have a 14-inch-monitor. So I tried to reduce the resolution in the kde controlcenter. But its the only option I got. There's just no other to pick.
Searching the internet has brought me to the /etc/X11/xorg.conf file. But in that file the only resolution for any colordepth is 1400x1050.
I read a lot about the driver (i810) and many people had the opposite problem: They only can pick 800x600 or less. 
How is it possible that kde says it has a resolution of 1280x1024 if theres no such entry in the xorg.conf? What am I doing wrong?
And the most interesting question for me: Can anyone help me to reduce my resolution?

Thanks in advance.

---

### Post by bh4887 on 2005-08-10
Hey,
I, unfortunately, have a similar problem so I thought I'd jump in with this thread.  My screen is 1280x800 and the only option there is under Screen Resolution is 1024x768  0Hz... As a result my picture is coming out poorly, and I haven't seen any ways to get the required resolution settings to match my screen.  Thanks for the help.

---

### Post by indispus on 2005-08-10
[QUOTE=bh4887]Hey,
I, unfortunately, have a similar problem so I thought I'd jump in with this thread.  My screen is 1280x800 and the only option there is under Screen Resolution is 1024x768  0Hz... As a result my picture is coming out poorly, and I haven't seen any ways to get the required resolution settings to match my screen.  Thanks for the help.[/QUOTE]
Try this:

dpkg-reconfigure xserver-xorg

---

### Post by HubertFarnsworth on 2005-08-10
I don't know why, but when I was looking for this thread (and not earlier...) I found this thread:

[http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)

What I did is download the 855resolution-thing and the changes described there. That didn't change anything.
Then I tried the command 
dpkg-reconfigure xserver-xorg
resluting in a error message telling me that package was not installed. Then I just added the refreshrates like described in the thread above. And now it works!

---

### Post by mrtrick on 2005-10-25
I'm having the same problem of only being able to display 1024X768 showing 0Hz. I'm running an ATI Radeon Mobility in a Dell laptop. Any ideas?

---

