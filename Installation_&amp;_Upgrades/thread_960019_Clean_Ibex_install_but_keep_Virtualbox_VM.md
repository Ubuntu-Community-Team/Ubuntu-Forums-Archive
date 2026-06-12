---
title: "Clean Ibex install but keep Virtualbox VM"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by eidauk on 2008-10-27
I have a VirtualBox with a Win XP virtual machine on it on my Hardy host. I'd like to remove Hardy and perform a clean install of Ibex (format root, but keep /home) so I don't have to recreate my Win XP VM. Can I just reinstall VBox after the upgrade and it will recognize my old Win XP image in my home directory?

---

### Post by lemming465 on 2008-10-28
It should.  I haven't done this with VirtualBox, but I have done similar things with vmware without problems.

---

### Post by eidauk on 2008-10-29
Thanks lemming. Anyone else had experience with VirtualBox?

---

### Post by joker535 on 2008-11-05
I would like to know about this too. I am in the same boat. I have been using this box with hardy since the day it came out and so far the only problem has been the recycle bin is corrupt. I have highly customized windows loads on sun virtual box 1.x that I just don't have the time to reload.

I know I can't save snapshots, but will they work ok on ibex with sun Virtualbox 2.x if I save the files?

---

### Post by Fire_Chief on 2008-11-05
I just did this on my laptop (Hardy with an XP vm in Vbox). The only difference in my case was I created a dedicated partition for the VM to reside. In terms of functionality, it should be identical.

If you have a separate /home partition then you should have zero problems with a clean install of Ibex and getting back into your VM. Here's are the basic steps I went through.

-Made list of all Ubuntu apps I wanted to reinstall after Ibex install.
-Tarred my home directory and stored in another partition. (I don't have a separate /home partition on my system so this was necessary to keep all my settings after formatting /).
-Performed clean install of Ibex
-Booted and performed updates
-Rebooted (kernel fixes in updates required it)
-Installed all apps desired from Synaptic or downloaded manually (did this for Virtualbox since I use the Non-OSE version).
-Untarred my saved home directory back to the newly created home directory.
-reset ownership of all files (including hidden!!) in home directory to match current user info (chown)
-log out, log in..viola! Everything was just as I had it previously configured in Hardy.

Since you have a separate /home, you should not need to mess with tarring, untarring, and chown'ing your /home files.

Cheers!


*EDIT*  I did not have to make any changes to the VM for it to load in the new version of xVM (Sun's version of Vbox). I had v1.6.5 on Hardy and it booted fine with v2.0.4 in Ibex. I did upgrade the Guest Additions after XP booted.

---

### Post by eidauk on 2008-11-06
I completed my upgrade and was able to keep my WinXP VM install intact. I decided to not upgrade to Intrepid due to some unrelated problems and reinstalled Hardy. Here's how I did it:

[LIST=1]
[*]Renamed .VirtualBox to VirtualBox (for simplicity in next step).
[*]Used the Hardy live boot CD and deleted all "." folders and files in my /home.
[*]Backed up /home on external HD.
[*]Formatted my / partition
[*]Installed Hardy only on / partition (kept /home untouched)
[*]Renamed "VirtualBox" back to ".VirtualBox"
[*]Installed VirtualBox
[*]Used Virtual Device Manager in VirtualBox to reassign (find) my existing WinXP.
[/LIST]
I had to change permissions on almost all files/folders in the .VirtualBox folder since I messed them up when I renamed the folder in step 1 above. All works great now. Plus I've now got the latest VirtualBox and a clean Hardy install to enjoy. It even kept my Guest Additions for me!

---

