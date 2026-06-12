---
title: "Lost Control of Desktop"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by Morganman on 2009-11-29
Hi Folks
I've just messed up big time.
A year ago I started to switch to Linux Ubuntu.
Yesterday I upgraded to 9.10 and got the last bits working that I needed, even effective dual screens.
To day I thought I'd tidy up and remove that which I do use.
This is where I messed up. There was a large white block in the middle of the top panel and I assumed this had no purpose so I removed it.
Now all the panels do is flash, I cannot get access to anything and I cant even log out other than by switching of.
I managed to scheme a launcher for a terminal on the desktop and the system seems to recognise me.

What have done?
And can I reverse it?
HELP!

Regards:confused:

---

### Post by ajgreeny on 2009-11-29
Use a terminal and try ```
mv /home/username/.gconf/apps/panel /home/username/.gconf/apps/panelbak
```then logout and login again.  You may end up with a default panel, but you can then if needed put back the applets etc etc that you want with a right click in an empty part of the panel and "Add to panel".

All this command does is rename the folder in which your panel configuration is stored, it will not remove anything else.

---

### Post by Morganman on 2009-11-29
Thanks.
My faith in all things Linux is restored.

You were right on the button.

All now appears back to normal. 
Glad I avoided the re install.

Many thanks
Dave:)

---

