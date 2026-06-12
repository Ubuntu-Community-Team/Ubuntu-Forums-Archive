---
title: "Thunderbird segmentation fault after upgrade to 10.04"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by bergamot on 2010-05-13
Since upgrading to 10.04 Thunderbird doesn't work properly.

It is Thunderbird 3.04.

It works for locally-created users but exits with 'segmentation fault' when the user is from LDAP. In the latter case, the home directory is local, created by pam_mkhomedir.

I get the same problem with a newly-installed 10.04 system.

I cannot understand why it worked fine in 9.10 but not in 10.04. :confused:
I set "set -x" in the thunderbird script and here is the trace from that:

$ thunderbird
+ moz_libdir=/usr/lib/thunderbird-3.0.4
+ found=0
+ progname=/usr/lib/thunderbird-3.0.4/thunderbird
+ dirname /usr/lib/thunderbird-3.0.4/thunderbird
+ curdir=/usr/lib/thunderbird-3.0.4
+ basename /usr/lib/thunderbird-3.0.4/thunderbird
+ progbase=thunderbird
+ run_moz=/usr/lib/thunderbird-3.0.4/run-mozilla.sh
+ test -x /usr/lib/thunderbird-3.0.4/run-mozilla.sh
+ dist_bin=/usr/lib/thunderbird-3.0.4
+ found=1
+ [ 1 = 0 ]
+ script_args=
+ debugging=0
+ MOZILLA_BIN=thunderbird-bin
+ [  = beos ]
+ pass_arg_count=0
+ [ 0 -gt 0 ]
+ [ 0 = 1 ]
+ /usr/lib/thunderbird-3.0.4/run-mozilla.sh /usr/lib/thunderbird-3.0.4/thunderbird-bin
Segmentation fault
+ exitcode=139
+ exit 139

Anyone got any ideas? Is it a bug? If so is there a workaround?

Thanks

---

### Post by dlepiane on 2010-05-14
Hey, I get the same failure in the same setup.  So far no help online.  Lots of other bugs with crashes during runtime, but nobody with crashing on startup.  

I have similar scenario, though I'm x86.  But users are from LDAP with mkhomedir.  No problems for locally created users (to my limited testing).  But the directory users find Thunderbird just throws a segmentation fault immediately on startup.   

With my own account, I've removed all .mozilla-thunderbird and .thunderbird links and directories.  After attempting to start Thunderbird, I see a .mozilla-thunderbird softlink which points to a .thunderbird folder which doesn't exist.  And putting my existing Thunderbird profile in .thunderbird does not alleviate the problem.

---

### Post by blue_bullet on 2010-05-14
I have had similar problems the past few days.  I now am copying my default profile under .thunderbird (actually the whole .thunderbird) somewhere else so I can recover if something goes wrong.  I have had to rebuild mail files and my abook.mab from old directories.  Quite confusing.  Some of the addins seem to be causing a problem in particular GDATA that provides connections between Google calendars and Lightning.  It can destroy data in your address book.

Once I recovered a profile that worked I reinstalled each of my addins one at a time per tbird session being cautious to back up .thunderbird before each reinstall.  

Don't know if it helps but I upgraded from 9.10 to 10.04 and was using 3.2pre (Shredder) on 9.10. 

I was so confused/frustrated at one point I even installed Evolution but haven't used it much since I am hooked on Thunderbird. 

Unfortunately everything is so new that some of the documentation has not kept up with the software and cannot be relied upon for accuracy.  Somehow I got directories named .tb, .tb-abandoned, and .thunderbird-abandoned in addition to the usual .thunderbird and .mozilla-thunderbird.   I was able to somewhat recover piecing together a new .thunderbird directory by copying in old mail files from those directories.

---

### Post by blue_bullet on 2010-05-14
Correction it is 3.0.3pr I am running on my laptop w/o problems.  It has been running on 9.04, Lucid beta, and now Lucid 10.04 (upgrade).  All my problems have occurred on my desktop after an upgrade to Lucid from 9.10.

---

