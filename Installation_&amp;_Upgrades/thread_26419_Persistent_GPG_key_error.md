---
title: "Persistent GPG key error"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by tennessee@tennessee.id.au on 2005-04-12
I get 

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

even when I re-run apt-get update several times. I don't know, really, exactly what that means. It might mean that there is genuinely a problem with tha pat repository, but it also might be my end.

I have booted off an older kernel image, because I was messing around with my config today, and my machine stopped booting. I hadn't run update in about 6 days, so I was a little behind given that HH changes so much. When I ran apt-get remove nvidia-kernel-common to remove the nvidia driver, it also downloaded a new kernel and refused to boot (hung on "Booting kernel..."). I tried reverting, and my machine booted up just fine.

I thought I would run apt-get update just to get my system properly up-to-speed to see if it fixed the problem, and that's when I came across the message. So maybe the problem is that I am booting in recovery mode, or maybe the respository is damaged somehow, but I didn't want to run upgrade until I knew.

Cheers,
-T

---

### Post by flaming_monkey on 2005-04-14
I too am having a similar problem.  Can anyway lets us know what's going on here?

---

### Post by speedman on 2005-04-14
You can try restoring the default keys as follows:

System > Administration > Synaptic Package Manager

Once synaptic launches go to:

Settings > Repositories > Authentication > Restore default keys

HTH


Regards,

SM

---

### Post by chaitatp on 2005-04-15
I also have the same problem as yours.  See the link

