---
title: "Plymouth errors after cloning server installation"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by TC!! on 2011-10-04
I've just upgraded my server setup 10.04 LTS to use a larger hard disk and now something strange is happening.

My setup before was this:
160GB drive 20GB partition for /
1TB drive whole drive for /home
2TB drive whole drive for /media/films

I wanted to shift over to use a 500GB drive using separate partitions for / and /home. I read up a lot about it and was confused by most of it. After having all sorts of trouble trying to boot from a 10.10 desktop CD I downloaded 11.04 and used that to setup my 500GB disk like this:
20GB - /
476GB /home
4GB /swap

I then installed 10.04 server onto the new drive to take care of the boot record, booted up from the 11.04 CD again and used ddrescue to copy my old system over. It told me it was going to copy 20GB of data but failed at 19998 and told me the new disk was too small. I did a quick comparison and could see that all the data had been copied over OK, the system was only 3.3G of the 20G.

I rebooted after removing my old disk and everything seems to be running fine apart from two strange things.

Whenever I restart the machine I now  see this before the login message:
mountall: Plymouth command failed
mountall: Disconnected from Plymouth

I can see that Plymouth is linked to the desktop but since I don't have that installed on my server setup then why am I getting these messages?

My system also now shows up in my router as 'ubuntu' which is what I remember allowing it to use when I installed the 'dummy' server installation, but in /etc/hostname it has the correct name 'hp'.

Can anyone explain the plymouth messages?

---

### Post by furia on 2011-11-19
I have very similar problem after copying a lucid SERVER installation from a 500gig HD to a second server with only difference a smaller harddisk. 
 
The diskcopy was done via Ghost for Linux (G4L). Due to smaller harddisk the disk copy is hanging at 99,99 %, which is ofcourse logical as the new disk is too small, but this I was able to fix via sfdisk afterwards.
 
Only remaining problem(?) is that the "mountall: Plymouth command failed"  and "mountall:Disconnected from Plymouth" are appearing in the first tty login screen. 
 
anyone a suggestion ? lot's of Plymouth posts found, but nothing found to cure this - and this post is still unanswered.

---

### Post by cbowman57 on 2011-11-19
Seems like I used to just purge Plymouth & reinstall it to get rid of those errors.

My memory isn't what it used to be so make sure it doesn't try to remove everything if you attempt it.

---

