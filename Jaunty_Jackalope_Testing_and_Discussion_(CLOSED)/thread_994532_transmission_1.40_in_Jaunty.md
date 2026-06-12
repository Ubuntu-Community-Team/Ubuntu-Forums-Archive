---
title: "transmission 1.40 in Jaunty"
date: 2008-11-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-11-26
Hi all, 
I dunno about everybody else but I love transmission. (atleast till deluge doesn't have a stable release) so I do hope we have transmission 1.40 in jaunty atleast. I have filed [lpbug]302672[/lpbug] requesting the same. I hope we can have it in time for jaunty 9.04. If you guys feel for the same, just select Me/too on the bug.

---

### Post by hellion0 on 2008-11-27
Brainstorm might work better for this sort of request...

---

### Post by plun on 2008-11-27
> **hellion0 said:**
> Brainstorm might work better for this sort of request...

There is no need for a brainstorm to upgrading apps to latest version.:)
(99% of all and a developer version such as Jaunty)


If a upgrade is refused from a "bug request" there might be need for a "brainstorm"....  OO-3 is one example.

---

### Post by chrisccoulson on 2008-11-27
A bug report is definately the best way to request a package is upgraded in the development release. You should also add the tag "upgrade" for these bug reports too.

Brainstorm is cluttered enough as it is, and it definately is not the place to request package updates.

---

