---
title: "[server] Hot to report bugs when testing lucid?"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nutnut on 2010-03-17
Hi,

I use ubuntu-bug to report issues during my testing of Luic, on the desktop.

But, how and where is this to be done for the server.
For example I'm having issues installing Lucid server within a VM on Vmware ESX.

Thanks in advance

---

### Post by go2dell on 2010-03-18
First off, THANKS for helping to make Ubuntu better!  This is especially important for LTS releases, as with the upcoming 10.04, so your contribution is very valuable.

There's a wiki page describing all the ways of reporting bugs [here]("https://help.ubuntu.com/community/ReportingBugs").  There are lots of different ways of reporting bugs because, as you've already discovered, sometimes it isn't possible to use the "official" way of bug reporting.

Enjoy your testing!

edit: One more thought: Since you're (presumably) working at a command line, anything that can be typed in a Run Dialog can also be typed at the command line.

---

### Post by slakkie on 2010-03-18
> **nutnut said:**
> Hi,

I use ubuntu-bug to report issues during my testing of Luic, on the desktop.

But, how and where is this to be done for the server.
For example I'm having issues installing Lucid server within a VM on Vmware ESX.

Thanks in advance

You can use the same tool. It will then use a text based version.

---

### Post by whoop on 2010-03-18
I just use: "ubuntu-bug <messed up package>" inside an ssh session (to the server). At the end it returns a url, I can copy this and start it in my browser on the desktop...

---

### Post by nutnut on 2010-03-18
Thanks indeed.
What package do I choose (for ubuntu-bug) when I have a problem after installation, after the initial reboot? Its not obvious what module is involved. And the installation if different between desktop and server..

---

### Post by nutnut on 2010-03-18
Just found the answer, I believe it should be "debian-installer" for server.

[edit] Spoke too soon "debian-installer does not use Launchpad for bug tracking."
[https://bugs.launchpad.net/debian-installer](https://bugs.launchpad.net/debian-installer) 

Regards,

P.S. If someone has sufficient rights, maybe the typo in the subject could be corrected from "hot" to how?

---

### Post by Yofel on 2010-03-18
Debian-installer itself indeed doesn't use LP for bug tracking. But unless you're sure the bug exists in the debian version of the package file a bug against the ubuntu package [_here. _]("https://edge.launchpad.net/ubuntu/+source/debian-installer")
Or rather file a bug with 'ubuntu-bug debian-installer'

---

