---
title: "Debootstrap Error"
date: 2005-09-14
forum: Installation &amp; Upgrades
---

### Post by Zac on 2005-09-14
Hello to all you fellow Ubuntu users :)

I  have a problem when installing Ubuntu onto my 233Mhz, 64 mb ram, 2 gigs machine. I would really appreciate any help and advice that can be given so that I could reach my goal of successfully installing Ubuntu as a server.

I started off booting from the cd and running the 'server' setup for Ubuntu Hoary Hedgehog 5.04. Then once I got to the partitions menu this is how I set it up.

IDE2 master (hdc) - 2.1 GB WDC AC22100L
	#1 primary  1.7 GB     ext3	   /
	#2 primary  403 MB     swap	swap

After doing that I finished partitioning and wrote the current partitions to disk.

The installation goes well antil 6%, I get a error that says:

'Debootstrap Error."
'Couldn't retrieve apt. This may be due to a network problem or a bad CD, depending on your installation method.

If you are installing from a CD-R or CD-RW, burning the CD at a lower speed may help.'

What I've found out is that it couldn't be the cd because i have installed Ubuntu onto a different system with the same disk and all went well and everything is running 100% at the moment on that machine.

After getting the debootstrap error and entering to continue I get a error as follows:

"Failed to install the base system"
'The base system installation into /target/ failed.

Check /var/log/messages or see virtual console 3 for the details.'

Once I get this message I went over to the virtual console 3 for the details and this is what I get over there:

'No volume groups found
Reading all physical volumes. This may take a while...'

And from there on I really have no clue what to do. :(
I've tried all that I could possibly think of and I've read all the other posts on Debootstrap Errors and have had no luck.

I would really appreciate it if someone could give me some advice on what to do next or what I could try that may help in the least.

Thanks Zac.

---

