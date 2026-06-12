---
title: "Clean Install on new HD  -  /home on 2nd HD"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by tj1520 on 2008-10-18
Just installed kubuntu 8.1 as a clean install on a new hard drive.

My home directory is safely on a 2nd hard drive.

edited /etc/fstab with this line to mount new home

/dev/sda1   /home  ext3  nodev, nosuid  0  2

However, when I reboot the login menu only shows the user I set up as a default to get the installation going.  When I login in I got an error message stating that home was not found using ./  Clicked ok, then just cycles again to the login menu.

So, I used vi to delete the line, rebooted and I was ok.

So I edited /etc/fstab with this line to mount a new home

/dev/sda1   /home  ext3  defaults, errors=remount -rw 0 2

My login still only shows the default user, but I can log in.  The line in /etc/fstab is noted as an error and it is skipped over.

I've used a couple hours scouring google links and the forums and can't find a solution that exactly fits my situation.

Would someone be so kind as to help me out with this?

Thanks in advance!

---

### Post by tj1520 on 2008-10-20
Let me simplify . . .

I have a new install of kubuntu 8.10
It has its own home directory residing on the same harddrive as the install.

I have a saved /home directory residing on another harddrive.

How do I restore the use of the old /home directory into the new install?:confused:

---

### Post by Hexagoon on 2008-10-20
The simplest way is:

   * Copy content from old HDD home to new HDD home
   * Create users for each user folder (dont forget to set homes to the correct folders)
   * Correct the permissions of each user home with chown/chgrp

After that all should be fine :)

Edit: If you want /home to reside on the second HDD, you still will have to correct permissions to be able to use the homes. (Press ctrl+alt+f1 to get a promt to work in, in case you didn't know)

---

### Post by tj1520 on 2008-10-20
> **Hexagoon said:**
> The simplest way is:

   
Edit: If you want /home to reside on the second HDD, you still will have to correct permissions to be able to use the homes. (Press ctrl+alt+f1 to get a promt to work in, in case you didn't know)

Thanks for the quick reply.

I must have some video issues, because I am quessing that ctrl+alt+f1 drops to a console?  All I get is blank screen with blinking colored vertical bars.

Yes, I do indeed want to use the /home on the second hard drive and leave it there.


!noobie alert!
Would you please kindly be specific as to the commands I would use to change the ownership group etc.

---

### Post by Hexagoon on 2008-10-20
Oh, try ctrl+alt+f2 and so on and check if you get a console.

  The commands to change permissions at the folder is (with the 2nd hdd mounted at /home)

```
sudo chown user:group /home/user
```

replace user and group (probably the same as user) with the corresponding credentials.

I'm out of time now (at work), so i hope you get it to work :)

---

