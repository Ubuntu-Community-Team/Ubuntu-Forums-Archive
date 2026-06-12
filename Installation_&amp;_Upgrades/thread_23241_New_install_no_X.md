---
title: "New install no X"
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by deucedlt on 2005-03-31
Hi all. I'm a semi-newbie linux hobbyist. Have had some success with redhat,vector
and even peanut distros, thought I'd try ubuntu. First install went OK until login
when X wouldn't start. Using an AMD K6 350 with 256M ram and a 6-gig HD, with
W98 on the first 3 gigs & ubuntu on the rest. I used the warty-release-install-ii386.iso. This message: "This is a pre-release version of Xfree86, and is not supported in any way.
   Xfree Version 4.3.8.1
   Release Date: 15 August 2003
   X Protocol Version 11, Revision 0, Release 6.6
   Build Date: 18 Oct. 2004
   Build Operating System:Linux 2.6.8.1 i686 [ELF]
I am somewhat clueless about what to do next and would appreciate advice. I have an internet capable redhat setup on my other disk but am stuck at the command prompt in the new ubuntu install.

---

### Post by Whiffle on 2005-03-31
Dig around in /var/log/ and you'll find a log file for X.  If you look  through that you'll probably find an error somewhere, they usually start with EE at the front of the line, and WW are warnings but usful sometimes too.  Let us know what you find and we'll go from there.

---

### Post by deucedlt on 2005-04-01
Thanks Whiffle. I checked file you referenced and found driver error which i fixed
wih a reinstall. (I chose s3Virge instead of incorrect s3 for my s3trio3D video card)
After logging in at the login screen the gnome desktop started up OK. Then I opened a terminal, ran: sudo passwd root to setup, but now i was unable to login
as root at the login screen. root seems to work OK for other stuff once logged in
as ordinary user. Can I do something to make the login screen accept root login?

---

### Post by candc540 on 2005-04-01
[QUOTE=deucedlt]Thanks Whiffle. I checked file you referenced and found driver error which i fixed
wih a reinstall. (I chose s3Virge instead of incorrect s3 for my s3trio3D video card)
After logging in at the login screen the gnome desktop started up OK. Then I opened a terminal, ran: sudo passwd root to setup, but now i was unable to login
as root at the login screen. root seems to work OK for other stuff once logged in
as ordinary user. Can I do something to make the login screen accept root login?[/QUOTE]

if using GDM, edit your /etc/gdm/gdm.conf file and look for allowrootaccess or allowroot something like that and change from false to true that's all there is to it

---

