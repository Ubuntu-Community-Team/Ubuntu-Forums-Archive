---
title: "Boot stuck after upgrading from Ubuntu 16.04 LTS to Ubuntu 16.10"
date: 2017-04-24
forum: Installation &amp; Upgrades
---

### Post by umesh.narain on 2017-04-24
I upgraded my OS from Ubuntu 16.04 LTS to Ubuntu 16.10. Once updated, the restart is kind of stuck and not moving forward after the "Ubuntu" screen.
I clicked Ctrl + Alt + F3 to view the progress and it seems to be stuck in "Started Cleanup of Temporary Directories."
Please find the details below from the screen:

Starting Network Manager Script Dispatcher Service...
[ OK] Started Network Manager Script Dispatcher Service.
[ OK] Started Samba SMB Daemon.
[ OK] Started Samba NMB Daemon.
[ OK] Created slice User Slice of gdm.
         Starting User Manager for UID 127...
[ OK] Started Session c1 of user gdm.
[ OK] Started Daily apt activities.
[ OK] Started Run Click system-level hooks.
[ OK] Started LSB: Apache2 web server.
[ OK] Started MySQL Community Server.
[ OK] Started User Manager for UID 127.
         Starting Cleanup of Temporary Directories...
[ OK] Started Cleanup of Temporary Directories.

Please help to resolve this issue and identify what the issue could be.

Regards

---

### Post by LastDino on 2017-04-25
For starters upgrading LTS version to non LTS one is a major problem. Why did you do it? 

This is basic recipe for many conflicts. And problems occurring in this are..well..

I would suggest going back to 16.04 LTS, if you've your files backed up, do fresh install.

---

### Post by RobGoss on 2017-04-25
+1 LastDino

16.10 will come to its end of life in about two months, it would have been worth sticking with 16.04.2 LTS you still have a few more years

---

### Post by umesh.narain on 2017-04-26
Thanks for your response, LastDino , Rob. I agree to your points that I should not have updated from LTS version to non LTS version. 
I now have no backup from 16.04 so have to stick around with this version and update to future versions. 

To resolve the issue that I have been facing: boot getting stuck, I did the following:

typed the following command from terminal:

sudo dpkg -reconfigure lightdm

select 'lightdm' instead of 'gdm' in the popup dialog box.
Now restart the system. It should restart with no issues.

16.04 LTS was really stable and  gave a feel good factor than the future versions (16.10, 17.04)

Hope this suggestion helps other users as well.

Thanks,
Umesh

---

### Post by RobGoss on 2017-04-26
Thanks for sharing your solution with us

You can mark this thread as solved by using the** Thread tool** at the top of this post

---

