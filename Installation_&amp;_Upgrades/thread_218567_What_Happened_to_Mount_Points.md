---
title: "What Happened to Mount Points?"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by OldSeaDog on 2006-07-18
Until now every (character mode) install included a lot of ability to manually tune the partition table, which I make liberal use of, since I test various distros and have a total of 11 partitions on three drives for that purpose.  I use Ubuntu as the main OS, with a variety of others available.

When I wnet in to install DD, the partitioner did not give me the ability to change mount points.  Maybe I am a blind fool, but I cannot use an OS that doessn't allow me to fine tune the install and can't find a way in.

Any ideas?

O;ldSeaDog

---

### Post by BuffaloX on 2006-07-18
Maybe I misunderstand, but when you choose manual parttioning, isn't it what the selction of /root, swap and usr is about?
That worked for me, but maybe I was just lucky?

btw I used alternate CD.

---

### Post by OldSeaDog on 2006-07-21
The problem is that it chose where to install the boot, root and swap partitions, and I begged to differ.  In addition it chose to format my data drive, which would have caused me a bit of gas.  It is backed up, but restoring it is a pain.

When I right-click on any of the partitions, I can only make a new partition within the existing one, delete it, Resize/move it, copy it, unmpount it, and deactivate it.  I assume I could have done it on the information tab, but it was disabled (greyed out).

Is the Live CD with an install icon the only way to do this or can I sneak in another way?

---

### Post by avtolle on 2006-07-21
You need to dl and burn the Alternate Install .iso. I think this will provide the control you desire.

---

### Post by Herman on 2006-07-21
Yes, the Dapper Drake 'Alternate' Install CD will allow people to perform special, customized installations. It features the more traditional text based installer we relied on for years.
 
The 'Desktop' Live/Install CD is a great idea and is there for the majority of new users who just want a quick, simple install and who found the text based installer and partitioner too complicated and difficult to understand.

The 'Alternate' Install CD is not really difficult to use at all, it's just that if offers more options, and those who may be installing for the first-time lack the experience of course to be able to know what they want. In the hands of someone with a little experience, the 'Alternate' Install CD is far more useful than the 'Desktop' one.

I made a website dedicated to the 'Alternate' CD to help show people how it may be used. 
My first two sig links show how to use it for installing Ubuntu with a single partition of '/' and a swap area, dual booting with Windows. 
My third sig link will be the one you are after, it illustrates the way to use the partitioner to install Ubuntu with a seperate /home partition. If you carry on in a similar manner as illustrated after step 25, you can keep creatings as many new partitions as you like. 
I must have deleted something there, I though I had the full list of possible partitions listed there somewhere in the sequence the installer will offer them. For example  /boot partition, /usr, /var,  and the rest. It loks like I will have to find that info again and add it again to the web-page.

oldseadog, reading between the lines, I can sense that you know what you are doing.
Some old fashioned Linux sites tell people they *have* to install Linux on all these extra partitions and it isn't true for most (new) people, and can cause more trouble than they are worth. 

For the information of any new-to-Linux people who may chance to read this:
I recommend single partition installs however, especially if you are multiple booting, Unless, that is, you really have a special reason to need a multiple partition install.
The advantage of a nice simple, single partition '/' and swap install is that  directories (folders)  are always automatically the exact size they need to be at any instant.
If we make a seperate partition for every directory, we either waste a lot of disk space making each one more than large enough to allow for future expansion, or risk running out of room in one or more of them and needing to resize them with partitioning software. 
I don't even believe in making my /home partition seperate. It's an old fashioned idea from before we had wonderful journalling filesystems like ext3 and reiserfs.

Modern partitioning software allows us to easily copy the whole partition and paste it to the end of our hard disk as a backup of our installed software and settings instead. It only takes a little over 2 or 2.5 GB or so of space, and about ten minutes of our time.

But that's just my opinion, and we are all entitled to our opinioins and encouraged to install Ubuntu how we like. Especailly when we know what we are doing and have special requirements or needs.

oldseadog,
I will edit that page shortly with the missing oinformation for you and others who may want to make a multi-partiton install with the maximum number of partitions. Maybe it was something I had planned and then just forgot to add.
Regards, Herman :grin:

EDIT: Here are the missing sentences,
>         If you like to make seperate partitions for more parts of your filesystem, such as /boot, /tmp, /usr, /var, /srv, /opt, /usr /local, and even enter more your own manually, you can. In this install the mount point '/home' just comes up automatically in fig 25 and if I had pressed 'enter' while it was highlighted I could have showed you all those options. I found that in the old 'Breezy' web page that the new one replaced. I will add that soon. 
The sequence those are mentioned is the sequence they were offered in 'Breezy', (beginning with /home though). I will have to do another test install to check that the sequence is still the same in 'Dapper'. Probably it will be. (We are not 'tied' to that sequence anyway, though, I'm just being fussy). :grin:

---

### Post by GnuSense on 2006-08-18
Something seems to be mucked up with at least the Xubuntu Dapper Alternate Disc and booting multiple partitions.  I have a laptop with XP plus another installation, Blag 300003. BLAG is on a primary partition, as is XP. Blag also has a /home partition that I wanted to share with Xubuntu (with different usernames so there theoretically shouldn't be a conflict).  There was also a 2 GB vfat partition that I decided to convert to the root partition for Xubuntu. When I got to the partitioner program (some incarnation of QTPARTED, I guess) I told the install program to mount my Windows partition as /win and my Blag partition as /blag.  I got an error message telling me I couldn't mount the Windows partition for some reason.  I went back and deleted references to mounting the NTFS partition, figuring (rightly it turns out) that I could go back and set it up properly in the FSTAB later.  I told Xubuntu to mount BLAG as /media/hda3, I believe.

So I booted in to Xubuntu and then in to Windows (which gave me a chkdsk, but no big deal), but when I tried booting BLAG I got a slew of error messages.  

> touch: cannot touch '/var/log/wtmp': Read-only file system....
rm: cannont remove '/var/run/acpid.socket': Read-only file system....
chmod: changing permissions of '/var/run/utmp': Read-only file system   And so forth. I got a warning that I couldn't boot X and the machine just hung. I booted to Xubuntu & looked at the permissions in the Blag /var directory, which seem normal, with root owning everything, or course.  I double checked the GRUB configuration and even pasted the original BLAG stanze in to it, but got the same result.  So it looks like Xubuntu somehow scrambled some permissions.

What is more, I decided to upgrade to a more recent version of BLAG.  I ran the installer and got > Multiple devices on your system are labelled /. Labels across devices must be unitque for your system to function properly.

Please fix this problem and restart the installation process.  So not only did Xubuntu make it impossible to boot my other Linux distribution, it appears to have made it impossible for me to fix the situation without deleting Xubuntu.  I may try installing another distro over the BLAG partition, but I'd actually like to rescue the old install.  Suggestions?

---

