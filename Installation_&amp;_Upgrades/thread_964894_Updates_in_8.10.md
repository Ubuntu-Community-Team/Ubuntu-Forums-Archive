---
title: "Updates in 8.10"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by hornetster on 2008-10-31
Hi, have just installed the Full release of Intrepid, my problem is that I can't seem to check for updates/uninstalled software.
When I try to run Update Manager/Synaptic, I get:

[I]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.[/I]

Anyone else having this problem?
I think I managed to get one update done straight after install, but no joy since....
Thanks, John.

---

### Post by aheckler on 2008-10-31
Try switching to a different server and then updating again. Look under System > Administration > Software Sources, and in the "Download From:" box, choose "Main server". See if that helps.

---

### Post by Joeb454 on 2008-10-31
I've found that a couple of the update servers have gone down - they usually do.

I'm using a different one temporarily :)

---

### Post by hornetster on 2008-10-31
Now about 15 hours later, and still have the same (or similar) problem... 

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.bz2)  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.


Is there any way to reset/ignore the signatures? (I know, not a good thing!)
Have tried many different servers at this point and get same/similar probs with all....
I would like to update/install some new stuff, but all I can see in package manager is the stuff I have already installed. :(
Thanks, John.

---

### Post by hornetster on 2008-11-02
Could somebody please let me know how to reset my software sources (or whatever...) so I can start getting notices of updates that are available??

Thanks in Advance...
   John.

---

### Post by anfeilong on 2008-11-02
Just switch to main server it works for me...

---

### Post by hornetster on 2008-11-02
No, have tried all the servers, and all options within the GUI app. I am sure I need to kill a cache/history/key storage somewhere to fix it...?

---

### Post by hashbrowns on 2009-01-19
> **hornetster said:**
> No, have tried all the servers, and all options within the GUI app. I am sure I need to kill a cache/history/key storage somewhere to fix it...?

I have my own errors that are similar to yours that I'm about to post about, but in case you didn't solve your problem (you didn't tag the post as solved) here's how you reset your keys:

system -> administration -> software sources -> authentication

click remove for both of the keys that are (hopefully) there and then click "restore defaults"

Hope you fixed your problem a few months ago :) heck maybe you can help me with mine, then!

---

### Post by hornetster on 2009-01-20
Well, must admit haven't looked at this for a while, have installed Suse 11.1 (not bad!) and been using that for a while. Have just fixed up my grub, and got back into Ubuntu, and all is now working fine... downloading and installing 72 updates as we speak... :popcorn:
Now, which distro to use..... ;)
Thanks, John.

---

### Post by SOULRiDER on 2009-01-26
I had the same problem. [http://ubuntuforums.org/showthread.php?t=1031404&highlight=40976EAF437D05B5&page=2](http://ubuntuforums.org/showthread.php?t=1031404&highlight=40976EAF437D05B5&page=2) That was the reason why.

---

