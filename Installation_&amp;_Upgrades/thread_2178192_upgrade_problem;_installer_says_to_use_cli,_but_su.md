---
title: "upgrade problem; installer says to use cli, but sudo denies login"
date: 2013-10-02
forum: Installation &amp; Upgrades
---

### Post by davidmaxwaterman on 2013-10-02
I have been upgrading a system from the LTS (12.04?) to whatever the latest is (assume 13.04, but I've not succeeded yet)...I intended to attempt an install of 13.10 after that, but...

The software updater indicates a problem...to reproduce, I run software updater, which tells me "Updated software is available for this computer. Do you want to install it now?" - I click "Install Now". It then prompts for my admin password, which I enter....and it then gives me a dialog window stating, "The package system is broken....if you ar eusing third party repositories then disable them, since they are a common source of problems. Now run the following command in a terminal: apt-get install -f".

So, I disable what I can see under the 'other' tab in the settings, and close the dialog; then open a terminal and type 'sudo apt-get install -f', at which point I am greated by "<id> is not in the sudoers file. This indicent will be reported."

So, how to proceed?

FYI, 'about this computer' tells me I am now at 13.04.

---

### Post by davidmaxwaterman on 2013-10-02
OK, I think I got past the problem. When I first set up the system, I made an admin account, and sudo still worked for that, so I was able to fix the problem.

The issue was something due to a qt4-demos-dbg package, which I just removed with dpkg -r, and that freed up apt.

I'm still curious what I would have done if I didn't have that admin account...anyone have any ideas?

---

### Post by The Cog on 2013-10-02
Existing administrators can put other users in the **sudo** group to allow them to use sudo. This is done with the normal users and groups settings dialog. If the last administrator removes themselves from the sudo group, then I think you will need to boot into recovery mode and use the command-line tools to add a user back into the sudo group. I think the command is something like useradd but I would have to google to be sure.

EDIT: Correct group name (original post said group adm).

---

### Post by steeldriver on 2013-10-02
In current versions of Ubuntu, the group to add users to for administrative (sudo) priviledges is called **sudo**. Earlier versions used the group **admin** and the default sudoers file may still grant elevated privileges to that group for backward compatibility, but its use is deprecated. The **adm** group is the group that's allowed to read log files such as /var/log/auth.log and /var/log/syslog, and afaik doesn't give any elevated privileges beyond that.

---

### Post by davidmaxwaterman on 2013-10-02
hrm, thanks guys...it seems that the recovery mode trick is probably what I'd have to do, or perhaps boot to a live image off a usb stick/etc.

---

### Post by steeldriver on 2013-10-02
All the info you need should be here --> [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by The Cog on 2013-10-02
> In current versions of Ubuntu, the group to add users to for administrative (sudo) priviledges is called sudo.
Ah. Thanks for the correction. I will correct my post.

---

