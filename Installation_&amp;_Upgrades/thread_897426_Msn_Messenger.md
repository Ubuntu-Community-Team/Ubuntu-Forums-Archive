---
title: "Msn Messenger?"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by jontas7 on 2008-08-22
Hi there :D

Is it possible to install MSN Messenger on Ubuntu ? cuz i dont like Pidgin very much :/
So is it possible and how do i do it then :O

Thankful for answers.

---

### Post by Partyboi2 on 2008-08-22
A program similar to msn is amsn, its in the ubuntu repos and can be install by add/remove, apt-get.

---

### Post by redneckclutch on 2008-08-22
amsn is similar in many ways to MSN messenger. MSN messenger does not install on linux.   [http://www.amsn-project.net/](http://www.amsn-project.net/)
I use amsn, and am satisfied with the results

---

### Post by Scunge on 2008-08-22
My kids used aMSN 0.95, but recently reported that it stopped working. I dug around on the web and found a few articles about Microsoft changing the protocol somehow and it affecting even older versions of MSN messenger itself.

I got them to use Gaim (still on Dapper) but they prefer the bells and whistles that aMSN gives them. Kids, eh?

Anyway, can anyone confirm what is the earliest version of aMSN that is working at the moment, either with Dapper or Hardy?
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by jkyahoo101 on 2008-08-23
My amsn stopped working a few days ago but then I saw updates for it in the update manager and they fixed the problem whatever it was.

---

### Post by Sef on 2008-08-23
There is also emesene.   

Both emesene and amsn are available from add/remove.

Applications > Add/Remove > Show: All Available Applications > Search: emesene (or amsn) > apply changes > apply > close.

---

### Post by Scunge on 2008-08-24
I'll have a look a emenene.

The aMSN in Dapper's repositories is still 0.95-1. How do I get access to later versions through the respoitories (i.e. without having to download and compile the source, which also means that it will get automatically updated via the Update Manager as well)?

Edit: emesene isn't in Dapper's repositories at all. Yes, I have everything up to and including multiverse enabled.

Edit 2: Ok, I'm going to download the packages using a Hardy installation and copy them over to install in the Dapper system. Other than making sure I have all the dependencies (which it will tell me if I haven't, right?), anything else I should be aware of about doing this?
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by Sef on 2008-08-24
> The aMSN in Dapper's repositories is still 0.95-1. How do I get access to later versions through the respoitories (i.e. without having to download and compile the source, which also means that it will get automatically updated via the Update Manager as well)?

[amsn]("http://www.amsn-project.net/linux-downloads.php") uses autopackage which is easy to use to install:  Just follow the directions.

---

### Post by Scunge on 2008-08-24
Ok. I got aMSN 0.97 installed but it wasn't entirely plain sailing.

Here's what went on in case others want to try it out.

This is using **Ubuntu Dapper Drake 6.06**, but the crash I mention might occur for other releases or distributions, so it's here in full.

