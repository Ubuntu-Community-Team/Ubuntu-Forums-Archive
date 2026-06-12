---
title: "updated - now won't boot"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by LinuxQuint on 2012-01-21
I can't boot now after an update.  I'm getting this:

> error: cannot read the linux header
error: you need to load the kernel first

Press any key to continue...
After than it says

> Failed to boot both default and fallback entriesthen it goes to grub and I pick 'previous linux versions' and I can boot into -14

It's a P-III, 1133Ghz, 512RAM, Dell Laptop 
I have: 

3.0.0-14
3.0.0-13
3.0.0-12

It's been running Lubuntu fine for about six months now.  Last night I did the updates and it won't boot.

I scanned the RAM and the hard drive and they are fine.  Then I tried the 'previous version" which is 3.0.0-14 and it works fine.  I went into 
/etc/default/grub and changed the video to 640x480 and did 'sudo update-grub' and that worked so I know that's working. 

So, it seems to me that either:[INDENT]3.0.0-15 doesn't run on a P-III, or

3.0.0-15 got corrupt somehow
[/INDENT]How can I uninstall -15 and re-install it, ... or ... where would I need to look to see if -15 stopped supporting P-III's , ... or, can I back out the update somehow?

thanks

---

### Post by carl4926 on 2012-01-21
If you can boot 14
You should be able mark 15 for re-installation in synaptic
You should install synaptic if you haven't already!

---

### Post by LinuxQuint on 2012-01-21
what do I search for to find it?

headers
header
kernel
3.0.0-15
linux

...

I'm not really sure what it's called and what all the parts are, though I guess the package manager should get all the parts if I select the main cahuna.  

By "Synaptic" you mean the "Synaptic Package Manager"?  ... Yeah, but that came OOB IIRC.  I don't think I installed it.

---

### Post by LinuxQuint on 2012-01-21
I searched for "3.0.0-15" and found three that are checked.  Are these three enough?

linux-headers-3.0.0-15
linux-headers-3.0.0-15-generic
linux-image-3.0.0-15-generic

---

### Post by carl4926 on 2012-01-21
I still have 14
Let me check the updates

---

### Post by carl4926 on 2012-01-21
Are you working outside the defaults?
How were you updating?

---

### Post by LinuxQuint on 2012-01-21
Nothing special.  I'm pretty sure my home folder is encrypted if that matters.  The update was the simple update manager pop-up that happens every week or so.  

So, with Synaptic, I searched for 'linux-image' and removed (not completely) the entry.  
And did the same with '3.0.0-15'  

I rebooted and it worked fine (in 14).

I re-installed the 'linux-image' for 15

and rebooted -- no workie, some error about collectd.  No grub menu. Dead in the water.  (Is there some key like Windows F8 for 'safe boot'?) So I booted with live CD, edited

>  /boot/grub/grub.cfgand changed the three '-15's in the top entry to '-14' and I could boot in 14 again (yay) 

I went back in synaptic and searched for 3.0.0-15 to get the headers again, and couldn't remember if it was <blank> or 'generic' I needed, so I installed them both.

I checked 

>  /boot/grub/grub.cfg and I was still set at 14 (surprizingly), so I ran 'update-grub' and checked again and it was correctly at 15

rebooted, "checking disk for errors .............................................." then booted okay
system profiler says OS is -15. (yay)

rebooted again, no disk check, but I notice error about Plymouth, but it still boots okay.

> could not write bytes: Broken pipe
Already started
Starting atop system monitor: mountall: Plymouth command failed
moutall: Disconnected from Plymouth
atop.
checking for running unattended-upgrades
so bottom line: my PC is up and running again with 15, but I'm slightly concerned about this: 

[LIST]
[*]Broken pipe
[*]Plymouth
[*]atop
[/LIST]
Any thoughts on what's wrong here?  Does 15 have a bug?  Could it be my hardware?  Or did I forget something in the update/remove/reinstall?

And is there some Linux safe boot key, like Windows F8?

---

### Post by rpaco on 2012-04-07
I had this same problem on my Dell D600  Latitude laptop. Both on the 17 to 18 update and on the latest which came up this afternoon  07/04/12 mid afternoon BST.

On both occasions I had to re load the generic-pae version this time with  3.0.0-19 twice! I gather the -pae version is for 32 bit machines like mine. But it seems to need some of the other bits as well, since it would not work with only the -pae header and kernel installed.

I am using Oneric 10.11 and Gnome 3.2.1 since I cannot use Unity with the dell provided display. (It is ok on my Samsung N110 netbook though) I believe that Pangolin has been written for 64 bit machines only since I cannot get any version to work.

I would have thought a few warnings on the updates would be in order for us poor people with older machines.

---

