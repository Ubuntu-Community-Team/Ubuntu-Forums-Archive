---
title: "Installed 10.10 64 bit; does not accept administrator password"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by entropy1 on 2010-10-10
I had 9.04 64-bit with / and /home in separate partitions. Today I used 10.10 alternate install to install a command line system.  Then installed gnome-core, synaptic, gparted, and a few other things.  Now when I go to System > Administration > Synaptic Package Manager  or to  Gparted, I am asked for the "administrator password".  I type in my password, but it is not accepted.  However, from a terminal I can "sudo synaptic", give my password, and install whatever I want.  Why is my password not accepted when I use the menu to invoke Synaptic?

---

### Post by AKADAP on 2010-10-11
> **entropy1 said:**
> I had 9.04 64-bit with / and /home in separate partitions. Today I used 10.10 alternate install to install a command line system.  Then installed gnome-core, synaptic, gparted, and a few other things.  Now when I go to System > Administration > Synaptic Package Manager  or to  Gparted, I am asked for the "administrator password".  I type in my password, but it is not accepted.  However, from a terminal I can "sudo synaptic", give my password, and install whatever I want.  Why is my password not accepted when I use the menu to invoke Synaptic?

Your password is not accepted for the root password because it is not the root password.

By default Ubuntu does not create a root account. This used to be a big problem if you needed to use the failsafe boots because they required you to log in as root, and there was no root. This may have been fixed.

In order for the root password to work, you need to set the password for the root user.

---

### Post by entropy1 on 2010-10-11
But I never created a root account/password.  If one has been created inadvertently, can it be deleted, and would that solve the problem?

---

### Post by LarryMi on 2010-10-11
[entropy1]("http://ubuntuforums.org/member.php?u=778720"),  have the same problem as you running 64 bit.

Yesterday, most everything seemed to work fine until I applied an update.  This update was for 'update-manager' and 'update-manager-core'.

If I choose synaptic or the run applications (alt + F2), it will ask for a password.  My password is rejected; however,  when I run synaptic at the terminal it will ask for my password, but is accepted. If I choose "Users and Groups", it will accept my password.

Does the update-manger work for you?  If I choose "Check", it does run, but is grayed-out but never completes to allow me to close the application.

Something is also strange, when I boot by system, and when I get to the login screen, I don't have a mouse.  After entering my password (which is accepted), and when I get into Ubuntu, my mouse pointer appears.

Not sure what's going on, but home to see some fixed soon.

If anyone has any advice, it is appreciated.

---

### Post by entropy1 on 2010-10-11
Users and Groups works for me.

Update Manager does not work for me; either from the menu or from a terminal.

My mouse DOES work at the login screen.

---

### Post by LarryMi on 2010-10-11
See if this works for you.  [Info is here]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes") See **Upstart jobs cannot be run in a chroot)**
on this page.

I entered:
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

as root, and now it's accepting my password; however, still have a problem with update-manager, so I have to "kill" it via the System Monitor

---

### Post by entropy1 on 2010-10-11
> **LarryMi said:**
> See if this works for you.  [Info is here]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes") See **Upstart jobs cannot be run in a chroot)**
on this page.

I entered:
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

as root, and now it's accepting my password; however, still have a problem with update-manager, so I have to "kill" it via the System Monitor

I tried this, but even after a shutdown and restart, I cannot run synaptic or update-manager from the menu.

---

### Post by entropy1 on 2010-10-12
In Virtualbox, I used 10.10 alternate install 32-bit to install a command line system. Then installed gnome-core, synaptic, gparted, and a few other things.  I have the same problem as in my original post.  I then created another virtual machine using the 10.10 alternate 32-bit to install the regular desktop ubuntu.  I didn't have the problem.  Then in the first virtual machine, I installed gnome-desktop and my problem went away.  This required an addition 166 MB download.  Seems like overkill to fix my problem.  Maybe there are just one or two items I need to install to fix the problem.  Any suggestions?

---

### Post by LarryMi on 2010-10-12
I don't have an answer, but still trying to figure out how to solve this.

---

### Post by LarryMi on 2010-10-12
I got my mouse working by installing gnome-core, and synaptic to acknowledge by passwords by installing desktop-base.

---

### Post by decoherence on 2010-10-15
> **LarryMi said:**
> I got ... synaptic to acknowledge by passwords by installing desktop-base.

Worked for me as well. It appears to use a different password dialogue now. Is AuthKit broken? (does Ubuntu still use AuthKit?)

---

### Post by Smartflight on 2011-01-10
Had this issue on Ubuntu 10.10 amd64. Installed desktop-base, working good now!

---

### Post by jmontee on 2011-01-29
> **Smartflight said:**
> Had this issue on Ubuntu 10.10 amd64. Installed desktop-base, working good now!
I wasn't happy with a fix that required me to install extra software, so I kept digging.  I just got to the bottom of this and wanted to share the solution.  

What's happening is that gksu is being used to perform authentication, but by default, gksu is set to operate in the wrong authentication mode.

Here's what to do.  Drop to the terminal, run gksu-properties, switch the authentication mode from su to sudo, and you're done.

That's it.  No installing any extra software to fix this issue.  Hope this helps!

---

### Post by palmero on 2011-02-21
Thanks jmontee

It worked flawlessly for my (ubuntu 10.10 server 64 bits)

Just a remark: 

First time I run "sudo gksu-properties", and changed from SU to SUDO. It didn't work. 

Then I realized that you said "gksu-properties" without "sudo"and gave it a try... Perfect!

Thanks again; very elegant solution.

Palmero

---

### Post by LazyBoy on 2011-05-01
Thanks jmontee!

---

### Post by entropy1 on 2011-05-30
Thanks jmontee.  This works great.

---

### Post by wirephobia on 2011-09-01
Thanks jmontee, this worked for me on 11.04 too.

---

### Post by deenak on 2012-02-16
awesome solution jmontee!!!

---

