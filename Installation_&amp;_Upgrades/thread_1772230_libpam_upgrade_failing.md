---
title: "libpam upgrade failing"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by amvapor on 2011-05-31
My system (Lucid) prompted me to update this morning, but in the process it is getting a404 on the file [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-2ubuntu5.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-2ubuntu5.2_i386.deb)

did someone forget to push this file out? I can find a diff file for this version, but not the packaged deb.

Thanks.

---

### Post by keithweddell on 2011-05-31
I'm seeing a lot of problems with this.  Systems I updated last night were spamming /var/log/auth.log with errors - unable to open pam_env.so until I restarted Cron.  Now the packages are missing from the repos.  Can anyone explain what went wrong?

Keith

---

### Post by sjwk on 2011-05-31
> **amvapor said:**
> My system (Lucid) prompted me to update this morning, but in the process it is getting a404 on the file [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-2ubuntu5.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-2ubuntu5.2_i386.deb)

did someone forget to push this file out? I can find a diff file for this version, but not the packaged deb.

Thanks.

Can't solve the problem for you, but can confirm I'm seeing the same thing so unlikely to just be your system (or mine).

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-2ubuntu5.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-2ubuntu5.2_i386.deb)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-2ubuntu5.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-2ubuntu5.2_i386.deb)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-2ubuntu5.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-2ubuntu5.2_all.deb)  404  Not Found [IP: 91.189.92.166 80]

Hopefully it'll sort itself out soon...

Steve.

---

### Post by Silvertones on 2011-05-31
Same here.

---

### Post by ksimmons on 2011-05-31
Same 404 on the following packages:

libpam0g amd64 1.1.2-2ubuntu8.2
libpam-modules-bin amd64 1.1.2-2ubuntu8.2
libpam-modules amd64 1.1.2-2ubuntu8.2
libpam-runtime all 1.1.2-2ubuntu8.2

versions 1.1.2-2ubuntu8.1 appear to exist on the server.  perhaps someone made a typo or the package wasn't pushed out.

---

### Post by Caddisfly on 2011-05-31
I looked at the version of libpam-modules visible and as of May 30 it looks like there was an upgrade from 1.1.1-2ubuntu5.2 up to 1.1.2-2ubuntu8.2

Unfortunately I'm not at all sure how to proceed from that minor discovery, being a nearly absolute beginner with updating/upgrading packages in ubuntu outside of the update manager,

---

### Post by keithweddell on 2011-05-31
OK.  Bug report [here]("https://bugs.launchpad.net/ubuntu/+source/pam/+bug/790538")

Keith

---

### Post by jvonmitchell on 2011-05-31
Hey guys.  I've looked at the repository and found that the package is not on the server so there is nothing on your system you need to fix.  I imagine that at some point they will get that link up to the site. We may need to wait a few days before we update but I'm just going to sit it out until the problem is solved.

---

### Post by v_krishna on 2011-05-31
> **keithweddell said:**
> OK.  Bug report [here]("https://bugs.launchpad.net/ubuntu/+source/pam/+bug/790538")

Keith

From looking at this launchpad report, it seems the offending file (libpam-modules=1.1.1-2ubuntu5.2) was removed from the repos but it is still listed as an upgrade waiting to occur...

Temporarily fixed by doing a sudo apt-get install libpam-modules=1.1.1-2ubuntu2 to downgrade libpam. Unfortunately you then can't do a sudo apt-get update && sudo apt-get upgrade as it will try to reinstall the missing package - but if you do sudo apt-get upgrade and say n, you can then copy-and-paste the list of packages waiting to be upgraded (minus the libpam stuff) and get the rest of your system up-to-date.

That "fixes" your local system, but what the frack is going on with libpam? How did anybody think the proper behavior in dealing with a buggy package is to simply remove the buggy package from the repositories after it has been released? Even if the fix was to roll back to an earlier version, they should have then released the earlier version as a new version - otherwise you have what occurred here - people who upgraded before whenever the package was removed (it seems like 3 hours ago?) now have a package that doesn't exist anywhere else installed from the official repositories, and other people (like myself) have apt-get claiming they need to install a package that doesn't exist... this just seems like horrible practice all around. :confused:

---

### Post by brentini on 2011-05-31
Restarted the cron daemon
```
sudo[COLOR=Black] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]init.d[COLOR=#000000]**/**[/COLOR]cron restart[/COLOR]
```And then ran```
sudo apt-get update && sudo apt-get upgrade
```That fixed this issue for me.

---

### Post by jonvel on 2011-05-31
> **v_krishna said:**
> 
Temporarily fixed by doing a sudo apt-get install libpam-modules=1.1.1-2ubuntu2 to downgrade libpam. Unfortunately you then can't do a sudo apt-get update && sudo apt-get upgrade as it will try to reinstall the missing package - but if you do sudo apt-get upgrade and say n, you can then copy-and-paste the list of packages waiting to be upgraded (minus the libpam stuff) and get the rest of your system up-to-date.


You can also just do a:

```
sudo apt-get upgrade --fix-missing
```

like it says if you try the upgrade without anything.  While this doesn't actually fix the problem, it lets up upgrade other modules that it can actually find.  You'll still run into the problem if you try to upgrade later.