### Post by dlepiane on 2010-05-14
> **blue_bullet said:**
> Once I recovered a profile that worked I reinstalled each of my addins one at a time per tbird session being cautious to back up .thunderbird before each reinstall.  

This sounds like a different issue.  If I remove Thunderbird and all plugins from my system and blow away all profile information including any potential plugins there, it still throws segmentation fault even before it starts the "setup a new email account" wizard.

---

### Post by blue_bullet on 2010-05-14
OK, then I suggest you remove your .thunderbird and .mozilla-thunderbird folders (rename if you like and delete later), completely remove thunderbird via synaptic, and finally reinstall thunderbird via synaptic.  That should get you a complete fresh start. I gather you have no old mail files you want to recover.

---

### Post by dlepiane on 2010-05-14
> **blue_bullet said:**
> OK, then I suggest you remove your .thunderbird and .mozilla-thunderbird folders (rename if you like and delete later), completely remove thunderbird via synaptic, and finally reinstall thunderbird via synaptic.  That should get you a complete fresh start. I gather you have no old mail files you want to recover.


> **dlepiane said:**
> With my own account, I've removed all .mozilla-thunderbird and .thunderbird links and directories.  After attempting to start Thunderbird, I see a .mozilla-thunderbird softlink which points to a .thunderbird folder which doesn't exist.  And putting my existing Thunderbird profile in .thunderbird does not alleviate the problem.

Removing Thunderbird and re-installing it did not work either.  And the OP reported the same failure from a fresh 10.04 install.

](*,)

---

### Post by sensorial on 2010-05-16
Just try run thunderbird with '-safe-mode' parameter, set default theme and disable all additional plugins. (In my case this is was FireTray).

That's helped me.

---

### Post by bergamot on 2010-05-17
Running thunderbird safe mode gives the same result - segmentation fault with no other output.

I find it worrying that something popular like Thunderbird does not work on this new Ubuntu release. On my own computer I'm using Evolution for the moment, which is OK but rather slow compared to Thunderbird. I can't force other people in my organisation to use Evolution though. Quite rightly they are keen on using Thunderbird and it's our supported mail client.

---

### Post by Sinestro13 on 2010-05-23
Hello all,

I can confirm that I too have seen this particular error. My setup is very similar to everyone else´s, home directories are attached to the workstations from a NFS server, and user authentication is done by LDAP. 

I´ve been able to duplicate the segmentation fault errors with thunderbird. I have also seen the same problem with gtkpod (of all applications?). 

Surprisingly enough, I was able to resolve this issue by installing the nscd package. Once it was installed, the segmentation fault error messages (miraculously) went away. I was immediately able to load thunderbird without issue and gtkpod also ran without a hitch. Years of system administration have taught me to be cautious, so I rebooted each workstation several times to confirm that the fix would continue working, and sure enough it did.

I hope this helps. 

Thanks.

---

### Post by bergamot on 2010-05-24
Thankyou, you've saved me a lot of headaches.

I installed nscd and straight away I could start thunderbird with no problem. The machine is OK after reboot too.

I wonder how you worked out it was nscd? I would never have worked that out.

Thanks again.

:KS

---

### Post by Sinestro13 on 2010-05-24
Bergamot to answer your question, I was pulling my hair out over the weekend trying to figure out a solution to this problem until I was reminded of the nscd daemon by a post on the opensuse forums. Sorry, I don't know which link I saw that reminded me of it. I'd actually seen similar problems in the past with Debian, so it seemed like a fair chance that this could be a fix. 

Luckily it worked!

---

### Post by Kbelt on 2010-05-31
I had the same problem in Ubuntu 10.04. I tried installing the nscd package and it did not work for me. The only way I got it to work was by completely removing the default package available from the repositories and installing the version available from the thunderbird website directly. I hope this help others. Mine is working fine now.

---

### Post by dlepiane on 2010-06-01
I didn't try nscd but at the time I had tried the stock Thunderbird package from Thunderbird directly and that didn't work.

The work-around I found was to dump passwd entries from ldap into the local passwd file, total kludge but good enough for the affected system

```
# getent passwd <user> >> /etc/passwd
```

---

