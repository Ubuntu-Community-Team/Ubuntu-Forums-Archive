---
title: "Installing BackTrack 5 r2 Error cannot unmount partitions."
date: 2012-07-08
forum: Installation &amp; Upgrades
---

### Post by Edenthinker on 2012-07-08
I'm booting to backtrack 5 from a live CD. I open the gui by typing startx. When I do so I click the Install backTrack icon on desktop and go to install. I go through the steps but when I click install... it right away gives me a error message stating:

Failed to unmount partitions

The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/cdrom

Please close any applications using these mount points. 

Would you like the installer to try to unmount these partitions again?

When I was using UNetbootin to do a Frugal Install I came across the same problem... I did some research and was told to type into the terminal the command Sudo umount -l -r -f /cdrom before I opened the installer and then right before I click install remount it with the command I learned from typing Man 8 Mount in the terminal. This did not work all the way. It allowed the changes to the partition tables to be done but it would not allow the install to work... it would give me an error message basically saying systemfiles missing. 

Any help would be much appreciated. I need to know how to get around this problem with the partitions with out compromising the install.



{Solution was going back to Win7 and uninstalling UNetbootin somehow (even when I was installing form a live cd it was interfering.) once i uninstalled UNetbootin and rebooted from the live cd and no error came up currently at 26% yay!}

---

