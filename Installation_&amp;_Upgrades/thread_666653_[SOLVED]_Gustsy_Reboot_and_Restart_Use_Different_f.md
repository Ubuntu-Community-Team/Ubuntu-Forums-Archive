---
title: "[SOLVED] Gustsy Reboot and Restart Use Different files?"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by merrydown on 2008-01-13
Hi, can anyone shed some light on this?

When I cold start my server the site that is displayed seems to be different to that when I reboot.  Also the fstab file seems to produce mounting errors on reboot but work fine from a restart.

Do reboot and restarts use different users or versions of the software some how?

Getting a stable server is proving really difficult with all these intricacies, can anyone please help?

Thanks, Jim:confused:

---

### Post by Craigus on 2008-01-13
> the site that is displayed seems to be different to that when I reboot.

Could you be a bit more specific ?

---

### Post by merrydown on 2008-01-13
Apologies, I am still investigating this and being quite noob I am not sure what to include.

When I restart my server from cold it uses a different version of the database, fstab and other files to when I do a reboot.  Also the files in my website (root /home/siteName/www/html/) are different versions depending on whether I am using the site after a cold start or reboot.

Thanks for your reply.  If you need any more information, then do not hesitate to prompt me.  I am a server noob and have been trying to get this server shipshape for a couple of months.

Jim

---

### Post by Craigus on 2008-01-13
Do you know where these different versions are stored on the system ?

---

### Post by merrydown on 2008-01-13
Well I believe they are all in the same place for both methods of starting the machine.   Just different file versions are in that place depending on whether I cold started or rebooted the server.

That's it the best I can make out.

Jim

---

### Post by merrydown on 2008-01-13
I should probably add that I have done a 'locate' to try to find duplicates of the system on restart and on reboot but no alternate files seem to be shown.  I am using both the server in place, webmin and my ftp client to work with the server.

For example: the version of fstab in /etc is different depending on the way I started up the machine...

Does this sound impossible or could there be a sane explanation for this?

Jim

---

### Post by merrydown on 2008-01-14
Aditionally I have had to copy over my phpMyAdmin config.ini.php from the cold start webroot/phpMyAdmin to the same folder after reboot.  Before I did that there was no config file available on reboot so I couldnt use phpMyAdmin on my server...

Any clues?

---

### Post by merrydown on 2008-01-15
Can no one offer help with this problem?  Is there anywhere else I can check - this is driving me mad...

---

### Post by merrydown on 2008-01-20
The problem is solved.  The system wasn't recognising the hardware raid built into my server and was alternating between the two disks with almost identical content at boot time.  Now I have installed dmraid (and fixed the many disk errors that occurred at the time) the problem has not recurred.  Shame dmraid isn't part of the original installation by default!

Jim

---

### Post by Craigus on 2008-01-21
Woah - that was tricky. Well done for sorting it out. As the thread originator, you can mark the thread [solved] .

---

### Post by merrydown on 2008-01-21
Thanks, will do :)

---

