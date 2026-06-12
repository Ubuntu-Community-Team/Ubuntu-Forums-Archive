---
title: "Symantec backup exec ralus solutioin (revisited)"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by LumbeeNDN on 2011-07-26
Hey guys Hate to drag up an old thread, but I am trying to get backup exec running on an Ubuntu 11,04 box. Actually BE seems to be installed on the server OK (I can ps -ef | grep beremote) the problem is my server is not showing up in my network admins (I'm the web developer, not the network admin :/) media server console. I did find at least one mention in another thread where you have to have the correct version of BE installed for the media server to 'discover' your server, however we have aother server (SUSE) with BE installed and it is showing up OK.

Here is my ralus.dfg...[http://pastie.org/2275291](http://pastie.org/2275291)

..and here are relevant lines from /etc/services...[http://pastie.org/2275297](http://pastie.org/2275297)

Any help appreciated...thanx!

---

### Post by Audiosears on 2011-11-10
Lumbee,

Are you running the 3.x kernel or still on the 2.6.x kernel?  I was having problems after upgrading to 11.10, and finally found that it was the 3.x kernel that for whatever reason was causing issues - rebooting with a 2.6.x kernel seems to fix that.  You may also need to specify your BE agent port in etc\services - this is the line I added:

ndmp		10000/tcp			# Backup Exec

At one point way back, I couldnt get the media server to pick my ubuntu box up and browse its contents until I added that and restarted.

---

### Post by LumbeeNDN on 2011-11-11
..hey audio, funny you posted this. I had this working back in the summer, but my backups started failing a few weeks ago. I have not had time to really look into it but I will post back when I do. Thanx!

---

### Post by Rubi1200 on 2011-11-11
I have closed the original thread because of its age.

The relevant posts have now been moved into their own thread.

Here is a link to the original post:
[http://ubuntuforums.org/showpost.php?p=7896068&postcount=1](http://ubuntuforums.org/showpost.php?p=7896068&postcount=1)

Thanks for understanding.

---

