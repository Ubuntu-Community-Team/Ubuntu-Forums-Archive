---
title: "Delta debs and using zsync for package updates"
date: 2009-07-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2009-07-16
Recently saw a thread on ubuntu-devel about zsync benchmarks and plans for Karmic for "delta debs". I hope they can pull it off in time for feature-freeze so that it is included in Karmic. Even though my broadband connection is costly and slow, it's a fixed-monthly-price deal so I am willing to help test this when the devs ask us.

Thread start: [https://lists.ubuntu.com/archives/ubuntu-devel/2009-July/028529.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-July/028529.html)
Thread page for other posts: [https://lists.ubuntu.com/archives/ubuntu-devel/2009-July/thread.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-July/thread.html)

Some interesting links from the thread:

[https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads](https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads)
[https://wiki.ubuntu.com/AptSyncInKarmicSpec](https://wiki.ubuntu.com/AptSyncInKarmicSpec)
[https://bugs.launchpad.net/ubuntu/+source/apt-setup/+bug/74747](https://bugs.launchpad.net/ubuntu/+source/apt-setup/+bug/74747)

They're also looking at: [http://dev.chromium.org/developers/design-documents/software-updates-courgette](http://dev.chromium.org/developers/design-documents/software-updates-courgette)

From reading these links, my understanding is the planned "delta deb" feature could turn out superior to Fedora's "delta rpm" (Presto) stuff in the following ways:

1. Deltas are computed on the client thus relieving server load thanks to zsync's use of http range request feature.
2. You can update from version N to any nearby future versions like N+1 or N+2 or N+3 etc but Presto can only do N+1.

Can anyone comment on whats right/wrong here? Any other points to add?

Cheers!

---

### Post by wayne_cat on 2009-07-16
this is something like Fedora Presto?

[http://fedoraproject.org/wiki/Releases/FeaturePresto](http://fedoraproject.org/wiki/Releases/FeaturePresto)

edit: read first ... think ... than answer ... you have mentioned Presto :)

---

### Post by vishalrao on 2009-07-16
Some choice snippets from the above spec link:

> The rsync program of the rsync algorithm is unsuitable for this, primarily because it requires a lot of server-side resources. However, the zsync implementation works around this: the server is a standard HTTP server, and a new data file is added (containing the rsync "signature" data). All the rest of the computation will then happen on the client, which uses HTTP Range requests to fetch parts of the file from the server.

> The RPM world has presto, which relies on the package archive generating delta-RPM packages. These are then downloaded normally, and applied by the client differently from normal RPMs. This requires upgrades to happen from a specific version, which the rsync/zsync/apt-sync approach avoids.

Courgette I think needs server resources again to disassemble and calculate diffs (reassembled on the client) binaries so it might not be nice for volunteer mirrors.

---

### Post by vishalrao on 2009-07-16
> **wayne_cat said:**
> this is something like Fedora Presto?

[http://fedoraproject.org/wiki/Releases/FeaturePresto](http://fedoraproject.org/wiki/Releases/FeaturePresto)

edit: read first ... think ... than answer ... you have mentioned Presto :)

:lolflag: it happens to us all

---

### Post by wayne_cat on 2009-07-16
> **vishalrao said:**
> :lolflag: it happens to us all
Karma +1 for vishalrao :biggrin:

---

### Post by enderandrew on 2009-07-17
> **vishalrao said:**
> Some choice snippets from the above spec link:

Courgette I think needs server resources again to disassemble and calculate diffs (reassembled on the client) binaries so it might not be nice for volunteer mirrors.

However, those mirrors are now transferring much smaller files. File servers are rarely CPU bottle-necked. It is disk IO and network bandwidth that kills them. I'm sure more mirrors would gladly trade disk IO and bandwidth for a little CPU overhead.

---

### Post by vishalrao on 2009-07-17
I wonder if its just a "little" cpu overhead, what with a single mirror serving many users? But I hope the devs get time/resources to test their ideas including whether Courgette is feasible... I will be very happy if this feature overall gets into Karmic...

---

### Post by zekopeko on 2009-07-17
> **vishalrao said:**
> I wonder if its just a "little" cpu overhead, what with a single mirror serving many users? But I hope the devs get time/resources to test their ideas including whether Courgette is feasible... I will be very happy if this feature overall gets into Karmic...

well isn't the whole point that the server generates the diff and then it serves it to all of the users just like a normal .deb which is then merged on the client side? so the server only has to do that only one time and then serve it up.

---

### Post by vishalrao on 2009-07-17
oh, right :) well, im just eagerly awaiting some good news on this front...

---

### Post by nanog on 2009-07-18
I am so very excited about courgette and all the other goodies that google is developing. I think bug #1 will be solved sooner that expected.

---

### Post by vishalrao on 2009-08-10
Does anyone know of or have any updates about this? Things seem to have gone quiet since the last benchmarking activity. And it's worrying for Karmic since feature freeze is so close :(

Is there a webpage/mailing list to track this activity (other than the mail devel/discuss/announce lists)... ?

---

### Post by vishalrao on 2009-08-11
Got the following response on the mailing list from Lars Wirzenius - guy who is doing the benchmarking etc and I guess leading the effort:

> The spec is at [https://wiki.ubuntu.com/AptSyncInKarmicSpec](https://wiki.ubuntu.com/AptSyncInKarmicSpec) but doesn't
change much.

The summary of my conclusions:

* zsync works very well for ISO images (for testers)
* zsync works very well for Packages files
* debdelta works well for .deb files

The ISO images are now having .zsync files generated. This is useful to
reduce the time to do ISO testing cycles during beta and release
candidate testing. Testers need to update their images often. It is not
useful for end-users, who merely need to get the final version;
bittorrent is better for that.

The Launchpad developers will try to implement generation of
Packages.zsync and debdeltas for the karmic release, and I will try to
get the corresponding apt changes done as well. However, since I have
little C++ skill and no experience with the apt code base, this might
not make it for the actual release. If not, then I'll provide a PPA with
the modifications.

There is also the blueprint at [https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads](https://blueprints.launchpad.net/ubuntu/+spec/rsync-based-deb-downloads)

But sadly it looks like Karmic development is already at a good pace and shortage of developer resources and nearby deadlines means this might not make it for the release. There might be a PPA setup and I hope for sure its available for Karmic+1 since this is a killer feature IMO...

---

### Post by vishalrao on 2009-08-14
I just saw the latest Foundations release status at: [https://wiki.ubuntu.com/FoundationsTeam/ReleaseStatus/Karmic](https://wiki.ubuntu.com/FoundationsTeam/ReleaseStatus/Karmic)

Even though this feature is marked as "high" priority its status is "red" or "at high risk for not making it in karmic" :)

The comment says there could be a PPA setup post release as noted above but who knows if the mirror infrastructure will be there to test this well before/into the karmic+1 development cycle: [https://wiki.ubuntu.com/FoundationsTeam/ReleaseStatus/Karmic#Speedup_.debs_Downloads_with_rsync_POC](https://wiki.ubuntu.com/FoundationsTeam/ReleaseStatus/Karmic#Speedup_.debs_Downloads_with_rsync_POC)

This was my number one feature for karmic so I guess I'll have to amuse myself with all the bling that's anticipated instead :lolflag:

---

### Post by Regenweald on 2009-08-14
A wee bit off topic here, but this particular issue is what sparked my interest in Foresight Linux. The Conary package manager. As far as i understand, a .Deb file is a software bundle containing 'sub packages' and in  Conary these sub packages are called Troves. Conary manages software on this level so that rather than downloading an entire .deb, one can simply download actual changes to a software bundle, thus saving precious bandwith and improving the update process. Conary also fully supports rollbacks, a feature planned for Appcentre.

Even though i would love to see Ubuntu using conary, I do appreciate the mammoth undertaking that such a process would be in changing the OS at such a fundamental level. I do believe however, that it is the premier package management solution for our repo-dependent linux distributions. From what i read also it seems that packaging for conary is comparably painless too :)

anyways, just some off/on topic thoughts.

---

### Post by slakkie on 2009-08-15
I don't think this should be included in karmic, or in the next release tbh. I would like to see this being tested for a longer period of time, since it will touch one of the more (if not most) important things in the system: package-management.

I applaud the idea, but I think Ubuntu/Debian should be a bit conservative to include this in upcoming releases. But that we should go to something that support delta's is definitely a good plan.

---

