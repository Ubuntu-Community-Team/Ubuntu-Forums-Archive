---
title: "trouble installin 16.04 trying to preseve the /home partition"
date: 2017-12-14
forum: Installation &amp; Upgrades
---

### Post by knott9 on 2017-12-14
Dear Forum:  I am trying to install Lubuntu 16.04 on a PC 
with an existing ubuntu 9.0 system.
My user 1000 (admin user) is knott.  

There are 4 partitions:  [/boot = sda1 ext2 3gb] 
[swap = sda2 4gb] [/ = sda3 ext3 50gb] and [/home = sda5 ext3 103gb]

I want to preserve /home and overwrite /boot and /.

I booted the install +live dvd and selected "something else".
I specified that the partitioning "tool" 
mount /boot on sda1 and reformat as ext2,
mount swap on sda2 
mount / on sda3 and reformat as ext4,  (!)
mount /home on sda5 and do not reformat. 
I changed none of the partition sizes.

 
When asked, I gave my user name knnew with a password.
[user knnew should have the user number 1000.]
(later I will move all my /home/knott files to /home/knmew.
and change the user name knnew to knott, and 
finally discard the directory /home/knott, and 
change the directory name /home/knnew to /home/knott.

(1) Is this a suitable way to do this "update"?
(I think there should be a better way - an option 
in install to say use an existing user as the admin user.)

(By the way, how do I change my user name from knnew to knott?)

[I have another admin user # 1001 named csi  how can I 
get that user "alive" and log-in-able?]


(2) when the install process moved on, it displayed 
a screen saying "formatting /boot as ext2 in partition 1".
The progress bar is just short of half way and it
is "hung" - nothing is changing.


Help!  What should I do?  (What I did 
was click on "skip".  This put up a black 
mini-frame with some lines like 
/usr/lib/ubiquity - blah blah source id not found 
 when attempting to remove blah blah

I typed ^C, but nothing happened.  

I then clicked on the 'X' to kill the window, 
and a window poppe-up saying 'do you really want 
to quit?'   [Well, no - I really want to 
have the installation work.] - I clicked on "cancel"  (not "quit").

A suggestion: no screen should be unresponsive - something 
more than a spinning wheel  (like occasional text lines saying 
what's happening) should be continually appearing so that 
a hung screen is really cause for panic.

So I'm going home.  Tomorrow I expect to see 
the PC in the same state.   Then I'll pull the power
cord, and I expect to have a damaged unbootable 
machine!!!

So what should I do then?

Thanks

---

### Post by DuckHook on 2017-12-15
First and foremost: ***backup your data.*** A complete reinstall is only a minor inconvenience when your data is safe. Read the link in my sig: **!!BACKUP FIRST!!**

Secondly:> A suggestion: no screen should be unresponsive - something
more than a spinning wheel (like occasional text lines saying
what's happening) should be continually appearing so that
a hung screen is really cause for panic.This is a volunteer forum comprised entirely of Ubuntu users such as yourself. The developers rarely if ever visit here. If you have suggestions or want to influence development of Ubuntu, [this page]("https://wiki.ubuntu.com/UbuntuDevelopers") points you to the various ways you can do so. You should note that unless you've already made or are willing to make some contribution to the community, your comments are unlikely to be given very serious consideration.

Re: your query

You have made the process needlessly complicated. If your old /home is already segregated into its own partition, then all that is necessary is to install the new /boot, swap and / (root) in the old partitions with your old name and password. No need to make up new username and password with the intent of changing it back later. Though possible, it's a difficult and convoluted process that is not even necessary for what you are trying to do.

Subsequent users can be created the same way: by reusing the same username and password.

Your biggest problem, in fact, is attempting to keep your old /home. Many system configurations and settings are actually kept in /home, though many users don't realize this. Since you are jumping from Ubuntu 9.04 to 16.04, then by trying to keep your old /home, you are telling the system to shoehorn an ancient and obsolete 7-year-old group of settings and configs into a system that isn't even running the same Desktop Environment anymore. I can't even remember what DE 9.04 was running. Was it Gnome version 1? It sure wasn't Unity. This is bound to lead to much wailing and gnashing of teeth.

My suggestion would be to not map /home at all. Instead, allow the new /home to simply reside under / in the same partition. Then, mount the old /home into /mnt and *symlink* the old data directories individually to their new locations. That way, you inherit only the pure data and not the obsolete config files and settings. Your new /home will have the right configs/settings to function properly.

If the install process is hanging at the formatting step, then firstly, make sure your install medium is good. Don't skip the media verification and MD5 checksumming that almost everyone ignores. Next, I would use gparted in a LiveUSB/DVD to reformat those partitions beforehand. When installing, don't bother to format.

Remember… if you don't back up your data before trying this, all bets are off. It's simply foolish to upgrade, especially one involving such a giant version leap as yours, without your data backed up.

See if all this helps.

---

### Post by knott9 on 2017-12-15
Dear Duckhook:   Thanks for the reply.

(1) Does the material like "Interpreting Lisp" that I've posted in various places and published 
count as "contributions"?  (google "gary d. knott)  (But, I don't have the time to figure-out how 
to communicate with "developers", so my thoughts will have to remain just that, "thoughts", 
even though some may be worthy of consideration.)

(2) About backing-up, I'm aware of the risk, and I have backed-up crucial files - 
although I'd say it is a cardinal sin to damage non-system non-configuration files during an install 
that are not intended to be so destroyed, and every attempt shoud be made 
in the install procedre to determine the user's intent; for example, 
when the install process offers the option "install 16.04 along-side 9.1"
It should also have the option "install 16.04 replacing 9.01"  (which exactly what
I'm trying to do.)  

(3) About letting /home be "unused", and letting a new /home be created in / with the 
admin user 'knott'; that seems like a promising idea, but then 
I need to eventutally use the "ignored" old home/ and discard the newly created 
/home.   So you suggest mounting the ignored partition (as /thome/ say, to get access
to it. But then what?  I could copy whatever is in the new /home into thome, but 
I then need to delete the new /home dierectory, and somehow get 
the old mounted thome to become home/ within /  (not using links), 
and to make know that the partition holding thome is to be automounted at boot.
I really need step-by-step directions if this method is to succeed.

(By the way, I would expect the install process to create /home/knnew 
in the /home partition(directory) an place whatever config files need to go there.
But I do see possible difficulties here too - such as if any config file for firefox, etc.
is using the user name knnew inside!!)  So If there is a way 
to get my objective of replacing my system files in / and in boot, and 
then getting my config files for emacs, mozilla, etc in /home/knott 
updated or replaced, I be happy to know about it.

[I need to remark that updating Linux seems to be its Achilles heel -- 
if it were't for browsers not working when they fail to be updated (and 
repositories going away to make such updating hard or impossible), I'd 
have no interest in updating.  - As long as emacs, TeX (latex} gcc and Firefox 
keep working, I don't care about updating my kernel or "modules".)

But, alas, I do need to update.  

(3) I have checked my DVD using the option on the install dvd, and it checks ok.
But, the install I "ran" overnight did not come close to working.  9.1 is still there
and I cannot boot it.  Although I can boot a "recovery mode" option, and then 
startx to get the seemilgly original system up which works okay.

So again, any ideas about how to proceed?  I am stuck.

---

### Post by agillator on 2017-12-15
What DuckHook advised is absolutely correct. I will be a bit stronger.   Trying to 'update' across that many versions is an exercise in frustration and futility which you are discovering. At this point I would strongly suggest a brand new installation without disturbing the old one. In other words, create a separate partition as large as necessary (ext4). I would use gparted but that is only personal preference. Be sure to write down the remaining partition numbers (/dev/xxxx/) and what they contain. During the new install, do the 'something else' option and tell it to install to the new partition, mounting it as /. Leave the existing partitions completely alone. Don't even mention them to the installation program. Complete the installation. Reboot, test, make sure everything is working properly.   Then and only then, create mount points for any of the old partitions you need to look at. You will have lost nothing at this point (yet). Reinstall software the new installation doesn't have (to the new installation, of course), reconfigure software it has, etc. based on the old files. Copy any of them if that works (copy the new ones somewhere so you can go back if you need to). But do not just move files and expect them to work. Remember at all points you are doing a fresh install. It will be a bit (a lot?) of work, but it will get you where you want to be without disturbing anything you have now.   In fact, if your current (old) setup is working grub should find it during installation and give you an option to boot into it every time you boot, so it will always be available.   If old partitions have data you want to use (not configuration or program files, but pure data files used by programs) you can always mount those partitions automatically through /etc/fstab, although I would not advise it in your case. As you use your programs that would mean the old data would get changed and therefore be lost. I think you would be better served to simply copy the files to new locations so none of your old files are disturbed. At some point in the future if you wish you can delete the old partitions and reclaim the space if you are satisfied they will never be needed again.  As to users, create them in the new installation as you wish them to be. All that will mean is that when you look at the contents of old files the users and groups may be weird. If that becomes a problem you can change the permissions, users and groups on the old files. If you ever need to you can always changed them back. The only effect will be that if you ever boot back into the old system the users and groups will be screwed up, so you would really be better served to leave them alone.  Now, do remember Murphy is alive and well. I will promise you he will try to rear his ugly head at some point in all this. But don't let that bother you, just deal with him and go on your way.

---

### Post by yancek on 2017-12-15
> [I need to remark that updating Linux seems to be its Achilles heel -- 

No it isn't.  You are trying to update an 8 year old system, there have been so many changes in 8 years I can't image you would have much success with it.  It's not practical to maintain repositories forever because of all the constant changes not to mention the cost of maintaining servers to hold all the software.

No OS is supported forever.  Microsoft dropped support for xp several years ago even though it was the most used OS by home computer users.  They did the same with windows 98 previously.  Also, it wasn't possible when windows 8 came out to upgrade to it from xp or earlier versions.  Expecting a specific OS release to be maintained forever is just not realistic so this certainly isn't anything specific to Linux.  

As has been pointed out above, the /home/user directory contains numerous configuration files for different software and it is extremely unlikely that they will work with a new system which has had massive changes over an 8 year period.  Because of this, many users have a separate data partition instead.

I would expect the process to work well upgrading from release to release or from an LTS to a new LTS.  Not sure why you waited 8 years to do this?

---

### Post by DuckHook on 2017-12-15
> **knott9 said:**
> …even though some may be worthy of considerationMy intent was to inform you that we have no ability to implement your suggestions. I repeat…
> **DuckHook said:**
> …This is a volunteer forum comprised entirely of Ubuntu users such as yourself. The developers rarely if ever visit here.
> **knott9 said:**
> It should also have the option "install 16.04 replacing 9.01"  (which exactly what
I'm trying to do.)  
But you can. I just explained the method you would follow to do so. I will repeat it again in what follows…
> **knott9 said:**
> (3) About letting /home be "unused", and letting a new /home be created in / with the admin user 'knott'; that seems like a promising idea, but then I need to eventutally use the "ignored" old home/ and discard the newly created /home.
Actually, no, you do not. The new /home contains all of the requisite DE settings and configs needed for the new desktop. It is not "discarded". The objective is not to replace the new /home with the old, but rather, to—in a sense—relegate the old /home to a "data" directory.
> **knott9 said:**
> So you suggest mounting the ignored partition (as /thome/ say, to get access to it. But then what?  I could copy whatever is in the new /home into thome,No, not copy. ***Symlink***.
> **knott9 said:**
> but I then need to delete the new /home dierectory, and somehow get the old mounted thome to become home/ within /  (not using links)
Why not? Using symlinks is by far the most versatile and elegant solution. Your insistence on deleting the new and replacing with the old is unnecessary and is what will trip you up.
> **knott9 said:**
> …to make know that the partition holding thome is to be automounted at boot.
/etc/fstab is the file that automounts partitions at boot. Instructions: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
> **knott9 said:**
> I really need step-by-step directions if this method is to succeed.
Instructions are pointless without your understanding and accepting the principle behind this suggestion:

To be blunt: you cannot simply inherit your old /home and expect it to work in your new system. This is an unrealistic and unreasonable expectation. You've left your upgrading for far too long and are now expecting a Model T body to fit on a Tesla chassis. Your only choices are to back up all of your important data, install a brand new system, tweak it to your liking, then copy back only the data back onto the new install, or to use the sort of strategy that I'm proposing, which is (to repeat from my first post) as follows:

When you look at a newly installed pristine /home, it has a bunch of empty directories within it like "Music", "Pictures", "Documents", etc. The idea is to replace these empty directories with symlinks to your old directories in your old /home partition (now thought of as just a data repository). Once the symlink is established, it points to your old data. This gives you the best of both worlds: your new settings and configs remain untouched and therefore relevant to your new OS, and your old data is accessible transparently. It requires learning how to symlink, but that's knowledge that will always reward you well and only has to be done once each time you upgrade. Basic tutorials on symlinking are all over the internet. After minimal practice, the process could not be easier. Here is a typical tutorial: [https://stackoverflow.com/questions/1951742/how-to-symlink-a-file-in-linux](https://stackoverflow.com/questions/1951742/how-to-symlink-a-file-in-linux) You can find others on your own.

> **knott9 said:**
> I would expect the install process to create /home/knnew in the /home partition(directory) an place whatever config files need to go there.
Why do you keep bringing up this knnew user? Why is it necessary? If all of your old data, settings, etc are associated with the user knott, then why do you want to change this in your new install???

From what I can see, you keep focusing on creating such a user because you have this erroneous notion that you can only upgrade by way of a convoluted process involving temporary new users that you later change back to your old ones. Frankly, I can't even follow your logic. This is what I meant in my initial reply:> **DuckHook said:**
> …You have made the process needlessly complicated…
> **knott9 said:**
> But I do see possible difficulties here too - such as if any config file for firefox, etc. is using the user name knnew inside!!)  So If there is a way to get my objective of replacing my system files in / and in boot, and then getting my config files for emacs, mozilla, etc in /home/knott updated or replaced, I be happy to know about it.
I'll say this one more time: your settings and configs are not isolated only to /boot and /. They are also in /home because that's where desktop settings reside and, since each desktop is unique to each user, they can't reside anywhere else. Your assumption that /home is a pure data directory is erroneous. Ironically, it's the strategy I've given you that actually works with your assumption, because it is designed to *treat* your old /home as a pure data directory (rather than trying to resurrect it as some kind of undead /home directory).
> **knott9 said:**
> I need to remark that updating Linux seems to be its Achilles heel -- if it were't for browsers not working when they fail to be updated (and repositories going away to make such updating hard or impossible), I'd have no interest in updating.
And I need to remark that the problem here is nothing to do with Linux. Your real Achilles heel is your refusal to stay current, waiting until your system is obsolete, out of support and a security hole, then complaining about Linux's inability to deal with the impossible. Had you updated all along while you still could, you would have simply rolled your /home and all of your settings from one version to the next. The upgrade process is reasonably well tested to deal with the last version. It is not designed, nor can it ever be designed, to deal with a version that is 13 versions in arrears. You may as well complain that Windows 10 can't update from Windows 3.1.
> **knott9 said:**
> …As long as emacs, TeX (latex} gcc and Firefox keep working, I don't care about updating my kernel or "modules".)
This expectation is the classical case of demanding to have your cake and eat it too. All of these things stop working for precisely the reason that kernels and modules need updating… over time they are discovered to have serious security holes, bugs and other nasty surprises that must be fixed. I for one am ecstatic that many sites today no longer permit old Firefox browsers to work properly. Those FF versions relied on Windows Explorer security holes to work. The fact that closing off those holes breaks old versions of FF is just too-bad-so-sad.
> **knott9 said:**
> So again, any ideas about how to proceed?  I am stuck.
I have already laid out in my first post a very good proposal on how to proceed. This follow-up post is only a little more detailed. It's up to you whether you want to actually execute it. I don't know what good I'm achieving with any further participation on this thread when you keep asking for ideas while rejecting perfectly good ones that have already been proposed.

---

### Post by Impavidus on 2017-12-16
After reading the original post twice, I think that
> **knott9 said:**
> 
When asked, I gave my user name knnew with a password.
[user knnew should have the user number 1000.]
(later I will move all my /home/knott files to /home/knmew.
and change the user name knnew to knott, and 
finally discard the directory /home/knott, and 
change the directory name /home/knnew to /home/knott.

actually makes sense, provided you don't move all files from /home/knott to /home/knnew, but only move your documents, leaving config files behind (and later discard those). /home/knnew will contain proper settings for 16.04; changing username gives the opportunity to get fresh config files despite reusing the /home directory. /home/knott and /home/knnew will be owned by the same user ID and are on the same partition, so it will be trivial to move those documents using mv. Later, you can change username and home directory to restore your original username. I think there's a command or even a gui tool to do so, but I don't know exactly. This should change the name belonging to user ID 1000, the path of the home directory of user ID 1000, and rename /home/knnew to /home/knott.
> 
[I have another admin user # 1001 named csi  how can I 
get that user "alive" and log-in-able?]

Create the user csi-new as second user. It should get user ID 1001. Then repeat the same trick as performed for user ID 1000.
> 
(2) when the install process moved on, it displayed 
a screen saying "formatting /boot as ext2 in partition 1".
The progress bar is just short of half way and it
is "hung" - nothing is changing.

That seems to be a completely unrelated error. Not sure what could be causing it. Broken partition table? Broken hard drive?

Keep in mind that, unless you want LVM or full system encryption (which implies LVM), or have very old hardware with a big drive that wants the boot files close to the start of the drive, you don't really need a /boot partition. They only cause trouble.

---