### Post by basily on 2010-06-05
I have some more information to add. Everything was working fine for me under Lucid and Thunderbird 3.04. Then I copied my profile over to an NTFS drive so I could share it with my dual boot Windows XP.

Still worked fine.

I was transferring emails from a local folder to a gmail imap folder, and then thunderbird suddenly shut down. Trying to restart it, even after a reboot only gives "Segmentation Fault". Thunderbird tries to start, fails and I get "Segmentation Fault".

The strange thing is that it STILL works fine with the default profile (the original which is still on an EXT4 drive) AND the profile on my NTFS drive works in Windows.

I've tried installing nscd to no avail.

Now I'm trying to remove Thunderbird (that was installed via the Ubuntu Software Centre) and installing directly from mozilla... still no good. This is very strange.

Safe-mode. Same deal.

What gives???

---

### Post by Ukrainian on 2010-06-18
Hi  I've filed bug [https://bugzilla.mozilla.org/show_bug.cgi?id=573071](https://bugzilla.mozilla.org/show_bug.cgi?id=573071) for this and described my workaround - after disabling polling on start one of two gmail IMAP accounts segmentation faults was gone. BTW also there is somehow related restriction of simultaneous connections to server in Advanced Account Settings. I changed value of it from 5 to 1 after founding described workaround.

---

### Post by Ukrainian on 2010-06-25
> **Ukrainian said:**
> my workaround - after disabling polling on start one of two gmail IMAP accounts segmentation faults was gone.

Problem reappeared, but looks like this time the root was in message filter, which should perform replying with Template. But Templates folder wasn't subscribed, so after subscribing to the Templates folder problem was gone. Previous receipt with reducing IMAP polling wasn't successful this time and I am not confident either previously haven't manipulations with Templates folder.

---

### Post by bluelightav on 2010-12-04
> **Kbelt said:**
> I had the same problem in Ubuntu 10.04. I tried installing the nscd package and it did not work for me. The only way I got it to work was by completely removing the default package available from the repositories and installing the version available from the thunderbird website directly. I hope this help others. Mine is working fine now.

TB on Lucid fresh install but .mozilla file from Hardy - same problem
Got an error message in kernel:

Nov 30 08:43:18 offering kernel: [ 2915.092086] thunderbird-bin[4838]: segfault at 0 ip 0808d23e sp bf866a78 error 4 in thunderbird-bin[8048000+bc0000]

install nscd package. Installation alone doesn't help here. THe nscd damon has to be started !

/etc/init.d/nscd status
* Status of Name Service Cache Daemon service:
* not running.

starting nscd -d  
but after 30 sec or so 
nscd: cache.c:402: prune_cache: Assertion `dh->usable' failed.

nscd was not running any more
after clearing the cache
rm /var/cache/nscd/*

and starting nscd
/etc/init.d/nscd start


Thunderbird is starting again.

---

### Post by josepato on 2010-12-21
Starting with 
thunderbird -safe-mode
helped me.. thanks
once I started I disabled one addons in (funanmbol) and everything went back to normal...

---

### Post by niever on 2011-01-11
nscd saved me... thank you :D

---

### Post by 905jay on 2011-02-03
> **Sinestro13 said:**
> Hello all,

I can confirm that I too have seen this particular error. My setup is very similar to everyone else´s, home directories are attached to the workstations from a NFS server, and user authentication is done by LDAP. 

I´ve been able to duplicate the segmentation fault errors with thunderbird. I have also seen the same problem with gtkpod (of all applications?). 

Surprisingly enough, I was able to resolve this issue by installing the nscd package. Once it was installed, the segmentation fault error messages (miraculously) went away. I was immediately able to load thunderbird without issue and gtkpod also ran without a hitch. Years of system administration have taught me to be cautious, so I rebooted each workstation several times to confirm that the fix would continue working, and sure enough it did.

I hope this helps. 

Thanks.


I can confirm that in my setup at work, this did indeed work. The user in particular was having issues opening synaptic, software install /uninstall /thunderbird and various other apps.

Once I installed the package nscd, everything started working properly.

---

