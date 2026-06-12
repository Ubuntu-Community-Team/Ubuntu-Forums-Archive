---
title: "Vmware windows"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by Frankie88 on 2007-06-01
I really have not got a clue when it comes to computers let alone linux and ubuntu.

so here is the problem: my vmware no longer opens when i load it.

I type vmware into the terminal and it says:

"vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl."

I type in that command and it replies: 

"Please re-run this program as the super user.

Execution aborted."

I type in "su" and my username and password and then type in the "/usr/bin/vmware-config.pl" command and it still says:

"Please re-run this program as the super user.

Execution aborted."

can any one help!!! please? as far as i am aware i am the SU

---

### Post by PilotJLR on 2007-06-01
do this:
```

sudo vmware-config.pl

```

"sudo" makes the command following it be run as superuser.

---

### Post by Frankie88 on 2007-06-02
Thanks,

I have done that and I now have a nother problem. 
it now says:

"Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]"

However, I do not know where the location of the directory of C header files are... is there any way in which i can find out?

---

### Post by PilotJLR on 2007-06-02
This likely means you don't have them. Easy fix though... type this out (or copy paste) verbatim please:

```

sudo apt-get update
sudo apt-get install build-essential linux-headers-`uname -r`

```

---

### Post by PilotJLR on 2007-06-02
ALSO - IF you are running Feisty (version 7.04), also apply the patch as described here:
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

If you are using Edgy, this patch is not needed.

---

### Post by veloce on 2007-06-03
And, if you are using Feisty,  if this is all too hard, uninstall your version of vmware and install the version from the commercial repository.

---

### Post by hoggbottom59 on 2007-06-03
Alternatively even easier is to:

uninstall it.
install a program called Automatix. It's another package installer than will appear in your Applications-System Tools menu.

Run this and install Vmware using this.

The Vmware Server is now free and allows you to actually make virtual machines unlike the older player.

Try to always use the package managers for installation. They'll require a password but they do everything for you. 

Unlike the Windows Add/Remove Programs the package managers allow you to install a world of software without hunting for it.

Have fun and experiment with Linux you'll find it has features Microsoft could only dream of.

Leon.

---

### Post by veloce on 2007-06-04
> **hoggbottom59 said:**
> Alternatively even easier is to:

uninstall it.
install a program called Automatix. It's another package installer than will appear in your Applications-System Tools menu.

Run this and install Vmware using this.

The Vmware Server is now free and allows you to actually make virtual machines unlike the older player.

Try to always use the package managers for installation. They'll require a password but they do everything for you. 

Unlike the Windows Add/Remove Programs the package managers allow you to install a world of software without hunting for it.

Have fun and experiment with Linux you'll find it has features Microsoft could only dream of.

Leon.

Where would I find automatix?  is it in the repos somewhere?

---

### Post by veloce on 2007-06-04
.

Sorry, accidentally doubled up here.

---

