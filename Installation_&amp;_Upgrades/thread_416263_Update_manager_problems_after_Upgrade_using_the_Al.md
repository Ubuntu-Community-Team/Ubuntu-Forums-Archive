---
title: "Update manager problems after Upgrade using the Alternate Install CD"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by shakyone on 2007-04-21
I'm giving this its own post, so it easier to find.

    After upgrade with alternate CD Update Manager asks for Install CD!
    
This was plaguing me then I remembered what I did when I upgraded to 6.10.

    After upgrading from 6.10 to 7.04 via the alternate install CD let the system reboot. The "updates available" icon will show new stuff available. When you try to use the update manager it asks you to insert for the normal install CD rom.

    Don't panic. There is an easy fix!

    Just close that update window, and open the System>Administration>Software Sources window.

    The active tab should be: Ubuntu Software. At the bottom of the window is a check box next to "Cdrom with Ubuntu 7.04 'Feisty Fawn.'

    Un-check this box.

    Then open the System>Administration>Update Manager and check for updates. It should work now.

    The same problem occurs with the upgrade from 6.06 to 6.10. I finally remembered it.

    Hopefully it works for you. 

Good luck,

Shakyone

---

