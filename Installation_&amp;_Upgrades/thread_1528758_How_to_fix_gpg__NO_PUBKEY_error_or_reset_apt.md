---
title: "How to fix gpg / NO_PUBKEY error or reset apt"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by reakin on 2010-07-11
Hi,

I have been trying in vain to fix my apt keys, nothing seems to make the error messages go away.  Is there any way to just reset the entire thing (I mean, make it fetch all the keys again)?

I tried the suggestions at: [http://ubuntuforums.org/showthread.php?t=1221323](http://ubuntuforums.org/showthread.php?t=1221323)

without any success, I also tried this: 

> 
r@r-laptop:~$ sudo gpg --keyserver pgpkeys.mit.edu --recv-key A040830F7FAC5991
gpg: requesting key 7FAC5991 from hkp server pgpkeys.mit.edu
gpg: key 7FAC5991: public key "Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1


I think my repositories are updating, but I can't tell.  Anyone know how to clean up these error messages?

Thanks,
Rich

---

### Post by reakin on 2010-07-21
Does anyone know how I can fix these authentication errors, or at least reset my apt repository list?  It seems that, even though now that I am no longer behind a firewall, I still get the authentication errors. I try the apt-key method, it says nothing has changed.. I try to update, and still it says the keys are not there.

Thanks if you can help,
Rich

---

### Post by JustinR on 2010-07-21
Search the forums!

[http://ubuntuforums.org/showthread.php?p=9489003#post9489003](http://ubuntuforums.org/showthread.php?p=9489003#post9489003)

Post #2.

(Maybe the link you posted already said this, I didn't look at it.)

---

### Post by reakin on 2010-07-21
I did search the forums, a few times, for weeks now.  I tried the key server, as that post suggests:


```

r@r-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 2EBC26B60C5A2783 40976EAF437D05B5 40976EAF437D05B5 FC918B335044912E 71346C8340130828 A040830F7FAC5991
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/launchpad-c-korn.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 2EBC26B60C5A2783 40976EAF437D05B5 40976EAF437D05B5 FC918B335044912E 71346C8340130828 A040830F7FAC5991
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: requesting key 5044912E from hkp server keyserver.ubuntu.com
gpg: requesting key 40130828 from hkp server keyserver.ubuntu.com
gpg: requesting key 7FAC5991 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key 0C5A2783: "Medibuntu Packaging Team <admin@lists.medibuntu.org>" not changed
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key 5044912E: "Dropbox Automatic Signing Key <linux@dropbox.com>" not changed
gpg: key 40130828: "Launchpad PPA for Christoph Korn" not changed
gpg: key 7FAC5991: "Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>" not changed
gpg: Total number processed: 7
gpg:              unchanged: 7
r@r-laptop:~$ 

```

I still get the same huge list of GPG errors.  Also, all these posts say to use different key servers.  It seems that Ubuntu merged another new feature into their releases before it was ready.


There should be some way to reset it, without having to type in that ugly command I did above, followed by 7 hash codes.

---

### Post by JustinR on 2010-07-21
From the result you posted it looked like a success, are you still having problems?

---

### Post by reakin on 2010-07-21
I still get the same errors when I run apt-get update.  It says the keys are unchanged, how does this mean success?  To me, it means they are on my computer, but the verification system can't find them.  But I don't really understand this type overly complicated stuff.

---

### Post by JustinR on 2010-07-21
> **reakin said:**
> I still get the same errors when I run apt-get update.  It says the keys are unchanged, how does this mean success?  To me, it means they are on my computer, but the verification system can't find them.  But I don't really understand this type overly complicated stuff.

Sorry for the misunderstanding, in your previous post the last sentence read into my mind as past tense - as if you fixed the problem.

So, as of now, I still don't know enough about APT to provide you with a solution. Maybe someone else can help but best of look to you!

---