[http://ubuntuforums.org/showthread.php?t=26817](http://ubuntuforums.org/showthread.php?t=26817)

In brief, after I had had a fresh installation of Hoary and then ``apt-get update''ed and it just failed.  What the heck... T_T

Thanks speedman, but I bet that won't fix.

---

### Post by jrblevin on 2005-04-24
I apologize for the long post, but I wanted to add a few details about this problem.  I have read all the posts and the Ubuntu guide and nothing has worked.  I have downloaded and installed the public key and I have used Synaptic to restore the default keys both with no luck.

Here is what I have done: First, I downloaded packages for apt and apt-utils from the pool and reinstalled by hand, just to overwrite any configuration files:

[INDENT]root@syd:/home/jrblevin # dpkg -i --force-overwrite apt_0.6.35ubuntu2_i386.deb apt-utils_0.6.35ubuntu2_i386.deb[/INDENT]

This replaced my trustdb.gpg and trusted.gpg in /etc/apt.  Then, I tried to
update again, giving the following:

[INDENT]
root@syd:/etc/apt # apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Fetched 378B in 0s (409B/s)
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems[/INDENT]

Notice that this is a different error than previously--now it is NO_PUBKEY.
So I downloaded the public key as follows:

[INDENT]jrblevin@syd:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 0x40976EAF437D05B5
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
jrblevin@syd:~$ gpg --armor --export 437D05B5 | sudo apt-key add -[/INDENT]

Note that the key in question is not the  Christian Marillat (1F41B907) key mentioned in the Ubuntu Guide.  Have the signing keys changed or something?
At any rate, even after adding this other key, we are back to the original problem (omitting the Get list):

[INDENT]root@syd:/etc/apt # apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
[...]
Fetched 378B in 3s (120B/s)
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems[/INDENT]

The problem persists even with the --allow-unauthenticated option to apt-get...

Any ideas?

Thanks

---

### Post by SQFreak on 2005-06-19
Continuing with this and a bump, here's my apt-get update output which gives a similar error, as well as some others:

```

$ sudo apt-get update
Get:1 http://archive.ubuntu.com hoary Release.gpg [189B]
Get:2 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:4 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Hit http://archive.ubuntu.com hoary Release
Hit http://security.ubuntu.com hoary-security Release
Hit http://us.archive.ubuntu.com hoary Release
Ign http://archive.ubuntu.com hoary Release
Ign http://security.ubuntu.com hoary-security Release
Ign http://us.archive.ubuntu.com hoary Release
Hit http://us.archive.ubuntu.com hoary-updates Release
Hit http://archive.ubuntu.com hoary/multiverse Packages
Ign http://us.archive.ubuntu.com hoary-updates Release
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Ign http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Get:5 http://us.archive.ubuntu.com hoary/universe Packages [2853kB]
99% [5 Packages gzip 0] [Waiting for headers] [Waiting for headers]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com hoary/universe Packages
  Sub-process gzip returned an error code (1)
Ign http://public.planetmirror.com hoary-backports Release.gpg
Ign http://public.planetmirror.com hoary-extras Release.gpg
Ign http://cp.yi.org ./ Release.gpg
Ign http://cp.yi.org ./ Release
Ign http://public.planetmirror.com hoary-backports Release
Hit http://cp.yi.org ./ Packages
Ign http://public.planetmirror.com hoary-extras Release
Ign http://public.planetmirror.com hoary-backports/main Packages
Ign http://public.planetmirror.com hoary-backports/universe Packages
Ign http://public.planetmirror.com hoary-backports/multiverse Packages
Ign http://public.planetmirror.com hoary-backports/restricted Packages
Ign http://public.planetmirror.com hoary-extras/main Packages
Ign http://public.planetmirror.com hoary-extras/universe Packages
Ign http://public.planetmirror.com hoary-extras/multiverse Packages
Ign http://public.planetmirror.com hoary-extras/restricted Packages
Hit http://public.planetmirror.com hoary-backports/main Packages
Hit http://public.planetmirror.com hoary-backports/universe Packages
Hit http://public.planetmirror.com hoary-backports/multiverse Packages
Hit http://public.planetmirror.com hoary-backports/restricted Packages
Hit http://public.planetmirror.com hoary-extras/main Packages
Hit http://public.planetmirror.com hoary-extras/universe Packages
Hit http://public.planetmirror.com hoary-extras/multiverse Packages
Hit http://public.planetmirror.com hoary-extras/restricted Packages
Fetched 757B in 4s (176B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://security.ubuntu.com hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any suggestions?

---

### Post by saadat on 2005-07-16
[QUOTE=SQFreak]Continuing with this and a bump, here's my apt-get update output which gives a similar error, as well as some others:

```

$ sudo apt-get update
Get:1 http://archive.ubuntu.com hoary Release.gpg [189B]
Get:2 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:4 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Hit http://archive.ubuntu.com hoary Release
Hit http://security.ubuntu.com hoary-security Release
Hit http://us.archive.ubuntu.com hoary Release
Ign http://archive.ubuntu.com hoary Release
Ign http://security.ubuntu.com hoary-security Release
Ign http://us.archive.ubuntu.com hoary Release
Hit http://us.archive.ubuntu.com hoary-updates Release
Hit http://archive.ubuntu.com hoary/multiverse Packages
Ign http://us.archive.ubuntu.com hoary-updates Release
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Ign http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Get:5 http://us.archive.ubuntu.com hoary/universe Packages [2853kB]
99% [5 Packages gzip 0] [Waiting for headers] [Waiting for headers]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com hoary/universe Packages
  Sub-process gzip returned an error code (1)
Ign http://public.planetmirror.com hoary-backports Release.gpg
Ign http://public.planetmirror.com hoary-extras Release.gpg
Ign http://cp.yi.org ./ Release.gpg
Ign http://cp.yi.org ./ Release
Ign http://public.planetmirror.com hoary-backports Release
Hit http://cp.yi.org ./ Packages
Ign http://public.planetmirror.com hoary-extras Release
Ign http://public.planetmirror.com hoary-backports/main Packages
Ign http://public.planetmirror.com hoary-backports/universe Packages
Ign http://public.planetmirror.com hoary-backports/multiverse Packages
Ign http://public.planetmirror.com hoary-backports/restricted Packages
Ign http://public.planetmirror.com hoary-extras/main Packages
Ign http://public.planetmirror.com hoary-extras/universe Packages
Ign http://public.planetmirror.com hoary-extras/multiverse Packages
Ign http://public.planetmirror.com hoary-extras/restricted Packages
Hit http://public.planetmirror.com hoary-backports/main Packages
Hit http://public.planetmirror.com hoary-backports/universe Packages
Hit http://public.planetmirror.com hoary-backports/multiverse Packages
Hit http://public.planetmirror.com hoary-backports/restricted Packages
Hit http://public.planetmirror.com hoary-extras/main Packages
Hit http://public.planetmirror.com hoary-extras/universe Packages
Hit http://public.planetmirror.com hoary-extras/multiverse Packages
Hit http://public.planetmirror.com hoary-extras/restricted Packages
Fetched 757B in 4s (176B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://security.ubuntu.com hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any suggestions?[/QUOTE]
 it seems that even I am having this problem as many people here - any sort of solution???????

---

### Post by TSJason on 2005-07-18
Had this problem after I upgraded my debian sarge box to kubuntu. I ended up just copying the /etc/apt/trusted.gpg file from my amd64 kubuntu box to fix it.
sorry I couldn't be more helpful.

---

### Post by loney on 2005-07-28
[QUOTE=saadat]it seems that even I am having this problem as many people here - any sort of solution???????[/QUOTE]
 I had to remove and readd the offending repositories. In my case, updates and security-updates binary and source were removed and readded.

---

### Post by podious on 2005-10-05
Bumping this again.  I've looked around the Net for an answer and still can't find one.
I'm having the exact same problem.  I've tried adding and readding repositories and keys and neither works.
Someone please help!!!!  
Anyone know if Mark Shuttleworth scours this forum?  ;)

---

### Post by michan on 2005-10-15
I was having a similar problem but I found a way to fix it!  when I looked in /etc/apt there was a file called trusted.gpg and a backup file called trusted.gpg~.  i simply restored the trusted.gpg~ (delete or back up trusted.gpg and rename trusted.gpg~ to trusted.gpg), and it works again now.

---

### Post by yuk on 2005-10-15
Thank you michan! You saved my day.

---

### Post by NemoPaice on 2005-10-15
I have that same problem...... My question is, How do you restore the back up?

---

### Post by yuk on 2005-10-16
[QUOTE=NemoPaice]I have that same problem...... My question is, How do you restore the back up?[/QUOTE]
cd /etc/apt
sudo cp trusted.gpg trusted.gpg_backup (make a backup of the trusted.gpg file)
sudo cp trusted.gpg~ trusted.gpg ;)

