---
title: "Partitioning"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by mdhollis on 2011-05-11
I was wondering what the best way is to partition multiple distros to share one home partition.

---

### Post by pSYcl0Ne on 2011-05-11
Sharing a home partition isn't a great idea. A lot of configuration settings are stored there and separate operating systems can cause headaches.

My advice would be to have a separate partition altogether for documents etc, formatted to ntfs or fat if youre also using windows or mac

---

### Post by mdhollis on 2011-05-11
Yeah I have been learning this the hard way.

---

### Post by pSYcl0Ne on 2011-05-11
I've been learning that way for years.

---

### Post by srs5694 on 2011-05-11
> **pSYcl0Ne said:**
> Sharing a home partition isn't a great idea. A lot of configuration settings are stored there and separate operating systems can cause headaches.

It's critical to distinguish between two very different, but similarly-named, things:


[list]
[*]**The /home directory or partition** -- This location holds the home directories (see below) for an arbitrary number of users. It's often split off into a separate partition, although Ubuntu doesn't do this by default (IMO, it should).
[*]**Users' home directories** -- These are usually subdirectories of the /home directory. Normally, each user has a separate home directory, such as /home/harry or /home/sally.
[/list]


Your statement is true of user home directories, but not of the /home directory/partition. It's perfectly safe to share a /home partition between dual-booted distributions *if* you create separate user home directories for each user on each distribution. For instance, /home/harry-f14 and /home/harry-u1104 could be the user harry's home directories for Fedora 14 and Ubuntu 11.04, respectively. This sort of configuration is easily achieved in various ways. The easiest, particularly with Ubuntu's limited install-time tools, is to use a different username for each distribution. A more sophisticated method is to use the same username in each distribution but assign a home directory that's not identical to the username -- so the user harry's home directory would be /home/harry-f14 or /home/harry-u1104 depending on the distribution. This is easily done with text-mode tools like useradd, and even with GUI tools in most distributions, although AFAIK the Ubuntu installer doesn't support setting things up this way from the start.

> My advice would be to have a separate partition altogether for documents etc, formatted to ntfs or fat if youre also using windows or mac

If you want to share most of your documents with another OS, this makes sense (although using NTFS for a Linux/MacOS dual-boot is extremely inadvisable for various reasons; use FAT or unjournaled HFS+ instead). When not booting with one of these OSes, or when the need for data exchange with these OSes is limited, though, I recommend using a single /home partition and separate user home directories, as just described. Using a separate Linux data partition is just re-inventing the wheel. The /home directory is intended to hold user data, and creating another partition (and therefore another directory) for this purpose just complicates your partition and directory layout, creating a variety of problems that range from very minor to moderately serious. These range from additional administrative effort (in partitioning, creating symbolic links, etc.) to added risk (if you create separate /home and data partitions, and guess the sizes wrong, resizing after the fact is risky).

---

### Post by mdhollis on 2011-05-13
I have it set up now with different usernames, is there a way grant permissions to another user from a different os?  

I very rarely boot into windows anymore.  I have fedora, ubuntu and mint installed on my computer.  I'm not so much worried about mint because I have been testing it as a ubuntu alternative.  But I really want to share my music, videos and documents with ubuntu and fedora.  I have tried using the same username and I ran into problems.

