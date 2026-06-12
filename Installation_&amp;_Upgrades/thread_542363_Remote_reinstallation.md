---
title: "Remote reinstallation"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by MikeBenza on 2007-09-03
Hello all,

I just walked someone through fsck fixing a lot of file errors which prohibited my (remote) machine from booting.  I'd like to perform a remote reinstallation (+ upgrade), so that anything that isn't quite right will be replaced with new files.

My home directories are on a separate physical hard drive, and they're backed up on another hard drive.

I have SSH and VNC access to the machine.  Can I do a remote reinstallation, or should I set aside a few hours to be on the phone?

- Mike Benza

---

### Post by MikeBenza on 2007-09-04
Does anyone even have a clue?

---

### Post by MikeBenza on 2007-09-09
Can anyone even speculate if this is possible?

---

### Post by MikeBenza on 2007-09-14
Would someone please help me?  This machine is locking up every other day.  The machine completely locks up.  Alt+SysRq+[REISUB] does nothing.  There are no messages in any logs, no indication of anything actually going wrong.  I need to reinstall, and I can either do it in an hour or two remotely, or 6 hours over the phone.

PLEASE, Someone answer this.

- Mike Benza

---

### Post by Yoooder on 2007-09-25
I'm looking for the same thing as you, but not finding much.

Here's your best bet, send whoever has physical access to the box an Ubuntu CD and have them throw it in the drive and reboot.

They'll need to bring up the LiveCD, then they'll need to install and enable SSH/VNC access for you (to the LiveCD)

Then you can remote in and perform the installation, after that's done you'll probably need to call them back up and have them (again) install and enable SSH so you can remote into the *new* installation.

---

