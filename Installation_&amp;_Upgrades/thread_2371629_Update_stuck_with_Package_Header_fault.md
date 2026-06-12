---
title: "Update stuck with Package Header fault"
date: 2017-09-16
forum: Installation &amp; Upgrades
---

### Post by netsurfau on 2017-09-16
Have this "Stop" symbol appear in the status bar near the clock. Not something I've seen before.
Tells me an error occurred and to run Package Manager or apt-get in Terminal to see what is wrong.
It then goes on about a "Package Header" problem.

Result from running apt-get check:
luke@Quad-Core:~$ sudo apt-get check
[sudo] password for luke: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

What do I need to do next? I saw a few apt-get commands for cleaning/removing but, am not familiar enough 
with it to confidently try a fix.

---

### Post by ajgreeny on 2017-09-17
Try running ```
sudo rm /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_main_binary-amd64_Packages
``` and then ```
sudo apt update
``` which should solve the problem by removing the corrupt entry from /var/lib/apt/lists and then recreating it.

---

### Post by netsurfau on 2017-09-17
Thanks @ajgreeny

Running sudo apt update resulted in:

[I]Err:9 [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) xenial Release                           
  404  Not Found [IP: 91.189.92.152 80][/I]

Then:

[I]Err:45 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted amd64 DEP-11 Metadata
  Hash Sum mismatch[/I]

And finally:

[I]Hit:55 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse DEP-11 64x64 Icons
Reading package lists... Error!                                                
E: The repository 'http://extras.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.[/I]

At which point the update process came to a halt.
I haven't changed any of the settings on my system and installing updates as they come through.
I was offline for a few days around the time this error presented itself, not that that should've caused any problems.

---

### Post by ajgreeny on 2017-09-19
OK, so now let's try removing all those list files and then recreating them with ```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

---

### Post by netsurfau on 2017-09-19
I've run the commands and final result was:

Fetched 53.7 MB in 3min 37s (247 kB/s)                                                                                                                      
Reading package lists... Done
W: The repository 'http://extras.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/xenial/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/xenial/main/source/Sources)  404  Not Found [IP: 91.189.92.152 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

So, this appears to have fixed the problem. The Software Updater want to download & install about 183Mb of
updates, and the error symbol has disappeared from the status bar.

Thank you very much Ajgreeny, your knowledge & help are greatly appreciated.

Cheers
Luke

PS: Will mark this one as solved.

---

### Post by ajgreeny on 2017-09-19
Great news! Thanks for marking as SOLVED. It is a great help to users searching the forum.

---

