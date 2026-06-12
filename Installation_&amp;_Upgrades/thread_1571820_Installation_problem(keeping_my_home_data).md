---
title: "Installation problem(keeping my home data)"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by Bucum on 2010-09-10
Had to reinstall my ubuntu and lost my data which I wanted to keep. How should do reinstall next time so this doesnt happen.

Basically wanted to keep files in Downloads/Pictures/Documents/....

I partion manually

1.Boot 100mb
2./    15gb
3. swap 6gb
4. Home 20gb

I did format 1,2,3 and home left unformatted. 

Should I have left 4. Home just blank and not put home partition at all?

---

### Post by sharathcshekhar on 2010-09-10
When you left home unformatted, did you also mention the mount point for that partition as /home?
Is your home partition totally formatted now or is it just you dont have permissions to access it?

---

### Post by Bucum on 2010-09-10
> **sharathcshekhar said:**
> When you left home unformatted, did you also mention the mount point for that partition as /home?


Yes. When partitioning I mounted home on the old partion where home was before.

> **sharathcshekhar said:**
> 
Is your home partition totally formatted now or is it just you dont have permissions to access it?

I think its all gone. Folders are empty. I used same username so I think thats the reason? 

I try to use some filerestoring program since the data should be there.

Next time should I just not mount the Home folder when partitioning or just use different user name?

---

### Post by ajgreeny on 2010-09-10
From your description it sounds as if you did everything correctly, so I can't figure out why all your /home folders are empty.  Just a quick thought; did you check that the "Format" box in the listed partitions was definitely unchecked when you hit the final button to install?  You must certainly include the old /home partition and set it as the new /home, or a completely new home folder will be made for you and the old one not used at all.  I suspect that you did not remove the "Format" checkmark from the box, therefore everything will be gone.  You could try testdisk if it is very important to you to get the old partition back, but it may be easier to start again if you have backups.

Run ```
sudo fdisk -l
``` just to see what is really on disk, and also ```
df -h
``` to see the space usage of everything, including your home.

---

### Post by Bucum on 2010-09-10
Was pretty sure that when setting up the partitions it was uncheked. 

Well no super important data was lost. Just something. Ill just take the hit and move on.

---

### Post by sharathcshekhar on 2010-09-10
Agree with ajgreeny. Everything you have done seems right.

> 
Next time should I just not mount the Home folder when partitioning or just use different user name?

No. In fact you have to use the same user name. Or You wont have permissions to it when you log on; in which case you have to run chown on that directory. And you also have to mount the home partition under /home while installation.
If you manage to know what went wrong, I would be keen to see it as well!

---

