---
title: "2 Kernel Panics withing 45 mins.~ What is going on here? Help?"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by Rasa1111 on 2011-10-14
Hey all...
Ive never had a single "kernel panic" in my 2 years using Linux/Ubuntu..
So Im really lost here. 

So, I've been running 11.10 since beta 2 was released..
and had no problems with it. 
It ran great for the 3-4 weeks i used it. 

So today, I do a fresh install of 11.10, and wiped my whole HDD and all 3 partitions for it. 

I had JUST gotten all my programs installed, settings how I wanted.. 
and everything as it should be... (except my ACYL icons), lol
 icons), lol

Then i logged in to gnome shell and got my settings all set up in there. 

I was simply installing a new GTK3/Gnome shell theme..
When suddenly my top panel, and all my window borders vanished. 
I could open nothing, could move no open windows.. Nothing. 

The top panel only had a global menu items in the left corner.

So I tried to open a terminal, 
and my screen went black..
gave me a whole long list of text...
Then at the bottom it said... 
**"Panic in Kernel, Now reverting back to text mode"**
(something like that)

It just stayed there and did nothing...
So I rebooted it... 
and tried logging back into both Unity, and gnome...
and I got the same blank top panel on top and nothing else. 

SO....
I figured "meh! I'll just reinstall it" because I was sure I couldnt fix it.. 

So I just got the reinstall done... icons), lol

and I went to "safely remove" an external hard drive..
and BAM, right back to the black screen .. "kernel panic, etc etc".. Same as above. 

Why could this be happening?
How do I remedy this? 

It's been running fine again since rebooting after that 2nd "panic"... (about 10-15 minutes)
So I came right here to try and figure this out before I go absolutely insane. 

 Do i have a bad ISO?
Did I screw something up for good?

Im truly clueless here. 

Im kind of fearing it's going to do it to me again any minute now.
Not a good feeling! :confused:

Someone please help? 
I'd be forever grateful. 

Thanks for looking. 
sigghh

---

### Post by mtron on 2011-10-14
did you examine the kernel logfile /var/log/kern.log or even better can you provide / examine the crash dump (automatically created when a kernel crash occours) /var/crash/linux-image*.crash

---

### Post by Rasa1111 on 2011-10-14
Hey mtron, thanks for stopping in. 

