---
title: "Upgraded 12.3 to 12.10, now only get underscore."
date: 2014-01-28
forum: Installation &amp; Upgrades
---

### Post by mrjacque on 2014-01-28
Have an HP Pavillion with an Intel video chip and have been running Ubuntu 12.3 for a while. Decided to upgrade finally to 12.10 towards 13.10.
The update was without errors. 
Rebooted. Past GRUB. Get the Ubuntu splash screen. Then the screen goes blank with only an underscore or cursor (not blinking). 
I have tried to get a terminal with CTL ALT F1 and nothing comes up. 
Also saw suggestion of ALT F7.
Have gone on to 12.3 recovery mode and done sudo apt-get update and upgrade. They seemed to do something but reboot results in only the cursor. 
How do I get back top my desktop?
Thanks

---

### Post by claracc on 2014-01-29
Perhaps is the NOMODESET problem for your graphics card?, please see [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) ,the tutorial will address you to  try the workarounds about nomodeset.

---

### Post by Bucky Ball on 2014-01-29
You chose the path of MOST resistance. Going 12.04>12.10>13.04>13.10 is extremely problematic, not least because 13.04 is no longer supported. A clean install, and only then if you had a good reason, of 13.10 was your best option. 12.04 LTS is a long-term release, and as such, can be upgraded directly to the next LTS release in April, leapfrogging the interim releases. LTS has five years support.

PS: There is no 12.3.

---

### Post by claracc on 2014-01-29
```
That was a bad move as 12.10 is no longer supported. You will now probably need a clean install of either 12.04 LTS (most stable) or 13.10, both directly upgradeable to 14.04 LTS when it is released in April
```

But, as ubuntu wiki says: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) , attached image, ubuntu is still supported and won't reach its eol support till april 2014, so there are  two or a little more months to get security updates for it, isn't it?

---

### Post by Bucky Ball on 2014-01-29
Yep, that was my mistake and I've already edited my post accordingly. 13.04, of course, is not supported, though, so upgrading through the interims becomes an issue there I would think. One can only try.

---

### Post by mrjacque on 2014-01-29
Tried the nomodeset in GRUB and after the splash screen, came up with a command line. I told it to run Firefox and it says no display specified.

---

### Post by Bucky Ball on 2014-01-29
You got to a command line? Get back to it and try:

sudo service lightdm start

---

### Post by mrjacque on 2014-01-30
I went in and ran do-release-upgrade and now cannot even get to the prompt using nomodeset. Keeps telling me that a drive is not accessable.

---

### Post by mrjacque on 2014-01-30
New info - tried the nomodeset again and get the prompt. When I run "sudo service lightdm start" get the error "Job failed to start".

---

### Post by Bucky Ball on 2014-01-30
You are using a regular Ubuntu with its regular Unity desktop environment? You haven't deleted it or are using something else? Did you also try the 'startx'?

If you are online with a cable or your wireless is working, at that terminal, can you update? 'sudo apt-get update'?

---

### Post by mrjacque on 2014-01-30
I tried to run startx and it says /user/bin/x: not found and failed to start.
Do not have a wireless to this computer. 
I went back and ran the update. Now what?

---

### Post by Bucky Ball on 2014-01-30
You are online with this machine with a cable, then? Please confirm. If not, running updates, and a bunch of other things, is futile.

---

### Post by mrjacque on 2014-01-30
I am on a DSL connection. Have done upgrades. Would like to do a downgrade to get back to something that works. The update even broke the old releases that are in GRUB.

---

### Post by claracc on 2014-01-31
There is not a way to do a downgrade (once upgrading to 12.10) to 12.04, except installing again 12.04. As you can enter in your system (at least at command line) with nomodestet setting you could backup your /home folder and cleanly install 12.04 or 13.10, as BuckyBall's post number 3 suggests is the straightwordward way. 

In order to do backup there is a very good guide here: [http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup).

However, you can wait for more expertize advice, since perhaps someone with more knowledge can adress you in order to fix the problem of your graphics card and driver with ubuntu 12.10 release. But certainly, it seems the harder way.

---

### Post by Bucky Ball on 2014-01-31
> **claracc said:**
> There is not a way to do a downgrade (once upgrading to 12.10) to 12.04, except installing again 12.04. 

That's your option for a downgrade. Back up first, as advised.

---

