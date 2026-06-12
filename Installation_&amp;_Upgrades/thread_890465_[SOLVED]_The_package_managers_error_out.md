---
title: "[SOLVED] The package managers error out"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by kflorek on 2008-08-15
This is using Hardy Heron i386.

I had lots of packages lined up to install from Synaptic. Synaptic began the downloads, but since my connection had been dropped, it just did some stuff from the DVD. Then it errored out. This is what the error box said:

BEGIN

An error occured

The following details are provided:

E: The package emacspeak is not OK and I don't know how to fix it!
E: Internal error opening cache(1). Please report.

END

And then synaptic closes when I close the error box. If I start up Synaptic, I immediately receive the same error box before anything can be done.

Unfortunately all the package managers do likewise, so I can't get packages to install that way.

Update Manager
BEGIN

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package emacspeak is not ok and I don't know how to fix it!'

END

The yellow box message when I hover over the system tray is a little different:
BEGIN

The error message was: 'Unkown Error:'<type'exceptions.SystemError:'>'(E:The package emacspeak is not ok and I don't know how to fix it!)'This usually means that your installed packages have unmet dependencies.
END



apt-get gives me this:

BEGIN

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package emacspeak is not ok and I don't know how to fix it!

END


aptitude crashes when I try to install anything. It dumps me to the command prompt, where I get this:

BEGIN
kflorek@nfii-ubu10:/media/cdrom0/pool/main/e/espeak$ sudo aptitude
Ouch!  Got SIGSEGV, dying..
Segmentation fault
END

I didn't see a package named "emacspeak" on the DVD, but there is "espeak"

dpkg will install and uninstall packages:

kflorek@nfii-ubu10:~$ sudo dpkg -r emacspeak
dpkg - warning: ignoring request to remove emacspeak which isn't installed.
kflorek@nfii-ubu10:~$ cd /media/cdrom0/pool/main/e/espeak
kflorek@nfii-ubu10:/media/cdrom0/pool/main/e/espeak$ sudo dpkg -i espeak_1.36-0ubuntu1_i386.deb 
(Reading database ... 121834 files and directories currently installed.)
Preparing to replace espeak 1.36-0ubuntu1 (using espeak_1.36-0ubuntu1_i386.deb) ...
Unpacking replacement espeak ...
Setting up espeak (1.36-0ubuntu1) ...
kflorek@nfii-ubu10:/media/cdrom0/pool/main/e/espeak$ sudo dpkg -r espeak
(Reading database ... 121833 files and directories currently installed.)
Removing espeak ...

 Installing espeak didn't change anything. Uninstalling it didn't either.

 I could get packages by wget I guess and install with dpkg, but I'm lost.

 So how do I get out of this?****

---

### Post by kflorek on 2008-08-16
I rebooted the computer and tried everything again, which changed nothing.

For fixing dependencies, it is somewhere recommended to do

sudo apt-get install -f

which gave me: Segmentation fault.


Since the problem involved emacspeak, which I never tried to install, unless it was some kind of dependency, I downloaded it directly from the unbuntu repository and attempted to install it, which naturally failed due to a dependency on emacs, etc. It changed nothing of course.

For fixing configuration problems, it is somewhere recommended to do

sudo dpkg --configure -a

This gave me a bunch of dependencies, such as emacs, but no errors of the weird kind. Hmm... So let's try removing emacspeak...

sudo dpkg --remove emacspeak

No errors about emacspeak! Let's retry the configuration fix and the dependency fix:

sudo dpkg --configure -a
sudo apt-get install -f

No strange errors!

And Synaptic works! So does apt-get.

Apparently there was an error in the package information that involved emacspeak, bad enough to crash programs. Installing emacspeak, even though it failed, redid some part of the packing information, and uninstalling it deleted the dependencies. Maybe.

I don't get it, but I'll take it. I was about to reformat and reinstall.:KS

---

