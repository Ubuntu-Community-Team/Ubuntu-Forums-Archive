---
title: "Installing updates, icon in top right."
date: 2006-05-14
forum: Installation &amp; Upgrades
---

### Post by electronate on 2006-05-14
How do I get updates to install?  Ver. 5.10

Root access I only know how to get through terminal.  I can't login as the root account I setup as a session after Ubuntu starts up.

There is this red cicle with slash that I click and try to "Show updates" or "Install all updates" but get a password window.  I setup three passwords, all the same, for grub, root, and a new user.  So I know I've entered the password right, tried it 5 times already too.  I did an expert install off the cd, so maybe that's my problem, shoulda done regular install being a noob.  I just had to make it hard on myself ](*,) 

Thanks,
Nate

---

### Post by meng on 2006-05-14
Did you use the password for the user account? It's not clear (to me) whether the new user you refer to is your only user, or an additional one.

---

### Post by electronate on 2006-05-14
I think there were three accounts I setup.  One for the boot loader GRUB, one for a regular user, and one for a super user, which I called 'root'... not sure if that name 'root' is a problem.  The account I can log in with as a user works to login, then there are updates waiting in the top right, it asks for a password when i click this.  The passwords I setup for all three accounts were the same in case something like this came up.  So I know I'm entering a correct password, assuming it's one of those three.

Some things I'm thinking:
- I saw a boot loader LILO i could use instead of GRUB.
- Try logging into root through terminal, using apt-get update.

---

### Post by electronate on 2006-05-14
If I don't enter a password and click continue, I get this error message:

"Failed to run /user/bin/update-manager as user root:
 No password was supplied and sudo needs it."

If I purposely enter an incorrect password, this error:

"Failed to run /user/sbin/synaptic --upgrade-mode --non-interactive --hide-main-window as user root:
Wrong password."

Since neither of these showed before, I'm more confident the password I enter regularly is the correct one.  Must be a problem with the apt tool.

---

### Post by electronate on 2006-05-14
Running 'apt-get update' after logging in as su:

Err [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy Release.gpg
  Could not resolve '.archive.ubuntu.com'
Err [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports Release.gpg
  Could not resolve '.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Ign [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy Release
Ign [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports Release
Ign [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy/universe Packages
Ign [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy/universe Sources
Ign [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/main Packages
Ign [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/main Sources
Ign [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/restricted Sources
Ign [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/universe Sources
Ign [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/multiverse Sources
Err [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy/universe Packages
  Could not resolve '.archive.ubuntu.com'
Err [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy/universe Sources
  Could not resolve '.archive.ubuntu.com'
Err [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/main Packages
  Could not resolve '.archive.ubuntu.com'
Err [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/restricted Packages
  Could not resolve '.archive.ubuntu.com'
Err [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/universe Packages
  Could not resolve '.archive.ubuntu.com'
Err [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/multiverse Packages
  Could not resolve '.archive.ubuntu.com'
Err [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/main Sources
  Could not resolve '.archive.ubuntu.com'
Err [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/restricted Sources
  Could not resolve '.archive.ubuntu.com'
Err [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/universe Sources
  Could not resolve '.archive.ubuntu.com'
Err [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports/multiverse Sources
  Could not resolve '.archive.ubuntu.com'
Failed to fetch [http://.archive.ubuntu.com/dists/breezy/Release.gpg](http://.archive.ubuntu.com/dists/breezy/Release.gpg)  Could not r esolve '.archive.ubuntu.com'
Failed to fetch [http://.archive.ubuntu.com/dists/breezy-backports/Release.gpg](http://.archive.ubuntu.com/dists/breezy-backports/Release.gpg)  C ould not resolve '.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release). gpg  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://.archive.ubuntu.com/dists/breezy/universe/binary-i386/Pac](http://.archive.ubuntu.com/dists/breezy/universe/binary-i386/Pac) kages.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch [http://.archive.ubuntu.com/dists/breezy/universe/source/Sources](http://.archive.ubuntu.com/dists/breezy/universe/source/Sources). gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch [http://.archive.ubuntu.com/dists/breezy-backports/main/binary-i3](http://.archive.ubuntu.com/dists/breezy-backports/main/binary-i3) 86/Packages.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch [http://.archive.ubuntu.com/dists/breezy-backports/restricted/bin](http://.archive.ubuntu.com/dists/breezy-backports/restricted/bin) ary-i386/Packages.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch [http://.archive.ubuntu.com/dists/breezy-backports/universe/binar](http://.archive.ubuntu.com/dists/breezy-backports/universe/binar) y-i386/Packages.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch [http://.archive.ubuntu.com/dists/breezy-backports/multiverse/bin](http://.archive.ubuntu.com/dists/breezy-backports/multiverse/bin) ary-i386/Packages.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch [http://.archive.ubuntu.com/dists/breezy-backports/main/source/So](http://.archive.ubuntu.com/dists/breezy-backports/main/source/So) urces.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch [http://.archive.ubuntu.com/dists/breezy-backports/restricted/sou](http://.archive.ubuntu.com/dists/breezy-backports/restricted/sou) rce/Sources.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch [http://.archive.ubuntu.com/dists/breezy-backports/universe/sourc](http://.archive.ubuntu.com/dists/breezy-backports/universe/sourc) e/Sources.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch [http://.archive.ubuntu.com/dists/breezy-backports/multiverse/sou](http://.archive.ubuntu.com/dists/breezy-backports/multiverse/sou) rce/Sources.gz  Could not resolve '.archive.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy_universe_binary-i3 86_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports /main Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backports_ma in_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports /restricted Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backpo rts_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports /universe Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backport s_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports /multiverse Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backpo rts_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-securi ty_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy- security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-se curity_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy_universe_binary-i3 86_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports /main Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backports_ma in_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports /restricted Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backpo rts_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports /universe Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backport s_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://.archive.ubuntu.com](http://.archive.ubuntu.com) breezy-backports /multiverse Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backpo rts_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-securi ty_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy- security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-se curity_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.

---

### Post by electronate on 2006-05-14
[http://www.ubuntuforums.org/showthread.php?t=175229&highlight=multiverse](http://www.ubuntuforums.org/showthread.php?t=175229&highlight=multiverse)

Replaced sources.list code, somehow a period got in front of archive....

---

### Post by electronate on 2006-05-14
[http://www.ubuntuforums.org/showthread.php?t=175229&highlight=multiverse](http://www.ubuntuforums.org/showthread.php?t=175229&highlight=multiverse)

-Followed advice for changing sources.list
-A period got in front of archive
-Didn't use eb-src line from example sources.list at top, had a deb-cdrom line up there.

---

### Post by electronate on 2006-05-14
[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)

Installing anything in Ubuntu...:KS

---

### Post by electronate on 2006-05-14
My problem seems to boil down to Synaptic not functioning...  I've settled on using the terminal version 'aptitude'.  For noobs like me, open a terminal Applications>Accessories>Terminal, then run 'sudo aptitude' or 'su' then 'aptitiude'

---

