---
title: "Upgrade 11.04 to 11.10 failed"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by atravnic on 2011-10-29
Hi folks -- I can see from the threads here I'm not the only one having 11.10 upgrade problems. 

My attempt to upgrade terminated abnormally. When I reboot it takes me as far as "waiting for network config" followed by "booting without full network configuration" and hangs there. When I boot into safe made, I get "unable to connect to system bus: failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused". 

I'm running an HP Pavilion tx 2500 laptop; AMD Turion X2 Dual Core; and an ST9250827 AS hard drive.

Is there a way to walk the upgrade back to 11.04? Can I start the upgrade over from scratch? Is there a work-around (anything to get me out Vista (I'm dual booted))? Can I go out and get drunk now? What if any help does Canonical offer?

I sure would appreciate your help. Thank you so much!   ...Fred

---

### Post by stephanhuiser on 2011-10-29
Same problem here ... I rebooted into the 11.04 kernel (2.6.38), and it works. Not a real solution for the problem, of course :)

---

### Post by mörgæs on 2011-10-29
You can not roll back to 11.04. If you want this one back, a fresh install is the only way - and a fresh install is also the best option, if you want 11.10 :-)

More advice in the link in my signature.

---

### Post by atravnic on 2011-10-29
> **mörgæs said:**
> You can not roll back to 11.04. If you want this one back, a fresh install is the only way - and a fresh install is also the best option, if you want 11.10 :-)

More advice in the link in my signature.


I read your extensive dissertation, and while much of it is over my head, it truly is a labor of love for which I thank you.

No doubt, as you point out, a fresh install is best, but as I recall that also wipes the disk. So is there a way to do an install and save your data? Or is there a way to get at my data without Ubuntu? By now you've guessed, I did not back anything up. Mea culpa. At this point, all I can do is move on.

Thank you for your help.

---

### Post by westie457 on 2011-10-29
> **atravnic said:**
> I read your extensive dissertation, and while much of it is over my head, it truly is a labor of love for which I thank you.

No doubt, as you point out, a fresh install is best, but as I recall that also wipes the disk. So is there a way to do an install and save your data? Or is there a way to get at my data without Ubuntu? By now you've guessed, I did not back anything up. Mea culpa. At this point, all I can do is move on.

Thank you for your help.

Install as normal and at the 'Where to Install' screen choose 'Something Else'. Here select the original partition and do not format it. System installs and rewrites the system files only.

Have a backup of your personal files just in case something goes wrong.

---

### Post by atravnic on 2011-10-29
> **stephanhuiser said:**
> Same problem here ... I rebooted into the 11.04 kernel (2.6.38), and it works. Not a real solution for the problem, of course :)

Thank you for your suggestion. I'm anxious to try it--11.04 worked fine for me, and waiting a few months for 11.10 will give it a chance to settle down--but, full disclosure: I'm not a techie and I have no idea how to do what you suggest. 

So I ask for your help once more. Can you please give me complete instructions on how to boot into the 11.04 kernel, and anything else I may need to do. And will I have to do this every time I log into Ubuntu 11.04

Thanks again for your help.

---

### Post by oldtimer7777 on 2011-10-29
I'm going to be brutally honest here. I've never liked the dist-upgrade option to upgrade my entire Ubuntu system.  I tired that years and years ago..  with very very little success ever.. and things weren't exactly broken, but I think I had to spend more time getting everything the way it was, than the time would it take to reinstall with a simple walkthrough like this:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

Just back up your settings, files, documents, and passwords/bookmarks, and let it go.

I'm not waiting around for them to fix the upgrade process from one releases to the next because there are just too many things that can get messed up during the upgrade process. It is always better to simply do a quick fresh installation from a flash thumb drive of Ubuntu.  

> **atravnic said:**
> Thank you for your suggestion. I'm anxious to try it--11.04 worked fine for me, and waiting a few months for 11.10 will give it a chance to settle down--but, full disclosure: I'm not a techie and I have no idea how to do what you suggest. 

So I ask for your help once more. Can you please give me complete instructions on how to boot into the 11.04 kernel, and anything else I may need to do. And will I have to do this every time I log into Ubuntu 11.04

Thanks again for your help.

---

### Post by atravnic on 2011-11-01
I'd like to thank everyone who responded with their ideas. But before I thank each of you individually, my overriding concern is backing up my data before I do any of what you all suggested. Dumb idea, what if I were to use wubi from within Vista to grab my data (I may be demonstrating my ignorance -- but hey, what the hell)?

