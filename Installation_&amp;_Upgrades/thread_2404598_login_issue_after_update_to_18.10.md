---
title: "login issue after update to 18.10"
date: 2018-10-25
forum: Installation &amp; Upgrades
---

### Post by yazdzik-k on 2018-10-25
Dear friends,

I have the oddest login issue ever,  and I am no stranger to login in extreme situations.

Update from 18.04 went smoothly,  but when the default kerne, 4.18l appears,  I get the gdm screen,  but it does not accept password.  If I manually select kernel 4.15,  I can easily login with username and password.

This perplexes me,  as I do not have any workaround in my repertoire.

Please if anyone is an expert,  try to see what is wrong, or at least tell me what logs you need to explore.

Best,

Martin

---

### Post by Frogs Hair on 2018-10-28
I'm not an expert , but I experienced this with a very early upgrade to 18.10. In my case the on-screen keyboard worked to login and I think it was related to the input method packages.
The only viable work-around for me was to go back to 18.04 and  perform a clean installation far latter in the cycle. I have upgraded another computer without issue since then.

---

### Post by ajgreeny on 2018-10-28
I also had this problem in my first attempt to install Lubuntu 18.10 as a VM in VirtualBox.
I assumed this was just a glitch and reinstalled the OS again with slightly lower amount of ram given to the VM and it then worked fine and has done ever since.

However your thread makes me now wonder if this is something to do with the OS itself as I have never seen this before in all the installations of Ubuntu based OSs, including Mint as both full-hardware and virtual installs since I began using Linux exclusively over 13 years ago.

---

### Post by yazdzik-k on 2018-10-29
Thank you both for responding and pointing the way.

I did the following which worked,  as kludgelike as it is,  in case anyone else has the issue.

installed lightdm as manager,  since it is easier to manipulate if something goes awary
logged in on the earlier kernel
purged every bit of the 4.18 kernel
rebooted(belts and braces,  I am neurotic)
logged in on older kernel
installed 4.18 packages 
rebooted  and logged in on the 4.18 kernel,  as thought nothing were wrong.

I also experienced a "race" issue between timidity and something else,  which I did not bother to check,  since I do not need timidity,  which killed sound.  I am not sure the two are related,  but it appears as if loading order has changed somewhat,  and if there were also a "race" between a kernel module required to use GDM,  similar to the sound issue,  this would explain it.    

Clean installs are always better,  and,  I admit,  since 15.10 until now,  I never had a single issue,  so I saved a lot of time,  as my system is highly personalised.  I promised myself never to do this again,  but the seduction of ubuntu simplicity on this box mesmerises me.  It would take a day to get debian up and running,  whereas this and the sound were simply a few posts.  At any rate,   I spent ten minutes as opposed to two hours.   I suspect however,  this is the last time this will work,  as settings,  ibus, dconf,  and so on are as confused as lovesick gelding. 

Thank you both,  and thanks to all,'
M

---

