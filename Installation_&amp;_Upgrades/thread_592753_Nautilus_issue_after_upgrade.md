---
title: "Nautilus issue after upgrade"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by umarvlie on 2007-10-26
After an upgrade i found that when i browse through directory structure of one particular folder (mp3/mpc/ogg files) i have after some time a pop-up with following notice:

The folder contents could not be displayed.

Now this happened first only when i was browing this folder (which is on a ntfs partition) however today i worked on another machine onto which i copied the particular directory and had the same issue. This PC had a clean install with Gutsy and no ntfs. Nautilus wont open new folders and i cant browse in any folder anymore.

Does anyone have a clue as what might cause this problem? I have to use System Monitor to kill nautilus as it just sits there eating CPU cycles and does not respond anymore (i.e. not opening any new window or directory) after this pop-up.

After i kill the process (nautilus) i can use it again and it works for some time but then the problem pops up again.

---

### Post by umarvlie on 2007-10-27
I just read some issues ralted to SMB and permissions on this with similar resulting pop-ups and tried to rund nautilus (after i reached a condition in which the problem occurs) as root with "sudo nautilus" from a terminal and then it starts and i can browse the folders i previously could not.

Weird as whn it is on NTFS i can understand it might be related to file permissions (screwed up in some way after some time) but i copeid these files (usign ftp) to another computer with onyl UBUNTU and i see the same problem on that directory.

Does anyone experienced the same and/or know of a solution? It is really irritating to have to restart nautilus ever so often :(

---

### Post by umarvlie on 2007-10-29
Just to clarify that with the previous version of Ubuntu (7.04 - Feisty Fawn) i never experienced this issue.

---

### Post by umarvlie on 2007-10-31
I have experienced the "same" problem now even when using nautilus with sudo from terminal, though it wont hang it stops recognising teh MP3 as audio files.

I get some output in the terminal that might point:

> (nautilus:7342): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (nautilus:7342): WARNING **: destroyed file has call_when_ready pending

** (nautilus:7342): WARNING **: destroyed file has call_when_ready pending

--- Hash table keys for warning below:
--> &#65533;U

(nautilus:7342): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

---

### Post by umarvlie on 2008-02-21
Well, the only thing i found is that this looks to be related to a bug and is fixed in Hardy (but not in Edgy :( ) 

Would a change to Kubuntu be worth it (i.e. use konquerer rather than nautilus) and/or is it easy to replace the windows manager from gnome to kde?

---

### Post by froy02 on 2008-02-21
That happened to me when I copied a whole directory from a different partition (I have 32-bit and 64 bit Ubuntu installed).  I copied the Pictures directory from my 64-bit installation to my 32-bit installation using 'gksu Nautilus'.  It replaced the 32-bit Pictures directory with the one from the 64-bit but when I rebooted I could not access the files. 
What I did was remove that Pictures directory and made another one without using the gksu option in Nautilus.

It seem that when I replaced that directory with one from another installation it carried with it the ownership.

Hope this helps.

---

