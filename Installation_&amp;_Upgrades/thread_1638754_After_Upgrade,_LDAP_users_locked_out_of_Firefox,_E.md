---
title: "After Upgrade, LDAP users locked out of Firefox, Evolution"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by Palindroves on 2010-12-06
Pardon my long-windedness here, but I feel the context is necessary to understanding my problem. To put it shortly: I upgraded from Ubuntu 8.04 to 10.04 desktop on my first machine (Red) which screwed up my RAID and LDAP server config on that machine. After correcting the problems, my non-LDAP users can access Firefox and Evolution on Red, but my LDAP users cannot. They can log in and everything else seems to work, but I get a "Firefox is already running" lock file error when I try to start Firefox. I have checked permissions and they are good. I have another machine (Yellow) running Kubuntu 9.10. I have set it up to mount the Red home directories via NFS and to use Red's LDAP server for user identification.  When logging in from Yellow the users can access Firefox no problem. But when they log in on Red they cannot, even though the user profiles, user conf files and permissions are in the same place on Red either way. 

I fear the problem is that some setting was changed in the Firefox config or home config files of the non-LDAP users which did not get changed for the LDAP users either because they did not exist or their home directories did not exist when the upgrade script was running. Any ideas would be greatly appreciated.

Background: My setup is a little non-standard, in that I have a few users in etc/passwd with home directories in /home2 on the boot drive, and the rest are implemented with Kerberos/LDAP with home directories on a RAID 1 array mounted at /home.

On upgrade, I had two problems. The first was that the upgrade script did not like my SLAPD config file and would not install SLAPD. The second was that the upgrade deleted the md0 file for my RAID and tried to recreate the array as md_d0. md_d0 was non-functional and was not mounted in fstab in any case.

So after the upgrade most of my users did not exist and had no home directories. 

The RAID problem was easy to fix. I just had to stop the non-functioning md_d0 array, re-assemble md0, and add it to the mdadm conf file.

The SLAPD problem was not so easy to fix, and I think I made a tactical error. I tried re-installing SLAPD and got multiple errors on my config file. I didn't see any problem with the config file and didn't feel like trying to spend ages figuring it out. So I renamed the config file to something else and re-installed without a config file. I figured I could look at the differences between the new default config and my old config files after installation and quickly spot the problem. To my surprise SLAPD created a whole config directory instead of a config file, so my plan went out the window. After some research, I figured out how to make SLAPD re-create the config directory from the old config file. 
So now SLAPD worked - but my database was gone!

Sadly I did not backup my ldap database before upgrading, but I still have all of the old LDIF files I read into SLAP to create the database in the first place. So I read them in again. Voila, now my users can log in once more, and all of their files are present.

BUT, we cannot use Firefox or Evolution, for no reason as far as I can see. HELP!!

---

