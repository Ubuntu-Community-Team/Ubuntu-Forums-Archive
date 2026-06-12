---
title: "This is unbelievable!"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by rowck001 on 2006-06-21
I am starting another thread similar to the user sambler a couple of days ago regarding the debacle that is the xubuntu 6.0.6 CD installs, as I hope someone who knows will tell me this isn't the usual modus operandi for ubuntu distros.

The text based install (xubuntu-alternative) doesnt prompt for or create a main user with the necessary groups to access the system when it is completed, making it a useless piece of binary code on the hard disk without lots of work setting user/groups which most users skilled or not dont have time for!

The ubiquity GUI install (Live CD) wont install on a low-resource (128MB RAM) machine that the whole point of xubuntu is designed for - and requires a machine with (lots of memory) to install to which wouldnt really need to run xubuntu - and then as above, the other available option, the text install, is flawed as well! 

Sounds like a Monty Python Sketch to me!!

Whilst I am not a Linux expert (only 6 months down the track), what I am is a newly graduated Software Engineer and in some of the team projects in the course of my degree (30,000 + lines of code), we would be hung and quartered if we released a deliverable with such a basic errors as exist here!!

This can only be bad for Linux and helps to propagate Microsoft's false propaganda about Linux's ability to be a viable alternative.

If I didnt rely on a couple of Linux applications (some of the best apps I have ever used incidently) I would go back to Windows where at least installs work!

Sorry to be a raving flamer - but I hope my resons can be understood.

---

### Post by Sef on 2006-06-21
> The text based install (xubuntu-alternative) doesnt prompt for or create a main user with the necessary groups to access the system when it is completed, making it a useless piece of binary code on the hard disk without lots of work setting user/groups which most users skilled or not dont have time for!


You had a bad install for some reason.  After partitioning some time, you do set up a  user name and a password.  Sudo is used instead of root. [Root Sudo Link]("https://help.ubuntu.com/community/RootSudo")  To add users or groups, just do this:  System > Administration > Users and Groups.

---

### Post by rowck001 on 2006-06-21
I have installed three times and never do I get an option to set a username and password. I just cannot login when the install completes.

Sef, have you installed the XUBUNTU-alternative CD Image and got to put the above details during install??

---

### Post by nocturn on 2006-06-21
I think Sef is talking about the Ubuntu installer, not the Xubuntu one.

---

### Post by rcarring on 2006-06-21
I used the ubuntu alternate cd. I installed server, then apt-get to install xubuntu desktop after installing xserver-xorg.

Using the ubuntu alternate cd I always get asked to create a user.

The only problem I have now, following the last update is a network connection that moves from eth0 to eth1 on bootup. I have to manually configure it and activate it.

---

### Post by sambler on 2006-06-21
Hello,

I started the thread "Xubuntu install woes" after encountering exactly the same problem: Xubuntu won't install on a machine with 128 mb of memory from the desktop disk, and the text-based install routine didn't prompt me to set up a default user account.

I agree competely that this does not enhance the reputation of Linux as friendly to newbies or easy to install even by semi-experts.

What puzzles me is that there is some evidence that this problem **does not** happen to everyone. A review of Xubuntu was posted on June 17 at:

[http://www.oreillynet.com/linux/blog/2006/06/meet_the_newest_member_of_the.html](http://www.oreillynet.com/linux/blog/2006/06/meet_the_newest_member_of_the.html)

The reviewer used the text-based installation and claims that it worked "flawlessy." I think she was referring mostly to hardware detection, but she does not mention any problems about not being prompted to set up a user account. I've just posted a comment to that review and am waiting for replies to the comment.

It would appear that that the problem happens only sporadically, perhaps depending on the type of computer. If this is the case, it certainly qualifies as a serious bug. I posted a bug report, but the last time I checked it was listed as "unconfirmed." It would be nice to get some detailed feedback from the developers on this problem.

---

### Post by sambler on 2006-06-21
Hi Rcarring,

I also got a working Xubuntu system by doing a server install of Ubuntu and adding the ubuntu-desktop package.

This is straightforward for someone who knows what they're doing, but it does seem to reinforce the point of rowck001 above, "This can only be bad for Linux and helps to propagate Microsoft's false propaganda about Linux's ability to be a viable alternative."

---

### Post by sambler on 2006-06-21
Oops,

Should have typed "xubuntu-desktop package" in previous post.

---

### Post by rcarring on 2006-06-21
I saw that Microsoft recently posted a new whitepaper on why the TCO of Windows Server 2003 is less than "linux", they do use Red Hat, SUSE as the "competition" though.

Seems the only point they could make was the old wives tale that linux distributions are too fragmented to be used as a consistent solution. I would argue the same applies to windows server depending on which service pack and security updates have been installed.

I may do another server install but this time on a very small vm disk, say 3GB all in.

---

