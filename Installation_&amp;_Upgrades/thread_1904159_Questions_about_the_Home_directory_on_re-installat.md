---
title: "Questions about the Home directory on re-installation of Ubuntu"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by spielball on 2012-01-04
Hello guys! I need some advice here. Somehow, my Ubuntu 11.10 is pretty much scrambled. So I decided to make a fresh install. But this is my first re-install of Ubuntu ever.

My questions:

1. What happens to the home directory when I re-install? I have my home directory on a separate partition. Can I point the Ubuntu installer there and then it will leave my home directory 'as is'?

2. Even though I want to keep my files (music, video, documents), I want to wipe all previous software settings. And I wonder if Ubuntu will take these old settings when I point it to that home partition. So how can I tell Ubuntu: 'Give me a clean, untouched install. But keep my data files.'

3. If I encrypt my home directory during installation: Will I have to wait for the whole 200GB partition to be 'pre-encrypted'? Or will the partition simply be marked as: 'everything that goes in here will be encrypted'? Because I remember from Windows/TrueCrypt that once I had to wait a whole day for my external 1TB drive when I followed TrueCrypt's recommendation to pre-encrypt the partition.

4. If my home partition is encrypted after all. And if at some point I have to do another fresh install. Is it possible to use that encrypted home directory for the fresh install? Or will there be any difficulties?

5. And what if I switch to another distro? I suppose it won't be a problem when switching to Kubuntu. But what if I switch to OpenSuse for instance?

Thanks in advance! ):P

---

### Post by ottosykora on 2012-01-04
1.
yes you can do that and don't forget NOT to partition it, then it will remain where it is
also choose the same user name , then all your data will be present without hassle

2.
this might be more complex. the user settings are stored there too, so if you want have complete clean new install, then copy only your personal datat to some external drive or so and import them later back.

3.
no, it does not take whole day

4.
there will be problems

5.
there will be problems definitely

---

### Post by ajgreeny on 2012-01-04
[LIST=1]
[*]As ottosykora says, re-using your separate /home partition is easy, however, he meant to say you must make sure you "do not format" the /home partition when you reinstall, not "do not partition".  His wording may have been a little confusing.
[*]To get rid of the various configurations for applications, remove or rename all the hidden files and folders in your home partition, (those starting with a .).  It will probably be easiest to move them all into a subfolder of home which you make and call /hidden, that way you can make sure everything is still available, (eg emails in /thunderbird, bookmarks etc etc in .mozilla), and you can move those folders that you certainly will need back to the root of your home.
[/LIST]
With regard to encryption, I will have to leave answers to others;  I have never used it and only know of situations where it has caused problems rather than helped.

---

### Post by spielball on 2012-01-04
Thank you very much, guys. This was very helpful. I know what I have to do now. Also a nice recommendation to move all the application settings files to a subfolder in order to have them still available if needed (Thunderbird etc).

As for the encryption, now I guess I will not encrypt my home folder eventually. Probably I'll just make one /.Private folder with eCryptfs, where I only put important personal files, but nothing else.

One more question though: Can I create a new user (another user name than from the old install) during the re-install and then just move the needed application settings from the previous user to my new user's home directory?

---

### Post by ottosykora on 2012-01-04
@ajgreeny

yes, right, sometimes mix the words ;-)

@spielball

well yes sure you can copy all by hand, but keep in mind, that those items, that means all the files those infos are stored in, belong to the former user and to none else. Thus you can not even access them from your current new user properly and if you copy them as root, then they will become root properties...then you would have to change the rights there again to the new user...getting then rather complex for not much use after.

I do sometimes move things around like that, but doing it following way:
copy those items (like thunderbird profile) by any user (incl root) to a drive formated in fat32.
By that any rights and property bits are lost as fat32 does not have any means to store such info.
Later copy them from the fat32 drive to the proper place under the current user I want to work them too.
This way those files become property of my user and nothing more has to be done.

But you mentioned that you do not want have those config and settings in your new install?

---

### Post by spielball on 2012-01-04
> **ottosykora said:**
> 
I do sometimes move things around like that, but doing it following way:
copy those items (like thunderbird profile) by any user (incl root) to a drive formated in fat32.
By that any rights and property bits are lost as fat32 does not have any means to store such info.
Later copy them from the fat32 drive to the proper place under the current user I want to work them too.
This way those files become property of my user and nothing more has to be done.

Good idea :KS

> **ottosykora said:**
> 
But you mentioned that you do not want have those config and settings in your new install?
Yes, I want to wipe all application settings, but not my permanent data (such as audio, video, pictures and documents).

---

