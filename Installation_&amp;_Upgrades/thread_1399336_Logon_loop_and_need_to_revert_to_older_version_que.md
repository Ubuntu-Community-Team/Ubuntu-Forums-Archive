---
title: "Logon loop and need to revert to older version question."
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by drhans2 on 2010-02-05
Logon loop and need to revert to older version question.

Ever since updating to 9.10 from 9.04 I have been experiencing a logon loop problem. Maybe 1 in 15 tries is successful. When I was able to logon I was not able to mount the multi-boot Hd.. (Windows NTFS, Linux root Sda2, Home Sda3, Swap Sda4, + unallocated space). A error screen told me that I didn't have admin privileges.. Thats incorrect as I'm the only user and logged on at the time. Some other changes I tried also produced the same error. I found some clues on this forum to address the logon issue, and changed my resolution to 1280 x960 and that seems to let me logon each time as needed. But trying to mount the hd still results in the error message. I can not use the computer at the current resolution, too hard on the eyes.. (don't know how anyone could).

My question is... Since I have the live CD for version 9.04 and that version worked just fine, how should I or do I need to delete ver 9.10 and than reinstall version 9.04? If I run the 9.04 install program will it automatically choose the Sda2 partition, or do I need to precondition and define Sda2 & Sda3, & swap drives again? Will it perform the installation seeing that theres a newer version already on the hd? Also is there a option to uncheck so I won't get any auto-updates because it appears that the newer version is not compatible with my computer.
thanks,
denny

---

### Post by drhans2 on 2010-02-07
Just wondering... anybody have any input about this question?

thanks,
denny

---

### Post by darkod on 2010-02-07
I'm not sure about you logon issue, but in case you want to install 9.04 over the current 9.10:
One very IMPORTANT thing when installing on existing partitions. Ubuntu (and other linux I believe) considers ALL existing partitions as unavailable.
You have to specifically tell it to use them. I guess this is the way to avoid overwriting partition that it isn't supposed to.

So, in step 4 you will need to select the manual partitioning option. All three linux partitions will be marked as Not Used at start. Select them one by one, then hit the Change button at the bottom.

You will have to change the options to:
For /
Filesystem to ext3 or ext4, what ever it was
Mount point to /
Format, Yes (to wipe the previously installed version)

For /home
Filesystem, as needed
Mount point to /home
Format NO NO NO (unless you want data from your /home lost)

For swap
Filesystem, swap
Mount swap
Format, not applicable to swap area

That's the way to clean reinstall and keeping your /home intact when you have it as separate partition. Don't forget to create the same user, it would have to be the same because your folder in home is named like that. I haven't tried to set different first user.
If there are more users, the data will be there too, you will add them later to the existing home folders, so they will keep their data too.

I'm not sure how to make ubuntu not offer upgrade to 9.10, just the updates for 9.04. Maybe google can help for that.

---

### Post by darkod on 2010-02-07
PS. Also for future clean reinstalls (like when 10.04 LTS is out), you might want to read this:
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

It's a very simple procedure how to save a list of your packages installed from repositories, and then with one command to install them again in the new clean install. As long as they are again in the repositories, it should work.

Any third party software you had installed manually yourself, will need to be installed again.

---

### Post by oldos2er on 2010-02-07
There's info on mounting partitions here: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

If you want to overwrite 9.10 with 9.04, during the installation process select manual installation, and point it to the partition currently occupied by 9.10. All your data will destroyed, so backup anything you wish to save first. I'm assuming you do not have your /home directory on its own partition.

---

### Post by drhans2 on 2010-02-07
Darko... Thanks for the input.. makes sense, I'll try it.

However another question has arises ... Since ubuntu 9.10 has changed to a newer "grub 2" do I need delete it? I read somewhere that it was installed differently and maybe didn't use the menu.ini file or its possibly in a different location then the "grub 1" used in ubuntu 9.04. This will be a dual boot computer.. Windows XP pro & Ubuntu 9.04.

Ann... Thanks for the response... From what you said, I assume that by just manually pointing the ubuntu CD 9.04 installation at the partition that 9.10 is currently occupying, my "home" & "swap" folder will be placed inside that same partition. I do have separate partitions for "Home" & "Swap" and sounds like I need to install as Darko suggested above.

thanks,
denny

---

### Post by darkod on 2010-02-07
Yes, you definitely want to use the same /home and that's the point to have it separate.
The grub config files (doesn't matter whether it's grub1 or grub2) are in /boot/grub on your / partition. By formatting the 9.10 root partition you will get rid of all config files, and the 9.04 new install will create new config files. It will also replace grub2 on your MBR of the hdd with grub1.
You are right, grub1 uses /boot/grub/menu.lst as main config file, and grub2 uses /boot/grub/grub.cfg.

---

### Post by bweis on 2010-02-07
Sorry for jumping in at this spot but I am getting desperate.  My Ubuntu 9.10 has disappeared.  When I reboot the screen goes through a routine of checking the drive and only gets up to about 15% when it gives up.  I tried running live from a GOS (google os) cd but could not get a terminal up.  Am now doing this request on a Mac. 

UBUNTU SHOULD BE WORKING ON A DESKTOP PC.

I can be contacted on [email]bob@weisfilms.com[/email]

IF YOU CAN HELP, THANKS

BOB WEIS

---

### Post by drhans2 on 2010-02-07
Darkod... Thanks your instructions worked without any problems. I than went to the setting for the updates and found that I could uncheck the option for showing future releases. That should prevent me from upgrading this old desktop but still allow updates to the current version. 

As for Bweis problem... if you originally configured your computer with separate partitions for "\", "home", & "swap" as I did you could follow the 3rd post as that will reinstall your unbuntu version, and keep your personal setting & files, etc.. unless of course you have some hardware issues or other problem with your computer. Following the 5th post will start you over fresh with a clean install of unbuntu with "home" & "swap" all in 1 partition vs 3 partitions.  Anybody jump in here if I'm incorrect in my understanding of what going on).

---

### Post by darkod on 2010-02-07
> **drhans2 said:**
> Following the 5th post will start you over fresh with a clean install of unbuntu with "home" & "swap" all in 1 partition vs 3 partitions.  Anybody jump in here if I'm incorrect in my understanding of what going on).

I'm glad it worked fine for you.
Actually, swap would usually be separate partition. The default install is with two partitions, / and swap. It's whether you have separate /home partition that you want to keep that makes a difference in the installation procedure.
And by the way, having separate /home is worth gold sometimes, as you saw yourself how easy it is to do a clean install without worrying about your home folder.

---