---

### Post by monoworks on 2005-10-16
**[POSSIBLE SOLUTION]**

Hi!
I fixed this problem in a dumb, but effective way. :)
Please tell me if this fixed also your problem.

It seems, that if gpg repository is changed, then the old repository key seems to be yet cached. So my solution was to readd the repository.

**Way of solution:**
```

1. sudo cp /etc/apt/sources.list /etc/apt/sources.list.breezybackup (make Backup)
2. sudo vim /etc/apt/sources.list (create new repository file)
3. Type following without quotes: ":x"  (Yes, you are right! This creates an empty file!)
4. sudo apt-get update (update to delete all old repositories)
5. sudo cp /etc/apt/sources.list.breezybackup /etc/apt/sources.list (change back to good old known repository file)
6. sudo apt-get update (and voila, there should be no more gpg error.)

```

Ok, have fun and see you again! :-)

---

### Post by marguz on 2005-10-17
NICE!!!!

Worked GREAT :-)

---

### Post by br0wer on 2005-10-17
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

I just tried both fixes and I'm STILL having problems. Is there another way to restore the defaults or clear the cache? Please forgive my ignorance, I'm new to Ubuntu! I'm used to Fedora :(

---

### Post by Quake_Sinatra on 2005-10-17
After trying everything i saw in this forum about this message, to no avail. i noticed i had the cds in the repository and didnt have the cd in at the time i tried to update. (each previous time i had the cd in it worked fine.. the only thing that changed since it last worked was that i did not have the cd in). i removed the cd from the repository list and it updated fine, no GPG error. not sure if that helps anyone else, but its worth a shot.

---

### Post by aysiu on 2005-10-17
[QUOTE=br0wer]W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

I just tried both fixes and I'm STILL having problems. Is there another way to restore the defaults or clear the cache? Please forgive my ignorance, I'm new to Ubuntu! I'm used to Fedora :([/QUOTE] Try taking the *us* out of your repositories: ```
http://archive.ubuntu.com
``` instead of ```
http://us.archive.ubuntu.com
```

---

### Post by schilcha on 2005-10-18
Many thanks!

After all other fixes in this thread failed, this one finally put my system back in a good shape. By the way, in my case it were the *at* mirrors that had to be removed.

---

### Post by Leonardo Helman on 2005-10-18
This solution worked for me.

[I]This is my problem (similar)W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
[/I]

So I import the keys, and update the apt keys with that:
```
  
  gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
  apt-key add ~/.gnupg/pubring.gpg

```

Saludos
Leonardo Helman

---

### Post by Tanjerine on 2005-10-18
Had this very same problem this morning. Tried several of the solutions, but what worked for me was this:

[INDENT][/home/sarah 11:33:11]$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 0x40976EAF437D05B5[/INDENT]

after it got the keys, apt-get update worked perfectly! :)

---

### Post by ganesh on 2005-10-19
[QUOTE=Quake_Sinatra]After trying everything i saw in this forum about this message, to no avail. i noticed i had the cds in the repository and didnt have the cd in at the time i tried to update. (each previous time i had the cd in it worked fine.. the only thing that changed since it last worked was that i did not have the cd in). i removed the cd from the repository list and it updated fine, no GPG error. not sure if that helps anyone else, but its worth a shot.[/QUOTE]

Thanks. That was it. After commented out entry for CD-ROM everything looks fine now.

---

### Post by ThirdWorld on 2005-10-20
I restored the authentication key in synaptic package manager and everything its working fine now. Looks like another bug to me. So far i have discover 3 different bugs in Ubuntu operating sistem:
1- the authentication key issue in synaptic discussed in this forum-(now fixed)
2- the cursor go black sometimes after using an application
3- when I login im getting this message: "Your $HOME/.drmc file has incorrect permissions and is being ignored. This prevents the session from being saved. File should be owned by user and have 644 permissions."
where I can report this to Ubuntu developers?

---

### Post by Mentalbug on 2005-11-09
- deleted message-

* aw nevermind, I tought the problem was solved but it's still not working after the "gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5" trick*  :'(

edit, new update!
It seems to work with [monoworks's trick](http://ubuntuforums.org/showthread.php?t=26419&page=2#top) ^^

---

