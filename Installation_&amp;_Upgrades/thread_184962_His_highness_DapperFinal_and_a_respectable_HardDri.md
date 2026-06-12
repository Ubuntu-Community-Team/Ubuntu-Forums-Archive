---
title: "His highness DapperFinal and a respectable HardDrive configuration"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by sherlock-holmes on 2006-05-30
Folks,

Now that the new Dapper around the corner, I am planning for a fresh install rather than a dist-upgrade.

...what would be the best way to partition the hard drive.

Its confusing ...

I now have the root partition (Boot) and then additional ext3 for /home.
But when I finished my installation successfully, I now have 2 /home partitions. The one I created as a /home dir the other created as the 'default' /home dir; associated with my username .

While going thru the manual partition while installing I had the option of creating partition as /home, /tmp, /var, etc... I selected /home (avoided /var, /etc thinking that it might need permissions...)

My system now looks approximately like this:

6 gb for root (ext3) ---> this also has a /home associated with my username
17 gb for /home (ext3) --> this one i created
10 gb XP (ntfs)
5.5 gb (fat32) ---> used by both xp and linux
the rest 1.5 gb for swap...

total 40 gb

1. What would be the best way to partition the drive...I dont want 2 /home partitions

2. whats the difference between the /home, /tmp, /var, /opt options for separate partitions?

3. how do i use the partitioning tool effectively so that i dont screw up my entire hard drive... what i am looking at is a root partition with my kernel and all other system stuff and a separate like /home to have my files, applications...

4. how do i make ubuntu install stuff not in the default location but in one of the separate ext3 partition (while using apt or synaptic, or while using dpkg) so that i still have the installed applications in case i later decide to reinstall the OS..

thanks a lot...

---

### Post by Ptero-4 on 2006-05-30
The /home you see in the / filesystem isn't there. It's actually your 17GB /home partition, it's created as /home in your / filesystem b/c it's a special type of partition and as such it isn't put in /media with the regular drives.

---

### Post by llamakc on 2006-05-30
First off, why are you not JUST going to do a dist-upgrade? That is a proper move from Breezy to Dapper.

For your partition needs, if you are going to be like many of the Ubuntu users who regularly reinstall and move between releases, creating a /home partition is a good idea.

When you reinstall you choose to 'leave the data as is' and make sure that the new install is going to use that partition.

---

### Post by nealklomp on 2006-05-30
I can think of one reason, Breezy works and Dapper may not. While I have had Dapper installed on this box, some things were not perfect and others were much better. I really like my system right now in Breezy and I don't want to take a chance until I am sure the next upgrade is ok on my box.

---

### Post by neoflight on 2006-05-30
i am actually planning to reinstall too..i am running dapper now already...i want a fresh system.....the new smell....

---

### Post by sherlock-holmes on 2006-06-01
ok now i have a new system... 10 gb for root, 20 for home, and the rest for swap, fat32 , and xp...

still trying to tweak my system.....automatix for dapper is awesome...

---

