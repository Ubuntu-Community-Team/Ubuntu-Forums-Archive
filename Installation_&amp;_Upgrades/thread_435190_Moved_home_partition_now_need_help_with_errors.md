---
title: "Moved /home partition now need help with errors"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by heatpumpcontrol on 2007-05-06
Hi guys,

Feisty installation

I messed up. To make a long story short... I have a what I believe is an fstab error.

I moved /home from an external drive. (don't ask how it got there..lol), and I was somewhat successful at moving it back onto the local /home. 

Upon boot I get:
Your home directory is listed as '/home/miguel' but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.

If I click no I go back to the log in screen. I I click yes I get the following:
User's $HOME/.drmc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

Clicking Ok gives me the following:

Your session only lasted 10 seconds. If you have not logged out yourself......blah blah blah. Try logging in with one of the failsafe sessions to see if you can fix the problem.

Clicking view details gives me /etc/gdm/Presession errors..pretty long so I'll skip this unless it is necessary.

Here are the following stats that I can give you. 
Mind you all this has to be typed... using another terminal to enter this.

Dual boot:
/dev/sda1            ntfs                XP                 13.30gig
/dev/sda2            extended                            23.95gig
/dev/sda5            ntfs                Navigation    6.37gig
/dev/sda6            ntfs                Data             10.28gig
/dev/sda7            ext3               /                   4.24gig
/dev/sda8            ext3              /home           2.05gig
/dev/sda9          linux-swap                           1gig

I also get this:

*Checking file systems...
fsck 1.40-WIP (14-Nov-2006)
fsck.ext3:Unable to resolve 'UUID=e1fb1119-a8b8-4a65-b2fb-84bf856cd8fb'
/dev/sda8:clean 1207/269280 files, 33067/538169 blocks
fsck died with exit status 8

  *File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable. 
Please repair the file system manually.
 *A maintenance shell will now be started. 
CONTROL-D will terminate this shell and resume system boot.
Give root password for maintenance.
(or type Control-D to continue)...

If I type the root password I get the following:

bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: The: command not found
The program 'apt-get' is currently not installed. You can install it by typing:
apt-get install apt
bash: apt-get: command not found
bash: dircolors: command not found

My fstab file has the following:

proc /proc proc defaults 0 0
#entry for /dev/sda8 :
UUID=4f23b710-9db5-4cd7-971f-1b86e78d46e5 / ext3 defaults, errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=5A604B78604B5A41 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=f070AEA170AE6E52 /media/sda5 nfts-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda6 :
UUID=10D521F69D4B0DF1 /media/sda6 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda7 :
UUID=551e2ee4-59c4-4c40-8c66-18ee716439ef none swap sw 0 0
/dev/scd0 /media/cdrom0 udf , iso9660 user , noauto 0 0
/dev/scdc /media/floppy0 auto rw,user,noauto 0 0

Please help.....

any help will be greatly appreciated.
HPC:(

---

### Post by heatpumpcontrol on 2007-05-06
Added the following at the end of the fstab file:

/dev/sda8 /home ext3 nodev,nosuid 0 2

now I get:
fsck 1.40-WIP
/dev/sda7: clean, 103886/539648 files, 618161/1112493 blocks
*Checking file systems...
fsck 1.40-WIP (14-Nov-2006)
fsck.ext3:Unable to resolve 'UUID=e1fb1119-a8b8-4a65-b2fb-84bf856cd8fb'
/dev/sda8:clean 1207/269280 files, 33067/538169 blocks
fsck died with exit status 8

*File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable. 
Please repair the file system manually.
*A maintenance shell will now be started. 
CONTROL-D will terminate this shell and resume system boot.
Give root password for maintenance.
(or type Control-D to continue)...

I hit Ctl-D and I get a report that dev 'UUID=e1fb1119-a8b8-4a65-b2fb-84bf856cd8fb' does not exist. 
Could this be the external device which contained the /home partition?

Anyway.. I continue to proceed with the login and it will give me another error which is about the:
User's $HOME/.dmrc file....... I click OK and the system boots to my original settings. Progress but with some errors. 

Thanks to anyone taking the time to read this.

---

### Post by heatpumpcontrol on 2007-05-06
UPDATE:
Logged on. Performed a 
$ blkid

and my results are:
sda7 UUID='4f23b710-9db5-4cd7-971f-1b86e78d46e5'
sda8 UUID='5275ff93-47d0-4094-886f-3151ff63920f'
sda9 UUID='d59b696f-c7db-46c5-b1d5-046fe7428135'

I will place these in the fstab by using
sudo gedit /etc/fstab I have a backup of my fstab already so I feel OK messing with it.

I'll post my findings.

---

### Post by heatpumpcontrol on 2007-05-06
OK, I've added the respective UUIDs into the locations pointing to the respective places in the fstab and I got a pretty clean boot. I will have to do it a few more times. 

Upon logging in I stil get the $HOME/.dmrc file error. I will look for a repair to that and report any new findings. I hope this helps some newbies like myself out there.

HPC

---

### Post by heatpumpcontrol on 2007-05-06
OK, I booted in recovery mode and I see that sda8 shows up as a clean boot twice. Is this normal? 

Noticed swap is trying to use sda8 also. 

Will have to edit fstab again to see if that will correct that.

Machine is now running slow though. I believe it's because of all the conflicts. 

When I open gparted, it does not show sda7 as my '/' but it does show sda8 as '/home' and sda9  as 'swap'. 
Sda7 is flagged with 'Unable to find Mount Point' along with the same flags on the three ntfs partitions. (sda1,sda5,sda6) Getting close.

Anyone have any suggestions?

---

### Post by HeyItsMatt on 2007-05-06
Hey, I'm probably even more of a newbie than you so I have a hard time even understanding everything in your post :)   However, your problem sounds fairly similar to mine - I have had many of the same errors as you and cannot log in - instead I get dumped to a command prompt.  I also was messing with my /home folder (put it on a separate partition a little while before trying to upgrade to Feisty).  Here is my post:

[http://ubuntuforums.org/showthread.php?p=2604638#post2604638](http://ubuntuforums.org/showthread.php?p=2604638#post2604638)

Perhaps if I can get any solutions to my problem, they will apply to yours too.

---

### Post by HeyItsMatt on 2007-05-07
I just fixed my problem - all I had to do was change the "hda1" and "hda5" entries in my fstab to "sda1" and "sda5" respectively, and now I feisty seems to be working normally as far as I can tell.  I realize that's not what your problem looks like, but here is a fairly large thread that might have some useful information:

[http://ubuntuforums.org/showthread.php?t=405630&highlight=feisty+sda+fstab](http://ubuntuforums.org/showthread.php?t=405630&highlight=feisty+sda+fstab)

it looks to me like those "UUID" ways of identifying partitions can change a lot, so perhaps you're not using the right ones?  I think there were some directions in the above thread describing how to find the current UUID of a hard drive partition with some command line commands.

---

### Post by heatpumpcontrol on 2007-05-07
> **HeyItsMatt said:**
> I just fixed my problem - all I had to do was change the "hda1" and "hda5" entries in my fstab to "sda1" and "sda5" respectively, and now I feisty seems to be working normally as far as I can tell.  I realize that's not what your problem looks like, but here is a fairly large thread that might have some useful information:

[http://ubuntuforums.org/showthread.php?t=405630&highlight=feisty+sda+fstab](http://ubuntuforums.org/showthread.php?t=405630&highlight=feisty+sda+fstab)

it looks to me like those "UUID" ways of identifying partitions can change a lot, so perhaps you're not using the right ones?  I think there were some directions in the above thread describing how to find the current UUID of a hard drive partition with some command line commands.

Hi Matt,

Good morning and thanks for your response. I have been using Ubuntu/linux for about 5 weeks now coming out of the nightmare that is MS. Don't get me wrong, I love MS, it's just all the attacks on it and all the restrictions on having the software on only one PC that really bothers me. 

I have figured out my issue also. I had to change the UUIDs to point them to the correct sda's or partitions. Sorry if my post is confusing. I figured I put it all on here to help others. My pc boots up normally except for the $HOME/.drmc problem. I am working on that. 

[Here's a link for the $HOME/.dmrc issue]("http://ubuntuforums.org/archive/index.php/t-91455.html") Good luck to you Matt and let me know if I can help. I like to tinker so I'll break this installation soon enough anyway...lol :popcorn:

---

