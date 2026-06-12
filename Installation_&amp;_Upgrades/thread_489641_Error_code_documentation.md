---
title: "Error code documentation"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2007-07-01
Perhaps I am looking in the wrong places, but where do I find a list of error codes for Ubuntu, what the codes mean, and how does one correct the problem?  An example of an error code I need help on is:

The error code is: 1

John

---

### Post by kidders on 2007-07-02
Hi there,

There are no Ubuntu-specific error codes or messages. What returned "1" to you?

[SIZE=1]A little background, just in case you need it...

Executing processes typically return a numeric value to the parent process when they're done, to describe the manner in which they terminated. (By convention, this is always zero, under normal circumstances.) The parent process can then decide whether to proceed, based on whether any subprocesses it spawns fail to do their jobs properly. To pull an example out of thin air ...> [SIZE=1]RETURN VALUE
0      The action was successfully executed.
1      The  user to delete was not a system account. No action was performed.
2      There is no such user. No action was performed.
3      There is no such group. No action was performed.
4      Internal error.
5      The group to delete is not empty. No action was performed.
6      The user does not belong to the specified group.
7      You cannot remove a user from its primary group.
[/SIZE]I lifted this straight out of **deluser**'s man page. It describes what the various error codes it might return are intended to mean. Besides these, there are a few additional conventions ... for instance, an exit code of 11 (even though this particular command's documentation doesn't mention it) is generally taken to mean "Segmentation fault".
[/SIZE]
So, that's why I asked the question above. In general terms, "1" often indicates a non-specific failure that involves no special circumstances that might be of interest to a parent process, but it's impossible to be any more specific than that without more information.

---

### Post by Herman on 2007-07-02
Well if you're talking about "*GRUB error 1*"  maybe I can help you, here's where to look up some error codes from boot loaders, [Common Booting Errors and Some Possible Cures]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Common_Booting_Errors_and_Some_Possible")

---

### Post by cigtoxdoc on 2007-07-04
Thank you for your help.  Error in question came just after I entered my username and password in gnome.  Error referred to a panel not being regiostered with the bonobo-activation server.  Software that had been loaded came with Ubuntu 7.04 .

John

---

