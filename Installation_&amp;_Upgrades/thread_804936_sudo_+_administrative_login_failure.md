---
title: "sudo + administrative login failure"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by step77 on 2008-05-23
Hi, since I switched to Hardy I've been having upgrade problems. It doesn't get to the admin login page using adept. So I upgraded sudo apt-get upgrade. It worked and I upgraded 117 packages and security upgrades. Now i can't install anything. It's giving me authentication failure using sudo. I am truely stuck.
Steve.

---

### Post by fs3rp4 on 2008-05-23
> **step77 said:**
> Hi, since I switched to Hardy I've been having upgrade problems. It doesn't get to the admin login page using adept. So I upgraded sudo apt-get upgrade. It worked and I upgraded 117 packages and security upgrades. Now i can't install anything. It's giving me authentication failure using sudo. I am truely stuck.
Steve.


Ok...

When you try to use "sudo su" in terminal what kind of message do you receive?

---

### Post by step77 on 2008-05-23
Hi, thanks. It thought about it but it's let me in as root. root@stephen-desktop:/home/stephen#

Steve.

---

### Post by fs3rp4 on 2008-05-23
Nice.

Try this:

sudo su
apt-get update && apt-get dist-upgrade
restart the PC and look if the upgrade fixed the problem...

---

### Post by step77 on 2008-05-23
Hi, thanks. It told me I had a false/incorrect security module but it was fixing it. So I restarted and no administrative access on programs still. I ran the CI again and everythings up to date and installed but I've no admin access. Bummer.
Steve.

---

### Post by fs3rp4 on 2008-05-23
> **step77 said:**
> Hi, thanks. It told me I had a false/incorrect security module but it was fixing it. So I restarted and no administrative access on programs still. I ran the CI again and everythings up to date and installed but I've no admin access. Bummer.
Steve.

OK. :)

Let's try to put your user again in the admin group with this commnad:

sudo su
adduser "name of your user" admin

If the system return a message The user "name of your user" is already a member of `admin'. Try to use the editor visudo and post file here...

---

### Post by step77 on 2008-05-23
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
"/etc/sudoers.tmp" 23 lines, 496 characters

---

### Post by fs3rp4 on 2008-05-23
Unfortunaly looks like everything fine. I really dont'n know what's happening. 

Sorry...

---

### Post by step77 on 2008-05-23
Ta, think I'll back up all my mail and bits and reinstall. But thanks for the effort you put in.
Steve.

---

