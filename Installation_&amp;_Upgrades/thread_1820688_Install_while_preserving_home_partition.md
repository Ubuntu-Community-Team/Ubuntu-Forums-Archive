---
title: "Install while preserving /home partition?"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by DemonSharkKisame on 2011-08-07
Dunno if Kubuntu Trinity receives a lot of support here, but I'll give it a shot.

After hearing that Trinity Desktop Environment might not be ported to Fedora (a consequence of Fedora not allowing stuff to install in /opt), I've considered moving back to (K)ubuntu. I keep my root and /home separate, but I was wondering how exactly to install Trinity so it recognizes my current /home?

---

### Post by ankspo71 on 2011-08-08
Hi,
Switching distributions and preserving your existing home partition can get a little complicated or might not even work well, so I personally recommend backing up your personal files to a cdrom or any other storage device, then preferably do a clean install (reformat) of both / and /home, because I've seen some people have major problems trying to preserve (or share) existing /home partitions between distributions that seem to have major differences from each other (font's, locales, permissions, directory names or structure, etc).

But if you want to try preserving your /home partition while switching from Fedora to Trinity, you could try the following (after making backups of your important data)...

First You would have to use the manual partitioning option when you go to install Trinity. Once you are there in the manual partitioning options, you will  need to assign your mountpoints "/" and "/home" to the corresponding partitions, and then you will need to tell Trinity to reformat the "/" partition, but DO NOT tell Trinity to reformat the "/home" partition. See example image below:

[[IMG]http://img193.imageshack.us/img193/8346/manualparion.png[/IMG]](http://imageshack.us/photo/my-images/193/manualparion.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Reformatting will delete the contents of the partition by recreating the partition, but not formatting the partition will leave the existing files in tact.

When you get to the username and password configuration (further into the installation), use the same username that you used in Fedora, otherwise a new username will use a different home folder.

Hopefully that will be all there is to it, but there are some complications that can occur...

You might need to rename some directories in your home directory:
For example, some distributions use a directory called ".kde4" in your home folder to store the user's KDE specific configurations, but other distributions might use a folder called ".kde". 

You might need to change ownership permissions (userid:groupid) of files and directories:
Ubuntu based distros start out with a userid of 1000 and a groupid of 1000, and other distributions might start out with 500:500 (such as PClinuxOS). I don't know what Fedora starts out with, but you should be able to check your id's in Fedora using the 'id' command:

```
id username
```
Example output showing my userid, groupid, and the groups I belong to.
```
james@Kubuntu:~$ id james
uid=1000(james) gid=1000(james) groups=1000(james),4(adm),20(dialout),24(cdrom),46(plugdev),113(lpadmin),115(admin),120(sambashare)
```

If you need to change ownership of files and directories you could use this command:
```
sudo chown -R username:username /home/username
OR
sudo chown -R 1000:1000 /home/username

```

Note: username:username is actually "your username":"your groupname" and 1000:1000 is actually "your userid":"your groupid"

Hope this helps.

---

### Post by DemonSharkKisame on 2011-08-08
Cool, thanks! Been confused about the specifics of what to do. Will try this once I get the chance. Post saved for future reference. :)

---

