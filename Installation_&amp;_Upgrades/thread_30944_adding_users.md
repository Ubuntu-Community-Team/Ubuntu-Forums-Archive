---
title: "adding users"
date: 2005-05-01
forum: Installation &amp; Upgrades
---

### Post by robshep on 2005-05-01
I have installed ubuntu fine and setup nis and nfs  mounts for the network users

however I have realised my nis users cannot access some things like audio for example.

It is apparent the local user 'admin' which was created at install time, is a member of all these extra groups and so has access to /dev/audio for the audio example.

How can I work round this.

May I can configure udev to modify the permissions for /dev/audio and friends from 660 to 666?

But what other group related nasties lurk beneath the surface? Any comments greatful

If no workaround then bye bye ubuntu   :sad: 

many thanks

Rob

---

### Post by iamkmaniam on 2005-05-01
If your using NFS the problem may be in your set up. I beleive that in order for NFS to work correctly the UID must match on all the machines, if they do not that system will not work. It's a security advantage of using NFS. An example of this would be. The first user on a Fedora core machine gets a UID of 500 the first user on Ubuntu gets a UID of 1000, if I try to connect my fedora machine to my ubuntu machine via NFS it won't work unless uou set the UID correctly when you add the user.  Try adding the users with the -u option for useradd and set proper UID's for your different users. If that doesn't work and security is not a big issue, that is if it's just a home machine with no corporate info on it. switch to samba. 

Special note: I am having trouble adding users via the useradd command in Ubuntu. It seems that it won't create a home dir for the users. They seem to be using the adduser command which is different, I'm not sure of the options that go along with this.

---

### Post by robshep on 2005-05-02
[QUOTE=iamkmaniam]If your using NFS the problem may be in your set up. I beleive that in order for NFS to work correctly the UID must match on all the machines, [/QUOTE]

Yes that's what NIS is for - to make a networked version of /etc/passwd on all systems


[QUOTE=iamkmaniam] if they do not that system will not work. It's a security advantage of using NFS.
[/QUOTE]
It's actually an implicit security DISadvantage - all you need to do is match the UID/GID and you've got free reign through NFS. Making UIDs/GIDs match is a trivial task for any kid with a knoppix disk......



[QUOTE=iamkmaniam] [if] security is not a big issue, that is if it's just a home machine with no corporate info on it. switch to samba. [/QUOTE]

Samba is more secure than plain NFS! it requires Authentication at the server.

Maybe you misunderstood what I am asking. NIS/NFS is fine. users can log in and get their home's etc. However because they are not part of the 'plugdev' group they cannot run pmount to get USB flash disks etc. Also because they are not part of the 'audio' group they cannot play audio. Same for CDROM, Scanner,Floppy and Video.

As a workaround:

I changed permissions in udev for audio and video.
I added a few users to the plugdev group to allow execution of pmount. 
Although this is unfeasable for a large numberof workstations and a large number of NIS users.

Rob

---

