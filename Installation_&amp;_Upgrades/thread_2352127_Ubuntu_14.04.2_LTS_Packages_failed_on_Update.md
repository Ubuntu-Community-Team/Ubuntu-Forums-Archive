---
title: "Ubuntu 14.04.2 LTS Packages failed on Update"
date: 2017-02-09
forum: Installation &amp; Upgrades
---

### Post by enjiel on 2017-02-09
I'm running Ubuntu Server 14.04.2 LTS
When running sudo apt-get update, most of the packages install, but some are rejected.  I had my network guy open port 80 to those IP addresses but a number of them still failed.  Is that because they don't exist anymore or is there likely more that I need to do network/server side to get the update to complete?

Running $ sudo apt-get update takes about 6 hours.  When it's done, I generally come across a number of errors including 404 Not found errors and others.
 I tried $ sudo apt-get upgrade after running update; I get
"Reading package lists... Error!"
"Encountered a section with no package: header"
"Problem with MergeList /var/lib/apt/lists/..."
"The package lists or status file could not be parsed or opened"
(I get the same thing with a $ sudo apt-get check)

I have found a few discussions on this topic that suggest running:
$ sudo rm /var/lib/apt/lists/* -vf 
Then running update again, which, after 6 hours I run into the same problem.

I also tried:
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update

Another 6 hours, and I end up with the same errors.


I'm trying to decide where to go from here.  Is there a way to completely uninstall the apt application and start fresh without reinstalling Ubuntu?
This server is currently in production, so reinstalling Ubuntu would be problematic.
Are there other files that can be removed or recreated to point apt to the right places?

I've never had to do troubleshooting with apt before because it's always just worked.  It's one of my favorite things about Ubuntu, but after working on this for a couple of days I feel like I'm just fumbling around in the dark.
[ATTACH=CONFIG]273606[/ATTACH]

---

### Post by TheFu on 2017-02-10
Support for 14.04.2 ended last August.

14.04.5 is the current supported version.  Please upgrade to that. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Of, if you prefer, 14.04.1 and 14.04.0 running 3.13.x kernels are supported as well.

```
sudo apt update
sudo apt dist-upgrade
``` over and over until nothing new can be installed.

And make a recoverable backup before beginning. Would be terrible for some unrelated issue to completely trash the system and not be able to get it back to make another attempt.

If the update cannot complete, you have some other issue - probably a network problem or the repos in your config are gone. Pick some other repos in a different country?

---

### Post by enjiel on 2017-02-10
Thank you for responding.  I tried running do-release-upgrade and got the same error:
SytemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu.com_ubuntu_dists_trusty_main_il8n_Translation-en, E:The package lists or status file could not be parsed or opened.

Is this server hosed?  I have backups, but I doubt I have any that will be before this issue began considering that it has been quite some time since I've run an update on it.

---

### Post by TheFu on 2017-02-10
**do-release-upgrade** will take you from 14.04 --> 16.04. I think it only works with a currently patched system.  I'd **restore from backups** and NOT attempt do-release-upgrade again until everything is working.

I've never heard of attempting to move to a new release from a broken system helping.  Just sayin'.

---

### Post by enjiel on 2017-02-10
Word, thanks. I'll try doing a backup restore and see if that helps, but I'm not sure when this issue started.  So there is no way to unintall/reinstall aptitude/apt or repair it?

---

### Post by TheFu on 2017-02-10
Can't tell from what was posted. From here, it seems the suggested steps were ignored.  We can only go by what you post. It is bad form for us to assume things. Only you can tell us stuff.

After you restore, do what was suggested and log everything to a file.  Then post the *relevant* issues using **code tags**. That will make things line up and be readable. Things that aren't easy to read don't get as much help.

---

### Post by enjiel on 2017-02-11
Thanks for the advice.  I apologize for the lack of code tags and information on what I've done.  I haven't ignored any steps but I didn't run a backup restore, mainly because if I do a restore from a couple of days back before I noticed the issue (I'm don't even know when the issue started so it may or may not solve the problem) I'm still looking at potential data loss since this is an active server that end users are dealing with on a daily basis.

I considered my options and in the time that it would take me to backup and database and files in it, run a bare metal backup-restore, then restore the files and database back onto it.  Then do an update/upgrade to a newer version that is supported, I think it would be faster just to create a new server along side this one, configure it then move all the files and database over.  I'm going to call this solved, thank you guys so much for your help.  I was hoping that there was another way to update the server, or fix "apt/aptitude", I never really got a straight answer I.E. "No there is no way to uninstall/resinstall apt/aptitude or repair apt/aptitude" but I'm going to assume that's the case because I can't find anywhere in the forums or Ubuntu instructions on how to do so.

---

### Post by TheFu on 2017-02-11
There might have been, but we didn't have the necessary data to know.

I asked you to```

sudo apt update
sudo apt dist-upgrade
```
and suggested if that didn't work (because no connections were possible to those repos, but networking everywhere else WAS still working), to change the repos do a different country. 

Did you attempt any of that?

Nobody could say "YES, 100%, we can fix this." That isn't how things work with computers.  I think there was a 90% chance for a solution, but we will never know now.

Good luck.

---

