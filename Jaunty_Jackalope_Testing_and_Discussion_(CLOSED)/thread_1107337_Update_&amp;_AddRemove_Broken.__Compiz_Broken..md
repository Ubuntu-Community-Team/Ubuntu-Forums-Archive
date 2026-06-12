---
title: "Update &amp; Add/Remove Broken.  Compiz Broken."
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by CyberPrime on 2009-03-26
Well, I got my internet working but now synaptic is broken. When I try to update it tells me I have a partial upgrade to do. When I try that it gives me the following error in the Terminal drop down: ```
ERROR:root:SystemError from cache.commit(): E:Internet Error, Could not perform immediate configuration (2) on debconf

** (update-manager:6793): WARNING **:Serious fd usage error 12

** (update-manager:6793(: WARNING **: Failed to send buffer
update-manager: Fatal IO error 9 (Bad file descriptor) on X server :0.0.
none

```
When I go into the Package Manager it says that Compiz is broken, but when I try to remove it it gives me this:
```
E: Internal Error, Could not perform immediate configuration (1) on debconf
``` And hitting "Fix Broken Packages" doesn't do anything.
When I run Add/Remove It pops up with this:
```
Failed to check for installed and available applications.
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.[/CODE]
Upon running sudo apt-get update it runs through the updates and then gives me this: ```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 224D9D15EE176F89
W: You may want to run apt-get update to correct these problems

```
and when I run sudo apt-get install -f it gives me this: ```
E: Internal Error, Could not perform immediate configuration (1) on debconf

```

What could this be? I have searched around but haven't found anything. My internet works (obviously) but for some reason it's still showing the 5 empty bars like I don't have a connection. As well the error icon is next to it (red circle with white line thru it) saying ```
An error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCount > 0' This usually means that your installed packages have unmet dependencies
```

Any ideas?

---

### Post by syko21 on 2009-03-26
disable all of your non-ubuntu repositories for starters.
try
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.BACKUP
```
and then go to System -> Administration -> Software Sources 
enable the all the repositories on the Ubuntu Software tab.
On the updates tab enable the first two repositories and hit close. From here try and update and do an install -f again. If apt tells you about a specific package like package-hello that it is unable to fix then try removing the package.

---

### Post by CyberPrime on 2009-03-29
Nope, everything is the same. I am pretty sure it's all stemming from this one compiz install that refuses to be deleted. This is the error message that seems to be causing it all:
```
E: Internal Error, Could not perform immediate configuration (1) on debconf
```

Any ideas?

---

### Post by SketchyClown on 2009-03-29
Change to a different repository until you don't get the **Partial Upgrade **warning.

***System > Administration > Software Sources ***

---

### Post by syko21 on 2009-03-29
also try

sudo dpkg --configure -a

---

### Post by CyberPrime on 2009-03-29
When I ran ```
sudo dpkg --configure -a
``` I got
```
Errors were encountered while processing:
 compiz
```

Isn't there a sure-fire way to remove compiz? Or maybe stop it from starting?

---

### Post by syko21 on 2009-03-29
Removing the package doesn't work?

sudo apt-get remove compiz

---

### Post by CyberPrime on 2009-03-29
Wow, I guess whatever I did before worked because I just removed compiz and went ahead and updated! Thanks for the help fellas.

---

