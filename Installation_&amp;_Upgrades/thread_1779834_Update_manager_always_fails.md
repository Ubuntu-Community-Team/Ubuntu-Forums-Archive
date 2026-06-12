---
title: "Update manager always fails"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by andrewbtiom on 2011-06-11
Hi all

I'm new to Ubuntu and installed 11.04 on an old Thinkpad T23.  The Live CD worked fine as did an install to the HD, but I get a message from Update manager that there are updates that need to be applied and these always fail.  I've tried selecting different ones in case it is just a particular update, but nothing has updated.  

The error message is below, and I've found this in another post but although the post was marked as solved there was no solution given.  Can anyone help?

Thanks

Andrew

installArchives() failed: Setting up tzdata (2011g-0ubuntu0.11.04) ... 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
dpkg: error processing tzdata (--configure): 
 subprocess installed post-installation script returned error exit status 128 
Errors were encountered while processing: 
 tzdata 
Setting up tzdata (2011g-0ubuntu0.11.04) ... 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
dpkg: error processing tzdata (--configure): 
 subprocess installed post-installation script returned error exit status 128

---

### Post by mörgæs on 2011-06-11
Try to reboot the computer and run 

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```
If you get error messages, please post them.

---

### Post by andrewbtiom on 2011-06-11
Many thanks mörgæs, that worked - all of the apps updated without errors and the update manager now reports there are no more updates.  I didn't really follow what it was that I was doing, but the outcome's good.

Thanks again

Andrew

---

### Post by mörgæs on 2011-06-11
You are welcome.

If you want to learn more about Apt, the manual in my signature is a good place to begin.

---

