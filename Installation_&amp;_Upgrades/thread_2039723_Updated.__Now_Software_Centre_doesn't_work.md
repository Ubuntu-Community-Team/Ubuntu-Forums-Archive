---
title: "Updated.  Now Software Centre doesn't work"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by Rob Sayer on 2012-08-09
Did my daily updates, as usual.  When I tried to run Software Centre immediately after  it crashed.

The message suggested I run the package manager or sudo apt-get.  When I ran sudo apt-get update it seemed to run OK until the last part, where it processes the package list.  This is the error message at this point:

> Reading package lists... Error!
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG A7E13D78E4A4F4F4 Launchpad PPA named smplayer for rvm
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures were invalid: BADSIG AAFF4A5B336064B5 Opera Software Archive Automatic Signing Key 2012 <packager@opera.com>
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.


Then I ran Synaptic Package Manager.  It crashed with the following message:

> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I'm also getting an error message from Update Manager, which I can't copy.  It crashed too.

On top of that there's a Ubuntu 12.04 internal error message.

NOT impressed ...

Any ideas?  I'm seriously hoping it's a problem with their server.

---

### Post by PhoneixS on 2012-08-10
I have the same problem.

EDIT:
I have found the solution in many pages:
> [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] clean
[COLOR=#7a0874]**cd**[/COLOR] [COLOR=#000000]**/**[/COLOR]var[COLOR=#000000]**/**[/COLOR]lib[COLOR=#000000]**/**[/COLOR]apt[COLOR=#c20cb9][B]
sudo[/B][/COLOR] [COLOR=#c20cb9]**mv**[/COLOR] lists lists.old[COLOR=#c20cb9][B]
sudo[/B][/COLOR] [COLOR=#c20cb9]**mkdir**[/COLOR] [COLOR=#660033]-p[/COLOR] lists[COLOR=#000000]**/**[/COLOR]partial[COLOR=#c20cb9][B]
sudo[/B][/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] clean
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] update
From [http://maketecheasier.com/solve-badsig-error-in-ubuntu/2012/01/13](http://maketecheasier.com/solve-badsig-error-in-ubuntu/2012/01/13)

---

### Post by Rob Sayer on 2012-08-10
> **PhoneixS said:**
> I have the same problem.

EDIT:
I have found the solution in many pages:
From [http://maketecheasier.com/solve-badsig-error-in-ubuntu/2012/01/13](http://maketecheasier.com/solve-badsig-error-in-ubuntu/2012/01/13)

Thanks.  I'll try that later.  It happened on my other machine.

---

### Post by cortman on 2012-08-10
Try those commands first, and if that doesn't work, more instructions on how to fix [here]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/").

---

### Post by Rob Sayer on 2012-08-10
It worked.  Thanks all.

---

