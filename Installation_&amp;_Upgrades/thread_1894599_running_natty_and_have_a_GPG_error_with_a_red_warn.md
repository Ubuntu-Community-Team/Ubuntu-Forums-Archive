---
title: "running natty and have a GPG error with a red warning sign update manager"
date: 2011-12-12
forum: Installation &amp; Upgrades
---

### Post by test_tube_baby on 2011-12-12
Can anybody help. I have update manager giving me a warning symbol - a red exclamation mark and it won't go away.

This is the message I get:

```
Fetched 14.4 MB in 34s (413 kB/s)                                              
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://debian.wgdd.de lucid InRelease: The following signatures were invalid: KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://debian.wgdd.de maverick InRelease: The following signatures were invalid: KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487

W: Failed to fetch http://debian.wgdd.de/ubuntu/dists/lucid/InRelease  

W: Failed to fetch http://debian.wgdd.de/ubuntu/dists/maverick/InRelease  

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I tried the following:
- Changing software sources location to best location and main server but no luck
- sudo apt-get update but no luck

Any ideas?

---

### Post by Bucky Ball on 2011-12-12
You have Synaptic Package Manager or Update Manager open as you are trying to do this? Use the terminal *or *Synaptic/Update Manager/Software Centre. ;)

---

### Post by test_tube_baby on 2011-12-12
> **Bucky Ball said:**
> You have Synaptic Package Manager or Update Manager open as you are trying to do this? Use the terminal *or *Synaptic/Update Manager/Software Centre. ;)

Thanks but I still get an error:

Tried again with Synaptic Package Manager closed. Receive the following error:
```
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://debian.wgdd.de lucid InRelease: The following signatures were invalid: KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://debian.wgdd.de maverick InRelease: The following signatures were invalid: KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487 KEYEXPIRED 1319053487

W: Failed to fetch http://debian.wgdd.de/ubuntu/dists/lucid/InRelease  

W: Failed to fetch http://debian.wgdd.de/ubuntu/dists/maverick/InRelease  

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

Any other ideas?

---

### Post by Bucky Ball on 2011-12-12
Open update manager and go to 'Settings'. In Software Sources>Other Software, what do you have ticked? I don't recognise these software sources. You could unmark the offending repositories and try again.

---

### Post by mlevin2 on 2011-12-12
> **test_tube_baby said:**
> 
```
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>

```


I'm getting this, too, also on natty. Must be a problem at Google's end. I'm sure it will resolve itself soon.

---

### Post by Bucky Ball on 2011-12-12
Yea, untick all in software sources *except* the repos for Natty. That will/should fix. ;)

---

### Post by RealityMaster on 2011-12-12
> **mlevin2 said:**
> I'm getting this, too, also on natty. Must be a problem at Google's end. I'm sure it will resolve itself soon.

Yeah, I'm now getting the same thing, and it was working earlier today...

---

### Post by Bucky Ball on 2011-12-12
A problem at Google's end? OP is getting problems with old release repos. Your Google issues are unrelated. Unless the OP also winds up with one after unticking all old repos in Software Sources. They do have a problem with Google Chrome repo but might be related to other issues. ;)

---

### Post by RealityMaster on 2011-12-12
> **Bucky Ball said:**
> A problem at Google's end? OP is getting problems with old release repos. Your Google issues are unrelated. Unless the OP also winds up with one after unticking all old repos in Software Sources. They do have a problem with Google Chrome repo but might be related to other issues. ;)

Correct, I was referring to Google Chrome repo, should have clarified.  And unticking old repos will fix his problem.

---

### Post by malspa on 2011-12-13
I was getting the same Google Chrome message in Debian Stable, but it appears to be fixed now, might want to try it again and see.

---

