---
title: "Evolution gone!"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by EricLorenz on 2010-10-16
Hi-

Just upgraded last night to 10.10, and for the most part everything seems to have gone fine, except...afterwards, I went back into update manager to check for any updates, and it said that a partial upgrade was needed, that it could not update all packages? I let it do it...during the upgrade, the system indicated it wanted to remove evolution (which I use). I figured OK, maybe it's putting a new version in, so I let it go. Well, it removed it allright, and did not put it back. When I went to the software center to try and re-install it, it wouldn't...I got this error message-

"Package dependanceis could not be resolved-" (it would not let me copy and paste the message).

I opened evolution once before I ran update manager again and it ran fine (or seemed to). 1. Why did it take evolution out? 2. How can I reinstall/fix this? Evolution WAS included with 10.10 right?

Thanks,
Eric

---

### Post by lemming465 on 2010-10-17
> 1. Why did it take evolution out? 
Because it was confused, probably by a repository that was only partially synchronized with new updates.  That's why you got a partial upgrade warning; as you have discovered, it can be dangerous to allow them.

> 2. How can I reinstall/fix this?
The first thing I'd try is ```
sudo aptitude clean
sudo aptitude update
sudo aptitude full-upgrade
```
If that doesn't do it, next```
sudo apt-get install --fix-broken
```
If that still doesn't do it, change to a different repository (drop down in software sources from synaptic), reload the repositories, and then try```
sudo apt-get install ubuntu-desktop --reinstall
```
If that still doesn't do it, write back for yet more options.

> Evolution WAS included with 10.10 right?
Yes.

---

### Post by EricLorenz on 2010-10-17
Thanks for the help...I will try your suggestions.

If it will help...now when I try to install Evolution from Synaptic, I get this...

Does this confirm what you are saying...?

Thanks,
Eric

---

### Post by EricLorenz on 2010-10-17
Tried all of them, and am still getting the same error box as what I uploaded previously. At the end of each of the first 2 steps, the info I get back at the prompt seems to indicate that no packages are changed, installed or uploaded (in other words, doesn't do anything). I did have some 'outside' repository sources setup in Sources, but I have since taken them all out, so I think what is there is simply what Ubuntu sets up by default.

Thanks again,
eric

---

### Post by GoldNugget on 2010-10-21
Your problem sounds similar to one I encountered awhile back. A bad driver install broke apt and left me completely stuck. Perhaps this thread could be helpful:
[http://ubuntuforums.org/showthread.php?t=540460](http://ubuntuforums.org/showthread.php?t=540460) 

Heres the important part. (Thanks to stego_s_aurus for this fix.):
"To manually abort the error so you can have a functioning package manager again (but with a bum package), Edit the /var/lib/dpkg/status file: Look for the entry that is giving you problems (search for the package name), and manually change the status from "install reinstreq half-installed" to "install ok installed". I know that this doesn't fix the problem with the package itself, but it at least gets the package manager out from being between a rock and a hard place."

Good Luck.

---

### Post by EricLorenz on 2010-10-22
So, if I do this...should that allow me to re-install Evolution? Or do I need to remove the entry for Evolution completely? Sorry, I am new at this...just getting my hands dirty on the internal workings of Ubuntu/Linux. I think I need to make a backup of my /home directory before going any further... :-)

Eric

---

### Post by EricLorenz on 2010-10-30
GoldNugget-

Tried your suggestion, but could not find the evolution package referenced...probably because right now, it is not installed.

Thanks for trying and the suggestion...appreciate it!

This is getting frustrating...I will re-post what I get when I try to install and see if maybe a fresh pair of eyes will see it and be able to offer a suggestion.

---

### Post by EricLorenz on 2010-10-30
Hi-

Again, my issue is this...started an 'alterative CD' upgrade from 10.04 to 10.10- apparently it ended up not installing fully, but seemed to complete OK. Nexst time I ran upgrade manager...it asked if I wanted to do a partial upgrade- and I said yes. It then proceeded to uininstall evolution (among other things). Now when I try to re-install it, I get the following error message (see attached screenshot). I am not sure exactly what it is telling me. I have deleted all 3rd party or other respositories that I thought might be causing this, but no joy. Do I need to go back to an earlier version of evolution? Current version in Synaptic is 2.30, I had 2.28 before.

ANY help appreciated...I do have my email installed in Google Apps, but liked accessing it and my calendar via Evolution. I am not ready to give up...yet, but if I cannot figure this out soon, I'll have to go back to Thunderbird/Lightning, which I'm not crazy about.

Thanks!
Eric

---