### Post by andrewabc on 2008-11-27
[https://launchpad.net/ubuntu/jaunty/+source/transmission/](https://launchpad.net/ubuntu/jaunty/+source/transmission/)

I would assume they would upgrade transmission to the latest version, same with all other software that was released in 2008. Especially for software that is installed by default.

Hmm, I do see other software that has not been updated in Jaunty.
Specifically: preload
Which is a 2 year old version.

I made a bug report:
[https://bugs.launchpad.net/ubuntu/+source/preload/+bug/302829](https://bugs.launchpad.net/ubuntu/+source/preload/+bug/302829)

---

### Post by chrisccoulson on 2008-11-27
> **andrewabc said:**
> [https://launchpad.net/ubuntu/jaunty/+source/transmission/](https://launchpad.net/ubuntu/jaunty/+source/transmission/)

I would assume they would upgrade transmission to the latest version, same with all other software that was released in 2008. Especially for software that is installed by default.

Hmm, I do see other software that has not been updated in Jaunty.
Specifically: preload
Which is a 2 year old version.

I made a bug report:
[https://bugs.launchpad.net/ubuntu/+source/preload/+bug/302829](https://bugs.launchpad.net/ubuntu/+source/preload/+bug/302829)

There was already a bug report for preload. You didn't need to open another one.

Software doesn't automatically get updated in Ubuntu when a new upstream version becomes available. At the start of every release cycle, packages are sync'd and merge'd with those that are in Debian. (The sync's happen automatically for packages in Ubuntu that have no Ubuntu-specific changes. The merges are generally a semi-automatic process, that may require some manual resolution). If Debian doesn't have the latest upstream version, then Ubuntu won't get the latest upstream version when the package is sync'd or merge'd. In this case, a contributor (or developer) has to package the new upstream version manually (usually in response to a bug report)

---

### Post by andrewabc on 2008-11-27
> **chrisccoulson said:**
> There was already a bug report for preload. You didn't need to open another one.

Software doesn't automatically get updated in Ubuntu when a new upstream version becomes available. At the start of every release cycle, packages are sync'd and merge'd with those that are in Debian. (The sync's happen automatically for packages in Ubuntu that have no Ubuntu-specific changes. The merges are generally a semi-automatic process, that may require some manual resolution). If Debian doesn't have the latest upstream version, then Ubuntu won't get the latest upstream version when the package is sync'd or merge'd. In this case, a contributor (or developer) has to package the new upstream version manually (usually in response to a bug report)

Thanks Chris. I did do a quick look to see if it was already reported, but I didn't see one. (I did ctrl+F preload, but no results when I searched)

---

### Post by chrisccoulson on 2008-11-27
I've prepared the transmission 1.40 update. It's just awaiting sponsorship now

---

### Post by shirishagarwal on 2008-12-01
Its in jaunty. Now if we could get the backport in intrepid now [lpbug]304252[/lpbug].

---

### Post by chrisccoulson on 2008-12-02
Should be a simple backport. In fact, I accidentally already built it for Intrepid whilst I was testing the build of it for Jaunty.

Have you tried building it with [Prevu]("https://wiki.ubuntu.com/Prevu")? If not, I'll do this when I get home from work later.

---

### Post by shirishagarwal on 2008-12-02
oops, I tried assigning the bug to hardy-backports and that backfired. I dunno why.

On the seccond thing, while I don't have any issues with making the package with Prevu but then its just for the self, or I can just upload the resulting .deb to the intrepid backports?

---

### Post by shirishagarwal on 2008-12-03
chris, looking forward to your answer on the same.

---

### Post by Kow on 2008-12-03
Why not just wait until 1.41 is released? 1.40 is actually quite buggy if you look at all of the tickets closed for 1.41. BTW, 1.41 Beta 2 was just released.

[http://trac.transmissionbt.com/query?milestone=1.41&group=component&groupdesc=1&order=severity](http://trac.transmissionbt.com/query?milestone=1.41&group=component&groupdesc=1&order=severity)

Some of those are pretty serious bugs. Such as not being able to add trackers to a pre-existing torrent, randomly losing access to the tracker (I've had this happen with almost every torrent using 1.40). Their initial lazy bitfield support sucks.

---

### Post by chrisccoulson on 2008-12-04
There's no point waiting for a future release which would reduce the window of opportunity for finding and fixing more bugs in the newer versions

Edit: Actually, it's not clear from your post if you're talking about waiting for the Intrepid backport. If you are, then it would be a good idea to wait if 1.40 has quite a lot of bugs which may cause regressions.

---

### Post by ShirishAg75 on 2008-12-19
hi all, 
 how do people to get transmission 1.41 b4 getting it in jaunty .  [http://www.transmissionbt.com/](http://www.transmissionbt.com/) [http://transmission.pastebin.com/m7f7614b8](http://transmission.pastebin.com/m7f7614b8) 

Hopefully somebody has a PPA or something which has the latest for jaunty.

---

### Post by chrisccoulson on 2008-12-19
> **ShirishAg75 said:**
> hi all, 
 how do people to get transmission 1.41 b4 getting it in jaunty .  [http://www.transmissionbt.com/](http://www.transmissionbt.com/) [http://transmission.pastebin.com/m7f7614b8](http://transmission.pastebin.com/m7f7614b8) 

Hopefully somebody has a PPA or something which has the latest for jaunty.

I'll put it in to my PPA this afternoon so people can provide feedback to upstream before the 1.41 release goes in to Jaunty

---

### Post by ShirishAg75 on 2008-12-19
Hi Chrisccoulson, 
 A link to your PPA for the same would be good. You would be doing it for Jaunty or for Intrepid as well?

---

### Post by rudenko_ruslan on 2008-12-19
> **ShirishAg75 said:**
> Hi Chrisccoulson, 
 A link to your PPA for the same would be good. You would be doing it for Jaunty or for Intrepid as well?
Check [this]("https://launchpad.net/~chrisccoulson/+archive"), I think that it's his PPA.

---

### Post by chrisccoulson on 2008-12-19
That's the one. I'm working on it now. I can do a version for Jaunty and Intrepid

---

### Post by chrisccoulson on 2008-12-19
I've uploaded versions for Jaunty and Intrepid, and they're building now. If you wait about 15 minutes or so, you should be able to install it

---

### Post by ShirishAg75 on 2008-12-19
How do I install it? I can see your package :-

```

 apt-cache madison transmission
transmission | 1.34-0ubuntu2.2 | http://archive.ubuntu.com intrepid-proposed/universe Packages
transmission | 1.34-0ubuntu2.1 | http://archive.ubuntu.com intrepid-updates/universe Packages
transmission | 1.34-0ubuntu2 | http://archive.ubuntu.com intrepid/universe Packages
transmission | 1.34-0ubuntu2 | http://archive.ubuntu.com intrepid/main Sources
transmission | 1.34-0ubuntu2.1 | http://archive.ubuntu.com intrepid-updates/main Sources
transmission | 1.34-0ubuntu2.2 | http://archive.ubuntu.com intrepid-proposed/main Sources
transmission | 1.41~b4-0ubuntu0chrisccoulson1~intrepid1 | http://ppa.launchpad.net intrepid/main Sources

```

Update:- Another update process solved it, doing it as we speak.

---

### Post by ShirishAg75 on 2008-12-19
Chris, first issue, if one clicks on preferences, I get a segmentation fault and its down. Any workaround for that in 1.41b4. This is on Intrepid though.

---

### Post by chrisccoulson on 2008-12-19
> **ShirishAg75 said:**
> Chris, first issue, if one clicks on preferences, I get a segmentation fault and its down. Any workaround for that in 1.41b4. This is on Intrepid though.

Hmmm, I can't recreate that on Intrepid. Does it happen with a new user profile?

---

### Post by ShirishAg75 on 2008-12-19
I haven't tried with a new user profile. Would try, a little later though. I'm in a middle of a download as we speak.

---

### Post by plun on 2008-12-19
> **ShirishAg75 said:**
> I haven't tried with a new user profile. Would try, a little later though. I'm in a middle of a download as we speak.

I cannot see any problem except for a really dirty tracker within my own country.  A real "dustbin" **and a shame for my country**  :(:(:(...... India is a heavy user for this junksite.


[http://www.alexa.com/data/details/traffic_details/thepiratebay.org](http://www.alexa.com/data/details/traffic_details/thepiratebay.org)

:mad:

---

### Post by chrisccoulson on 2008-12-19
> **ShirishAg75 said:**
> I haven't tried with a new user profile. Would try, a little later though. I'm in a middle of a download as we speak.

I'm uploading a new version that builds a transmission-dbg package, so you can get a backtrace of the crash

---

### Post by ShirishAg75 on 2008-12-19
chrisccoulson, maybe you can make both a -dbg as well as -dgbsym files. I use dbgsym for debugging.

---

### Post by chrisccoulson on 2008-12-19
> **ShirishAg75 said:**
> chrisccoulson, maybe you can make both a -dbg as well as -dgbsym files. I use dbgsym for debugging.

There is no difference between the *-dbg and *-dbgsym packages that you normally use, other than the filename. Generally, the *-dbg packages you see in the repository are created from some rules in the debian source package, and only some packages have the necessary rules. The *-dbgsym packages you see in the repository are automatically created by the build daemons independently of the rules in the debian source package, as long as the package calls dh_strip and the source is compiled with debugging information (I think). This doesn't happen for PPA's though.

They both contain the same information though - the symbols stripped from the binaries.

---

### Post by ShirishAg75 on 2008-12-22
chrisccoulson, 
 removed transmission from .config and restarted. Got the segmentation fault. 

Ran it through gdb and got the required .dbg file. Lemme know if anything else is needed.

---

### Post by chrisccoulson on 2008-12-23
Thanks. Would you mind installing the following additional packages and then opening a new ticket at [http://trac.transmissionbt.com/]("http://trac.transmissionbt.com/"): libc6-i686-dbgsym, libglib2.0-0-dbgsym, libgtk2.0-0-dbgsym, libcurl3-gnutls-dbgsym.

You can install these packages by following the guide at [https://wiki.ubuntu.com/DebuggingProgramCrash]("https://wiki.ubuntu.com/DebuggingProgramCrash")

---

### Post by ShirishAg75 on 2008-12-23
chrisccoulson,
 [http://trac.transmissionbt.com/ticket/1625](http://trac.transmissionbt.com/ticket/1625) for your convenience

---

### Post by chrisccoulson on 2008-12-23
Thanks Shirish. I'm just uploading a new version with a patch for you to test. If it works, I'll attach the patch to the upstream ticket.

---

### Post by ShirishAg75 on 2008-12-23
chrisccoulson,
still no go with 1.41~b5-0ubuntu0chrisccoulson1~intrepid3 . Still get a segfault. Do you need a debug of the same? Will give you the same after 5 minutes

Update: Here it is. Sorry I had to tar it as the file was 24 KiB but the forums limits to 19.2 KiB.

---

### Post by ShirishAg75 on 2008-12-27
chrisccoulson,
 hope you update the same, 1.42 got released upstream.

---

### Post by taavikko on 2008-12-27
I wish they build-in feature to automatically drop connections 
which tries to shrink windows to try exploit CVE.

dmesg logs are filled with these entries when running extended periods of time :D

Which reminds me to report this, no one is able to fix my concerns until properly notified...

---

### Post by vishalrao on 2008-12-27
shirish, i just moved to jaunty and have transmission 1.40 but cant repro. im also on en_IN locale of course, kernel 2.6.28.3, gnome 2.25.3

---

### Post by vishalrao on 2008-12-28
nevermind, the reason i can't repro is because i have 1.40 r7096, the problem was introduced in r7355. 1.42 release will have the fix. 1.41 should too, looking at their SVN revision log.

---

### Post by ShirishAg75 on 2008-12-28
the bug was reported upstream and was fixed.

---

### Post by ShirishAg75 on 2009-01-04
hope chris coulson does get it in the archive.

---

### Post by ShirishAg75 on 2009-01-06
And the issue is solved. transmission 1.42 is in the archive. Now to get deluge as well.

---

