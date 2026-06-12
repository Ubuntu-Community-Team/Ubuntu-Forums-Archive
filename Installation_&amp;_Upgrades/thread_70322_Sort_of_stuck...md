---
title: "Sort of stuck.."
date: 2005-09-29
forum: Installation &amp; Upgrades
---

### Post by cmilhaus on 2005-09-29
I burned a ISO of "Breezy" and the computer (which has Ubuntu running on it) will not boot into the CD, so then I saw this message about changing the /etc/apt/sources.list file to point to "Breezy" but the system will not allow me to save the changes, even though (gasp) I made myself owner of the file.
So, I suspect I need to  be able to edit and save the [/etc/apt/sources.list] file with the new references to "breezy" but do not know how to do it.
I suspect it is something simple and I am simply missing it
Can anybody help
I'm off ill from work today and this could well me my one real accomplishment for the day
Cheers

---

### Post by SilentCacophony on 2005-09-29
Hello. A couple of notes about burning .iso files. If you put the cd in and examine it from whatever OS you have running, you should see a normal file and directory structure, and not an .iso image file itself. If not, you burned it as a file instead of disc-at-once. You can also use the md5sum utility to verify the .iso is not corrupted, and try burning at a low speed.
As for changing the sources.list file, you don't need to change the ownership of the file (bad idea, security-wise,) but just need to use *sudo gedit /etc/apt/sources.list* as outlined in the [ubuntuguide]("http://www.ubuntuguide.org/#extrarepositories"), changing the hoary references to breezy. If you don't have gedit, you can always use the nano editor.

---

### Post by cmilhaus on 2005-09-29
Knew it was something easy, thank you so much. You've made my day!! Upgrading now on my Linux box

---