Okay, here come the thank you notes:

  . **stephanhuiser **for suggesting to reboot into the kernel (still don't know how to do that though)

  . **mörgæs **for suggesting a fresh install (as soon as I get a definitive on how to get to my data first so I can back them up before I wipe the slate clean with that fresh install)

  . **westie457 **for the clever way to install 11.10 without touching my data -- has anyone else done that? (I still hope to find a way to back up my data first, though, before I do anything else)

  . **oldtimer7777 **-- I share your frustration (but until I can get to my data... see preceding)

You've been a great bunch of folks to offer all that help.

Thank you!

...Fred

---

### Post by stephanhuiser on 2011-11-02
I rebooted again to kernel 3.0 and it just works now ... don't ask me why :)

---

### Post by atravnic on 2011-11-02
> **stephanhuiser said:**
> I rebooted again to kernel 3.0 and it just works now ... don't ask me why :)

And exactly how do I boot into kernel 3.0, and at what point? You need to give me step-by-step instructions. Pretend you're explaining it to a 5-year old.

I assume this will get me back to 11.04, correct?

Thanks!!   ...Fred

---

### Post by bcbc on 2011-11-03
You can copy your data right from windows using something like [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)
So there's no reason to resort to installing wubi or whatever. The only downside is that if you copy to NTFS it won't remember the permissions/attributes etc.

But if you seriously have important data on your hard drive with no backup, you should buy an external drive and back it up. Hard drives fail and (more often) accidents happen so it's important to have backups.

If you don't want to use that ext2read program you could also boot from an Ubuntu CD in live mode, plug in the external and copy your data.

---

### Post by atravnic on 2011-11-03
> **bcbc said:**
> You can copy your data right from windows using something like [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)
So there's no reason to resort to installing wubi or whatever. The only downside is that if you copy to NTFS it won't remember the permissions/attributes etc.

But if you seriously have important data on your hard drive with no backup, you should buy an external drive and back it up. Hard drives fail and (more often) accidents happen so it's important to have backups.

If you don't want to use that ext2read program you could also boot from an Ubuntu CD in live mode, plug in the external and copy your data.

Thank you bcbc. 

Some basic questions (at work this is all done for us, hence the dumb questions):

  o using exr2read, is it a case of simply copying the data folder-by-folder to backup? and then copying the folders back into Ubuntu if I do a clean install?

  o what other options beside NTFS are there? and what are the pros and cons?

  o the most current Live CD I have is 10.04; does that matter? does it have be the current release? 

  o is copying to an  external drive (I do have one) and then copying back into 11.10 the same simple folder-by-folder exercise? is NTFS an issue doing it this way?

Thank you for your help (and your patience!).

...Fred

---

### Post by atravnic on 2011-11-03
> **stephanhuiser said:**
> I rebooted again to kernel 3.0 and it just works now ... don't ask me why :)

How do you boot into the kernel? 

And which release does kernel 3.0 represent?

Thanks!    ...Fred

---

### Post by bcbc on 2011-11-03
> **atravnic said:**
> Thank you bcbc. 

Some basic questions (at work this is all done for us, hence the dumb questions):

  o using exr2read, is it a case of simply copying the data folder-by-folder to backup? and then copying the folders back into Ubuntu if I do a clean install?

  o what other options beside NTFS are there? and what are the pros and cons?

  o the most current Live CD I have is 10.04; does that matter? does it have be the current release? 

  o is copying to an  external drive (I do have one) and then copying back into 11.10 the same simple folder-by-folder exercise? is NTFS an issue doing it this way?

Thank you for your help (and your patience!).

...Fred
1. Yes. 
2. Since you're using windows and ext2read - your choices are any file system Windows can read: ntfs, fat... for most it's just ntfs. Fat32 cannot support files > 4GB. Either way you'll lose the ownership/permissions (which isn't likely a big deal for straight docs/photos/etc.
3. A 10.04 CD will work fine - anything since 9.10 if you have an ext4 partition.
4. If you copy to an external drive I assume you can compress it and not worry about losing the permissions (if that's a concern). e.g. [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Edit: that backup link is howto backup everything - you'd want to limit it to data you care about i.e. not your broken system files. It's just an example of backing up data.

---

### Post by afrodeity on 2011-11-05
> **atravnic said:**
> Hi folks -- I can see from the threads here I'm not the only one having 11.10 upgrade problems. 

My attempt to upgrade terminated abnormally. When I reboot it takes me as far as "waiting for network config" followed by "booting without full network configuration" and hangs there. When I boot into safe made, I get "unable to connect to system bus: failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused". 


First time this has ever happened with an online upgrade. System totally failed to come up. Usually there are one or two problems with graphics issues, but this has something to do with the new 3.0 kernel. Got exactly the same error system bus error.

---

### Post by atravnic on 2011-11-05
> **bcbc said:**
> 1. Yes. 
2. Since you're using windows and ext2read - your choices are any file system Windows can read: ntfs, fat... for most it's just ntfs. Fat32 cannot support files > 4GB. Either way you'll lose the ownership/permissions (which isn't likely a big deal for straight docs/photos/etc.
3. A 10.04 CD will work fine - anything since 9.10 if you have an ext4 partition.
4. If you copy to an external drive I assume you can compress it and not worry about losing the permissions (if that's a concern). e.g. [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Edit: that backup link is howto backup everything - you'd want to limit it to data you care about i.e. not your broken system files. It's just an example of backing up data.
Quote: "1. Yes.
2. Since you're using windows and ext2read - your choices are any file system Windows can read: ntfs, fat... for most it's just ntfs. Fat32 cannot support files > 4GB. Either way you'll lose the ownership/permissions (which isn't likely a big deal for straight docs/photos/etc.
3. A 10.04 CD will work fine - anything since 9.10 if you have an ext4 partition.
4. If you copy to an external drive I assume you can compress it and not worry about losing the permissions (if that's a concern). e.g. [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Edit: that backup link is howto backup everything - you'd want to limit it to data you care about i.e. not your broken system files. It's just an example of backing up data.
Last edited by bcbc; 2 Days Ago at 06:28 PM.. 

"I used my 10.04 live disk as you suggested and was able to find and back up most of my data. I did run into 'access denied, you don't have permission'. I ran into that on some of my password protected files, but also on some other files. What is it looking for? How can I give it permission? And would that be my administrator password?

I also could not copy files with an .lnk extension. Is there a way around it? Do I even need that kind if a file?

Finally, I chose not to back up the following folders which seem to contain system files: bin; boot; cdrom; dev; etc; lib; media; mnt; opt; opt/google/earth; sbin; srv; run; spool. I also skipped the following files: initrd and initrd.old; vmlinuz and vmlinuz.old.

Did I miss anything?

Thanks again for your help!!!

...Fred

---

### Post by afrodeity on 2011-11-06
I used a liveCD to[ chroot into the system.]("http://ubuntuforums.org/showpost.php?p=10219240&postcount=4") Then I installed linux-generic and booted with this kernel in recovery mode, since the kernel which was installed with the online upgrade is the pae kernel.

I now get to a root prompt.

It appears there is a problem with the dbus-daemon and changing into runlevel 3 <telinit 3) fails.

I have also tried dpkg-reconfigure -a

Will see what more I can do.

I found this [tutorial]("http://joshua14.homelinux.org/blog/?p=1029") on solving the waiting for network configuration boot freeze.

After getting to a / prompt, I could telinit to 3 and reinstalled the Nvidia Driver, which I had installed manually. I was also able to reboot and log into a GDM session.

However, to get network services, I needed to sudo dhclient eth0, so there a few other problems, including unity quitting frequently. I am in the process of [reinstalling unity]("http://ubuntuforums.org/showpost.php?p=11219498&postcount=4").

```

gconftool-2 --recursive-unset /apps/compiz-1 unity --reset
```

did the trick :)

---

### Post by bcbc on 2011-11-06
> **atravnic said:**
> I used my 10.04 live disk as you suggested and was able to find and back up most of my data. I did run into 'access denied, you don't have permission'. I ran into that on some of my password protected files, but also on some other files. What is it looking for? How can I give it permission? And would that be my administrator password?

I also could not copy files with an .lnk extension. Is there a way around it? Do I even need that kind if a file?

Finally, I chose not to back up the following folders which seem to contain system files: bin; boot; cdrom; dev; etc; lib; media; mnt; opt; opt/google/earth; sbin; srv; run; spool. I also skipped the following files: initrd and initrd.old; vmlinuz and vmlinuz.old.

Did I miss anything?

Thanks again for your help!!!

...Fred
It depends. You could have some config files you've customized in /etc/ ... a maybe some mail in /var/mail (I use gmail so not sure about that). If you know what apps you use and that you have their data backed up then probably not an issue.
Other than that, from the listing you provided it looks like your exclusions are good. Here's a general breakdown of the file system hierarchy [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) and also [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

There are some things that will give you permission errors if you try to copy them e.g. .gvfs folders, but this shouldn't happen for your own 'password protected files' (please elaborate on what type of file is failing). Or try copying with elevated privileges.

---

### Post by atravnic on 2011-11-06
> **bcbc said:**
> It depends. You could have some config files you've customized in /etc/ ... a maybe some mail in /var/mail (I use gmail so not sure about that). If you know what apps you use and that you have their data backed up then probably not an issue.
Other than that, from the listing you provided it looks like your exclusions are good. Here's a general breakdown of the file system hierarchy [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) and also [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

There are some things that will give you permission errors if you try to copy them e.g. .gvfs folders, but this shouldn't happen for your own 'password protected files' (please elaborate on what type of file is failing). Or try copying with elevated privileges.


I will follow up on your suggestions, and how do I elevate my privileges working from a live CD? Also, where does Firefox store its files? I have quite a few Bookmark Toolbar entries that'll be a pain to have to recreate.

To add to my misery, I now have a Window Vista problem. I can only use it on a temporary basis, and changes I make are not retained. 

Thanks muchly.

...Fred

---

### Post by bcbc on 2011-11-06
If you're using nautilus to copy you can elevate privileges with  Alt-F2, gksu nautilus
Or sudo from command line.

Then hit Ctrl-H to see hidden files. Your firefox bookmarks will be under .mozilla/firefox in your home directory - you should just be able to copy the whole folder to your new install (I don't use firefox much myself so confirm it somewhere else if you're not sure). 
If you have ssh keys or gpg keys, copy the .ssh and .gpg folders. (Just copy your entire home directory if not sure).

---

### Post by atravnic on 2011-11-08
> **bcbc said:**
> If you're using nautilus to copy you can elevate privileges with  Alt-F2, gksu nautilus
Or sudo from command line.

Then hit Ctrl-H to see hidden files. Your firefox bookmarks will be under .mozilla/firefox in your home directory - you should just be able to copy the whole folder to your new install (I don't use firefox much myself so confirm it somewhere else if you're not sure). 
If you have ssh keys or gpg keys, copy the .ssh and .gpg folders. (Just copy your entire home directory if not sure).

I went ahead and copied my entire home directory (Select all, Copy, Paste into folder). Startling what all got rejected.

The reasons varied. Probably the most frequent one: 'Folder "folder name" could not be handled because you do not have permission to read.' Most of the rejects seemed to be system or operational in nature and I don't think I needed to worry about about those. But there were some of my files such as "googleearth", one of my tax return files, climate related files, "Tor", "Chrome", photos, and a bunch of odt text files. But I also got stuff like "ssh", "dconf", "ibus", "root", etc. I spent hours writing them all down, in case you're curious -- haha.

Another rejection reason, 'Error while copying "file name" into "target backup drive name". File system does not support symbolic links.'

'Error while copying "file name". Error opening file: Permission denied.'

And the cryptic 'Can't copy special file'. I recorded some of those file names if it's important.

At this point, hundreds of files later, I gave up keeping records and just flipped through to look for names that might be my data. And there were some of those. But since it was hours later, I finally broke down and said "Skip all."

My next, and hopefully final, step is to load 11.10 into a USB drive and do a clean install, keeping my fingers crossed that most of what's important to me made it across.

Your thoughts. :confused:

...Fred

---

### Post by bcbc on 2011-11-09
Try this:
Assuming your external drive is mounted on [COLOR="Blue"]/media/label/[/COLOR]:
```
sudo tar cvpzf [COLOR="Blue"]/media/label/[/COLOR]homebackup.tgz --exclude=/home/*/.gvfs /home
```

That should get it all just in case and keep all permissions, links etc.


Then follow *westie457*'s instructions to install without formatting. That's supposed to keep your /home intact.

---

### Post by atravnic on 2011-11-09
> **bcbc said:**
> Try this:
Assuming your external drive is mounted on [COLOR="Blue"]/media/label/[/COLOR]:
```
sudo tar cvpzf [COLOR="Blue"]/media/label/[/COLOR]homebackup.tgz --exclude=/home/*/.gvfs /home
```

That should get it all just in case and keep all permissions, links etc.


Then follow *westie457*'s instructions to install without formatting. That's supposed to keep your /home intact.

Thanks for the terminal command line. I would not have known how to do that.

I recall seeing "media". I guess I fill in the label name when I mount the external drive.

Does the USB drive have to be specifically Linux-compliant or will any stick do?

Thanks!!!!!!!!!!!!!

...Fred

---

### Post by bcbc on 2011-11-10
It doesn't matter where you save it - NTFS is fine. The only limitation on FAT32 is that files must be < 4GB in size. But if you have that much data this probably isn't the best approach. In that case, I'd copy multimedia files separately.

You can check the usb mount point with:
```
ls /media
```

If the USB partition has a label it will be automatically mounted as /media/<label>, if not it might be /media/<uuid> which is ugly to type. But if it is a uuid, just type the first few characters and hit TAB and it should autocomplete.

---

### Post by atravnic on 2011-11-10
> **bcbc said:**
> It doesn't matter where you save it - NTFS is fine. The only limitation on FAT32 is that files must be < 4GB in size. But if you have that much data this probably isn't the best approach. In that case, I'd copy multimedia files separately.

You can check the usb mount point with:
```
ls /media
```

If the USB partition has a label it will be automatically mounted as /media/<label>, if not it might be /media/<uuid> which is ugly to type. But if it is a uuid, just type the first few characters and hit TAB and it should autocomplete.

Do I need a Linux-compliant USB stick or does it not matter? Really don't mean to rush you, but I only have 5 days to return it. Ty!

---

### Post by bcbc on 2011-11-10
All the usb sticks I've used work on Ubuntu. Maybe if it has some proprietary software it won't work. Just plug it in and you'll find out pretty quickly whether it works or not.

If you have one of those USB drives with built in security that only mount the drive after entering a password, then odds are it won't work in Ubuntu. In that case, removing the password may work - at least it did on my one.

---

### Post by atravnic on 2011-11-12
> **bcbc said:**
> Try this:
Assuming your external drive is mounted on [COLOR="Blue"]/media/label/[/COLOR]:
```
sudo tar cvpzf [COLOR="Blue"]/media/label/[/COLOR]homebackup.tgz --exclude=/home/*/.gvfs /home
```

That should get it all just in case and keep all permissions, links etc.


Then follow *westie457*'s instructions to install without formatting. That's supposed to keep your /home intact.
..........................
During execution of the sudo command as above, there was an error early on (I should have written down the line right before the error):  
Cannot stat, No such file or directory
tar: Removing leading `/' from member names
/home/

It ran for a spell and then crashed due to that error. Here's what went down:
/home/ubuntu/.pulse [long code]-runtime
tar: /home/ubuntu/.gvfs: Cannot stat: Permission denied
And it ended thusly:
/home/ubuntu/./profile
/home/ubuntu/./bashrc
/home/ubuntu/./bash logout
tar: Exiting with failure status due to previous errors

So there you have it. [http://ubuntuforums.org/images/icons/icon8.gif](http://ubuntuforums.org/images/icons/icon8.gif) I hope you can help.
Thanks!!
...Fred

---

### Post by bcbc on 2011-11-12
It sounds like a typo - that's likely the cause of the 'no such file or directory'. And the error on .gvfs is exactly what that --exclude== is supposed to avoid. Please can you double check the the command and this time copy the result if you get errors so you can paste it back here.

---

### Post by atravnic on 2011-11-12
> **bcbc said:**
> It sounds like a typo - that's likely the cause of the 'no such file or directory'. And the error on .gvfs is exactly what that --exclude== is supposed to avoid. Please can you double check the the command and this time copy the result if you get errors so you can paste it back here.

Will do.
How do I copy, or take a screen shot?
...Fred

---

### Post by bcbc on 2011-11-12
> **atravnic said:**
> Will do.
How do I copy, or take a screen shot?
...Fred

You can press Alt-E then A to Select **A**ll. Or click and drag your mouse to select the terminal text.

Then Ctrl+Shift+C to copy (or Alt-E and then C).

Or run Screenshot to take a snap. But it's probably easier to copy and paste.

Also run:
ls /media as well so that we can see where your external is mounted.

---

### Post by atravnic on 2011-11-13
> **bcbc said:**
> It sounds like a typo - that's likely the cause of the 'no such file or directory'. And the error on .gvfs is exactly what that --exclude== is supposed to avoid. Please can you double check the the command and this time copy the result if you get errors so you can paste it back here.

After fiddling with your sudo command line a bit, I did get a "successful" run in that it seemed to terminate normally and without error messages (/home/ubuntu.bash_logout). The ls /media command produced a much shorter label (134A-02z0). But -- nothing ever showed up in the /media folder on the external.

As far as copy/pasting the command script for you look over, as you know I have to boot into Vista to log into the forums. The copy/pasting action, however, occurs onn 10.04 side as a guest user. I had no problem selecting/copying the script, but in order to get it across the Vista/Ubuntu divide I had to paste it into a USB stick so as to have it available here . Unfortunately, I never did get the "paste into folder" feature to activated on the 10.04 side, and am therefore unable to show it to you.

Maybe, as guest user in 10.04, I don't have write privileges? I also tried to paste the script into the external drive. Same result, no "paste into folder". I can't imagine what I could be doing wrong. Is there a work-around?

Thank you again for your patience, and for being there for me in a time of need.

Ciao
...Fred

---

### Post by bcbc on 2011-11-13
/media isn't a folder on the external, but rather a mountpoint on your current file system, or to be more precise, if your external partition's uuid is 134A-02z0 then /media/134A-02z0 is a mountpoint. So when you save your backup to /media/134A-02z0/homebackup.tgz you're saving it in the root of your external drives partition.

e.g. on Windows, if it's the F: drive then you'll find it as F:\homebackup.tgz (not that you can open it under windows).

So before rebooting check that the file is there and contains your data:
```
nautilus /media/134A-02z0/
```

And from the nautilus windows you can double click on homebackup.tgz and view your data.

---

### Post by atravnic on 2011-11-25
> **bcbc said:**
> /media isn't a folder on the external, but rather a mountpoint on your current file system, or to be more precise, if your external partition's uuid is 134A-02z0 then /media/134A-02z0 is a mountpoint. So when you save your backup to /media/134A-02z0/homebackup.tgz you're saving it in the root of your external drives partition.

e.g. on Windows, if it's the F: drive then you'll find it as F:\homebackup.tgz (not that you can open it under windows).

So before rebooting check that the file is there and contains your data:
```
nautilus /media/134A-02z0/
```

And from the nautilus windows you can double click on homebackup.tgz and view your data.

Hello bcbc --  Been under the weather and just as I was getting back to normal, Vista crashed and I don't have the energy to deal with that right now. I'm actually more interested in getting Ubuntu up and running again.

Ubuntu wasn't able to find the nautilus command, neither for some reason was the ls /media command working. So I re-ran the lengthy command to copy the entire /homefile. Same results, no luck verifying the data is actually there. 

My last resort is to just follow what Westiennn suggested and just hope the data are there.

What am I doing wrong?

...Fred

---

### Post by bcbc on 2011-11-26
> **atravnic said:**
> Hello bcbc --  Been under the weather and just as I was getting back to normal, Vista crashed and I don't have the energy to deal with that right now. I'm actually more interested in getting Ubuntu up and running again.

Ubuntu wasn't able to find the nautilus command, neither for some reason was the ls /media command working. So I re-ran the lengthy command to copy the entire /homefile. Same results, no luck verifying the data is actually there. 

My last resort is to just follow what Westiennn suggested and just hope the data are there.

What am I doing wrong?

...Fred

I'm not really sure what's going wrong. If you're entering "ls /media" and it doesn't return anything (and no error) then that means the external drive isn't mounted. At least on my system, when I plug in my external usb it automounts all partitions under /media by label or uuid (if no label)

So... that's what you should do. Boot to a live CD desktop, plug in the external. It should automount it under /media but if there's still nothing check the output of:
```
df -h

```

This will give you the size of all mounted partitions as well as the mountpoint.

If you can't get the backup completed, then you'll have to make the judgement call on how to proceed.

---

### Post by atravnic on 2011-11-26
> **bcbc said:**
> I'm not really sure what's going wrong. If you're entering "ls /media" and it doesn't return anything (and no error) then that means the external drive isn't mounted. At least on my system, when I plug in my external usb it automounts all partitions under /media by label or uuid (if no label)

So... that's what you should do. Boot to a live CD desktop, plug in the external. It should automount it under /media but if there's still nothing check the output of:
```
df -h

```

This will give you the size of all mounted partitions as well as the mountpoint.

If you can't get the backup completed, then you'll have to make the judgement call on how to proceed.

My problem may be that I connected the external too soon. So I waited until the live CD finished. That seems to have done the trick. I ran the backup again and it "seems" to have gone okay, except that it won't let me use nautilus. Take a look at the output from the session pasted below.

As I already mentioned, with both Vista and Ubuntu kaput, I'm having to use a family member's Windows laptop to get online to communicate with the Forum. And in order to create a bootable USB drive I would again have to use someone's laptop. That makes me nervous. I have enough problems with my own computer without screwing up someone else's. 

So I thought of using the 10.04 disk that I've been using, installing 10.04 and then upgrading to 10.10 and the upgrading to 11.04, and waiting until 12.04 is out before upgrading to 11.10. Aside it being tedious, it avoids the data problem and other potential problems as well. Your thoughts, please.

Backup session output:
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ ls /media
Easy Drive
ubuntu@ubuntu:~$ nautilus /media/Easy Drive
ubuntu@ubuntu:~$ sudo tar cvpzf /media/easy drive/homebackup.tgz --exclude=/home/*/.gvfs /home
tar: drive/homebackup.tgz: Cannot stat: No such file or directory
tar: Removing leading `/' from member names
/home/
/home/ubuntu/
/home/ubuntu/.update-notifier/
/home/ubuntu/.gnome2_private/
/home/ubuntu/.thumbnails/
/home/ubuntu/.thumbnails/normal/
/home/ubuntu/.thumbnails/normal/33e82336b65eb0fb558339950ae36f01.png
/home/ubuntu/.thumbnails/normal/33b5207600fc0932e1e29db3e9fcee4d.png
/home/ubuntu/.thumbnails/normal/4a1998bb58ad84dc4e7efe261a2428c4.png
/home/ubuntu/.thumbnails/normal/e848a58e540bd6546355cfd19650c7eb.png
/home/ubuntu/.thumbnails/normal/0a4e65b5ec8a3a4b366d94fbd0a3161e.png
/home/ubuntu/.thumbnails/normal/73e8e7ed649138cfbed5af3e09ddefce.png
/home/ubuntu/.thumbnails/normal/3a47941925eea143b789ec7592d8b84f.png
/home/ubuntu/.thumbnails/normal/35793403ef576a09c5f98f2dd5af4696.png
/home/ubuntu/.thumbnails/normal/0a55f5526eef7e2d120a2650aaa398de.png
/home/ubuntu/.thumbnails/normal/10a0a4027074546e70a7778efafc293e.png
/home/ubuntu/.thumbnails/normal/b8b7ecc6d42771a318346ca0bca1fb2f.png
/home/ubuntu/.thumbnails/normal/82cc1cf95d11b6a29c957c43915234ab.png
/home/ubuntu/.thumbnails/normal/a9b91a95293a3602c4c1dbc3d42bc94e.png
/home/ubuntu/.thumbnails/normal/6f8e6471aef1bde86a14ae03f64540ac.png
/home/ubuntu/.thumbnails/normal/2a400e0ab34463b70770a46b5588658a.png
/home/ubuntu/.thumbnails/normal/c515e647c7eca815780d3f1c4af2d4d5.png
/home/ubuntu/.thumbnails/normal/29029245f4a472d01d9a2f423da929d6.png
/home/ubuntu/.thumbnails/normal/08f3f5e749c739808715c2d29ef38f47.png
/home/ubuntu/.thumbnails/normal/960688906ff18f70d46acdbaab65bdc1.png
/home/ubuntu/.nautilus/
/home/ubuntu/.gtk-bookmarks
/home/ubuntu/.gnome2/
/home/ubuntu/.gnome2/nautilus-scripts/
/home/ubuntu/.gnome2/accels/
/home/ubuntu/.gnome2/accels/nautilus
/home/ubuntu/.gnome2/panel2.d/
/home/ubuntu/.gnome2/panel2.d/default/
/home/ubuntu/.gnome2/panel2.d/default/launchers/
/home/ubuntu/.gnome2/keyrings/
/home/ubuntu/.ICEauthority
/home/ubuntu/Videos/
/home/ubuntu/Pictures/
/home/ubuntu/Music/
/home/ubuntu/Documents/
/home/ubuntu/Public/
/home/ubuntu/Templates/
/home/ubuntu/Downloads/
/home/ubuntu/.xsession-errors
/home/ubuntu/.esd_auth
/home/ubuntu/.pulse-cookie
/home/ubuntu/.pulse/
/home/ubuntu/.pulse/3c63a2d0fe3dc724ea17b1474ed1334c-default-source
/home/ubuntu/.pulse/3c63a2d0fe3dc724ea17b1474ed1334c-default-sink
/home/ubuntu/.pulse/3c63a2d0fe3dc724ea17b1474ed1334c-card-database.tdb
/home/ubuntu/.pulse/3c63a2d0fe3dc724ea17b1474ed1334c-stream-volumes.tdb
/home/ubuntu/.pulse/3c63a2d0fe3dc724ea17b1474ed1334c-device-volumes.tdb
/home/ubuntu/.pulse/3c63a2d0fe3dc724ea17b1474ed1334c-runtime
/home/ubuntu/.fontconfig/
/home/ubuntu/.fontconfig/cabbd14511b9e8a55e92af97fb3a0461-le32d4.cache-3
/home/ubuntu/.fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
/home/ubuntu/.fontconfig/eeebfc908bd29a90773fd860017aada4-le32d4.cache-3
/home/ubuntu/.fontconfig/21a99156bb11811cef641abeda519a45-le32d4.cache-3
/home/ubuntu/.config/
/home/ubuntu/.config/indicators/
/home/ubuntu/.config/indicators/application/
/home/ubuntu/.config/indicators/application/lru-file.json
/home/ubuntu/.config/compiz/
/home/ubuntu/.config/compiz/compizconfig/
/home/ubuntu/.config/compiz/compizconfig/config
/home/ubuntu/.config/gnome-disk-utility/
/home/ubuntu/.config/gnome-disk-utility/ata-smart-ignore/
/home/ubuntu/.config/gnome-session/
/home/ubuntu/.config/gnome-session/saved-session/
/home/ubuntu/.config/user-dirs.locale
/home/ubuntu/.config/user-dirs.dirs
/home/ubuntu/.gconfd/
/home/ubuntu/.gconfd/saved_state
/home/ubuntu/.dbus/
/home/ubuntu/.dbus/session-bus/
/home/ubuntu/.dbus/session-bus/3c63a2d0fe3dc724ea17b1474ed1334c-0
/home/ubuntu/.local/
/home/ubuntu/.local/share/
/home/ubuntu/.local/share/gvfs-metadata/
/home/ubuntu/.local/share/gvfs-metadata/uuid-6E1F-B38B
/home/ubuntu/.local/share/gvfs-metadata/uuid-6E1F-B38B-900fee2b.log
/home/ubuntu/.local/share/gvfs-metadata/home
/home/ubuntu/.local/share/gvfs-metadata/home-ea6f570d.log
/home/ubuntu/.sudo_as_admin_successful
/home/ubuntu/.cache/
/home/ubuntu/.cache/indicator-applet.log
/home/ubuntu/.cache/indicator-applet-session.log
/home/ubuntu/.cache/wallpaper/
/home/ubuntu/.cache/wallpaper/zoom_1280_800__usr_share_backgrounds_warty-final-ubuntu.png
/home/ubuntu/.cache/compizconfig/
/home/ubuntu/.cache/compizconfig/zoom.pb
/home/ubuntu/.cache/compizconfig/workarounds.pb
/home/ubuntu/.cache/compizconfig/wobbly.pb
/home/ubuntu/.cache/compizconfig/winrules.pb
/home/ubuntu/.cache/compizconfig/water.pb
/home/ubuntu/.cache/compizconfig/wall.pb
/home/ubuntu/.cache/compizconfig/vpswitch.pb
/home/ubuntu/.cache/compizconfig/video.pb
/home/ubuntu/.cache/compizconfig/titleinfo.pb
/home/ubuntu/.cache/compizconfig/thumbnail.pb
/home/ubuntu/.cache/compizconfig/text.pb
/home/ubuntu/.cache/compizconfig/switcher.pb
/home/ubuntu/.cache/compizconfig/svg.pb
/home/ubuntu/.cache/compizconfig/staticswitcher.pb
/home/ubuntu/.cache/compizconfig/snap.pb
/home/ubuntu/.cache/compizconfig/shift.pb
/home/ubuntu/.cache/compizconfig/session.pb
/home/ubuntu/.cache/compizconfig/screenshot.pb
/home/ubuntu/.cache/compizconfig/scaleaddon.pb
/home/ubuntu/.cache/compizconfig/scale.pb
/home/ubuntu/.cache/compizconfig/rotate.pb
/home/ubuntu/.cache/compizconfig/ring.pb
/home/ubuntu/.cache/compizconfig/resizeinfo.pb
/home/ubuntu/.cache/compizconfig/resize.pb
/home/ubuntu/.cache/compizconfig/regex.pb
/home/ubuntu/.cache/compizconfig/put.pb
/home/ubuntu/.cache/compizconfig/png.pb
/home/ubuntu/.cache/compizconfig/place.pb
/home/ubuntu/.cache/compizconfig/opacify.pb
/home/ubuntu/.cache/compizconfig/obs.pb
/home/ubuntu/.cache/compizconfig/neg.pb
/home/ubuntu/.cache/compizconfig/move.pb
/home/ubuntu/.cache/compizconfig/mousepoll.pb
/home/ubuntu/.cache/compizconfig/minimize.pb
/home/ubuntu/.cache/compizconfig/mag.pb
/home/ubuntu/.cache/compizconfig/kdecompat.pb
/home/ubuntu/.cache/compizconfig/inotify.pb
/home/ubuntu/.cache/compizconfig/imgjpeg.pb
/home/ubuntu/.cache/compizconfig/gnomecompat.pb
/home/ubuntu/.cache/compizconfig/glib.pb
/home/ubuntu/.cache/compizconfig/fs.pb
/home/ubuntu/.cache/compizconfig/fade.pb
/home/ubuntu/.cache/compizconfig/ezoom.pb
/home/ubuntu/.cache/compizconfig/expo.pb
/home/ubuntu/.cache/compizconfig/decoration.pb
/home/ubuntu/.cache/compizconfig/dbus.pb
/home/ubuntu/.cache/compizconfig/cube.pb
/home/ubuntu/.cache/compizconfig/core.pb
/home/ubuntu/.cache/compizconfig/commands.pb
/home/ubuntu/.cache/compizconfig/colorfilter.pb
/home/ubuntu/.cache/compizconfig/clone.pb
/home/ubuntu/.cache/compizconfig/blur.pb
/home/ubuntu/.cache/compizconfig/annotate.pb
/home/ubuntu/.cache/compizconfig/animation.pb
/home/ubuntu/.cache/notify-osd.log
/home/ubuntu/.cache/event-sound-cache.tdb.3c63a2d0fe3dc724ea17b1474ed1334c.i486-pc-linux-gnu
/home/ubuntu/.cache/motd.legal-displayed
/home/ubuntu/.gconf/
/home/ubuntu/.gconf/desktop/
/home/ubuntu/.gconf/desktop/gnome/
/home/ubuntu/.gconf/desktop/gnome/applications/
/home/ubuntu/.gconf/desktop/gnome/applications/window_manager/
/home/ubuntu/.gconf/desktop/gnome/applications/window_manager/%gconf.xml
/home/ubuntu/.gconf/desktop/gnome/applications/%gconf.xml
/home/ubuntu/.gconf/desktop/gnome/peripherals/
/home/ubuntu/.gconf/desktop/gnome/peripherals/touchpad/
/home/ubuntu/.gconf/desktop/gnome/peripherals/touchpad/%gconf.xml
/home/ubuntu/.gconf/desktop/gnome/peripherals/%gconf.xml
/home/ubuntu/.gconf/desktop/gnome/accessibility/
/home/ubuntu/.gconf/desktop/gnome/accessibility/keyboard/
/home/ubuntu/.gconf/desktop/gnome/accessibility/keyboard/%gconf.xml
/home/ubuntu/.gconf/desktop/gnome/accessibility/%gconf.xml
/home/ubuntu/.gconf/desktop/gnome/%gconf.xml
/home/ubuntu/.gconf/desktop/%gconf.xml
/home/ubuntu/.gconf/apps/
/home/ubuntu/.gconf/apps/gnome-terminal/
/home/ubuntu/.gconf/apps/gnome-terminal/profiles/
/home/ubuntu/.gconf/apps/gnome-terminal/profiles/Default/
/home/ubuntu/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml
/home/ubuntu/.gconf/apps/gnome-terminal/profiles/%gconf.xml
/home/ubuntu/.gconf/apps/gnome-terminal/%gconf.xml
/home/ubuntu/.gconf/apps/nm-applet/
/home/ubuntu/.gconf/apps/nm-applet/%gconf.xml
/home/ubuntu/.gconf/apps/nautilus/
/home/ubuntu/.gconf/apps/nautilus/desktop-metadata/
/home/ubuntu/.gconf/apps/nautilus/desktop-metadata/Easy@32@Drive@46@volume/
/home/ubuntu/.gconf/apps/nautilus/desktop-metadata/Easy@32@Drive@46@volume/%gconf.xml
/home/ubuntu/.gconf/apps/nautilus/desktop-metadata/directory/
/home/ubuntu/.gconf/apps/nautilus/desktop-metadata/directory/%gconf.xml
/home/ubuntu/.gconf/apps/nautilus/desktop-metadata/%gconf.xml
/home/ubuntu/.gconf/apps/nautilus/%gconf.xml
/home/ubuntu/.gconf/apps/evolution/
/home/ubuntu/.gconf/apps/evolution/calendar/
/home/ubuntu/.gconf/apps/evolution/calendar/notify/
/home/ubuntu/.gconf/apps/evolution/calendar/notify/%gconf.xml
/home/ubuntu/.gconf/apps/evolution/calendar/%gconf.xml
/home/ubuntu/.gconf/apps/evolution/%gconf.xml
/home/ubuntu/.gconf/apps/compiz/
/home/ubuntu/.gconf/apps/compiz/general/
/home/ubuntu/.gconf/apps/compiz/general/allscreens/
/home/ubuntu/.gconf/apps/compiz/general/allscreens/options/
/home/ubuntu/.gconf/apps/compiz/general/allscreens/options/%gconf.xml
/home/ubuntu/.gconf/apps/compiz/general/allscreens/%gconf.xml
/home/ubuntu/.gconf/apps/compiz/general/%gconf.xml
/home/ubuntu/.gconf/apps/compiz/%gconf.xml
/home/ubuntu/.gconf/apps/metacity/
/home/ubuntu/.gconf/apps/metacity/general/
/home/ubuntu/.gconf/apps/metacity/general/%gconf.xml
/home/ubuntu/.gconf/apps/metacity/%gconf.xml
/home/ubuntu/.gconf/apps/netbook-launcher/
/home/ubuntu/.gconf/apps/netbook-launcher/favorites/
/home/ubuntu/.gconf/apps/netbook-launcher/favorites/ubiquity/
/home/ubuntu/.gconf/apps/netbook-launcher/favorites/ubiquity/%gconf.xml
/home/ubuntu/.gconf/apps/netbook-launcher/favorites/%gconf.xml
/home/ubuntu/.gconf/apps/netbook-launcher/%gconf.xml
/home/ubuntu/.gconf/apps/gnome-power-manager/
/home/ubuntu/.gconf/apps/gnome-power-manager/general/
/home/ubuntu/.gconf/apps/gnome-power-manager/general/%gconf.xml
/home/ubuntu/.gconf/apps/gnome-power-manager/%gconf.xml
/home/ubuntu/.gconf/apps/gnome-screensaver/
/home/ubuntu/.gconf/apps/gnome-screensaver/%gconf.xml
/home/ubuntu/.gconf/apps/panel/
/home/ubuntu/.gconf/apps/panel/toplevels/
/home/ubuntu/.gconf/apps/panel/toplevels/top_panel_screen0/
/home/ubuntu/.gconf/apps/panel/toplevels/top_panel_screen0/background/
/home/ubuntu/.gconf/apps/panel/toplevels/top_panel_screen0/background/%gconf.xml
/home/ubuntu/.gconf/apps/panel/toplevels/top_panel_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/toplevels/bottom_panel_screen0/
/home/ubuntu/.gconf/apps/panel/toplevels/bottom_panel_screen0/background/
/home/ubuntu/.gconf/apps/panel/toplevels/bottom_panel_screen0/background/%gconf.xml
/home/ubuntu/.gconf/apps/panel/toplevels/bottom_panel_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/toplevels/%gconf.xml
/home/ubuntu/.gconf/apps/panel/general/
/home/ubuntu/.gconf/apps/panel/general/%gconf.xml
/home/ubuntu/.gconf/apps/panel/objects/
/home/ubuntu/.gconf/apps/panel/objects/menu_bar_screen0/
/home/ubuntu/.gconf/apps/panel/objects/menu_bar_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/objects/browser_launcher_screen0/
/home/ubuntu/.gconf/apps/panel/objects/browser_launcher_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/objects/yelp_launcher_screen0/
/home/ubuntu/.gconf/apps/panel/objects/yelp_launcher_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/objects/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/
/home/ubuntu/.gconf/apps/panel/applets/clock_screen0/
/home/ubuntu/.gconf/apps/panel/applets/clock_screen0/prefs/
/home/ubuntu/.gconf/apps/panel/applets/clock_screen0/prefs/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/clock_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/notification_area_screen0/
/home/ubuntu/.gconf/apps/panel/applets/notification_area_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/indicator_applet_screen0/
/home/ubuntu/.gconf/apps/panel/applets/indicator_applet_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/show_desktop_button_screen0/
/home/ubuntu/.gconf/apps/panel/applets/show_desktop_button_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/window_list_screen0/
/home/ubuntu/.gconf/apps/panel/applets/window_list_screen0/prefs/
/home/ubuntu/.gconf/apps/panel/applets/window_list_screen0/prefs/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/window_list_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/workspace_switcher_screen0/
/home/ubuntu/.gconf/apps/panel/applets/workspace_switcher_screen0/prefs/
/home/ubuntu/.gconf/apps/panel/applets/workspace_switcher_screen0/prefs/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/workspace_switcher_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/trashapplet_screen0/
/home/ubuntu/.gconf/apps/panel/applets/trashapplet_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/fast_user_switch_screen0/
/home/ubuntu/.gconf/apps/panel/applets/fast_user_switch_screen0/%gconf.xml
/home/ubuntu/.gconf/apps/panel/applets/%gconf.xml
/home/ubuntu/.gconf/apps/panel/global/
/home/ubuntu/.gconf/apps/panel/global/%gconf.xml
/home/ubuntu/.gconf/apps/panel/%gconf.xml
/home/ubuntu/.gconf/apps/%gconf.xml
/home/ubuntu/Desktop/
/home/ubuntu/Desktop/examples.desktop
/home/ubuntu/Desktop/ubiquity-gtkui.desktop
/home/ubuntu/.profile
/home/ubuntu/.bashrc
/home/ubuntu/.bash_logout
tar: Exiting with failure status due to previous errors
ubuntu@ubuntu:~$

---

### Post by bcbc on 2011-11-26
Ubuntu is case sensitive - and also there is a space in easy drive. So... the command is:
```
sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=/home/*/.gvfs /home
```

But... you're booting from the live cd right? So you don't want to backup the live CD's /home, but your own home.
So you need to mount your old Ubuntu partition and use that instead. You can just open up a nautilus file browser window and click on your old ubuntu partition, then it will show up in "ls /media" or you could mount it manually. let's assume it's /dev/sda5
Then the commands would be:
```
sudo mount /dev/sda5 /mnt
sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=/home/*/.gvfs **/mnt**/home
```

If your ubuntu partition mounts with a uuid or label, change the mount point as required. Remember that everything is case-sensitive and spaces need to be 'escaped' with a backslash \

---

### Post by atravnic on 2011-11-27
> **bcbc said:**
> Ubuntu is case sensitive - and also there is a space in easy drive. So... the command is:
```
sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=/home/*/.gvfs /home
```

But... you're booting from the live cd right? So you don't want to backup the live CD's /home, but your own home.
So you need to mount your old Ubuntu partition and use that instead. You can just open up a nautilus file browser window and click on your old ubuntu partition, then it will show up in "ls /media" or you could mount it manually. let's assume it's /dev/sda5
Then the commands would be:
```
sudo mount /dev/sda5 /mnt
sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=/home/*/.gvfs **/mnt**/home
```

If your ubuntu partition mounts with a uuid or label, change the mount point as required. Remember that everything is case-sensitive and spaces need to be 'escaped' with a backslash \

Thank you bcbc. By hook or by crook you're turning me into a Linux programmer.

At this time I'm using a 10.04 live CD to get my data backed up prior to creating a bootable live USB drive and installing 11.10 per Westiennn's suggestion. If that goes well, great. And I'll have a complete back up, too. (There was an error in my logic of repetitive upgrades from 10.04 to 10.10 to 11.04 to avoid the data situation. I have to install 10.04 before I can upgrade, and the install will wipe out my data. So much for that clever idea.)

Just to confirm that I'm understanding you correctly, the first command would back up the wrong /home, correct? I need to mount the old Ubuntu partition and change the back up command accordingly, correct? 

"You can just open up a nautilus file browser window and click on your old ubuntu partition." Two questions. One, I've so far not been able to use nautilus. Could it be that nautilus wasn't yet available in 10.04? Whatever the reason, Ubuntu is not finding it. Two, how would I recognize the old Ubuntu partition.

Thank you so very much for your help.

...Fred

---

### Post by bcbc on 2011-11-27
It's under the places menu on 10.04. Basically it's the default file browser in Ubuntu and you should be able to run it by name (all lower case). But never mind, go to the Places menu and you should see your Ubuntu partition by size or label and then clicking on it will mount. If it's got some long UUID and it gets mounted as /media/xxxx-xxxx-xxxx-xxx then you might want to mount it on /mnt instead.

So go to a terminal after mounting, and run:
df -h

This will tell you the partition e.g. /dev/sda5 and the mountpoint. Then you can decide whether to instead mount it on /mnt or use the existing mountpoint.

In terms of your plan to reinstall and upgrade... this is a painful, time-consuming process (multiple upgrades). And there is always the chance of failure (especially not knowing why your last one failed). You should be able to download the 11.10 ISO while booting the 10.04 CD in live mode, and then running the USB creator.

---

### Post by atravnic on 2011-11-27
> **bcbc said:**
> It's under the places menu on 10.04. Basically it's the default file browser in Ubuntu and you should be able to run it by name (all lower case). But never mind, go to the Places menu and you should see your Ubuntu partition by size or label and then clicking on it will mount. If it's got some long UUID and it gets mounted as /media/xxxx-xxxx-xxxx-xxx then you might want to mount it on /mnt instead.

So go to a terminal after mounting, and run:
df -h

This will tell you the partition e.g. /dev/sda5 and the mountpoint. Then you can decide whether to instead mount it on /mnt or use the existing mountpoint.

In terms of your plan to reinstall and upgrade... this is a painful, time-consuming process (multiple upgrades). And there is always the chance of failure (especially not knowing why your last one failed). You should be able to download the 11.10 ISO while booting the 10.04 CD in live mode, and then running the USB creator.

10.04 gives you a choice--as they all do--to either try or install. I have not been able to get on-line in the former mode, so shall I assume to take the install route to get on-line, run the USB creator, download 11.10 and install it?
...Fred

---

### Post by atravnic on 2011-11-27
> **atravnic said:**
> 10.04 gives you a choice--as they all do--to either try or install. I have not been able to get on-line in the former mode, so shall I assume to take the install route to get on-line, run the USB creator, download 11.10 and install it?
...Fred

So I assume I've been using nautilus by default. Is there a way to print a directory?

Here's what I did, but I can't for the life of me figure out if I'm looking at the right partition. What size am I looking for, and what label?

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ ls /media
1adba56a-e24d-4c56-abd8-5952dc041706  Easy Drive
ubuntu@ubuntu:~$ sudo mount /Easy\ Drive/
mount: can't find /Easy Drive/ in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount 1adba56d-e24d-4c56-abd8-5952dc041706
mount: can't find 1adba56d-e24d-4c56-abd8-5952dc041706 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  1.4G   33M  1.4G   3% /
none                  1.4G  360K  1.4G   1% /dev
/dev/sr0              700M  700M     0 100% /cdrom
/dev/loop0            672M  672M     0 100% /rofs
none                  1.4G  100K  1.4G   1% /dev/shm
tmpfs                 1.4G   12K  1.4G   1% /tmp
none                  1.4G   80K  1.4G   1% /var/run
none                  1.4G  4.0K  1.4G   1% /var/lock
none                  1.4G     0  1.4G   0% /lib/init/rw
/dev/sdc1             150G   13G  137G   9% /media/Easy Drive
/dev/sda7              28G  9.2G   18G  35% /media/1adba56a-e24d-4c56-abd8-5952dc041706
ubuntu@ubuntu:~$

---

### Post by bcbc on 2011-11-27
```
sudo mount /dev/sda7 /mnt
ls /mnt/home

```
Make sure that your home directory appears.

Then use that backup command with /mnt/home

Why can't you get online when ysing the live cd?

---

### Post by bluexrider on 2011-11-27
WOW! I have to say that as much time you put into this "save-a-upgrade" you could have backed your data and installed a fresh copy. --IMHO

Good luck, really!

---

### Post by atravnic on 2011-11-28
> **bcbc said:**
> ```
sudo mount /dev/sda7 /mnt
ls /mnt/home

```
Make sure that your home directory appears.

Then use that backup command with /mnt/home

Why can't you get online when ysing the live cd? (no idea, could be I need a driver; had no problem when I had 10.04 installed; however, 9.10 before that required a driver, once installed all was well)

Thanks!
...Fred

---

### Post by atravnic on 2011-11-28
> **bluexrider said:**
> WOW! I have to say that as much time you put into this "save-a-upgrade" you could have backed your data and installed a fresh copy. --IMHO

Good luck, really!

[http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)
Almost funny. Try and understand, it's the journey, not the destination. Thanks to bcbc I learned a lot.

But stay tuned. The struggle so far has been all about getting a complete back up of my data. The best is yet to come: the actual installation and rolling the backup forward.

You're of course right in what you say, but for a techno nerd (at least in the Linux world) like me it hasn't been easy and I admire bcbc's patience sticking with me.

Eternity is a very long time, especially toward the end. Are we there yet?

...Fred

---

### Post by bluexrider on 2011-11-28
> **atravnic said:**
> [http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)
Almost funny. Try and understand, it's the journey, not the destination. Thanks to bcbc I learned a lot.
Well,  I hope you packed a lunch.....

> **atravnic said:**
> 
But stay tuned. The struggle so far has been all about getting a complete back up of my data. The best is yet to come: the actual installation and rolling the backup forward.

Oh YEAH this is better than soap operas

> **atravnic said:**
> 
You're of course right in what you say, but for a techno nerd (at least in the Linux world) like me it hasn't been easy and I admire bcbc's patience sticking with me.
I gotta say that if it takes me more than an hour to do what I need then its a waste, google is my friend.....so is cut and paste!

> **atravnic said:**
> 
Eternity is a very long time, especially toward the end. Are we there yet?

...Fred

I will be watching the watcher watch you.

---

### Post by atravnic on 2011-11-29
> **bcbc said:**
> ```
sudo mount /dev/sda7 /mnt
ls /mnt/home

```
Make sure that your home directory appears.

Then use that backup command with /mnt/home

Why can't you get online when ysing the live cd?

Okay, here's proof if anyone can screw it up, I can. Please note embedded, bracketed comments/question.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mnt
sudo: mnt: command not found
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
ubuntu@ubuntu:~$ ls /mnt/home
atravnic 
[COLOR="Black"]**[atravnic is my home directory on the hard drive which presumably contains all my data]**[/COLOR]

ubuntu@ubuntu:~$ sudo tar cvpzf /media/atravnic/homebackup.tgz --exclude=/home/*/.gvfs /mnt/home 
**[So I think I did it bass ackwards treating the target directory as the source -- correct?]**

tar: Removing leading `/' from member names
tar: /media/atravnic/homebackup.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
/mnt/home/
/mnt/home/atravnic/
/mnt/home/atravnic/.bashrc
/mnt/home/atravnic/Music/
/mnt/home/atravnic/Music/Playlists/
/mnt/home/atravnic/Music/Playlists/Sample Playlist.wpl
**[Not sure what I was trying to accomplish here]**

ubuntu@ubuntu:~$ ls /media
1adba56a-e24d-4c56-abd8-5952dc041706  Easy Drive
ubuntu@ubuntu:~$ ls /mmnt/home
ls: cannot access /mmnt/home: No such file or directory
**[Ditto]**

ubuntu@ubuntu:~$ sudo tar cvpzf /atravnic/homebackup.tgz --exclude=/home/*/.gvfs /mnt/home
tar: Removing leading `/' from member names
/mnt/home/
/mnt/home/atravnic/
/mnt/home/atravnic/.bashrc
/mnt/home/atravnic/Music/
/mnt/home/atravnic/Music/Playlists/
/mnt/home/atravnic/Music/Playlists/Sample Playlist.wpl
/mnt/home/atravnic/Music/Playlists/QuickPlay Playlist.wpl
tar: /atravnic/homebackup.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
/mnt/home/atravnic/tax federal/
/mnt/home/atravnic/tax federal/health/
/mnt/home/atravnic/tax federal/health/medicare registration.ps
ubuntu@ubuntu:~$ sudo tar cvpzf /home/atravnic/homebackup.tgz --exclude=/home/*/.gvfs /mnt/home
tar: Removing leading `/' from member names
/mnt/home/
/mnt/home/atravnic/
/mnt/home/atravnic/.bashrc
/mnt/home/atravnic/Music/
/mnt/home/atravnic/Music/Playlists/
/mnt/home/atravnic/Music/Playlists/Sample Playlist.wpl
/mnt/home/atravnic/Music/Playlists/QuickPlay Playlist.wpl
/mnt/home/atravnic/tax federal/
/mnt/home/atravnic/tax federal/health/
/mnt/home/atravnic/tax federal/health/medicare registration.ps
tar: /home/atravnic/homebackup.tgz: Cannot open: No such file or directory
**[Getting desprate]**
tar: Error is not recoverable: exiting now

ubuntu@ubuntu:~$ sudo tar cvpzf /30\ GB\ Filesystem/home/atravnic/homebackup.tgz --exclude=/home/*/.gvfs /mnt/home
**[30 GB Filesystem is the name of the filesystem on my hard  drive]**

tar: Removing leading `/' from member names
/mnt/home/
/mnt/home/atravnic/
/mnt/home/atravnic/.bashrc
/mnt/home/atravnic/Music/
/mnt/home/atravnic/Music/Playlists/
/mnt/home/atravnic/Music/Playlists/Sample Playlist.wpl
/mnt/home/atravnic/Music/Playlists/QuickPlay Playlist.wpl
/mnt/home/atravnic/tax federal/
/mnt/home/atravnic/tax federal/health/
/mnt/home/atravnic/tax federal/health/medicare registration.ps
tar: /30 GB Filesystem/home/atravnic/homebackup.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
ubuntu@ubuntu:~$ sudo tar cvpzf /media/atravnic/homebackup.tgz --exclude=/home/*/.gvfs /mnt/home
**[Same as before, reversing source and target -- Am I right???]**

So here is what I think I need to do:


```
ubuntu@ubuntu:~$ sudo tar cvpzf /Easy\ Drive/homebackup.tgz --exclude=/home/*/.gvfs /mnt/home 

```

If this is not correct, please set me straight.
What will the backed up data file be called on the external (Easy Drive)?

Thank you!
...Fred

---

### Post by bcbc on 2011-11-29
> **atravnic said:**
> Okay, here's proof if anyone can screw it up, I can. Please note embedded, bracketed comments/question.
...

So here is what I think I need to do:


```
ubuntu@ubuntu:~$ sudo tar cvpzf /Easy\ Drive/homebackup.tgz --exclude=/home/*/.gvfs /mnt/home 

```

If this is not correct, please set me straight.
What will the backed up data file be called on the external (Easy Drive)?

Thank you!
...Fred
Hey, we've all been there ;)

Try this:
```
sudo mount /dev/sda7 /mnt
sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=/mnt/home/*/.gvfs /mnt/home
```

This will create a file on your Easy Drive called "homebackup.tgz".

After it's done, open up the file browser (nautilus), browse to your easy drive and open up the file - it will let you browse inside it and make sure all the files are there.

---

### Post by atravnic on 2011-11-29
> **bcbc said:**
> Hey, we've all been there ;)

Try this:
```
sudo mount /dev/sda7 /mnt
sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=/mnt/home/*/.gvfs /mnt/home
```

This will create a file on your Easy Drive called "homebackup.tgz".

After it's done, open up the file browser (nautilus), browse to your easy drive and open up the file - it will let you browse inside it and make sure all the files are there.

Well, 3.3GB were backed up and it looks to me all my data made it across. There were some problems, but I'm not sure it matters. My one concern is that since it did terminate abnormally, will this be a problem if I need to use the backup during installation?

Also, I now have two homebackup.tgz files, one on the external--I unzipped it and used Archive Mounter to look through it--the other, which has software as well as data, is somewhere, but I couldn't tell where. When I moused over, here is what I got: "archive: //file%253A%252F%252F%252Fmedia%252FEasy%252520Drive%252Fhomebackup.tgz/". Maybe this is the extracted version, do you think?

Here are the problems I was able to capture:
tar: mnt/home/atravnic/misc/Screenshot-atravnic@atravnic-laptop\: ~.png: Cannot open: Invalid argument
tar: mnt/home/atravnic/.mozilla/firefox/vkuuxfit.default/lock: Cannot create symlink to `127.0.0.1:+2409': Operation not permitted
tar: mnt/home/atravnic/.local/share/gvfs-metadata/computer\:: Cannot open: Invalid argument
tar: mnt/home/atravnic/.local/share/gvfs-metadata/smb-network\:-e27e69ea.log: Cannot open: Invalid argument
tar: mnt/home/atravnic/.local/share/gvfs-metadata/trash\:: Cannot open: Invalid argument
tar: mnt/home/atravnic/.local/share/gvfs-metadata/computer\:-f326492f.log: Cannot open: Invalid argument
tar: mnt/home/atravnic/.local/share/gvfs-metadata/network\:: Cannot open: Invalid argument
tar: mnt/home/atravnic/.local/share/gvfs-metadata/trash\:-07e8b8d2.log: Cannot open: Invalid argument
tar: mnt/home/atravnic/.local/share/gvfs-metadata/smb-network\:: Cannot open: Invalid argument
tar: mnt/home/atravnic/.local/share/gvfs-metadata/network\:-cebaf726.log: Cannot open: Invalid argument
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libQtXml.so.4.6: Cannot create symlink to `libQtXml.so.4.6.2': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libQtXml.so.4: Cannot create symlink to `libQtXml.so.4.6.2': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libQtCore.so.4: Cannot create symlink to `libQtCore.so.4.6.2': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libpng14.so: Cannot create symlink to `libpng14.so.14.3.0': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libevent_extra-2.0.so.5: Cannot create symlink to `libevent_extra-2.0.so.5.0.1': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libQtNetwork.so.4: Cannot create symlink to `libQtNetwork.so.4.6.2': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libQtNetwork.so: Cannot create symlink to `libQtNetwork.so.4.6.2': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libQtGui.so.4: Cannot create symlink to `libQtGui.so.4.6.2': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libQtNetwork.so.4.6: Cannot create symlink to `libQtNetwork.so.4.6.2': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libQtGui.so.4.6: Cannot create symlink to `libQtGui.so.4.6.2': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libz/libz.so: Cannot create symlink to `libz.so.1.2.3': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libz/libz.so.1: Cannot create symlink to `libz.so.1.2.3': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libevent_extra.so: Cannot create symlink to `libevent_extra-2.0.so.5.0.1': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libevent_core-2.0.so.5: Cannot create symlink to `libevent_core-2.0.so.5.0.1': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libQtCore.so: Cannot create symlink to `libQtCore.so.4.6.2': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libevent_core.so: Cannot create symlink to `libevent_core-2.0.so.5.0.1': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libQtXml.so: Cannot create symlink to `libQtXml.so.4.6.2': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libQtCore.so.4.6: Cannot create symlink to `libQtCore.so.4.6.2': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libssl.so: Cannot create symlink to `libssl.so.0.9.8': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libcrypto.so: Cannot create symlink to `libcrypto.so.0.9.8': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libevent.so: Cannot create symlink to `libevent-2.0.so.5.0.1': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libpng14.so.14: Cannot create symlink to `libpng14.so.14.3.0': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libevent-2.0.so.5: Cannot create symlink to `libevent-2.0.so.5.0.1': Operation not permitted
tar: mnt/home/atravnic/tor-browser_en-US/Lib/libQtGui.so: Cannot create symlink to `libQtGui.so.4.6.2': Operation not permitted
tar: mnt/home/atravnic/.pulse/5bd6dd0d96b42fcb891f4dd64b54acde-runtime: Cannot create symlink to `/tmp/pulse-yHZzsRwpC5iU': Operation not permitted
tar: mnt/home/atravnic/.googleearth/instance-running-lock: Cannot create symlink to `/proc/2656': Operation not permitted
tar: Exiting with failure status due to previous errors

What's your read on these errors?
Thank you!
...Fred

---

### Post by bcbc on 2011-11-30
I don't like those errors. I've just run a little test and mine was totally clean. But some like .local/share/gvfs-metadata are probably irrelevant. And I doubt the broken symlinks for the torbrowser matter - you can probably just set that up again.

Why don't you capture the errors - then you can analyze them and see whether you care? Also you can add more excludes:
```
sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=/mnt/home/*/.gvfs --exclude=/mnt/home/*/.local/share --exclude=/mnt/home/*/tor-browser_en-US /mnt/home > normal.out 2> errors.out
```

After it's finished you can view the errors.out and see whether there's something there you care about:
```
less errors.out
```

Also, regarding that other backup that you can't find. You'd better find it. If you can't find it now, you're not likely to find it later!?

---

### Post by bcbc on 2011-11-30
I've been playing with this on my own machine - actually a virtual machine with two installs - and I have some adjustments to make. The main issue is the path names being retained in the archive. It's a lot simpler to avoid this when restoring.

So my suggestion is this, to navigate to your home directory prior to backing up. As per the following:
```
sudo mount /dev/sda7 /mnt
cd /mnt/home
sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=atravnic/.gvfs --exclude=atravnic/.local/share --exclude=atravnic/tor-browser_en-US atravnic > normal.out 2> errors.out
```

Then to restore (if required, on new install):
```
cd /home
sudo tar xvfz /media/Easy\ Drive/homebackup.tgz -C .
```

This worked for me (I deleted my home directory completely before restoring - with no noticeable issues).

PS that '.' at the end of the restore command isn't a mistake, and it is required. I probably could have just said /home instead, but that's how I did my test - and my /home is on a separate partition)

---

### Post by atravnic on 2011-12-01
> **bcbc said:**
> I've been playing with this on my own machine - actually a virtual machine with two installs - and I have some adjustments to make. The main issue is the path names being retained in the archive. It's a lot simpler to avoid this when restoring.

So my suggestion is this, to navigate to your home directory prior to backing up. As per the following:
```
sudo mount /dev/sda7 /mnt
cd /mnt/home
sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=atravnic/.gvfs --exclude=atravnic/.local/share --exclude=atravnic/tor-browser_en-US atravnic > normal.out 2> errors.out
```

Then to restore (if required, on new install):
```
cd /home
sudo tar xvfz /media/Easy\ Drive/homebackup.tgz -C .
```

This worked for me (I deleted my home directory completely before restoring - with no noticeable issues).

PS that '.' at the end of the restore command isn't a mistake, and it is required. I probably could have just said /home instead, but that's how I did my test - and my /home is on a separate partition)

Now what?
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt

mount: /dev/sda7 already mounted or /mnt busy

mount: according to mtab, /dev/sda7 is already mounted on /mnt

ubuntu@ubuntu:~$ cd /mnt/home

ubuntu@ubuntu:/mnt/home$ sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=atravnic/.gvfs --exclude=atravnic/.local/share --exclude=atravnic/tor-browser_en-US atravnic > normal.out2> errors.out

bash: normal.out2: Permission denied

If I survive this, correction, if we survive this, and if I ever get out to Vancouver again--got as close as looking down on it from the mountains but had to get back to Banff before dark--I'll buy you a drink. Might even get you drunk. I owe you big time for what I've put you through.

Thanks!
...Fred

---

### Post by bcbc on 2011-12-01
> **atravnic said:**
> Now what?
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt

mount: /dev/sda7 already mounted or /mnt busy

mount: according to mtab, /dev/sda7 is already mounted on /mnt

ubuntu@ubuntu:~$ cd /mnt/home

ubuntu@ubuntu:/mnt/home$ sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=atravnic/.gvfs --exclude=atravnic/.local/share --exclude=atravnic/tor-browser_en-US atravnic > normal.out2> errors.out

bash: normal.out2: Permission denied

If I survive this, correction, if we survive this, and if I ever get out to Vancouver again--got as close as looking down on it from the mountains but had to get back to Banff before dark--I'll buy you a drink. Might even get you drunk. I owe you big time for what I've put you through.

Thanks!
...Fred
I'm always up for a drink. (I might need to buy you one for what I'm putting you through ;) )

So there's a space between "normal.out" and "2>" - you have "normal.out2>"

Try cutting and pasting the command from post #50 (use Ctrl+Shift+V to paste in a terminal).

Once it's finished view the errors to make sure there's nothing you think should have been copied that failed:
```
less errors.out
```

---

### Post by atravnic on 2011-12-02
> **bcbc said:**
> I'm always up for a drink. (I might need to buy you one for what I'm putting you through ;) )

So there's a space between "normal.out" and "2>" - you have "normal.out2>"

Try cutting and pasting the command from post #50 (use Ctrl+Shift+V to paste in a terminal).

Once it's finished view the errors to make sure there's nothing you think should have been copied that failed:
```
less errors.out
```

To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 

ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt 
ubuntu@ubuntu:~$ cd /mnt/home 
ubuntu@ubuntu:/mnt/home$ sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=atravnic/.gvfs --exclude=atravnic/.local/share --exclude=atravnic/tor-browser_en-US atravnic > normal.out 2> errors.out 
bash: normal.out: Permission denied 
ubuntu@ubuntu:/mnt/home$ 

The longer I stare at "normal.out" and "2>" the more I begin to realize there is an evil, galactic conspiracy in progress against me. I just don't see what I did wrong this time. HELP, before I go nuts.

Have a good weekend. Take some time off. Split some firewood. It's a wonderful, mind-emptying thing to restore sanity.

Thank you!
...Fred

P.S. -- I'll take you up on that drink [http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif) but I'm clearly benefiting more from this exchange. Take care!

---

### Post by bcbc on 2011-12-02
It's probably because /dev/sda7 is mounted readonly or someother permissions problem (because we've navigated onto the mounted drive.)

So... I suppose you can redirect the output to the live CD's /home directory. That will survive long enough to check the output.

```
sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=atravnic/.gvfs --exclude=atravnic/.local/share --exclude=atravnic/tor-browser_en-US atravnic > ~/normal.out 2> ~/errors.out
less ~/errors.out
```
Note the 'tilde forward slash' ~/ which translates to your current home directory, so ~/errors.out is the same as /home/ubuntu/errors.out (on the live CD).

---

### Post by atravnic on 2011-12-03
> **bcbc said:**
> It's probably because /dev/sda7 is mounted readonly or someother permissions problem (because we've navigated onto the mounted drive.)

So... I suppose you can redirect the output to the live CD's /home directory. That will survive long enough to check the output.

```
sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=atravnic/.gvfs --exclude=atravnic/.local/share --exclude=atravnic/tor-browser_en-US atravnic > ~/normal.out 2> ~/errors.out
less ~/errors.out
```
Note the 'tilde forward slash' ~/ which translates to your current home directory, so ~/errors.out is the same as /home/ubuntu/errors.out (on the live CD).

Looks like a got a good run this time, well, good enough maybe:

ubuntu@ubuntu:~$ cd /mnt/home

ubuntu@ubuntu:/mnt/home$ sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz  --exclude=atravnic/.gvfs --exclude=atravnic/.local/share --exclude=atravnic/tor-browser_en-US atravnic > ~/normal.out 2> ~/errors.out less ~/errors.out

ubuntu@ubuntu:/mnt/home$ 
Errors out:
tar: less: Cannot stat: No such file or directory

tar: Removing leading `/' from member names

tar: Exiting with failure status due to previous errors

Normal out:
see attached file --  I went through the motions and clicked upload, but I don't see it anywhere. This forum is a tad quirky in many ways. Let me know if it doesn't show up. We can always resort to emailing directly I suppose.

Thanks!
...Fred

---

### Post by bcbc on 2011-12-04
Nearly there. That "less ~/errors.out" is a separate command that you use to browse the errors.

So run the archive again:
```
sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=atravnic/.gvfs --exclude=atravnic/.local/share --exclude=atravnic/tor-browser_en-US atravnic > ~/normal.out 2> ~/errors.out
```

Then check for errors:
```
less ~/errors.out
#or if you prefer gedit
gedit ~/errors.out
```

PS the errors you uploaded didn't appear. (don't upload normal.out; just the errors.out and only if there's something there you are concerned about)

---

### Post by atravnic on 2011-12-04
> **bcbc said:**
> Nearly there. That "less ~/errors.out" is a separate command that you use to browse the errors.

So run the archive again:
```
sudo tar cvpzf /media/Easy\ Drive/homebackup.tgz --exclude=atravnic/.gvfs --exclude=atravnic/.local/share --exclude=atravnic/tor-browser_en-US atravnic > ~/normal.out 2> ~/errors.out
```

Then check for errors:
```
less ~/errors.out
#or if you prefer gedit
gedit ~/errors.out
```

PS the errors you uploaded didn't appear. (don't upload normal.out; just the errors.out and only if there's something there you are concerned about)

Had a clean run, no errors – woo-hoo!

Okay, next. At some point I need to FAT16/FAT32 format a USB stick, then make it downloadable and bootable (on a Windows machine, no choice but shouldn't be a problem) using ubuntu. com's recommended pendrivelinux universal usb installer – unless you have another suggestion. 

Download 11.10, take the magic stick to my laptop and, using westie457's technique installing only the system files (start a normal install and at “Where to Install” select “Something Else”, select the original partition (I assume that means the partition on my laptop's hard drive???) and do not format) leaving the data untouched.

What are the chances it'll be that simple – haha!?!

Now in the event I should need the data backup, I assume it'll automatically select the most recent? Yes, no? And the code for restoring the backed up data from the external to my hard drive is: 
```
cd /home
sudo tar xvfz /media/Easy\ Drive/homebackup.tgz -C .
```

Did I miss anything? No doubt about it.
...Fred

P.S. -- Is there something like the "erase" command in Windows in the Linux world?

---

### Post by bcbc on 2011-12-04
Great! So... no matter how many times you ran that command, it was replacing the same archive so you only have the one backup. And yes that instruction I gave for restoring was one I've tested. 

To create the USB, follow the instructions on [ubuntu.com]("http://www.ubuntu.com/download/ubuntu/download") for creating the bootable USB.

Yes when installing you choose something else, then you have to select which partition will be root - that's what you currently have on /dev/sda7 so select that. So click on that. Then select "Change". From the popup box, select Use as Ext4, select "/" from the "Mount point" drop down box, and make sure that the Format check box is not selected.

Also select the partition you'll be using as swap.

I'll try and get you some screenshots so you can see what it looks like.

---

### Post by bcbc on 2011-12-04
This is the 11.04 installer and it's a VM with different partitions, but it will look similar. I haven't personally installed like this myself. These are just screen shots on the steps:

1. After picking "Something else" you'll see a list of partitions. Pick the one you are reinstalling on i.e. /dev/sda7 and click on "Change"
2. For "Use as" select "Ext4 ..."
3. Leave Format partition unchecked
4. For "Mount point" choose "/"
5. The last shot shows what it should look like before proceeding. (The mountpoint as "/" and the format unchecked)

The swap partition should be selected automatically.

---

### Post by atravnic on 2011-12-05
> **bcbc said:**
> This is the 11.04 installer and it's a VM with different partitions, but it will look similar. I haven't personally installed like this myself. These are just screen shots on the steps:

1. After picking "Something else" you'll see a list of partitions. Pick the one you are reinstalling on i.e. /dev/sda7 and click on "Change"
2. For "Use as" select "Ext4 ..."
3. Leave Format partition unchecked
4. For "Mount point" choose "/"
5. The last shot shows what it should look like before proceeding. (The mountpoint as "/" and the format unchecked)

The swap partition should be selected automatically.

Someday I'll get to this point I'm sure, just not quite yet. I seem to attract problems the way a tuxedo attracts lint. 

Trying to set up the Universal USB installer, in step 1 you elect the version of Ubuntu you plan to use (11.10 for me). No problem. Step 2 gives you: "Select your Ubuntu 11.10*.iso" and invites you to browse to it. I click browse and get: "No match...". 

If it's looking for a downloaded Ubuntu 11.10, I can understand why it can't find it, since I haven't downloaded it yet. So I clicked on the big orange box on Ubuntu.com's main page, and it starts to download ubuntu into the person's laptop I'm using. However, I had promised her I would not download anything into her machine, and was expecting to download ubuntu directly into my usb stick. So I stopped the download and not sure where to go from here. Not sure I have the order in which to proceed down correctly. My assumption was the usb installer software would come first.

Furthermore, since I'm working on a Windows machine, I'm not sure this is entirely germane to this thread (or forum?). So I'm wondering, should I open a different thread, is this part a tad out of your realm to begin with, or should I stop torturing you and just bite the bullet and buy a 11.10 CD from Canonical?

The latter is probably the best option. Your thoughts?

Thank you!
...Fred

---

### Post by bcbc on 2011-12-05
> **atravnic said:**
> Someday I'll get to this point I'm sure, just not quite yet. I seem to attract problems the way a tuxedo attracts lint. 

Trying to set up the Universal USB installer, in step 1 you elect the version of Ubuntu you plan to use (11.10 for me). No problem. Step 2 gives you: "Select your Ubuntu 11.10*.iso" and invites you to browse to it. I click browse and get: "No match...". 

If it's looking for a downloaded Ubuntu 11.10, I can understand why it can't find it, since I haven't downloaded it yet. So I clicked on the big orange box on Ubuntu.com's main page, and it starts to download ubuntu into the person's laptop I'm using. However, I had promised her I would not download anything into her machine, and was expecting to download ubuntu directly into my usb stick. So I stopped the download and not sure where to go from here. Not sure I have the order in which to proceed down correctly. My assumption was the usb installer software would come first.

Furthermore, since I'm working on a Windows machine, I'm not sure this is entirely germane to this thread (or forum?). So I'm wondering, should I open a different thread, is this part a tad out of your realm to begin with, or should I stop torturing you and just bite the bullet and buy a 11.10 CD from Canonical?

The latter is probably the best option. Your thoughts?

Thank you!
...Fred

I don't understand why you can't download the ISO. It's just a (700MB) file: you save it, run the usb installer, and then delete it. It's less intrusive than downloading the USB installer which is a program.

I suppose you could buy it from Canonical if you want to wait longer - that's up to you. I download a lot of ISOs so that's not really an option for me.

---

### Post by atravnic on 2011-12-05
> **bcbc said:**
> I don't understand why you can't download the ISO. It's just a (700MB) file: you save it, run the usb installer, and then delete it. It's less intrusive than downloading the USB installer which is a program.

I suppose you could buy it from Canonical if you want to wait longer - that's up to you. I download a lot of ISOs so that's not really an option for me.

Tried it again, still no match for ubuntu-11.10*.iso, nor does it show up in a search. The instruction after downloading the universal installer is to browse to ubuntu-11.10*.iso. When I click on the browse button per instructions I get the no match response. So I don't know what I'm doing wrong--and it's not as though I had never downloaded anything--but it just ain't thar.
...Fred

---

### Post by bcbc on 2011-12-05
> **atravnic said:**
> Tried it again, still no match for ubuntu-11.10*.iso, nor does it show up in a search. The instruction after downloading the universal installer is to browse to ubuntu-11.10*.iso. When I click on the browse button per instructions I get the no match response. So I don't know what I'm doing wrong--and it's not as though I had never downloaded anything--but it just ain't thar.
...Fred

Most browsers save downloads by default in the user's Downloads folder, or prompt you where to save it. That's a big download 700MB and you would have had to wait around 30 minutes for it to complete. Open up the Windows Explorer and look for Downloads on the left (near the top) or if XP go to My Documents, and find the Downloads folder. Then sort by size and it should be near the top. If that fails hit F3 to do a windows search and look for *.iso on your computer.

---

### Post by atravnic on 2011-12-06
> **bcbc said:**
> Most browsers save downloads by default in the user's Downloads folder, or prompt you where to save it. That's a big download 700MB and you would have had to wait around 30 minutes for it to complete. Open up the Windows Explorer and look for Downloads on the left (near the top) or if XP go to My Documents, and find the Downloads folder. Then sort by size and it should be near the top. If that fails hit F3 to do a windows search and look for *.iso on your computer.

Aah, didn't think it could take that long. That may be the problem. I'm still somewhat familiar with the rest of the stuff you mentioned from my Windows days years ago, but a welcome refresher nonetheless. 

Stay tuned.
Thank you!
...Fred

---

### Post by atravnic on 2011-12-06
Can I direct the .iso file download, to, say, a usb stick instead of taking up space in my borrowed laptop?
...Fred

---

### Post by bcbc on 2011-12-06
Yes, you can save it on a USB stick.

---

### Post by atravnic on 2011-12-07
Let it run for over 20 minutes and still didn't get a match. I do have a broadband connection, but I'll try again and let run 30 or more minutes.

What disturbs me is that there is no indication that anything is happening. Should there be? Should I e seeing something?
...Fred

---

### Post by bcbc on 2011-12-08
> **atravnic said:**
> Let it run for over 20 minutes and still didn't get a match. I do have a broadband connection, but I'll try again and let run 30 or more minutes.

What disturbs me is that there is no indication that anything is happening. Should there be? Should I e seeing something?
...Fred

What browser are you using? If you were using IE you first click on the big download box, then it prompts you what to do (click save), then it asks you where (select your usb drive), then it shows you the download progress until the end. See snaps.

---

### Post by atravnic on 2011-12-08
> **bcbc said:**
> What browser are you using? If you were using IE you first click on the big download box, then it prompts you what to do (click save), then it asks you where (select your usb drive), then it shows you the download progress until the end. See snaps.

Thank you for the screen shots. Alright, full disclosure: I don't use IE. I use Firefox. And this Pendrive/Universal installer thing may be rigged to work only with IE. So I'll break down and use IE.

However, before I commit heresy, are we on the same sheet? My point of departure is that Universal USB Installer pop-up window which asks which version of ubuntu I want to download, and, at the same time, and optionally, invites me to download the iso.

In the next step I'm instructed to "Select your ubuntu-11.10*.iso" by pressing the Browse button. And that, my friend, is the end of the road for me. After I do that, nothing happens.

Not sure if this has anything to do with IE vs Firefox, but I'll give it a shot.
...Fred

PS -- What software do you use for capturing and pasting screen shots?

---

### Post by bcbc on 2011-12-08
> **atravnic said:**
> Thank you for the screen shots. Alright, full disclosure: I don't use IE. I use Firefox. And this Pendrive/Universal installer thing may be rigged to work only with IE. So I'll break down and use IE.

However, before I commit heresy, are we on the same sheet? My point of departure is that Universal USB Installer pop-up window which asks which version of ubuntu I want to download, and, at the same time, and optionally, invites me to download the iso.

In the next step I'm instructed to "Select your ubuntu-11.10*.iso" by pressing the Browse button. And that, my friend, is the end of the road for me. After I do that, nothing happens.

Not sure if this has anything to do with IE vs Firefox, but I'll give it a shot.
...Fred

PS -- What software do you use for capturing and pasting screen shots?

I don't use IE either - I use Chrome. For screenshots I just use the snipping tool that comes with win7 or screenshot in ubuntu.

I haven't used the usb installer for a long time, so can't say whether it downloads or not. If you use firefox it should still prompt you what to do with it. This screenshot is from Ubuntu but running firefox under windows should be the same.

---

### Post by oldtimer7777 on 2011-12-09
> **bcbc said:**
> I don't use IE either - I use Chrome. For screenshots I just use the snipping tool that comes with win7 or screenshot in ubuntu.

I haven't used the usb installer for a long time, so can't say whether it downloads or not. If you use firefox it should still prompt you what to do with it. This screenshot is from Ubuntu but running firefox under windows should be the same.

Here is the guide for Ubuntu 11.10:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

You can download from other mirrors if your connection seems slow.  Links are provided in the walk-through.  Make sure you read it.

---

### Post by atravnic on 2011-12-10
> **oldtimer7777 said:**
> Here is the guide for Ubuntu 11.10:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

You can download from other mirrors if your connection seems slow.  Links are provided in the walk-through.  Make sure you read it.

Well hello there oldtimer! I'm an old timer myself (although, like Jack Benny, I'm perennially 35). I cut my baby teeth on IBM's 1401, writing code in SPS and operating system patches in machine language. Do I qualify?

But now to the business at hand. I was under the impression you HAD to use the Universal USB Installer because it contained some serious magic. If that's not the case, hell, I know how to download. It's been a while since I used DOS, though. I understand I need to format my USB drive for FAT16/FAT32. What's the command for that? And is there anything else I need to know about?

I did read your epistle back when you first posted to this (endless) thread, but I need to read it again. I chose to go with Ubuntu's recommendation instead, just seemed the safer thing to do.

Thanks for your advice and take care.
...Fred

---

### Post by atravnic on 2011-12-10
> **bcbc said:**
> I don't use IE either - I use Chrome. For screenshots I just use the snipping tool that comes with win7 or screenshot in ubuntu.

I haven't used the usb installer for a long time, so can't say whether it downloads or not. If you use firefox it should still prompt you what to do with it. This screenshot is from Ubuntu but running firefox under windows should be the same.

That screen shot you sent, that's exactly what I expected to happen, but it never did. So I suspect there is a bug in the usb installer.

How do you do your downloads and installs, and do you happen to know the DOS command for formatting a USB drive for FAT16/FAT 32? Probably "format" but what are the parameters?

Thank you!
...Fred

---

### Post by bcbc on 2011-12-10
You can format using gparted, or from the windows disk management console. For Vista/7 hit the windows key, type "Disk management" and it will pop a "Create and format disk partitions" entry at the top. Click that and it will open the Disk management console.
Just be careful what you format.

From command line on vista/7 I use diskpart (for more advanced partitioning) but I normally google a microsoft support site to find the correct instructions before using.

What I was saying about downloading is - I don't know if the universal installer downloads the ISO itself - it looks like it should from the screen shots, but why don't you just download the ISO right from the browser. I'm not entirely clear on whether you are using the browser or trying only from the Universal Installer.

---

### Post by atravnic on 2011-12-10
> **bcbc said:**
> You can format using gparted, or from the windows disk management console. For Vista/7 hit the windows key, type "Disk management" and it will pop a "Create and format disk partitions" entry at the top. Click that and it will open the Disk management console.
Just be careful what you format.

From command line on vista/7 I use diskpart (for more advanced partitioning) but I normally google a microsoft support site to find the correct instructions before using.

What I was saying about downloading is - I don't know if the universal installer downloads the ISO itself - it looks like it should from the screen shots, but why don't you just download the ISO right from the browser. I'm not entirely clear on whether you are using the browser or trying only from the Universal Installer.

So I have this brand new, never before used, virginal USB stick--in honor of 11.10-- and the formatting app warns me that "this is an active partition" and if I format it I'll lose all data. Does this mean it'll wipe out the header info and whatever else may be on there already, or is this a boiler plate warning and I can just go ahead? Also, the disk management window shows the stick as having the FAT32 file system. Does this mean it's already formatted?
Thank you!
...Fred

---

### Post by bcbc on 2011-12-11
> **atravnic said:**
> So I have this brand new, never before used, virginal USB stick--in honor of 11.10-- and the formatting app warns me that "this is an active partition" and if I format it I'll lose all data. Does this mean it'll wipe out the header info and whatever else may be on there already, or is this a boiler plate warning and I can just go ahead? Also, the disk management window shows the stick as having the FAT32 file system. Does this mean it's already formatted?
Thank you!
...Fred
It is standard to warn when formatting, for good reason. If it's already FAT32 then, yes, you probably don't have to. If you do, make sure you verify the size of the partition matches your USB stick.

---

### Post by atravnic on 2011-12-12
"...verify the size of the partition matches your USB stick." It's a 16GB stick. Do I get to select the size of the partition, and how big should I make it? 

So I'll go ahead and download 11.10 into it, and if something goes wrong I can always go back, format the stick and start over. Oui?

Thanks!
...Fred

---

### Post by bcbc on 2011-12-12
It won't hurt using the whole stick, but you should be fine creating a 1GB partition (you only need ~700MB for the ISO).

---

### Post by atravnic on 2011-12-16
Quick update: talked Canonical into sending me a free 11.10 CD; that'll avoid me having to use another's computer and possible complications. I'll keep you posted.
...Fred

---

### Post by atravnic on 2011-12-30
I hope your Christmas, or whatever you celebrate around this time, was good. We had house guests, so I took some time off. Meanwhile, the 11.10 disk from Canonical arrived, and I've started using it following westie457's suggestion to start a normal install and select "Something else" when asked where to install.

When you do that you get the "Installation type" screen with several choices. I assumed that /dev/sda7 / is the original partition, but I get the "No root file system defined" error message and it tells me to "[...] correct this problem from the partitioning menu."

This is where Linux once again leaves me in the dust. What, and where, is the partitioning menu, how do I get there, and how can I know for sure what my original partition is?

I appreciate any help you can give me.

...Fred

---

### Post by bcbc on 2011-12-30
Hi, Welcome back!

That error normally means you haven't assigned "/" as the mountpoint. See the screenshots from one of my previous posts [here]("http://ubuntuforums.org/showpost.php?p=11513217&postcount=59") 

I don't think you've run the bootinfoscript. That's usually good at confirming which partition you want to be using. I think we spent more time looking at the reinstall rather than diagnosing the problem so that it was missed. But you backed up your /home from /dev/sda7 so it's likely the correct one. But why don't you download and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") anyway and post the results back here?

---

### Post by atravnic on 2011-12-30
The window you refer to "where you are choosing the partition to install to in the bottom right hand corner is a little box," doesn't have that little box. I wish I could send you a screen shot, but the install isn't far enough along to do that. It's also possible we're not on the same window, so let me briefly describe the window I'm on.

It's titled the "Installation type", has a multicolored space allocation bar across the top, lists partitions /dev/sda blank, 1, 7, 8, 5, 6, and 2. Then it shows a few function boxes: "New Partition Table..., Add, Change, Delete, Revert, and ends with a drop down table of "Device for boot loader installation", none of which includes "/", but it does list /dev/sda7 Ubuntu 11.10 (11.10) -- tempting. Howevere, I have not taken any action, and will contain myself until I hear back from you, or others.

Happy New Year!

...Fred

---

### Post by atravnic on 2011-12-30
Re: Upgrade 11.04 to 11.10 failed

The window you refer to "where you are choosing the partition to install to in the bottom right hand corner is a little box," doesn't have that little box. I wish I could send you a screen shot, but the install isn't far enough along to do that. It's also possible we're not on the same window, so let me briefly describe the window I'm on.

It's titled the "Installation type", has a multicolored space allocation bar across the top, lists partitions /dev/sda blank, 1, 7, 8, 5, 6, and 2. Then it shows a few function boxes: "New Partition Table..., Add, Change, Delete, Revert, and ends with a drop down table of "Device for boot loader installation", none of which includes "/", but it does list /dev/sda7 Ubuntu 11.10 (11.10) -- tempting. Howevere, I have not taken any action, and will contain myself until I hear back from you, or others.

Happy New Year!

...Fred

---

### Post by bcbc on 2011-12-31
So on that "installation type" screen, click on /dev/sda7, then click on "Change". That will popup a screen that you can select the Mountpoint from a drop down box - select "/". 

Make sure the "Format" checkbox is unchecked.
Also, you may need to specify the "Use as" - make sure it matches whatever file system is on /dev/sda7 (it shows you on the previous screen).

When you click OK at the bottom it will take you back to the "installation type" screen. The "device for the bootloader" should be /dev/sda (which is likely the default, so you probably don't have to change it).

Happy New Year!

---

### Post by atravnic on 2011-12-31
> **bcbc said:**
> So on that "installation type" screen, click on /dev/sda7, then click on "Change". That will popup a screen that you can select the Mountpoint from a drop down box - select "/". 

Make sure the "Format" checkbox is unchecked.
Also, you may need to specify the "Use as" - make sure it matches whatever file system is on /dev/sda7 (it shows you on the previous screen).

When you click OK at the bottom it will take you back to the "installation type" screen. The "device for the bootloader" should be /dev/sda (which is likely the default, so you probably don't have to change it).

Happy New Year!

Good thing one of us has an intact memory. I had completely forgotten that you had sent me screen shots a while ago of precisely that "Installation Type" screen and what to do. But your instructions were also great.

So the installation went beautifully and it popped up my old desk top at the end, a good sign. There is a little hitch though: my curser is frozen. So I can't verify that the rest of the data made it across, nor poke around to check on functions (e.g., not sure I can go on-line). Got any ideas how to "liberate"/jail-break the curser?

If you have any plans for tonight I hope you have a really good time. And if you're like me, I'll probably turn in well before midnight and feel good in the morning.

Thanks for staying involved. You've been a tremendous help.

...Fred

---

### Post by atravnic on 2011-12-31
I'll run the *bootinfoscript *as soon as I'm fully operational.

---

### Post by bcbc on 2011-12-31
> **atravnic said:**
> Good thing one of us has an intact memory. I had completely forgotten that you had sent me screen shots a while ago of precisely that "Installation Type" screen and what to do. But your instructions were also great.

So the installation went beautifully and it popped up my old desk top at the end, a good sign. There is a little hitch though: my curser is frozen. So I can't verify that the rest of the data made it across, nor poke around to check on functions (e.g., not sure I can go on-line). Got any ideas how to "liberate"/jail-break the curser?

If you have any plans for tonight I hope you have a really good time. And if you're like me, I'll probably turn in well before midnight and feel good in the morning.

Thanks for staying involved. You've been a tremendous help.

...Fred
Is it just your cursor frozen - is it always frozen or it just freezes after a while? Does your keyboard work e.g. if you hit Ctrl-Alt-T do you get to a terminal?

There are many reports of cursors freezing in 11.10, but I'm not sure your issue matches the problem as described.

If, when you log in, you select the 2D unity (click the 'cog' on the logon screen and select unity 2d), does that also freeze?

What computer brand/model do you have?

---

### Post by atravnic on 2011-12-31
> **bcbc said:**
> Is it just your cursor frozen - is it always frozen or it just freezes after a while? Does your keyboard work e.g. if you hit Ctrl-Alt-T do you get to a terminal?

There are many reports of cursors freezing in 11.10, but I'm not sure your issue matches the problem as described.

If, when you log in, you select the 2D unity (click the 'cog' on the logon screen and select unity 2d), does that also freeze?

What computer brand/model do you have?

The cursor is frozen right from the start, and the keyboard also doesn't work, i.e., no luck getting a terminal session. The only time the keyboard did work was in the grub menu and it's subfunctions. 

Finally, what's a 'cog'? If it's something I need to get to in order to click on, I won't be able to do that once I'm on the login screen since neither cursor nor keyboard are responding at that point.

I'm using a two-year old HP Pavillion tx2500 laptop running on an AMD Turion X2, ATI Radeon graphics card and a WACOM pen screen/tablet. The comm board is Broadcom, can't remember the model, and Altec something or other. I have the specs stored on, you guessed it, my inaccessible laptop. What sweet irony.

Hope this helps.

...Fred

---

### Post by bcbc on 2011-12-31
The 'cog' is the little cogwheel icon on the signon screen to the right of the password box. 

If the 2d Unity login doesn't work you could try using 'nomodeset' as a boot option. That might stop the freezing and you can then look for a custom driver for your card
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Otherwise we can pick this up in the new year!

---

### Post by atravnic on 2011-12-31
> **bcbc said:**
> The 'cog' is the little cogwheel icon on the signon screen to the right of the password box. 

If the 2d Unity login doesn't work you could try using 'nomodeset' as a boot option. That might stop the freezing and you can then look for a custom driver for your card
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Otherwise we can pick this up in the new year!

Good idea! Let's pick it up in 2012. Happy New Year! Catch you later.    ...Fred

---

### Post by atravnic on 2012-01-03
I hope you survived your entry into 2012.

What you suggested would probably work--thanks for telling me what a cog is, it's always the little things that trip you up--except for that annoying little detail that my darn cursor won't budge and therefore I have no way to get to that cog. Infuriating, isn't it!?!

...Fred

---

### Post by bcbc on 2012-01-03
Okay, when your computer boots you should see the Grub menu. If not, hold the SHIFT key as it boots.

Then press 'e' on the keyboard (the first entry in the menu should be highlighted and pressing 'e' will allow you to edit it).
Using the arrow keys, navigate to where it says 'quiet splash' and add 'nomodeset'. Don't add the quotes so it will look like this:
quiet splash nomodeset

Then hold down the Ctrl key and hit X to boot.

If you manage to get through the login this time, then run the 'additional-drivers' to see if there is something for your graphics card.
Hopefully that works better. I'm not sure why you'd be having graphic card issues with 11.10 but not 11.04 though...

---

### Post by atravnic on 2012-01-03
> **bcbc said:**
> Okay, when your computer boots you should see the Grub menu. If not, hold the SHIFT key as it boots.

Then press 'e' on the keyboard (the first entry in the menu should be highlighted and pressing 'e' will allow you to edit it).
Using the arrow keys, navigate to where it says 'quiet splash' and add 'nomodeset'. Don't add the quotes so it will look like this:
quiet splash nomodeset

Then hold down the Ctrl key and hit X to boot.

If you manage to get through the login this time, then run the 'additional-drivers' to see if there is something for your graphics card.
Hopefully that works better. I'm not sure why you'd be having graphic card issues with 11.10 but not 11.04 though...

This is weird. Same result as before: frozen cursor and neither the keyboard nor the pen work. Not to be redundant, but I'm able to login and the desktop loads, but that's all.

---

### Post by bcbc on 2012-01-03
I thought you were freezing at the login... maybe you're thinking of a different 'cog' - the one on the desktop. This is what I mean. Your popup menu should look a little different, just "Ubuntu" and "Ubuntu 2D". Pick the 2D and see if that freezes.

Otherwise... not sure what to suggest. Maybe drop to a terminal Ctrl+Alt+F1 and run to get all the latest 11.10 updates:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by atravnic on 2012-01-03
> **bcbc said:**
> I thought you were freezing at the login... maybe you're thinking of a different 'cog' - the one on the desktop. This is what I mean. Your popup menu should look a little different, just "Ubuntu" and "Ubuntu 2D". Pick the 2D and see if that freezes.

Otherwise... not sure what to suggest. Maybe drop to a terminal Ctrl+Alt+F1 and run to get all the latest 11.10 updates:
```
sudo apt-get update
sudo apt-get upgrade
```

Yes, the cursor is frozen from the moment it appears, and that's why I can't get to the cog that you showed in the attached screen shot. And after I included nomodeset in the first line of the grub menu nothing different happened.

I will run the updates tomorrow and keep my fingers crossed.

Thank you!

...Fred

---

### Post by bcbc on 2012-01-04
Ah, so the keyboard isn't frozen on the signon screen, just the mouse, and after logging in both freeze... frustrating.

I'm not doing too well on this one ;) Maybe someone else has some ideas? I suppose there could be something in your /home directory that's causing issues. When you boot from the CD in live mode (select "Try Ubuntu" without installing), do you have any issues getting to the live desktop?

---

### Post by atravnic on 2012-01-04
> **bcbc said:**
> Ah, so the keyboard isn't frozen on the signon screen, just the mouse, and after logging in both freeze... frustrating.

I'm not doing too well on this one ;) Maybe someone else has some ideas? I suppose there could be something in your /home directory that's causing issues. When you boot from the CD in live mode (select "Try Ubuntu" without installing), do you have any issues getting to the live desktop?

I'm afraid I inadvertently misled you. Sorry! Yes, the keyboard, at the login screen, is okay.

So I tried logging in again--knowing how devious technology can be--same result: frozen cursor. Then I took a shot at ctrl-alt-f1, and voila, the keyboard still works. But the result was weird. I got a mishmash of icons with text overlaying the desktop, and the text is rendered in illegible dots and the mass of icons shows all in lines. 

I can't tell if the cursor is still there, would be hard to find in this mess. I didn't detect any movement, and the keyboard doesn't seem to respond either. So I can't run the updates.

Graphics problem?

Meanwhile, I'll do the "Try" thing, and will let you know what happens.

Thanks!

...Fred

---

### Post by atravnic on 2012-01-04
The "Try" option seems to be alive and well, cursor and keyboard are functioning and everything seems normal. (However, I can't get a network connection (running a wireless Cisco router and a Broadcom comms board). But I've had this problem several times before, and that's for another day.)

So you may be on to something suspecting the /home directory. How in hell do you debug that? And running a normal, clean install that wipes everything out and importing the backup won't solve anything. It'll just roll the problem back in.

I need a miracle.

...Fred

---

### Post by bcbc on 2012-01-04
Maybe try resetting Unity and compiz... you'll lose any desktop customization etc.

[http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration](http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration)

To summarise, hit Ctrl+Alt+F1, and run:
```
unity --reset
```
I'd restart to check if it workedL
```
sudo reboot
```

If that doesn't work, this website also shows how to reset compiz settings:
[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)

---

### Post by atravnic on 2012-01-04
> **bcbc said:**
> Maybe try resetting Unity and compiz... you'll lose any desktop customization etc.

[http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration](http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration)

To summarise, hit Ctrl+Alt+F1, and run:
```
unity --reset
```
I'd restart to check if it workedL
```
sudo reboot
```

If that doesn't work, this website also shows how to reset compiz settings:
[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)

I have tried cntrl-alt-f1 from the desktop and from the login screen, and each time I get the same mess I described above and I can't do anything. I even tried to "intercept" a mythical point where I could slip in the terminal multi-punch right up to the login screen, no luck. Bottom line: the way 11.10 is installed, I can't do anything unless I can open a terminal session. 

Is there any other way to get into unity and compiz? Isn't this stuff written in C++? Does Canonical provide the source code? There must be some C++ programmers on these forums.

Or what do you think of re-installing (using westi457's technique)?

If I lived in Vancouver, I'd say let's go out and get drunk.

Thank you!

...Fred

---

### Post by bcbc on 2012-01-05
> **atravnic said:**
> I have tried cntrl-alt-f1 from the desktop and from the login screen, and each time I get the same mess I described above and I can't do anything. I even tried to "intercept" a mythical point where I could slip in the terminal multi-punch right up to the login screen, no luck. Bottom line: the way 11.10 is installed, I can't do anything unless I can open a terminal session. 

Is there any other way to get into unity and compiz? Isn't this stuff written in C++? Does Canonical provide the source code? There must be some C++ programmers on these forums.

Or what do you think of re-installing (using westi457's technique)?

If I lived in Vancouver, I'd say let's go out and get drunk.

Thank you!

...Fred

I think that reinstalling with the non-reformat option likely will result in the same issue. Reinstalling fresh will probably work fine, but then you have to restore your data from the backup you made, which is a bit of work.

I've been trying to figure out how to reset unity (unity --reset) without running unity - but it doesn't work from a recovery prompt unfortunately. I found a link that looked promising but when I tried it in my virtual install, it was fatal ;) 

I wonder whether you should create a question on askubuntu.com - there are a lot of experts there, and provided you focus just on the current issue you might get some good help. (Many devs seem to monitor askubuntu.com)

e.g. something like:
Question title: Unity freezing on login. How to reset? 

Question text:
Upgrade from 11.04 to 11.10 failed. Reinstalled 11.10 without formatting. Appears that config files in /home are breaking Unity (because it runs fine from a live CD). Cannot run 'unity --reset' as the graphics corrupt, the mouse freezes and it appears the keyboard is frozen as well. How can I repair this from recovery mode?

Tags: unity

---

### Post by atravnic on 2012-01-05
> **bcbc said:**
> I think that reinstalling with the non-reformat option likely will result in the same issue. Reinstalling fresh will probably work fine, but then you have to restore your data from the backup you made, which is a bit of work.

I've been trying to figure out how to reset unity (unity --reset) without running unity - but it doesn't work from a recovery prompt unfortunately. I found a link that looked promising but when I tried it in my virtual install, it was fatal ;) 

I wonder whether you should create a question on askubuntu.com - there are a lot of experts there, and provided you focus just on the current issue you might get some good help. (Many devs seem to monitor askubuntu.com)

e.g. something like:
Question title: Unity freezing on login. How to reset? 

Question text:
Upgrade from 11.04 to 11.10 failed. Reinstalled 11.10 without formatting. Appears that config files in /home are breaking Unity (because it runs fine from a live CD). Cannot run 'unity --reset' as the graphics corrupt, the mouse freezes and it appears the keyboard is frozen as well. How can I repair this from recovery mode?

Tags: unity

Please don't do anything that's gonna cause you problems. It's enough that I have them, and I don't want you to curse the day you first responded to my question. 

I will post on askubuntu using the question as you phrased it, and thank you so much for writing it for me. I would have been far more verbose for one. Of course that's provided I would know what to focus on which is highly unlikely.

Is unity a standard file with standard content that comes with every install, or is it a system file that captures certain user data and therefore ends up being unique?  Where I'm going with that is, can a standard copy of unity be used to overlay the defective one, either in the computer or in the backup? It gets around the problem of not being able to initiate a terminal session--and therefore not being able to execute sudo apt-get update and sudo apt-get upgrade--and also doesn't require a comm link.

Another thought is to use the "Try" mode and use terminal to  repair unity on my backup, then do a clean install and roll the data in from the backup with a good copy of unity. 

Thank you again, and again! :D

...Fred

---

### Post by imachavel on 2012-01-05
> **mörgæs said:**
> You can not roll back to 11.04. If you want this one back, a fresh install is the only way - and a fresh install is also the best option, if you want 11.10 :-)

More advice in the link in my signature.

no kidding. Amazing. upgrades that fail SUCK! Thought linux didn't mess up as often the way windows upgrades mess up every time.

---

### Post by bcbc on 2012-01-07
> **atravnic said:**
> Please don't do anything that's gonna cause you problems. It's enough that I have them, and I don't want you to curse the day you first responded to my question. 

I will post on askubuntu using the question as you phrased it, and thank you so much for writing it for me. I would have been far more verbose for one. Of course that's provided I would know what to focus on which is highly unlikely.

Is unity a standard file with standard content that comes with every install, or is it a system file that captures certain user data and therefore ends up being unique?  Where I'm going with that is, can a standard copy of unity be used to overlay the defective one, either in the computer or in the backup? It gets around the problem of not being able to initiate a terminal session--and therefore not being able to execute sudo apt-get update and sudo apt-get upgrade--and also doesn't require a comm link.

Another thought is to use the "Try" mode and use terminal to  repair unity on my backup, then do a clean install and roll the data in from the backup with a good copy of unity. 

Thank you again, and again! :D

...Fred

Don't worry about my installs. I have a script that synchs a copy that I can play around with them ;)

So, I saw your request and the comment lead to [this post]("http://askubuntu.com/questions/56313/how-do-i-reset-gnome-to-the-defaults"). So I ran a test on it from recovery mode (similar to what you'll have to do). And it worked for me. So if you want to try it, this is what I did.

1. Boot and select Recovery mode (2nd entry)
2. If this leads to the 'read only recovery menu' select option 3 to remount read/write. Then select the 'root terminal' (last option). 
If it leads you straight to a root prompt, then continue.
3. Change to your /home directory:
```
cd /home/atravnic
```
4. Enter the following command...:
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails .config/dconf/user .compiz*

```
5. reboot 
```
reboot
```

Please note that the rm -rf command is extremely dangerous. If you make a simple typo you can delete everything on your partition. Make sure you're in your home directory, and type it carefully (you have to type it because you can't copy and paste in a recovery mode terminal).

Alternatively, you could do it from a live CD by mounting /dev/sda7 first. Then you can copy and paste:
```
sudo mount /dev/sda7 /mnt
cd /mnt/home/atravnic
sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails .config/dconf/user .compiz*
```

Again, please take care with that **rm** command.

---

### Post by atravnic on 2012-01-08
> **imachavel said:**
> no kidding. Amazing. upgrades that fail SUCK! Thought linux didn't mess up as often the way windows upgrades mess up every time.

IMHO, it's not Linux that's screwing up, it's Canonical for releasing beta-level software, thereby shifting the costly debugging function to the Ubuntu user community. But in all fairness you have to factor in that Ubuntu is an outstanding OS that costs nothing. Personally, although frustrated at times, I have not regretted the agony of trying and failing. On the contrary, I have learned a lot from it.

Not trying to offend you, imachavel, just trying to keep things in perspective. Also want to point out that my contact with Canonical has been nothing but positive. They understood my frustration and bent over backwards to be supportive.

Finally, I switched to Ubuntu 5 years ago,and in spite of all the problems, I have never looked back. And this is largely due to the unselfish support of the Ubuntu user community.

Good luck my friend!

...Fred

---

### Post by atravnic on 2012-01-08
> **bcbc said:**
> Don't worry about my installs. I have a script that synchs a copy that I can play around with them ;)

So, I saw your request and the comment lead to [this post]("http://askubuntu.com/questions/56313/how-do-i-reset-gnome-to-the-defaults"). So I ran a test on it from recovery mode (similar to what you'll have to do). And it worked for me. So if you want to try it, this is what I did.

1. Boot and select Recovery mode (2nd entry)
2. If this leads to the 'read only recovery menu' select option 3 to remount read/write. Then select the 'root terminal' (last option). 
If it leads you straight to a root prompt, then continue.
3. Change to your /home directory:
```
cd /home/atravnic
```
4. Enter the following command...:
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails .config/dconf/user .compiz*

```
5. reboot 
```
reboot
```

Please note that the rm -rf command is extremely dangerous. If you make a simple typo you can delete everything on your partition. Make sure you're in your home directory, and type it carefully (you have to type it because you can't copy and paste in a recovery mode terminal).

Alternatively, you could do it from a live CD by mounting /dev/sda7 first. Then you can copy and paste:
```
sudo mount /dev/sda7 /mnt
cd /mnt/home/atravnic
sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails .config/dconf/user .compiz*
```

Again, please take care with that **rm** command.

Good news and bad news. I survived the treacherousness and unspeakable horrors of the rm -rf command and booted up just fine (desktop icons are a tad more scattered but everything is clean.

Bad news, I still can't move the cursor.

Then I tried nomodeset. No help there, but when I pressed ctrl x to reboot it sounded a penetrating alarm but went ahead with the boot anyway.

Finally, I tried to plunge into the netherworld of alt-ctrl-f1. Big Oops. Same messed up desktop as the last time I tried it, and neither cursor nor terminal anywhere. 

This is beginning to stretch into eternity. And you know about eternity, don't you. It's an awfully long time, especially toward the end.

Thank you!

...Fred

---

### Post by atravnic on 2012-01-08
Went through some old posts on this thread and re-read Afrodeity's stuff:

Post 15: First time this has ever happened with an online upgrade. System totally failed to come up. Usually there are one or two problems with graphics issues, but this has something to do with the new 3.0 kernel. Got exactly the same error system bus error.

Post 17: I used a liveCD to chroot into the system. Then I installed linux-generic and booted with this kernel in recovery mode, since the kernel which was installed with the online upgrade is the pae kernel.

I now get to a root prompt.

It appears there is a problem with the dbus-daemon and changing into runlevel 3 <telinit 3) fails.

I have also tried dpkg-reconfigure -a

Will see what more I can do.

I found this tutorial on solving the waiting for network configuration boot freeze.

After getting to a / prompt, I could telinit to 3 and reinstalled the Nvidia Driver, which I had installed manually. I was also able to reboot and log into a GDM session.

However, to get network services, I needed to sudo dhclient eth0, so there a few other problems, including unity quitting frequently. I am in the process of reinstalling unity.

Code:

gconftool-2 --recursive-unset /apps/compiz-1 unity --reset

did the trick 

................................................................

I stayed away from it because it seemed too difficult for me at the time. I'm more comfortable with it now. Your thoughts.

...Fred

---

### Post by bcbc on 2012-01-08
I think, by reinstalling you probably removed the need for most of that. If you had wanted to repair your upgrade you could have tried chroot'ing and trying to complete it.

You've already reset everything to do with gnome/unity, so the only thing I think might do it for you is:
```
sudo dpkg-reconfigure -a
```

Other than that, I think you're probably at the point where a complete reinstall is worth it. You've got your backup so it might be the quickest.

---

### Post by atravnic on 2012-01-08
> **bcbc said:**
> I think, by reinstalling you probably removed the need for most of that. If you had wanted to repair your upgrade you could have tried chroot'ing and trying to complete it.

You've already reset everything to do with gnome/unity, so the only thing I think might do it for you is:
```
sudo dpkg-reconfigure -a
```

Other than that, I think you're probably at the point where a complete reinstall is worth it. You've got your backup so it might be the quickest.

But how can I do that? I'm back to a frozen cursor and unable to access terminal. Should I use "Try" mode?

---

### Post by bcbc on 2012-01-08
> **atravnic said:**
> But how can I do that? I'm back to a frozen cursor and unable to access terminal. Should I use "Try" mode?

From a root terminal (recovery mode). As before make sure your drives are mounted read/write. You can drop the 'sudo' from the root terminal.

You'll get a whole bunch of prompts that you can probably leave as default. TAB to navigate between buttons etc.

---

### Post by atravnic on 2012-01-08
> **bcbc said:**
> From a root terminal (recovery mode). As before make sure your drives are mounted read/write. You can drop the 'sudo' from the root terminal.

You'll get a whole bunch of prompts that you can probably leave as default. TAB to navigate between buttons etc.

Before I go ahead, it would help to know what dpkg-reconfigure -a does. Also, do I need to change to /home/atravnic for this.

So here, abbreviated, is what I will do:
go into recovery mode
select remount read/write
select root terminal
cd /home/atravnic
dpkg-reconfigure -a

And then what? Reboot?

Finally, you said: "Other than that, I think you're probably at the point where a complete reinstall is worth it. You've got your backup so it might be the quickest." True, but the backup hasn't been changed, only my home folder on the hard drive. Do I need to do another backup to make sure both files are identical in case something ever should go wrong?

Thank you!

...Fred

---

### Post by bcbc on 2012-01-08
It reconfigures installed packages - the -a switch tells it to do all of them. So the idea is that something has a setting which is causing an issue, and by reconfiguring the affected package it removes the aberrant setting.

[http://manpages.ubuntu.com/manpages/oneiric/man8/dpkg-reconfigure.8.html](http://manpages.ubuntu.com/manpages/oneiric/man8/dpkg-reconfigure.8.html)

You don't have to be in your home directory for this. Some of the stuff won't make much sense (a lot really) so my advice is to accept the defaults in those cases.

After that you can 'exit' or 'reboot'.

I'm not sure about the backup. You backed up /home but since there is something in /home that's causing problems you don't want to restore everything in that back up. You could selectively restore data instead.

---

### Post by atravnic on 2012-01-08
> **bcbc said:**
> It reconfigures installed packages - the -a switch tells it to do all of them. So the idea is that something has a setting which is causing an issue, and by reconfiguring the affected package it removes the aberrant setting.

[http://manpages.ubuntu.com/manpages/oneiric/man8/dpkg-reconfigure.8.html](http://manpages.ubuntu.com/manpages/oneiric/man8/dpkg-reconfigure.8.html)

You don't have to be in your home directory for this. Some of the stuff won't make much sense (a lot really) so my advice is to accept the defaults in those cases.

After that you can 'exit' or 'reboot'.

I'm not sure about the backup. You backed up /home but since there is something in /home that's causing problems you don't want to restore everything in that back up. You could selectively restore data instead.

Got some errors.
[  118.057137] Ext4-fs (sda7) : re-mounted. Opts: errors=remount-ro,commit=0
a second error followed identical to the preceding except for [118.325419]
and then, at the Terminal Font screen, this was a show stopper:
error:could not identify the package root@atravnic-HP-Pavillion-tx2500-Notebook-PC:~#

Needless to say, cursor, etc., continue to be comfortably numb.

Is there a way to print out a directory (not the content, just the table of contents). I'm getting ready to ask you to help me identify any files other then data files that are important.

Thank you! 

...Fred

---

### Post by bcbc on 2012-01-09
> **atravnic said:**
> Got some errors.
[  118.057137] Ext4-fs (sda7) : re-mounted. Opts: errors=remount-ro,commit=0
a second error followed identical to the preceding except for [118.325419]
and then, at the Terminal Font screen, this was a show stopper:
error:could not identify the package root@atravnic-HP-Pavillion-tx2500-Notebook-PC:~#

Needless to say, cursor, etc., continue to be comfortably numb.

Is there a way to print out a directory (not the content, just the table of contents). I'm getting ready to ask you to help me identify any files other then data files that are important.

Thank you! 

...Fred
Can you run fsck from the recovery menu?

Re. backups, I thought you had backed up all your data already.

---

### Post by atravnic on 2012-01-09
> **bcbc said:**
> Can you run fsck from the recovery menu?

Re. backups, I thought you had backed up all your data already.

Ran fsck (see errors below), then normal boot. No luck--don't know if I should have expected anything--frozen cursor, etc.

I do indeed have all my data backed up. What did I say to bring up that question? If I do a clean install, it's more then data I need to retrieve from back up, right?!? Files like networking, Firefox, settings, etc. Am I making a wrong assumption?

Depending on how many files are corrupted, might it be quicker to restore the entire backup and then delete the offending files?

Error following fsck.
[  17.468492] Adding 1317292 swap on /dev/sda8. Priority: 1 across: 1317292k

/dev/sda7: 164173/1839600 files (0.3% non-contiguous), 1762158/7353738 blocks

[25.709792] EXT4-fs: re-mounted, Opts: error=remount-ro

Thank you!

...Fred

---

### Post by bcbc on 2012-01-09
Okay I misunderstood. You're referring to deciding which files to restore from backup - I thought you were talking about backing up again (which didn't make sense, which is why I mentioned it).

I don't know an easy way to accomplish this other than by looking at each applications settings and identifying where they are stored. So for firefox it's in your /home directory under .mozilla/firefox/...  

I wonder whether you should zip your logs and post them - maybe that will have some clues as to what is hanging. To do this, boot the live CD, then:
```
sudo mount /dev/sda7 /mnt
sudo zip -r logs /mnt/var/log

```

and attach logs.zip from the /home/ubuntu folder before rebooting. Or if you just want to attach the /var/log/dmesg and /var/log/syslog then that should be enough I guess.
```
sudo zip  logs /mnt/var/log/syslog /mnt/var/log/dmesg
```

---

### Post by atravnic on 2012-01-09
> **bcbc said:**
> Okay I misunderstood. You're referring to deciding which files to restore from backup - I thought you were talking about backing up again (which didn't make sense, which is why I mentioned it).

I don't know an easy way to accomplish this other than by looking at each applications settings and identifying where they are stored. So for firefox it's in your /home directory under .mozilla/firefox/...  

I wonder whether you should zip your logs and post them - maybe that will have some clues as to what is hanging. To do this, boot the live CD, then:
```
sudo mount /dev/sda7 /mnt
sudo zip -r logs /mnt/var/log

```

and attach logs.zip from the /home/ubuntu folder before rebooting. Or if you just want to attach the /var/log/dmesg and /var/log/syslog then that should be enough I guess.
```
sudo zip  logs /mnt/var/log/syslog /mnt/var/log/dmesg
```

Infuriating as it is, I still have to chuckle about the occasionally blunt error messages. Here's what I got after I executed the zip command: "zip error: Nothing to do! (try zip -r logs . -i /mnt/var/logs)

Should I?

BTW, it took me almost an hour to find how to attach a file. Kinda proud of myself, for once I did my own research.

...Fred

---

### Post by bcbc on 2012-01-09
> **atravnic said:**
> Infuriating as it is, I still have to chuckle about the occasionally blunt error messages. Here's what I got after I executed the zip command: "zip error: Nothing to do! (try zip -r logs . -i /mnt/var/logs)

Should I?

BTW, it took me almost an hour to find how to attach a file. Kinda proud of myself, for once I did my own research.

...Fred
:) that research will speed up after a while

I think you probably just have to change /mnt/var/logs to /mnt/var/log to get it to work.

```
sudo zip -r logs /mnt/var/log
```

---

### Post by atravnic on 2012-01-10
> **bcbc said:**
> :) that research will speed up after a while

I think you probably just have to change /mnt/var/logs to /mnt/var/log to get it to work.

```
sudo zip -r logs /mnt/var/log
```

Ran your log script last night using LiveCD "Try" mode and ctrl-alt-f1 to open terminal. Everything ran great, lots of output, except alt-E and C didn't work, nor able to find /home/ubuntu. In fact, I was stuck in terminal mode, didn't know how to get out, so I finally just pulled the plug and went to bed. So I have nothing for you to look at.

Is ctrl-alt-f1 legal only in recovery mode? And was I in the wrong place for alt-E and C? Went back into LiveCD today but couldn't find a way to get terminal, nor find any traces of what I did last night. I'll happily rerun everything if you can figure out what genius over here is doing wrong this time.
 
Thank!  

...Fred

---

### Post by bcbc on 2012-01-10
Boot the live CD to the desktop. Go to a terminal (Ctrl+Alt+T). Mount the partition, zip the logs. Type 'exit' to get back to the desktop.

Attach the file to your forum post from /home/ubuntu/logs.zip.

If you reboot the zip file will no longer be there.

---

### Post by atravnic on 2012-01-10
> **bcbc said:**
> Boot the live CD to the desktop. Go to a terminal (Ctrl+Alt+T). Mount the partition, zip the logs. Type 'exit' to get back to the desktop.

Attach the file to your forum post from /home/ubuntu/logs.zip.

If you reboot the zip file will no longer be there.

Ah yes, 'exit', of course. Shoulda known.

Logs file attached. Hope it worked, didn't check. Didn't want to mess anything up.

Well, I spoke too soon: "logs.zip: Your file of 1.32 MB bytes exceeds the forum's limit of 976.6 KB for this filetype." What do you suggest? Segmenting? Printing it to a file and copy/pasting it directly into a message? E-mail it to you?

I have it on a usb stick (it's the only way I can get it from my computer to the one I'm using).

...Fred

---

### Post by bcbc on 2012-01-10
You could open the zip file and delete a bunch of stuff. Just make sure you leave syslog and dmesg. Copy the whole thing first beforehand just in case.

---

### Post by atravnic on 2012-01-10
> **bcbc said:**
> You could open the zip file and delete a bunch of stuff. Just make sure you leave syslog and dmesg. Copy the whole thing first beforehand just in case.

Here we go again. Don't know where it is but it looked like it went. Let me know. Thanks! ...Fred

---

### Post by bcbc on 2012-01-11
Please can I have the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") results as well please.

Thanks

It looks like you have a 9.10 install on /dev/sda5, 11.10 on /dev/sda7 and swap on /dev/sda8 and Windows on /dev/sda2 but there are a few strange bits I'd like to check.

---

### Post by atravnic on 2012-01-11
> **bcbc said:**
> Please can I have the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") results as well please.

Thanks

It looks like you have a 9.10 install on /dev/sda5, 11.10 on /dev/sda7 and swap on /dev/sda8 and Windows on /dev/sda2 but there are a few strange bits I'd like to check.

Since, for some obscure reason, I cannot get online from my laptop, I would have to use the loaner laptop, a Windows machine which is online, to download bootinfoscript and save it to my usb stick, and run it on my laptop and save the results to the usb stick for sneaker net style transport. Do you see a problem with that?

As far as 9.10, swap, and Windows are concerned, that can all go. Do you know how to delete stuff like that?

Thanks!

...Fred

---

### Post by bcbc on 2012-01-11
> **atravnic said:**
> Since, for some obscure reason, I cannot get online from my laptop, I would have to use the loaner laptop, a Windows machine which is online, to download bootinfoscript and save it to my usb stick, and run it on my laptop and save the results to the usb stick for sneaker net style transport. Do you see a problem with that?

As far as 9.10, swap, and Windows are concerned, that can all go. Do you know how to delete stuff like that?

Thanks!

...Fred
When you reinstall, you just tell the installer to select the entire drive - it will remove all those partitions and create a huge /dev/sda1 for Ubuntu and an extended /dev/sda2 with a single /dev/sda5 for swap. You can take control of this yourself if you want a different setup e.g. separate /home etc. But letting the installer do it is the easiest.

Since it looks like you're going to have to reinstall from scratch, that makes the most sense. Just ensure that any data on those old Windows/9.10 partitions has been backed up.

PS yes copying the bootinfoscript between computers will work fine.

---

### Post by atravnic on 2012-01-11
> **bcbc said:**
> When you reinstall, you just tell the installer to select the entire drive - it will remove all those partitions and create a huge /dev/sda1 for Ubuntu and an extended /dev/sda2 with a single /dev/sda5 for swap. You can take control of this yourself if you want a different setup e.g. separate /home etc. But letting the installer do it is the easiest.

Since it looks like you're going to have to reinstall from scratch, that makes the most sense. Just ensure that any data on those old Windows/9.10 partitions has been backed up.

PS yes copying the bootinfoscript between computers will work fine.

Ah the vicissitudes of being a Linux guy. It means I can ask dumb questions. So here's one. I have bootinfoscript on my usb stick, I have booted to the desktop with LiveCD. Do I need to extract (need detailed instruction), install on my hard drive, how do I execute bootinfoscript and how do I direct the output to the usb stick. I know this is basic stuff, unfortunately that's where I'm at -- which you surely know by now (haha).

Thank you!

...Fred

---

### Post by bcbc on 2012-01-12
Boot to live CD desktop, plug in USB. Should autopop nautilus file browser. Right click on bootinfoscript.sh (or the .zip file if not extracted) and select "Copy to" then "Home".

Then if it's the zip, click on Home (top left of nautilus window, under Computer) and right click on the .zip and "Extract Here". Then enter the boot_info_script060 folder and right click on bootinfoscript.sh and select "Move to" "Home".

Then drop to the terminal Ctrl+Alt+T and run:
```
sudo bash bootinfoscript.sh
exit
```

Now you should see it in the Home directory, right click on the RESULTS.txt file, select 'Copy', and then click on the original USB partition, and 'Paste' it somewhere.

That's about it - more or less.

---

### Post by atravnic on 2012-01-12
> **bcbc said:**
> Boot to live CD desktop, plug in USB. Should autopop nautilus file browser. Right click on bootinfoscript.sh (or the .zip file if not extracted) and select "Copy to" then "Home".

Then if it's the zip, click on Home (top left of nautilus window, under Computer) and right click on the .zip and "Extract Here". Then enter the boot_info_script060 folder and right click on bootinfoscript.sh and select "Move to" "Home".

Then drop to the terminal Ctrl+Alt+T and run:
```
sudo bash bootinfoscript.sh
exit
```

Now you should see it in the Home directory, right click on the RESULTS.txt file, select 'Copy', and then click on the original USB partition, and 'Paste' it somewhere.

That's about it - more or less.

"More or less", eh! Thanks for the warning. Got some stuff to take care of, so I'll do it later. Thanks!   ...Fred

---

### Post by atravnic on 2012-01-12
> **atravnic said:**
> "More or less", eh! Thanks for the warning. Got some stuff to take care of, so I'll do it later. Thanks!   ...Fred

It didn't go as anticipated, but I experimented and maybe you got some usable results.

One more thing, I'm sick and tired of the Forums ridiculous and unrealistic limits on attachment. 19.5 KB is absurd. So here is the results page. Hope it all helps.       ...Fred

...............................................................

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /ubuntu/winboot/menu.lst /bootmgr /boot/bcd 
                       /Windows/System32/winload.exe /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'swsuspend'

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.72 2008-09-25
    Boot sector info:   Syslinux looks at sector 265090 of /dev/sdc1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   242,308,394   242,308,332   7 NTFS / exFAT / HPFS
/dev/sda2         468,482,048   488,390,655    19,908,608   7 NTFS / exFAT / HPFS
/dev/sda3         242,308,519   468,471,464   226,162,946   f W95 Extended (LBA)
/dev/sda5         303,773,148   461,675,969   157,902,822  83 Linux
/dev/sda6         461,676,033   468,471,464     6,795,432  82 Linux swap / Solaris
/dev/sda7         242,308,521   301,138,424    58,829,904  83 Linux
/dev/sda8         301,138,488   303,773,084     2,634,597  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4110 MB, 4110228480 bytes
16 heads, 63 sectors/track, 7964 cylinders, total 8027790 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     8,027,789     8,027,727   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        046BD50C3577B5FA                       ntfs       
/dev/sda2        D2360C62360C49C5                       ntfs       HP_RECOVERY
/dev/sda5        ca3f8b0b-b77f-46e3-9e48-1fbd64f64729   ext4       
/dev/sda6        8d190093-de3c-46a4-99f1-d078b7467ed9   swsuspend  
/dev/sda7        1adba56a-e24d-4c56-abd8-5952dc041706   ext4       
/dev/sda8        91554091-d7fd-4c7e-8455-83bf370a0a7a   swap       
/dev/sdc1        134A-02C0                              vfat       CRUZER 4 GB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/CRUZER 4 GB       vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== sda1/ubuntu/winboot/menu.lst: =========================

--------------------------------------------------------------------------------
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set ca3f8b0b-b77f-46e3-9e48-1fbd64f64729
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ca3f8b0b-b77f-46e3-9e48-1fbd64f64729
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=ca3f8b0b-b77f-46e3-9e48-1fbd64f64729 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ca3f8b0b-b77f-46e3-9e48-1fbd64f64729
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=ca3f8b0b-b77f-46e3-9e48-1fbd64f64729 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ca3f8b0b-b77f-46e3-9e48-1fbd64f64729
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ca3f8b0b-b77f-46e3-9e48-1fbd64f64729 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ca3f8b0b-b77f-46e3-9e48-1fbd64f64729
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ca3f8b0b-b77f-46e3-9e48-1fbd64f64729 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 046bd50c3577b5fa
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d2360c62360c49c5
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 1adba56a-e24d-4c56-abd8-5952dc041706
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=1adba56a-e24d-4c56-abd8-5952dc041706 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 1adba56a-e24d-4c56-abd8-5952dc041706
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=1adba56a-e24d-4c56-abd8-5952dc041706 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ca3f8b0b-b77f-46e3-9e48-1fbd64f64729 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8d190093-de3c-46a4-99f1-d078b7467ed9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.31-14-generic              1
               =                boot/initrd.img-2.6.31-17-generic              2
               =                boot/vmlinuz-2.6.31-14-generic                 1
               =                boot/vmlinuz-2.6.31-17-generic                 1
               =                initrd.img                                     2
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=========================== sda7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 1adba56a-e24d-4c56-abd8-5952dc041706
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root 1adba56a-e24d-4c56-abd8-5952dc041706
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 1adba56a-e24d-4c56-abd8-5952dc041706
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=1adba56a-e24d-4c56-abd8-5952dc041706 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 1adba56a-e24d-4c56-abd8-5952dc041706
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=1adba56a-e24d-4c56-abd8-5952dc041706 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 1adba56a-e24d-4c56-abd8-5952dc041706
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=1adba56a-e24d-4c56-abd8-5952dc041706 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 1adba56a-e24d-4c56-abd8-5952dc041706
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=1adba56a-e24d-4c56-abd8-5952dc041706 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 1adba56a-e24d-4c56-abd8-5952dc041706
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=1adba56a-e24d-4c56-abd8-5952dc041706 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 1adba56a-e24d-4c56-abd8-5952dc041706
	echo	'Loading Linux 2.6.38-12-generic ...'
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=1adba56a-e24d-4c56-abd8-5952dc041706 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 1adba56a-e24d-4c56-abd8-5952dc041706
	linux	/boot/vmlinuz-2.6.32-34-generic root=UUID=1adba56a-e24d-4c56-abd8-5952dc041706 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 1adba56a-e24d-4c56-abd8-5952dc041706
	echo	'Loading Linux 2.6.32-34-generic ...'
	linux	/boot/vmlinuz-2.6.32-34-generic root=UUID=1adba56a-e24d-4c56-abd8-5952dc041706 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 1adba56a-e24d-4c56-abd8-5952dc041706
	linux	/boot/vmlinuz-2.6.31-23-generic root=UUID=1adba56a-e24d-4c56-abd8-5952dc041706 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.31-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 1adba56a-e24d-4c56-abd8-5952dc041706
	echo	'Loading Linux 2.6.31-23-generic ...'
	linux	/boot/vmlinuz-2.6.31-23-generic root=UUID=1adba56a-e24d-4c56-abd8-5952dc041706 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 1adba56a-e24d-4c56-abd8-5952dc041706
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 1adba56a-e24d-4c56-abd8-5952dc041706
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 046BD50C3577B5FA
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root D2360C62360C49C5
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root ca3f8b0b-b77f-46e3-9e48-1fbd64f64729
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=ca3f8b0b-b77f-46e3-9e48-1fbd64f64729 ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root ca3f8b0b-b77f-46e3-9e48-1fbd64f64729
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=ca3f8b0b-b77f-46e3-9e48-1fbd64f64729 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root ca3f8b0b-b77f-46e3-9e48-1fbd64f64729
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ca3f8b0b-b77f-46e3-9e48-1fbd64f64729 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root ca3f8b0b-b77f-46e3-9e48-1fbd64f64729
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ca3f8b0b-b77f-46e3-9e48-1fbd64f64729 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=1adba56a-e24d-4c56-abd8-5952dc041706 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=91554091-d7fd-4c7e-8455-83bf370a0a7a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.31-23-generic              1
               =                boot/initrd.img-2.6.32-34-generic              2
               =                boot/initrd.img-2.6.38-12-generic              3
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/initrd.img-3.0.0-13-generic               4
               =                boot/vmlinuz-2.6.31-23-generic                 1
               =                boot/vmlinuz-2.6.32-34-generic                 1
               =                boot/vmlinuz-2.6.38-12-generic                 2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic                  1
               =                initrd.img                                     3
               =                vmlinuz                                        1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             vesamenu.c32                                   1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 vesamenu.c32                       :  COM32R module (v3.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  32 0b d2 24 79 85 ed d7  b1 54 8d 79 f0 cd 47 e1  |2..$y....T.y..G.|
00000010  ce af 8d 7e 93 0d 76 e5  7c f2 32 27 c0 d9 ec 0a  |...~..v.|.2'....|
00000020  0f ef 78 9c 67 9d 16 44  af 60 c2 99 89 0b d1 12  |..x.g..D.`......|
00000030  66 c6 c2 78 22 aa a4 22  0b 4b 6e 9b a1 68 53 f4  |f..x"..".Kn..hS.|
00000040  ac 63 e4 1f d7 79 0b 13  49 57 06 9b 29 6d 71 e2  |.c...y..IW..)mq.|
00000050  b5 b2 6c 6c 5f ea da e6  45 41 ca b9 aa 9a 51 e2  |..ll_...EA....Q.|
00000060  0b 59 47 30 25 15 06 22  50 30 55 d3 ca d0 17 4d  |.YG0%.."P0U....M|
00000070  16 0b 8d d6 e6 6f 01 9e  82 3b 47 97 c2 d2 8d 65  |.....o...;G....e|
00000080  07 b7 ce ff fd a5 46 ba  48 27 b6 d4 f0 f9 5f 2d  |......F.H'...._-|
00000090  91 7a 71 a5 0e c1 c5 d7  21 99 79 18 2d e9 bf 7e  |.zq.....!.y.-..~|
000000a0  81 1d d0 b2 dd ea 7e f2  91 f3 ae ea b7 ba 63 f3  |......~.......c.|
000000b0  1f c2 e1 ad 3c eb 3c 7e  ef bb 33 0f 17 33 33 60  |....<.<~..3..33`|
000000c0  1d 07 8b c3 1a 51 3e 32  8e 0e 28 d6 b7 69 f9 32  |.....Q>2..(..i.2|
000000d0  90 3e 59 04 b5 6b 56 47  f1 e0 bd 15 e0 78 05 3f  |.>Y..kVG.....x.?|
000000e0  93 2a 30 05 b1 e3 e4 97  ad 7c e7 a5 57 57 65 ee  |.*0......|..WWe.|
000000f0  bb ca 93 d0 2d 83 87 c7  b8 a8 42 ef de 07 a0 d8  |....-.....B.....|
00000100  94 30 ef 8a c0 20 5c d4  15 40 3e ba a7 04 68 1c  |.0... \..@>...h.|
00000110  f8 01 a2 df 72 e3 ef 19  94 60 5a 2d bc 22 da fe  |....r....`Z-."..|
00000120  47 91 bb 48 f7 03 c0 12  69 5d f7 1b cb 71 6f e8  |G..H....i]...qo.|
00000130  29 10 33 70 65 d5 9e df  6f f8 b3 25 1c 10 5a 8e  |).3pe...o..%..Z.|
00000140  31 1c 8a e2 a1 b3 e4 6a  52 51 cd ea 77 e7 d7 d1  |1......jRQ..w...|
00000150  15 d3 ca 53 70 64 e2 76  ed fe ae 51 0b 34 d5 03  |...Spd.v...Q.4..|
00000160  03 5b b0 cb db 9e 0f 28  22 c6 56 14 48 bd 58 85  |.[.....(".V.H.X.|
00000170  8c 86 ca 48 91 84 04 f3  de 45 fa 17 88 44 d7 32  |...H.....E...D.2|
00000180  10 dd 70 a8 69 b1 7d 84  b4 a3 90 b9 96 4b ae 14  |..p.i.}......K..|
00000190  09 b6 a9 ef d7 49 2a 32  4e 21 d7 91 25 16 f5 33  |.....I*2N!..%..3|
000001a0  59 5c a4 c2 65 52 2f 5f  f5 2d ec ed 59 58 e4 4c  |Y\..eR/_.-..YX.L|
000001b0  0c 2b de 3a 9d 04 90 a9  75 41 32 98 ef 68 00 fe  |.+.:....uA2..h..|
000001c0  ff ff 83 fe ff ff 35 e0  a9 03 e6 67 69 09 00 fe  |......5....gi...|
000001d0  ff ff 05 fe ff ff 1b 48  13 0d e7 b0 67 00 00 00  |.......H....g...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

### Post by bcbc on 2012-01-13
Okay that looks good. It looks like your final act on the /dev/sda5 karmic install was to hibernate it.

You're losing use of most of your hard drive when you use just the /dev/sda7 install - unless you were mounting other partitions from it. So you should check it to make sure there is no data you need to backup if you reinstall over the whole drive. (Because you only backed up your /home on /dev/sda7 and I would assume you must have data on /dev/sda1 and /dev/sda5 as well.)

It's a little bit frustrating (a lot for you I guess) that it's taken a long time and I'm sure it would have been easier to just sit down at the computer. But I think at this point a reinstall makes sense.

---

### Post by atravnic on 2012-01-13
> **bcbc said:**
> Okay that looks good. It looks like your final act on the /dev/sda5 karmic install was to hibernate it.

You're losing use of most of your hard drive when you use just the /dev/sda7 install - unless you were mounting other partitions from it. So you should check it to make sure there is no data you need to backup if you reinstall over the whole drive. (Because you only backed up your /home on /dev/sda7 and I would assume you must have data on /dev/sda1 and /dev/sda5 as well.)

It's a little bit frustrating (a lot for you I guess) that it's taken a long time and I'm sure it would have been easier to just sit down at the computer. But I think at this point a reinstall makes sense.

So the dreaded moment is upon me: clean install. But before I bungee jump off that bridge I wanted to close the loop on a few things. 

My final act on the /dev/sda5 karmic install was to hibernate it. My good man/woman, you're giving me far, far more credit than I deserve. This act of hibernation was neither willfull nor premeditated. I am assuredly not responsible for it. It must have been cosmic intervention that guided my hand. What I would like to understand is what it means, and can I be the prince charming who awakens this sleep beauty with some dazzling display of Linux magic?

You said you found " [..] a few strange bits [you'd] like to check out". What did you find and what does it mean? A related question, what did you find in the /home directory that was causing problems? Also, you indicated that "It looks like you have a 9.10 install on /dev/sda5, 11.10 on /dev/sda7 and swap on /dev/sda8 and Windows on /dev/sda2 but there are a few strange bits I'd like to check". The wider question of course is, are there any corrupted files I should avoid entirely and what are they?

What did analysis of the bootinfoscript results tell you?

Finally, whatever you advise me to do, factor in that I will be installing Windows again so I can run in dual boot mode. Meanwhile, I will be checking /home/sda7, 1 and 5 (any others?) for any stranded data. And if you think of anything else I should do, please, by all means tell me.

Thanks again!!!

...Fred

---

### Post by bcbc on 2012-01-14
The bootinfoscript gives some specific information about your installs and their setup, but doesn't answer the sorts of questions you're asking i.e. what's wrong in your /home directory.

It does show that you had karmic (9.10) on /dev/sda5 and it's swap was /dev/sda6 which I had noticed had a hibernated image (from one of the logs). It shows that your main windows partition is /dev/sda1, but doesn't show any reason why it wouldn't boot. What happens when you try?

Or for that matter if you try booting the /dev/sda5 install?

I'm not sure what I was expecting with the reinstall you did, but it looks like you have kernels from 9.10 throught to 11.10. What happens if you boot the 2.6.38 kernel for instance (under 'Previous versions')?

Anyway - that's all interesting, but it might be a waste of your time to keep playing with it. If you're planning to reinstall Windows as well as Ubuntu, then it's better to install Windows first - you can just let it install over the whole hard drive. Then you can refer to this guide to install Ubuntu after that:[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html) (it's written for 10.10 but most of it should be spot on for 11.10 - and a lot of time and attention to detail went into it).

As I said, mount the /dev/sda1 and /dev/sda5 partition and pull any data you need off it first.

---

### Post by atravnic on 2012-01-15
> **bcbc said:**
> The bootinfoscript gives some specific information about your installs and their setup, but doesn't answer the sorts of questions you're asking i.e. what's wrong in your /home directory.

It does show that you had karmic (9.10) on /dev/sda5 and it's swap was /dev/sda6 which I had noticed had a hibernated image (from one of the logs). It shows that your main windows partition is /dev/sda1, but doesn't show any reason why it wouldn't boot. What happens when you try?

Or for that matter if you try booting the /dev/sda5 install?

I'm not sure what I was expecting with the reinstall you did, but it looks like you have kernels from 9.10 throught to 11.10. What happens if you boot the 2.6.38 kernel for instance (under 'Previous versions')?

Anyway - that's all interesting, but it might be a waste of your time to keep playing with it. If you're planning to reinstall Windows as well as Ubuntu, then it's better to install Windows first - you can just let it install over the whole hard drive. Then you can refer to this guide to install Ubuntu after that:[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html) (it's written for 10.10 but most of it should be spot on for 11.10 - and a lot of time and attention to detail went into it).

As I said, mount the /dev/sda1 and /dev/sda5 partition and pull any data you need off it first.

I share your frustation not having found why the cusor hangs. You put so much time and effort into this, you went way beyond what most people do. I truely thank you with all my heart. You have been a teacher and a friend.

Change of subject. I can't get an Internet connection when I run 11.10 in "Try" mode. What's the likelihoood of this resolving itself when I do a full install? Not great I imagine. If it comes down to it, is this an issue I should post on a different forum?

Where do you go to get your Windows questions answered? 

Also, since I'm in no particular hurry to buy and load Windows, so, unless there is a really compelling reason to load it first, how much of a disadvantage is it to load 11.10 first and Windows later? And do you know of a guide to install 11.10?

Well, that's enough questions. Take care.

...Fred

---

### Post by atravnic on 2012-01-15
Sorry, but I do have one more question. Should Canonical be apprised of this cursor/keyboard problem? If someone as knowledgeable as you can't find it, it seems they should be getting to work on it.

I imagine by now they already know about the 11.04 to 11.10 upgrade problem (which is what started this journey in the first place).

...Fred

---

### Post by bcbc on 2012-01-16
> **atravnic said:**
> Sorry, but I do have one more question. Should Canonical be apprised of this cursor/keyboard problem? If someone as knowledgeable as you can't find it, it seems they should be getting to work on it.

I imagine by now they already know about the 11.04 to 11.10 upgrade problem (which is what started this journey in the first place).

...Fred

During the development cycle a lot of people (some anyway) test upgrades - I did a few myself - and report bugs etc. if things go wrong. But despite that there are always failures for various reasons. I doubt that they spend much time after a release looking into it (that's my impression) because they're diving in to the work for the next release. But for sure, unless there's a bug report with attached logs they aren't looking at it.
I do think it's a problem that for many users, they get caught up in the rolling releases and if the upgrade does fail there is no easy recovery. Hopefully there'll be a solution, or at least a big warning recommending to backup beforehand would be nice. 

The thing with the cursor/keyboard freezing - since it's not happening on the live CD it's probably a by-product of the failed upgrade - and so they're probably not aware of it either. 

I'm not big on networking problem solving - you should definitely take a look in the [Networking and wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") subforum as they have some stickies for trouble shooting.

Regarding installing Windows first or second, it's definitely easier installing it first. I'd caution that it's not easy to install Windows (not like Ubuntu) unless you have all the drivers you need. I tend to just use the Windows that comes preinstalled - but the last time I reinstalled it was a real pain. And I'm not sure where you go for help with Windows issues - or to be more precise, I don't know what the best place is, I just search on google if I need help.
So, if you can get your current Windows working or boot the 'restore' partition (/dev/sda2) it might be easier than reinstalling fresh (otherwise make sure you have the drivers).

Anyway... I think you've been quite a trouper working through your issues. You're giving me a little too much credit for helping: at the end of the day you've had to do the work... and there's still a fair amount there. (Probably if I was in your shoes I would have dropped the computer off at my local computer tech store - it's good to learn, but at the end of the day the computer (and operating system) should just work, not be the work).

---

### Post by atravnic on 2012-01-16
Thank you for your detailed message, will respond later.

Quick question. I should know this, but you have filled my brain with so much, it's all a bit of a jumble. Trying to scour sda1, 5 and 7 for stray data and can't remember how to load the correct directory. From LiveCD I got a terminal and did sudo mount /dev/sda1 /mnt, but don't remember how to bring up the table of contents. I expected Nautilus to pop up the file browser, but I guess even 11.10 can't do magic - yet.    ...Fred

---

### Post by bcbc on 2012-01-17
> **atravnic said:**
> Thank you for your detailed message, will respond later.

Quick question. I should know this, but you have filled my brain with so much, it's all a bit of a jumble. Trying to scour sda1, 5 and 7 for stray data and can't remember how to load the correct directory. From LiveCD I got a terminal and did sudo mount /dev/sda1 /mnt, but don't remember how to bring up the table of contents. I expected Nautilus to pop up the file browser, but I guess even 11.10 can't do magic - yet.    ...Fred

There is a setting whether to 'autopop' on mount. Not sure what it defaults to on the live CD or whether there are exclusions. Anyway, just enter:
```
nautilus /mnt
```

If you open nautilus, you should see the partitions listed by either size or label. Since /dev/sda1 and /dev/sda5 don't have labels they'll show up by size. Then you can click on them, which mounts and browses in a single step.

---

### Post by pinkfab4 on 2012-01-17
> **atravnic said:**
> Hi folks -- I can see from the threads here I'm not the only one having 11.10 upgrade problems. 

My attempt to upgrade terminated abnormally. When I reboot it takes me as far as "waiting for network config" followed by "booting without full network configuration" and hangs there. When I boot into safe made, I get "unable to connect to system bus: failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused". 

I'm running an HP Pavilion tx 2500 laptop; AMD Turion X2 Dual Core; and an ST9250827 AS hard drive.

Is there a way to walk the upgrade back to 11.04? Can I start the upgrade over from scratch? Is there a work-around (anything to get me out Vista (I'm dual booted))? Can I go out and get drunk now? What if any help does Canonical offer?

I sure would appreciate your help. Thank you so much!   ...Fred

I wasted a lot of time etc., downloading in attempt at 11.10 with graphics. Go to terminal  where people mean business.  sudo do-release-upgrade-d

If that doesn't click! delete the -d at the end

---

### Post by mörgæs on 2012-01-17
Thanks for contributing, but please read the latest 3-4 pages (at least) before posting.

---

### Post by atravnic on 2012-01-17
> **bcbc said:**
> There is a setting whether to 'autopop' on mount. Not sure what it defaults to on the live CD or whether there are exclusions. Anyway, just enter:
```
nautilus /mnt
```

If you open nautilus, you should see the partitions listed by either size or label. Since /dev/sda1 and /dev/sda5 don't have labels they'll show up by size. Then you can click on them, which mounts and browses in a single step.

What's the official Forum allotment for dumb questions? I'm sure I must have passed the max a long time ago. But I'll take another chance. 

Okay, the file browser came up as expected and it shows in the upper left corner under "Devices" 124GB, 81GB and 30GB Filesystem. Clicking on each shows a very similar file structure and everything has a name. So how do I know if and when I'm in dev/sda1 or whichever?

Pinkfab4's sudo ```
do-release-upgrade-d
``` suggestion sounds like an upgrade fix. I might try it--waddaya think?--I've tried everything else.

Thanks!

...Fred

---

### Post by atravnic on 2012-01-17
> **bcbc said:**
> During the development cycle a lot of people (some anyway) test upgrades - I did a few myself - and report bugs etc. if things go wrong. But despite that there are always failures for various reasons. I doubt that they spend much time after a release looking into it (that's my impression) because they're diving in to the work for the next release. But for sure, unless there's a bug report with attached logs they aren't looking at it.
I do think it's a problem that for many users, they get caught up in the rolling releases and if the upgrade does fail there is no easy recovery. Hopefully there'll be a solution, or at least a big warning recommending to backup beforehand would be nice. 

The thing with the cursor/keyboard freezing - since it's not happening on the live CD it's probably a by-product of the failed upgrade - and so they're probably not aware of it either. 

I'm not big on networking problem solving - you should definitely take a look in the [Networking and wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") subforum as they have some stickies for trouble shooting.

Regarding installing Windows first or second, it's definitely easier installing it first. I'd caution that it's not easy to install Windows (not like Ubuntu) unless you have all the drivers you need. I tend to just use the Windows that comes preinstalled - but the last time I reinstalled it was a real pain. And I'm not sure where you go for help with Windows issues - or to be more precise, I don't know what the best place is, I just search on google if I need help.
So, if you can get your current Windows working or boot the 'restore' partition (/dev/sda2) it might be easier than reinstalling fresh (otherwise make sure you have the drivers).

Anyway... I think you've been quite a trouper working through your issues. You're giving me a little too much credit for helping: at the end of the day you've had to do the work... and there's still a fair amount there. (Probably if I was in your shoes I would have dropped the computer off at my local computer tech store - it's good to learn, but at the end of the day the computer (and operating system) should just work, not be the work).


How about an even bigger warning: "The software in this release has not been fully tested and is currently in beta release only. Use at your own discretion. If you encounter problems, recovery may be difficult or impossible." It's not fair for them to oil the marketing gears and lure unsuspecting users into using software in good faith that is nowhere near ready for prime time. I don't think they're a bad company, they just do dumb and inconsiderate things.

Looked back at some of my older posts and was reminded that I had had the very same network problem for the last three upgrades. So I know what to do: activate the Broadcom STA driver. (Ask me why that's not done as part of an upgrade/install as soon as Ubuntu sees the comm board.)

You made a good point, and a timely reminder, that Windows is a pain to install. Of course my HP laptop came with it installed. And then something happened and it crashed. I'll make a feeble effort to resurrect it. If that turns out to be too onerous, I may just get one of the low-end pad thingies so I'll have a fallback. Of course if I start fiddling around with Windows now, it'll delay installing 11.10 even more. But it may be worth it in terms of pain (Windows pain) avoidance. (How do I boot the 'restore' partition (/dev/sda2)?)

Thanks for classifying me as a trooper. Nice compliment. I learned a lot. That made it worthwhile, and your patience with a neophyte like me.

I'm sure we'll be talking again sooner or later -- maybe sooner (haha).

Hang in there, and thanks again!

...Fred

---

### Post by bcbc on 2012-01-17
> **atravnic said:**
> How about an even bigger warning: "The software in this release has not been fully tested and is currently in beta release only. Use at your own discretion. If you encounter problems, recovery may be difficult or impossible." It's not fair for them to oil the marketing gears and lure unsuspecting users into using software in good faith that is nowhere near ready for prime time. I don't think they're a bad company, they just do dumb and inconsiderate things.

Looked back at some of my older posts and was reminded that I had had the very same network problem for the last three upgrades. So I know what to do: activate the Broadcom STA driver. (Ask me why that's not done as part of an upgrade/install as soon as Ubuntu sees the comm board.)

You made a good point, and a timely reminder, that Windows is a pain to install. Of course my HP laptop came with it installed. And then something happened and it crashed. I'll make a feeble effort to resurrect it. If that turns out to be too onerous, I may just get one of the low-end pad thingies so I'll have a fallback. Of course if I start fiddling around with Windows now, it'll delay installing 11.10 even more. But it may be worth it in terms of pain (Windows pain) avoidance. (How do I boot the 'restore' partition (/dev/sda2)?)

Thanks for classifying me as a trooper. Nice compliment. I learned a lot. That made it worthwhile, and your patience with a neophyte like me.

I'm sure we'll be talking again sooner or later -- maybe sooner (haha).

Hang in there, and thanks again!

...Fred

The release cycle is so tight with 6month releases. I don't think it's possible to get it right with such a major update. It's actually better to stick with the LTS and upgrade every 2 - 3 years unless you like adventure. 

So... when you boot from the hard drive, you should get a grub menu and at the bottom there is the option to boot Windows on /dev/sda1 and Windows on /dev/sda2. The second one looks like the recovery. You shouldn't attempt this before you've made sure you've backed up your data. Also, often these recovery setups don't work so well if you've repartitioned, so it might not work - or it could restore the entire computer. (i.e. I really have no idea what's going to happen).

Re. an earlier post of yours, I believe the 120GB is /dev/sda1, the 80GB is /dev/sda5 and the 30GB should be /dev/sda7. I haven't done an exact calc, but looks right.

---

### Post by atravnic on 2012-01-22
Hi there --
Succeeded in saving Vista from a gruesome death under the bus, so now it's on to 11.10. In other words, Vista is up and running again. So, any last words of advice before I jump?   ...Fred

---

### Post by bcbc on 2012-01-23
> **atravnic said:**
> Hi there --
Succeeded in saving Vista from a gruesome death under the bus, so now it's on to 11.10. In other words, Vista is up and running again. So, any last words of advice before I jump?   ...Fred

I guess it depends how you got Vista running - did you restore it? repartition? etc.

If it's the same as before (same partitions), then you can boot to a live desktop from the install CD, run GParted, and delete your linux and swap partitions, then kickoff the installer and let it use the free space. Or if you prefer a finer control and want to make sure your swap is big enough (in order to hibernate) you could choose 'Something else' and create new partitions in that space.

If you restored your computer so it only has windows, then you will probably need to shrink the windows partition using the windows Disk Management console (or let Ubuntu do it when you install).

Best if you report back with specifics if you're not sure.

---

### Post by atravnic on 2012-01-23
> **bcbc said:**
> I guess it depends how you got Vista running - did you restore it? repartition? etc.

If it's the same as before (same partitions), then you can boot to a live desktop from the install CD, run GParted, and delete your linux and swap partitions, then kickoff the installer and let it use the free space. Or if you prefer a finer control and want to make sure your swap is big enough (in order to hibernate) you could choose 'Something else' and create new partitions in that space.

If you restored your computer so it only has windows, then you will probably need to shrink the windows partition using the windows Disk Management console (or let Ubuntu do it when you install).

Best if you report back with specifics if you're not sure.

I recreated the corrupted profile. That's not a restore, I guess? And my guess is the partitions are the same as before, too, since I didn't touch them.

The installer knows best, not planning on getting fancy with partitions. Ditto for letting Ubuntu shrink the Windows partition.

Let's keep our fingers crossed.     ...Fred

---

### Post by bcbc on 2012-01-23
> **atravnic said:**
> I recreated the corrupted profile. That's not a restore, I guess? And my guess is the partitions are the same as before, too, since I didn't touch them.

The installer knows best, not planning on getting fancy with partitions. Ditto for letting Ubuntu shrink the Windows partition.

Let's keep our fingers crossed.     ...Fred

Well, the installer might get confused. And you don't need a third swap partition. 

Since you want to replace the /dev/sda5 and the /dev/sda7 install and you don't need two swaps, I would recommend booting to the live desktop, running GParted and removing all of these, then creating a new ext4 partition in the space, and a single swap that is equal to the size of your RAM + half a GB (or + 1 GB if it's low, e.g. 1GB ram = 2GB swap). That way you'll be able to hibernate. Then install and manually select the new partition as "/".

---

### Post by atravnic on 2012-01-23
> **bcbc said:**
> Well, the installer might get confused. And you don't need a third swap partition. 

Since you want to replace the /dev/sda5 and the /dev/sda7 install and you don't need two swaps, I would recommend booting to the live desktop, running GParted and removing all of these, then creating a new ext4 partition in the space, and a single swap that is equal to the size of your RAM + half a GB (or + 1 GB if it's low, e.g. 1GB ram = 2GB swap). That way you'll be able to hibernate. Then install and manually select the new partition as "/".

Stated the install and am sitting on the Install Ubuntu alongside them window, it's showing me 42.5 GB for sda5 (ext4) and 38.4 GB for sda6 (ext4). At Advanced partitioning I get for sda1 124061 (ntsf), sda7 (ext4) 30120 MB, sda8 swap 1348 MB, sda5 (ext4) 80846 MB, and sda6 wassup 3479 MB.

Question, should I abort installation now with no harm and do what you suggest first?

What do I call the new ext4 partition and is there a cool way to look up how much RAM I have? And how do I manually select the new partition?

Thanks.

...Fred

---

### Post by atravnic on 2012-01-23
> **bcbc said:**
> Well, the installer might get confused. And you don't need a third swap partition. 

Since you want to replace the /dev/sda5 and the /dev/sda7 install and you don't need two swaps, I would recommend booting to the live desktop, running GParted and removing all of these, then creating a new ext4 partition in the space, and a single swap that is equal to the size of your RAM + half a GB (or + 1 GB if it's low, e.g. 1GB ram = 2GB swap). That way you'll be able to hibernate. Then install and manually select the new partition as "/".

Stated the install and am sitting on the Install Ubuntu alongside them window, it's showing me 42.5 GB for sda5 (ext4) and 38.4 GB for sda6 (ext4). At Advanced partitioning I get for sda1 124061 (ntsf), sda7 (ext4) 30120 MB, sda8 swap 1348 MB, sda5 (ext4) 80846 MB, and sda6 wassup 3479 MB.

Question, should I abort installation now with no harm and do what you suggest first?

What do I call the new ext4 partition and is there a cool way to look up how much RAM I have? And how do I manually select the new partition?

Thanks.

...Fred

---

### Post by bcbc on 2012-01-23
You've done nothing yet, so aborting the install shouldn't be a problem. But once you start deleting partitions you'll have an issue booting, because the grub2 bootloader is looking for /dev/sda7 and without that you won't boot (anything). It's easy enough to replace a bootloader, but why go through the hassle.

So it's best to know what you are going to do, before you start.

You can check the size of your ram with the 'free -m' command or using the 'system monitor' (from desktop hit launcher key and enter 
system monitor' to find it).

---

### Post by atravnic on 2012-01-23
> **bcbc said:**
> You've done nothing yet, so aborting the install shouldn't be a problem. But once you start deleting partitions you'll have an issue booting, because the grub2 bootloader is looking for /dev/sda7 and without that you won't boot (anything). It's easy enough to replace a bootloader, but why go through the hassle.

So it's best to know what you are going to do, before you start.

You can check the size of your ram with the 'free -m' command or using the 'system monitor' (from desktop hit launcher key and enter 
system monitor' to find it).

Confused again! Should I or should I not delete sda7? I'm hearing both. And that is further complicated by the fact that I do indeed NOT know what I need to do. (If you don't know where you're going, any road will get you there -- how I wish that were true.)

Help. And thank you!

...Fred

---

### Post by bcbc on 2012-01-23
> **atravnic said:**
> Confused again! Should I or should I not delete sda7? I'm hearing both. And that is further complicated by the fact that I do indeed NOT know what I need to do. (If you don't know where you're going, any road will get you there -- how I wish that were true.)

Help. And thank you!

...Fred

What do you want to do? I though you decided a fresh install was what you want. That would imply replacing the current (/dev/sda7) install. And since you don't want the old 9.10 install (on /dev/sda5) or it's related swap (/dev/sda6) you can delete those.
So, it makes sense to me that you would delete /dev/sda5, 6, 7, and 8 and recreate a new /dev/sda5 for root (/) and /dev/sda6 for swap.

Ultimately you need to decide what to do. If you wanted to keep /dev/sda7 you could instead install to /dev/sda5 (it's bigger than /dev/sda7). I don't know why you would, but you could.

---

### Post by atravnic on 2012-01-23
> **bcbc said:**
> What do you want to do? I though you decided a fresh install was what you want. That would imply replacing the current (/dev/sda7) install. And since you don't want the old 9.10 install (on /dev/sda5) or it's related swap (/dev/sda6) you can delete those.
So, it makes sense to me that you would delete /dev/sda5, 6, 7, and 8 and recreate a new /dev/sda5 for root (/) and /dev/sda6 for swap.

Ultimately you need to decide what to do. If you wanted to keep /dev/sda7 you could instead install to /dev/sda5 (it's bigger than /dev/sda7). I don't know why you would, but you could.

Ah, now I understand your question. You're raising issues I wouldn't necessarily think of, so this is good. Yes, I want to clean up the disk environment.

But what confused me, and still does, is this statement of yours: "But once you start deleting partitions you'll have an issue booting, because **the grub2 bootloader is looking for /dev/sda7 and without that you won't boot (anything)**. It's easy enough to replace a bootloader, but why go through the hassle." So what do you think I should do with sda7?

I imagine recreating sda5 and 6 is part of the partitioning process and there is no esoteric code I need to know?!?

Thank you!          ...Fred

---

### Post by atravnic on 2012-01-23
Sorry I'm taking so much of your time, and, by extension, other people's time who need your help!!!!

---

### Post by bcbc on 2012-01-23
> **atravnic said:**
> Ah, now I understand your question. You're raising issues I wouldn't necessarily think of, so this is good. Yes, I want to clean up the disk environment.

But what confused me, and still does, is this statement of yours: "But once you start deleting partitions you'll have an issue booting, because **the grub2 bootloader is looking for /dev/sda7 and without that you won't boot (anything)**. It's easy enough to replace a bootloader, but why go through the hassle." So what do you think I should do with sda7?

I imagine recreating sda5 and 6 is part of the partitioning process and there is no esoteric code I need to know?!?

Thank you!          ...Fred

Right - the point I was making is that once you delete the /dev/sda7 or start repartitioning, you should follow through with the install. During the install it will set up the bootloader again and make sure it's pointing to the new ubuntu partition. So that was just a warning to make sure you're ready to follow through with the install (it's not a big deal to setup a new windows bootloader on a temp basis, but it saves you some more hassle - and you've had your fair share already).


> **atravnic said:**
> Sorry I'm taking so much of your time, and, by extension, other people's time who need your help!!!!
I honestly don't think I am spending as much time as you think I am but you're welcome :) and it has no relation to the help I give others (or don't give). The forum works on an ad-hoc basis and there are many, many people that help, so it's not dependent on anyone.

---

### Post by atravnic on 2012-01-25
Attached is what free -m produced. It's an .odt file and I couldn't find anything in Vista that would read it. Also, somewhere in the specs for my laptop I found that it came with 3GB of RAM. That seems like a lot to reserve.

Just wanted to confirm that the 120GB is /dev/sda1, the 80GB is /dev/sda5 and the 30GB should be /dev/sda7. And again to confirm, I should delete sda5, 6, 7, and 8. Correcto? How do I find sda6 and 8?

Finally, what's the best way to delete these partitions?

As always, thank you!

...Fred

---

### Post by bcbc on 2012-01-26
> **atravnic said:**
> Attached is what free -m produced. It's an .odt file and I couldn't find anything in Vista that would read it. Also, somewhere in the specs for my laptop I found that it came with 3GB of RAM. That seems like a lot to reserve.

Just wanted to confirm that the 120GB is /dev/sda1, the 80GB is /dev/sda5 and the 30GB should be /dev/sda7. And again to confirm, I should delete sda5, 6, 7, and 8. Correcto? How do I find sda6 and 8?

Finally, what's the best way to delete these partitions?

As always, thank you!

...Fred

Yes you have 3GB of RAM. While it seems like a lot to have a 3.5GB swap partition, I wouldn't sweat it. If you know you're never going to hibernate, you can make it less. (You already have 3.5GB space for that old swap you never use).

You have (approx): 
/dev/sda1 = 124GB windows
/dev/sda2 = 10GB windows recovery
/dev/sda5 = 80GB ubuntu 9.10
/dev/sda6 = 3.5GB swap
/dev/sda7 = 30GB ubuntu 11.10
/dev/sda8 = 1.4 GB swap

To delete partitions you can boot from the Ubuntu CD to the live desktop, and run GParted. Then select the partitions you want to delete (all the logicals) and then recreate two logicals, one for swap and one for root (the rest of the space).

I attached a snap of what gparted looks like on my drive.

---

### Post by atravnic on 2012-01-26
> **bcbc said:**
> Yes you have 3GB of RAM. While it seems like a lot to have a 3.5GB swap partition, I wouldn't sweat it. If you know you're never going to hibernate, you can make it less. (You already have 3.5GB space for that old swap you never use).

You have (approx): 
/dev/sda1 = 124GB windows
/dev/sda2 = 10GB windows recovery
/dev/sda5 = 80GB ubuntu 9.10
/dev/sda6 = 3.5GB swap
/dev/sda7 = 30GB ubuntu 11.10
/dev/sda8 = 1.4 GB swap

To delete partitions you can boot from the Ubuntu CD to the live desktop, and run GParted. Then select the partitions you want to delete (all the logicals) and then recreate two logicals, one for swap and one for root (the rest of the space).

I attached a snap of what gparted looks like on my drive.

So I should NOT delete sda1 and 2 since that's windows. Is that correct?

But sda5,6,7 and 8 can be deleted. Is that correct?

And how do I create a new partition????

Thanks for the screen shot. That helps.    ...Fred

---

### Post by bcbc on 2012-01-26
Yes, you delete all the logical partitions. Not /dev/sda1 /dev/sda2 or /dev/sda3. /dev/sda3 is the extended partition.

So after deleting /dev/sda5/6/7/8 you create 2 new logicals. See screenshots attached. To do this, click on the "Free space" within /dev/sda3, and then click Partition, New. At the end click the green Tick to Apply operations.

Then kick off the installation, select "Something else", and select the 'new' /dev/sda5 and select as "/".

PS I have a lot of other partitions in the screenshot - if you find it confusing just ask for clarification. (Once you start you want to make sure you complete the installation). Not critical if you don't, but easiest.

---

### Post by atravnic on 2012-01-27
> **bcbc said:**
> Yes, you delete all the logical partitions. Not /dev/sda1 /dev/sda2 or /dev/sda3. /dev/sda3 is the extended partition.

So after deleting /dev/sda5/6/7/8 you create 2 new logicals. See screenshots attached. To do this, click on the "Free space" within /dev/sda3, and then click Partition, New. At the end click the green Tick to Apply operations.

Then kick off the installation, select "Something else", and select the 'new' /dev/sda5 and select as "/".

PS I have a lot of other partitions in the screenshot - if you find it confusing just ask for clarification. (Once you start you want to make sure you complete the installation). Not critical if you don't, but easiest.

Just when you thought...........
Got myself all psyched up to tackle this, get a terminal and, innocent me, type in gparted only to have it tell me I need root privileges to use it. Man, will I ever get there. What do I have to do get root privileges? Thanks!   ...Fred

---

### Post by bcbc on 2012-01-27
> **atravnic said:**
> Just when you thought...........
Got myself all psyched up to tackle this, get a terminal and, innocent me, type in gparted only to have it tell me I need root privileges to use it. Man, will I ever get there. What do I have to do get root privileges? Thanks!   ...Fred
Hit the super (windows) key. That will bring up the unity application lens (or whatever it's called). Start typing in gpa... and you see it appear below (looks like a disk). Then double-click on it. If it prompts you for a password hit Enter. 

From command line you'd run:
```
gksu gparted
```

---

### Post by atravnic on 2012-01-27
> **bcbc said:**
> Hit the super (windows) key. That will bring up the unity application lens (or whatever it's called). Start typing in gpa... and you see it appear below (looks like a disk). Then double-click on it. If it prompts you for a password hit Enter. 

From command line you'd run:
```
gksu gparted
```

The MS magic key (super window whatever) worked, got to gparted, tried to delete sda7, got this: "Unable to delete sda7"; "please mount any logical partitions having a number greater than 7."

However, there seem to be none that are higher than seven. Not sure what this all means.

Help please.

...Fred

---

### Post by bcbc on 2012-01-27
> **atravnic said:**
> The MS magic key (super window whatever) worked, got to gparted, tried to delete sda7, got this: "Unable to delete sda7"; "please mount any logical partitions having a number greater than 7."

However, there seem to be none that are higher than seven. Not sure what this all means.

Help please.

...Fred
This doesn't make a lot of sense. You should have the swap partition on /dev/sda8 but you can't mount it. Did it maybe say "Unmount"? 

I think the live CD might pick up and use an existing swap so maybe you need to turn that off. (You should see a 'key' icon showing which partitions are 'locked').

So try that:
```
sudo swapoff -a
```

Otherwise, if that doesn't work, please can you post a screenshot. (Super key, screenshot). Thanks

---

### Post by atravnic on 2012-01-28
> **bcbc said:**
> This doesn't make a lot of sense. You should have the swap partition on /dev/sda8 but you can't mount it. Did it maybe say "Unmount"? 

I think the live CD might pick up and use an existing swap so maybe you need to turn that off. (You should see a 'key' icon showing which partitions are 'locked').

So try that:
```
sudo swapoff -a
```

Otherwise, if that doesn't work, please can you post a screenshot. (Super key, screenshot). Thanks

Did the swapoff, same thing happened. Please give me the terminal command for taking a screen shot. Thank you!  ...Fred

---

### Post by bcbc on 2012-01-28
> **atravnic said:**
> Did the swapoff, same thing happened. Please give me the terminal command for taking a screen shot. Thank you!  ...Fred

I don't think you can do a screenshot from terminal. You can run gnome-screenshot I guess, but easiest to do it from the GUI

---

### Post by atravnic on 2012-01-28
> **bcbc said:**
> I don't think you can do a screenshot from terminal. You can run gnome-screenshot I guess, but easiest to do it from the GUI

Ah, bcbc my good friend, you are once again overestimating my prowess. Do you mean to use the screen shot capability from within gparted? If there is one I haven't seen it. Ditto for the desktop under Live CD. I miss the old "Places", etc., the unparalleled simplicity. But maybe I'm looking in all the wrong places.

Merci, mon ami!

...Fred

---

### Post by bcbc on 2012-01-28
> **atravnic said:**
> Ah, bcbc my good friend, you are once again overestimating my prowess. Do you mean to use the screen shot capability from within gparted? If there is one I haven't seen it. Ditto for the desktop under Live CD. I miss the old "Places", etc., the unparalleled simplicity. But maybe I'm looking in all the wrong places.

Merci, mon ami!

...Fred
:) Hit the super (windows) key, and type in 'screenshot' - after the first few letters you'll see a camera appear below. Click on that. Then select "Grab the current window" and Grab after a delay of 2 seconds. That gives you time to position yourself on GParted when it takes the shot.

---

### Post by atravnic on 2012-01-29
> **bcbc said:**
> :) Hit the super (windows) key, and type in 'screenshot' - after the first few letters you'll see a camera appear below. Click on that. Then select "Grab the current window" and Grab after a delay of 2 seconds. That gives you time to position yourself on GParted when it takes the shot.

Here's the screen shot you needed. Let me know if this will do it or if you need more.

That Uber windows key is pretty handy. Thanks for putting me on to it.

...Fred

---

### Post by bcbc on 2012-01-29
> **atravnic said:**
> Here's the screen shot you needed. Let me know if this will do it or if you need more.

That Uber windows key is pretty handy. Thanks for putting me on to it.

...Fred

Please give the output of 'mount' (run from the terminal Ctrl+Alt+T) as well. Thanks.

It's showing /dev/sda8 as locked. That's your swap. Please also give the output of:
```
swapon -s
```

If you see /dev/sda8, run
```
sudo swapoff -a
swapon -s
```

You shouldn't see /dev/sda8 anymore. Make sure the key is gone from /dev/sda8 (in gparted after that) and then try again. If you get anything different from expected please post the terminal output showing the errors etc.

---

### Post by atravnic on 2012-01-30
> **bcbc said:**
> Please give the output of 'mount' (run from the terminal Ctrl+Alt+T) as well. Thanks.

It's showing /dev/sda8 as locked. That's your swap. Please also give the output of:
```
swapon -s
```

If you see /dev/sda8, run
```
sudo swapoff -a
swapon -s
```

You shouldn't see /dev/sda8 anymore. Make sure the key is gone from /dev/sda8 (in gparted after that) and then try again. If you get anything different from expected please post the terminal output showing the errors etc.

Wasn't sure what you wanted me to mount, so I took a guess. If this is not quite what you needed, just tell me. Thanks!  ...Fred

---

### Post by bcbc on 2012-01-30
Okay so by swapping off /dev/sda8 it removes the lock. That should allow you to proceed. 
(I didn't intend for you to mount something; if you enter "mount" by itself it outputs a list of everything that's mounted - I don't believe you need this anymore). 

So the steps should be:
1. Boot the live CD to the desktop
2. Ctrl+Alt+T to a terminal and run:
```
sudo swapoff -a
```
3. "exit" the terminal and run GParted.
4. delete /dev/sda5, 6, 7, 8
5. create new /dev/sda5 (ext4) and /dev/sda6 (swap)
6. Exit GParted and double click "Install" from the desktop (or top of the Unity bar) to kick off the install
7. Select "Something else" when asked how/where to install
8. Select /dev/sda5 as "/" (the new partition)
9. (Swap should be already selected, but you can check)
10. Install.

---

### Post by atravnic on 2012-01-30
> **bcbc said:**
> Okay so by swapping off /dev/sda8 it removes the lock. That should allow you to proceed. 
(I didn't intend for you to mount something; if you enter "mount" by itself it outputs a list of everything that's mounted - I don't believe you need this anymore). 

So the steps should be:
1. Boot the live CD to the desktop
2. Ctrl+Alt+T to a terminal and run:
```
sudo swapoff -a
```
3. "exit" the terminal and run GParted.
4. delete /dev/sda5, 6, 7, 8
5. create new /dev/sda5 (ext4) and /dev/sda6 (swap)
6. Exit GParted and double click "Install" from the desktop (or top of the Unity bar) to kick off the install
7. Select "Something else" when asked how/where to install
8. Select /dev/sda5 as "/" (the new partition)
9. (Swap should be already selected, but you can check)
10. Install.

To the best of my recollection--I related it all on my son's tablet but it failed to transmit--I deleted sda 5,6,7, 8, went to create sda5, but got an error and can't remember what it was. Took screen shots, logged off to get into Vista to send them to you, but couldn't get in: "error: no such partition", and "> grub rescue".

I other words, I'm locked out of Vista, 11.10 is not up, and the my sons tablet will end up permanently implanted in the nearest wall if I keep trying to use it.

Don't know if it'll work, but I'll try to attach the screen shots.

Help.    ...Fred

P.S. -- On second thought, I don't have any screen shots after all. All I can do is redo the whole sorry mess and take screen shots again. I'll do anything for you to make helping me easy.

---

### Post by bcbc on 2012-01-30
> **atravnic said:**
> To the best of my recollection--I related it all on my son's tablet but it failed to transmit--I deleted sda 5,6,7, 8, went to create sda5, but got an error and can't remember what it was. Took screen shots, logged off to get into Vista to send them to you, but couldn't get in: "error: no such partition", and "> grub rescue".

I other words, I'm locked out of Vista, 11.10 is not up, and the my sons tablet will end up permanently implanted in the nearest wall if I keep trying to use it.

Don't know if it'll work, but I'll try to attach the screen shots.

Help.    ...Fred

P.S. -- On second thought, I don't have any screen shots after all. All I can do is redo the whole sorry mess and take screen shots again. I'll do anything for you to make helping me easy.
:(

Boot up the live CD and try again. Check what the error is. You could always let Ubuntu install automatically, it should use the largest free space. That will get the bootloader sorted so windows can boot as well.

If you still get errors, please write down as much as you can.
Thanks

---

### Post by bcbc on 2012-01-30
If you find you just want Vista back there are a couple of options. Booting from your Windows DVD or a recovery CD to a repair prompt and running:
```
bootrec /fixmbr
```
will fix it until you get Ubuntu installed.

---

### Post by atravnic on 2012-01-31
> **bcbc said:**
> :(

Boot up the live CD and try again. Check what the error is. You could always let Ubuntu install automatically, it should use the largest free space. That will get the bootloader sorted so windows can boot as well.

If you still get errors, please write down as much as you can.
Thanks

So I started to run through the whole sequence again until that ominous warning, which I didn't heed the first time through, but probably should have, and also might explain why I'm so royally screwed now.

Shot 1: output from mount and swapoff command.
Shot 2: output form gparted, now, after I deleted sda5678 yesterday.
Shot 3: this is the fatal one, I looked for a way to create sda5 (ext4) and sda6 (swap), the partition drop-down was empty, the only thing that came close was "Device" which warned me as you can see. Nonetheless, yesterday, I ignored the warning and went ahead. That's probably what did me in. 

Today I stopped short of that point, and the rest is history. 

If you need more, holler.

Thank you!

...Fred

P.S. -- Your other suggestion: bootrec /fixmbr resulted in "commond not found".

---

### Post by bcbc on 2012-01-31
woah stop right there.

You need to create a partition, not a partition table.

First select the Unallocated space UNDER /dev/sda3. Then click on Partition, New.

You've selected "Device, create partition table" in that screenshot which will not end well.

PS bootrec /fixmbr has to be run from a Windows repair prompt (via booting from a Windows DVD or a Windows repair CD)

---

### Post by bcbc on 2012-01-31
Okay I reread your first post - did you say you already went ahead and created a new partition table?

If so, you'll be wanting to run "testdisk" to try to recover the old one. Hopefully you didn't do this, but if so you'll want to review this: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

To install testdisk you need access to the internet, so that might be an issue. oh boy

Please confirm what state you're in

---

### Post by atravnic on 2012-01-31
> **bcbc said:**
> woah stop right there.

You need to create a partition, not a partition table.

First select the Unallocated space UNDER /dev/sda3. Then click on Partition, New.

You've selected "Device, create partition table" in that screenshot which will not end well.

PS bootrec /fixmbr has to be run from a Windows repair prompt (via booting from a Windows DVD or a Windows repair CD)

Too late for me to get into anything serious now, I usually hit the sack around 11, but I'll rerun this tomorrow. I just have one question, having rashly chosen the partition table option, have I done irreversible damage?

I have neither a Windows DVD nor a repair CD. I assume they can be bought, but if there are any free sources, please let me know.

Thanks again my friend.    ...Fred

---

### Post by bcbc on 2012-01-31
> **atravnic said:**
> Too late for me to get into anything serious now, I usually hit the sack around 11, but I'll rerun this tomorrow. I just have one question, having rashly chosen the partition table option, have I done irreversible damage?

I have neither a Windows DVD nor a repair CD. I assume they can be bought, but if there are any free sources, please let me know.

Thanks again my friend.    ...Fred

Okay - first confirm whether you've overwritten the partition table. Boot your Ubuntu CD to a live desktop and run GParted. If you don't see your partitions, then you need to recover the partition table.

Do not attempt to create any partitions or write anything to the hard drive.

I think you should confirm first that the partitions are gone. Unfortunately things have got more complicated now - and since you don't have internet access from your live CD we'll need to work something out to get testdisk.

PS it won't help to install the windows bootloader if the partition table is gone.

---

### Post by atravnic on 2012-02-01
> **bcbc said:**
> Okay - first confirm whether you've overwritten the partition table. Boot your Ubuntu CD to a live desktop and run GParted. If you don't see your partitions, then you need to recover the partition table.

Do not attempt to create any partitions or write anything to the hard drive.

I think you should confirm first that the partitions are gone. Unfortunately things have got more complicated now - and since you don't have internet access from your live CD we'll need to work something out to get testdisk.

PS it won't help to install the windows bootloader if the partition table is gone.

Sorry I screwed things up. I should have stopped when I didn't know how to create new partitions instead of experimenting recklessly.

Meanwhile, I've attached the screenshot you had wanted, but didn't do anything with it.

I'm trying to figure out how to activate Broadcom in live CD mode, and then you can have access to my computer if that's the way you want to go.

Hang in there, buddy. But if this whole thing becomes too much of a pain, the simplest thing would probably to throw Vista under the bus and just install 11.10.

Thanks again, and again, and again!

...Fred

---

### Post by bcbc on 2012-02-01
Is that a current screenshot? If so, then you're okay (you didn't splat the partition table). That's GREAT. (*Breathes sigh of relief*)

So what you've got there is good - it's going to create a logical partition with the full space of the extended partition.
So make the following adjustments:
1. Change "Free space following" to 3500 (that will be for swap).
2. Change "File system" to "Ext4"
3. Click Add.
4. Click on the unallocated line after the "new partition #1" it shows. It will be for the remaining 3500 MB. 
5. Make sure it also says "Create as" logical partition
6. Change "File system" to "Linux swap"
7. Click Add.

Review...

You will see under /dev/sda3:
New partition #1 ext4        103GB (or 104)
New partition #2 linux-swap   3.5GB  (more or less)

If that looks good, click on the Green Tick Mark to "Apply all operations"

Once that completes, you can proceed to the install.
When it prompts you about the partitions, choose "Something Else".
Click /dev/sda5, click Change, and select to use as: "/".

If you have any questions stop and contact me.
Good luck.

---

### Post by atravnic on 2012-02-01
> **bcbc said:**
> Is that a current screenshot? If so, then you're okay (you didn't splat the partition table). That's GREAT. (*Breathes sigh of relief*)

So what you've got there is good - it's going to create a logical partition with the full space of the extended partition.
So make the following adjustments:
1. Change "Free space following" to 3500 (that will be for swap).
2. Change "File system" to "Ext4"
3. Click Add.
4. Click on the unallocated line after the "new partition #1" it shows. It will be for the remaining 3500 MB. 
5. Make sure it also says "Create as" logical partition
6. Change "File system" to "Linux swap"
7. Click Add.

Review...

You will see under /dev/sda3:
New partition #1 ext4        103GB (or 104)
New partition #2 linux-swap   3.5GB  (more or less)

If that looks good, click on the Green Tick Mark to "Apply all operations"

Once that completes, you can proceed to the install.
When it prompts you about the partitions, choose "Something Else".
Click /dev/sda5, click Change, and select to use as: "/".

If you have any questions stop and contact me.
Good luck.

Screen shot is current as of AM today. I think we're both breathing easier. Didn't know "splat" was a technical term.

I'm gonna be extremely cautious now, and ask questions first.

"1. "Change "Free space following" to 3500 (that will be for swap)." What's your point of departure? E.g., what/where is "Free space following" and what's the amount I'm changing the 3500 from?

2. "Change "File system" to "Ext4"" Is this the first unallocated line on gparted following sda3?

3. "Click Add."  Where is "Add"?

4. "Click on the unallocated line after the "new partition #1" it shows. It will be for the remaining 3500 MB." I'm lost here, but it'll probably become clear after I do the above. Please confirm.

I'll stop here, to stay out of trouble, mainly. Thanks!!!   

...Fred

---

### Post by bcbc on 2012-02-02
The screenshots here show me creating two logical partitions. It's a little different because I only have 8GB in my extended partition, but the steps you take are the same.

Just use all of the space when you create the first logical partition EXCEPT 3500MiB

---

### Post by bcbc on 2012-02-02
Now you apply the changes - you'll get a big warning, and then it will show your new partitions.

---

### Post by bcbc on 2012-02-02
Now proceed to install from the desktop install icon or from the top of the unity bar.

After entering the language, you need to select "SOMETHING ELSE". Then click on /dev/sda5 and click on CHANGE.
Follow screenshot of what to set:
Use as: Ext4 journaling file system
Format partition: tick (not required, but do it)
Mount point: /

The swap is selected automatically. Click INSTALL NOW.

---

### Post by bcbc on 2012-02-02
> **atravnic said:**
> Screen shot is current as of AM today. I think we're both breathing easier. Didn't know "splat" was a technical term.

I'm gonna be extremely cautious now, and ask questions first.

"1. "Change "Free space following" to 3500 (that will be for swap)." What's your point of departure? E.g., what/where is "Free space following" and what's the amount I'm changing the 3500 from?

2. "Change "File system" to "Ext4"" Is this the first unallocated line on gparted following sda3?

3. "Click Add."  Where is "Add"?

4. "Click on the unallocated line after the "new partition #1" it shows. It will be for the remaining 3500 MB." I'm lost here, but it'll probably become clear after I do the above. Please confirm.

I'll stop here, to stay out of trouble, mainly. Thanks!!!   

...Fred

I'm going to answer these as well, just so I don't miss anything...

1 & 2:
Click on the "Unallocated" line under /dev/sda3.
When you first click "Partition, New" it will default to the entire unallocated space within /dev/sda3. So you just have to modify the "Free space following" to 3500. This will give you room for your swap partitoin.
You also set it to be "File system: ext4"

3. Then click add (bottom right in the "Create new partition" window

4. Then you'll see /dev/sda3, and right under that "New partition #1". Following that will be another "Unallocated". Click on that, then on the menu "Partition, New".
This will default to the full 3500 Mib. Set it to "File system: linux-swap".
Click on Add (bottom right).

Hopefully that answered the questions and together with the screenshots it will be clear.

Again, if anything is unclear, stop and ask ;)
Good luck.

---

### Post by atravnic on 2012-02-02
> **bcbc said:**
> I'm going to answer these as well, just so I don't miss anything...

1 & 2:
Click on the "Unallocated" line under /dev/sda3.
When you first click "Partition, New" it will default to the entire unallocated space within /dev/sda3. So you just have to modify the "Free space following" to 3500. This will give you room for your swap partitoin.
You also set it to be "File system: ext4"

3. Then click add (bottom right in the "Create new partition" window

4. Then you'll see /dev/sda3, and right under that "New partition #1". Following that will be another "Unallocated". Click on that, then on the menu "Partition, New".
This will default to the full 3500 Mib. Set it to "File system: linux-swap".
Click on Add (bottom right).

Hopefully that answered the questions and together with the screenshots it will be clear.

Again, if anything is unclear, stop and ask ;)
Good luck.

Right now I'm at the point in the install where you have me change dev/sda5 from ext4 to root ("/"). However, the options provided for "use as" don't include the /. So I decided not to get bold this time and ask you first.

---

### Post by bcbc on 2012-02-02
> **atravnic said:**
> Right now I'm at the point in the install where you have me change dev/sda5 from ext4 to root ("/"). However, the options provided for "use as" don't include the /. So I decided not to get bold this time and ask you first.

Set as follows:

**Use as**: Ext4 journaling file system
**Format the partition**: check
**Mount point**: /

---

### Post by atravnic on 2012-02-02
> **bcbc said:**
> Set as follows:

**Use as**: Ext4 journaling file system
**Format the partition**: check
**Mount point**: /

Well, bcbc my good friend, thanks to you I got a hat trick today. Vista is back (clumsy as ever), 11.10 is installed, cursor still frozen but I hit the cog and went with Ubuntu2D and the cursor is alive and well there. Then I got hit with 347 updates, restarted and guess what: they finally fixed the GD cursor problem. What can I say, life is good. And you made it possible.

I don't even remember when we got started untangling this mess, but ours is the longest running cyber chat I've ever had. I feel we've become friends, and your willingness to stick it out with a newbee like me is nothing short of remarkable.

I have checked out both Vista and 11.10 and as near as I can tell right now, everything is okay. Even the comm problem is gone. All I need now is to bring back my data into 11.10 from excile. Given that the cursor problem is now fixed, do you think it's safe to bring everything back, or is it wise to proceed cautiosly.

THANK YOU!!!!!!!!!!!!!

...Fred

---

### Post by bcbc on 2012-02-02
> **atravnic said:**
> Well, bcbc my good friend, thanks to you I got a hat trick today. Vista is back (clumsy as ever), 11.10 is installed, cursor still frozen but I hit the cog and went with Ubuntu2D and the cursor is alive and well there. Then I got hit with 347 updates, restarted and guess what: they finally fixed the GD cursor problem. What can I say, life is good. And you made it possible.

I don't even remember when we got started untangling this mess, but ours is the longest running cyber chat I've ever had. I feel we've become friends, and your willingness to stick it out with a newbee like me is nothing short of remarkable.

I have checked out both Vista and 11.10 and as near as I can tell right now, everything is okay. Even the comm problem is gone. All I need now is to bring back my data into 11.10 from excile. Given that the cursor problem is now fixed, do you think it's safe to bring everything back, or is it wise to proceed cautiosly.

THANK YOU!!!!!!!!!!!!!

...Fred

Well, I am very happy to hear that! Good job!!! You're right it's been a long journey (although there were a few gaps in-between). The important thing is that it's all working again.

I'd be a bit nervous about restoring all the backed up data (e.g. whatever was in your /home config that caused issues after your 'in-place upgrade' attempt). The data part will be fine, so you could extract folder by folder e.g. Pictures, Documents, Music etc.

And then selectively restore other things e.g. firefox config (including bookmarks etc.). The way you could approach it is to e.g. move/rename the existing folder to keep as a backup before extracting the one from your /home backup.

To restore selectively, you can plug in the external drive with your homebackup.tgz and then browse to it in Nautilus, open it and then manually select files and or folders and extract to the desired location. This would be the safest approach - rather than trying to replace your entire /home directory. 

I just looked back and saw your first post was in October last year - a lot longer than I recalled. You're remarkably patient to have kept at it in spite of some serious roadblocks.

---

### Post by mörgæs on 2012-02-03
> **atravnic said:**
> ... your willingness to stick it out with a newbee like me is nothing short of remarkable.



+1 

I have spent quite some time in the forum and have never seen anything like this. 

It is indeed 'ubuntu' =D>

---

### Post by atravnic on 2012-02-04
> **mörgæs said:**
> +1 

I have spent quite some time in the forum and have never seen anything like this. 

It is indeed 'ubuntu' =D>

In all honesty, mörgæs, while it was frustrating at times, I also learned a lot, and I feel much more confident handling Ubuntu problems. But much of the credit belongs to BCBC and his patience and perserverance. 

I appreciate your comment, and more importantly, your interest in following the progress on this thread.

...Fred

---

### Post by atravnic on 2012-02-08
Decided to take a few days off from the rigours of Ubuntu, and had just now decided to get moving on data transfer when I ran into an unexpected problem. I had just logged in and a notice popped up telling me I was signed in as atravnic (correct) and that Ubuntu would terminate in 60 seconds (which it did). When I tried to log back in it didn't recognize my password.

Any idea what's going on? Can I change my password in recovery mode? 

Ciao     ...Fred

---

### Post by bcbc on 2012-02-08
No I have no idea what is going on.

Log in to recovery mode - you'll get to a read-only recovery menu. Select option 3 (I believe) to remount drives read-write.
Then you can drop to a root shell, and enter:
```
passwd atravnic
```
Enter your new password. Enter 'exit' to return to the recovery menu, and resume normal boot. (It will be a bit weird since recovery boots with 'nomodeset' so just restart to get back to normal).

Once that's done you can review your logs to see if there is something that indicates what happened.

---

### Post by atravnic on 2012-02-08
> **bcbc said:**
> No I have no idea what is going on.

Log in to recovery mode - you'll get to a read-only recovery menu. Select option 3 (I believe) to remount drives read-write.
Then you can drop to a root shell, and enter:
```
passwd atravnic
```
Enter your new password. Enter 'exit' to return to the recovery menu, and resume normal boot. (It will be a bit weird since recovery boots with 'nomodeset' so just restart to get back to normal).

Once that's done you can review your logs to see if there is something that indicates what happened.

Worked like a charm. Wish evrything were as simple. Is there another way to change your password. You know, just change it, not to get a new one due to a problem.

How do I check the logs to look for what might have happened?

Did you ever get a sense which file(s) might be implicated in the problems I had. Would it save me work if, instead of data file by data file, I rolled in the entire backup and just threw out the suspects?

Thank you for your help.

...Fred

---

### Post by atravnic on 2012-02-08
How do you set up spell checking globally?

---

### Post by bcbc on 2012-02-08
If it were me I'd copy data... photos, music, video, documents, code, downloads. Nothing there is going to hurt. It's likely the 'config' files that will cause issues.

Of those there are a small number I'd care about. For me, it's the .ssh, .gnupg, plus a few others. Most of my browser settings are in the cloud so I don't care about that, but if you want your bookmarks etc. you'll need the .mozilla/firefox etc. None of these should cause you any issues. I'd probably just ignore the rest - if you find you need something later you know where to go back and get it.

I'm not sure what you mean about a global spellcheck.

Regarding logs, I don't know specifically what I'd look for - that problem you reported seems a bit strange. So I'd just browse through the /var/log/syslog and maybe /var/log/auth.log just to see if there is anything that stands out.

---

### Post by atravnic on 2012-02-13
> **bcbc said:**
> 

I'm not sure what you mean about a global spellcheck.

In the past when I've upgraded, there was always a spell checker running in the background, no matter what I was doing or which application I was using. I had to do nothing, It was just there. Now it's not. So what do I need to do to activate it? And that's what I meant bu global.

Thank you!

Ciao    ...Fred

---

### Post by atravnic on 2012-02-20
> **bcbc said:**
> If it were me I'd copy data... photos, music, video, documents, code, downloads. Nothing there is going to hurt. It's likely the 'config' files that will cause issues.

Of those there are a small number I'd care about. For me, it's the .ssh, .gnupg, plus a few others. Most of my browser settings are in the cloud so I don't care about that, but if you want your bookmarks etc. you'll need the .mozilla/firefox etc. None of these should cause you any issues. I'd probably just ignore the rest - if you find you need something later you know where to go back and get it.

I'm not sure what you mean about a global spellcheck.

Regarding logs, I don't know specifically what I'd look for - that problem you reported seems a bit strange. So I'd just browse through the /var/log/syslog and maybe /var/log/auth.log just to see if there is anything that stands out.

I tend to procrastinate when I have to do something I don't feel like doing because it's tedious work. Like restoring my backed-up data. But I fianlly did it. And of course I have questions.

I restored my desktop, well sort of. Turns out what I got was a collection of files in a folder called, surprise, desktop. What do I need to do to make it look like my original desktop.

I seem to have a similar situation regarding Firefox. I naively expected everything to roll back into all its proper positions. But clearly some additional work is needed.

I also brought back SDA1, 5 and 7. Not sure why. Because they were there I guess. Do I actually need them on my hard drive?

Finally, how/where do I turn on the universal spell checker. I do get spell checking in LibreOffice, but not anywhere else.

Thanks!

...Fred

---

### Post by bcbc on 2012-02-20
I have no idea about a global spell checker. I'm not even sure how something like that would work actually.

If you've copied the backed-up Desktop folder to the Desktop instead of the contents, you can open up a nautilus Windows, browse to Desktop/Desktop, then select the contents and drag it to the Desktop entry (on the left under "Computer"). Then delete the empty Desktop folder afterwards. You'll still likely have to layout the icons the way you want.

SDA1, 5 and 7 - you can just copy off the data you want. Or keep them backed up in case you find you're missing something.

Firefox - from what I gather - you would rename ~/.mozilla to ~/.mozillaOLD and then copy your old .mozilla into your home directory.
e.g. 
open nautilus, navigate to your home directory, hit Ctrl+H to show hidden folders. Then, exit firefox and then rename the **.mozilla** folder to **.mozillaOLD**. Then extract your old .mozilla folder into your home directory

---