I can see/share the /var/log/*kern.log file..*but I see nothing in /var/crash/
it's just an empty folder. 

but my kern.log is here. If anyone wants to take a look..
[http://ubuntuone.com/2xus648D2eue73DlPSmFv8](http://ubuntuone.com/2xus648D2eue73DlPSmFv8)
(thought it was too long to paste, sorry)

Im not even sure what I should be looking for in here.. :confused:

Lots. To. Learn. Still. lol

Thanks again.

---

### Post by Rasa1111 on 2011-10-14
Also..
more noobness...

Does a kernel panic mean an entire install is bad and can't/shoouldnt be used?
Or is it something that can happen, and once it's "over", 
You still have a good, usable system? 

Does a kernel panic mean it's all a fail? lol

hmm

---

### Post by mtron on 2011-10-14
open /var/crash/ as root . e.g.

```
sudo -s
cd /var/crash
ls
```

kern.log looks ok, so it's most probably not a buggy staging driver that is causing this. This is good news ;)

> Does a kernel panic mean an entire install is bad and can't/shouldn't be used?
no. it's either a buggy driver or bad code in a application

> Or is it something that can happen, and once it's "over",
Kernel panics have a reason that should be identified and fixed. 

> You still have a good, usable system? 
When we find the error and can fix/work around it then yes ;)

---

### Post by mörgæs on 2011-10-14
Slightly off topic, but why did you reinstall if you already had a working 11.10 on your system?

---

### Post by Rasa1111 on 2011-10-14
Because I had 3 partitions, 
and the 11.10 partition only had 10 GB's. 
I wanted 11.10 installed on the entire disk. 
and I dont think im good enough with partitioning to do what it would have taken to give that little install the whole disk. :/

mtron..
Those commands dont pull up anything for me. 
:/just give symbols like ># or something like that. lol
idontknow, Sorry.

Thanks for the info. :) much appreciated. 
maybe ill have more luck when im not sleep deprived.

---

### Post by Rasa1111 on 2011-10-14
forgot to add...
After that first kernel panic,
once i had just gotten everything installed and set up..
No matter if i rebooted, cold booted, logged out...
when the desktop would load, it was only giving me the blank top panel and nothing else. 
thats why Im here at this 2nd, fresh install 
grr

---

### Post by Rasa1111 on 2011-10-14
well this is just flipping sad.

Yet ANOTHER kernel panic.

Seems I cannot disconnect my external drive without having a GD kernel panic. 

I see there was a bug filed on this during the Alpha..
and it's still happening?

I've never been soo irked by ubuntu in my life. 

Using the beta for at least a month...
and not a single problem!

Could install my icons, could use my devices without having kernel panics...
and now Ive installed the "final release" I can't do either. 

I also have an extra "battery icon" in my top panel, thats also irking the hell out of me. 

Really wish I could find my 11.10 beta2 file...
I would install it over this rubbish in a minute. 

GAHH
this is freakin ridiculous.

---

### Post by 23dornot23d on 2011-10-14
Searched for some torrents if you want to go for the Beta .....

[http://www.google.com/search?client=ubuntu&channel=fs&q=11.10+beta+linuxtracker&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=11.10+beta+linuxtracker&ie=utf-8&oe=utf-8)

---

### Post by Rasa1111 on 2011-10-14
thanks man.
Yeah I found a beta2 torrent im downloading now. 

Im soo freakin aggravated right now it's unsettling. 
:/

---

### Post by Rasa1111 on 2011-10-15
Alrighty..

Ive marked this as Solved..
I learned that the kernel panic happens whenever I attempt to right click on an external drive in the Unity 'dock', to "safely remove drive" 

Kernel panic everytime, without fail. 

There have been bugs filed on it since Alpha.

ANyway...
as long as i just right click the drive from within nautilus (or desktop), I can remove it fine, no panic..
but try again with Unity.. PANIC!! lol :rolleyes:

Got my ACYL icons working finally. 
man, took forever.

Anyway, got it all good again, and Im happy.
Thanks for the posts everyone, I appreciate you all. <3

---

### Post by 23dornot23d on 2011-10-15
Good to see you are back in business Rasa1111 .... no idea why they have not fixed the Safely remove USB ....... where is the link to the Bug Report .....

I will add it on my page of Failed Upgrades as it seems quite important that this is fixed ...

---

### Post by Rasa1111 on 2011-10-15
Thanks my friend. :)

Ok...

Now Im looking closer..
i see therre are a few of them (bugs filed)..
and apparently there is a "fix" in this one, #20.. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/844957](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/844957)

Just found it though, so havent tried anything..
Here are some others..
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872706)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/874530](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/874530)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/874710](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/874710)

Thanks again man. :)

---

### Post by Rasa1111 on 2011-10-15
p.s.. I have no idea what post #20 is talking about, 
or even how to implement the "fix"... lol
:rolleyes:

---

### Post by 23dornot23d on 2011-10-15
Ok cheers will have a look through and see if I can work out why if its been fixed  - you
are still being affected by it ....

Thank you .... :)

---

### Post by Rasa1111 on 2011-10-15
You got it. :)

Im trying to figure out what to do with this?
Am I just supposed to install this .deb, or what?
>                  I've posted both an amd64 and i386 test kernel to the following location.  Please test and let me know your results.  Thanks.
 [http://people.canonical.com/~ogasawara/lp844957/]("http://people.canonical.com/%7Eogasawara/lp844957/")

        


and someone says right after it..
> With the test kernel  (i386),  have tested with a WD external, ntfs, the drive has no power switch
Did 6 connects & safely removes - all went well, no panic
Also tried a seagate that has it's own power switch, the same, no panics.

So How do I do that? lol

I see there's some kind of .deb, with a kernel..[http://people.canonical.com/~ogasawara/lp844957/i386/](http://people.canonical.com/~ogasawara/lp844957/i386/)
but unsure what to do..
:???:

 Thanks man. :)

---

