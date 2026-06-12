---
title: "Update manager crashing after upgrade"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by MrPaez on 2008-04-25
I decided to upgrade my x64 of 7.10  to 8.04 on my HP NC6400. The upgrade process went quite smoothly but afterwards hardy has been acting strange.

I tried to run the update manager and it continuously crashes on me. I am not sure exactly what the cause because I get that there was a problem with python or NPViewer.

Has anyone had this problem yet?

PS my laptop has a ATi video card and is funning the fglrx drivers. Just in case that could be the problem.

---

### Post by dsiembab on 2008-04-25
sudo apt-get autoclean

---

### Post by MrPaez on 2008-04-25
> **dsiembab said:**
> sudo apt-get autoclean

I tried what you suggested and got the following:

$sudo apt-get autoclean
$sudo: unable to resolve host WAYNE

I have an internet connection. If I upgraded should I still see 7.10 repositories listed?

---

### Post by dsiembab on 2008-04-25
no
i think you sudoers file is a little bit trifled. you could probably got into your root folder and look for sodoers now go to view and make sure you can see your hidden folders now go back down to sudoers and see if their is a backup of that file it should look like "sudoers~" now you can reboot the computer and and hit esc when iit asks you about your grub go down to recovery mode should be secomnd listing in your grub  click it an dyou will be logged in as root noe change directory to etc "cd /etc/" now we both know sudoers and sudoers~ is there even if you don't have a sudoers file but still have the backup file type c"cp sudoers~ /etc/sudoers 
type in ls su* to make the fuiles are their then srestart your computer by typing reboot. hopefully this was youer problem if not then put your two hands together and and say oh heavenly father begone these demons from my computer.

---

### Post by MrPaez on 2008-04-25
Dsiembab, there is just a sudoers file there, there is no sudoers~ file.

Here is the contents of the sudoers file.
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by dsiembab on 2008-04-25
well your sudoers file looks typical. Do you have apache installed?

---

### Post by MrPaez on 2008-04-26
dsiembab, it doesnt appear that any apache packages are installed...

---

### Post by buntunub on 2008-04-26
I have same problem after updgrade to Hardy. Update Manager just hangs forever. Try to kill it with sudo killall update-manager and I get $ unable to resolve host. Whats going on?!?!?

---

### Post by buntunub on 2008-04-26
[This]("http://ubuntuforums.org/showthread.php?t=723361") thread fixed things for me.

---

### Post by MrPaez on 2008-04-28
I will try that thread you linked when I get home. I will let you know how it works out.

---

### Post by DRHamp on 2008-04-28
I have edited the hosts file and removed the domain name -- this fixed my sudo problem and it now works correctly.

Since my upgrade to Hardy -- I have received no updates.

When I go into Update manager -- after reading the state information - it says "Your system is up-to-date"

I then hit the "check" button and it downloads 64 of 64 files.   No Install, nothing else ----
Then I get a pop-up which says "Reading Package Information"

Then nothing -- "Your system is up-to-date"

I'm certainly a linux newbie -- am I overlooking something obvious?

---

### Post by dsiembab on 2008-04-30
lol :lol: it's downloading the package information from the mirrors and then checking your systems package list for updates. Windows kept me in the dark too.

---

