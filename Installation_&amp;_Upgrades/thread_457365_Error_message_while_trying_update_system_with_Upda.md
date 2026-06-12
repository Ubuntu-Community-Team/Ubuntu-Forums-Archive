---
title: "Error message while trying update system with Update Manager"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by mmmpancakes on 2007-05-28
Whenever I try to run the Update Manager, I get this error message:

> A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing thekompany-support (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Thanks in advance.

---

### Post by hoornet on 2007-05-28
I tred to install debian package of Skype and the result is that Updater doesn't work any more.
This is what I get:


E: The package skype needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Please help

P.S. I Also get this:
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package skype needs to be reinstalled, but I can't find an archive for it.'

---

### Post by fawkes on 2007-05-28
Pancakes: 

I'm getting the same error, verbatim. I used Automatix a couple of days ago to d/l and install a single program (i'm trying to remember what it was.) I HAVE run update manager since then and it worked fine. Now, today, this.

If you find a solution, please post? 

T.I.A.

---

### Post by arnieboy on 2007-05-28
The erring package has long been fixed and a simple

```
sudo apt-get update
```

will fix this issue

---

### Post by fawkes on 2007-05-28
Arnieboy:

Awesome.

Thanks!! 

Excuse the noobs...

---

### Post by mmmpancakes on 2007-05-29
That solution worked perfectly. Thanks, all.

---

### Post by raphenry on 2008-03-04
[COLOR="Navy"]This the message I got before the sudo apt-get update[/COLOR]

E: firehol: subprocess post-installation script returned error exit status 1

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E[COLOR="Navy"]23C5FC3

this is the one i get after sudo apt-get update[/COLOR]

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: You may want to run apt-get update to correct these problems

[COLOR="Navy"]Any suggestions[/COLOR]

thanks

---

### Post by zvacet on 2008-03-05
Applications>accesssories>terminal type

gpg --keyserver hkp://subkeys.pgp.net --recv-keys CC919A31E23C5FC3
gpg --export --armor CC919A31E23C5FC3 | sudo apt-key add -

```
sudo apt-get update
```

---

### Post by raphenry on 2008-03-09
E: firehol: subprocess post-installation script returned error exit status 1

I still receive the above error whenever i update thru the update manager.

---

