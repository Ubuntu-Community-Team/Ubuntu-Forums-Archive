---
title: "Superior Linux Guru Needed Re: Sharing Home Directory Across Multiple Linux Flavours."
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by 42dorian on 2010-03-25
Okay.  I'm rather familiar with Linux at this point, I'm quite proficient in fact.  But a question has come up in my mind and I don't have an answer.

Can multiple Linux flavours share a Home directory?  Say, Xubuntu, eLive, and Fedora?

From what I know, it should be easy, as long as all the OSes can read the format of the partition it should work.  Even if you have to create a separate profile for each OS.

Why do this?  To try multiple OSes, 'cause I'm like that.  I want to put my single Home directory on a big hard drive I've got, then partition a second, slightly smaller hard drive, so that it can serve as the root directories for other OSes.  My Primary right now is Xubuntu, and I've got eLive and Fedora installed on the other hard drive right now.  But I've got separate home partitions for each of them.

Can I use a single /Home directory for all of these OSes?

---

### Post by unkilbeeg on 2010-03-25
Sure.  Each OS will have its own root directory, with its own /etc/fstab.  Just make sure that the /home partition in each OS points to the same device.  You'll probably want to do the same with the swap partition, no reason they can't share that too.  There is some potential for desktop breakage if the different versions of the desktop software don't agree on how config files should be written.  You'll also want to make sure that the UID and GUID for your user[s] match across OSes, or you'll have permission problems.

I did this a long time ago -- I think I had 6 or 7 flavors of Linux on one machine.  That was before GRUB came along, I did it all with LILO.

Keep in mind that each OS will be able to see all the others, with potential for some real read/write ugliness if you're not careful.

---

### Post by d3v1150m471c on 2010-03-25
**Yes, with** **a lot of work.** You have to take into consideration that several configuration files go into a home directory. Things like window managers, menu configurations, profiles, trash, local, ect ect. A lot of these things are specific to the parent that uses them that will vary from distro to distro and from app to app. Not to mention different distros use different package systems, which may or may not have an effect but something to take into consideration. If you're just wanting to try distros then **virtualbox or vmware** is a promising alternative for said reasons. You can also access the partitions from one distro to another btw.

---

### Post by andrewthomas on 2010-03-25
> **d3v1150m471c said:**
> **Yes, with** **a lot of work.** 
 +1 maybe share a data partition, but too many complications for a home

---

### Post by 42dorian on 2010-03-26
Thank you all!  This makes my next Xubuntu install a far more intricate and interesting one.  So, as long as I specify the same partition for Home across all of them, it should work.

Excellent.

---

### Post by Fafler on 2010-03-26
I have to ask. This fascination with rebooting, what that's about? If you are a software tester and need the different distributions for testing, wouldn't virtualbox be a better choice? Otherwise it just seems pointless, or at least to me it does.

---

### Post by 42dorian on 2010-03-26
It's not about the rebooting, and it's more about bandwidth usage.  These virtual appliances take up space on their own, plus have to be downloaded.  When I compare a 1-4GB virtual appliance with a 700MB install CD, the bandwidth choice is clear.  I can get 3 or 4 flavours of Linux in the same bandwidth space it would take to download a single virtual appliance.

Add to that the hardware I'm using isn't very new, and having an entire OS run on it's own saves resources.  I'm not a software tester, I just like Linux.  It's incredibly economical to use a single flavour of Linux most of the time, and switch between them by rebooting when you have a curiosity or you want to do something that another flavour is set up better to do.

I currently have Xubuntu 9.10 as my main OS, eLive 1.0 on another partition with it's own Home directory, and Fedora 12 and IT'S own Home directory.  eLive does enlightenment and graphics a little better than Xubuntu, just the way I have it set up, and Fedora is set up as a test for certain communications programs I use, just in case they aren't working just right in Xubuntu or something.

I'm not the average Linux user, I'm rather strange.  There may be easier ways to do things, but I'm just out to play with it.  This is more fun for me than games or sports.  But I do completely get where you're coming from with virtualization.  If it wasn't for my bandwidth cap, I'd jump on it.

---

### Post by lien_meat on 2010-03-26
I've done exactly what you are talking about on multiple occasions.  Different configs for the same DE are gonna conflict and over write each other though...so, be careful there.  Perhaps you could symlink the necessary config files at boot time (via a startup script or something), and store them in a specific directory for each distro... if you do it right, that will work...but it might be hard to find everything that is specific to each distro.

---

### Post by 42dorian on 2010-03-27
Yep,  I get you.  Though I'm kinda clueless on all of those options.  But, that's the fun of it for me.  See a challenge, learn how to deal with it, know how to back yourself out and fix it.

I'm kinda like a junkie.  A challenge is just a fix for the cerebellum.

In all likelihood I'll create separate users for each distro, to resolve the issues.  All I care is that my home settings are able to be preserved through upgrades and reinstalls.  I don't care about having the exact same files available to all distros.  That's easy.  Toying with multiple OSes, keeping your settings in case it buggers up, not abusing my bandwidth/making it economical, and having fun with it... that's my goal.

I still thank you all for giving me the info and the hints.  As of the next edition of Xubuntu release, I'm going all new format.  So thank you!

---