I went to the [**[COLOR="Blue"]aMSN download page[/COLOR]**](http://www.amsn-project.net/linux-downloads.php) and in there it talks about a different version of the package to download depending on which version of Tcl/Tk is already installed. Dapper has 8.4, so that meant [**[color=blue]this download[/color]**](http://prdownloads.sourceforge.net/amsn/amsn-0.97.2-1.tcl84.x86.package).

I followed the instructions on the [**[color=blue]How to install Linux autopackages in 4 easy steps[/color]**](http://www.autopackage.org/docs/howto-install/) page and then ran aMSN's .package file after uninstalling the existing aMSN available through Dapper's repositories (version 0.95). The new aMSN package installation said that it needed to install some autopackage stuff first, so off that went.

During the installation for these, it asked for the "system password", but giving it the root password didn't seem to help. It failed on all three attempts so I had to run the package again. This time, however, I chose "No password" and it says on the tooltip for that that that means it will install the package manager for me only - fair enough, actually, I think that's better than allowing just anyone to install anything.

It completed the installation of autopackage itself and then went on to install aMSN.

Or not. It just finished, no menu option. Tried again, no change.

At the bottom of the "How to install" page it says how to run the package manager on the command line. So, based on that, I started a terminal window and entered the following command (the '$' at the start of the line represents the prompt, this is not part of any command)...
```
$ bash amsn-0.97.2-1.tcl84.x86.package
FAIL:Install the package with the command 'package install' instead.
```

Ok, then...
```
$ package install amsn-0.97.2-1.tcl84.x86.package
/home/xxx/.local/share/autopackage/apkg-io: line 309: 15553 Floating point exceptionautopackage-frontend-gtk "$@"
```

Eek! After a quick search, I found [**[color=blue]this error report[/color]**](http://trac.autopackage.org/ticket/87), and it seems that the standard autopackage installer doesn't work in Dapper. A new version was required, available (it says later) as [**[color=blue] an attachment[/color]**](http://trac.autopackage.org/attachment/ticket/87/autopackage-gtk-1.2.5.package) to that error report. Downloaded that and tried to run it as instructed in the error report...

```
$ package remove autopackage-gtk
Removing currently installed version of 'Autopackage Software Installer (GTK+)'.This may take a moment, please wait ... done

$ package install autopackage-gtk-1.2.5.package
package is in the database but was not installed by autopackage

```

Does that mean it's worked or not? Tried again...
```
$ package remove autopackage-gtk
Removing currently installed version of 'autopackage-gtk'.
This may take a moment, please wait ... failed
FAIL: Package autopackage-gtk was not found.

$ package install autopackage-gtk-1.2.5.package
package is in the database but was not installed by autopackage
```

I decided to try installing aMSN anyway, it seems like the old version was removed ok and that messages may not be an actual error...
```
$ package install amsn-0.97.2-1.tcl84.x86.package
# Preparing package: AMSN MSN client
# Checking for required C library versions ... passed
# Checking for X ... passed
# Checking for TCL Scripting Language ... passed
# Checking for Tk GUI Toolkit ... passed
# Installing package: AMSN MSN client (package 1 of 1)
# 100%[==================================================] Extracting
# Preparing executables...
# Installing data files...
# 100%[==================================================] Copying
# Installing executables...
# Installing menu items...
# Installing icons...
# Updating package database...

The following package was successfully installed:
* AMSN MSN client

The following menu entry is now available:
* aMSN (Network, InstantMessaging)

This installation used 8.13 MiB (8.52 MB) of disk space.


Remove this package by running package remove amsn from the command line.
```

Great!

Now, I can get it to run, but when another user on the computer tries to use it, it's not in their menu.

Edit:

The reason aMSN's not available to others is because all that instllation I did above has operated only on my user account, i.e. aMSN is installed in /home/xxx/.local/bin. Obvious, really, once I think about it!

I've seen people talking about running the installation using "sudo", but having tried that with aMSN it just installs it in my local directory again. I guess the initial package manager run should have been done with "sudo", and perhaps then it would have installed itself globally and hence aMSN would then be global. Perhaps.

I'm also annoyed that there is now an "autopackage.nnnnnnn" folder in my home directory; is it a temporary one from the installation, or necessary to run aMSN (whose name appears in folders within it)? I don't want installations to scatter things around, whether as left-overs or as part of installed programs. If it's the former then that's just sloppiness; if it's the latter, isn't that what /home/xxx/.local/bin is for?

So I don't know how autopackage will work when installed globally and I now don't really care to experiment with it.

If you want more than one user to use aMSN it works fine just installing the package manager locally and their own copy of aMSN with that. Note that this does not work if you "su" in as them in a terminal window - you have to be actually logged in as them. Reason? The Tk GUI check will fail with no actual GUI to get parameters from.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by gjoellee on 2008-08-24
click on the link and wait a few seconds
[apt://amsn](apt://amsn)

---

### Post by Scunge on 2008-08-24
Sorry, that doesn't work for me. I get "Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program".

Anyway, sorted out multiple users, well, not ideally, but it works. I've edited my post above to talk about that too, keep it all in one place.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by e2k on 2008-08-24
I really recommend emesene, imho it feels faster and more up-to-date than pidgin (in terms of msn functions). Closest you'll get to the Windows version (if that is what you're looking for that is)..

---

