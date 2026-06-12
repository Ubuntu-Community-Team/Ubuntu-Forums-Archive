---
title: "catfish database  cannot update after upgrading from Xubuntu 20.04 to 22.LTS"
date: 2022-10-29
forum: Installation &amp; Upgrades
---

### Post by jamesr on 2022-10-29
Hi All,

I have updated 2 PC's from Xubuntu 20.04 LTS to 22.04 LTS. After the upgrade I have been unable to update my Catfish database.
The update seems to go through the process of finding the differences but it seems to be unable to update the database.
 The error message is > /var/lib/mlocate/mlocate.db
Updated 2021-11-29 07:36:08 AM
Error is "An error occurred while updating the database" 
I note that the date & Time information is old and possibly is related to the time that the database was last updated correctly. This error only occurs on the 2 systems that I have updated to 22.04.1 LTS ( I usually wait until the version 1 is released). All other systems that I have not updated still work.

Also the 2nd system worked satisfactorily until I upgraded to 22.04.1 LTS. This was the test to see if the upgrade was the problem.

I have other problems since the upgrade occurred, the other major one is related to Mondorescue (Mondoarchive).
I have stopped updating my other Servers until these problems are solved. Any suggestions will be gratefully appreciated.  I am going the check the size and permissions of the current mlocate.db file
I also note that I will need to update my signature, 16.04 to 20.04 LTS

---

### Post by jamesr on 2022-11-03
Hi All,

Any suggestions or is anybody else seeing the problem.

I checked the permission settings between 20,04 LTS and 22.04.1 LTS. there was a difference Group permissions had changed from mlocate to root. Changed on 1 system from  root to mlocate to match older working system but no change.

Are people no longer using catfish?  and if so, what are they  using?

---

### Post by ajgreeny on 2022-11-04
I'm not on my Linux machine at the moment so can't easily check this but I think I recall mlocate being replaced by placate.

Have a search through your system to see if there is anything which suggests this change, though how you deal with it I'm not sure. I have never upgraded a Linux version but always clean installed. However running the command ***sudo updatedb*** should create a new database of the filesystem and allow you to use the ***locate*** command.

Have a look at the catfish configuration to see what that says about the database used; perhaps that needs editing.

---

### Post by Jim_Robinson on 2022-11-28
Hi,

Thanks for the reply and my apologies for not replying sooner but I am having problems logging to this site and I am not sure why.

But back to your reply, should your comment > being replaced by placate.  actually be being replaced by plocate.

I will try your suggestion and reply back in a shorter time scale this time.

Two additional pieces of information. 
I have had total failure of another system. Replaced the PC and therefore, I had to install from scratch not an update  and catfish worked. It seems that I did not have to create a database. I will be able check this once once I have a requirement to do a move exhaustive search.

---

