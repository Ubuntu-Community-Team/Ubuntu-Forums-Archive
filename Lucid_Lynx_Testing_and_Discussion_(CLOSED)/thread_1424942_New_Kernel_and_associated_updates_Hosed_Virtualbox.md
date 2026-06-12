---
title: "New Kernel and associated updates Hosed Virtualbox Guest Additions"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by grubdude on 2010-03-08
Hi,
 
I have been running 10.04 for a while here with relatively few problems. Today's kernel update to -16, disabled my guest additions and screen resolution.
 
I tried re-installing and that created a kernel panic upon reboot to reset guest additions. The entire install looks like it is now kind of trashed.
 
I am doing a re-install in another vm of todays build without updating the kernel (assuming) the new kernel is in that build and see if it works okay. I will save the original machine to look over.
 
Anyone else have this type of problem?

---

### Post by DoeRayMe on 2010-03-08
I tried to use the -16 one, but made my system so bloody slow, took 5 seconds for the menu to open and then close :S

Dont know whats happened with this update...

---

### Post by grubdude on 2010-03-08
Well at least it is not just me :-). I am downloading today's build. If it has the new kernel and works like -15 did after duplicating my original install, I will report back.
 
I am surprised that no one else is complaining yet....

---

### Post by grubdude on 2010-03-08
Update: I just did a fresh install and upgraded everything including -16 kernel. All was working fine until I installed Virtualbox Guest additions to fix screen resolution.
 
After this install again got hosed and stuck on low resolution. So, Guest Additions works with -15 but they missed something with -16.
 
I am pretty much hosed here until that unless I don't mind a really small display....Darn..

---

### Post by pricetech on 2010-03-08
I have a related issue every time the kernel is updated in previous versions.  I"m using VirtualBox OSE and it just stops working when the new kernel installs.  I edit my menu.lst to go back to the earlier kernel until VBox is updated, then move to the later kernel.

Sounds like that may be similar to your issue.  Hope that's some help anyway.

---

### Post by grubdude on 2010-03-08
Thanks I will keep that in mind. I have a new install up and running. The display is filling about 3/4 of the screen now which is better but it is acting like Guest Additions is not even installed. For example seamless mode is greyed out now.

I will probably just use it like this for now until a fix comes out. How long did you typically have to wait for that?

---

### Post by pricetech on 2010-03-08
I want to say a few weeks, but don't hold me to that.

---

### Post by grubdude on 2010-03-08
So, if I leave things the way they are and just continue to boot into -16 kernel, at some point this should be corrected without my involvement or tweaking?

---

### Post by grubdude on 2010-03-09
Does anyone have any updated info on this? I have a fresh install of 10.04 but I know if I do the updates for the -16 kernel it will hose my display and cause kernel panic.

How does one know when this will be fixed? Works fine under -15 kernel.  Thanks.

My list of updates is growing. I have not updated anything since yesterday because the new kernel hoses my install. I would really like to update but how will I know if there is an update that fixes the X problem with Guest Additions?

---

### Post by grubdude on 2010-03-09
Am I the only one having this problem? :-)

---

### Post by stink on 2010-03-10
You're not alone - I'm having the same issue.  I found it when installing lucid today and yesterday from a daily livecd iso in virtualbox on a windows host.  My guess is that you can just hang out with the low res graphics for now and it will be fixed eventually, but I couldn't even guess when.  I'm probably going to go dig for a -15 kernel .deb and install that locally, while planning to go back to the kernel in the repo later (maybe in a couple of weeks).

---

### Post by stink on 2010-03-10
@grubdude: According to

[http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html](http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html)

you can install the mainline 2.6.32.8 kernel and get something that's like the 2.6.32-14 package.  I installed linux-image-2.6.32-02063208-generic_2.6.32-02063208_i386.deb from

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.8/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.8/)

and the video magic in virtualbox works now.  Note that this may reintroduce old otherwise-fixed kernel bugs, but I'll going to use it for now.  You will probably need to edit your xorg.conf to make mouse integration work (and to make a pointer appear at all) as shown here:

[http://forums.virtualbox.org/viewtopic.php?f=3&p=127976](http://forums.virtualbox.org/viewtopic.php?f=3&p=127976)

I used the snippet in the first reply.

Hope this helps.

---

### Post by grubdude on 2010-03-10
Thanks...Actually, I was able to reconfigure the grub to boot back into -15 for now and will see what happens when they release the next kernel update....

---

### Post by PA28 on 2010-03-11
Selecting the -15 kernel worked for me too. Mouse integration and graphics acceleration is still broken though. I tried re-running the VirtualBox Additions script again but it didn't fix anything.

I guess instability is to be expected during the Alpha's. ;)

I'll do a fresh install when Beta 1 lands and see how it goes from there.

---

### Post by grubdude on 2010-03-11
I will probably do the same. I hope they fix this as it seems like -15 was more stable than the current -16. Not sure if the first beta will be much more than a compilation of the last alpha though. Time will tell.... :-)

---

### Post by pricetech on 2010-03-11
May or may not be relevant since I'm running Hardy, but yesterday I got an update for the kernel and for VBox, both the same kernel version, and everything is still working just fine.

The kernel update I already had, but I was running the older kernel.  I guess it thought I needed the new one since I wasn't running it yet.

It seems the headers for Virtual Box are behind the kernel when it comes to updates.  That aspect of it is probably going to be the same no matter what version of Ubuntu, or Linux for that matter, you are running.

---

### Post by grubdude on 2010-03-11
was that a 3.1.4 vb upgrade?

---

### Post by pricetech on 2010-03-11
Help - About says 1.5.6 OSE.

It looks like we're using entirely different version of Virtual Box, but I think the kernel headers thing may be the same issue, or at least similar.

---

### Post by stink on 2010-03-12
> **PA28 said:**
> Selecting the -15 kernel worked for me too. Mouse integration and graphics acceleration is still broken though. I tried re-running the VirtualBox Additions script again but it didn't fix anything.

I guess instability is to be expected during the Alpha's. ;)

I'll do a fresh install when Beta 1 lands and see how it goes from there.
@PA28: You can fix the mouse integration problem with a few lines in xorg.conf.  See the first reply here:

[http://forums.virtualbox.org/viewtopic.php?f=3&p=127976](http://forums.virtualbox.org/viewtopic.php?f=3&p=127976)

---

