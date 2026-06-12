---
title: "Mint 17 &quot;locks all controls after login&quot;"
date: 2014-11-18
forum: MINT
---

### Post by chris36 on 2014-11-18
After I changed the toolbar to "hidden" the next login revealed a system lockup... 

The tool bar is not visable or 'reveled' with 'mouse over', no desktop files or locations are accessable, 'Menu' is hidden as per 'toolbar' issue :( Mouse moves but cannot get access to anything on screen. Right click is not available.
Tried rebooting several times - just locks up after login. Visable are all usual folders and some desktop files. Just not accessable.

What can I do? I have a Iso DVD of Mint 17. I put this in and booted ok, however, nearly all files on HDD in my "installed" Home have a 'X' on them. They cant be moved and most cant be accessed. :( I broke my Mint!! :(

How do I recover from this? I have other HDD's avail just not fitted to this PC. Thought If i fitted one with a Linux OS running - I could access files, Save and backup, Re-install, setting everything back to default...

---

### Post by mips on 2014-11-18
> **chris36 said:**
> 
What can I do? I have a Iso DVD of Mint 17. I put this in and booted ok, however, nearly all files on HDD in my "installed" Home have a 'X' on them. They cant be moved and most cant be accessed. :( I broke my Mint!! :(

You need to use sudo, be root or chroot into your installed system, any of these 3 options should work.

---

### Post by chris36 on 2014-11-21
Solved
Thanks Mips - sounds like your correct too.

An 'IT' friend helped with the "Controls locked" issue and this fixed the  menu shortcuts "crosslinks" somehow. As a result both isses were  resolved. Unknown why or how this occured? 

If you have this problem then  one way to solve could be to create an admin login on the login page  via terminal, step 2

"Sudo adduser (name here)" and then reboot

Step 3
--> change the current (hidden folders) .local  and .config to--> .localold and .configold - 

mv /home/yourname/.config /home/yourname/.configold
mv /home/yourname/.local /home/yourname/.localold

Step 4
-->Remove old  folders in the "Old Login" which has the problem and then copy new folders from new "Account"

sudo cp -R /home/newadmin/.config/* home/yourname/.config/*

 sudo cp -R /home/newadmin/.local/* home/yourname/.local/*

Logout and reboot

However... in Evolution (Evo) email,  it required that the emails and folders all  had to be copied from the .localold and .configold locations... to fully  retrieve them, other wise (Evo) requested a new setup by default,  Goodnews Thunderbird did not and all emails were saved and no changes required.


For me this fixed both issues.

Thanks "Combat Wombat"

---

