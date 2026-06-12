---
title: "Upgrading Firefox from tar file"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by KMJones1 on 2010-03-29
I have Firefox 3.0.18 and can't find a way to upgrade to 3.6. The Synaptic Package Manager says Firefox is already installed, so I uninstalled it but the re-install just gives me 3.0.18 again!
I have downloaded the tar file.
What do I do now?

---

### Post by malspa on 2010-03-29
I use the instructions on this page:

[http://support.mozilla.com/en-US/kb/installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/installing+Firefox+on+Linux)

See the section "Installing outside of a package manager."

I just use the steps 1 thru 5.  I've done this on several different distros.  No problems so far.

I haven't used the instructions for "Installing Firefox on Ubuntu" that are linked on that page.

---

### Post by KMJones1 on 2010-03-29
Thanks - I tried that and got the message "tar: bzip2: Cannot exec: No such file or directory". ls shows the file exists OK. I gave it the full reference path. Any ideas?

---

### Post by malspa on 2010-03-30
Yeah, I had that problem come up before, in Debian Lenny.  I had to install **bzip2** from the repos.

---

### Post by KMJones1 on 2010-03-30
Thanks - that worked fine. However!! now when I try to run the shell it cannot find the shared library libdbus-glib-1.so.2. This file exists OK in /usr/lib, and I tried copying it to the firefox folder but got same message. Does it matter where I have the firefox folder? 
It's times like this that I love Windows - things just work!

---

### Post by mkvnmtr on 2010-03-30
Why go to all that trouble when you can go to the Ubuntuzilla site and enable a repository to get the latest Firefox which is 3.6.2 and then get updates form Mozilla. Just follow the instructions . Paste a couple of commands in the terminal and you have the latest Firefox stable.

---

### Post by KMJones1 on 2010-03-30
Thanks for a new idea. I followed the instructions (copying the commands from the site) and mostly things worked, but ended with:
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
kevin@server:~$ sudo apt-get install firefox-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firefox-mozilla-build

I looked at the site referenced for a tutorial: 
[http://www.psychocats.net/ubuntu/ubuntuzilla](http://www.psychocats.net/ubuntu/ubuntuzilla)
and followed their instruction to use Synaptic Package Manager to search for mozilla-build, found it, and it was empty, so no help there.

By the way, the ubuntuzilla page doesn't tell me how to start the new Firefox! My system still goes to the old version.

Why is nothing ever simple!

---

### Post by malspa on 2010-03-30
> **mkvnmtr said:**
> Why go to all that trouble when you can go to the Ubuntuzilla site and enable a repository to get the latest Firefox which is 3.6.2 and then get updates form Mozilla. Just follow the instructions . Paste a couple of commands in the terminal and you have the latest Firefox stable.

This is probably good advice for Ubuntu, even though I haven't found it to be much trouble at all to install Firefox from the Mozilla site.

> **KMJones1 said:**
> Thanks - that worked fine. However!! now when I try to run the shell it cannot find the shared library libdbus-glib-1.so.2. This file exists OK in /usr/lib, and I tried copying it to the firefox folder but got same message. Does it matter where I have the firefox folder?

Here, Firefox is in my home directory.

I installed FF from the Mozilla site in Linux Mint Elyssa, which is based on Hardy, and it looks like you're using Hardy, but I don't recall having the error with libdbus-glib-1.so.2 and I don't have anything about it in my notes.  I would probably check the Mozilla site where it talks about making sure your computer has the required libraries, and also search with Synaptic for libdbus, but the advice from mkvnmtr to just use Ubuntuzilla is probably better in this case.

As for the errors you got installing Firefox using Ubuntuzilla, sorry I can't help you much with that as I have never taken that approach.  For those I would probably try copying the error messages and pasting them into a Google search and seeing what I could come up with.

But I do believe that if you went back to the Mozilla approach that you could make it work.  I happen to know of several other people who use the same approach in different distros.  If you are interested, here's a thread I started at the MepisLovers forums on the subject, got a lot of replies from other users there:

[http://www.mepislovers.org/showthread.php?t=22645](http://www.mepislovers.org/showthread.php?t=22645)

Anyway, I did a search in Mint Elyssa, using Synaptic, for **libdbus**, and also for **glib**, and if you do the same thing in Hardy perhaps you will find a packages in there that, when updated, allows you to use Firefox 3.6.2.  Good Luck!  I really hope someone else here will help you to get it going with the Ubuntuzilla approach because that seems like it might be the better approach in your case.

---

### Post by mkvnmtr on 2010-03-30
The error with the key might be because you did not download the key. It is a seperaate paste in the instructions. There has been a couple of times that when I tried it did not download. It is not a critical problem and I could always download it a few hours later. If you llllneed 64 bit support I have never uesd 64 bit but I believe there are instructions on the same page. It seems that Mozilla does not provide 64bit binaries.

---

