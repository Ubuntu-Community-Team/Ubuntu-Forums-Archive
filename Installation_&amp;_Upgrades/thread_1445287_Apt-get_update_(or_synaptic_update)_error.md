---
title: "Apt-get update (or synaptic update) error"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by wcorey on 2010-04-02
Hi,
   On a recent install of U9.10 It was either I or Synaptic Package Manager was trying to do routine maintenance. Here is what I get when trying to do it with apt-get update. 


Fetched 60.6MB in 2min 29s (405kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...u1.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/...u1.1_amd64.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...u5.6_amd64.deb](http://us.archive.ubuntu.com/ubuntu/...u5.6_amd64.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...u5.6_amd64.deb](http://us.archive.ubuntu.com/ubuntu/...u5.6_amd64.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...10.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/...10.1_amd64.deb) Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

This has gone for days. What do I try now, it is a fresh install of 9.10 Desktop.

On an existing 9.10 system this has been occuring for several days, if not weeks.

Failed to fetch [http://dl.google.com/linux/deb/pool/main/g/google-chrome-beta/google-chrome-beta_5.0.342.7-r42476_amd64.deb](http://dl.google.com/linux/deb/pool/main/g/google-chrome-beta/google-chrome-beta_5.0.342.7-r42476_amd64.deb)  Hash Sum mismatch

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.0-3ubuntu5.6_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.0-3ubuntu5.6_amd64.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I have tried running it with --fix-missing

I have also tried this on two machines, so it is not environmental.

Thanks,

Walt

---

### Post by shashi859 on 2010-04-02
It appears that the repository servers are down.
Just try changing to other repository servers from present server from which apt-get is failing to fetch softwares ..change can be done in synaptic repository settings or from software sources ,i e system>preferences>software sources

---

### Post by wcorey on 2010-04-02
Sorry...didn't mean Synaptic Package Mgr, I meant the System->Administration->Update Mgr

---

### Post by shashi859 on 2010-04-02
you can do that from update manager also.open update manager>ubuntu software>download from
Then select different server than previous...

---

### Post by wcorey on 2010-04-02
I tried "Pick Best" under "Other" which is dutifully performed. What I've noticed in the past in the gui refresh as well as apt-get update is it rolls through all the packages and then stops for an inordinately long period of time, when I get this message. On the new server it stopped 2 prior to the last, not at the last.

Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/karmic/universe/binary-amd64/Packages.bz2](http://archive.linux.duke.edu/ubuntu/dists/karmic/universe/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

I tried yet another source and received the following:

72% [12 Packages bzip2 0] [13 Sources 2417/2,795kB 0%] [Waiting for headers]   
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages                      
  Sub-process /bin/bzip2 returned an error code (2)
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages [185kB]            
98% [13 Sources bzip2 0] [14 Packages 577/185kB 0%] [Waiting for headers]      
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources                    
  Sub-process /bin/bzip2 returned an error code (2)

---

### Post by shashi859 on 2010-04-02
just google like  'Hash Sum mismatch' ,i got some ubuntuforums posts who faced similar problem..just look at it once..you may get soln

---

### Post by wcorey on 2010-04-02
I actually did that. Here's the problem, and this is, unfortunately, indemic to forums, not just this one. Some really high percentage of responses, although all are well meaning, effectively are 'try this'. 

I am actually in the software development business and yes, occasionally, some developer 'breaks the build'. Since, in the case of Ubuntu, I am not in the build and deploy loop I would expect after a day or two or a week the problem will resolve itself. So far this has not been the case. 

In some of the hits I see that someone has added a source or changed something. Perhaps they brought the problem on themselves. In this case it happened all on its lonesome. I am just now trying University of Chicago, and it is stopping at 43 of 45. Duke University got to 44 of 45, and main stalled on 45 of 45.

Doing this with apt-get it appears to stall right after it prints multiverse sources. Does one need multiverse sources? I didn't turn that on so I hesitate to turn that off.

ailed to fetch [http://archive.linux.duke.edu/ubuntu/dists/karmic/main/binary-amd64/Packages.bz2](http://archive.linux.duke.edu/ubuntu/dists/karmic/main/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/karmic/universe/binary-amd64/Packages.bz2](http://archive.linux.duke.edu/ubuntu/dists/karmic/universe/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: GPG error: [http://astromirror.uchicago.edu](http://astromirror.uchicago.edu) karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://astromirror.uchicago.edu/ubuntu/dists/karmic/main/source/Sources.bz2](http://astromirror.uchicago.edu/ubuntu/dists/karmic/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

As you can see, the above messages come from two different sources but appear to be the same package? I can't see my previous post but I recall one called out two packages.  At any rate, I switched to Ubuntu years back from another distro because of the "It just works" image, if not mantra. So far I've spent hours spanning days on this and I do not believe this qualifies as "It just works". So I guess a follow-up question is, do the MOTU folks know there is a problem?

Walt

---

### Post by davit on 2010-04-05
> **wcorey said:**
> I actually did that. Here's the problem, and this is, unfortunately, indemic to forums, not just this one. Some really high percentage of responses, although all are well meaning, effectively are 'try this'. 
....
..
.
.
...

As you can see, the above messages come from two different sources but appear to be the same package? I can't see my previous post but I recall one called out two packages.  At any rate, I switched to Ubuntu years back from another distro because of the "It just works" image, if not mantra. So far I've spent hours spanning days on this and I do not believe this qualifies as "It just works". So I guess a follow-up question is, do the MOTU folks know there is a problem?

Walt


I have been trying to update and install various Ubuntu's on a box from Ubuntu disks and from my own burnt iso's.  

I sill having problems after two day trying to get a repository to work on a update.  All giving a hash-sum mistmatch or a bzip2 error. some at 99% download.

I had this problem before last year but moved away from EUROPEs mirrors ato US side which solved the problem then. This time I can not find a mirror that seems the work on the update.

I checked a few iso's md5sums and found I could not get to downloaded iso to match the MD5's as printed on Ubuntu Source server.

Would it be the network pipes?

---

### Post by wcorey on 2010-04-11
> **davit said:**
> I have been trying to update and install various Ubuntu's on a box from Ubuntu disks and from my own burnt iso's.  

I sill having problems after two day trying to get a repository to work on a update.  All giving a hash-sum mistmatch or a bzip2 error. some at 99% download.

I had this problem before last year but moved away from EUROPEs mirrors ato US side which solved the problem then. This time I can not find a mirror that seems the work on the update.

I checked a few iso's md5sums and found I could not get to downloaded iso to match the MD5's as printed on Ubuntu Source server.

Would it be the network pipes?


I doubt it has anything to do with network as tcp does check message consistency with source via the tcp header checksum.

Like yourself I have tried multiple repository locations and they are all bad. Actually this would be consistent if the source were bad that would be replicated to all mirrors. Similarly, once the source is fixed, it would eventually be fixed at the mirrors by virtue of replication. Or so the theory goes.

I have seen references to hash mismatch in Launchpad. Unfortunately one of them was allegedly closed because the author apparently moved on. 

What would be interesting is if someone where to respond and say, I am on 9.10 and use the 9.10 repositories and they work just fine for me at <location>.

I did find, for 10.4 they had the same problem and someone reported, "Hey not broken yet in the Netherlands", followed by "Cool, problem solved". So I thought, first, oh, so the mirrors are fracked in 10.4 as well but maybe not in Netherlands (yet). Well, I am here to report, at least for 9.10, they are broken now. 

Finding a place where it is not broken doesn't mean it's fixed, merely not broken there yet.  I found another hit where they said the problem was apt-get and aptitude worked fine. Nope, not any more it doesn't...that's assuming the problem was actually not bad data being replicated when MOTU put out the upgrade packages. Me thinks there is a whole bunch of "la la la la la la la" going on here. This is really frustrating.

---

### Post by wcorey on 2010-04-25
The executive overview of this is try recycling your cable modem after removing any batteries for e911 backup.

Discussion:

Hopefully this post will be found by others and provide some assistance if they run into the infamous hash sum mismatch.

As mentioned previously, this situation has been causing great distress to me for perhaps a month or so. Since I saw this error on 4 machines in 2 locations I assumed the singular thing they had in common was the Ubuntu repositories. As a previous post in this thread asked, could it be the network. I did dismiss that as a bad tcp packet would be tossed by the stack and never see the underlying client application. 

I was on a Windows machine updating iTunes when it also failed with bad signature. Well, this seems semantically the same as hash sum mismatch. This was a separate machine natively running Windows. So it no longer was a Ubuntu repository issue. In looking up bad signature I ran across one post that said effectively, as unintuitive as this sounds, try another router. Again, see tcp header check sum. My initial reaction was, "I don't think so" but now I have a more wide-spread issue. Unless I had a virus on 4 machines, Linux and Windows, I was hard pressed not to try recycling the Netgear router (to no avail) and recycling the cable modem. 

Not only did that fix the problem it also doubled my network connection speed. 

I would really appreciate it if someone would explain how a good source file could be 'properly' received by a client and yet, be bad when it got to the client.  Oh, does http not do checksums or crc's as tcp does in its packets? I am at a loss to explain this.

As I was so previously vocal I wanted to post what turned out to be the issue, in this case. This, of course, doesn't explain why I had the problem on my office server as well.

---

### Post by denzykabzy on 2010-04-26
> **wcorey said:**
> I doubt it has anything to do with network as tcp does check message consistency with source via the tcp header checksum.

Like yourself I have tried multiple repository locations and they are all bad. Actually this would be consistent if the source were bad that would be replicated to all mirrors. Similarly, once the source is fixed, it would eventually be fixed at the mirrors by virtue of replication. Or so the theory goes.

I have seen references to hash mismatch in Launchpad. Unfortunately one of them was allegedly closed because the author apparently moved on. 

What would be interesting is if someone where to respond and say, I am on 9.10 and use the 9.10 repositories and they work just fine for me at <location>.

I did find, for 10.4 they had the same problem and someone reported, &quot;Hey not broken yet in the Netherlands&quot;, followed by &quot;Cool, problem solved&quot;. So I thought, first, oh, so the mirrors are fracked in 10.4 as well but maybe not in Netherlands (yet). Well, I am here to report, at least for 9.10, they are broken now. 

Finding a place where it is not broken doesn't mean it's fixed, merely not broken there yet.  I found another hit where they said the problem was apt-get and aptitude worked fine. Nope, not any more it doesn't...that's assuming the problem was actually not bad data being replicated when MOTU put out the upgrade packages. Me thinks there is a whole bunch of &quot;la la la la la la la&quot; going on here. This is really frustrating. thanks wcorey, i tried the Netherlands' Ubuntu server and my update manager worked very well!!!!! I tried it for karmic and everything is working fine now.

---

### Post by saney2 on 2012-06-22
Thanks for the message, this led me on the right track. I'm in China and got these messages a lot recently, independent of which server I'd select. Turning on my VPN connection to my university in Germany solved the problem. My guess is that the great firewall changes the TCP packets, which then leads to mismatching hash sums.

---

### Post by davedorm on 2013-02-17
I'll be dipped, it recycling my router worked! I would have never thought that would help. I looked at other solutions, such as using a different repo. But this was a PPA and a different repo was not possible.

Old posts come through, thanks for keeping this live.

---