[QUOTEYour statement is true of user home directories, but not of the /home directory/partition. It's perfectly safe to share a /home partition between dual-booted distributions if you create separate user home directories for each user on each distribution. For instance, /home/harry-f14 and /home/harry-u1104 could be the user harry's home directories for Fedora 14 and Ubuntu 11.04, respectively. This sort of configuration is easily achieved in various ways. The easiest, particularly with Ubuntu's limited install-time tools, is to use a different username for each distribution. **A more sophisticated method is to use the same username in each distribution but assign a home directory that's not identical to the username -- so the user harry's home directory would be /home/harry-f14 or /home/harry-u1104 depending on the distribution. This is easily done with text-mode tools like useradd, and even with GUI tools in most distributions, although AFAIK the Ubuntu installer doesn't support setting things up this way from the start.**[/QUOTE]

Can you expand on that? Thanks for the reply!

---

### Post by srs5694 on 2011-05-13
Fundamentally, Linux uses numbers for everything. You're not really mdhollis, or harry, or jones, or whatever; you're 1000 or 507 or some such. Unfortunately, Ubuntu begins numbering its users at 1000, whereas Fedora begins numbering its users at 500. Thus, your home directory, and the files it contains, are probably owned by user ID (UID) 500 in Fedora, whereas those in Ubuntu are owned by UID 1000. Even if you've got the same username, this means that your files will look like they're owned by different users when you create them from different distributions. (You'd get the same problem whether you use a shared /home partition, as I advised, or a separate user data partition, as others have advised.)

The solution is to synchronize your UID values across the two distributions. This is most easily done on the Fedora side:


[list=1]
[*]Boot Fedora.
[*]If your system is configured for automatic login, log out.
[*]Type Ctrl+F2 to get a text-mode login prompt.
[*]Log in as root.
[*]Type "ls -n /home" to view your home directories and determine the UID associated with your Ubuntu home directory. The UID should be in the third column (the second column with numbers). Chances are it will be 1000.
[*]Type "usermod -u 1000 myname", but change "1000" to the UID you determined in the last step and "myname" to your username in Fedora.
[*]Type "ls -n /home" again to check the UID of your Fedora home directory. If it hasn't changed since you used usermod, you'll have to type "chown -R myname: /home/mydir" (making appropriate substitutions for "myname" and "mydir") to change the file ownership. Chances are usermod will have done this automatically, though; this step is mainly just to verify it actually was done.
[*]Type Ctrl+F1 to get to the Fedora login prompt and try to log in and use the system. It should work fine. If you detect any weirdness, there's probably a file somewhere with inappropriate ownership for the new UID; you'll need to track it down and fix it.
[/list]


As to using a home directory name that's not identical to your username, you can use usermod to modify the user's home directory or username. For instance, if you created the accounts harry-f14 and harry-u1104, with matching home directories, you could type, as root in Fedora:

```

usermod -l harry harry-f14

```

This will change the username from harry-f14 to harry. A similar command will work in Ubuntu; however, because Ubuntu doesn't activate the root account, there may be some weirdness if you try this using sudo from the account you want to change. Your best bet is to either activate the root account (which Ubuntu's developers discourage) or create another account with administrative privileges and run the usermod command (using sudo) from that account. It's possible you'll need to do some cleanup by editing /etc/group, /etc/sudoers, and other files that reference users by name rather than by UID. I'm not sure offhand how many such files usermod changes automatically.

Type "man usermod" to learn more about this command. It's very flexible. You can do some of what it does from GUI tools, but I gave up long ago trying to remember which distributions' GUI tools did what, so you'll have to look them over yourself if you want to use the GUI tools.

---

### Post by mdhollis on 2011-05-13
Changing my UID value worked like a charm.  Thanks for the simple directions.

---

### Post by pSYcl0Ne on 2011-05-14
> **srs5694 said:**
> 
Your statement is true of user home directories, but not of the /home directory/partition. It's perfectly safe to share a /home partition between dual-booted distributions *if* you create separate user home directories for each user on each distribution. For instance, /home/harry-f14 and /home/harry-u1104 could be the user harry's home directories for Fedora 14 and Ubuntu 11.04, respectively. This sort of configuration is easily achieved in various ways. The easiest, particularly with Ubuntu's limited install-time tools, is to use a different username for each distribution. A more sophisticated method is to use the same username in each distribution but assign a home directory that's not identical to the username -- so the user harry's home directory would be /home/harry-f14 or /home/harry-u1104 depending on the distribution. This is easily done with text-mode tools like useradd, and even with GUI tools in most distributions, although AFAIK the Ubuntu installer doesn't support setting things up this way from the start.




Wow, thanks hey - I'm gonna do some repartitioning later and save a lot of space/grief (permissions) thanks. I never thought of that - mainly due to the fact I often use the same user name over all distro's.

---

