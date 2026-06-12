---
title: "/home from earlier installation. What is the solution?"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by kagashe on 2005-11-18
Hi,

I have solved this problem. Read the last post.

I have /home on separate partition since I first installed Ubuntu 5.04 Hoary. I also have Mandriva in dual boot and there is another userid on the same /home which uses Mandriva. (In fact I started in Linux with Mandrake which installed /home on separate partition as default).

I had no problems in Hoary. I made two abortive attempts to upgrade to Breezy but finally decided to go for fresh install of Breezy.

I faced one problem in using Synaptic (which I posted in another thread). When I did not get any solution I searched for "Gtk-CRITICAL" (the error I was getting) on this forum and read a couple of posts.

I have concluded that the error in Synaptic (and a few minor ones in other applicaons) are due to /home being from the earlier installation.

I would like to keep the user from the earlier installation since it has all the mails, address book and so much more stuff.

Please tell me how to use the same user (/home from earlier installation) on Breezy without getting errors.

kagashe

---

### Post by Arktis on 2005-11-19
I don't think there is an easy answer if that's what you're wondering.  My procedure for doing this would require identifying all the difference in configuration files stored in the user's home between the two distros, and deleting/editing to compensate.  I think you should just make backups of all the configs, do a fresh install, and incrementally add the appropriate information into the configs.  See?  No fun.

It's going to be a chore unless there is some sort of cross-distro migration tool, which I doubt.

---

### Post by kagashe on 2005-11-19
[QUOTE=Arktis]My procedure for doing this would require identifying all the difference in configuration files stored in the user's home between the two distros, and deleting/editing to compensate. [/QUOTE]Sorry. There was no need to mention Mandriva. Perhaps there is some confusion. The userid for Mandriva has nothing to do with Ubuntu. It is not a cross-distro migration.

I had created one userid for Hoary. When I installed Breezy I created the same userid. I could login to GDM with that and use all the files and priviledges.

The problem is I am getting some errors and I feel this is because the user was created in Hoary. I had posted about the problem I faced using Synaptic [here.]("http://ubuntuforums.org/showthread.php?t=91390")

kagashe

---

### Post by kagashe on 2005-11-20
Hi,

I did a fresh install of Breezy after deleting all hidden files/folders on /home (except .evolution, .gaim etc which seem harmless to me). I deleted .mozilla also after saving the bookmarks.

Every thing is running very smooth now.

kagashe

---

