---
title: "AGHHH not again. Pubkeys...."
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by miss_beckie_louise on 2010-07-01
So, I "Checked" my updates on the update manager, and more blooming things have come up. I haven't changed anything, it's just majorly messed up. Is it down to my OS version?? 8.04 is what I have... 

So anyway here is what's come up...

[I]W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/I]

Can you help?? also Firefox 3.0 is being gay and won't update! GRRR

---

### Post by mikewhatever on 2010-07-01
I'd suggest simply trying again tomorrow or switching to another mirror.

---

### Post by miss_beckie_louise on 2010-07-01
A mirror???

---

### Post by mikewhatever on 2010-07-01
Mirror or online repository, which is the same thing. You can select another one under System->Admin->Software Sources.

---

### Post by RJARRRPCGP on 2010-07-01
It's usually not caused by the server's end. 

You need to check your configuration. Sorry. :(

---

### Post by mhgsys on 2010-07-01
This might help you; 

[http://swiss.ubuntuforums.org/showthread.php?t=1262936](http://swiss.ubuntuforums.org/showthread.php?t=1262936)

---

### Post by sgosnell on 2010-07-01
Not having the keys doesn't prevent updates, that's just a warning of a possible security problem, if you download from unknown repositories.  You can ignore those warnings and go ahead with the updates.  'Apt-get update' doesn't actually update anything except the repository information, you use 'apt-get upgrade' to update your packages.

---

### Post by miss_beckie_louise on 2010-07-01
Okay, so if the pubkeys don't mean anything what can I do to get all the updates working again normally? I don't do anything on this laptop apart from write, twitter and gtalk! I totally don't get it. All these problems for this, it's stupid.

---

### Post by mhgsys on 2010-07-01
Have you tried the two possible solutions offered to you?

> **mikewhatever said:**
> I'd suggest simply trying again tomorrow or switching to another mirror.

> **mhgsys said:**
> This might help you; 

[http://swiss.ubuntuforums.org/showthread.php?t=1262936](http://swiss.ubuntuforums.org/showthread.php?t=1262936)

---

### Post by miss_beckie_louise on 2010-07-01
Yeah I've tried everything suggested and it keeps coming back. I just want an overall thing that'll work once n I never have to do again

---

### Post by mhgsys on 2010-07-01
did you notice to enter the **last 8 digits?**  of each signature

---

### Post by miss_beckie_louise on 2010-07-01
yup

---

### Post by mhgsys on 2010-07-01
That's pretty quick then !.

hmmz, I'll guess there will be lot's of more people to help you with this.. 

 This is not really my thing.

---

### Post by rollin on 2010-07-01
I found this: 
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg860911.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg860911.html)
and a solution >
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg862836.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg862836.html)

Might help? Some guy managed to fix the issue by deleting a file under the /etc/apt/sources.list.d/ directory. 

Obviously you should approach this with caution I think and perhaps back up the files before you start deleting any! 

Take a look at the link, it might help??

---

