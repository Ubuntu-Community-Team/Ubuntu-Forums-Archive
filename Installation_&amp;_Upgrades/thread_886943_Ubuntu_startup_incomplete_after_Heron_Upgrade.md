---
title: "Ubuntu startup incomplete after Heron Upgrade"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by boobahzone on 2008-08-11
I've searched the forum for this type of problem but so far have not found anything that explains this.  I've had Ubuntu for a few months now, though I'm still relatively new to understanding it (but trying my best!).

I recently went to upgrade my Ubuntu Gutsy to Hardy Heron after I ran my system upgrades.  After getting about half way through, the progress bar for my upgrade seemed to stop (though the system itself was not frozen, just the upgrade progress).  It seemed that the upgrade process stopped saying that there were 8 minutes left to complete installation, and after letting it sit for about 3 hours I came back and it was still frozen at that same point.

At this point, I decided that maybe I should reboot my computer (probably a bad idea now in retrospect).  I went to restart the computer using a soft shutdown, however the progress bar for Ubuntu logging out would not finish, so I then did a hard shutdown.  

When I restart the computer now, it goes through some odd behavior then never completely starts Ubuntu.  The BIOS runs okay, then the Ubuntu progress bar comes on showing that it is making progress to start ubuntu, then the progress seems as if it jumps back to the beginning once, then shows that the progress is complete.  I then get to a  black screen with white text saying something about "Anachron acron [OK]" and "Diferral exon scheduler [OK]" which flashes on the screen a few times.  Then, it tells me that my computer is running in low graphics mode because my graphics card cannot be found, and asks if I want to continue or not.  When I continue, I can sign in with my username and password, but it just leaves me with a blank Ubnuntu-colored orange-brown screen that never actually opens to anything.

I have a feeling this is because my Hardy Heron never installed.  Is there a way I can finish installing Hardy Heron or fix these problems?

Thanks for any help!  Much appreciated.

---

### Post by boobahzone on 2008-08-12
Also, I should note that I am able to reach the command line and run prompts from there.  When I got to the command line, I ran

sudo dpkg-reconfigure -phigh xserver-xorg

but it said that the path was broken or not fully installed.  I got this from the post at [http://ubuntuforums.org/archive/index.php/t-633381.html](http://ubuntuforums.org/archive/index.php/t-633381.html).

Any ideas?

---

### Post by Kevbert on 2008-08-12
Probably your best bet is a new clean install of Hardy (rather than trying to fix it).  I had a similar problem when upgrading and ended up starting again from scratch.  If you have a wired internet connection (broadband/cable) have that connected when you install as this will help.

---

### Post by boobahzone on 2008-08-12
I might be narrowing down the problem a little if this helps.  Here's what I've done:

I booted the computer, then pressed CTRL+ALT+F1 at login to get to the command line.

I then ran 

sudo apt-get update

to attempt to just try to start re-upgrading, and go the error message "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem".  I got the same error message when I ran sudo apt-get dist-upgrade.

So I ran

sudo dpkg --configure -a

and it gets stuck saying 
"Generating locales
en_AU.UTF-8"

Any ideas for what this could be specifically?  I have a lot of data and settings that I'd prefer not to lose if at all possible, and I'd really like to not have to reformat.

Thanks for any help!

---

### Post by Kevbert on 2008-08-12
> **boobahzone said:**
> I might be narrowing down the problem a little if this helps.  Here's what I've done:

I booted the computer, then pressed CTRL+ALT+F1 at login to get to the command line.

I then ran 

sudo apt-get update

to attempt to just try to start re-upgrading, and go the error message "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem".  I got the same error message when I ran sudo apt-get dist-upgrade.

So I ran

sudo dpkg --configure -a

and it gets stuck saying 
"Generating locales
en_AU.UTF-8"

Any ideas for what this could be specifically?  I have a lot of data and settings that I'd prefer not to lose if at all possible, and I'd really like to not have to reformat.

Thanks for any help!

I think it may be Australian English Language Support and it should be put in /usr/lib/locale directory.

---

### Post by Kevbert on 2008-08-12
Here's the files you need.  I've tarred them and they go in the en_AU.utf8 directory.

---

### Post by NateVandy on 2009-02-07
I had this same problem, and I replaced my en_AU.UTF-8 file with the file Kevbert provided, but it didn't fix the problem.

I fixed the problem following the advice left by siberoptik on this thread.

> **siberoptik said:**
> Just had this problem myself. It seems to be to do with the latest Gutsy kernel version.

These steps worked for me:

[LIST=1]
[*]Reboot your box, and press ESC to enter the GRUB menu
[*]Select the previous version of the kernel xxx.14 rather than xxx.15 (sorry I can't recall the exact version numbers) - don't select the fail-safe mode.
[*]Log-in as your admin user into recovery mode
[*]Manually (re)start the upgrade via a terminal session: dpkg --configure -a
[/LIST]

It should complete the install.

Good luck

A lot of people have this problem, as evidenced by the length of that thread.

---

