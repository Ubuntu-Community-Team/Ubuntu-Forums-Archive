---
title: "Moved home folder to new partion and can't log in anymore"
date: 2014-10-19
forum: Installation &amp; Upgrades
---

### Post by darb78 on 2014-10-19
I moved my /home folder to a new partition. Most everything works ok, except that I can no longer log is as the primary user. I am able to log in using the guest account. Is there a way to restore this user or should I set-up a new account?

---

### Post by sudodus on 2014-10-19
Did you add a line pointing to the new partition (and its UUID) in the file **/etc/fstab**?

---

### Post by darb78 on 2014-10-21
I did edit the fstab, I know there is a permission issue with the old partion and haven't addressed it yet. However the new /home folder which is a copy of the date on the /old_home folder looks to be set-up correctly. It would seem to me if the fstab wasn't set-up correctly the computer wouldn't boot (or at very least wouldn't show any users). It still boots fine and shows my user but just won't let me log into it. 

As a fix I created a new user id as an Administrator and I'm able to do everything I was doing. It's just bothering me trying to figure out what I did wrong. 

   # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 
 # / was on /dev/sdc2 during installation UUID=c52fe81f-3358-4b3d-815b-934ff56fa9cb /home               ext4    defaults 0       2 
 # /home was on /dev/sdc3 during installation UUID=674e5fad-2f38-4aa9-9813-98fd9554cc8b /old_home           ext4    defaults        0       2 
 # swap was on /dev/sdc4 during installation UUID=e26aa608-7fa8-4ca5-a783-3a37765b6e54 none            swap    sw              0       0

---

### Post by sudodus on 2014-10-21
It seems that your home directory works properly in the new partition. Otherwise it should not be possible to create and use a new user id. I think that there is some specific permission issue or copying error that affects your old user id. Something that may or may not be caused by the creation of a new /home partition.

---

### Post by darb78 on 2014-10-21
I have corrected the permissions issue as best as I can tell. I copied the whole contents of the original /home folder to the new /home folder again, logged out and attempted to log back into my old account. Still no luck. Subsequently I gave up and decided to simply delete the old user and run with my new user account rather than continue to put significant time into it. However when I tried to delete the old account I recieved the following error: 

GDBus.Error:org.freedesktop.Accounts.Error.Failed: running '/usr/sbin/userdel' failed: /usr/sbin/userdel returned an error (8): userdel: user brad is currently logged in

I also tried removing the password requirement to see if I could get in and no dice. I'm going to restart and see what happens then.

---