> **v_krishna said:**
> 
That "fixes" your local system, but what the frack is going on with libpam? How did anybody think the proper behavior in dealing with a buggy package is to simply remove the buggy package from the repositories after it has been released? Even if the fix was to roll back to an earlier version, they should have then released the earlier version as a new version - otherwise you have what occurred here - people who upgraded before whenever the package was removed (it seems like 3 hours ago?) now have a package that doesn't exist anywhere else installed from the official repositories, and other people (like myself) have apt-get claiming they need to install a package that doesn't exist... this just seems like horrible practice all around. :confused:

Yeah, I think someone botched the deployment, is my guess.  From how I understand the apt-get process to work, there's a "file" on the remote repo (a Packages.gz file) that suggests what the "new" (or at least current) files/versions are on the repo.  That's what's checked when you do a "apt-get update".  Your system is then compared for installed components against the current set in the repo, and if there are discrepancies, they're flagged for upgrade.  Then the "apt-get upgrade" pulls down the actual .deb files for installation.  If that's how it really works, then the real fix would have been to re-update the version string file on the repo (what gets checked with "apt-get update") to reflect the roll back.

Then again, I am probably completely incorrect on how I interpret how apt-get "works".

**Update**
Just read some more about the bug that was filed - the upgraded pam modules (libpam0g, libpam-modules-bin, libpam-modules and libpam-runtime) were breaking some other things, so it was pulled from the repo.  The problem is that some users have already applied the update, so they're (Canonical) are in a bit of a bind.  There are some people that have the more recent update for the pam modules (version 1.1.2-2ubuntu8.2, as reported by the 'apt-get update') already installed.  For them, it's not a simple matter of updating the Packages.gz file.  This is probably because of the way apt-get works to determine what is "newer".  However Canonical could create a minor update (say version 1.1.2-2ubuntu8.2.1) that houses the rolled back prior version instead.  I don't know if that'll work, however.  Plus, any interrogations on the local system that don't go through apt-get or dpkg will show an inconsistent file version.

However, it appears as though it will be "fixed" in the next few hours.

---

### Post by mdbelt on 2011-05-31
Is there a way around this?  I'm trying to do a distribution upgrade & am completely stuck.  Looks like users around the entire world can't use "apt-get upgrade" currently.

---

### Post by rbowen1 on 2011-05-31
Looks like a problem with the file repository for the updates.  I am getting similar messages.

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.2-2ubuntu8.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.2-2ubuntu8.2_i386.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules-bin_1.1.2-2ubuntu8.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules-bin_1.1.2-2ubuntu8.2_i386.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.2-2ubuntu8.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.2-2ubuntu8.2_i386.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.2-2ubuntu8.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.2-2ubuntu8.2_all.deb) 404  Not Found [IP: 91.189.92.166 80]

---

### Post by mdbelt on 2011-05-31
I think it's fixed.  I just did a apt-get update then upgrade & it didn't list it anymore.

---

### Post by Samatva on 2011-05-31
> **brentini said:**
> Restarted the cron daemon
```
sudo[COLOR=Black] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]init.d[COLOR=#000000]**/**[/COLOR]cron restart[/COLOR]
```And then ran```
sudo apt-get update && sudo apt-get upgrade
```That fixed this issue for me.

I had to use "sudo service cron restart" to get cron to restart...

However, after restarting cron, apt-get claims that libpam is up to date!??!! 
Using --fix-missing has no effect, nothing upgraded.

---

### Post by jonvel on 2011-05-31
> **Samatva said:**
> I had to use "sudo service cron restart" to get cron to restart...

However, after restarting cron, apt-get claims that libpam is up to date!??!! 
Using --fix-missing has no effect, nothing upgraded.

As a note, the [FONT="Courier New"]--fix-missing[/FONT] would only work for people that were trying to do a [FONT="Courier New"]sudo apt-get upgrade[/FONT] between the time when Canonical pulled the libpam modules through before Canonical pulled the libpam modules from the Packages.gz file.  If you upgraded between the time that Canonical initially put up the (defective) libpam modules and when they pulled the libpam modules, then it won't help you.  You already have the "bad" libpam modules installed.  What you'll have to do is what v_krishna posted:

[QUOTE=v_krishna]Temporarily fixed by doing a sudo apt-get install libpam-modules=1.1.1-2ubuntu2 to downgrade libpam[/QUOTE]

ie downgrade the installed version of the libpam modules.  You might need to repeat that for the [FONT="Courier New"]libpam0g[/FONT], [FONT="Courier New"]libpam-modules-bin[/FONT], and [FONT="Courier New"]libpam-runtime[/FONT] modules as well.

Since Canonical has now updated their repository index to not include the updated libpam modules, anyone who didn't upgrade to the "defective" 1.1.2-2ubuntu8.2 (I think it's 1.1.2-2ubuntu5.2 for 10.04 LTS) should be fine.  I know, no consolation to those of you that auto-updated.  If you check out the thread on the [launchpad bug number 790538]("https://bugs.launchpad.net/ubuntu/+source/pam/+bug/790538") report, it'll provide some more information.

---

### Post by bogdarnet on 2011-05-31
Okay, what version of libpam should we have now (and how do we check that?)

---

### Post by ksimmons on 2011-05-31
> **mdbelt said:**
> I think it's fixed.  I just did a apt-get update then upgrade & it didn't list it anymore.

Fixed here also without restarting cron.  I saw the proper 8.2 packages install.

---

### Post by Samatva on 2011-05-31
Everything is upgrading correctly now. It's *great* that things like this rarely happen with Ubuntu,  and it's *wonderful* how quickly the problem was identified and fixed.

Kudos to the folks who have create a Linux for us mortals!

---

