---
title: "BusyBox prompt after update"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by Peet on 2008-02-08
Hi,
I have upgraded from kubuntu 7.04 to 7.1 (AMD64) on my HP Compa nx 7400, no problem (hich surprised me as I believe there are issues with HP laptops, but I want to get Mixxx working, so needed the upgrade), so I get occasional updates, fine, then comes about 28 updates (cannot recall which)

---

### Post by Peet on 2008-02-11
No reply or advise, so I will reformat and hope the same does not happen again, I would still like to know what I could have done. Will download the 7.1 image at some stage, then there might be a repair option from the DVD?

---

### Post by Herman on 2008-02-11
:) Hello Peet,
 I don't know why you would get the BusyBox prompt after update. I haven't seen that error for quite a while but I'm also interested in learning something.
I try to collect information on all kinds of booting errors.

If you had a busybox prompt after doing some work with a hard disk partitioner that maybe changed your file system UUID number it could be this, [busybox or tty error]("http://users.bigpond.net.au/hermanzone/p15.htm#busybox") and that's easy to fix and used to happen sometimes. Especailly when people insisted on using partitioners made only for Windows.

Otherwise there's this one here and probably lots of variations of it, [Target filesystem doesn't have /sbin/init]("http://users.bigpond.net.au/hermanzone/p15.htm#Target_filesystem_doesnt_have_").

Maybe this link will lead to more understanding,[The Linux Boot Process]("http://www.google.com.au/url?sa=t&ct=res&cd=5&url=http%3A%2F%2Foldfield.wattle.id.au%2Fluv%2Fboot.html&ei=aAewR7WIGpOkpASE1PySAw&usg=AFQjCNGs48QXL6MoLjclewri4uOa3CQomA&sig2=Lt2AYcgPpjB89t2uo5iFJg")

Also check this link, 
[[SOLVED] SOLUTION: missing /sbin/init causes boot to exit to ...]("http://www.google.com.au/url?sa=t&ct=res&cd=10&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D466603%26highlight%3DTarget%2Bfilesystem%2Bdoesn%27t%2Bhave%2B%252Fsbin%252Finit&ei=aAewR7WIGpOkpASE1PySAw&usg=AFQjCNHH_tlqSsas_BJIsgwdmfuzyCxAwA&sig2=aK0zJ4aJuOS0B0z5TMhm9g")

I hope something there at least makes interesting reading.
Regards, Herman :)

---

### Post by Peet on 2008-02-12
Hello Herman,

Thank you for your reply, you gave me some threads I have not found!  (And some new hope!), I did not reformat yet, as I needed to take my laptop home, so now  I have booted with live DVD, mounted my normal hard disk, chroot'ed to it and am running update (still 123 upgradable, hoping to complete the upgrade and miraculously have a fixed system!

Will post the results, it is taking laboriously long to download 179M!

Cheers
Peet

---

### Post by Peet on 2008-02-13
OK, Applied all updates I could, some problem with Openoffice, removed it, restarted updates... Still getting the prompt, so I guess it is now a reinstall job!

Is there not a function on the DVD's that one can use to rebuild an existing OS, rather than complete reinstall?  That is one of the few nice functions with micro$oft, though the last time I used it, it repartitioned my drive, causing me to loose my working Linux!

---

### Post by Herman on 2008-02-13
First, do you have more then one set of entries for Ubuntu in your [GRUB menu]("http://users.bigpond.net.au/hermanzone/p15.htm#gui")?
If you had a new kernel in your update and that's what's causing your trouble, you should be able to scroll down to the previous kernel in your GRUB menu and boot Ubuntu as before. 

Linux is very different in lots of ways, and everyone has their own way of backing up their systems and organising their disks and partitions. I have tried making backups of the operating system with 'dd' commands, and then with Partimage. Here's a link, [Use PartImage]("http://www.psychocats.net/ubuntu/partimage") 
Those were both good ways fo doing things but lately I haven't been too bothered about backing up my systems and software, just my files.

Since Ubuntu is free, there's no restriction on the number of copies of Ubuntu I can have on one hard disk. Therefore, it's quite simple to install a fresh copy of Ubuntu beside the older or disabled one. The new installation will automatically mount the existing one. I just installed Hardy Herron yesterday beside my old Gutsy installation and I can just reach into my old /home/username directory and grab any files I need.
If you click 'view'-->'show hidden files', you'll see just about all the files you'll want to transfer across. Just copy and paste those from your old /home/username directory into your new one.
I always open my .evolution directory and copy my calendar, addressbook, mail, memos and tasks. Those will be copied into my new .evolution directory once I open Evolution and set it up in my new system.
Firefox bookmarks are in .mozilla/firefox/hash.default. That can be copied into the same location in the new system once I start firefox.
The rest depends on what software you installed. I use 'password manager', so I copy my .gpass directory to the new /home/username folder. Then when I install Password manager again it will automatically find that and open it.
Any PGP keys or RSA keys are important to transfer.
If you're moving into the same version of Ubuntu, it's easy to grab all the packages for added software you've downloaded from /var/cache/apt/archives. Copy those to /var/cache/apt/archives in the new system. That saves downloading them all over again, you just need to re-install them, which is pretty quick when they're already there.

Ubuntu only takes around half an hour to install from just one CD, complete with just about everything we need. It's not as if we're going to spend days with a big pile of CDs and having to reverify our accounts with antispyware apps and download updates and reboot several dozen times and all those hassles. In around another half hour if you know what you are doing you'll have everything back to normal again.

I'm pretty lazy so I always just have two or more copies of Ubuntu all the time. Sometimes it's the current release and the older version of Ubuntu. Then when it gets closer to time for the next release to come out I might delete the oldest installation and install a test version in its place, of the next Ubuntu, a while before it's release date.

Other people have different ways of doing things. A lot of people like to create a separate /home partition when they install Ubuntu. Then if their system gets borked they just install again and all their files and settings remain in the /home partition, which is mounted again by their fresh install.

Ubuntu does have some nice backup and restore software as well, but you need to install it yourself and run it, I've tried out '[sbackup]("http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html")', which is very good. 
Here's another way, [Backing up Ubuntu]("http://www.psychocats.net/ubuntu/backup")

---

### Post by Peet on 2008-02-15
Hi, Again thanks for the informative reply, especially where /archives is concerned, I tend to spend almost a day reinstalling software (At work we have a 4M ADSL pipe, though downloads still take ages).

I have tried booting to the previous kernal, but I then get the tty... err with BusyBox prompt, while the "normal" boot gives me no visible errors, just busybox prompt, from where I am stuck.

I have to use M!cro$oft, as I need programs like Autocad (Or direct equivelant), and I programme a number of devices..., I have not been successful at pasing ports through to WinE.  I therefore keep all my data on the NTSF partition, so that I can access everything anywhere.  I have even figured out how to let Thunderbird use the same directory in win and Linux, saving the need to download everything twice!

I am not realy interested in backing up my OS, in my experence I have never been able to restore a backed up OS to a working state, trying to use w restore has 3 times resulted in having to reformat and start that OS again.

Thanks again for the great advice!

---

