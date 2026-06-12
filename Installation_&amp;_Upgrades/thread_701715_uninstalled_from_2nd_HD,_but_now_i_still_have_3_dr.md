---
title: "uninstalled from 2nd HD, but now i still have 3 drive letters (in xp)"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by nicoretteMan on 2008-02-19
I tried out Ubuntu on a secondary HD on my work computer. I later uninstalled it (keeping it on my home computer - Ubuntu rocks!). Deleted the 3 partitions/reformatted to NTFS, 'fixmbr' to be safe, even tried "MBRFIX.EXE", and various other things. But the issue that I'm having is that when I'm booted in XP, I see my normal C:\ Drive & my newly formatted D:\ Drive, but I also have an L:\ M:\ & N:\ drive (old root, swap, & home, I believe). I can't seem to get rid of them. The L:\ drive just takes me to my 2nd HD (same as D:\), M:\ & N:\ give the following error:
---------------------------
My Computer
---------------------------
M:\ refers to a location that is unavailable. It could be on a hard drive on this computer, or on a network. Check to make sure that the disk is properly inserted, or that you are connected to the Internet or your network, and then try again. If it still cannot be located, the information might have been moved to a different location.
---------------------------
OK   
---------------------------

Any ideas?

---

### Post by Zimmer on 2008-02-20
If I remember correctly from my Windows days it is a bit like network drives..  windows has defined the locations , as it does network drives, and keeps them until you tell it to forget those links or reassign the letters to another drive.  

When you open Win Explorer there will be a tools option to disconnect them (even though they are disconnected/no longer exist)  I think it is 'Disconnect Network Drive)

---

### Post by nicoretteMan on 2008-02-21
Thanks Zimmer, but those drives don't show up on the list. (I used Tools > Disconnect Network Drive... - in windows explorer).

Any other ideas?

---

### Post by Zimmer on 2008-02-21
[http://support.microsoft.com/default.aspx?scid=kb;en-us;307844&sd=tech](http://support.microsoft.com/default.aspx?scid=kb;en-us;307844&sd=tech)

This may provide you with a solution...  I cannot test it for you, however.. :)

---

### Post by nicoretteMan on 2008-02-22
Those drive letters L:\, M:\, and N:\ don't show up in the disk management snap-in - I just see C:\ and D:\

I deleted the Ubuntu partitions on 2nd HD, & reformatted as NTFS, and assigned the letter to D:\ 

Don't know why L:\, M:\, and N:\ are still showing up in 'My Computer'

Thanks again Zimmer.

---

