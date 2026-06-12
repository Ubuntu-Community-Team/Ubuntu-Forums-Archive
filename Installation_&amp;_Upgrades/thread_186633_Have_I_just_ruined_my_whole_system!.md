---
title: "Have I just ruined my whole system?!"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by King Blah on 2006-06-02
I am in the middle of installing Kubuntu dapper drake, and it is partitioning my hard drive. Before I just had one windows ntfs partition taking up the drive. 
I selected to alter the partition tables manually because I didn't know what the setup would do automatically and I resized my only partition and made two other ones in the free space - a swap partition and ext3 one.

Now it's on the next step and the windows of the installation are blanked out but I can hear my hard drive being accessed still. This is 10 minutes after it started "partitioning". I am worried my hard drive has just been messed up.

Please say no...

---

### Post by SqRt7744 on 2006-06-02
seems odd that the screen has blanked out, but DON'T do any resets or turn anything off just yet!  If the hard disk is active, then work is being done.  If the screen is still black in a few hours, then yes reset and probably everything is trashed.

---

### Post by King Blah on 2006-06-02
Oh my god I knew i shouldn't have tried to install linux...

Edit: good news, it seems to have worked, I'll try to continue the installation and see how it goes.

---

### Post by King Blah on 2006-06-02
It is on the stage of "Prepare mount points". Should I include my windows partition in this?

---

### Post by bernardfrancois on 2006-06-02
If you want to have it mounted somewhere, yes. You could mount it to some point like /home/windows or whatever you wish. Normally you should be able to set if it should be formatted - make sure it won't be. If you're not sure, don't set a mount point for your windows partition, this can be done easily after the installation as well (see **man mount**).

---

### Post by King Blah on 2006-06-02
Thanks! I'll set one later.

---

