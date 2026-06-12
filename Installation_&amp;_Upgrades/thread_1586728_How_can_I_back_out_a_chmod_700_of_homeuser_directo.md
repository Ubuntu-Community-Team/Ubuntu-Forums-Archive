---
title: "How can I back out a chmod 700 of /home/user directory (misguided attempt at security"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by rocksockdoc on 2010-10-02
a) How come root isn't helping me here?
b) It doesn't help that the ubuntu-generated encrypted passphrase was stored INSIDE the home directory.

Problem:
What I did, following some web advice, was chmod 700 my /home/user directory ('user' is the login of the user) in a misguided attempt at security.
$ chmod -700 /home/user

Upon reboot, unfortunately, gnome wouldn't work (presumably due to the fact it must need something to write to). 

So, silly me, I thought I'd just su to root or sudo as the user and change the permissions back.

Well, ROOT won't do that. It won't even MOUNT the file system. It tells me how to mount it but it's encrypted, probably when I installed ubuntu a month ago.

Thinking back to when I installed Ubuntu a month ago, I opted for encrypted file system, but it never reared it's ugly head until now. I remember dimly that Ubuntu would not let me tell it the passphrase, it needed to tell me, so I put it in a file inside the file system. (Dumb dumb dumb.)

I can log into Gnome as an xterminal, but even it won't access the directory. There is only one user and I am the only user of the laptop. I guess I can wipe the system clean and re-install the operating system, but, if I could just get root access to the /home/user directory, I could chmod it back!

Two questions:
a) How can I get root to be real root (like in the UNIX days?) to chmod it back?
b) What can I log into if Gnome won't work?

---

### Post by luvshines on 2010-10-02
Are you not able to get to the login screen ??
I mean, can't you login to the user through the terminal ?

---

### Post by rocksockdoc on 2010-10-02
> **luvshines said:**
> Are you not able to get to the login screen ??
I mean, can't you login to the user through the terminal ?

It's hard to explain.
Yesterday ... 
- I logged into Gnome as "user"
- Up came my customized screen
- In "Places", I could go to my sub directories under /home/user, e.g., /home/user/data.

Then, I followed some web advice for security to chmod 700 /home/user (and used the computer for the rest of the day and today, this morning, it was fine). Maybe it was something else I did, because I did install "wine" and in "Ubuntu Tweak", I did update applications. 

Then I rebooted.


From there on, my whole world is different.

First thing, Gnome complained a few times about not being able to access some dot files (I should have written it down but I wasn't expecting it) and just showed the default purplish clouds (and almost nothing else). This error went away when I did a subsequent "sudo -i" and chmod -R 777 /home/user so now I can log into Gnome and the menu system is at the default but my files are nowhere to be seen.

ls /home/user just reports:
Access-Your-Private-Data.desktop  Downloads  Pictures     Templates
Desktop                  Public     Videos
Documents              Music      README.txt

But, I had lots of FILES & DIRECTORIES there which are nowhere to be seen.

At this point, after running the chmod back (to 777 for now), I can log into the "user" account in Gnome without it complaining; but EVERYTHING is different. It's back to the original Gnome default look and feel (which is no big deal) and ALL my files (e.g., /home/user/data) are nowhere to be found (which is a big deal).

Even my Firefox customizations are all lost. 

Interestingly, all my programs in the Gnome Applications menu are still there ... but none of my files under /user/home seem to be there (other than the defaults shown above). I am perplexed! 

There is only one password for this system, and I'm the only user, and I have the ultimate power ... if I only knew how to figure out what went wrong (maybe it wasn't the chmod but I think it was because Gnome complained about not being able to write to a dot configuration file at first).

What debugging can I do to find where my files & directories went?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171087&stc=1&d=1286040010[/IMG]

---

### Post by efflandt on 2010-10-02
You did NOT **chmod 700** your home directory, you did **chmod -700**.  I could be wrong, but doesn't that "remove" all permissions for yourself (including even disabling **ls** of that directory)?

I have not used encrypted directories, so not even sure if you could fix that using sudo from live/install CD.

---

### Post by luvshines on 2010-10-02
No, it must have been chmod 700 or something else, but definitely not chmod -700
```

chmod -700 /tmp/a
chmod: invalid option -- '7'
Try `chmod --help' for more information.

```

---

### Post by luvshines on 2010-10-02
Can you paste the output of:

sudo fdisk -l

AND

mount

commands

---

### Post by Quark718 on 2010-10-02
I got bit by this one once back in 9.04 days.  I encrypted my drive then silly me I thought I could change my system password.  Well my system would boot to an extent but when it tried to mount my file system the new system password wouldn't decrypt.  You sound like your in better shape than I was.  I eventually got it by mounting my file system from a live disc which has full root privileges with a simple sudo -s.  This also bypasses your chmod permissions issue because it is effect a totally different os.  I forget how to mount the encrypted file system from a live disc but it's up here somewhere and it was pretty simple.

I only encrypt my data directories now a days.  I learned my lesson.

---

### Post by rocksockdoc on 2010-10-02
> **efflandt said:**
> You did NOT **chmod 700** your home directory

I didn't write it down when I did it so I might be mixing my Solaris commands with my Ubuntu commands. 

It was a cut and paste of a web article, one line, that did a chmod 700.

At this point, I think my problem is that the encryption software kicked in (probably from too many failed attempts).

I remember, it's coming back to me anyway, when I installed Ubuntu, it asked if I wanted my directory encrypted (I think) and I remember it did NOT give me (as I would have expected) the choice of a passphrase. :(   

It just gave me a passphrase (which, IIRC, was a list of numbers, about 10 digits long).

THAT passphrase is saved in a file on the hard disk in the directory that is now encrypted and I can't get to it. I didn't do ANYTHING with the encryption (except try a few passphrases which all failed).

I have full root, and I know the names of the files I want ... they're just not there. :(

---

### Post by rocksockdoc on 2010-10-02
> **luvshines said:**
> sudo fdisk -l AND mount

I'd be happy to provide you any information you need!

Here is the result:
```

user@donna:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00096a1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112412672   83  Linux
/dev/sda2           13995       14594     4805633    5  Extended
/dev/sda5           13995       14594     4805632   82  Linux swap / Solaris

```

```

user@donna:~$ sudo mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /dev/shm type tmpfs (ro)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=user)
user@donna:~$ 


```



[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171094&stc=1&d=1286043790[/IMG]

---

### Post by luvshines on 2010-10-02
I haven't worked with encrypted filesystem :(

But the guy here in the last comments tells how to recover it.
[http://newyork.ubuntuforums.org/showthread.php?t=1534704](http://newyork.ubuntuforums.org/showthread.php?t=1534704)

Better wait and let some expert comment come into this thread.

---

### Post by rocksockdoc on 2010-10-02
> **Quark718 said:**
> I only encrypt my data directories now a days.  I learned my lesson.

I'm learning mine! :(

I think, but don't know for sure, the "problem" now is that, for some reason, the encrypted file system (which is my entire home directory) is not mounted.

But, Gnome, yesterday, was mounting it fine. So, I "think" the chicken-and-the-egg problem I have right now is that, while I can su to root and chmod the home directory to 777, I just can't seem to MOUNT those files in order to chmod them.

But, the thing is, GNOME should be able to do that when I reboot; but it no longer does.

It's almost as if I have to enter the (missing) encrypted passphrase (oh how I wish I hadn't stored it in my data files!) before Gnome will mount my (true) home directory.

Right now, Gnome is mounting 'something' which 'looks' like a home directory, but it's not mine. Mine is, .. somehow ... missing.

Is this the process:
- Boot to live cd ubuntu
- Switch to root
- Somehow mount the /home/user file system (the real one)
- Read the encrypted passphrase out of the file inside that file system

Then go back to a normal boot?

PS: Why does Gnome NOT do all that decryption stuff it did yesterday?

---

### Post by rocksockdoc on 2010-10-02
I'm going to try to 'mount' the apparently encrypted home directory from a ubuntu cd.
I found[ these instructions]("http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/"):
[http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)

Before I do that, may I ask someone who has done this before.

Is this a waste of time (i.e., will it ask for the encryption passphrase generated by Ubuntu when I installed the operating system?)?

(That encryption passphrase, which was a bunch of numbers IIRC, is stored on the encrypted drive! :(  )

Or will it ask for the login? (root is the same as the user).

It doesn't say in the article (I wish they'd be more explicit.).

Thanks for any help,
Donna

---

### Post by luvshines on 2010-10-02
Can't you access the data by following the shortcut or typing that command which it says ??

---

### Post by rocksockdoc on 2010-10-02
> **luvshines said:**
> Can't you access the data by following the shortcut or typing that command which it says ??

I'm hoping the solution is something as simple as that, but, I think THAT command is exactly what has the system locked at the moment!

I tried it three or five times (hoping it was asking for the root password and not the Ubuntu-assigned encryption key).

```

user@donna:~$ ls
Access-Your-Private-Data.desktop  Documents  Music     Public       Templates
Desktop                  Downloads  Pictures  README.txt  Videos
user@donna:~$ cat README.txt
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
user@donna:~$ ecryptfs-mount-private
Enter your login passphrase:
Inserted auth tok with sig [2a1860e7cb545c30] into the user session keyring
open: Read-only file system
Error locking counteruser@donna:~$ 


```
The main problem right now is that the file system under /home/user is not mounted!

Apparently that /home/user file system is encrypted. And I can't unencrypt it because Ubuntu never gave me the opportunity to define my own encryption key (which I could remember). And the encryption key is on the encrypted drive. 
[COLOR=DarkRed]
[B]It's a chicken and egg thing ... 

If only Gnome could access the encrypted drive, I could either chmod 744 the /home/user file system and/or read the encryption key stored in that file system. [/B][/COLOR]

**Why won't Gnome read the encryption keys? (It did yesterday!)**

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171109&stc=1&d=1286054880[/IMG]

---

### Post by rocksockdoc on 2010-10-02
[COLOR=DarkRed]**THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.**[/COLOR]

**Why did this happen?**
And how do I recover from this?

---

### Post by rocksockdoc on 2010-10-02
> **rocksockdoc said:**
> [COLOR=DarkRed]**THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA**[/COLOR]

**It would be nice if someone can tell me whether I'm dead or not.**

There's no way I'm going to remember that encryption passphrase Ubuntu generated for me (which, silly me, I left in a text file in the home directory). 

In (sad) hindsight, I recommend two things to the next user:
1. DO NOT use Ubuntu encryption (use Truecrypt which allows you to have your own passphrase!)
2. If you do use Ubuntu encryption, then you MUST WRITE the Ubuntu-generated encryption passphrase on a piece of paper (because Ubuntu won't let you use your own key that you can remember at the time of installation)!
3. Since you have to write down the incomprehensible Ubuntu-generated passphrase, go back to #1 above ... DO NOT use Ubuntu encryption!

[COLOR=DarkRed]**This is dumb.**[/COLOR] Both on the part of Ubuntu (for not letting me choose my own passphraseat the time of installation that I could remember and therefore forcing me to write it down on a piece of paper which I didn't do); and dumb on my part (for leaving the passphrase in my installation log text file in the encrypted home directory).

But, lesson learned doesn't solve the current problem of:
[COLOR=DarkRed]**THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA**[/COLOR]

**To solve that, I have the following questions to answer:**
**Q1:** If the encryption passphrase is only in a text file in the encrypted directory, how did GNOME access the encryption key in the first place for the last month (since installation)?

**Q2**: And, WHY was the encrypted filesystem unmounted anyway? I didn't manually unmount it.

**Q3:** The big one: There is no way I'll guess at that encryption passphrase. Is there another way to mount that /home/user directory WITHOUT the encryption passphrase?

**Note: I'm reading the following references, hoping they'll help:**
[SIZE=1]https://help.ubuntu.com/community/EncryptedHome
[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)
[http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html](http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
[/SIZE]http://ecryptfs.sourceforge.net/ecryptfs-pam-doc.txt

---

### Post by luvshines on 2010-10-02
Can you do this ?

ls -lRa in /home/user

---

### Post by rocksockdoc on 2010-10-02
May I ask ... 

WHAT passphrase is my "login passphrase"?

The only passphrase I know is my login password.

Is THAT what Ubuntu is asking for below?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171113&stc=1&d=1286058828[/IMG]

---

### Post by nerdy_kid on 2010-10-02
ok the passphrase is your login password.

what you need to do is go into recovery mode by hitting shift as the system boots and selecting recovery.  choose root prompt at the dialog.

then create a new user and add him to the admin group:

adduser help
addgroup help admin

then reboot

reboot

login to the new user.
open a terminal.

go to the encypted home of the old user and do the ./ecryptfs-mount-private thing.  The passphrase is your original user's password.  once it is mounted, switch to the orginal user in the terminal:

sudo -i -u USER_NAME

make sure you are in your $HOME.  then do 
chmod -R u+rw *

you should have write access again.  switch sessions and log in to the orginal user.  conferm that everything works right.  if not...

go back to the help account and do
chmod -R u+rw .*
try again.

if so...
you are all set!
reboot the pc; log back into the fixed account and delete the help account.

hope this helps.

---

### Post by rocksockdoc on 2010-10-02
> **luvshines said:**
> ls -lRa in /home/user

I'll do anything! :)  Just tell me what to do! :)

Note: I also installed "wine" yesterday - but I don't think that was the problem.

```

user@donna:~$ pwd
/home/user
...
user@donna:~$ ls -lRa
.:
total 300
drwxrwxrwx 36 user user  4096 2010-10-02 15:48 .
drwxr-xr-x  4 root root  4096 2010-08-12 04:26 ..
lrwxrwxrwx  1 user user    56 2010-08-12 04:26 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
drwx------  3 user user  4096 2010-10-02 10:31 .adobe
-rwxrwxrwx  1 user user  1102 2010-10-02 15:47 .bash_history
drwxrwxrwx  4 user user  4096 2010-10-02 15:28 .cache
drwx------  3 user user  4096 2010-10-02 09:35 .compiz
drwxrwxrwx 12 user user  4096 2010-10-02 14:49 .config
drwxrwxrwx  3 user user  4096 2010-10-02 07:43 .dbus
drwxrwxrwx  2 user user  4096 2010-10-02 07:43 Desktop
-rw-r--r--  1 user user    41 2010-10-02 15:28 .dmrc
drwxrwxrwx  2 user user  4096 2010-10-02 07:43 Documents
drwxrwxrwx  2 user user  4096 2010-10-02 07:43 Downloads
lrwxrwxrwx  1 user user    30 2010-08-12 04:26 .ecryptfs -> /home/.ecryptfs/user/.ecryptfs
-rwxrwxrwx  1 user user    16 2010-10-02 07:43 .esd_auth
drwxr-xr-x  2 user user  4096 2010-10-02 10:12 .fontconfig
drwxrwxrwx  4 user user  4096 2010-10-02 15:28 .gconf
drwxrwxrwx  2 user user  4096 2010-10-02 15:47 .gconfd
drwx------  4 user user  4096 2010-10-02 10:12 .gegl-0.0
drwxr-xr-x 22 user user  4096 2010-10-02 11:23 .gimp-2.6
drwxrwxrwx  8 user user  4096 2010-10-02 15:27 .gnome2
drwxrwxrwx  2 user user  4096 2010-10-02 07:55 .gnome2_private
drwxr-xr-x  2 user user  4096 2010-10-02 10:21 .gstreamer-0.10
-rw-r--r--  1 user user   132 2010-10-02 15:28 .gtk-bookmarks
dr-x------  2 user user     0 2010-10-02 15:28 .gvfs
-rwxrwxrwx  1 user user  1570 2010-10-02 15:28 .ICEauthority
drwxr-xr-x  2 user user  4096 2010-10-02 09:45 .icons
drwxrwxrwx  3 user user  4096 2010-10-02 07:47 .local
-rw-r--r--  1 user user     0 2010-10-02 15:48 ls_-lRa.txt
drwx------  3 user user  4096 2010-10-02 10:31 .macromedia
drwxrwxrwx  4 user user  4096 2010-10-02 07:55 .mozilla
drwxrwxrwx  2 user user  4096 2010-10-02 07:43 Music
drwxrwxrwx  2 user user  4096 2010-10-02 07:43 .nautilus
drwxrwxrwx  2 user user  4096 2010-10-02 07:43 Pictures
lrwxrwxrwx  1 user user    29 2010-08-12 04:26 .Private -> /home/.ecryptfs/user/.Private
drwxrwxrwx  2 user user  4096 2010-10-02 07:43 Public
drwx------  2 user user  4096 2010-10-02 15:28 .pulse
-rwxrwxrwx  1 user user   256 2010-10-02 07:43 .pulse-cookie
lrwxrwxrwx  1 user user    52 2010-08-12 04:26 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
drw-------  2 user user  4096 2010-10-02 10:05 .recently-used.xbel
-rwxrwxrwx  1 user user     0 2010-10-02 07:49 .sudo_as_admin_successful
drwxrwxrwx  2 user user  4096 2010-10-02 07:43 Templates
drwxr-xr-x  2 user user  4096 2010-10-02 09:45 .themes
drwx------  4 user user  4096 2010-10-02 09:45 .thumbnails
drwx------  2 user user  4096 2010-10-02 10:16 .TrueCrypt
drwx------  2 user user  4096 2010-10-02 09:35 .update-notifier
drwxrwxrwx  2 user user  4096 2010-10-02 07:43 Videos
-rwxrwxrwx  1 user user  3584 2010-10-02 11:19 .viminfo
drwxr-xr-x  4 user user  4096 2010-10-02 09:56 .wine
-rw-------  1 user user 24323 2010-10-02 15:48 .xsession-errors
-rw-------  1 user user 98680 2010-10-02 15:27 .xsession-errors.old

./.adobe:
total 12
drwx------  3 user user 4096 2010-10-02 10:31 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..
drwx------  3 user user 4096 2010-10-02 10:31 Flash_Player

./.adobe/Flash_Player:
total 12
drwx------ 3 user user 4096 2010-10-02 10:31 .
drwx------ 3 user user 4096 2010-10-02 10:31 ..
drwx------ 3 user user 4096 2010-10-02 10:31 AssetCache

./.adobe/Flash_Player/AssetCache:
total 12
drwx------ 3 user user 4096 2010-10-02 10:31 .
drwx------ 3 user user 4096 2010-10-02 10:31 ..
drwx------ 2 user user 4096 2010-10-02 10:31 ZLUJPMKG

./.adobe/Flash_Player/AssetCache/ZLUJPMKG:
total 8
drwx------ 2 user user 4096 2010-10-02 10:31 .
drwx------ 3 user user 4096 2010-10-02 10:31 ..

./.cache:
total 40
drwxrwxrwx  4 user user  4096 2010-10-02 15:28 .
drwxrwxrwx 36 user user  4096 2010-10-02 15:48 ..
drwxrwxrwx  2 user user  4096 2010-10-02 15:28 compizconfig
-rwxrwxrwx  1 user user 12288 2010-10-02 11:34 event-sound-cache.tdb.0d6e2173dda0703366309b6c4c6423db.i486-pc-linux-gnu
-rw-r--r--  1 user user   528 2010-10-02 15:37 indicator-applet.log
-rw-r--r--  1 user user  4071 2010-10-02 15:47 indicator-applet-session.log
-rwxrwxrwx  1 user user    93 2010-10-02 15:31 notify-osd.log
drwxrwxrwx  2 user user  4096 2010-08-12 04:28 wallpaper

./.cache/compizconfig:
total 228
drwxrwxrwx 2 user user 4096 2010-10-02 15:28 .
drwxrwxrwx 4 user user 4096 2010-10-02 15:28 ..
-rwxrwxrwx 1 user user 4338 2010-10-02 07:32 animation.pb
-rwxrwxrwx 1 user user   58 2010-10-02 07:32 annotate.pb
-rwxrwxrwx 1 user user   71 2010-10-02 07:32 blur.pb
-rwxrwxrwx 1 user user   49 2010-10-02 07:32 clone.pb
-rwxrwxrwx 1 user user   73 2010-10-02 07:32 colorfilter.pb
-rwxrwxrwx 1 user user 2021 2010-10-02 07:32 commands.pb
-rwxrwxrwx 1 user user 3087 2010-10-02 07:32 core.pb
-rwxrwxrwx 1 user user   77 2010-10-02 07:32 cube.pb
-rwxrwxrwx 1 user user   46 2010-10-02 07:32 dbus.pb
-rwxrwxrwx 1 user user  526 2010-10-02 07:32 decoration.pb
-rwxrwxrwx 1 user user 1362 2010-10-02 07:32 expo.pb
-rwxrwxrwx 1 user user 1912 2010-10-02 07:32 ezoom.pb
-rwxrwxrwx 1 user user  602 2010-10-02 07:32 fade.pb
-rwxrwxrwx 1 user user   40 2010-10-02 07:32 fs.pb
-rwxrwxrwx 1 user user   46 2010-10-02 07:32 glib.pb
-rwxrwxrwx 1 user user  586 2010-10-02 07:32 gnomecompat.pb
-rwxrwxrwx 1 user user  142 2010-10-02 07:32 imgjpeg.pb
-rwxrwxrwx 1 user user   55 2010-10-02 07:32 inotify.pb
-rwxrwxrwx 1 user user   61 2010-10-02 07:32 kdecompat.pb
-rwxrwxrwx 1 user user   60 2010-10-02 07:32 mag.pb
-rwxrwxrwx 1 user user   89 2010-10-02 07:32 minimize.pb
-rwxrwxrwx 1 user user  160 2010-10-02 07:32 mousepoll.pb
-rwxrwxrwx 1 user user  314 2010-10-02 07:32 move.pb
-rwxrwxrwx 1 user user  252 2010-10-02 07:32 neg.pb
-rwxrwxrwx 1 user user   61 2010-10-02 07:32 obs.pb
-rwxrwxrwx 1 user user   61 2010-10-02 07:32 opacify.pb
-rwxrwxrwx 1 user user  636 2010-10-02 07:32 place.pb
-rwxrwxrwx 1 user user   78 2010-10-02 07:32 png.pb
-rwxrwxrwx 1 user user   43 2010-10-02 07:32 put.pb
-rwxrwxrwx 1 user user   49 2010-10-02 07:32 regex.pb
-rwxrwxrwx 1 user user  443 2010-10-02 07:32 resizeinfo.pb
-rwxrwxrwx 1 user user  673 2010-10-02 07:32 resize.pb
-rwxrwxrwx 1 user user   52 2010-10-02 07:32 ring.pb
-rwxrwxrwx 1 user user   64 2010-10-02 07:32 rotate.pb
-rw-r--r-- 1 user user  858 2010-10-02 15:28 scaleaddon.pb
-rwxrwxrwx 1 user user 1264 2010-10-02 07:32 scale.pb
-rwxrwxrwx 1 user user   78 2010-10-02 07:32 screenshot.pb
-rwxrwxrwx 1 user user  139 2010-10-02 07:32 session.pb
-rwxrwxrwx 1 user user   65 2010-10-02 07:32 shift.pb
-rwxrwxrwx 1 user user  327 2010-10-02 07:32 snap.pb
-rwxrwxrwx 1 user user 1868 2010-10-02 07:32 staticswitcher.pb
-rwxrwxrwx 1 user user   82 2010-10-02 07:32 svg.pb
-rwxrwxrwx 1 user user   58 2010-10-02 07:32 switcher.pb
-rwxrwxrwx 1 user user   88 2010-10-02 07:32 text.pb
-rwxrwxrwx 1 user user   78 2010-10-02 07:32 thumbnail.pb
-rwxrwxrwx 1 user user   61 2010-10-02 07:32 titleinfo.pb
-rwxrwxrwx 1 user user   56 2010-10-02 07:32 video.pb
-rwxrwxrwx 1 user user  930 2010-10-02 07:32 vpswitch.pb
-rwxrwxrwx 1 user user 2563 2010-10-02 07:32 wall.pb
-rwxrwxrwx 1 user user   62 2010-10-02 07:32 water.pb
-rwxrwxrwx 1 user user   58 2010-10-02 07:32 winrules.pb
-rwxrwxrwx 1 user user   87 2010-10-02 07:32 wobbly.pb
-rwxrwxrwx 1 user user  595 2010-10-02 07:32 workarounds.pb
-rwxrwxrwx 1 user user   46 2010-10-02 07:32 zoom.pb

./.cache/wallpaper:
total 216
drwxrwxrwx 2 user user   4096 2010-08-12 04:28 .
drwxrwxrwx 4 user user   4096 2010-10-02 15:28 ..
-rwxrwxrwx 1 user user 210036 2010-08-12 04:28 zoom_1024_768__usr_share_backgrounds_warty-final-ubuntu.png

./.compiz:
total 12
drwx------  3 user user 4096 2010-10-02 09:35 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..
drwx------  2 user user 4096 2010-10-02 15:27 session

./.compiz/session:
total 20
drwx------ 2 user user 4096 2010-10-02 15:27 .
drwx------ 3 user user 4096 2010-10-02 09:35 ..
-rw-r--r-- 1 user user  584 2010-10-02 09:35 102a193e54f83e990c128603729679462600000014100027
-rw-r--r-- 1 user user  342 2010-10-02 15:27 109208ad05a57dde1112860509953367000000014280027
-rw-r--r-- 1 user user  342 2010-10-02 12:23 10e5ebce3825cd46ad12860375212949500000016650027

./.config:
total 56
drwxrwxrwx 12 user user 4096 2010-10-02 14:49 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..
drwxrwxrwx  2 user user 4096 2010-10-02 13:23 autostart
drwx------  3 user user 4096 2010-10-02 09:34 compiz
drwx------  2 user user 4096 2010-10-02 10:21 enchant
drwxr-xr-x  3 user user 4096 2010-10-02 09:35 gnome-disk-utility
drwxr-xr-x  3 user user 4096 2010-10-02 09:34 gnome-session
drwxr-xr-x  2 user user 4096 2010-10-02 15:37 google-googletalkplugin
drwxrwxrwx  2 user user 4096 2010-10-02 15:33 gtk-2.0
drwxr-xr-x  3 user user 4096 2010-10-02 09:39 indicators
drwxr-xr-x  2 user user 4096 2010-10-02 10:23 softwarecenter
drwxrwxrwx  8 user user 4096 2010-10-02 10:22 ubuntu-tweak
-rwxrwxrwx  1 user user  632 2010-10-02 07:43 user-dirs.dirs
-rwxrwxrwx  1 user user    5 2010-10-02 07:43 user-dirs.locale

./.config/autostart:
total 12
drwxrwxrwx  2 user user 4096 2010-10-02 13:23 .
drwxrwxrwx 12 user user 4096 2010-10-02 14:49 ..
-rw-r--r--  1 user user  389 2010-10-02 13:23 bluetooth-applet.desktop

./.config/compiz:
total 12
drwx------  3 user user 4096 2010-10-02 09:34 .
drwxrwxrwx 12 user user 4096 2010-10-02 14:49 ..
drwx------  2 user user 4096 2010-10-02 09:34 compizconfig

./.config/compiz/compizconfig:
total 12
drwx------ 2 user user 4096 2010-10-02 09:34 .
drwx------ 3 user user 4096 2010-10-02 09:34 ..
-rw-r--r-- 1 user user   56 2010-10-02 09:34 config

./.config/enchant:
total 8
drwx------  2 user user 4096 2010-10-02 10:21 .
drwxrwxrwx 12 user user 4096 2010-10-02 14:49 ..
-rw-r--r--  1 user user    0 2010-10-02 10:21 en_US.dic
-rw-r--r--  1 user user    0 2010-10-02 10:21 en_US.exc

./.config/gnome-disk-utility:
total 12
drwxr-xr-x  3 user user 4096 2010-10-02 09:35 .
drwxrwxrwx 12 user user 4096 2010-10-02 14:49 ..
drwxr-xr-x  2 user user 4096 2010-10-02 09:35 ata-smart-ignore

./.config/gnome-disk-utility/ata-smart-ignore:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 09:35 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:35 ..

./.config/gnome-session:
total 12
drwxr-xr-x  3 user user 4096 2010-10-02 09:34 .
drwxrwxrwx 12 user user 4096 2010-10-02 14:49 ..
drwxr-xr-x  2 user user 4096 2010-10-02 09:34 saved-session

./.config/gnome-session/saved-session:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 09:34 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:34 ..

./.config/google-googletalkplugin:
total 12
drwxr-xr-x  2 user user 4096 2010-10-02 15:37 .
drwxrwxrwx 12 user user 4096 2010-10-02 14:49 ..
-rw-r--r--  1 user user  448 2010-10-02 15:37 gtbplugin.log

./.config/gtk-2.0:
total 12
drwxrwxrwx  2 user user 4096 2010-10-02 15:33 .
drwxrwxrwx 12 user user 4096 2010-10-02 14:49 ..
-rw-r--r--  1 user user  209 2010-10-02 15:33 gtkfilechooser.ini

./.config/indicators:
total 12
drwxr-xr-x  3 user user 4096 2010-10-02 09:39 .
drwxrwxrwx 12 user user 4096 2010-10-02 14:49 ..
drwxr-xr-x  2 user user 4096 2010-10-02 15:32 application

./.config/indicators/application:
total 16
drwxr-xr-x 2 user user 4096 2010-10-02 15:32 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:39 ..
-rw-r--r-- 1 user user  442 2010-10-02 15:32 lru-file.json
-rw-r--r-- 1 user user  442 2010-10-02 15:29 lru-file.json~

./.config/softwarecenter:
total 12
drwxr-xr-x  2 user user 4096 2010-10-02 10:23 .
drwxrwxrwx 12 user user 4096 2010-10-02 14:49 ..
-rw-r--r--  1 user user   77 2010-10-02 10:23 softwarecenter.cfg

./.config/ubuntu-tweak:
total 48
drwxrwxrwx  8 user user 4096 2010-10-02 10:22 .
drwxrwxrwx 12 user user 4096 2010-10-02 14:49 ..
drwxrwxrwx  3 user user 4096 2010-10-02 09:56 appcenter
-rwxrwxrwx  1 user user 6452 2010-10-02 13:24 appstatus.json
drwxrwxrwx  5 user user 4096 2010-10-02 10:03 desktoprecovery
drwxr-xr-x  2 user user 4096 2010-10-02 10:04 scripts
drwxr-xr-x  3 user user 4096 2010-10-02 10:22 sourcecenter
-rw-r--r--  1 user user 5671 2010-10-02 13:24 sourcestatus.json
drwxr-xr-x  2 user user 4096 2010-10-02 10:22 temp
drwxr-xr-x  2 user user 4096 2010-10-02 10:04 templates
-rwxrwxrwx  1 user user    0 2010-10-02 13:24 ubuntu-tweak.log

./.config/ubuntu-tweak/appcenter:
total 84
drwxrwxrwx 3 user user  4096 2010-10-02 09:56 .
drwxrwxrwx 8 user user  4096 2010-10-02 10:22 ..
drwxr-xr-x 3 user user  4096 2010-07-31 06:32 appcenter
-rw-r--r-- 1 user user 54753 2010-09-24 08:13 apps.json
-rw-r--r-- 1 user user  4795 2010-09-24 08:13 cates.json
-rw-r--r-- 1 user user    10 2010-10-02 09:56 synced
-rw-r--r-- 1 user user    10 2010-09-24 08:13 timestamp

./.config/ubuntu-tweak/appcenter/appcenter:
total 28
drwxr-xr-x 3 user user  4096 2010-07-31 06:32 .
drwxrwxrwx 3 user user  4096 2010-10-02 09:56 ..
drwxr-xr-x 2 user user 20480 2010-09-18 22:49 logo

./.config/ubuntu-tweak/appcenter/appcenter/logo:
total 2232
drwxr-xr-x 2 user user 20480 2010-09-18 22:49 .
drwxr-xr-x 3 user user  4096 2010-07-31 06:32 ..
-rw-r--r-- 1 user user   767 2010-07-31 06:33 7zip-icon.png
-rwxr-xr-x 1 user user  1787 2010-07-31 06:33 7zip-logo.png
-rw-r--r-- 1 user user  1099 2010-07-31 06:33 acetoneiso-icon.png
-rwxr-xr-x 1 user user  4127 2010-07-31 06:33 acetoneiso-logo.png
-rw-r--r-- 1 user user  1173 2010-07-31 06:33 acire-icon.png
-rwxr-xr-x 1 user user  2964 2010-07-31 06:33 acire-logo.png
-rw-r--r-- 1 user user   966 2010-07-31 06:33 adobe-flash-player-plugin-installer-i386-icon.png
-rwxr-xr-x 1 user user  2057 2010-07-31 06:33 adobe-flash-player-plugin-installer-i386-logo.png
-rw-r--r-- 1 user user   966 2010-07-31 06:33 adobe-flash-player-plugin-installer-x86-64-icon.png
-rwxr-xr-x 1 user user  2057 2010-07-31 06:33 adobe-flash-player-plugin-installer-x86-64-logo.png
-rw-r--r-- 1 user user   921 2010-07-31 06:33 agave-icon.png
-rw-r--r-- 1 user user  2659 2010-07-31 06:33 agave-logo.png
-rw-r--r-- 1 user user  1205 2010-07-31 06:33 alarm-clock-icon.png
-rwxr-xr-x 1 user user  3453 2010-07-31 06:33 alarm-clock-logo.png
-rw-r--r-- 1 user user   999 2010-07-31 06:33 alexandria-icon.png
-rwxr-xr-x 1 user user  7611 2010-07-31 06:33 alexandria-logo.png
-rw-r--r-- 1 user user  1027 2010-07-31 06:33 amule-icon.png
-rw-r--r-- 1 user user  3967 2010-07-31 06:33 amule-logo.png
-rw-r--r-- 1 user user  1211 2010-07-31 06:33 anjuta-icon.png
-rw-r--r-- 1 user user  3606 2010-07-31 06:33 anjuta-logo.png
-rw-r--r-- 1 user user   891 2010-07-31 06:33 aquadreams-theme-icon.png
-rw-r--r-- 1 user user  3819 2010-07-31 06:33 aquadreams-theme-logo.png
-rw-r--r-- 1 user user  1119 2010-07-31 06:33 arc-colors-icon.png
-rw-r--r-- 1 user user  3114 2010-07-31 06:33 arc-colors-logo.png
-rw-r--r-- 1 user user   757 2010-07-31 06:33 audacious-icon.png
-rwxr-xr-x 1 user user  1504 2010-07-31 06:33 audacious-logo.png
-rw-r--r-- 1 user user  1158 2010-07-31 06:33 audacity-icon.png
-rwxr-xr-x 1 user user  3929 2010-07-31 06:33 audacity-logo.png
-rw-r--r-- 1 user user   533 2010-08-07 19:23 audio-recording-applet-for-the-gnome-desktop-icon.png
-rwxr-xr-x 1 user user  1421 2010-08-07 19:23 audio-recording-applet-for-the-gnome-desktop-logo.png
-rw-r--r-- 1 user user   763 2010-07-31 06:33 avant-window-navigator-icon.png
-rwxr-xr-x 1 user user  1790 2010-07-31 06:33 avant-window-navigator-logo.png
-rw-r--r-- 1 user user   741 2010-07-31 06:33 avant-windows-navigator-trunk-unstable-icon.png
-rwxr-xr-x 1 user user  1715 2010-07-31 06:33 avant-windows-navigator-trunk-unstable-logo.png
-rw-r--r-- 1 user user   991 2010-07-31 06:33 avidemux-icon.png
-rwxr-xr-x 1 user user  3798 2010-07-31 06:33 avidemux-logo.png
-rw-r--r-- 1 user user   947 2010-07-31 06:33 balanzan-theme-icon.png
-rw-r--r-- 1 user user  3898 2010-07-31 06:33 balanzan-theme-logo.png
-rw-r--r-- 1 user user   918 2010-07-31 06:33 bamboo-zen-theme-icon.png
-rw-r--r-- 1 user user  4106 2010-07-31 06:33 bamboo-zen-theme-logo.png
-rw-r--r-- 1 user user   982 2010-07-31 06:33 banshee-icon.png
-rw-r--r-- 1 user user  2791 2010-07-31 06:33 banshee-logo.png
-rw-r--r-- 1 user user  1223 2010-07-31 06:33 basenji-icon.png
-rwxr-xr-x 1 user user  5281 2010-07-31 06:33 basenji-logo.png
-rw-r--r-- 1 user user   501 2010-08-13 19:51 basmalah-plymouth-theme-icon.png
-rwxr-xr-x 1 user user  2690 2010-08-13 19:51 basmalah-plymouth-theme-logo.png
-rw-r--r-- 1 user user  1262 2010-07-31 06:33 battle-tanks-icon.png
-rwxr-xr-x 1 user user  7155 2010-07-31 06:33 battle-tanks-logo.png
-rw-r--r-- 1 user user   736 2010-07-31 06:33 bleachbit-icon.png
-rwxr-xr-x 1 user user  1724 2010-07-31 06:33 bleachbit-logo.png
-rw-r--r-- 1 user user   824 2010-08-05 07:00 blender-icon.png
-rwxr-xr-x 1 user user  2991 2010-08-05 07:00 blender-logo.png
-rw-r--r-- 1 user user  1182 2010-07-31 06:33 blob-wars-2-blob-and-conquer-icon.png
-rwxr-xr-x 1 user user  4471 2010-07-31 06:33 blob-wars-2-blob-and-conquer-logo.png
-rw-r--r-- 1 user user   977 2010-07-31 06:33 blueman-icon.png
-rw-r--r-- 1 user user  2975 2010-07-31 06:33 blueman-logo.png
-rw-r--r-- 1 user user  1213 2010-07-31 06:33 boinc-help-planetary-projects-icon.png
-rwxr-xr-x 1 user user  5436 2010-07-31 06:33 boinc-help-planetary-projects-logo.png
-rw-r--r-- 1 user user   975 2010-07-31 06:33 boswars-icon.png
-rwxr-xr-x 1 user user  4666 2010-07-31 06:33 boswars-logo.png
-rw-r--r-- 1 user user  1002 2010-07-31 06:33 breathe-icon-theme-icon.png
-rw-r--r-- 1 user user  3185 2010-07-31 06:33 breathe-icon-theme-logo.png
-rw-r--r-- 1 user user  1246 2010-07-31 06:33 byobu-icon.png
-rwxr-xr-x 1 user user  5157 2010-07-31 06:33 byobu-logo.png
-rw-r--r-- 1 user user  1134 2010-07-31 06:33 caffeine-icon.png
-rwxr-xr-x 1 user user  4429 2010-07-31 06:33 caffeine-logo.png
-rw-r--r-- 1 user user  1213 2010-07-31 06:33 cairo-dock-icon.png
-rw-r--r-- 1 user user  3669 2010-07-31 06:33 cairo-dock-logo.png
-rw-r--r-- 1 user user  1065 2010-07-31 06:33 canola-icon.png
-rwxr-xr-x 1 user user  3587 2010-07-31 06:33 canola-logo.png
-rw-r--r-- 1 user user  1140 2010-07-31 06:33 cdemu-icon.png
-rwxr-xr-x 1 user user  4564 2010-07-31 06:33 cdemu-logo.png
-rw-r--r-- 1 user user  1189 2010-07-31 06:33 cheese-icon.png
-rw-r--r-- 1 user user  3993 2010-07-31 06:33 cheese-logo.png
-rw-r--r-- 1 user user   987 2010-07-31 06:33 chmsee-icon.png
-rwxr-xr-x 1 user user  3265 2010-07-31 06:33 chmsee-logo.png
-rw-r--r-- 1 user user   893 2010-07-31 06:33 christine-icon.png
-rwxr-xr-x 1 user user  2663 2010-07-31 06:33 christine-logo.png
-rwxr-xr-x 1 user user   926 2010-07-31 06:33 chromium-browser-beta-channel-icon.png
-rwxr-xr-x 1 user user  4850 2010-07-31 06:33 chromium-browser-beta-channel-logo.png
-rw-r--r-- 1 user user  1206 2010-07-31 06:33 chromium-browser-icon.png
-rw-r--r-- 1 user user  4850 2010-07-31 06:33 chromium-browser-logo.png
-rw-r--r-- 1 user user  1009 2010-07-31 06:33 chromium-icon.png
-rwxr-xr-x 1 user user  4850 2010-07-31 06:33 chromium-logo.png
-rw-r--r-- 1 user user   940 2010-07-31 06:33 clam-antivirus-icon.png
-rwxr-xr-x 1 user user  5085 2010-07-31 06:33 clam-antivirus-logo.png
-rw-r--r-- 1 user user  1165 2010-07-31 06:33 claws-mail-icon.png
-rwxr-xr-x 1 user user  4688 2010-07-31 06:33 claws-mail-logo.png
-rw-r--r-- 1 user user   663 2010-09-10 13:27 clipgrab-icon.png
-rwxr-xr-x 1 user user  1829 2010-09-10 13:27 clipgrab-logo.png
-rw-r--r-- 1 user user  1136 2010-07-31 06:33 code-blocks-icon.png
-rw-r--r-- 1 user user  3572 2010-07-31 06:33 code-blocks-logo.png
-rw-r--r-- 1 user user  1217 2010-07-31 06:33 comix-icon.png
-rwxr-xr-x 1 user user  3990 2010-07-31 06:33 comix-logo.png
-rw-r--r-- 1 user user  1113 2010-07-31 06:33 cover-thumbnailer-icon.png
-rwxr-xr-x 1 user user  3876 2010-07-31 06:33 cover-thumbnailer-logo.png
-rwxr-xr-x 1 user user   673 2010-07-31 06:33 deadbeef-icon.png
-rwxr-xr-x 1 user user  3261 2010-07-31 06:33 deadbeef-logo.png
-rw-r--r-- 1 user user  1098 2010-07-31 06:33 deb-thumbnailer-icon.png
-rwxr-xr-x 1 user user  3404 2010-07-31 06:33 deb-thumbnailer-logo.png
-rw-r--r-- 1 user user  1132 2010-07-31 06:33 deja-dup-icon.png
-rwxr-xr-x 1 user user  4111 2010-07-31 06:33 deja-dup-logo.png
-rw-r--r-- 1 user user  1056 2010-07-31 06:33 deluge-icon.png
-rwxr-xr-x 1 user user  3432 2010-07-31 06:33 deluge-logo.png
-rw-r--r-- 1 user user  1005 2010-07-31 06:33 desmume-icon.png
-rwxr-xr-x 1 user user  2999 2010-07-31 06:33 desmume-logo.png
-rw-r--r-- 1 user user  1060 2010-07-31 06:33 devhelp-icon.png
-rw-r--r-- 1 user user  1701 2010-07-31 06:33 devhelp-logo.png
-rw-r--r-- 1 user user  1173 2010-07-31 06:33 dia-icon.png
-rw-r--r-- 1 user user  3344 2010-07-31 06:33 dia-logo.png
-rw-r--r-- 1 user user   762 2010-07-31 06:33 dockbar-icon.png
-rwxr-xr-x 1 user user  2018 2010-07-31 06:33 dockbar-logo.png
-rw-r--r-- 1 user user   762 2010-07-31 06:33 dockbarx-icon.png
-rwxr-xr-x 1 user user  2018 2010-07-31 06:33 dockbarx-logo.png
-rw-r--r-- 1 user user  1043 2010-07-31 06:33 docky-icon.png
-rw-r--r-- 1 user user  3607 2010-07-31 06:33 docky-logo.png
-rw-r--r-- 1 user user  1193 2010-07-31 06:33 dolphin-icon.png
-rwxr-xr-x 1 user user  4369 2010-07-31 06:33 dolphin-logo.png
-rw-r--r-- 1 user user  1205 2010-07-31 06:33 dropbox-icon.png
-rw-r--r-- 1 user user  3537 2010-07-31 06:33 dropbox-logo.png
-rw-r--r-- 1 user user   670 2010-07-31 06:33 easytag-icon.png
-rw-r--r-- 1 user user  2791 2010-07-31 06:33 easytag-logo.png
-rw-r--r-- 1 user user  1185 2010-07-31 06:33 eclipse-icon.png
-rw-r--r-- 1 user user  4362 2010-07-31 06:33 eclipse-logo.png
-rw-r--r-- 1 user user  1228 2010-07-31 06:33 eiskaltdc-icon.png
-rwxr-xr-x 1 user user  7252 2010-07-31 06:33 eiskaltdc-logo.png
-rw-r--r-- 1 user user   656 2010-07-31 06:33 electric-sheep-the-screensaver-icon.png
-rwxr-xr-x 1 user user  1810 2010-07-31 06:33 electric-sheep-the-screensaver-logo.png
-rw-r--r-- 1 user user  1120 2010-07-31 06:33 elementary-theme-icon.png
-rw-r--r-- 1 user user  2227 2010-07-31 06:33 elementary-theme-logo.png
-rw-r--r-- 1 user user  1117 2010-07-31 06:33 emesene-2-icon.png
-rwxr-xr-x 1 user user  4083 2010-07-31 06:33 emesene-2-logo.png
-rw-r--r-- 1 user user  1117 2010-07-31 06:33 emesene-icon.png
-rw-r--r-- 1 user user  4083 2010-07-31 06:33 emesene-logo.png
-rw-r--r-- 1 user user  1152 2010-07-31 06:33 empathy-icon.png
-rw-r--r-- 1 user user  2930 2010-07-31 06:33 empathy-logo.png
-rw-r--r-- 1 user user  1043 2010-07-31 06:33 enlightenment-icon.png
-rwxr-xr-x 1 user user  3898 2010-07-31 06:33 enlightenment-logo.png
-rw-r--r-- 1 user user  1128 2010-07-31 06:33 evolution-icon.png
-rwxr-xr-x 1 user user  4359 2010-07-31 06:33 evolution-logo.png
-rw-r--r-- 1 user user  1168 2010-07-31 06:33 exaile-icon.png
-rw-r--r-- 1 user user  3922 2010-07-31 06:33 exaile-logo.png
-rw-r--r-- 1 user user   952 2010-07-31 06:33 exotic-theme-icon.png
-rw-r--r-- 1 user user  3919 2010-07-31 06:33 exotic-theme-logo.png
-rw-r--r-- 1 user user   980 2010-07-31 06:33 extreme-tux-racer-icon.png
-rwxr-xr-x 1 user user  4384 2010-07-31 06:33 extreme-tux-racer-logo.png
-rw-r--r-- 1 user user   877 2010-09-18 22:49 fcitx-icon.png
-rwxr-xr-x 1 user user  3202 2010-09-18 22:49 fcitx-logo.png
-rw-r--r-- 1 user user  1093 2010-07-31 06:33 filezilla-icon.png
-rw-r--r-- 1 user user  1216 2010-07-31 06:33 filezilla-logo.png
-rw-r--r-- 1 user user   931 2010-07-31 06:33 firefox-icon.png
-rw-r--r-- 1 user user  5173 2010-07-31 06:33 firefox-logo.png
-rw-r--r-- 1 user user  1117 2010-07-31 06:33 flush-icon.png
-rwxr-xr-x 1 user user  4590 2010-07-31 06:33 flush-logo.png
-rw-r--r-- 1 user user   800 2010-08-08 03:26 font-manager-icon.png
-rwxr-xr-x 1 user user  2287 2010-08-08 03:26 font-manager-logo.png
-rw-r--r-- 1 user user   897 2010-07-31 06:33 freedc-icon.png
-rwxr-xr-x 1 user user  2016 2010-07-31 06:33 freedc-logo.png
-rw-r--r-- 1 user user  1167 2010-07-31 06:33 freefilesync-icon.png
-rwxr-xr-x 1 user user  4187 2010-07-31 06:33 freefilesync-logo.png
-rw-r--r-- 1 user user  1181 2010-07-31 06:33 frets-on-fire-icon.png
-rwxr-xr-x 1 user user  4307 2010-07-31 06:33 frets-on-fire-logo.png
-rw-r--r-- 1 user user  1071 2010-07-31 06:33 frozen-bubble-icon.png
-rwxr-xr-x 1 user user  3442 2010-07-31 06:33 frozen-bubble-logo.png
-rwxr-xr-x 1 user user  1016 2010-07-31 06:33 gameconqueror-icon.png
-rwxr-xr-x 1 user user  3355 2010-07-31 06:33 gameconqueror-logo.png
-rw-r--r-- 1 user user  1093 2010-07-31 06:33 gbilling-client-icon.png
-rwxr-xr-x 1 user user  3704 2010-07-31 06:33 gbilling-client-logo.png
-rw-r--r-- 1 user user  1093 2010-07-31 06:33 gbilling-server-icon.png
-rwxr-xr-x 1 user user  3704 2010-07-31 06:33 gbilling-server-logo.png
-rw-r--r-- 1 user user  1013 2010-07-31 06:33 gcstar-icon.png
-rwxr-xr-x 1 user user  3189 2010-07-31 06:33 gcstar-logo.png
-rw-r--r-- 1 user user  1192 2010-07-31 06:33 geany-icon.png
-rw-r--r-- 1 user user  4361 2010-07-31 06:33 geany-logo.png
-rw-r--r-- 1 user user   814 2010-07-31 06:33 geogebra-icon.png
-rwxr-xr-x 1 user user  2965 2010-07-31 06:33 geogebra-logo.png
-rw-r--r-- 1 user user   913 2010-07-31 06:33 getting-things-gnome-icon.png
-rwxr-xr-x 1 user user  2141 2010-07-31 06:33 getting-things-gnome-logo.png
-rw-r--r-- 1 user user  1040 2010-07-31 06:33 ghex-icon.png
-rwxr-xr-x 1 user user  2956 2010-07-31 06:33 ghex-logo.png
-rw-r--r-- 1 user user   875 2010-07-31 06:33 gimp-icon.png
-rw-r--r-- 1 user user  2885 2010-07-31 06:33 gimp-logo.png
-rw-r--r-- 1 user user   866 2010-07-31 06:33 giver-icon.png
-rwxr-xr-x 1 user user  2166 2010-07-31 06:33 giver-logo.png
-rw-r--r-- 1 user user  1179 2010-07-31 06:33 gkamus-icon.png
-rwxr-xr-x 1 user user  3916 2010-07-31 06:33 gkamus-logo.png
-rw-r--r-- 1 user user  1249 2010-07-31 06:33 glest-icon.png
-rwxr-xr-x 1 user user  6438 2010-07-31 06:33 glest-logo.png
-rw-r--r-- 1 user user   956 2010-07-31 06:33 glippy-icon.png
-rwxr-xr-x 1 user user  2365 2010-07-31 06:33 glippy-logo.png
-rw-r--r-- 1 user user  1248 2010-07-31 06:33 globulation-2-icon.png
-rwxr-xr-x 1 user user  4804 2010-07-31 06:33 globulation-2-logo.png
-rw-r--r-- 1 user user  1214 2010-07-31 06:33 gloobus-preview-icon.png
-rw-r--r-- 1 user user  3459 2010-07-31 06:33 gloobus-preview-logo.png
-rw-r--r-- 1 user user  1100 2010-07-31 06:33 gmailwatcher-extra-themes-icon.png
-rwxr-xr-x 1 user user  6881 2010-07-31 06:33 gmailwatcher-extra-themes-logo.png
-rw-r--r-- 1 user user  1100 2010-07-31 06:33 gmailwatcher-icon.png
-rwxr-xr-x 1 user user  6881 2010-07-31 06:33 gmailwatcher-logo.png
-rw-r--r-- 1 user user  1075 2010-07-31 06:33 gmchess-icon.png
-rw-r--r-- 1 user user  3017 2010-07-31 06:33 gmchess-logo.png
-rw-r--r-- 1 user user  1199 2010-07-31 06:33 gmountiso-icon.png
-rwxr-xr-x 1 user user  3941 2010-07-31 06:33 gmountiso-logo.png
-rw-r--r-- 1 user user  1144 2010-07-31 06:33 gmpc-icon.png
-rw-r--r-- 1 user user  4394 2010-07-31 06:33 gmpc-logo.png
-rw-r--r-- 1 user user   977 2010-07-31 06:33 gnash-icon.png
-rwxr-xr-x 1 user user  4379 2010-07-31 06:33 gnash-logo.png
-rw-r--r-- 1 user user  1089 2010-07-31 06:33 gnome-activity-journal-icon.png
-rwxr-xr-x 1 user user  3249 2010-07-31 06:33 gnome-activity-journal-logo.png
-rw-r--r-- 1 user user  1119 2010-07-31 06:33 gnome-colors-icon.png
-rw-r--r-- 1 user user  3114 2010-07-31 06:33 gnome-colors-logo.png
-rw-r--r-- 1 user user  1138 2010-07-31 06:33 gnome-do-icon.png
-rw-r--r-- 1 user user  3952 2010-07-31 06:33 gnome-do-logo.png
-rw-r--r-- 1 user user  1076 2010-07-31 06:33 gnome-globamenu-icon.png
-rwxr-xr-x 1 user user  3948 2010-07-31 06:33 gnome-globamenu-logo.png
-rw-r--r-- 1 user user  1093 2010-07-31 06:33 gnome-mplayer-icon.png
-rw-r--r-- 1 user user  2673 2010-07-31 06:33 gnome-mplayer-logo.png
-rw-r--r-- 1 user user  1141 2010-07-31 06:33 gnome-shell-icon.png
-rwxr-xr-x 1 user user  4480 2010-07-31 06:33 gnome-shell-logo.png
-rw-r--r-- 1 user user   994 2010-07-31 06:33 gnote-icon.png
-rw-r--r-- 1 user user  3209 2010-07-31 06:33 gnote-logo.png
-rw-r--r-- 1 user user   789 2010-09-15 03:27 gofris-icon.png
-rwxr-xr-x 1 user user  3083 2010-09-15 03:27 gofris-logo.png
-rw-r--r-- 1 user user  1238 2010-07-31 06:33 google-chrome-beta-icon.png
-rw-r--r-- 1 user user  4746 2010-07-31 06:33 google-chrome-beta-logo.png
-rw-r--r-- 1 user user  1238 2010-07-31 06:33 google-chrome-stable-icon.png
-rwxr-xr-x 1 user user  4746 2010-07-31 06:33 google-chrome-stable-logo.png
-rw-r--r-- 1 user user  1238 2010-07-31 06:33 google-chrome-unstable-icon.png
-rw-r--r-- 1 user user  4746 2010-07-31 06:33 google-chrome-unstable-logo.png
-rw-r--r-- 1 user user  1217 2010-07-31 06:33 google-earth-icon.png
-rwxr-xr-x 1 user user  3733 2010-07-31 06:33 google-earth-logo.png
-rw-r--r-- 1 user user  1240 2010-07-31 06:33 google-gadgets-icon.png
-rwxr-xr-x 1 user user  3788 2010-07-31 06:33 google-gadgets-logo.png
-rw-r--r-- 1 user user  1031 2010-07-31 06:33 gparted-icon.png
-rwxr-xr-x 1 user user  2805 2010-07-31 06:33 gparted-logo.png
-rw-r--r-- 1 user user  1036 2010-07-31 06:33 gpicview-icon.png
-rwxr-xr-x 1 user user  2924 2010-07-31 06:33 gpicview-logo.png
-rw-r--r-- 1 user user  1220 2010-07-31 06:33 gpodder-icon.png
-rwxr-xr-x 1 user user  4990 2010-07-31 06:33 gpodder-logo.png
-rw-r--r-- 1 user user   971 2010-07-31 06:33 granola-icon.png
-rwxr-xr-x 1 user user  4511 2010-07-31 06:33 granola-logo.png
-rw-r--r-- 1 user user  1137 2010-07-31 06:33 gufw-icon.png
-rwxr-xr-x 1 user user  3291 2010-07-31 06:33 gufw-logo.png
-rw-r--r-- 1 user user  1079 2010-07-31 06:33 gwibber-icon.png
-rwxr-xr-x 1 user user  3715 2010-07-31 06:33 gwibber-logo.png
-rw-r--r-- 1 user user  1217 2010-07-31 06:33 handbrake-icon.png
-rwxr-xr-x 1 user user  7764 2010-07-31 06:33 handbrake-logo.png
-rw-r--r-- 1 user user  1230 2010-07-31 06:33 hedgewars-icon.png
-rwxr-xr-x 1 user user  4846 2010-07-31 06:33 hedgewars-logo.png
-rw-r--r-- 1 user user  1212 2010-07-31 06:33 homebank-icon.png
-rwxr-xr-x 1 user user  3727 2010-07-31 06:33 homebank-logo.png
-rw-r--r-- 1 user user   896 2010-07-31 06:33 hugin-icon.png
-rwxr-xr-x 1 user user  2726 2010-07-31 06:33 hugin-logo.png
-rw-r--r-- 1 user user  1231 2010-07-31 06:33 icecat-icon.png
-rwxr-xr-x 1 user user  5396 2010-07-31 06:33 icecat-logo.png
-rw-r--r-- 1 user user   854 2010-07-31 06:33 infinity-theme-icon.png
-rw-r--r-- 1 user user  3774 2010-07-31 06:33 infinity-theme-logo.png
-rw-r--r-- 1 user user  1081 2010-07-31 06:33 inkscape-icon.png
-rw-r--r-- 1 user user  2849 2010-07-31 06:33 inkscape-logo.png
-rw-r--r-- 1 user user  1214 2010-07-31 06:33 k3b-icon.png
-rwxr-xr-x 1 user user  5040 2010-07-31 06:33 k3b-logo.png
-rw-r--r-- 1 user user   965 2010-07-31 06:33 kdenlive-icon.png
-rw-r--r-- 1 user user  3246 2010-07-31 06:33 kdenlive-logo.png
-rw-r--r-- 1 user user  1223 2010-07-31 06:33 keepassx-icon.png
-rw-r--r-- 1 user user  5587 2010-07-31 06:33 keepassx-logo.png
-rw-r--r-- 1 user user  1065 2010-07-31 06:33 kupfer-icon.png
-rwxr-xr-x 1 user user  2464 2010-07-31 06:33 kupfer-logo.png
-rw-r--r-- 1 user user  1122 2010-07-31 06:33 leafpad-icon.png
-rwxr-xr-x 1 user user  3685 2010-07-31 06:33 leafpad-logo.png
-rw-r--r-- 1 user user   960 2010-07-31 06:33 liferea-icon.png
-rwxr-xr-x 1 user user  3367 2010-07-31 06:33 liferea-logo.png
-rw-r--r-- 1 user user   955 2010-07-31 06:33 linuxdc-icon.png
-rwxr-xr-x 1 user user  4153 2010-07-31 06:33 linuxdc-logo.png
-rw-r--r-- 1 user user  1029 2010-07-31 06:33 lives-video-editing-system-icon.png
-rwxr-xr-x 1 user user  4454 2010-07-31 06:33 lives-video-editing-system-logo.png
-rw-r--r-- 1 user user  1231 2010-07-31 06:33 mangler-icon.png
-rwxr-xr-x 1 user user  4087 2010-07-31 06:33 mangler-logo.png
-rw-r--r-- 1 user user  1188 2010-07-31 06:33 midnight-commander-icon.png
-rwxr-xr-x 1 user user  4478 2010-07-31 06:33 midnight-commander-logo.png
-rw-r--r-- 1 user user  1144 2010-07-31 06:33 midori-icon.png
-rw-r--r-- 1 user user  3802 2010-07-31 06:33 midori-logo.png
-rw-r--r-- 1 user user   946 2010-07-31 06:33 minitube-icon.png
-rwxr-xr-x 1 user user  1831 2010-07-31 06:33 minitube-logo.png
-rw-r--r-- 1 user user  1095 2010-07-31 06:33 miro-icon.png
-rw-r--r-- 1 user user  3394 2010-07-31 06:33 miro-logo.png
-rw-r--r-- 1 user user   853 2010-08-09 03:54 mplayer-icon.png
-rwxr-xr-x 1 user user  3916 2010-08-09 03:54 mplayer-logo.png
-rw-r--r-- 1 user user  1126 2010-07-31 06:33 mumble-icon.png
-rwxr-xr-x 1 user user  4171 2010-07-31 06:33 mumble-logo.png
-rw-r--r-- 1 user user  1128 2010-07-31 06:33 mupen64-plus-icon.png
-rw-r--r-- 1 user user  1141 2010-07-31 06:33 mupen64plus-icon.png
-rwxr-xr-x 1 user user  4552 2010-07-31 06:33 mupen64-plus-logo.png
-rwxr-xr-x 1 user user  4703 2010-07-31 06:33 mupen64plus-logo.png
-rw-r--r-- 1 user user  1083 2010-07-31 06:33 music-player-daemon-icon.png
-rwxr-xr-x 1 user user  3145 2010-07-31 06:33 music-player-daemon-logo.png
-rw-r--r-- 1 user user  1129 2010-07-31 06:33 netbeans-icon.png
-rwxr-xr-x 1 user user  3874 2010-07-31 06:33 netbeans-logo.png
-rw-r--r-- 1 user user   703 2010-07-31 06:33 neverball-icon.png
-rwxr-xr-x 1 user user  2152 2010-07-31 06:33 neverball-logo.png
-rw-r--r-- 1 user user  1221 2010-07-31 06:33 nexuiz-icon.png
-rwxr-xr-x 1 user user  5337 2010-07-31 06:33 nexuiz-logo.png
-rw-r--r-- 1 user user  1030 2010-07-31 06:33 njam-pacman-icon.png
-rwxr-xr-x 1 user user  3362 2010-07-31 06:33 njam-pacman-logo.png
-rw-r--r-- 1 user user  1263 2010-07-31 06:33 ogmrip-icon.png
-rwxr-xr-x 1 user user  6060 2010-07-31 06:33 ogmrip-logo.png
-rw-r--r-- 1 user user  1239 2010-07-31 06:33 openshot-icon.png
-rw-r--r-- 1 user user  4078 2010-07-31 06:33 openshot-logo.png
-rw-r--r-- 1 user user  1182 2010-07-31 06:33 opera-icon.png
-rw-r--r-- 1 user user  3355 2010-07-31 06:33 opera-logo.png
-rw-r--r-- 1 user user  1247 2010-07-31 06:33 osd-lyrics-icon.png
-rwxr-xr-x 1 user user  5579 2010-07-31 06:33 osd-lyrics-logo.png
-rw-r--r-- 1 user user  1255 2010-07-31 06:33 pcsx-reloaded-icon.png
-rwxr-xr-x 1 user user  5813 2010-07-31 06:33 pcsx-reloaded-logo.png
-rw-r--r-- 1 user user  1073 2010-07-31 06:33 pdfmod-icon.png
-rwxr-xr-x 1 user user  3437 2010-07-31 06:33 pdfmod-logo.png
-rw-r--r-- 1 user user  1059 2010-08-07 19:26 pdf-shuffler-icon.png
-rwxr-xr-x 1 user user  4335 2010-08-07 19:26 pdf-shuffler-logo.png
-rw-r--r-- 1 user user  1183 2010-07-31 06:33 performous-icon.png
-rwxr-xr-x 1 user user  4535 2010-07-31 06:33 performous-logo.png
-rw-r--r-- 1 user user   930 2010-07-31 06:33 phatch-icon.png
-rwxr-xr-x 1 user user  4297 2010-07-31 06:33 phatch-logo.png
-rw-r--r-- 1 user user  1171 2010-07-31 06:33 pidgin-icon.png
-rw-r--r-- 1 user user  3564 2010-07-31 06:33 pidgin-logo.png
-rw-r--r-- 1 user user   988 2010-07-31 06:33 pino-icon.png
-rwxr-xr-x 1 user user  2663 2010-07-31 06:33 pino-logo.png
-rw-r--r-- 1 user user   926 2010-07-31 06:33 pinta-icon.png
-rwxr-xr-x 1 user user  4235 2010-07-31 06:33 pinta-logo.png
-rw-r--r-- 1 user user  1136 2010-07-31 06:33 pitivi-icon.png
-rwxr-xr-x 1 user user  3685 2010-07-31 06:33 pitivi-logo.png
-rw-r--r-- 1 user user  1187 2010-07-31 06:33 playonlinux-icon.png
-rwxr-xr-x 1 user user  3481 2010-07-31 06:33 playonlinux-logo.png
-rw-r--r-- 1 user user  1108 2010-07-31 06:33 postr-icon.png
-rwxr-xr-x 1 user user  3842 2010-07-31 06:33 postr-logo.png
-rw-r--r-- 1 user user  1158 2010-07-31 06:33 qbittorrent-icon.png
-rwxr-xr-x 1 user user  4784 2010-07-31 06:33 qbittorrent-logo.png
-rw-r--r-- 1 user user  1174 2010-07-31 06:33 qmmp-icon.png
-rwxr-xr-x 1 user user  4587 2010-07-31 06:33 qmmp-logo.png
-rwxr-xr-x 1 user user   851 2010-07-31 06:33 quantum-gis-icon.png
-rwxr-xr-x 1 user user  3686 2010-07-31 06:33 quantum-gis-logo.png
-rw-r--r-- 1 user user   701 2010-07-31 06:33 quod-libet-icon.png
-rwxr-xr-x 1 user user  2961 2010-07-31 06:33 quod-libet-logo.png
-rw-r--r-- 1 user user  1154 2010-07-31 06:33 qutim-icon.png
-rwxr-xr-x 1 user user  6327 2010-07-31 06:33 qutim-logo.png
-rw-r--r-- 1 user user  1052 2010-07-31 06:33 rabbitvcs-icon.png
-rwxr-xr-x 1 user user  3027 2010-07-31 06:33 rabbitvcs-logo.png
-rw-r--r-- 1 user user  1099 2010-07-31 06:33 rapid-photo-downloader-icon.png
-rwxr-xr-x 1 user user  2602 2010-07-31 06:33 rapid-photo-downloader-logo.png
-rw-r--r-- 1 user user  1186 2010-07-31 06:33 rawtherapee-icon.png
-rwxr-xr-x 1 user user  3681 2010-07-31 06:33 rawtherapee-logo.png
-rw-r--r-- 1 user user  1108 2010-07-31 06:33 remmina-icon.png
-rwxr-xr-x 1 user user  3324 2010-07-31 06:33 remmina-logo.png
-rw-r--r-- 1 user user  1100 2010-07-31 06:33 renamethemall-icon.png
-rwxr-xr-x 1 user user  3852 2010-07-31 06:33 renamethemall-logo.png
-rw-r--r-- 1 user user   993 2010-08-07 00:50 retroshare-icon.png
-rwxr-xr-x 1 user user  5362 2010-08-07 00:50 retroshare-logo.png
-rw-r--r-- 1 user user  1194 2010-07-31 06:33 rssowl-icon.png
-rwxr-xr-x 1 user user  6662 2010-07-31 06:33 rssowl-logo.png
-rw-r--r-- 1 user user  1171 2010-07-31 06:33 samsung-tools-icon.png
-rwxr-xr-x 1 user user  7223 2010-07-31 06:33 samsung-tools-logo.png
-rw-r--r-- 1 user user  1175 2010-07-31 06:33 screenlets-icon.png
-rwxr-xr-x 1 user user  3046 2010-07-31 06:33 screenlets-logo.png
-rw-r--r-- 1 user user   906 2010-09-15 14:53 scribus-development-branch-icon.png
-rwxr-xr-x 1 user user  3682 2010-09-15 14:53 scribus-development-branch-logo.png
-rw-r--r-- 1 user user  1216 2010-07-31 06:33 scribus-icon.png
-rwxr-xr-x 1 user user  3682 2010-07-31 06:33 scribus-logo.png
-rw-r--r-- 1 user user  1215 2010-07-31 06:33 secret-maryo-chronicles-icon.png
-rwxr-xr-x 1 user user  5880 2010-07-31 06:33 secret-maryo-chronicles-logo.png
-rw-r--r-- 1 user user   992 2010-07-31 06:33 sensors-applet-icon.png
-rwxr-xr-x 1 user user  4387 2010-07-31 06:33 sensors-applet-logo.png
-rw-r--r-- 1 user user  1119 2010-07-31 06:33 shiki-colors-icon.png
-rwxr-xr-x 1 user user  3114 2010-07-31 06:33 shiki-colors-logo.png
-rw-r--r-- 1 user user  1117 2010-07-31 06:33 shotwell-icon.png
-rwxr-xr-x 1 user user  4344 2010-07-31 06:33 shotwell-logo.png
-rw-r--r-- 1 user user   885 2010-07-31 06:33 showtime-theme-icon.png
-rw-r--r-- 1 user user  3818 2010-07-31 06:33 showtime-theme-logo.png
-rw-r--r-- 1 user user  1225 2010-07-31 06:33 shutter-icon.png
-rw-r--r-- 1 user user  4687 2010-07-31 06:33 shutter-logo.png
-rw-r--r-- 1 user user  1248 2010-07-31 06:33 skype-icon.png
-rw-r--r-- 1 user user  3101 2010-07-31 06:33 skype-logo.png
-rw-r--r-- 1 user user  1153 2010-07-31 06:33 smplayer-icon.png
-rwxr-xr-x 1 user user  4847 2010-07-31 06:33 smplayer-logo.png
-rw-r--r-- 1 user user  1205 2010-07-31 06:33 solang-icon.png
-rwxr-xr-x 1 user user  3532 2010-07-31 06:33 solang-logo.png
-rw-r--r-- 1 user user  1030 2010-07-31 06:33 sopcast-player-icon.png
-rwxr-xr-x 1 user user  2555 2010-07-31 06:33 sopcast-player-logo.png
-rw-r--r-- 1 user user   934 2010-07-31 06:33 step-into-freedom-theme-icon.png
-rw-r--r-- 1 user user  3686 2010-07-31 06:33 step-into-freedom-theme-logo.png
-rw-r--r-- 1 user user   886 2010-07-31 06:33 subsonic-icon.png
-rwxr-xr-x 1 user user  2126 2010-07-31 06:33 subsonic-logo.png
-rw-r--r-- 1 user user  1060 2010-07-31 06:33 subtitle-editor-icon.png
-rwxr-xr-x 1 user user  3142 2010-07-31 06:33 subtitle-editor-logo.png
-rw-r--r-- 1 user user  1129 2010-07-31 06:33 supertux-icon.png
-rwxr-xr-x 1 user user  4680 2010-07-31 06:33 supertux-logo.png
-rw-r--r-- 1 user user  1139 2010-07-31 06:33 synapse-icon.png
-rwxr-xr-x 1 user user  3781 2010-07-31 06:33 synapse-logo.png
-rw-r--r-- 1 user user  1057 2010-08-11 12:42 teamviewer-icon.png
-rwxr-xr-x 1 user user  2008 2010-08-11 12:42 teamviewer-logo.png
-rw-r--r-- 1 user user  1111 2010-07-31 06:33 terminator-icon.png
-rwxr-xr-x 1 user user  2595 2010-07-31 06:33 terminator-logo.png
-rw-r--r-- 1 user user  1168 2010-07-31 06:33 test-drive-icon.png
-rwxr-xr-x 1 user user  5022 2010-07-31 06:33 test-drive-logo.png
-rw-r--r-- 1 user user  1183 2010-07-31 06:33 the-battle-for-wesnoth-icon.png
-rwxr-xr-x 1 user user  5052 2010-07-31 06:33 the-battle-for-wesnoth-logo.png
-rw-r--r-- 1 user user  1211 2010-07-31 06:33 the-mana-world-icon.png
-rwxr-xr-x 1 user user  5645 2010-07-31 06:33 the-mana-world-logo.png
-rw-r--r-- 1 user user  1231 2010-07-31 06:33 thunderbird-icon.png
-rwxr-xr-x 1 user user  5741 2010-07-31 06:33 thunderbird-logo.png
-rw-r--r-- 1 user user  1070 2010-07-31 06:33 tomboy-icon.png
-rwxr-xr-x 1 user user  2644 2010-07-31 06:33 tomboy-logo.png
-rw-r--r-- 1 user user   872 2010-07-31 06:33 torus-trooper-icon.png
-rwxr-xr-x 1 user user  1949 2010-07-31 06:33 torus-trooper-logo.png
-rw-r--r-- 1 user user  1136 2010-07-31 06:33 tracker-icon.png
-rwxr-xr-x 1 user user  4145 2010-07-31 06:33 tracker-logo.png
-rw-r--r-- 1 user user  1070 2010-07-31 06:33 transmission-icon.png
-rwxr-xr-x 1 user user  2752 2010-07-31 06:33 transmission-logo.png
-rw-r--r-- 1 user user   944 2010-07-31 06:33 tropical-theme-icon.png
-rw-r--r-- 1 user user  4113 2010-07-31 06:33 tropical-theme-logo.png
-rw-r--r-- 1 user user  1000 2010-07-31 06:33 ubuntu-community-themes-icon.png
-rwxr-xr-x 1 user user  3849 2010-07-31 06:33 ubuntu-community-themes-logo.png
-rw-r--r-- 1 user user   855 2010-08-09 08:45 ubuntu-light-themes-icon.png
-rwxr-xr-x 1 user user  3849 2010-08-09 08:45 ubuntu-light-themes-logo.png
-rw-r--r-- 1 user user  1121 2010-07-31 06:33 ubuntu-restricted-extras-icon.png
-rwxr-xr-x 1 user user  4376 2010-07-31 06:33 ubuntu-restricted-extras-logo.png
-rw-r--r-- 1 user user   959 2010-07-31 06:33 ubuntu-sunrise-theme-icon.png
-rw-r--r-- 1 user user  4125 2010-07-31 06:33 ubuntu-sunrise-theme-logo.png
-rw-r--r-- 1 user user  1210 2010-07-31 06:33 ubuntu-tweak-icon.png
-rw-r--r-- 1 user user  4646 2010-07-31 06:33 ubuntu-tweak-logo.png
-rw-r--r-- 1 user user  1085 2010-07-31 06:33 vegastrike-icon.png
-rwxr-xr-x 1 user user  4501 2010-07-31 06:33 vegastrike-logo.png
-rw-r--r-- 1 user user  1135 2010-07-31 06:33 viewnior-icon.png
-rwxr-xr-x 1 user user  2818 2010-07-31 06:33 viewnior-logo.png
-rw-r--r-- 1 user user  1178 2010-07-31 06:33 virtualbox-icon.png
-rwxr-xr-x 1 user user  4590 2010-07-31 06:33 virtualbox-logo.png
-rw-r--r-- 1 user user  1118 2010-07-31 06:33 visual-boy-advance-icon.png
-rwxr-xr-x 1 user user  4517 2010-07-31 06:33 visual-boy-advance-logo.png
-rw-r--r-- 1 user user  1036 2010-07-31 06:33 vlc-media-player-icon.png
-rwxr-xr-x 1 user user  3167 2010-07-31 06:33 vlc-media-player-logo.png
-rw-r--r-- 1 user user  1066 2010-07-31 06:33 wakoopa-icon.png
-rwxr-xr-x 1 user user  2928 2010-07-31 06:33 wakoopa-logo.png
-rw-r--r-- 1 user user   899 2010-08-12 11:28 wally-icon.png
-rwxr-xr-x 1 user user  6722 2010-08-12 11:28 wally-logo.png
-rw-r--r-- 1 user user  1199 2010-07-31 06:33 warsow-icon.png
-rwxr-xr-x 1 user user  4193 2010-07-31 06:33 warsow-logo.png
-rw-r--r-- 1 user user  1195 2010-07-31 06:33 warzone-2100-icon.png
-rwxr-xr-x 1 user user  7090 2010-07-31 06:33 warzone-2100-logo.png
-rw-r--r-- 1 user user   941 2010-07-31 06:33 wild-shine-theme-icon.png
-rw-r--r-- 1 user user  4238 2010-07-31 06:33 wild-shine-theme-logo.png
-rw-r--r-- 1 user user   900 2010-07-31 06:33 wine-icon.png
-rw-r--r-- 1 user user  2594 2010-07-31 06:33 wine-logo.png
-rw-r--r-- 1 user user  1083 2010-07-31 06:33 wormux-icon.png
-rwxr-xr-x 1 user user  3260 2010-07-31 06:33 wormux-logo.png
-rw-r--r-- 1 user user   933 2010-09-16 02:14 wxformbuilder-icon.png
-rwxr-xr-x 1 user user  4105 2010-09-16 02:14 wxformbuilder-logo.png
-rw-r--r-- 1 user user   916 2010-07-31 06:33 xbmc-media-center-icon.png
-rwxr-xr-x 1 user user  2814 2010-07-31 06:33 xbmc-media-center-logo.png
-rw-r--r-- 1 user user  1126 2010-07-31 06:33 xqf-game-server-browser-icon.png
-rwxr-xr-x 1 user user  1182 2010-07-31 06:33 xqf-game-server-browser-logo.png
-rw-r--r-- 1 user user  1072 2010-07-31 06:33 xsplash-background-settings-icon.png
-rwxr-xr-x 1 user user  2484 2010-07-31 06:33 xsplash-background-settings-logo.png
-rw-r--r-- 1 user user  1083 2010-07-31 06:33 zik-icon.png
-rwxr-xr-x 1 user user  2762 2010-07-31 06:33 zik-logo.png
-rw-r--r-- 1 user user  1197 2010-07-31 06:33 zim-icon.png
-rwxr-xr-x 1 user user  3107 2010-07-31 06:33 zim-logo.png
-rw-r--r-- 1 user user  1232 2010-07-31 06:33 zsnes-icon.png
-rwxr-xr-x 1 user user  6319 2010-07-31 06:33 zsnes-logo.png

./.config/ubuntu-tweak/desktoprecovery:
total 20
drwxrwxrwx 5 user user 4096 2010-10-02 10:03 .
drwxrwxrwx 8 user user 4096 2010-10-02 10:22 ..
drwxr-xr-x 2 user user 4096 2010-10-02 10:03 apps
drwxrwxrwx 4 user user 4096 2010-10-02 10:03 desktop
drwxr-xr-x 3 user user 4096 2010-10-02 10:03 system

./.config/ubuntu-tweak/desktoprecovery/apps:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 10:03 .
drwxrwxrwx 5 user user 4096 2010-10-02 10:03 ..

./.config/ubuntu-tweak/desktoprecovery/desktop:
total 16
drwxrwxrwx 4 user user 4096 2010-10-02 10:03 .
drwxrwxrwx 5 user user 4096 2010-10-02 10:03 ..
drwxr-xr-x 2 user user 4096 2010-10-02 10:03 gnome
drwxr-xr-x 2 user user 4096 2010-10-02 10:03 ibus

./.config/ubuntu-tweak/desktoprecovery/desktop/gnome:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 10:03 .
drwxrwxrwx 4 user user 4096 2010-10-02 10:03 ..

./.config/ubuntu-tweak/desktoprecovery/desktop/ibus:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 10:03 .
drwxrwxrwx 4 user user 4096 2010-10-02 10:03 ..

./.config/ubuntu-tweak/desktoprecovery/system:
total 12
drwxr-xr-x 3 user user 4096 2010-10-02 10:03 .
drwxrwxrwx 5 user user 4096 2010-10-02 10:03 ..
drwxr-xr-x 2 user user 4096 2010-10-02 10:03 dns_sd

./.config/ubuntu-tweak/desktoprecovery/system/dns_sd:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 10:03 .
drwxr-xr-x 3 user user 4096 2010-10-02 10:03 ..

./.config/ubuntu-tweak/scripts:
total 112
drwxr-xr-x 2 user user 4096 2010-10-02 10:04 .
drwxrwxrwx 8 user user 4096 2010-10-02 10:22 ..
-rwxr-xr-x 1 user user   94 2010-10-02 10:04 Browse as root
-rwxr-xr-x 1 user user  715 2010-10-02 10:04 Check md5 sum
-rwxr-xr-x 1 user user 6103 2010-10-02 10:04 Compress PDF
-rwxr-xr-x 1 user user  241 2010-10-02 10:04 Convert image to GIF
-rwxr-xr-x 1 user user  240 2010-10-02 10:04 Convert image to JPG
-rwxr-xr-x 1 user user  241 2010-10-02 10:04 Convert image to PNG
-rwxr-xr-x 1 user user   87 2010-10-02 10:04 Copy to ...
-rwxr-xr-x 1 user user  110 2010-10-02 10:04 Copy to Desktop
-rwxr-xr-x 1 user user  111 2010-10-02 10:04 Copy to Download
-rwxr-xr-x 1 user user   99 2010-10-02 10:04 Copy to Home
-rwxr-xr-x 1 user user   91 2010-10-02 10:04 Create hardlink to ...
-rwxr-xr-x 1 user user   77 2010-10-02 10:04 Create Launcher ...
-rwxr-xr-x 1 user user   87 2010-10-02 10:04 Link to ...
-rwxr-xr-x 1 user user  110 2010-10-02 10:04 Link to Desktop
-rwxr-xr-x 1 user user  111 2010-10-02 10:04 Link to Download
-rwxr-xr-x 1 user user   99 2010-10-02 10:04 Link to Home
-rwxr-xr-x 1 user user  972 2010-10-02 10:04 Make hard shadow to image
-rwxr-xr-x 1 user user   87 2010-10-02 10:04 Move to ...
-rwxr-xr-x 1 user user  110 2010-10-02 10:04 Move to Desktop
-rwxr-xr-x 1 user user  111 2010-10-02 10:04 Move to Download
-rwxr-xr-x 1 user user   99 2010-10-02 10:04 Move to Home
-rwxr-xr-x 1 user user  261 2010-10-02 10:04 Open with your favourite text editor
-rwxr-xr-x 1 user user  271 2010-10-02 10:04 Open with your favourite text editor (as root)
-rwxr-xr-x 1 user user   31 2010-10-02 10:04 Search in current folder
-rwxr-xr-x 1 user user 2203 2010-10-02 10:04 Set image as wallpaper

./.config/ubuntu-tweak/sourcecenter:
total 184
drwxr-xr-x 3 user user   4096 2010-10-02 10:22 .
drwxrwxrwx 8 user user   4096 2010-10-02 10:22 ..
-rw-r--r-- 1 user user   4430 2010-09-24 08:13 cates.json
-rw-r--r-- 1 user user   1671 2010-09-24 08:13 distros.json
drwxr-xr-x 3 user user   4096 2010-07-31 06:33 sourcecenter
-rw-r--r-- 1 user user 152190 2010-09-24 08:13 sources.json
-rw-r--r-- 1 user user     10 2010-10-02 10:22 synced
-rw-r--r-- 1 user user     10 2010-09-24 08:13 timestamp

./.config/ubuntu-tweak/sourcecenter/sourcecenter:
total 28
drwxr-xr-x 3 user user  4096 2010-07-31 06:33 .
drwxr-xr-x 3 user user  4096 2010-10-02 10:22 ..
drwxr-xr-x 2 user user 20480 2010-09-18 21:55 logo

./.config/ubuntu-tweak/sourcecenter/sourcecenter/logo:
total 1376
drwxr-xr-x 2 user user 20480 2010-09-18 21:55 .
drwxr-xr-x 3 user user  4096 2010-07-31 06:33 ..
-rw-r--r-- 1 user user  1173 2010-07-31 06:33 acire-team-acire-releases-icon.png
-rwxr-xr-x 1 user user  2964 2010-07-31 06:33 acire-team-acire-releases-logo.png
-rw-r--r-- 1 user user  1205 2010-07-31 06:33 alarm-clock-ppa-icon.png
-rwxr-xr-x 1 user user  3453 2010-07-31 06:33 alarm-clock-ppa-logo.png
-rw-r--r-- 1 user user  1136 2010-07-31 06:33 alex-hunziker-ppa-icon.png
-rwxr-xr-x 1 user user  4145 2010-07-31 06:33 alex-hunziker-ppa-logo.png
-rw-r--r-- 1 user user  1027 2010-07-31 06:33 amule-releases-ppa-icon.png
-rwxr-xr-x 1 user user  3967 2010-07-31 06:33 amule-releases-ppa-logo.png
-rw-r--r-- 1 user user  1138 2010-07-31 06:33 anonbeat-guayadeque-icon.png
-rwxr-xr-x 1 user user  3298 2010-07-31 06:33 anonbeat-guayadeque-logo.png
-rw-r--r-- 1 user user  1057 2010-07-31 06:33 avant-window-navigator-unstable-icon.png
-rw-r--r-- 1 user user  1774 2010-07-31 06:33 avant-window-navigator-unstable-logo.png
-rw-r--r-- 1 user user  1057 2010-07-31 06:33 awn-core-ppa-icon.png
-rwxr-xr-x 1 user user  1774 2010-07-31 06:33 awn-core-ppa-logo.png
-rw-r--r-- 1 user user   628 2010-07-31 06:33 backtrack-4-repository-icon.png
-rwxr-xr-x 1 user user  1859 2010-07-31 06:33 backtrack-4-repository-logo.png
-rw-r--r-- 1 user user   982 2010-07-31 06:33 banshee-icon.png
-rw-r--r-- 1 user user  2791 2010-07-31 06:33 banshee-logo.png
-rw-r--r-- 1 user user   982 2010-07-31 06:33 banshee-team-banshee-unstable-icon.png
-rwxr-xr-x 1 user user  2791 2010-07-31 06:33 banshee-team-banshee-unstable-logo.png
-rw-r--r-- 1 user user   900 2010-07-31 06:33 bisigi-ppaicon.png
-rw-r--r-- 1 user user  2846 2010-07-31 06:33 bisigi-ppalogo.png
-rwxr-xr-x 1 user user  1095 2010-07-31 06:33 bjfs-ppa-icon.png
-rw-r--r-- 1 user user  3678 2010-07-31 06:33 bjfs-ppaicon.png
-rwxr-xr-x 1 user user  4083 2010-07-31 06:33 bjfs-ppa-logo.png
-rw-r--r-- 1 user user  8033 2010-07-31 06:33 bjfs-ppalogo.png
-rw-r--r-- 1 user user  1002 2010-07-31 06:33 breathe-dev-ppa-icon.png
-rw-r--r-- 1 user user  3185 2010-07-31 06:33 breathe-dev-ppa-logo.png
-rw-r--r-- 1 user user  1246 2010-07-31 06:33 byobu-icon.png
-rwxr-xr-x 1 user user  5157 2010-07-31 06:33 byobu-logo.png
-rw-r--r-- 1 user user  1134 2010-07-31 06:33 caffeine-developers-ppa-icon.png
-rwxr-xr-x 1 user user  4429 2010-07-31 06:33 caffeine-developers-ppa-logo.png
-rw-r--r-- 1 user user  1213 2010-07-31 06:33 cairo-dock-team-ppa-icon.png
-rw-r--r-- 1 user user  3669 2010-07-31 06:33 cairo-dock-team-ppa-logo.png
-rw-r--r-- 1 user user  1213 2010-07-31 06:33 cairo-dock-team-weekly-icon.png
-rw-r--r-- 1 user user  3669 2010-07-31 06:33 cairo-dock-team-weekly-logo.png
-rwxr-xr-x 1 user user   778 2010-07-31 06:33 canola-ppa-icon.png
-rwxr-xr-x 1 user user  3587 2010-07-31 06:33 canola-ppa-logo.png
-rw-r--r-- 1 user user  1164 2010-07-31 06:33 cdemu-ppa-icon.png
-rwxr-xr-x 1 user user  4292 2010-07-31 06:33 cdemu-ppa-logo.png
-rw-r--r-- 1 user user   987 2010-07-31 06:33 chmsee-icon.png
-rw-r--r-- 1 user user  3265 2010-07-31 06:33 chmsee-logo.png
-rw-r--r-- 1 user user  1206 2010-07-31 06:33 chromium-browser-beta-channel-icon.png
-rwxr-xr-x 1 user user  4850 2010-07-31 06:33 chromium-browser-beta-channel-logo.png
-rw-r--r-- 1 user user  1206 2010-07-31 06:33 chromium-browser-icon.png
-rw-r--r-- 1 user user  4850 2010-07-31 06:33 chromium-browser-logo.png
-rw-r--r-- 1 user user   997 2010-07-31 06:33 chromium-daily-ppaicon.png
-rw-r--r-- 1 user user  4400 2010-07-31 06:33 chromium-daily-ppalogo.png
-rw-r--r-- 1 user user  1206 2010-07-31 06:33 Chromium-icon.png
-rwxr-xr-x 1 user user  4850 2010-07-31 06:33 Chromium-logo.png
-rw-r--r-- 1 user user   940 2010-07-31 06:33 clam-antivirus-icon.png
-rwxr-xr-x 1 user user  5085 2010-07-31 06:33 clam-antivirus-logo.png
-rw-r--r-- 1 user user  1120 2010-07-31 06:33 claws-mail-ppaicon.png
-rw-r--r-- 1 user user  4688 2010-07-31 06:33 claws-mail-ppalogo.png
-rw-r--r-- 1 user user   663 2010-09-10 13:31 clipgrab-icon.png
-rwxr-xr-x 1 user user  1829 2010-09-10 13:31 clipgrab-logo.png
-rw-r--r-- 1 user user  1092 2010-07-31 06:33 compiz-ppa-icon.png
-rwxr-xr-x 1 user user  2633 2010-07-31 06:33 compiz-ppa-logo.png
-rwxr-xr-x 1 user user  1016 2010-07-31 06:33 coolwanglu-scanmem-icon.png
-rwxr-xr-x 1 user user  3355 2010-07-31 06:33 coolwanglu-scanmem-logo.png
-rw-r--r-- 1 user user  1113 2010-07-31 06:33 cover-thumbnailer-icon.png
-rwxr-xr-x 1 user user  3876 2010-07-31 06:33 cover-thumbnailer-logo.png
-rw-r--r-- 1 user user   897 2010-07-31 06:33 deadbeef-icon.png
-rwxr-xr-x 1 user user  2823 2010-07-31 06:33 deadbeef-logo.png
-rw-r--r-- 1 user user  1098 2010-07-31 06:33 deb-thumbnailer-team-ppa-icon.png
-rwxr-xr-x 1 user user  3404 2010-07-31 06:33 deb-thumbnailer-team-ppa-logo.png
-rw-r--r-- 1 user user  1068 2010-07-31 06:33 deja-dup-team-ppaicon.png
-rw-r--r-- 1 user user  4111 2010-07-31 06:33 deja-dup-team-ppalogo.png
-rw-r--r-- 1 user user  1099 2010-07-31 06:33 dlynch3-ppa-icon.png
-rwxr-xr-x 1 user user  2602 2010-07-31 06:33 dlynch3-ppa-logo.png
-rw-r--r-- 1 user user   762 2010-07-31 06:33 dockbar-main-ppa-icon.png
-rwxr-xr-x 1 user user  2018 2010-07-31 06:33 dockbar-main-ppa-logo.png
-rw-r--r-- 1 user user  1043 2010-07-31 06:33 docky-icon.png
-rw-r--r-- 1 user user  3607 2010-07-31 06:33 docky-logo.png
-rw-r--r-- 1 user user   982 2010-07-31 06:33 do-core-ppaicon.png
-rw-r--r-- 1 user user  3569 2010-07-31 06:33 do-core-ppalogo.png
-rw-r--r-- 1 user user  1205 2010-07-31 06:33 dropbox-official-source-icon.png
-rw-r--r-- 1 user user  3537 2010-07-31 06:33 dropbox-official-source-logo.png
-rw-r--r-- 1 user user  1228 2010-07-31 06:33 eiskaltdc-ppa-icon.png
-rwxr-xr-x 1 user user  7252 2010-07-31 06:33 eiskaltdc-ppa-logo.png
-rw-r--r-- 1 user user  1120 2010-07-31 06:33 elementaryart-elementarydesktop-icon.png
-rwxr-xr-x 1 user user  2227 2010-07-31 06:33 elementaryart-elementarydesktop-logo.png
-rw-r--r-- 1 user user  1120 2010-07-31 06:33 elementaryart-ppa-icon.png
-rw-r--r-- 1 user user  2227 2010-07-31 06:33 elementaryart-ppa-logo.png
-rw-r--r-- 1 user user  1043 2010-07-31 06:33 enlightenment-binary-packages-icon.png
-rwxr-xr-x 1 user user  3898 2010-07-31 06:33 enlightenment-binary-packages-logo.png
-rw-r--r-- 1 user user  1128 2010-07-31 06:33 evolution-icon.png
-rwxr-xr-x 1 user user  4359 2010-07-31 06:33 evolution-logo.png
-rw-r--r-- 1 user user  1081 2010-07-31 06:33 exaile-devel-ppaicon.png
-rw-r--r-- 1 user user  4305 2010-07-31 06:33 exaile-devel-ppalogo.png
-rw-r--r-- 1 user user  1167 2010-07-31 06:33 freefilesync-icon.png
-rwxr-xr-x 1 user user  4187 2010-07-31 06:33 freefilesync-logo.png
-rw-r--r-- 1 user user  1013 2010-07-31 06:33 gcstar-icon.png
-rwxr-xr-x 1 user user  3189 2010-07-31 06:33 gcstar-logo.png
-rwxr-xr-x 1 user user  1691 2010-07-31 06:33 gcstar-ppa-icon.png
-rwxr-xr-x 1 user user  3528 2010-07-31 06:33 gcstar-ppa-logo.png
-rw-r--r-- 1 user user  1192 2010-07-31 06:33 geany-dev-ppa-icon.png
-rw-r--r-- 1 user user  4361 2010-07-31 06:33 geany-dev-ppa-logo.png
-rw-r--r-- 1 user user   875 2010-07-31 06:33 gimp-testing-icon.png
-rw-r--r-- 1 user user  1076 2010-07-31 06:33 globalmenu-team-ppa-icon.png
-rwxr-xr-x 1 user user  3948 2010-07-31 06:33 globalmenu-team-ppa-logo.png
-rw-r--r-- 1 user user  1214 2010-07-31 06:33 gloobus-dev-gloobus-preview-icon.png
-rw-r--r-- 1 user user  3459 2010-07-31 06:33 gloobus-dev-gloobus-preview-logo.png
-rw-r--r-- 1 user user  1075 2010-07-31 06:33 gmchess-icon.png
-rw-r--r-- 1 user user  3017 2010-07-31 06:33 gmchess-logo.png
-rw-r--r-- 1 user user  1111 2010-07-31 06:33 gmpc-trunk-gmpc-stableicon.png
-rw-r--r-- 1 user user  4394 2010-07-31 06:33 gmpc-trunk-gmpc-stablelogo.png
-rw-r--r-- 1 user user  1083 2010-07-31 06:33 gmpc-trunk-mpd-stable-icon.png
-rwxr-xr-x 1 user user  3145 2010-07-31 06:33 gmpc-trunk-mpd-stable-logo.png
-rw-r--r-- 1 user user  1111 2010-07-31 06:33 gmpc-trunk-mpd-trunkicon.png
-rw-r--r-- 1 user user  4394 2010-07-31 06:33 gmpc-trunk-mpd-trunklogo.png
-rw-r--r-- 1 user user  1111 2010-07-31 06:33 gmpc-trunk-ppaicon.png
-rw-r--r-- 1 user user  4394 2010-07-31 06:33 gmpc-trunk-ppalogo.png
-rw-r--r-- 1 user user  1122 2010-07-31 06:33 gnome-colors-packagers-ppaicon.png
-rw-r--r-- 1 user user  4179 2010-07-31 06:33 gnome-colors-packagers-ppalogo.png
-rw-r--r-- 1 user user  1076 2010-07-31 06:33 gnome-globalmenu-icon.png
-rwxr-xr-x 1 user user  3948 2010-07-31 06:33 gnome-globalmenu-logo.png
-rw-r--r-- 1 user user  1066 2010-07-31 06:33 gnome-terminator-ppaicon.png
-rw-r--r-- 1 user user  4082 2010-07-31 06:33 gnome-terminator-ppalogo.png
-rw-r--r-- 1 user user   919 2010-07-31 06:33 gnote-ppaicon.png
-rw-r--r-- 1 user user  3209 2010-07-31 06:33 gnote-ppalogo.png
-rw-r--r-- 1 user user  1231 2010-07-31 06:33 gnuzilla-team-ppa-icon.png
-rwxr-xr-x 1 user user  5396 2010-07-31 06:33 gnuzilla-team-ppa-logo.png
-rw-r--r-- 1 user user  1238 2010-07-31 06:33 google-stable-source-icon.png
-rw-r--r-- 1 user user  4746 2010-07-31 06:33 google-stable-source-logo.png
-rw-r--r-- 1 user user   913 2010-07-31 06:33 gtg-development-ppa-icon.png
-rw-r--r-- 1 user user   822 2010-07-31 06:33 gtg-ppaicon.png
-rwxr-xr-x 1 user user  2141 2010-07-31 06:33 gtg-ppalogo_.png
-rw-r--r-- 1 user user  2141 2010-07-31 06:33 gtg-ppalogo.png
-rw-r--r-- 1 user user  1079 2010-07-31 06:33 gwibber-daily-ppa-icon.png
-rw-r--r-- 1 user user  3715 2010-07-31 06:33 gwibber-daily-ppa-logo.png
-rw-r--r-- 1 user user  1079 2010-07-31 06:33 gwibber-team-ppa-icon.png
-rwxr-xr-x 1 user user  3715 2010-07-31 06:33 gwibber-team-ppa-logo.png
-rw-r--r-- 1 user user  1217 2010-07-31 06:33 handbrake-ubuntu-ppa-icon.png
-rwxr-xr-x 1 user user  7764 2010-07-31 06:33 handbrake-ubuntu-ppa-logo.png
-rw-r--r-- 1 user user  1027 2010-07-31 06:33 happyaron-amule-dlp-icon.png
-rwxr-xr-x 1 user user  3967 2010-07-31 06:33 happyaron-amule-dlp-logo.png
-rw-r--r-- 1 user user   896 2010-07-31 06:33 hugin-hugin-builds-icon.png
-rwxr-xr-x 1 user user  2726 2010-07-31 06:33 hugin-hugin-builds-logo.png
-rw-r--r-- 1 user user  1158 2010-07-31 06:33 hydr0g3n-ppa-icon.png
-rwxr-xr-x 1 user user  4784 2010-07-31 06:33 hydr0g3n-ppa-logo.png
-rw-r--r-- 1 user user   888 2010-07-31 06:33 ibus-12-for-lucid-icon.png
-rwxr-xr-x 1 user user  1372 2010-07-31 06:33 ibus-12-for-lucid-logo.png
-rw-r--r-- 1 user user   888 2010-07-31 06:33 ibus-dev-ibus-12-karmic-icon.png
-rwxr-xr-x 1 user user  1372 2010-07-31 06:33 ibus-dev-ibus-12-karmic-logo.png
-rw-r--r-- 1 user user   888 2010-07-31 06:33 ibus-icon.png
-rw-r--r-- 1 user user  1372 2010-07-31 06:33 ibus-logo.png
-rw-r--r-- 1 user user  1030 2010-07-31 06:33 jason-scheunemann-ppa-icon.png
-rwxr-xr-x 1 user user  2555 2010-07-31 06:33 jason-scheunemann-ppa-logo.png
-rw-r--r-- 1 user user   965 2010-07-31 06:33 kdenlive-icon.png
-rw-r--r-- 1 user user  3246 2010-07-31 06:33 kdenlive-logo.png
-rw-r--r-- 1 user user  1236 2010-07-31 06:33 keepassx-icon.png
-rw-r--r-- 1 user user  5542 2010-07-31 06:33 keepassx-logo.png
-rw-r--r-- 1 user user  1239 2010-07-31 06:33 keepassx-ppaicon.png
-rw-r--r-- 1 user user  5587 2010-07-31 06:33 keepassx-ppalogo.png
-rw-r--r-- 1 user user  1229 2010-07-31 06:33 kubuntu-ppa-beta-icon.png
-rwxr-xr-x 1 user user  4462 2010-07-31 06:33 kubuntu-ppa-beta-logo.png
-rw-r--r-- 1 user user   701 2010-07-31 06:33 lazka-ppa-icon.png
-rwxr-xr-x 1 user user  2961 2010-07-31 06:33 lazka-ppa-logo.png
-rw-r--r-- 1 user user   960 2010-07-31 06:33 liferea-liferea-unstable-icon.png
-rwxr-xr-x 1 user user  3367 2010-07-31 06:33 liferea-liferea-unstable-logo.png
-rw-r--r-- 1 user user   883 2010-07-31 06:33 liferea-ppaicon.png
-rw-r--r-- 1 user user  3367 2010-07-31 06:33 liferea-ppalogo.png
-rw-r--r-- 1 user user   955 2010-07-31 06:33 linuxdcpp-team-ppa-icon.png
-rwxr-xr-x 1 user user  4153 2010-07-31 06:33 linuxdcpp-team-ppa-logo.png
-rw-r--r-- 1 user user   758 2010-07-31 06:33 listen-devel-ppaicon.png
-rw-r--r-- 1 user user  2669 2010-07-31 06:33 listen-devel-ppalogo.png
-rw-r--r-- 1 user user  1100 2010-07-31 06:33 loneowais-ppa-icon.png
-rwxr-xr-x 1 user user  6881 2010-07-31 06:33 loneowais-ppa-logo.png
-rw-r--r-- 1 user user  1084 2010-07-31 06:33 lottanzb-ppa-icon.png
-rwxr-xr-x 1 user user  2947 2010-07-31 06:33 lottanzb-ppa-logo.png
-rw-r--r-- 1 user user   893 2010-07-31 06:33 markuz-ppa-icon.png
-rwxr-xr-x 1 user user  2663 2010-07-31 06:33 markuz-ppa-logo.png
-rw-r--r-- 1 user user  2885 2010-07-31 06:33 matthaeus123-mrw-gimp-svn-logo.png
-rw-r--r-- 1 user user  1188 2010-07-31 06:33 midnight-commander-ppa-icon.png
-rwxr-xr-x 1 user user  4478 2010-07-31 06:33 midnight-commander-ppa-logo.png
-rw-r--r-- 1 user user  1179 2010-07-31 06:33 midori-ppaicon.png
-rw-r--r-- 1 user user  4963 2010-07-31 06:33 midori-ppalogo.png
-rw-r--r-- 1 user user  1095 2010-07-31 06:33 miro-icon.png
-rwxr-xr-x 1 user user  3394 2010-07-31 06:33 miro-logo.png
-rw-r--r-- 1 user user   971 2010-07-31 06:33 miserware-icon.png
-rwxr-xr-x 1 user user  4511 2010-07-31 06:33 miserware-logo.png
-rw-r--r-- 1 user user   946 2010-07-31 06:33 neversfelde-ppa-icon.png
-rwxr-xr-x 1 user user  1831 2010-07-31 06:33 neversfelde-ppa-logo.png
-rw-r--r-- 1 user user  1182 2010-07-31 06:33 opera-beta-icon.png
-rwxr-xr-x 1 user user  3355 2010-07-31 06:33 opera-beta-logo.png
-rw-r--r-- 1 user user  1247 2010-07-31 06:33 osd-lyrics-ppa-icon.png
-rwxr-xr-x 1 user user  5579 2010-07-31 06:33 osd-lyrics-ppa-logo.png
-rw-r--r-- 1 user user  1073 2010-07-31 06:33 pdfmod-team-ppa-icon.png
-rwxr-xr-x 1 user user  3437 2010-07-31 06:33 pdfmod-team-ppa-logo.png
-rw-r--r-- 1 user user  1060 2010-07-31 06:33 pidgin-developers-ppaicon.png
-rw-r--r-- 1 user user  3756 2010-07-31 06:33 pidgin-developers-ppalogo.png
-rw-r--r-- 1 user user  1151 2010-07-31 06:33 playdeb-icon.png
-rwxr-xr-x 1 user user  5109 2010-07-31 06:33 playdeb-logo.png
-rw-r--r-- 1 user user  1187 2010-07-31 06:33 playonlinux-ppa-icon.png
-rwxr-xr-x 1 user user  3481 2010-07-31 06:33 playonlinux-ppa-logo.png
-rw-r--r-- 1 user user  1040 2010-07-31 06:33 ppa-for-deluge-icon.png
-rwxr-xr-x 1 user user  3420 2010-07-31 06:33 ppa-for-deluge-logo.png
-rwxr-xr-x 1 user user   851 2010-07-31 06:33 qgis-stable-icon.png
-rwxr-xr-x 1 user user  3686 2010-07-31 06:33 qgis-stable-logo.png
-rwxr-xr-x 1 user user   851 2010-07-31 06:33 qgis-unstable-icon.png
-rwxr-xr-x 1 user user  3686 2010-07-31 06:33 qgis-unstable-logo.png
-rw-r--r-- 1 user user   701 2010-07-31 06:33 quod-libet-stable-icon.png
-rwxr-xr-x 1 user user  2961 2010-07-31 06:33 quod-libet-stable-logo.png
-rw-r--r-- 1 user user  1154 2010-07-31 06:33 qutim-qutim-icon.png
-rwxr-xr-x 1 user user  6327 2010-07-31 06:33 qutim-qutim-logo.png
-rw-r--r-- 1 user user  1052 2010-07-31 06:33 rabbitvcs-ppa-icon.png
-rwxr-xr-x 1 user user  3027 2010-07-31 06:33 rabbitvcs-ppa-logo.png
-rw-r--r-- 1 user user  1115 2010-07-31 06:33 rednotebook-icon.png
-rwxr-xr-x 1 user user  4338 2010-07-31 06:33 rednotebook-logo.png
-rw-r--r-- 1 user user   906 2010-09-15 14:47 repo-for-scribus-icon.png
-rwxr-xr-x 1 user user  3682 2010-09-15 14:47 repo-for-scribus-logo.png
-rw-r--r-- 1 user user  1141 2010-07-31 06:33 ricotz-testing-icon.png
-rwxr-xr-x 1 user user  4480 2010-07-31 06:33 ricotz-testing-logo.png
-rwxr-xr-x 1 user user   330 2010-07-31 06:33 rlinfati-ppa-icon.png
-rwxr-xr-x 1 user user   614 2010-07-31 06:33 rlinfati-ppa-logo.png
-rw-r--r-- 1 user user  1194 2010-07-31 06:33 rssowl-icon.png
-rwxr-xr-x 1 user user  6662 2010-07-31 06:33 rssowl-logo.png
-rw-r--r-- 1 user user  1153 2010-07-31 06:33 rvm-smplayer-icon.png
-rwxr-xr-x 1 user user  4847 2010-07-31 06:33 rvm-smplayer-logo.png
-rw-r--r-- 1 user user  1171 2010-07-31 06:33 samsung-tools-icon.png
-rwxr-xr-x 1 user user  7223 2010-07-31 06:33 samsung-tools-logo.png
-rw-r--r-- 1 user user   966 2010-07-31 06:33 sevenmachines-flash-icon.png
-rwxr-xr-x 1 user user  2057 2010-07-31 06:33 sevenmachines-flash-logo.png
-rw-r--r-- 1 user user  1225 2010-07-31 06:33 shutter-icon.png
-rw-r--r-- 1 user user  4687 2010-07-31 06:33 shutter-logo.png
-rw-r--r-- 1 user user  1225 2010-07-31 06:33 shutter-testing-team-ppa-icon.png
-rwxr-xr-x 1 user user  4687 2010-07-31 06:33 shutter-testing-team-ppa-logo.png
-rw-r--r-- 1 user user  1206 2010-07-31 06:33 skype-icon.png
-rwxr-xr-x 1 user user  4840 2010-07-31 06:33 skype-logo.png
-rw-r--r-- 1 user user  1040 2010-07-31 06:33 smc-icon.png
-rwxr-xr-x 1 user user  4397 2010-07-31 06:33 smc-logo.png
-rw-r--r-- 1 user user  1153 2010-07-31 06:33 smplayer-testing-icon.png
-rwxr-xr-x 1 user user  4847 2010-07-31 06:33 smplayer-testing-logo.png
-rw-r--r-- 1 user user  1096 2010-07-31 06:33 songbird-daily-ppa-icon.png
-rwxr-xr-x 1 user user  4177 2010-07-31 06:33 songbird-daily-ppa-logo.png
-rwxr-xr-x 1 user user   619 2010-07-31 06:33 subsonic-icon.png
-rwxr-xr-x 1 user user  2126 2010-07-31 06:33 subsonic-logo.png
-rw-r--r-- 1 user user  1148 2010-07-31 06:33 swiftfox-icon.png
-rwxr-xr-x 1 user user  4735 2010-07-31 06:33 swiftfox-logo.png
-rw-r--r-- 1 user user  1139 2010-07-31 06:33 synapse-ppa-icon.png
-rwxr-xr-x 1 user user  3781 2010-07-31 06:33 synapse-ppa-logo.png
-rw-r--r-- 1 user user   916 2010-07-31 06:33 team-xbmc-ppa-icon.png
-rwxr-xr-x 1 user user  2814 2010-07-31 06:33 team-xbmc-ppa-logo.png
-rw-r--r-- 1 user user   969 2010-07-31 06:33 telepathy-ppaicon.png
-rw-r--r-- 1 user user  3593 2010-07-31 06:33 telepathy-ppalogo.png
-rw-r--r-- 1 user user  1168 2010-07-31 06:33 testdrive-ppa-icon.png
-rwxr-xr-x 1 user user  5022 2010-07-31 06:33 testdrive-ppa-logo.png
-rw-r--r-- 1 user user  1182 2010-07-31 06:33 the-official-source-of-opera-icon.png
-rw-r--r-- 1 user user  3355 2010-07-31 06:33 the-official-source-of-opera-logo.png
-rwxr-xr-x 1 user user   617 2010-07-31 06:33 tomboy-packagers-stable-icon.png
-rwxr-xr-x 1 user user  2644 2010-07-31 06:33 tomboy-packagers-stable-logo.png
-rw-r--r-- 1 user user   988 2010-07-31 06:33 troorl-pino-icon.png
-rwxr-xr-x 1 user user  2663 2010-07-31 06:33 troorl-pino-logo.png
-rw-r--r-- 1 user user  1210 2010-07-31 06:33 ubuntu-tweak-icon.png
-rw-r--r-- 1 user user  4646 2010-07-31 06:33 ubuntu-tweak-logo.png
-rw-r--r-- 1 user user  1210 2010-07-31 06:33 ubuntu-tweak-testing-ppa-icon.png
-rwxr-xr-x 1 user user  4646 2010-07-31 06:33 ubuntu-tweak-testing-ppa-logo.png
-rw-r--r-- 1 user user  1199 2010-07-31 06:33 ubuntu-wine-ppaicon.png
-rw-r--r-- 1 user user  5101 2010-07-31 06:33 ubuntu-wine-ppalogo.png
-rw-r--r-- 1 user user  1154 2010-07-31 06:33 ubuntu-x-swat-x-updates-icon.png
-rwxr-xr-x 1 user user  5020 2010-07-31 06:33 ubuntu-x-swat-x-updates-logo.png
-rw-r--r-- 1 user user  1178 2010-07-31 06:33 virtualbox-offical-source-icon.png
-rwxr-xr-x 1 user user  4590 2010-07-31 06:33 virtualbox-offical-source-logo.png
-rw-r--r-- 1 user user  1066 2010-07-31 06:33 wakoopa-icon.png
-rwxr-xr-x 1 user user  2928 2010-07-31 06:33 wakoopa-logo.png
-rw-r--r-- 1 user user  1224 2010-07-31 06:33 webkit-team-ppaicon.png
-rw-r--r-- 1 user user  5431 2010-07-31 06:33 webkit-team-ppalogo.png
-rw-r--r-- 1 user user   877 2010-09-18 21:55 wengxt-fcitx-nightly-icon.png
-rwxr-xr-x 1 user user  3202 2010-09-18 21:55 wengxt-fcitx-nightly-logo.png
-rw-r--r-- 1 user user  1261 2010-07-31 06:33 xneur-icon.png
-rwxr-xr-x 1 user user  3019 2010-07-31 06:33 xneur-logo.png
-rw-r--r-- 1 user user   923 2010-07-31 06:33 xorg-edgers-ppa-icon.png
-rwxr-xr-x 1 user user  1649 2010-07-31 06:33 xorg-edgers-ppa-logo.png
-rw-r--r-- 1 user user  1135 2010-07-31 06:33 xsisqox-ppa-icon.png
-rwxr-xr-x 1 user user  2818 2010-07-31 06:33 xsisqox-ppa-logo.png
-rw-r--r-- 1 user user  1117 2010-07-31 06:33 yorba-ppa-icon.png
-rwxr-xr-x 1 user user  4344 2010-07-31 06:33 yorba-ppa-logo.png
-rw-r--r-- 1 user user  1204 2010-07-31 06:33 zeitgeist-ppa-icon.png
-rwxr-xr-x 1 user user  3041 2010-07-31 06:33 zeitgeist-ppa-logo.png
-rw-r--r-- 1 user user  1083 2010-07-31 06:33 zik-icon.png
-rwxr-xr-x 1 user user  2762 2010-07-31 06:33 zik-logo.png

./.config/ubuntu-tweak/temp:
total 704
drwxr-xr-x 2 user user   4096 2010-10-02 10:22 .
drwxrwxrwx 8 user user   4096 2010-10-02 10:22 ..
-rw-r--r-- 1 user user 709527 2010-10-02 10:22 sourcecenter-1285341217.tar.gz

./.config/ubuntu-tweak/templates:
total 52
drwxr-xr-x 2 user user 4096 2010-10-02 10:04 .
drwxrwxrwx 8 user user 4096 2010-10-02 10:22 ..
-rw-r--r-- 1 user user    0 2010-10-02 10:04 HTML document.html
-rw-r--r-- 1 user user 1381 2010-10-02 10:04 ODB Database.odb
-rw-r--r-- 1 user user 8632 2010-10-02 10:04 ODP Presentation.odp
-rw-r--r-- 1 user user 6364 2010-10-02 10:04 ODS Spreadsheet.ods
-rw-r--r-- 1 user user 7172 2010-10-02 10:04 ODT Document.odt
-rw-r--r-- 1 user user    0 2010-10-02 10:04 Plain text document.txt
-rw-r--r-- 1 user user  969 2010-10-02 10:04 Pygtk Example.py
-rw-r--r-- 1 user user   39 2010-10-02 10:04 Python script.py
-rw-r--r-- 1 user user   12 2010-10-02 10:04 Shell script.sh

./.dbus:
total 12
drwxrwxrwx  3 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 session-bus

./.dbus/session-bus:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx 1 user user  463 2010-10-02 15:28 0d6e2173dda0703366309b6c4c6423db-0

./Desktop:
total 8
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..

./Documents:
total 8
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..

./Downloads:
total 8
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..

./.fontconfig:
total 12
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..
-rw-r--r--  1 user user   80 2010-10-02 10:12 5b5ff9937a04042607e44b30283e1004-le32d4.cache-3

./.gconf:
total 16
drwxrwxrwx  4 user user 4096 2010-10-02 15:28 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 apps
drwxrwxrwx  3 user user 4096 2010-10-02 07:43 desktop

./.gconf/apps:
total 60
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 .
drwxrwxrwx  4 user user 4096 2010-10-02 15:28 ..
drwxr-xr-x  3 user user 4096 2010-10-02 09:35 compiz
drwxr-xr-x  3 user user 4096 2010-10-02 10:14 eog
drwxr-xr-x  3 user user 4096 2010-10-02 09:35 evolution
-rwxrwxrwx  1 user user    0 2010-10-02 07:43 %gconf.xml
drwxrwxrwx  4 user user 4096 2010-10-02 07:53 gedit-2
drwxrwxrwx  3 user user 4096 2010-10-02 07:57 gnome-power-manager
drwxr-xr-x  2 user user 4096 2010-10-02 15:33 gnome-screenshot
drwxrwxrwx  3 user user 4096 2010-10-02 07:50 gnome-terminal
drwxr-xr-x  2 user user 4096 2010-10-02 13:25 gwd
drwxr-xr-x  3 user user 4096 2010-10-02 09:46 metacity
drwxrwxrwx  6 user user 4096 2010-10-02 10:04 nautilus
drwxr-xr-x  2 user user 4096 2010-10-02 09:35 nm-applet
drwxrwxrwx  6 user user 4096 2010-10-02 07:43 panel
drwxrwxrwx  2 user user 4096 2010-10-02 13:26 ubuntu-tweak

./.gconf/apps/compiz:
total 12
drwxr-xr-x  3 user user 4096 2010-10-02 09:35 .
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 ..
-rw-r--r--  1 user user    0 2010-10-02 09:35 %gconf.xml
drwxr-xr-x  3 user user 4096 2010-10-02 09:35 general

./.gconf/apps/compiz/general:
total 12
drwxr-xr-x 3 user user 4096 2010-10-02 09:35 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:35 ..
drwxr-xr-x 3 user user 4096 2010-10-02 09:35 allscreens
-rw-r--r-- 1 user user    0 2010-10-02 09:35 %gconf.xml

./.gconf/apps/compiz/general/allscreens:
total 12
drwxr-xr-x 3 user user 4096 2010-10-02 09:35 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:35 ..
-rw-r--r-- 1 user user    0 2010-10-02 09:35 %gconf.xml
drwxr-xr-x 2 user user 4096 2010-10-02 15:28 options

./.gconf/apps/compiz/general/allscreens/options:
total 12
drwxr-xr-x 2 user user 4096 2010-10-02 15:28 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:35 ..
-rw-r--r-- 1 user user 2229 2010-10-02 15:28 %gconf.xml

./.gconf/apps/eog:
total 12
drwxr-xr-x  3 user user 4096 2010-10-02 10:14 .
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 ..
-rw-r--r--  1 user user    0 2010-10-02 10:14 %gconf.xml
drwxr-xr-x  2 user user 4096 2010-10-02 14:26 ui

./.gconf/apps/eog/ui:
total 12
drwxr-xr-x 2 user user 4096 2010-10-02 14:26 .
drwxr-xr-x 3 user user 4096 2010-10-02 10:14 ..
-rw-r--r-- 1 user user  188 2010-10-02 14:26 %gconf.xml

./.gconf/apps/evolution:
total 12
drwxr-xr-x  3 user user 4096 2010-10-02 09:35 .
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 ..
drwxr-xr-x  3 user user 4096 2010-10-02 09:35 calendar
-rw-r--r--  1 user user    0 2010-10-02 09:35 %gconf.xml

./.gconf/apps/evolution/calendar:
total 16
drwxr-xr-x 3 user user 4096 2010-10-02 09:35 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:35 ..
-rw-r--r-- 1 user user  119 2010-10-02 09:35 %gconf.xml
drwxr-xr-x 2 user user 4096 2010-10-02 09:35 notify

./.gconf/apps/evolution/calendar/notify:
total 12
drwxr-xr-x 2 user user 4096 2010-10-02 09:35 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:35 ..
-rw-r--r-- 1 user user  117 2010-10-02 09:35 %gconf.xml

./.gconf/apps/gedit-2:
total 16
drwxrwxrwx  4 user user 4096 2010-10-02 07:53 .
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 ..
-rwxrwxrwx  1 user user    0 2010-10-02 07:53 %gconf.xml
drwxrwxrwx  3 user user 4096 2010-10-02 07:53 plugins
drwxrwxrwx  3 user user 4096 2010-10-02 07:53 preferences

./.gconf/apps/gedit-2/plugins:
total 12
drwxrwxrwx 3 user user 4096 2010-10-02 07:53 .
drwxrwxrwx 4 user user 4096 2010-10-02 07:53 ..
drwxrwxrwx 3 user user 4096 2010-10-02 07:53 filebrowser
-rwxrwxrwx 1 user user    0 2010-10-02 07:53 %gconf.xml

./.gconf/apps/gedit-2/plugins/filebrowser:
total 12
drwxrwxrwx 3 user user 4096 2010-10-02 07:53 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:53 ..
-rwxrwxrwx 1 user user    0 2010-10-02 07:53 %gconf.xml
drwxrwxrwx 2 user user 4096 2010-10-02 15:30 on_load

./.gconf/apps/gedit-2/plugins/filebrowser/on_load:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 15:30 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:53 ..
-rwxrwxrwx 1 user user  331 2010-10-02 15:30 %gconf.xml

./.gconf/apps/gedit-2/preferences:
total 12
drwxrwxrwx 3 user user 4096 2010-10-02 07:53 .
drwxrwxrwx 4 user user 4096 2010-10-02 07:53 ..
-rwxrwxrwx 1 user user    0 2010-10-02 07:53 %gconf.xml
drwxrwxrwx 3 user user 4096 2010-10-02 07:53 ui

./.gconf/apps/gedit-2/preferences/ui:
total 12
drwxrwxrwx 3 user user 4096 2010-10-02 07:53 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:53 ..
-rwxrwxrwx 1 user user    0 2010-10-02 07:53 %gconf.xml
drwxrwxrwx 2 user user 4096 2010-10-02 15:30 statusbar

./.gconf/apps/gedit-2/preferences/ui/statusbar:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 15:30 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:53 ..
-rwxrwxrwx 1 user user  118 2010-10-02 15:30 %gconf.xml

./.gconf/apps/gnome-power-manager:
total 12
drwxrwxrwx  3 user user 4096 2010-10-02 07:57 .
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 ..
drwxrwxrwx  2 user user 4096 2010-10-02 10:25 backlight
-rwxrwxrwx  1 user user    0 2010-10-02 07:57 %gconf.xml

./.gconf/apps/gnome-power-manager/backlight:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 10:25 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:57 ..
-rwxrwxrwx 1 user user  193 2010-10-02 10:25 %gconf.xml

./.gconf/apps/gnome-screenshot:
total 12
drwxr-xr-x  2 user user 4096 2010-10-02 15:33 .
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 ..
-rw-r--r--  1 user user  482 2010-10-02 15:33 %gconf.xml

./.gconf/apps/gnome-terminal:
total 12
drwxrwxrwx  3 user user 4096 2010-10-02 07:50 .
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 ..
-rwxrwxrwx  1 user user    0 2010-10-02 07:50 %gconf.xml
drwxrwxrwx  3 user user 4096 2010-10-02 07:50 profiles

./.gconf/apps/gnome-terminal/profiles:
total 12
drwxrwxrwx 3 user user 4096 2010-10-02 07:50 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:50 ..
drwxrwxrwx 2 user user 4096 2010-10-02 15:48 Default
-rwxrwxrwx 1 user user    0 2010-10-02 07:50 %gconf.xml

./.gconf/apps/gnome-terminal/profiles/Default:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 15:48 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:50 ..
-rwxrwxrwx 1 user user  904 2010-10-02 15:48 %gconf.xml

./.gconf/apps/gwd:
total 12
drwxr-xr-x  2 user user 4096 2010-10-02 13:25 .
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 ..
-rw-r--r--  1 user user  213 2010-10-02 13:25 %gconf.xml

./.gconf/apps/metacity:
total 12
drwxr-xr-x  3 user user 4096 2010-10-02 09:46 .
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 ..
-rw-r--r--  1 user user    0 2010-10-02 09:46 %gconf.xml
drwxr-xr-x  2 user user 4096 2010-10-02 10:30 general

./.gconf/apps/metacity/general:
total 12
drwxr-xr-x 2 user user 4096 2010-10-02 10:30 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:46 ..
-rw-r--r-- 1 user user  275 2010-10-02 10:30 %gconf.xml

./.gconf/apps/nautilus:
total 24
drwxrwxrwx  6 user user 4096 2010-10-02 10:04 .
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 ..
drwxr-xr-x  2 user user 4096 2010-10-02 10:04 desktop
drwxrwxrwx  4 user user 4096 2010-10-02 10:04 desktop-metadata
-rwxrwxrwx  1 user user    0 2010-10-02 07:44 %gconf.xml
drwxrwxrwx  2 user user 4096 2010-10-02 07:48 list_view
drwxrwxrwx  2 user user 4096 2010-10-02 15:28 preferences

./.gconf/apps/nautilus/desktop:
total 12
drwxr-xr-x 2 user user 4096 2010-10-02 10:04 .
drwxrwxrwx 6 user user 4096 2010-10-02 10:04 ..
-rw-r--r-- 1 user user  118 2010-10-02 10:04 %gconf.xml

./.gconf/apps/nautilus/desktop-metadata:
total 16
drwxrwxrwx 4 user user 4096 2010-10-02 10:04 .
drwxrwxrwx 6 user user 4096 2010-10-02 10:04 ..
drwxrwxrwx 2 user user 4096 2010-10-02 15:28 directory
-rwxrwxrwx 1 user user    0 2010-10-02 07:44 %gconf.xml
drwxr-xr-x 2 user user 4096 2010-10-02 15:28 home

./.gconf/apps/nautilus/desktop-metadata/directory:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 15:28 .
drwxrwxrwx 4 user user 4096 2010-10-02 10:04 ..
-rwxrwxrwx 1 user user  470 2010-10-02 15:28 %gconf.xml

./.gconf/apps/nautilus/desktop-metadata/home:
total 12
drwxr-xr-x 2 user user 4096 2010-10-02 15:28 .
drwxrwxrwx 4 user user 4096 2010-10-02 10:04 ..
-rw-r--r-- 1 user user  389 2010-10-02 15:28 %gconf.xml

./.gconf/apps/nautilus/list_view:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 07:48 .
drwxrwxrwx 6 user user 4096 2010-10-02 10:04 ..
-rwxrwxrwx 1 user user 1318 2010-10-02 07:48 %gconf.xml

./.gconf/apps/nautilus/preferences:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 15:28 .
drwxrwxrwx 6 user user 4096 2010-10-02 10:04 ..
-rwxrwxrwx 1 user user  439 2010-10-02 15:28 %gconf.xml

./.gconf/apps/nm-applet:
total 12
drwxr-xr-x  2 user user 4096 2010-10-02 09:35 .
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 ..
-rw-r--r--  1 user user  102 2010-10-02 09:35 %gconf.xml

./.gconf/apps/panel:
total 24
drwxrwxrwx  6 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 ..
drwxrwxrwx 10 user user 4096 2010-10-02 07:43 applets
-rwxrwxrwx  1 user user    0 2010-10-02 07:43 %gconf.xml
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 general
drwxrwxrwx  5 user user 4096 2010-10-02 07:43 objects
drwxrwxrwx  4 user user 4096 2010-10-02 07:43 toplevels

./.gconf/apps/panel/applets:
total 40
drwxrwxrwx 10 user user 4096 2010-10-02 07:43 .
drwxrwxrwx  6 user user 4096 2010-10-02 07:43 ..
drwxrwxrwx  3 user user 4096 2010-10-02 07:44 clock_screen0
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 fast_user_switch_screen0
-rwxrwxrwx  1 user user    0 2010-10-02 07:43 %gconf.xml
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 indicator_applet_screen0
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 notification_area_screen0
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 show_desktop_button_screen0
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 trashapplet_screen0
drwxrwxrwx  3 user user 4096 2010-10-02 07:44 window_list_screen0
drwxrwxrwx  3 user user 4096 2010-10-02 07:44 workspace_switcher_screen0

./.gconf/apps/panel/applets/clock_screen0:
total 16
drwxrwxrwx  3 user user 4096 2010-10-02 07:44 .
drwxrwxrwx 10 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx  1 user user 1705 2010-10-02 07:43 %gconf.xml
drwxrwxrwx  2 user user 4096 2010-10-02 07:44 prefs

./.gconf/apps/panel/applets/clock_screen0/prefs:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 07:44 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:44 ..
-rwxrwxrwx 1 user user 2295 2010-10-02 07:44 %gconf.xml

./.gconf/apps/panel/applets/fast_user_switch_screen0:
total 12
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 10 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx  1 user user 1714 2010-10-02 07:43 %gconf.xml

./.gconf/apps/panel/applets/indicator_applet_screen0:
total 12
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 10 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx  1 user user 1709 2010-10-02 07:43 %gconf.xml

./.gconf/apps/panel/applets/notification_area_screen0:
total 12
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 10 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx  1 user user 1716 2010-10-02 07:43 %gconf.xml

./.gconf/apps/panel/applets/show_desktop_button_screen0:
total 12
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 10 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx  1 user user 1715 2010-10-02 07:43 %gconf.xml

./.gconf/apps/panel/applets/trashapplet_screen0:
total 12
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 10 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx  1 user user 1617 2010-10-02 07:43 %gconf.xml

./.gconf/apps/panel/applets/window_list_screen0:
total 16
drwxrwxrwx  3 user user 4096 2010-10-02 07:44 .
drwxrwxrwx 10 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx  1 user user 1714 2010-10-02 07:43 %gconf.xml
drwxrwxrwx  2 user user 4096 2010-10-02 07:44 prefs

./.gconf/apps/panel/applets/window_list_screen0/prefs:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 07:44 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:44 ..
-rwxrwxrwx 1 user user  635 2010-10-02 07:44 %gconf.xml

./.gconf/apps/panel/applets/workspace_switcher_screen0:
total 16
drwxrwxrwx  3 user user 4096 2010-10-02 07:44 .
drwxrwxrwx 10 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx  1 user user 1720 2010-10-02 07:43 %gconf.xml
drwxrwxrwx  2 user user 4096 2010-10-02 07:44 prefs

./.gconf/apps/panel/applets/workspace_switcher_screen0/prefs:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 07:44 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:44 ..
-rwxrwxrwx 1 user user  424 2010-10-02 07:44 %gconf.xml

./.gconf/apps/panel/general:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 6 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx 1 user user 1357 2010-10-02 07:43 %gconf.xml

./.gconf/apps/panel/objects:
total 20
drwxrwxrwx 5 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 6 user user 4096 2010-10-02 07:43 ..
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 browser_launcher_screen0
-rwxrwxrwx 1 user user    0 2010-10-02 07:43 %gconf.xml
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 menu_bar_screen0
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 yelp_launcher_screen0

./.gconf/apps/panel/objects/browser_launcher_screen0:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 5 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx 1 user user 1699 2010-10-02 07:43 %gconf.xml

./.gconf/apps/panel/objects/menu_bar_screen0:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 5 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx 1 user user 1624 2010-10-02 07:43 %gconf.xml

./.gconf/apps/panel/objects/yelp_launcher_screen0:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 5 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx 1 user user 1727 2010-10-02 07:43 %gconf.xml

./.gconf/apps/panel/toplevels:
total 16
drwxrwxrwx 4 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 6 user user 4096 2010-10-02 07:43 ..
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 bottom_panel_screen0
-rwxrwxrwx 1 user user    0 2010-10-02 07:43 %gconf.xml
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 top_panel_screen0

./.gconf/apps/panel/toplevels/bottom_panel_screen0:
total 16
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 4 user user 4096 2010-10-02 07:43 ..
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 background
-rwxrwxrwx 1 user user 2085 2010-10-02 07:43 %gconf.xml

./.gconf/apps/panel/toplevels/bottom_panel_screen0/background:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx 1 user user  754 2010-10-02 07:43 %gconf.xml

./.gconf/apps/panel/toplevels/top_panel_screen0:
total 16
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 4 user user 4096 2010-10-02 07:43 ..
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 background
-rwxrwxrwx 1 user user 2061 2010-10-02 07:43 %gconf.xml

./.gconf/apps/panel/toplevels/top_panel_screen0/background:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx 1 user user  754 2010-10-02 07:43 %gconf.xml

./.gconf/apps/ubuntu-tweak:
total 12
drwxrwxrwx  2 user user 4096 2010-10-02 13:26 .
drwxrwxrwx 15 user user 4096 2010-10-02 10:14 ..
-rwxrwxrwx  1 user user  957 2010-10-02 13:26 %gconf.xml

./.gconf/desktop:
total 12
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 4 user user 4096 2010-10-02 15:28 ..
-rwxrwxrwx 1 user user    0 2010-10-02 07:43 %gconf.xml
drwxrwxrwx 7 user user 4096 2010-10-02 09:46 gnome

./.gconf/desktop/gnome:
total 28
drwxrwxrwx 7 user user 4096 2010-10-02 09:46 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 ..
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 accessibility
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 applications
drwxr-xr-x 2 user user 4096 2010-10-02 10:30 background
-rwxrwxrwx 1 user user    0 2010-10-02 07:43 %gconf.xml
drwxr-xr-x 2 user user 4096 2010-10-02 10:30 interface
drwxrwxrwx 4 user user 4096 2010-10-02 09:46 peripherals

./.gconf/desktop/gnome/accessibility:
total 12
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 7 user user 4096 2010-10-02 09:46 ..
-rwxrwxrwx 1 user user    0 2010-10-02 07:43 %gconf.xml
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 keyboard

./.gconf/desktop/gnome/accessibility/keyboard:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx 1 user user 1627 2010-10-02 07:43 %gconf.xml

./.gconf/desktop/gnome/applications:
total 12
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 7 user user 4096 2010-10-02 09:46 ..
-rwxrwxrwx 1 user user    0 2010-10-02 07:43 %gconf.xml
drwxrwxrwx 2 user user 4096 2010-10-02 15:28 window_manager

./.gconf/desktop/gnome/applications/window_manager:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 15:28 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 ..
-rwxrwxrwx 1 user user  263 2010-10-02 15:28 %gconf.xml

./.gconf/desktop/gnome/background:
total 12
drwxr-xr-x 2 user user 4096 2010-10-02 10:30 .
drwxrwxrwx 7 user user 4096 2010-10-02 09:46 ..
-rw-r--r-- 1 user user  646 2010-10-02 10:30 %gconf.xml

./.gconf/desktop/gnome/interface:
total 12
drwxr-xr-x 2 user user 4096 2010-10-02 10:30 .
drwxrwxrwx 7 user user 4096 2010-10-02 09:46 ..
-rw-r--r-- 1 user user  253 2010-10-02 10:30 %gconf.xml

./.gconf/desktop/gnome/peripherals:
total 16
drwxrwxrwx 4 user user 4096 2010-10-02 09:46 .
drwxrwxrwx 7 user user 4096 2010-10-02 09:46 ..
-rwxrwxrwx 1 user user    0 2010-10-02 07:43 %gconf.xml
drwxr-xr-x 2 user user 4096 2010-10-02 10:30 mouse
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 touchpad

./.gconf/desktop/gnome/peripherals/mouse:
total 12
drwxr-xr-x 2 user user 4096 2010-10-02 10:30 .
drwxrwxrwx 4 user user 4096 2010-10-02 09:46 ..
-rw-r--r-- 1 user user  218 2010-10-02 10:30 %gconf.xml

./.gconf/desktop/gnome/peripherals/touchpad:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 4 user user 4096 2010-10-02 09:46 ..
-rwxrwxrwx 1 user user  125 2010-10-02 07:43 %gconf.xml

./.gconfd:
total 88
drwxrwxrwx  2 user user  4096 2010-10-02 15:47 .
drwxrwxrwx 36 user user  4096 2010-10-02 15:48 ..
-rwx------  1 user user 79423 2010-10-02 15:47 saved_state

./.gegl-0.0:
total 16
drwx------  4 user user 4096 2010-10-02 10:12 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..
drwx------  2 user user 4096 2010-10-02 10:12 plug-ins
drwx------  2 user user 4096 2010-10-02 10:12 swap

./.gegl-0.0/plug-ins:
total 12
drwx------ 2 user user 4096 2010-10-02 10:12 .
drwx------ 4 user user 4096 2010-10-02 10:12 ..
-rw-r--r-- 1 user user  616 2010-10-02 10:12 Makefile

./.gegl-0.0/swap:
total 8
drwx------ 2 user user 4096 2010-10-02 10:12 .
drwx------ 4 user user 4096 2010-10-02 10:12 ..

./.gimp-2.6:
total 544
drwxr-xr-x 22 user user   4096 2010-10-02 11:23 .
drwxrwxrwx 36 user user   4096 2010-10-02 15:48 ..
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 brushes
-rw-------  1 user user    739 2010-10-02 11:23 colorrc
-rw-------  1 user user   1863 2010-10-02 11:23 controllerrc
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 curves
-rw-------  1 user user     57 2010-10-02 11:23 dockrc
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 environ
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 fonts
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 fractalexplorer
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 gfig
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 gflare
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 gimpressionist
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 gradients
-rw-r--r--  1 user user    616 2010-10-02 10:12 gtkrc
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 interpreters
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 levels
-rw-r--r--  1 user user  77800 2010-10-02 11:23 menurc
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 modules
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 palettes
-rw-------  1 user user    102 2010-10-02 11:23 parasiterc
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 patterns
-rw-r--r--  1 user user 343576 2010-10-02 10:12 pluginrc
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 plug-ins
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 scripts
-rw-------  1 user user   1788 2010-10-02 11:23 sessionrc
-rw-------  1 user user   4817 2010-10-02 11:23 templaterc
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 templates
-rw-r--r--  1 user user    304 2010-10-02 11:21 themerc
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 themes
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 tmp
drwxr-xr-x  2 user user   4096 2010-10-02 10:12 tool-options
-rw-------  1 user user   3916 2010-10-02 11:23 toolrc
-rw-------  1 user user   1178 2010-10-02 11:23 unitrc

./.gimp-2.6/brushes:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/curves:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/environ:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/fonts:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/fractalexplorer:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/gfig:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/gflare:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/gimpressionist:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/gradients:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/interpreters:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/levels:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/modules:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/palettes:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/patterns:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/plug-ins:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/scripts:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/templates:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/themes:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/tmp:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gimp-2.6/tool-options:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 10:12 .
drwxr-xr-x 22 user user 4096 2010-10-02 11:23 ..

./.gnome2:
total 44
drwxrwxrwx  8 user user 4096 2010-10-02 15:27 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..
drwxrwxrwx  2 user user 4096 2010-10-02 10:26 accels
-rw-r--r--  1 user user 4997 2010-10-02 10:29 backgrounds.xml
drwxr-x---  2 user user 4096 2010-10-02 10:14 eog
drwxrwxrwx  2 user user 4096 2010-10-02 15:37 gedit
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 keyrings
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 nautilus-scripts
drwxrwxrwx  3 user user 4096 2010-10-02 07:43 panel2.d
-rwxrwxrwx  1 user user   33 2010-10-02 07:55 yelp

./.gnome2/accels:
total 36
drwxrwxrwx 2 user user  4096 2010-10-02 10:26 .
drwxrwxrwx 8 user user  4096 2010-10-02 15:27 ..
-rw-r--r-- 1 user user  3572 2010-10-02 14:26 eog
-rw-r--r-- 1 user user  9714 2010-10-02 15:37 gedit
-rw-r--r-- 1 user user 11565 2010-10-02 15:28 nautilus

./.gnome2/eog:
total 8
drwxr-x--- 2 user user 4096 2010-10-02 10:14 .
drwxrwxrwx 8 user user 4096 2010-10-02 15:27 ..

./.gnome2/gedit:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 15:37 .
drwxrwxrwx 8 user user 4096 2010-10-02 15:27 ..
-rw-r--r-- 1 user user   74 2010-10-02 15:37 gedit-2

./.gnome2/keyrings:
total 16
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 8 user user 4096 2010-10-02 15:27 ..
-rwxrwxrwx 1 user user  105 2010-10-02 07:43 login.keyring
-rwxrwxrwx 1 user user  207 2010-10-02 07:43 user.keystore

./.gnome2/nautilus-scripts:
total 8
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 8 user user 4096 2010-10-02 15:27 ..

./.gnome2/panel2.d:
total 12
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 8 user user 4096 2010-10-02 15:27 ..
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 default

./.gnome2/panel2.d/default:
total 12
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 ..
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 launchers

./.gnome2/panel2.d/default/launchers:
total 8
drwxrwxrwx 2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:43 ..

./.gnome2_private:
total 8
drwxrwxrwx  2 user user 4096 2010-10-02 07:55 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..

./.gstreamer-0.10:
total 612
drwxr-xr-x  2 user user   4096 2010-10-02 10:21 .
drwxrwxrwx 36 user user   4096 2010-10-02 15:48 ..
-rw-------  1 user user 615349 2010-10-02 10:21 registry.i486.bin

./.gvfs:
total 4
dr-x------  2 user user    0 2010-10-02 15:28 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..

./.icons:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:45 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..

./.local:
total 12
drwxrwxrwx  3 user user 4096 2010-10-02 07:47 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..
drwxrwxrwx  4 user user 4096 2010-10-02 10:21 share

./.local/share:
total 16
drwxrwxrwx 4 user user 4096 2010-10-02 10:21 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:47 ..
-rw-r--r-- 1 user user    0 2010-10-02 09:34 .converted-launchers
drwxrwxrwx 2 user user 4096 2010-10-02 15:38 gvfs-metadata
drwx------ 3 user user 4096 2010-10-02 10:21 webkit

./.local/share/gvfs-metadata:
total 152
drwxrwxrwx 2 user user  4096 2010-10-02 15:38 .
drwxrwxrwx 4 user user  4096 2010-10-02 10:21 ..
-rwxrwxrwx 1 user user   184 2010-10-02 07:48 computer:
-rwxrwxrwx 1 user user 32768 2010-10-02 07:48 computer:-49b62ce0.log
-rw------- 1 user user  1228 2010-10-02 15:38 home
-rw-r--r-- 1 user user 32768 2010-10-02 15:38 home-fa69984e.log
-rw------- 1 user user   260 2010-10-02 13:27 root
-rw-r--r-- 1 user user 32768 2010-10-02 13:27 root-815b280b.log
-rwxrwxrwx 1 user user    56 2010-10-02 07:59 trash:
-rwxrwxrwx 1 user user 32768 2010-10-02 07:59 trash:-6f7ca713.log

./.local/share/webkit:
total 12
drwx------ 3 user user 4096 2010-10-02 10:21 .
drwxrwxrwx 4 user user 4096 2010-10-02 10:21 ..
drwx------ 2 user user 4096 2010-10-02 10:23 icondatabase

./.local/share/webkit/icondatabase:
total 28
drwx------ 2 user user  4096 2010-10-02 10:23 .
drwx------ 3 user user  4096 2010-10-02 10:21 ..
-rw-r--r-- 1 user user 17408 2010-10-02 10:21 WebpageIcons.db

./.macromedia:
total 12
drwx------  3 user user 4096 2010-10-02 10:31 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..
drwx------  4 user user 4096 2010-10-02 10:31 Flash_Player

./.macromedia/Flash_Player:
total 16
drwx------ 4 user user 4096 2010-10-02 10:31 .
drwx------ 3 user user 4096 2010-10-02 10:31 ..
drwx------ 3 user user 4096 2010-10-02 10:31 macromedia.com
drwx------ 3 user user 4096 2010-10-02 10:31 #SharedObjects

./.macromedia/Flash_Player/macromedia.com:
total 12
drwx------ 3 user user 4096 2010-10-02 10:31 .
drwx------ 4 user user 4096 2010-10-02 10:31 ..
drwx------ 3 user user 4096 2010-10-02 10:31 support

./.macromedia/Flash_Player/macromedia.com/support:
total 12
drwx------ 3 user user 4096 2010-10-02 10:31 .
drwx------ 3 user user 4096 2010-10-02 10:31 ..
drwx------ 3 user user 4096 2010-10-02 10:31 flashplayer

./.macromedia/Flash_Player/macromedia.com/support/flashplayer:
total 12
drwx------ 3 user user 4096 2010-10-02 10:31 .
drwx------ 3 user user 4096 2010-10-02 10:31 ..
drwx------ 5 user user 4096 2010-10-02 14:49 sys

./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys:
total 24
drwx------ 5 user user 4096 2010-10-02 14:49 .
drwx------ 3 user user 4096 2010-10-02 10:31 ..
drwx------ 2 user user 4096 2010-10-02 11:45 #kinksterbdsm.com
drwx------ 2 user user 4096 2010-10-02 14:49 #mail.google.com
-rw-r--r-- 1 user user  411 2010-10-02 14:49 settings.sol
drwx------ 2 user user 4096 2010-10-02 13:40 #s.ytimg.com

./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#kinksterbdsm.com:
total 12
drwx------ 2 user user 4096 2010-10-02 11:45 .
drwx------ 5 user user 4096 2010-10-02 14:49 ..
-rw-r--r-- 1 user user   86 2010-10-02 11:45 settings.sol

./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#mail.google.com:
total 12
drwx------ 2 user user 4096 2010-10-02 14:49 .
drwx------ 5 user user 4096 2010-10-02 14:49 ..
-rw-r--r-- 1 user user   85 2010-10-02 14:49 settings.sol

./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#s.ytimg.com:
total 12
drwx------ 2 user user 4096 2010-10-02 13:40 .
drwx------ 5 user user 4096 2010-10-02 14:49 ..
-rw-r--r-- 1 user user   81 2010-10-02 13:40 settings.sol

./.macromedia/Flash_Player/#SharedObjects:
total 12
drwx------ 3 user user 4096 2010-10-02 10:31 .
drwx------ 4 user user 4096 2010-10-02 10:31 ..
drwx------ 5 user user 4096 2010-10-02 14:49 MYVH3TB8

./.macromedia/Flash_Player/#SharedObjects/MYVH3TB8:
total 20
drwx------ 5 user user 4096 2010-10-02 14:49 .
drwx------ 3 user user 4096 2010-10-02 10:31 ..
drwx------ 2 user user 4096 2010-10-02 11:45 kinksterbdsm.com
drwx------ 2 user user 4096 2010-10-02 15:36 mail.google.com
drwx------ 2 user user 4096 2010-10-02 13:40 s.ytimg.com

./.macromedia/Flash_Player/#SharedObjects/MYVH3TB8/kinksterbdsm.com:
total 8
drwx------ 2 user user 4096 2010-10-02 11:45 .
drwx------ 5 user user 4096 2010-10-02 14:49 ..

./.macromedia/Flash_Player/#SharedObjects/MYVH3TB8/mail.google.com:
total 12
drwx------ 2 user user 4096 2010-10-02 15:36 .
drwx------ 5 user user 4096 2010-10-02 14:49 ..
-rw-r--r-- 1 user user   37 2010-10-02 15:36 wakeup.sol

./.macromedia/Flash_Player/#SharedObjects/MYVH3TB8/s.ytimg.com:
total 12
drwx------ 2 user user 4096 2010-10-02 13:40 .
drwx------ 5 user user 4096 2010-10-02 14:49 ..
-rw-r--r-- 1 user user   49 2010-10-02 13:40 soundData.sol

./.mozilla:
total 16
drwxrwxrwx  4 user user 4096 2010-10-02 07:55 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..
drwxrwxrwx  3 user user 4096 2010-10-02 07:55 extensions
drwxrwxrwx  4 user user 4096 2010-10-02 07:55 firefox

./.mozilla/extensions:
total 12
drwxrwxrwx 3 user user 4096 2010-10-02 07:55 .
drwxrwxrwx 4 user user 4096 2010-10-02 07:55 ..
drwxrwxrwx 2 user user 4096 2010-10-02 07:55 {ec8030f7-c20a-464f-9b0e-13a3a9e97384}

./.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}:
total 8
drwxrwxrwx 2 user user 4096 2010-10-02 07:55 .
drwxrwxrwx 3 user user 4096 2010-10-02 07:55 ..

./.mozilla/firefox:
total 20
drwxrwxrwx 4 user user 4096 2010-10-02 07:55 .
drwxrwxrwx 4 user user 4096 2010-10-02 07:55 ..
drwxrwxrwx 2 user user 4096 2010-10-02 07:55 Crash Reports
drwxrwxrwx 8 user user 4096 2010-10-02 15:47 fqwbqbb9.default
-rwxrwxrwx 1 user user   94 2010-10-02 07:55 profiles.ini

./.mozilla/firefox/Crash Reports:
total 12
drwxrwxrwx 2 user user 4096 2010-10-02 07:55 .
drwxrwxrwx 4 user user 4096 2010-10-02 07:55 ..
-rwxrwxrwx 1 user user   10 2010-10-02 07:55 InstallTime20100915180533

./.mozilla/firefox/fqwbqbb9.default:
total 42528
drwxrwxrwx 8 user user     4096 2010-10-02 15:47 .
drwxrwxrwx 4 user user     4096 2010-10-02 07:55 ..
drwxrwxrwx 2 user user     4096 2010-10-02 07:56 bookmarkbackups
-rwxrwxrwx 1 user user    20162 2010-10-02 07:55 bookmarks.html
drwxrwxrwx 2 user user    20480 2010-10-02 15:41 Cache
-rwxrwxrwx 1 user user    65536 2010-10-02 15:37 cert8.db
drwxrwxrwx 2 user user     4096 2010-10-02 07:55 chrome
-rwxrwxrwx 1 user user      165 2010-10-02 07:55 compatibility.ini
-rwxrwxrwx 1 user user   150328 2010-10-02 07:55 compreg.dat
-rwxrwxrwx 1 user user     7168 2010-10-02 07:55 content-prefs.sqlite
-rwxrwxrwx 1 user user    37888 2010-10-02 15:41 cookies.sqlite
-rw-r--r-- 1 user user     3608 2010-10-02 15:41 cookies.sqlite-journal
-rwxrwxrwx 1 user user     2048 2010-10-02 07:55 downloads.sqlite
drwxrwxrwx 2 user user     4096 2010-10-02 07:55 extensions
-rwxrwxrwx 1 user user      280 2010-10-02 07:55 extensions.cache
-rwxrwxrwx 1 user user      300 2010-10-02 07:55 extensions.ini
-rwxrwxrwx 1 user user     3121 2010-10-02 07:55 extensions.rdf
-rwxrwxrwx 1 user user     4096 2010-10-02 15:39 formhistory.sqlite
-rwxrwxrwx 1 user user    16384 2010-10-02 15:37 key3.db
-rwxr-xr-x 1 user user     3040 2010-10-02 15:37 localstore.rdf
lrwxrwxrwx 1 user user       15 2010-10-02 15:37 lock -> 127.0.1.1:+2008
-rwxrwxrwx 1 user user     3452 2010-10-02 07:55 mimeTypes.rdf
drwxrwxrwx 2 user user     4096 2010-10-02 07:55 minidumps
drwx------ 2 user user     4096 2010-10-02 15:37 OfflineCache
-rwxrwxrwx 1 user user        0 2010-10-02 15:37 .parentlock
-rwxrwxrwx 1 user user     2048 2010-10-02 07:55 permissions.sqlite
-rwxrwxrwx 1 user user   729088 2010-10-02 15:41 places.sqlite
-rwxrwxrwx 1 user user        0 2010-10-02 15:47 places.sqlite-journal
-rw------- 1 user user     6354 2010-10-02 15:36 pluginreg.dat
-rwxr-xr-x 1 user user     1793 2010-10-02 15:37 prefs.js
-rwxrwxrwx 1 user user    14565 2010-10-02 15:37 search.json
-rwxrwxrwx 1 user user     2048 2010-10-02 07:55 search.sqlite
-rwxrwxrwx 1 user user    16384 2010-10-02 07:55 secmod.db
-rw------- 1 user user     6473 2010-10-02 15:47 sessionstore.js
-rw-r--r-- 1 user user    11264 2010-10-02 15:36 signons.sqlite
-rwxrwxrwx 1 user user 38711296 2010-10-02 15:41 urlclassifier3.sqlite
-rw-r--r-- 1 user user      154 2010-10-02 15:37 urlclassifierkey3.txt
-rw-r--r-- 1 user user     3072 2010-10-02 11:06 webappsstore.sqlite
-rwxrwxrwx 1 user user  2258219 2010-10-02 09:48 XPC.mfasl
-rwxrwxrwx 1 user user   100530 2010-10-02 07:55 xpti.dat
-rwxrwxrwx 1 user user  1262010 2010-10-02 10:31 XUL.mfasl

./.mozilla/firefox/fqwbqbb9.default/bookmarkbackups:
total 16
drwxrwxrwx 2 user user 4096 2010-10-02 07:56 .
drwxrwxrwx 8 user user 4096 2010-10-02 15:47 ..
-rwxrwxrwx 1 user user 5495 2010-10-02 07:56 bookmarks-2010-10-02.json

./.mozilla/firefox/fqwbqbb9.default/Cache:
total 76432
drwxrwxrwx 2 user user    20480 2010-10-02 15:41 .
drwxrwxrwx 8 user user     4096 2010-10-02 15:47 ..
-rw------- 1 user user   221357 2010-10-02 12:07 002C4B22d01
-rw------- 1 user user    41450 2010-10-02 15:16 006149E5d01
-rw------- 1 user user    28033 2010-10-02 12:21 00ABB850d01
-rw------- 1 user user    76334 2010-10-02 13:53 00CDFA35d01
-rw------- 1 user user    91596 2010-10-02 14:07 01309BE2d01
-rw------- 1 user user    21342 2010-10-02 13:55 015C6E94d01
-rw------- 1 user user   104685 2010-10-02 14:30 029CF063d01
-rw------- 1 user user   142051 2010-10-02 13:48 02AE419Dd01
-rw------- 1 user user   137583 2010-10-02 12:07 02F54E2Dd01
-rw------- 1 user user    66487 2010-10-02 13:31 0403F861d01
-rw------- 1 user user    24566 2010-10-02 12:11 04BC9A07d01
-rw------- 1 user user    77076 2010-10-02 12:10 04E15534d01
-rw------- 1 user user    29519 2010-10-02 12:21 04F60991d01
-rw------- 1 user user    53572 2010-10-02 13:41 057DE26Ed01
-rw------- 1 user user    57228 2010-10-02 13:31 0723BD32d01
-rw------- 1 user user   112839 2010-10-02 15:09 07CBBC36d01
-rw------- 1 user user    32378 2010-10-02 12:21 095A2BAAd01
-rw------- 1 user user    61728 2010-10-02 13:31 0989C25Fd01
-rw------- 1 user user    22689 2010-10-02 14:45 0A138D66d01
-rw------- 1 user user    68268 2010-10-02 13:41 0A5F5261d01
-rw------- 1 user user    39174 2010-10-02 12:21 0A87DD07d01
-rw------- 1 user user    79201 2010-10-02 13:40 0ACCB7ECd01
-rw------- 1 user user    96178 2010-10-02 13:40 0B950260d01
-rw------- 1 user user    39971 2010-10-02 12:20 0CDD3905d01
-rw------- 1 user user    58834 2010-10-02 14:02 0CE41B1Cd01
-rw------- 1 user user    28330 2010-10-02 12:21 0D567970d01
-rw------- 1 user user    55825 2010-10-02 13:31 0DBF53B0d01
-rw------- 1 user user    66036 2010-10-02 15:32 0E1CDABBd01
-rw------- 1 user user   109345 2010-10-02 13:35 0E272A3Cd01
-rw------- 1 user user    17007 2010-10-02 12:13 0E5E60E7d01
-rw------- 1 user user    23868 2010-10-02 13:39 0EC4EC34d01
-rw------- 1 user user    22222 2010-10-02 13:31 0F13147Bd01
-rw------- 1 user user    84416 2010-10-02 14:02 1092165Ed01
-rw------- 1 user user    16761 2010-10-02 12:21 1092FF1Bd01
-rw------- 1 user user    39857 2010-10-02 12:16 10FB6B8Ad01
-rw------- 1 user user    18749 2010-10-02 13:56 111700B4d01
-rw------- 1 user user    27705 2010-10-02 15:21 124A5788d01
-rw------- 1 user user    99470 2010-10-02 14:12 12569B00d01
-rw------- 1 user user    59295 2010-10-02 13:31 1269A643d01
-rw------- 1 user user    46270 2010-10-02 14:02 13230CD2d01
-rw------- 1 user user    44341 2010-10-02 12:21 1331AE9Ed01
-rw------- 1 user user    42039 2010-10-02 12:05 1383716Dd01
-rw------- 1 user user    31574 2010-10-02 12:20 13E55C28d01
-rw------- 1 user user    47178 2010-10-02 13:31 1535AA1Ed01
-rw------- 1 user user    61662 2010-10-02 15:40 15507A27d01
-rw------- 1 user user    93335 2010-10-02 13:41 17B5D1F5d01
-rw------- 1 user user    44386 2010-10-02 13:31 1804C89Bd01
-rw------- 1 user user    34998 2010-10-02 12:20 18CB8097d01
-rw------- 1 user user  4039102 2010-10-02 12:08 19678FFAd01
-rw------- 1 user user   130318 2010-10-02 15:36 199624CEd01
-rw------- 1 user user    46014 2010-10-02 13:31 1A04E132d01
-rw------- 1 user user    38014 2010-10-02 12:21 1A3D176Ed01
-rw------- 1 user user    32572 2010-10-02 12:21 1A4EB685d01
-rw------- 1 user user    63689 2010-10-02 14:02 1A57B783d01
-rw------- 1 user user    31754 2010-10-02 12:20 1B47AC66d01
-rw------- 1 user user   131220 2010-10-02 14:02 1BB0A684d01
-rw------- 1 user user   144559 2010-10-02 12:06 1BDBAC46d01
-rw------- 1 user user    21541 2010-10-02 13:45 1C17E65Ad01
-rw------- 1 user user    30289 2010-10-02 12:20 1C963776d01
-rw------- 1 user user   142740 2010-10-02 13:40 1C98DC14d01
-rw------- 1 user user    67952 2010-10-02 14:57 1CA0BFB3d01
-rw------- 1 user user    28892 2010-10-02 13:41 1CF58758d01
-rw------- 1 user user    99016 2010-10-02 13:53 1CF7A1EDd01
-rw------- 1 user user    17167 2010-10-02 13:56 1D878FF1d01
-rw------- 1 user user    40838 2010-10-02 12:21 1D952533d01
-rw------- 1 user user    31975 2010-10-02 12:20 1DE3D394d01
-rw------- 1 user user    39340 2010-10-02 12:20 1E0E8DCDd01
-rw------- 1 user user    28962 2010-10-02 15:16 1E47F2B5d01
-rw------- 1 user user    31048 2010-10-02 13:31 1E8846A5d01
-rw------- 1 user user    18925 2010-10-02 13:35 1ECC7CA3d01
-rw------- 1 user user    24651 2010-10-02 13:35 1F31FAFFd01
-rw------- 1 user user    37629 2010-10-02 12:20 1FA37DDCd01
-rw------- 1 user user    28111 2010-10-02 12:21 1FDC870Ed01
-rw------- 1 user user    49286 2010-10-02 15:16 201DD0F1d01
-rw------- 1 user user    42836 2010-10-02 13:31 20F1FA06d01
-rw------- 1 user user    20595 2010-10-02 13:40 225E97D1d01
-rw------- 1 user user    39059 2010-10-02 12:02 23DFCF43d01
-rw------- 1 user user    18273 2010-10-02 14:02 243538C3d01
-rw------- 1 user user    21441 2010-10-02 13:40 243F7BB7d01
-rw------- 1 user user    39746 2010-10-02 12:21 25F31894d01
-rw------- 1 user user    31100 2010-10-02 13:27 26753C1Fd01
-rw------- 1 user user    18335 2010-10-02 13:40 27BB73A5d01
-rw------- 1 user user    41866 2010-10-02 12:21 28D2B131d01
-rw------- 1 user user    18857 2010-10-02 13:40 28D737D1d01
-rw------- 1 user user    48393 2010-10-02 13:31 296D833Cd01
-rw------- 1 user user    16730 2010-10-02 14:28 298C0E14d01
-rw------- 1 user user    20820 2010-10-02 12:06 2A6563D7d01
-rw------- 1 user user    35467 2010-10-02 12:20 2A6921E5d01
-rw------- 1 user user    29379 2010-10-02 15:36 2B16A27Cd01
-rw------- 1 user user   100573 2010-10-02 13:45 2B2E9E7Fd01
-rw------- 1 user user    41615 2010-10-02 13:31 2B3BB4B8d01
-rw------- 1 user user    30641 2010-10-02 12:21 2B5A920Bd01
-rw------- 1 user user    26280 2010-10-02 13:31 2C315E21d01
-rw------- 1 user user    55384 2010-10-02 13:40 2D20F5D4d01
-rw------- 1 user user    60880 2010-10-02 12:21 2D540C9Cd01
-rw------- 1 user user    30660 2010-10-02 13:31 2D590C08d01
-rw------- 1 user user    63933 2010-10-02 12:20 2E262A87d01
-rw------- 1 user user    32761 2010-10-02 15:36 2E2C9909d01
-rw------- 1 user user    17246 2010-10-02 13:44 2F9D5321d01
-rw------- 1 user user    29921 2010-10-02 12:20 2FFB3CDFd01
-rw------- 1 user user    29246 2010-10-02 13:40 31AA2953d01
-rw------- 1 user user    39299 2010-10-02 12:13 3215A656d01
-rw------- 1 user user    36811 2010-10-02 12:20 32B1C6A0d01
-rw------- 1 user user    24019 2010-10-02 13:27 32DCE786d01
-rw------- 1 user user    30798 2010-10-02 13:32 3315E42Ed01
-rw------- 1 user user    64776 2010-10-02 15:21 340DFDD3d01
-rw------- 1 user user    53624 2010-10-02 13:35 3424DA53d01
-rw------- 1 user user    27365 2010-10-02 12:06 343F5471d01
-rw------- 1 user user    26027 2010-10-02 15:41 354CCC4Cd01
-rw------- 1 user user    22802 2010-10-02 13:45 3651E152d01
-rw------- 1 user user    32832 2010-10-02 12:20 376A1767d01
-rw------- 1 user user    47078 2010-10-02 12:06 37EB338Cd01
-rw------- 1 user user   115919 2010-10-02 12:11 38101A5Fd01
-rw------- 1 user user    52315 2010-10-02 13:31 384AC663d01
-rw------- 1 user user    19389 2010-10-02 12:18 3884892Cd01
-rw------- 1 user user    42358 2010-10-02 14:07 38BB0F3Fd01
-rw------- 1 user user    27513 2010-10-02 14:02 3955DA23d01
-rw------- 1 user user    57236 2010-10-02 14:02 3ABBD051d01
-rw------- 1 user user    26441 2010-10-02 14:07 3B35E437d01
-rw------- 1 user user    29683 2010-10-02 14:02 3B3DB7C3d01
-rw------- 1 user user    20746 2010-10-02 13:29 3B928E20d01
-rw------- 1 user user    60306 2010-10-02 13:31 3BA047CCd01
-rw------- 1 user user    73218 2010-10-02 13:31 3C85F154d01
-rw------- 1 user user    41625 2010-10-02 13:29 3C973C30d01
-rw------- 1 user user    47127 2010-10-02 13:31 3D01A492d01
-rw------- 1 user user    20769 2010-10-02 14:02 3E5BC95Ed01
-rw------- 1 user user    33107 2010-10-02 12:20 40314621d01
-rw------- 1 user user    41781 2010-10-02 13:31 408227FAd01
-rw------- 1 user user    33707 2010-10-02 12:20 40F47622d01
-rw------- 1 user user    74917 2010-10-02 15:36 410F3452d01
-rw------- 1 user user   104696 2010-10-02 14:07 415E9B34d01
-rw------- 1 user user    36412 2010-10-02 12:22 419712A3d01
-rw------- 1 user user    23863 2010-10-02 13:27 41AEF0FFd01
-rw------- 1 user user    25584 2010-10-02 12:21 41C5AC92d01
-rw------- 1 user user    62623 2010-10-02 13:41 41F28D76d01
-rw------- 1 user user    77319 2010-10-02 13:32 433F142Bd01
-rw------- 1 user user   100970 2010-10-02 12:06 436793DEd01
-rw------- 1 user user    79273 2010-10-02 14:02 44035123d01
-rw------- 1 user user    98520 2010-10-02 14:28 443205C6d01
-rw------- 1 user user    23787 2010-10-02 13:31 445BFFEFd01
-rw------- 1 user user    26522 2010-10-02 12:20 4507E86Ad01
-rw------- 1 user user    23433 2010-10-02 12:05 45C9067Bd01
-rw------- 1 user user    19818 2010-10-02 13:39 4670B591d01
-rw------- 1 user user    40623 2010-10-02 13:41 4693C799d01
-rw------- 1 user user    45505 2010-10-02 14:02 475B64ADd01
-rw------- 1 user user    31330 2010-10-02 14:02 486C42EAd01
-rw------- 1 user user    21990 2010-10-02 12:22 48816D2Ad01
-rw------- 1 user user    30796 2010-10-02 12:20 489C3773d01
-rw------- 1 user user    28489 2010-10-02 13:41 48E3FD1Ed01
-rw------- 1 user user    21218 2010-10-02 13:32 4960E803d01
-rw------- 1 user user    29591 2010-10-02 12:20 498F892Dd01
-rw------- 1 user user    50527 2010-10-02 13:31 4A056F84d01
-rw------- 1 user user    26529 2010-10-02 12:21 4A73AEB1d01
-rw------- 1 user user    19579 2010-10-02 14:00 4ABF7121d01
-rw------- 1 user user   144822 2010-10-02 14:02 4B6898D2d01
-rw------- 1 user user    28994 2010-10-02 12:21 4B6A5099d01
-rw------- 1 user user   155808 2010-10-02 13:41 4C4C6083d01
-rw------- 1 user user   156692 2010-10-02 12:07 4C7B7283d01
-rw------- 1 user user   144822 2010-10-02 13:41 4D6D7EADd01
-rw------- 1 user user    22645 2010-10-02 13:28 4D7AF038d01
-rw------- 1 user user    49872 2010-10-02 13:40 4D90747Bd01
-rw------- 1 user user    23568 2010-10-02 14:07 4E7F19B7d01
-rw------- 1 user user    41006 2010-10-02 13:31 4EECBCF0d01
-rw------- 1 user user    16718 2010-10-02 15:33 4F0444FAd01
-rw------- 1 user user    17278 2010-10-02 13:41 4F3D3E5Dd01
-rw------- 1 user user    26027 2010-10-02 13:45 4F5A9E5Fd01
-rw------- 1 user user    61831 2010-10-02 14:13 4F97BD03d01
-rw------- 1 user user    37318 2010-10-02 13:40 4FB2CAFFd01
-rw------- 1 user user    47603 2010-10-02 12:13 4FC5FB79d01
-rw------- 1 user user    91483 2010-10-02 14:07 4FE3552Dd01
-rw------- 1 user user    41871 2010-10-02 12:21 508713F6d01
-rw------- 1 user user    27596 2010-10-02 12:06 51BFEA3Bd01
-rw------- 1 user user    19777 2010-10-02 15:17 52D4E476d01
-rw------- 1 user user    16624 2010-10-02 13:28 53212F44d01
-rw------- 1 user user    33687 2010-10-02 12:20 534A2C5Ed01
-rw------- 1 user user    66882 2010-10-02 14:49 5353387Bd01
-rw------- 1 user user    31952 2010-10-02 12:21 5381D184d01
-rw------- 1 user user    59966 2010-10-02 13:32 5394E0EFd01
-rw------- 1 user user    36631 2010-10-02 13:39 539A3536d01
-rw------- 1 user user    37460 2010-10-02 14:07 53AF7F45d01
-rw------- 1 user user    34675 2010-10-02 12:14 54593247d01
-rw------- 1 user user    70870 2010-10-02 13:31 55AAE6A6d01
-rw------- 1 user user    32807 2010-10-02 12:21 55CB8D5Bd01
-rw------- 1 user user    34373 2010-10-02 13:35 56AC1786d01
-rw------- 1 user user    89216 2010-10-02 13:40 56BD01AEd01
-rw------- 1 user user    63376 2010-10-02 14:29 56CE9EC8d01
-rw------- 1 user user    63834 2010-10-02 13:31 5774755Cd01
-rw------- 1 user user    35901 2010-10-02 12:20 5780D14Bd01
-rw------- 1 user user    16903 2010-10-02 12:18 583B50E7d01
-rw------- 1 user user    18638 2010-10-02 13:35 59478AC8d01
-rw------- 1 user user    29410 2010-10-02 12:21 59C6A0E7d01
-rw------- 1 user user    41938 2010-10-02 13:31 59ECF6F6d01
-rw------- 1 user user    22039 2010-10-02 13:28 5A908FCDd01
-rw------- 1 user user    97793 2010-10-02 12:07 5AAB619Ed01
-rw------- 1 user user    24750 2010-10-02 15:21 5ACA4C75d01
-rw------- 1 user user    48011 2010-10-02 13:31 5ACC3A1Ed01
-rw------- 1 user user    30927 2010-10-02 12:21 5B170568d01
-rw------- 1 user user    30475 2010-10-02 12:11 5B57537Bd01
-rw------- 1 user user    48914 2010-10-02 12:10 5CBC8D23d01
-rw------- 1 user user    33396 2010-10-02 12:16 5D0B97A8d01
-rw------- 1 user user   121097 2010-10-02 13:45 5D5A476Bd01
-rw------- 1 user user    68632 2010-10-02 14:02 5D847539d01
-rw------- 1 user user    35312 2010-10-02 12:21 5E3DAF12d01
-rw------- 1 user user    17117 2010-10-02 12:16 5E7963F4d01
-rw------- 1 user user    26603 2010-10-02 12:06 5ECECFAFd01
-rw------- 1 user user    17688 2010-10-02 12:18 5ED30E7Cd01
-rw------- 1 user user    32946 2010-10-02 12:21 5ED50EDDd01
-rw------- 1 user user   137024 2010-10-02 15:21 5F6818A4d01
-rw------- 1 user user    17096 2010-10-02 12:05 5FD01086d01
-rw------- 1 user user    38163 2010-10-02 12:20 5FFCC9DBd01
-rw------- 1 user user    25057 2010-10-02 13:27 60BFC871d01
-rw------- 1 user user    31629 2010-10-02 13:29 61080AF2d01
-rw------- 1 user user    19747 2010-10-02 14:02 623F2F91d01
-rw------- 1 user user    63249 2010-10-02 12:17 6330AF4Dd01
-rw------- 1 user user    21471 2010-10-02 13:40 639C09A4d01
-rw------- 1 user user    29098 2010-10-02 12:21 63B817D7d01
-rw------- 1 user user    36628 2010-10-02 13:27 63EA828Dd01
-rw------- 1 user user    39978 2010-10-02 12:22 6405DCAAd01
-rw------- 1 user user    50893 2010-10-02 12:20 6440B796d01
-rw------- 1 user user    60298 2010-10-02 12:12 65185C5Cd01
-rw------- 1 user user    99016 2010-10-02 13:53 66073A0Ad01
-rw------- 1 user user    27158 2010-10-02 12:20 6649C3A7d01
-rw------- 1 user user    34573 2010-10-02 12:21 66F5F93Ad01
-rw------- 1 user user    46978 2010-10-02 13:31 67F842FEd01
-rw------- 1 user user    59205 2010-10-02 13:40 68860279d01
-rw------- 1 user user    17199 2010-10-02 12:12 69230C31d01
-rw------- 1 user user    26013 2010-10-02 13:31 695A51C2d01
-rw------- 1 user user    58800 2010-10-02 12:20 697783E7d01
-rw------- 1 user user    18311 2010-10-02 13:31 69981EE4d01
-rw------- 1 user user    57588 2010-10-02 12:21 69D22D08d01
-rw------- 1 user user    22134 2010-10-02 13:39 6A6D1262d01
-rw------- 1 user user    49010 2010-10-02 13:32 6AFF0D24d01
-rw------- 1 user user    48012 2010-10-02 13:32 6C0566C0d01
-rw------- 1 user user    51365 2010-10-02 13:31 6C66B166d01
-rw------- 1 user user    33662 2010-10-02 12:16 6D62F873d01
-rw------- 1 user user   116593 2010-10-02 14:49 6D6F432Dd01
-rw------- 1 user user    17759 2010-10-02 13:28 6D7F0DFBd01
-rw------- 1 user user    40120 2010-10-02 15:21 6DD935A0d01
-rw------- 1 user user    46813 2010-10-02 14:02 6E067CA5d01
-rw------- 1 user user    32399 2010-10-02 12:21 6E847EDDd01
-rw------- 1 user user    30028 2010-10-02 12:20 6F9ABDD6d01
-rw------- 1 user user    28342 2010-10-02 13:39 6FA254ACd01
-rw------- 1 user user    65490 2010-10-02 13:31 709104C6d01
-rw------- 1 user user    21703 2010-10-02 15:21 710F0F7Cd01
-rw------- 1 user user    64167 2010-10-02 13:31 71119C6Dd01
-rw------- 1 user user    83476 2010-10-02 13:58 71639230d01
-rw------- 1 user user    36084 2010-10-02 12:21 71B8040Bd01
-rw------- 1 user user    32981 2010-10-02 12:20 7277F406d01
-rw------- 1 user user   253177 2010-10-02 14:07 7355AAD0d01
-rw------- 1 user user    42041 2010-10-02 13:40 73F9FDBFd01
-rw------- 1 user user    61659 2010-10-02 15:36 746219B1d01
-rw------- 1 user user    52445 2010-10-02 13:31 750091ECd01
-rw------- 1 user user    46602 2010-10-02 12:13 751D2FFFd01
-rw------- 1 user user    97724 2010-10-02 14:07 7525D83Bd01
-rw------- 1 user user    38394 2010-10-02 12:21 752DC90Fd01
-rw------- 1 user user    47926 2010-10-02 13:31 755E50C4d01
-rw------- 1 user user   115946 2010-10-02 14:02 75687977d01
-rw------- 1 user user    26038 2010-10-02 14:07 75FD3988d01
-rw------- 1 user user   322678 2010-10-02 14:49 7618DC5Cd01
-rw------- 1 user user    58842 2010-10-02 14:02 76DCFD96d01
-rw------- 1 user user    18553 2010-10-02 13:53 7786C4EBd01
-rw------- 1 user user    34892 2010-10-02 12:20 77A73072d01
-rw------- 1 user user    38525 2010-10-02 13:32 786DF829d01
-rw------- 1 user user    52664 2010-10-02 12:20 791A9D5Dd01
-rw------- 1 user user    58383 2010-10-02 13:32 7957E5E0d01
-rw------- 1 user user    34996 2010-10-02 13:40 7974CC2Dd01
-rw------- 1 user user    28410 2010-10-02 14:07 79CD0500d01
-rw------- 1 user user    40076 2010-10-02 12:20 7A1C72A0d01
-rw------- 1 user user    28926 2010-10-02 12:21 7A85A135d01
-rw------- 1 user user    30679 2010-10-02 13:40 7B51912Bd01
-rw------- 1 user user    99398 2010-10-02 14:02 7B9A817Fd01
-rw------- 1 user user    17601 2010-10-02 12:15 7B9E7CC8d01
-rw------- 1 user user    88702 2010-10-02 12:06 7BD42310d01
-rw------- 1 user user   190789 2010-10-02 13:41 7C19E01Fd01
-rw------- 1 user user    69968 2010-10-02 13:28 7C9E3BD7d01
-rw------- 1 user user    28677 2010-10-02 12:21 7D54D2C9d01
-rw------- 1 user user    43603 2010-10-02 14:49 7EF31CC5d01
-rw------- 1 user user    50244 2010-10-02 12:07 7F95F45Bd01
-rw------- 1 user user    54406 2010-10-02 13:28 7FBF5343d01
-rw------- 1 user user    30298 2010-10-02 13:40 7FE44277d01
-rw------- 1 user user   261118 2010-10-02 15:34 8042E759d01
-rw------- 1 user user    17707 2010-10-02 12:22 80DFEE86d01
-rw------- 1 user user   221493 2010-10-02 13:40 81018F4Cd01
-rw------- 1 user user    49051 2010-10-02 14:02 8101E5C9d01
-rw------- 1 user user   116517 2010-10-02 12:06 81902340d01
-rw------- 1 user user    43808 2010-10-02 12:20 824F4275d01
-rw------- 1 user user    22491 2010-10-02 13:40 82595C10d01
-rw------- 1 user user    26013 2010-10-02 13:27 826634F5d01
-rw------- 1 user user    81615 2010-10-02 13:41 82B163CFd01
-rw------- 1 user user    72194 2010-10-02 15:17 82CA093Ad01
-rw------- 1 user user   116593 2010-10-02 15:36 843EB828d01
-rw------- 1 user user   145254 2010-10-02 13:40 84925457d01
-rw------- 1 user user    24041 2010-10-02 13:29 8599905Ed01
-rw------- 1 user user    35885 2010-10-02 12:20 85B1E717d01
-rw------- 1 user user    25043 2010-10-02 13:27 86518862d01
-rw------- 1 user user    24748 2010-10-02 12:21 871B5F5Fd01
-rw------- 1 user user    45842 2010-10-02 14:02 892A1506d01
-rw------- 1 user user    34007 2010-10-02 14:02 89BD877Fd01
-rw------- 1 user user    88043 2010-10-02 12:06 8AC35629d01
-rw------- 1 user user   126979 2010-10-02 13:45 8AFDC023d01
-rw------- 1 user user    27944 2010-10-02 13:40 8B3D9668d01
-rw------- 1 user user    25527 2010-10-02 14:02 8B41D9EEd01
-rw------- 1 user user    21547 2010-10-02 13:40 8B51692Ad01
-rw------- 1 user user    29847 2010-10-02 12:14 8C2E15ABd01
-rw------- 1 user user    43964 2010-10-02 12:07 8C88EA0Cd01
-rw------- 1 user user    28246 2010-10-02 12:21 8DFE311Bd01
-rw------- 1 user user    31379 2010-10-02 13:31 8EB734ECd01
-rw------- 1 user user    37499 2010-10-02 12:12 8F38FEBBd01
-rw------- 1 user user    22502 2010-10-02 12:13 8F76B800d01
-rw------- 1 user user   118527 2010-10-02 14:55 8F88E57Bd01
-rw------- 1 user user   222429 2010-10-02 13:32 8FC332FDd01
-rw------- 1 user user    56163 2010-10-02 13:31 8FE7AB21d01
-rw------- 1 user user   139890 2010-10-02 12:07 902A2915d01
-rw------- 1 user user    43919 2010-10-02 12:20 9031B398d01
-rw------- 1 user user    83536 2010-10-02 12:22 915B81C6d01
-rw------- 1 user user   471821 2010-10-02 13:29 91CC5F7Fd01
-rw------- 1 user user    29243 2010-10-02 12:21 928E22CFd01
-rw------- 1 user user    36301 2010-10-02 13:48 92B5039Ad01
-rw------- 1 user user   134384 2010-10-02 13:45 92FC9A33d01
-rw------- 1 user user    36665 2010-10-02 13:40 930F2B86d01
-rw------- 1 user user    30754 2010-10-02 12:20 932FC3B5d01
-rw------- 1 user user    26209 2010-10-02 12:10 949C23B5d01
-rw------- 1 user user    29090 2010-10-02 12:20 94D69712d01
-rw------- 1 user user    36564 2010-10-02 13:35 956E329Bd01
-rw------- 1 user user   123472 2010-10-02 14:02 9574FEE9d01
-rw------- 1 user user    41000 2010-10-02 13:40 95ECF2FFd01
-rw------- 1 user user    22580 2010-10-02 13:45 961C5C76d01
-rw------- 1 user user    30545 2010-10-02 12:20 965A3AD5d01
-rw------- 1 user user    52674 2010-10-02 12:20 9740CAB1d01
-rw------- 1 user user    45678 2010-10-02 13:41 9750A5C7d01
-rw------- 1 user user    28142 2010-10-02 12:20 977C5A60d01
-rw------- 1 user user    52997 2010-10-02 12:20 97BA512Ad01
-rw------- 1 user user    43266 2010-10-02 13:35 98E5551Cd01
-rw------- 1 user user    25281 2010-10-02 13:40 99742818d01
-rw------- 1 user user    19947 2010-10-02 12:22 9996009Ed01
-rw------- 1 user user    29379 2010-10-02 14:49 9A5AA62Ed01
-rw------- 1 user user    69573 2010-10-02 14:02 9AC72103d01
-rw------- 1 user user    23339 2010-10-02 12:16 9AD1E249d01
-rw------- 1 user user    52596 2010-10-02 13:31 9BC45843d01
-rw------- 1 user user    88784 2010-10-02 13:40 9BC8AB14d01
-rw------- 1 user user    32962 2010-10-02 13:41 9C3960DBd01
-rw------- 1 user user    69260 2010-10-02 13:45 9CCC128Ad01
-rw------- 1 user user    27021 2010-10-02 12:21 9CD1408Fd01
-rw------- 1 user user    30825 2010-10-02 12:21 9D46BE76d01
-rw------- 1 user user    32197 2010-10-02 12:21 9D6A9BC0d01
-rw------- 1 user user    28172 2010-10-02 12:21 9DCE7C62d01
-rw------- 1 user user    23535 2010-10-02 11:52 9E212985d01
-rw------- 1 user user    81496 2010-10-02 13:40 9E753A78d01
-rw------- 1 user user    21101 2010-10-02 13:31 9FAAAA32d01
-rw------- 1 user user    39342 2010-10-02 13:28 9FEFC387d01
-rw------- 1 user user   130318 2010-10-02 14:49 A154E1F3d01
-rw------- 1 user user   138439 2010-10-02 15:40 A2C0270Ad01
-rw------- 1 user user    40664 2010-10-02 13:31 A3DDFCB7d01
-rw------- 1 user user   171029 2010-10-02 12:07 A562F3CCd01
-rw------- 1 user user    28747 2010-10-02 12:06 A57091FCd01
-rw------- 1 user user    51495 2010-10-02 13:45 A5A7F9DDd01
-rw------- 1 user user    43367 2010-10-02 12:21 A5D7A5ABd01
-rw------- 1 user user    35164 2010-10-02 12:21 A5E1D2BEd01
-rw------- 1 user user    36691 2010-10-02 12:20 A5E5BEA5d01
-rw------- 1 user user    22406 2010-10-02 12:11 A61D919Dd01
-rw------- 1 user user   323456 2010-10-02 14:28 A6F75BC1d01
-rw------- 1 user user   125036 2010-10-02 14:07 A72A3ADAd01
-rw------- 1 user user    49842 2010-10-02 12:22 A72FDA5Cd01
-rw------- 1 user user    22299 2010-10-02 12:13 A73639CDd01
-rw------- 1 user user    25747 2010-10-02 12:21 A73BA5B0d01
-rw------- 1 user user    27540 2010-10-02 11:59 A7531EE3d01
-rw------- 1 user user    38104 2010-10-02 15:16 A816E992d01
-rw------- 1 user user    21147 2010-10-02 13:40 A83FC718d01
-rw------- 1 user user    57254 2010-10-02 13:27 A85323DEd01
-rw------- 1 user user    46434 2010-10-02 12:11 A876F39Fd01
-rw------- 1 user user    33810 2010-10-02 12:21 A9C7CAECd01
-rw------- 1 user user    48008 2010-10-02 12:13 A9F2893Dd01
-rw------- 1 user user    24458 2010-10-02 14:55 AB357174d01
-rw------- 1 user user    24818 2010-10-02 13:40 AC2A8605d01
-rw------- 1 user user    30642 2010-10-02 13:45 AC4468B5d01
-rw------- 1 user user    24870 2010-10-02 13:41 ACA7A197d01
-rw------- 1 user user    72166 2010-10-02 13:41 AD02CA10d01
-rw------- 1 user user    33942 2010-10-02 12:21 AD6E82E9d01
-rw------- 1 user user    33283 2010-10-02 13:31 ADEDD326d01
-rw------- 1 user user   172502 2010-10-02 13:31 AF054435d01
-rw------- 1 user user    32761 2010-10-02 14:49 AF22BE40d01
-rw------- 1 user user    28173 2010-10-02 14:07 AFCADA84d01
-rw------- 1 user user    34283 2010-10-02 12:21 AFE62248d01
-rw------- 1 user user    28117 2010-10-02 12:21 B0361AD9d01
-rw------- 1 user user    49925 2010-10-02 14:02 B0AF7B54d01
-rw------- 1 user user    56339 2010-10-02 12:21 B0EB14A0d01
-rw------- 1 user user    97874 2010-10-02 13:32 B12475B9d01
-rw------- 1 user user    19955 2010-10-02 12:21 B1D96FB0d01
-rw------- 1 user user    28166 2010-10-02 14:02 B23F47DAd01
-rw------- 1 user user   102842 2010-10-02 14:07 B2D09AABd01
-rw------- 1 user user    35201 2010-10-02 12:21 B3A15BC6d01
-rw------- 1 user user    91051 2010-10-02 13:41 B3A3E5BBd01
-rw------- 1 user user    28012 2010-10-02 13:50 B3B839B0d01
-rw------- 1 user user    30270 2010-10-02 12:20 B4BDAC88d01
-rw------- 1 user user    43574 2010-10-02 15:36 B4E7AA40d01
-rw------- 1 user user    83448 2010-10-02 14:02 B4FEB7EAd01
-rw------- 1 user user    41691 2010-10-02 12:22 B5040D6Ad01
-rw------- 1 user user    67749 2010-10-02 13:45 B51BF62Ed01
-rw------- 1 user user    26027 2010-10-02 13:29 B56D3F9Dd01
-rw------- 1 user user    35419 2010-10-02 12:20 B6B25DB8d01
-rw------- 1 user user   112553 2010-10-02 13:45 B77936ECd01
-rw------- 1 user user    33932 2010-10-02 12:11 B787D646d01
-rw------- 1 user user    30300 2010-10-02 13:31 B7E5D074d01
-rw------- 1 user user    51827 2010-10-02 12:20 B8F26C63d01
-rw------- 1 user user    27670 2010-10-02 12:21 B9440284d01
-rw------- 1 user user    69442 2010-10-02 12:21 BA5581ACd01
-rw------- 1 user user   100066 2010-10-02 14:07 BA56A4C5d01
-rw------- 1 user user    41573 2010-10-02 12:20 BBBE9FC9d01
-rw------- 1 user user    29729 2010-10-02 12:05 BC5CB955d01
-rw------- 1 user user    44926 2010-10-02 12:07 BCA86A9Fd01
-rw------- 1 user user    24000 2010-10-02 12:06 BCACA8A8d01
-rw------- 1 user user    34361 2010-10-02 13:40 BCEB7622d01
-rw------- 1 user user    66882 2010-10-02 15:36 BD6551F1d01
-rw------- 1 user user    30425 2010-10-02 12:20 BE9077A7d01
-rw------- 1 user user    47848 2010-10-02 13:41 BE9A0064d01
-rw------- 1 user user    18951 2010-10-02 12:05 BEF5A41Ed01
-rw------- 1 user user    51894 2010-10-02 13:40 BF9455C1d01
-rw------- 1 user user   125718 2010-10-02 15:40 BFC2FE10d01
-rw------- 1 user user    50689 2010-10-02 13:45 BFCD3738d01
-rw------- 1 user user    46583 2010-10-02 14:07 C0618009d01
-rw------- 1 user user    31835 2010-10-02 12:21 C063EBB9d01
-rw------- 1 user user    33067 2010-10-02 12:20 C103F483d01
-rw------- 1 user user    29839 2010-10-02 14:07 C118A401d01
-rw------- 1 user user    23615 2010-10-02 13:41 C13180C3d01
-rw------- 1 user user    29306 2010-10-02 12:20 C1B4E96Dd01
-rw------- 1 user user    38241 2010-10-02 12:20 C203B59Ad01
-rw------- 1 user user    17445 2010-10-02 12:22 C21FC335d01
-rw------- 1 user user    16581 2010-10-02 12:18 C24AB8F3d01
-rw------- 1 user user    20574 2010-10-02 12:22 C2715027d01
-rw------- 1 user user    21272 2010-10-02 12:16 C30D690Ed01
-rw------- 1 user user   124530 2010-10-02 13:28 C33A83B4d01
-rw------- 1 user user    63270 2010-10-02 14:57 C3F8B0FBd01
-rw------- 1 user user    54670 2010-10-02 12:21 C4CB1C46d01
-rw------- 1 user user    24450 2010-10-02 12:21 C5514110d01
-rw------- 1 user user    54047 2010-10-02 13:31 C5A94B3Bd01
-rw------- 1 user user    35686 2010-10-02 14:02 C5B5DBD5d01
-rw------- 1 user user    66535 2010-10-02 13:31 C70B0D19d01
-rw------- 1 user user   124223 2010-10-02 13:35 C80C78A8d01
-rw------- 1 user user    30513 2010-10-02 12:21 C8684866d01
-rw------- 1 user user   144217 2010-10-02 14:01 C8780E93d01
-rw------- 1 user user    31177 2010-10-02 13:31 C8CA8D30d01
-rw------- 1 user user    26272 2010-10-02 13:40 C91B825Ed01
-rw------- 1 user user    48047 2010-10-02 12:13 C91D2AFDd01
-rw------- 1 user user    55381 2010-10-02 14:07 C930BF80d01
-rw------- 1 user user   133968 2010-10-02 14:07 C9AE2255d01
-rw------- 1 user user    31873 2010-10-02 12:21 C9BFDFD4d01
-rw------- 1 user user    99115 2010-10-02 12:15 C9C43A4Bd01
-rwxrwxrwx 1 user user  2428310 2010-10-02 15:46 _CACHE_001_
-rwxrwxrwx 1 user user  1273932 2010-10-02 15:40 _CACHE_002_
-rwxrwxrwx 1 user user 38491767 2010-10-02 15:41 _CACHE_003_
-rwxrwxrwx 1 user user   131348 2010-10-02 15:37 _CACHE_MAP_
-rw------- 1 user user    53032 2010-10-02 12:21 CB19B858d01
-rw------- 1 user user    31636 2010-10-02 12:20 CB446E2Bd01
-rw------- 1 user user    18350 2010-10-02 13:40 CB5F61E8d01
-rw------- 1 user user    31225 2010-10-02 12:21 CBE5E9FBd01
-rw------- 1 user user    31477 2010-10-02 12:20 CBEA8B53d01
-rw------- 1 user user    30091 2010-10-02 12:21 CBF44CD1d01
-rw------- 1 user user    99982 2010-10-02 14:55 CC4746D1d01
-rw------- 1 user user    25075 2010-10-02 12:20 CC7F254Fd01
-rw------- 1 user user   174118 2010-10-02 13:31 CCF9B272d01
-rw------- 1 user user    34534 2010-10-02 15:21 CD4FF089d01
-rw------- 1 user user    17054 2010-10-02 13:41 CD62E70Bd01
-rw------- 1 user user   115881 2010-10-02 12:06 CDDBA70Fd01
-rw------- 1 user user    62143 2010-10-02 14:07 CE5BAC21d01
-rw------- 1 user user    28456 2010-10-02 14:01 CEBF17D1d01
-rw------- 1 user user    27860 2010-10-02 12:12 CEEF1936d01
-rw------- 1 user user   341938 2010-10-02 12:16 D0F7AC8Bd01
-rw------- 1 user user    25783 2010-10-02 12:21 D0F884B8d01
-rw------- 1 user user    61444 2010-10-02 13:32 D11CC670d01
-rw------- 1 user user    47098 2010-10-02 14:07 D1406FAAd01
-rw------- 1 user user    30804 2010-10-02 12:21 D143C335d01
-rw------- 1 user user    65311 2010-10-02 13:32 D1DBC096d01
-rw------- 1 user user    52965 2010-10-02 13:32 D257A44Cd01
-rw------- 1 user user    19135 2010-10-02 14:02 D275931Cd01
-rw------- 1 user user    31539 2010-10-02 12:21 D283BA86d01
-rw------- 1 user user    55087 2010-10-02 13:29 D2D9F2A1d01
-rw------- 1 user user    35725 2010-10-02 13:28 D2E04DC4d01
-rw------- 1 user user    28411 2010-10-02 12:21 D3A3D4E6d01
-rw------- 1 user user    56099 2010-10-02 13:31 D3AD4676d01
-rw------- 1 user user    74606 2010-10-02 13:27 D3B7ED2Ad01
-rw------- 1 user user    32048 2010-10-02 12:20 D3EF054Fd01
-rw------- 1 user user    23854 2010-10-02 14:02 D451E477d01
-rw------- 1 user user    29678 2010-10-02 12:21 D46485CBd01
-rw------- 1 user user    68114 2010-10-02 13:32 D504B4ABd01
-rw------- 1 user user   164062 2010-10-02 12:06 D722BFCAd01
-rw------- 1 user user   128672 2010-10-02 12:17 D72F4CAFd01
-rw------- 1 user user    34472 2010-10-02 12:20 D761D1E8d01
-rw------- 1 user user    52980 2010-10-02 12:20 D7B72F98d01
-rw------- 1 user user    51799 2010-10-02 13:31 D818DC54d01
-rw------- 1 user user    66432 2010-10-02 12:20 D85E8727d01
-rw------- 1 user user    27540 2010-10-02 13:29 D9FBAB43d01
-rw------- 1 user user    44670 2010-10-02 14:02 DB3A45E5d01
-rw------- 1 user user   126161 2010-10-02 15:34 DB85D465d01
-rw------- 1 user user   103249 2010-10-02 13:41 DB9ADF18d01
-rw------- 1 user user   104152 2010-10-02 12:06 DB9E3E91d01
-rw------- 1 user user    64042 2010-10-02 15:41 DBA68A88d01
-rw------- 1 user user    69797 2010-10-02 13:31 DC3C7A16d01
-rw------- 1 user user    35779 2010-10-02 12:20 DC8D58D0d01
-rw------- 1 user user    29090 2010-10-02 12:21 DD95A3A8d01
-rw------- 1 user user    55219 2010-10-02 13:32 DFE56E68d01
-rw------- 1 user user    19144 2010-10-02 13:27 DFE56F39d01
-rw------- 1 user user   110888 2010-10-02 13:28 E12CBE73d01
-rw------- 1 user user    18275 2010-10-02 13:27 E16E715Ad01
-rw------- 1 user user    52535 2010-10-02 13:32 E276C478d01
-rw------- 1 user user    29564 2010-10-02 13:58 E2CCA65Dd01
-rw------- 1 user user    78150 2010-10-02 14:02 E303AF90d01
-rw------- 1 user user    41517 2010-10-02 12:21 E366E9DEd01
-rw------- 1 user user    25112 2010-10-02 12:20 E37FD9C0d01
-rw------- 1 user user    33009 2010-10-02 12:20 E38685CAd01
-rw------- 1 user user    46263 2010-10-02 13:40 E3F9FFB0d01
-rw------- 1 user user    23384 2010-10-02 13:40 E4884440d01
-rw------- 1 user user    21975 2010-10-02 12:20 E4BBA54Ad01
-rw------- 1 user user    34285 2010-10-02 12:10 E4E00324d01
-rw------- 1 user user    29010 2010-10-02 13:45 E4F51086d01
-rw------- 1 user user    17907 2010-10-02 12:17 E5225927d01
-rw------- 1 user user    33402 2010-10-02 13:40 E542917Bd01
-rw------- 1 user user    29112 2010-10-02 13:31 E58824E9d01
-rw------- 1 user user    35000 2010-10-02 13:31 E6888CFEd01
-rw------- 1 user user    75850 2010-10-02 13:28 E6D33CBBd01
-rw------- 1 user user    52033 2010-10-02 12:21 E876231Fd01
-rw------- 1 user user    67928 2010-10-02 15:40 E8C4A75Bd01
-rw------- 1 user user    99230 2010-10-02 14:03 E8EE0B7Ad01
-rw------- 1 user user    64121 2010-10-02 13:31 E8F7826Bd01
-rw------- 1 user user    18566 2010-10-02 13:29 E95E1524d01
-rw------- 1 user user    62337 2010-10-02 12:20 E994A8BBd01
-rw------- 1 user user    50538 2010-10-02 13:35 E9FEE08Ad01
-rw------- 1 user user   322277 2010-10-02 15:36 EA2876FFd01
-rw------- 1 user user   111418 2010-10-02 12:21 EAE037E4d01
-rw------- 1 user user    27094 2010-10-02 12:21 EC407E85d01
-rw------- 1 user user    23682 2010-10-02 15:16 EC611EE1d01
-rw------- 1 user user    37172 2010-10-02 13:31 ED53A742d01
-rw------- 1 user user    31311 2010-10-02 13:28 ED5D936Ad01
-rw------- 1 user user    17229 2010-10-02 12:18 EF9FABB6d01
-rw------- 1 user user    53871 2010-10-02 13:31 EFC7B2B9d01
-rw------- 1 user user    55147 2010-10-02 14:02 F0290DF5d01
-rw------- 1 user user    98656 2010-10-02 13:46 F0D25136d01
-rw------- 1 user user    92942 2010-10-02 13:41 F0E257ECd01
-rw------- 1 user user    20402 2010-10-02 13:40 F16CCCADd01
-rw------- 1 user user    77666 2010-10-02 14:02 F1B54CF1d01
-rw------- 1 user user    22244 2010-10-02 12:21 F33DF1C9d01
-rw------- 1 user user    45123 2010-10-02 12:07 F39970F1d01
-rw------- 1 user user    81696 2010-10-02 14:07 F42C2A91d01
-rw------- 1 user user    44864 2010-10-02 13:31 F43B543Bd01
-rw------- 1 user user    21907 2010-10-02 13:44 F475EEEBd01
-rw------- 1 user user    62715 2010-10-02 13:45 F52ECD5Ad01
-rw------- 1 user user    17536 2010-10-02 12:16 F5BB687Fd01
-rw------- 1 user user    36628 2010-10-02 13:45 F6EA8758d01
-rw------- 1 user user    35149 2010-10-02 12:20 F6EC07F9d01
-rw------- 1 user user    34380 2010-10-02 13:35 F744A258d01
-rw------- 1 user user    17537 2010-10-02 12:11 F747A4F2d01
-rw------- 1 user user    47467 2010-10-02 14:02 F776447Dd01
-rw------- 1 user user    21450 2010-10-02 13:31 F7EDE261d01
-rw------- 1 user user    58483 2010-10-02 12:11 F84094CCd01
-rw------- 1 user user    21607 2010-10-02 12:21 F9911671d01
-rw------- 1 user user    99016 2010-10-02 13:47 F9B1ED86d01
-rw------- 1 user user    32232 2010-10-02 12:20 FA495ED6d01
-rw------- 1 user user    17669 2010-10-02 13:31 FA524C2Dd01
-rw------- 1 user user    58366 2010-10-02 12:21 FB34EC37d01
-rw------- 1 user user   105112 2010-10-02 13:45 FB634A60d01
-rw------- 1 user user    76677 2010-10-02 12:16 FB787B9Bd01
-rw------- 1 user user   387452 2010-10-02 13:40 FBD0228Ed01
-rw------- 1 user user    32423 2010-10-02 12:20 FD03CB9Ad01
-rw------- 1 user user    51702 2010-10-02 14:02 FDC752CAd01
-rw------- 1 user user    29657 2010-10-02 14:02 FDEBF397d01
-rw------- 1 user user    55087 2010-10-02 15:40 FE481DACd01
-rw------- 1 user user    41007 2010-10-02 13:35 FE9A9C57d01
-rw------- 1 user user    57548 2010-10-02 13:41 FF12DE4Cd01

./.mozilla/firefox/fqwbqbb9.default/chrome:
total 16
drwxrwxrwx 2 user user 4096 2010-10-02 07:55 .
drwxrwxrwx 8 user user 4096 2010-10-02 15:47 ..
-rwxrwxrwx 1 user user  959 2010-10-02 07:55 userChrome-example.css
-rwxrwxrwx 1 user user  663 2010-10-02 07:55 userContent-example.css

./.mozilla/firefox/fqwbqbb9.default/extensions:
total 8
drwxrwxrwx 2 user user 4096 2010-10-02 07:55 .
drwxrwxrwx 8 user user 4096 2010-10-02 15:47 ..

./.mozilla/firefox/fqwbqbb9.default/minidumps:
total 8
drwxrwxrwx 2 user user 4096 2010-10-02 07:55 .
drwxrwxrwx 8 user user 4096 2010-10-02 15:47 ..

./.mozilla/firefox/fqwbqbb9.default/OfflineCache:
total 20
drwx------ 2 user user  4096 2010-10-02 15:37 .
drwxrwxrwx 8 user user  4096 2010-10-02 15:47 ..
-rw-r--r-- 1 user user 10240 2010-10-02 13:26 index.sqlite

./Music:
total 8
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..

./.nautilus:
total 8
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..

./Pictures:
total 8
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..

./Public:
total 8
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..

./.pulse:
total 152
drwx------  2 user user  4096 2010-10-02 15:28 .
drwxrwxrwx 36 user user  4096 2010-10-02 15:48 ..
-rwxrwxrwx  1 user user   696 2010-10-02 07:43 0d6e2173dda0703366309b6c4c6423db-card-database.tdb
-rwxrwxrwx  1 user user    43 2010-10-02 15:28 0d6e2173dda0703366309b6c4c6423db-default-sink
-rwxrwxrwx  1 user user    42 2010-10-02 15:28 0d6e2173dda0703366309b6c4c6423db-default-source
-rwxrwxrwx  1 user user 61440 2010-10-02 07:55 0d6e2173dda0703366309b6c4c6423db-device-volumes.tdb
lrwxrwxrwx  1 user user    23 2010-10-02 15:28 0d6e2173dda0703366309b6c4c6423db-runtime -> /tmp/pulse-xvuTjj88etoD
-rwxrwxrwx  1 user user 73728 2010-10-02 12:07 0d6e2173dda0703366309b6c4c6423db-stream-volumes.tdb

./.recently-used.xbel:
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..

./Templates:
total 8
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..

./.themes:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:45 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..

./.thumbnails:
total 16
drwx------  4 user user 4096 2010-10-02 09:45 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..
drwx------  3 user user 4096 2010-10-02 09:45 fail
drwx------  2 user user 4096 2010-10-02 14:26 normal

./.thumbnails/fail:
total 12
drwx------ 3 user user 4096 2010-10-02 09:45 .
drwx------ 4 user user 4096 2010-10-02 09:45 ..
drwx------ 2 user user 4096 2010-10-02 10:29 gnome-thumbnail-factory

./.thumbnails/fail/gnome-thumbnail-factory:
total 12
drwx------ 2 user user 4096 2010-10-02 10:29 .
drwx------ 3 user user 4096 2010-10-02 09:45 ..
-rw------- 1 user user  241 2010-10-02 10:29 90fd2382a037e43b6aeeaa77c72cdea5.png

./.thumbnails/normal:
total 500
drwx------ 2 user user  4096 2010-10-02 14:26 .
drwx------ 4 user user  4096 2010-10-02 09:45 ..
-rw------- 1 user user  7028 2010-10-02 09:45 0467ea573f32694ddcf7a49d0268d3ed.png
-rw------- 1 user user  7908 2010-10-02 09:45 04b719e97caa6a31987ddf3697cab60b.png
-rw------- 1 user user 12568 2010-10-02 10:14 0b4c5d8291ba70a26b5549b9d4c4022a.png
-rw------- 1 user user 24246 2010-10-02 09:45 119557ed2398778d6a42a0a229d06659.png
-rw------- 1 user user 16059 2010-10-02 09:45 18a04d26778c0e7921e2331e0b5b182d.png
-rw------- 1 user user 13523 2010-10-02 10:17 26da9aa1b9d7752753baf6381e6ed1f1.png
-rw------- 1 user user 13476 2010-10-02 09:45 2caf3f7bd48f77fe6e8cfb612596422c.png
-rw------- 1 user user 18597 2010-10-02 09:45 3b6d298340152610450bead6b92b7e29.png
-rw------- 1 user user 16687 2010-10-02 09:45 3c20cc8621051d934aa812c8d6f868dc.png
-rw------- 1 user user 10940 2010-10-02 09:45 45a25808dc6a3b7456ffe53305aca943.png
-rw------- 1 user user 12560 2010-10-02 09:45 45e4dccde76057de6bd52d4718e14086.png
-rw------- 1 user user 13504 2010-10-02 10:18 6d72b27a5c4f11cca97603cb4dcf6fbf.png
-rw------- 1 user user 14315 2010-10-02 14:26 7929946902f7da029a786dee462eb19d.png
-rw------- 1 user user  6201 2010-10-02 09:45 7b68ff31490e4b4aefacde178363f7cd.png
-rw------- 1 user user  9616 2010-10-02 09:45 80669861f9aa5aea3fe60cb442f453cc.png
-rw------- 1 user user  3249 2010-10-02 09:45 8781342f6e6ebaffd457329c55117c1b.png
-rw------- 1 user user 12908 2010-10-02 09:45 8fbc659a6218a941f9924f48663dca20.png
-rw------- 1 user user  7509 2010-10-02 09:45 905a099045b49667ea51f092ca498899.png
-rw------- 1 user user 20817 2010-10-02 09:45 98d5716865fa5df1344876642cc0eb69.png
-rw------- 1 user user 23603 2010-10-02 09:45 9ec48eb5cf7e9d39e77b4981956057bf.png
-rw------- 1 user user  4564 2010-10-02 09:45 a6681e5fece07bf81fd49f50c21a204e.png
-rw------- 1 user user 24584 2010-10-02 09:45 a6cd2b3b15ace5c9dc114d4dc5160967.png
-rw------- 1 user user  5105 2010-10-02 09:45 afb4bf3db3cb1f1004599f801ee4af7b.png
-rw------- 1 user user 22400 2010-10-02 09:45 be8014304affa8dd4db3a73f1c4d21b0.png
-rw------- 1 user user 16764 2010-10-02 09:45 c0d76bca6e42e8acf7a06084c406c4f2.png
-rw------- 1 user user 12749 2010-10-02 11:21 c2d3e3483b66250fb4e71390989d3871.png
-rw------- 1 user user  7876 2010-10-02 09:45 de94f63027cd0eb5feff6d6079ff581d.png
-rw------- 1 user user 14429 2010-10-02 09:45 e10e818e03dc8d6546825dd79ab7c316.png
-rw------- 1 user user 14050 2010-10-02 10:19 e5eec4615a649bde5f440b0c2d8a659c.png
-rw------- 1 user user 20689 2010-10-02 09:45 e6c27e914a4236d9f9a8b5322dbeab53.png
-rw------- 1 user user 14078 2010-10-02 14:25 e8fb4fe6557f3d920548e0b8e53a761e.png
-rw------- 1 user user  8018 2010-10-02 09:45 fe9dd8adb964525f53455aa89da0e12d.png

./.TrueCrypt:
total 12
drwx------  2 user user 4096 2010-10-02 10:16 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..
-rw-------  1 user user 1714 2010-10-02 10:16 Configuration.xml

./.update-notifier:
total 8
drwx------  2 user user 4096 2010-10-02 09:35 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..

./Videos:
total 8
drwxrwxrwx  2 user user 4096 2010-10-02 07:43 .
drwxrwxrwx 36 user user 4096 2010-10-02 15:48 ..

./.wine:
total 624
drwxr-xr-x  4 user user   4096 2010-10-02 09:56 .
drwxrwxrwx 36 user user   4096 2010-10-02 15:48 ..
drwxr-xr-x  2 user user   4096 2010-10-02 09:55 dosdevices
drwxr-xr-x  5 user user   4096 2010-10-02 09:55 drive_c
-rw-r--r--  1 user user 584971 2010-10-02 09:56 system.reg
-rw-r--r--  1 user user     11 2010-10-02 09:55 .update-timestamp
-rw-r--r--  1 user user   2118 2010-10-02 09:56 userdef.reg
-rw-r--r--  1 user user  26165 2010-10-02 09:56 user.reg

./.wine/dosdevices:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 4 user user 4096 2010-10-02 09:56 ..
lrwxrwxrwx 1 user user   10 2010-10-02 09:55 c: -> ../drive_c
lrwxrwxrwx 1 user user    1 2010-10-02 09:55 z: -> /

./.wine/drive_c:
total 20
drwxr-xr-x  5 user user 4096 2010-10-02 09:55 .
drwxr-xr-x  4 user user 4096 2010-10-02 09:56 ..
drwxr-xr-x  4 user user 4096 2010-10-02 09:55 Program Files
drwxr-xr-x  4 user user 4096 2010-10-02 09:55 users
drwxr-xr-x 10 user user 4096 2010-10-02 09:55 windows

./.wine/drive_c/Program Files:
total 16
drwxr-xr-x 4 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 5 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 Common Files
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 Internet Explorer

./.wine/drive_c/Program Files/Common Files:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 4 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/Program Files/Internet Explorer:
total 12
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 4 user user 4096 2010-10-02 09:55 ..
-rwxr-xr-x 1 user user 2524 2010-10-02 09:55 iexplore.exe

./.wine/drive_c/users:
total 16
drwxr-xr-x  4 user user 4096 2010-10-02 09:55 .
drwxr-xr-x  5 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x 11 user user 4096 2010-10-02 09:55 Public
drwxr-xr-x 13 user user 4096 2010-10-02 09:55 user

./.wine/drive_c/users/Public:
total 44
drwxr-xr-x 11 user user 4096 2010-10-02 09:55 .
drwxr-xr-x  4 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Application Data
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Desktop
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Documents
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Favorites
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Music
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Pictures
drwxr-xr-x  3 user user 4096 2010-10-02 09:55 Start Menu
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Templates
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Videos

./.wine/drive_c/users/Public/Application Data:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 11 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/Public/Desktop:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 11 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/Public/Documents:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 11 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/Public/Favorites:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 11 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/Public/Music:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 11 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/Public/Pictures:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 11 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/Public/Start Menu:
total 12
drwxr-xr-x  3 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 11 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x  4 user user 4096 2010-10-02 09:55 Programs

./.wine/drive_c/users/Public/Start Menu/Programs:
total 16
drwxr-xr-x 4 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 Administrative Tools
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 StartUp

./.wine/drive_c/users/Public/Start Menu/Programs/Administrative Tools:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 4 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/Public/Start Menu/Programs/StartUp:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 4 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/Public/Templates:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 11 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/Public/Videos:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 11 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/user:
total 52
drwxr-xr-x 13 user user 4096 2010-10-02 09:55 .
drwxr-xr-x  4 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Application Data
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Cookies
lrwxrwxrwx  1 user user   18 2010-10-02 09:55 Desktop -> /home/user/Desktop
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Favorites
drwxr-xr-x  5 user user 4096 2010-10-02 09:55 Local Settings
lrwxrwxrwx  1 user user   10 2010-10-02 09:55 My Documents -> /home/user
lrwxrwxrwx  1 user user   16 2010-10-02 09:55 My Music -> /home/user/Music
lrwxrwxrwx  1 user user   19 2010-10-02 09:55 My Pictures -> /home/user/Pictures
lrwxrwxrwx  1 user user   17 2010-10-02 09:55 My Videos -> /home/user/Videos
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 NetHood
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 PrintHood
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Recent
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 SendTo
drwxr-xr-x  3 user user 4096 2010-10-02 09:55 Start Menu
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Temp
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Templates

./.wine/drive_c/users/user/Application Data:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 13 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/user/Cookies:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 13 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/user/Favorites:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 13 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/user/Local Settings:
total 20
drwxr-xr-x  5 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 13 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Application Data
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 History
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 Temporary Internet Files

./.wine/drive_c/users/user/Local Settings/Application Data:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 5 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/user/Local Settings/History:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 5 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/user/Local Settings/Temporary Internet Files:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 5 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/user/NetHood:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 13 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/user/PrintHood:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 13 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/user/Recent:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 13 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/user/SendTo:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 13 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/user/Start Menu:
total 12
drwxr-xr-x  3 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 13 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x  3 user user 4096 2010-10-02 09:55 Programs

./.wine/drive_c/users/user/Start Menu/Programs:
total 12
drwxr-xr-x 3 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 StartUp

./.wine/drive_c/users/user/Start Menu/Programs/StartUp:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/user/Temp:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 13 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/users/user/Templates:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 13 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/windows:
total 440
drwxr-xr-x 10 user user   4096 2010-10-02 09:55 .
drwxr-xr-x  5 user user   4096 2010-10-02 09:55 ..
drwxr-xr-x  2 user user   4096 2010-10-02 09:55 command
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 explorer.exe
drwxr-xr-x  2 user user   4096 2010-10-02 09:55 Fonts
drwxr-xr-x  2 user user   4096 2010-10-02 09:55 help
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 hh.exe
drwxr-xr-x  2 user user   4096 2010-10-02 09:55 inf
-rwxr-xr-x  1 user user 100768 2010-10-02 09:55 notepad.exe
-rwxr-xr-x  1 user user 199992 2010-10-02 09:55 regedit.exe
drwxr-xr-x  2 user user   4096 2010-10-02 09:55 system
drwxr-xr-x  7 user user  16384 2010-10-02 09:55 system32
-rw-r--r--  1 user user    481 2010-10-02 09:55 system.ini
drwxr-xr-x  2 user user   4096 2010-10-02 09:55 temp
-rw-r--r--  1 user user   1032 2010-10-02 09:55 twain_32.dll
-rw-r--r--  1 user user    206 2010-10-02 09:55 twain.dll
-rwxr-xr-x  1 user user    214 2010-10-02 09:55 winhelp.exe
-rwxr-xr-x  1 user user  65304 2010-10-02 09:55 winhlp32.exe
-rw-r--r--  1 user user    595 2010-10-02 09:55 win.ini
drwxr-xr-x  3 user user   4096 2010-10-02 09:55 winsxs

./.wine/drive_c/windows/command:
total 72
drwxr-xr-x  2 user user  4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user  4096 2010-10-02 09:55 ..
-rwxr-xr-x  1 user user 63548 2010-10-02 09:55 start.exe

./.wine/drive_c/windows/Fonts:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/windows/help:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/windows/inf:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/windows/system:
total 12
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user 4096 2010-10-02 09:55 ..
-rw-r--r--  1 user user  206 2010-10-02 09:55 ddeml.dll

./.wine/drive_c/windows/system32:
total 7824
drwxr-xr-x  7 user user  16384 2010-10-02 09:55 .
drwxr-xr-x 10 user user   4096 2010-10-02 09:55 ..
-rw-r--r--  1 user user   1032 2010-10-02 09:55 acledit.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 aclui.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 activeds.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 actxprxy.dll
-rw-r--r--  1 user user   2488 2010-10-02 09:55 advapi32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 advpack.dll
-rw-r--r--  1 user user   2460 2010-10-02 09:55 amstream.dll
-rw-r--r--  1 user user  49988 2010-10-02 09:55 appwiz.cpl
-rw-r--r--  1 user user   2016 2010-10-02 09:55 atl.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 attrib.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 authz.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 avicap32.dll
-rw-r--r--  1 user user  26532 2010-10-02 09:55 avifil32.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 avifile.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 avrt.dll
-rw-r--r--  1 user user   2496 2010-10-02 09:55 bcrypt.dll
-rw-r--r--  1 user user   9656 2010-10-02 09:55 browseui.dll
-rw-r--r--  1 user user   2468 2010-10-02 09:55 cabinet.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 cacls.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 capi2032.dll
-rw-r--r--  1 user user 251452 2010-10-02 09:55 cards.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 cfgmgr32.dll
-rwxr-xr-x  1 user user  46488 2010-10-02 09:55 clock.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 clusapi.dll
-rwxr-xr-x  1 user user 291608 2010-10-02 09:55 cmd.exe
-rw-r--r--  1 user user   2492 2010-10-02 09:55 comcat.dll
-rw-r--r--  1 user user  64508 2010-10-02 09:55 comctl32.dll
-rw-r--r--  1 user user 439552 2010-10-02 09:55 comdlg32.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 commdlg.dll
-rw-r--r--  1 user user    204 2010-10-02 09:55 comm.drv
-rw-r--r--  1 user user    208 2010-10-02 09:55 compobj.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 compstui.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 control.exe
-rw-r--r--  1 user user  80572 2010-10-02 09:55 credui.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 crtdll.dll
-rw-r--r--  1 user user  94784 2010-10-02 09:55 crypt32.dll
-rw-r--r--  1 user user   5684 2010-10-02 09:55 cryptdlg.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 cryptdll.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 cryptnet.dll
-rw-r--r--  1 user user 226024 2010-10-02 09:55 cryptui.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 ctapi32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 ctl3d32.dll
-rw-r--r--  1 user user    206 2010-10-02 09:55 ctl3d.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 ctl3dv2.dll
-rw-r--r--  1 user user   2492 2010-10-02 09:55 d3d10core.dll
-rw-r--r--  1 user user   2480 2010-10-02 09:55 d3d10.dll
-rw-r--r--  1 user user   2456 2010-10-02 09:55 d3d8.dll
-rw-r--r--  1 user user   2456 2010-10-02 09:55 d3d9.dll
-rw-r--r--  1 user user   2516 2010-10-02 09:55 d3dim.dll
-rw-r--r--  1 user user   2512 2010-10-02 09:55 d3drm.dll
-rw-r--r--  1 user user   2452 2010-10-02 09:55 d3dx9_24.dll
-rw-r--r--  1 user user   2452 2010-10-02 09:55 d3dx9_25.dll
-rw-r--r--  1 user user   2452 2010-10-02 09:55 d3dx9_26.dll
-rw-r--r--  1 user user   2452 2010-10-02 09:55 d3dx9_27.dll
-rw-r--r--  1 user user   2460 2010-10-02 09:55 d3dx9_28.dll
-rw-r--r--  1 user user   2460 2010-10-02 09:55 d3dx9_29.dll
-rw-r--r--  1 user user   2460 2010-10-02 09:55 d3dx9_30.dll
-rw-r--r--  1 user user   2460 2010-10-02 09:55 d3dx9_31.dll
-rw-r--r--  1 user user   2460 2010-10-02 09:55 d3dx9_32.dll
-rw-r--r--  1 user user   2460 2010-10-02 09:55 d3dx9_33.dll
-rw-r--r--  1 user user   2460 2010-10-02 09:55 d3dx9_34.dll
-rw-r--r--  1 user user   2468 2010-10-02 09:55 d3dx9_35.dll
-rw-r--r--  1 user user   2468 2010-10-02 09:55 d3dx9_36.dll
-rw-r--r--  1 user user   2468 2010-10-02 09:55 d3dx9_37.dll
-rw-r--r--  1 user user   2468 2010-10-02 09:55 d3dx9_38.dll
-rw-r--r--  1 user user   2468 2010-10-02 09:55 d3dx9_39.dll
-rw-r--r--  1 user user   2468 2010-10-02 09:55 d3dx9_40.dll
-rw-r--r--  1 user user   2468 2010-10-02 09:55 d3dx9_41.dll
-rw-r--r--  1 user user   2468 2010-10-02 09:55 d3dx9_42.dll
-rw-r--r--  1 user user   2476 2010-10-02 09:55 d3dxof.dll
-rw-r--r--  1 user user   2484 2010-10-02 09:55 dbghelp.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 dciman32.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 ddhelp.exe
-rw-r--r--  1 user user   2504 2010-10-02 09:55 ddraw.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 ddrawex.dll
-rw-r--r--  1 user user   6280 2010-10-02 09:55 devenum.dll
-rw-r--r--  1 user user   2468 2010-10-02 09:55 dinput8.dll
-rw-r--r--  1 user user   2464 2010-10-02 09:55 dinput.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 dispdib.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 dispex.dll
-rw-r--r--  1 user user   1142 2010-10-02 09:55 display.drv
-rw-r--r--  1 user user   2464 2010-10-02 09:55 dmband.dll
-rw-r--r--  1 user user   2476 2010-10-02 09:55 dmcompos.dll
-rw-r--r--  1 user user   2500 2010-10-02 09:55 dmime.dll
-rw-r--r--  1 user user   2472 2010-10-02 09:55 dmloader.dll
-rw-r--r--  1 user user   2480 2010-10-02 09:55 dmscript.dll
-rw-r--r--  1 user user   2480 2010-10-02 09:55 dmstyle.dll
-rw-r--r--  1 user user   2496 2010-10-02 09:55 dmsynth.dll
-rw-r--r--  1 user user   2484 2010-10-02 09:55 dmusic32.dll
-rw-r--r--  1 user user   2512 2010-10-02 09:55 dmusic.dll
-rw-r--r--  1 user user   2452 2010-10-02 09:55 dnsapi.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 dosx.exe
-rw-r--r--  1 user user   2492 2010-10-02 09:55 dplay.dll
-rw-r--r--  1 user user   2508 2010-10-02 09:55 dplayx.dll
-rw-r--r--  1 user user   2484 2010-10-02 09:55 dpnaddr.dll
-rw-r--r--  1 user user   2452 2010-10-02 09:55 dpnet.dll
-rw-r--r--  1 user user   2488 2010-10-02 09:55 dpnhpast.dll
-rw-r--r--  1 user user   2488 2010-10-02 09:55 dpnlobby.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 dpwsockx.dll
drwxr-xr-x  2 user user   4096 2010-10-02 09:55 drivers
-rw-r--r--  1 user user   1032 2010-10-02 09:55 drmclien.dll
-rw-r--r--  1 user user   2512 2010-10-02 09:55 dsound.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 dsound.vxd
-rw-r--r--  1 user user   1032 2010-10-02 09:55 dssenh.dll
-rw-r--r--  1 user user   2508 2010-10-02 09:55 dswave.dll
-rw-r--r--  1 user user   2512 2010-10-02 09:55 dwmapi.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 dxdiag.exe
-rw-r--r--  1 user user   2460 2010-10-02 09:55 dxdiagn.dll
-rw-r--r--  1 user user   2472 2010-10-02 09:55 dxgi.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 eject.exe
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 expand.exe
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 explorer.exe
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 extrac32.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 faultrep.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 fltlib.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 fusion.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 fwpuclnt.dll
-rw-r--r--  1 user user   2432 2010-10-02 09:55 gdi32.dll
-rwxr-xr-x  1 user user    686 2010-10-02 09:55 gdi.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 gdiplus.dll
drwxr-xr-x  3 user user   4096 2010-10-02 09:55 gecko
-rw-r--r--  1 user user   1032 2010-10-02 09:55 glu32.dll
-rw-r--r--  1 user user  14980 2010-10-02 09:55 gphoto2.ds
-rw-r--r--  1 user user   1032 2010-10-02 09:55 gpkcsp.dll
-rw-r--r--  1 user user   2468 2010-10-02 09:55 hal.dll
-rw-r--r--  1 user user  18444 2010-10-02 09:55 hhctrl.ocx
-rw-r--r--  1 user user   2440 2010-10-02 09:55 hid.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 hlink.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 hnetcfg.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 httpapi.dll
-rw-r--r--  1 user user   3988 2010-10-02 09:55 iccvid.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 icinfo.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 icmp.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 ifsmgr.vxd
-rw-r--r--  1 user user   1032 2010-10-02 09:55 imaadp32.acm
-rw-r--r--  1 user user   1032 2010-10-02 09:55 imagehlp.dll
-rw-r--r--  1 user user   2468 2010-10-02 09:55 imm32.dll
-rw-r--r--  1 user user    204 2010-10-02 09:55 imm.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 inetcomm.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 inetmib1.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 infosoft.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 initpki.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 inkobj.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 inseng.dll
-rw-r--r--  1 user user   2480 2010-10-02 09:55 iphlpapi.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 itircl.dll
-rw-r--r--  1 user user   4580 2010-10-02 09:55 itss.dll
-rw-r--r--  1 user user  38512 2010-10-02 09:55 jscript.dll
-rw-r--r--  1 user user 707908 2010-10-02 09:55 kernel32.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 keyboard.drv
-rwxr-xr-x  1 user user    692 2010-10-02 09:55 krnl386.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 loadperf.dll
-rw-r--r--  1 user user   4340 2010-10-02 09:55 localspl.dll
-rw-r--r--  1 user user  17004 2010-10-02 09:55 localui.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 lodctr.exe
-rw-r--r--  1 user user   2464 2010-10-02 09:55 lz32.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 lzexpand.dll
-rw-r--r--  1 user user   3912 2010-10-02 09:55 mapi32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 mapistub.dll
-rw-r--r--  1 user user  12424 2010-10-02 09:55 mciavi32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 mcicda.dll
-rw-r--r--  1 user user   2524 2010-10-02 09:55 mciqtz32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 mciseq.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 mciwave.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 midimap.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 mlang.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 mmdevapi.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 mmdevldr.vxd
-rw-r--r--  1 user user    208 2010-10-02 09:55 mmsystem.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 monodebg.vxd
-rw-r--r--  1 user user    696 2010-10-02 09:55 mouse.drv
-rw-r--r--  1 user user   1032 2010-10-02 09:55 mprapi.dll
-rw-r--r--  1 user user  20648 2010-10-02 09:55 mpr.dll
-rw-r--r--  1 user user  14320 2010-10-02 09:55 msacm32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msacm32.drv
-rw-r--r--  1 user user    206 2010-10-02 09:55 msacm.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msadp32.acm
-rw-r--r--  1 user user   1032 2010-10-02 09:55 mscat32.dll
-rw-r--r--  1 user user   2476 2010-10-02 09:55 mscms.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 mscoree.dll
-rw-r--r--  1 user user   2472 2010-10-02 09:55 msctf.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msdaps.dll
-rw-r--r--  1 user user   2440 2010-10-02 09:55 msdmo.dll
-rw-r--r--  1 user user   2500 2010-10-02 09:55 msftedit.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msg711.acm
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msgsm32.acm
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 mshta.exe
-rw-r--r--  1 user user  60212 2010-10-02 09:55 mshtml.dll
-rw-r--r--  1 user user 471292 2010-10-02 09:55 mshtml.tlb
-rw-r--r--  1 user user  35812 2010-10-02 09:55 msi.dll
-rwxr-xr-x  1 user user  17820 2010-10-02 09:55 msiexec.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msimg32.dll
-rw-r--r--  1 user user   2552 2010-10-02 09:55 msimtf.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msisip.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msisys.ocx
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msnet32.dll
-rw-r--r--  1 user user   7384 2010-10-02 09:55 msrle32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 mssign32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 mssip32.dll
-rw-r--r--  1 user user   2132 2010-10-02 09:55 mstask.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msvcirt.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msvcr70.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msvcr71.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msvcr80.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msvcr90.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msvcrt20.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msvcrt40.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msvcrtd.dll
-rw-r--r--  1 user user   2456 2010-10-02 09:55 msvcrt.dll
-rw-r--r--  1 user user  17908 2010-10-02 09:55 msvfw32.dll
-rw-r--r--  1 user user   3720 2010-10-02 09:55 msvidc32.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 msvideo.dll
-rw-r--r--  1 user user   2444 2010-10-02 09:55 mswsock.dll
-rw-r--r--  1 user user  46908 2010-10-02 09:55 msxml3.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 msxml4.dll
drwxr-xr-x  2 user user   4096 2010-10-02 09:55 mui
-rw-r--r--  1 user user   1032 2010-10-02 09:55 nddeapi.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 netapi32.dll
-rwxr-xr-x  1 user user  23340 2010-10-02 09:55 net.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 newdev.dll
-rwxr-xr-x  1 user user 100768 2010-10-02 09:55 notepad.exe
-rw-r--r--  1 user user   2468 2010-10-02 09:55 ntdll.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 ntdsapi.dll
-rwxr-xr-x  1 user user   2480 2010-10-02 09:55 ntoskrnl.exe
-rw-r--r--  1 user user   2508 2010-10-02 09:55 ntprint.dll
-rw-r--r--  1 user user   2448 2010-10-02 09:55 objsel.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 odbc32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 odbccp32.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 ole2conv.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 ole2disp.dll
-rw-r--r--  1 user user    204 2010-10-02 09:55 ole2.dll
-rw-r--r--  1 user user    702 2010-10-02 09:55 ole2nls.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 ole2prox.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 ole2thk.dll
-rw-r--r--  1 user user   4232 2010-10-02 09:55 ole32.dll
-rw-r--r--  1 user user  17200 2010-10-02 09:55 oleacc.dll
-rw-r--r--  1 user user   5352 2010-10-02 09:55 oleaut32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 olecli32.dll
-rw-r--r--  1 user user    206 2010-10-02 09:55 olecli.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 oledb32.dll
-rw-r--r--  1 user user  67164 2010-10-02 09:55 oledlg.dll
-rw-r--r--  1 user user   2508 2010-10-02 09:55 olepro32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 olesvr32.dll
-rw-r--r--  1 user user    206 2010-10-02 09:55 olesvr.dll
-rw-r--r--  1 user user   2480 2010-10-02 09:55 olethk32.dll
-rwxr-xr-x  1 user user 108620 2010-10-02 09:55 oleview.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 openal32.dll
-rw-r--r--  1 user user   2472 2010-10-02 09:55 opengl32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 pdh.dll
-rw-r--r--  1 user user   2420 2010-10-02 09:55 pidgen.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 ping.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 powrprof.dll
-rw-r--r--  1 user user   2504 2010-10-02 09:55 printui.dll
-rwxr-xr-x  1 user user 134968 2010-10-02 09:55 progman.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 propsys.dll
-rw-r--r--  1 user user   2500 2010-10-02 09:55 psapi.dll
-rw-r--r--  1 user user   9104 2010-10-02 09:55 pstorec.dll
-rw-r--r--  1 user user   2444 2010-10-02 09:55 qcap.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 qedit.dll
-rw-r--r--  1 user user   2152 2010-10-02 09:55 qmgr.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 qmgrprxy.dll
-rw-r--r--  1 user user   2496 2010-10-02 09:55 quartz.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 query.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 rasapi16.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 rasapi32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 rasdlg.dll
-rwxr-xr-x  1 user user  15700 2010-10-02 09:55 reg.exe
-rwxr-xr-x  1 user user   2464 2010-10-02 09:55 regsvr32.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 resutils.dll
-rw-r--r--  1 user user   2960 2010-10-02 09:55 riched20.dll
-rw-r--r--  1 user user   2496 2010-10-02 09:55 riched32.dll
-rw-r--r--  1 user user   2472 2010-10-02 09:55 rpcrt4.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 rpcss.exe
-rw-r--r--  1 user user   2476 2010-10-02 09:55 rsabase.dll
-rw-r--r--  1 user user   2472 2010-10-02 09:55 rsaenh.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 rtutils.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 rundll32.exe
-rw-r--r--  1 user user   6456 2010-10-02 09:55 sane.ds
-rw-r--r--  1 user user   1032 2010-10-02 09:55 sccbase.dll
-rw-r--r--  1 user user   2480 2010-10-02 09:55 schannel.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 secedit.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 secur32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 security.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 sensapi.dll
-rw-r--r--  1 user user  14900 2010-10-02 09:55 serialui.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 services.exe
-rw-r--r--  1 user user  21224 2010-10-02 09:55 setupapi.dll
-rw-r--r--  1 user user    206 2010-10-02 09:55 setupx.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 sfc.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 sfc_os.dll
-rw-r--r--  1 user user 110576 2010-10-02 09:55 shdoclc.dll
-rw-r--r--  1 user user  44988 2010-10-02 09:55 shdocvw.dll
-rw-r--r--  1 user user 978056 2010-10-02 09:55 shell32.dll
-rw-r--r--  1 user user    692 2010-10-02 09:55 shell.dll
-rw-r--r--  1 user user   2556 2010-10-02 09:55 shfolder.dll
-rw-r--r--  1 user user  15020 2010-10-02 09:55 shlwapi.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 slbcsp.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 slc.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 snmpapi.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 softpub.dll
-rw-r--r--  1 user user    206 2010-10-02 09:55 sound.drv
drwxr-xr-x  4 user user   4096 2010-10-02 09:55 spool
-rw-r--r--  1 user user   1032 2010-10-02 09:55 spoolss.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 spoolsv.exe
-rw-r--r--  1 user user  17740 2010-10-02 09:55 stdole2.tlb
-rw-r--r--  1 user user   6900 2010-10-02 09:55 stdole32.tlb
-rw-r--r--  1 user user   1032 2010-10-02 09:55 sti.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 storage.dll
-rw-r--r--  1 user user    206 2010-10-02 09:55 stress.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 svchost.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 svrapi.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 sxs.dll
-rw-r--r--  1 user user    206 2010-10-02 09:55 system.drv
-rw-r--r--  1 user user   1032 2010-10-02 09:55 t2embed.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 tapi32.dll
-rwxr-xr-x  1 user user 237860 2010-10-02 09:55 taskmgr.exe
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 termsv.exe
-rw-r--r--  1 user user    208 2010-10-02 09:55 toolhelp.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 traffic.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 typelib.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 unicows.dll
-rwxr-xr-x  1 user user  10852 2010-10-02 09:55 uninstaller.exe
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 unlodctr.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 updspapi.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 url.dll
-rw-r--r--  1 user user  24216 2010-10-02 09:55 urlmon.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 usbd.sys
-rw-r--r--  1 user user  74188 2010-10-02 09:55 user32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 userenv.dll
-rwxr-xr-x  1 user user    690 2010-10-02 09:55 user.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 usp10.dll
-rw-r--r--  1 user user   2448 2010-10-02 09:55 uxtheme.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 vdhcp.vxd
-rw-r--r--  1 user user   1032 2010-10-02 09:55 vdmdbg.dll
-rw-r--r--  1 user user    204 2010-10-02 09:55 ver.dll
-rw-r--r--  1 user user   2484 2010-10-02 09:55 version.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 vmm.vxd
-rw-r--r--  1 user user   1032 2010-10-02 09:55 vnbt.vxd
-rw-r--r--  1 user user   1032 2010-10-02 09:55 vnetbios.vxd
-rw-r--r--  1 user user   1032 2010-10-02 09:55 vtdapi.vxd
-rw-r--r--  1 user user   1032 2010-10-02 09:55 vwin32.vxd
-rw-r--r--  1 user user   1032 2010-10-02 09:55 w32skrnl.dll
-rw-r--r--  1 user user    206 2010-10-02 09:55 w32sys.dll
drwxr-xr-x  2 user user   4096 2010-10-02 09:55 wbem
-rw-r--r--  1 user user   1032 2010-10-02 09:55 wbemprox.dll
-rw-r--r--  1 user user   2536 2010-10-02 09:55 wiaservc.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 win32s16.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 win87em.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 winaspi.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 windebug.dll
-rw-r--r--  1 user user   2524 2010-10-02 09:55 windowscodecs.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 winealsa.drv
-rw-r--r--  1 user user   1032 2010-10-02 09:55 wineaudioio.drv
-rwxr-xr-x  1 user user  12572 2010-10-02 09:55 wineboot.exe
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 winebrowser.exe
-rwxr-xr-x  1 user user 340984 2010-10-02 09:55 winecfg.exe
-rwxr-xr-x  1 user user  93164 2010-10-02 09:55 wineconsole.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 winecoreaudio.drv
-rw-r--r--  1 user user   2452 2010-10-02 09:55 wined3d.dll
-rwxr-xr-x  1 user user  16856 2010-10-02 09:55 winedbg.exe
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 winedevice.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 wineesd.drv
-rwxr-xr-x  1 user user 130844 2010-10-02 09:55 winefile.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 winejack.drv
-rw-r--r--  1 user user   1032 2010-10-02 09:55 winejoystick.drv
-rw-r--r--  1 user user   1032 2010-10-02 09:55 winemapi.dll
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 winemenubuilder.exe
-rwxr-xr-x  1 user user  57056 2010-10-02 09:55 winemine.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 winemp3.acm
-rw-r--r--  1 user user   1032 2010-10-02 09:55 winenas.drv
-rw-r--r--  1 user user   1032 2010-10-02 09:55 wineoss.drv
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 winepath.exe
-rw-r--r--  1 user user    208 2010-10-02 09:55 wineps16.drv
-rw-r--r--  1 user user  10608 2010-10-02 09:55 wineps.drv
-rwxr-xr-x  1 user user   1032 2010-10-02 09:55 winevdm.exe
-rw-r--r--  1 user user   2452 2010-10-02 09:55 winex11.drv
-rw-r--r--  1 user user   1032 2010-10-02 09:55 wing32.dll
-rw-r--r--  1 user user    204 2010-10-02 09:55 wing.dll
-rw-r--r--  1 user user   2464 2010-10-02 09:55 winhttp.dll
-rw-r--r--  1 user user  29424 2010-10-02 09:55 wininet.dll
-rw-r--r--  1 user user 335980 2010-10-02 09:55 winmm.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 winnls32.dll
-rw-r--r--  1 user user    206 2010-10-02 09:55 winnls.dll
-rw-r--r--  1 user user    214 2010-10-02 09:55 winoldap.mod
-rw-r--r--  1 user user   2472 2010-10-02 09:55 winscard.dll
-rw-r--r--  1 user user    208 2010-10-02 09:55 winsock.dll
-rw-r--r--  1 user user  14152 2010-10-02 09:55 winspool.drv
-rw-r--r--  1 user user   1032 2010-10-02 09:55 wintab32.dll
-rw-r--r--  1 user user    206 2010-10-02 09:55 wintab.dll
-rw-r--r--  1 user user   2488 2010-10-02 09:55 wintrust.dll
-rwxr-xr-x  1 user user   2472 2010-10-02 09:55 winver.exe
-rw-r--r--  1 user user  45652 2010-10-02 09:55 wldap32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 wmi.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 wmiutils.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 wnaspi32.dll
-rwxr-xr-x  1 user user 142440 2010-10-02 09:55 wordpad.exe
-rw-r--r--  1 user user   1032 2010-10-02 09:55 wow32.dll
-rwxr-xr-x  1 user user   3376 2010-10-02 09:55 write.exe
-rw-r--r--  1 user user   2444 2010-10-02 09:55 ws2_32.dll
-rw-r--r--  1 user user   2444 2010-10-02 09:55 wsock32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 wtsapi32.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 wuapi.dll
-rw-r--r--  1 user user   2484 2010-10-02 09:55 wuaueng.dll
-rwxr-xr-x  1 user user  56352 2010-10-02 09:55 xcopy.exe
-rw-r--r--  1 user user   2492 2010-10-02 09:55 xinput1_1.dll
-rw-r--r--  1 user user   2492 2010-10-02 09:55 xinput1_2.dll
-rw-r--r--  1 user user   2492 2010-10-02 09:55 xinput1_3.dll
-rw-r--r--  1 user user   2496 2010-10-02 09:55 xinput9_1_0.dll
-rw-r--r--  1 user user   1032 2010-10-02 09:55 xmllite.dll

./.wine/drive_c/windows/system32/drivers:
total 24
drwxr-xr-x 2 user user  4096 2010-10-02 09:55 .
drwxr-xr-x 7 user user 16384 2010-10-02 09:55 ..
-rw-r--r-- 1 user user  1032 2010-10-02 09:55 mountmgr.sys

./.wine/drive_c/windows/system32/gecko:
total 24
drwxr-xr-x 3 user user  4096 2010-10-02 09:55 .
drwxr-xr-x 7 user user 16384 2010-10-02 09:55 ..
drwxr-xr-x 3 user user  4096 2010-10-02 09:55 1.0.0

./.wine/drive_c/windows/system32/gecko/1.0.0:
total 12
drwxr-xr-x  3 user user 4096 2010-10-02 09:55 .
drwxr-xr-x  3 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x 10 user user 4096 2010-10-02 09:55 wine_gecko

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko:
total 23472
drwxr-xr-x 10 user user     4096 2010-10-02 09:55 .
drwxr-xr-x  3 user user     4096 2010-10-02 09:55 ..
drwxr-xr-x  2 user user     4096 2010-10-02 09:55 chrome
drwxr-xr-x  2 user user     4096 2010-10-02 09:55 components
drwxr-xr-x  5 user user     4096 2010-10-02 09:55 defaults
-rw-r--r--  1 user user      145 2009-08-03 22:42 dependentlibs.list
drwxr-xr-x  2 user user     4096 2010-10-02 09:55 dictionaries
-rw-r--r--  1 user user   382976 2009-08-03 22:42 freebl3.dll
drwxr-xr-x  2 user user     4096 2010-10-02 09:55 greprefs
-rw-r--r--  1 user user  1142784 2009-08-03 22:42 js3250.dll
-rw-r--r--  1 user user    30826 2009-08-03 22:42 LICENSE
drwxr-xr-x  2 user user     4096 2010-10-02 09:55 modules
-rw-r--r--  1 user user   216064 2009-08-03 22:42 nspr4.dll
-rw-r--r--  1 user user   812544 2009-08-03 22:42 nss3.dll
-rw-r--r--  1 user user   320512 2009-08-03 22:42 nssckbi.dll
-rw-r--r--  1 user user   123392 2009-08-03 22:42 nssdbm3.dll
-rw-r--r--  1 user user    66560 2009-08-03 22:42 nssutil3.dll
-rw-r--r--  1 user user       52 2009-08-03 22:42 platform.ini
-rw-r--r--  1 user user    14336 2009-08-03 22:42 plc4.dll
-rw-r--r--  1 user user    10240 2009-08-03 22:42 plds4.dll
drwxr-xr-x  2 user user     4096 2010-10-02 09:55 plugins
-rwxr-xr-x  1 user user     6656 2009-08-03 22:42 redit.exe
drwxr-xr-x  6 user user     4096 2010-10-02 09:55 res
-rw-r--r--  1 user user   112128 2009-08-03 22:42 smime3.dll
-rw-r--r--  1 user user   176640 2009-08-03 22:42 softokn3.dll
-rw-r--r--  1 user user   489472 2009-08-03 22:42 sqlite3.dll
-rw-r--r--  1 user user   150016 2009-08-03 22:42 ssl3.dll
-rw-r--r--  1 user user       16 2009-08-03 22:42 VERSION
-rw-r--r--  1 user user    10752 2009-08-03 22:42 xpcom.dll
-rwxr-xr-x  1 user user    97280 2009-08-03 22:42 xpcshell.exe
-rwxr-xr-x  1 user user    84480 2009-08-03 22:42 xpidl.exe
-rwxr-xr-x  1 user user    30208 2009-08-03 22:42 xpt_dump.exe
-rwxr-xr-x  1 user user    26624 2009-08-03 22:42 xpt_link.exe
-rw-r--r--  1 user user 19635712 2009-08-03 22:42 xul.dll

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/chrome:
total 3420
drwxr-xr-x  2 user user    4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user    4096 2010-10-02 09:55 ..
-rw-r--r--  1 user user  821107 2009-08-03 22:42 classic.jar
-rw-r--r--  1 user user     494 2009-08-03 22:42 classic.manifest
-rw-r--r--  1 user user   40071 2009-08-03 22:42 comm.jar
-rw-r--r--  1 user user     144 2009-08-03 22:42 comm.manifest
-rw-r--r--  1 user user  327326 2009-08-03 22:42 en-US.jar
-rw-r--r--  1 user user     722 2009-08-03 22:42 en-US.manifest
-rw-r--r--  1 user user  279503 2009-08-03 22:42 pippki.jar
-rw-r--r--  1 user user      69 2009-08-03 22:42 pippki.manifest
-rw-r--r--  1 user user 1998105 2009-08-03 22:42 toolkit.jar
-rw-r--r--  1 user user     517 2009-08-03 22:42 toolkit.manifest

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/components:
total 1848
drwxr-xr-x  2 user user   4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user   4096 2010-10-02 09:55 ..
-rw-r--r--  1 user user 133742 2010-10-02 09:55 compreg.dat
-rw-r--r--  1 user user  65927 2009-08-03 22:42 FeedProcessor.js
-rw-r--r--  1 user user   1486 2009-08-03 22:42 jsconsole-clhandler.js
-rw-r--r--  1 user user  11604 2009-08-03 22:42 NetworkGeolocationProvider.js
-rw-r--r--  1 user user  11713 2009-08-03 22:42 nsAddonRepository.js
-rw-r--r--  1 user user   3104 2009-08-03 22:42 nsBadCertHandler.js
-rw-r--r--  1 user user  37255 2009-08-03 22:42 nsBlocklistService.js
-rw-r--r--  1 user user   5089 2009-08-03 22:42 nsContentDispatchChooser.js
-rw-r--r--  1 user user  33427 2009-08-03 22:42 nsContentPrefService.js
-rw-r--r--  1 user user   6334 2009-08-03 22:42 nsDefaultCLH.js
-rw-r--r--  1 user user   5737 2009-08-03 22:42 nsDownloadManagerUI.js
-rw-r--r--  1 user user 317499 2009-08-03 22:42 nsExtensionManager.js
-rw-r--r--  1 user user  14478 2009-08-03 22:42 nsFormAutoComplete.js
-rw-r--r--  1 user user  53725 2009-08-03 22:42 nsHandlerService.js
-rw-r--r--  1 user user  44160 2009-08-03 22:42 nsHelperAppDlg.js
-rw-r--r--  1 user user  36888 2009-08-03 22:42 nsLivemarkService.js
-rw-r--r--  1 user user   4920 2009-08-03 22:42 nsLoginInfo.js
-rw-r--r--  1 user user  50687 2009-08-03 22:42 nsLoginManager.js
-rw-r--r--  1 user user  50534 2009-08-03 22:42 nsLoginManagerPrompter.js
-rw-r--r--  1 user user  17685 2009-08-03 22:42 nsPlacesDBFlush.js
-rw-r--r--  1 user user  37236 2009-08-03 22:42 nsProgressDialog.js
-rw-r--r--  1 user user  13682 2009-08-03 22:42 nsProxyAutoConfig.js
-rw-r--r--  1 user user 123245 2009-08-03 22:42 nsSearchService.js
-rw-r--r--  1 user user  24315 2009-08-03 22:42 nsSearchSuggestions.js
-rw-r--r--  1 user user  22190 2009-08-03 22:42 nsTaggingService.js
-rw-r--r--  1 user user   3268 2009-08-03 22:42 nsTryToClose.js
-rw-r--r--  1 user user 107038 2009-08-03 22:42 nsUpdateService.js
-rw-r--r--  1 user user   3096 2009-08-03 22:42 nsURLFormatter.js
-rw-r--r--  1 user user   6920 2009-08-03 22:42 nsWebHandlerApp.js
-rw-r--r--  1 user user   8097 2009-08-03 22:42 nsXULAppInstall.js
-rw-r--r--  1 user user   3142 2009-08-03 22:42 pluginGlue.js
-rw-r--r--  1 user user  52873 2009-08-03 22:42 storage-Legacy.js
-rw-r--r--  1 user user  55935 2009-08-03 22:42 storage-mozStorage.js
-rw-r--r--  1 user user   6667 2009-08-03 22:42 txEXSLTRegExFunctions.js
-rw-r--r--  1 user user  94449 2010-10-02 09:55 xpti.dat
-rw-r--r--  1 user user 335901 2009-08-03 22:42 xulrunner.xpt

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/defaults:
total 20
drwxr-xr-x  5 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 autoconfig
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 pref
drwxr-xr-x  4 user user 4096 2010-10-02 09:55 profile

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/defaults/autoconfig:
total 20
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 5 user user 4096 2010-10-02 09:55 ..
-rw-r--r-- 1 user user   87 2009-08-03 22:42 platform.js
-rw-r--r-- 1 user user 7296 2009-08-03 22:42 prefcalls.js

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/defaults/pref:
total 12
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 5 user user 4096 2010-10-02 09:55 ..
-rw-r--r-- 1 user user 3867 2009-08-03 22:42 xulrunner.js

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/defaults/profile:
total 20
drwxr-xr-x 4 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 5 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 chrome
-rw-r--r-- 1 user user  153 2009-08-03 22:42 localstore.rdf
drwxr-xr-x 3 user user 4096 2010-10-02 09:55 US

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/defaults/profile/chrome:
total 16
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 4 user user 4096 2010-10-02 09:55 ..
-rw-r--r-- 1 user user 1078 2009-08-03 22:42 userChrome-example.css
-rw-r--r-- 1 user user  663 2009-08-03 22:42 userContent-example.css

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/defaults/profile/US:
total 16
drwxr-xr-x 3 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 4 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 chrome
-rw-r--r-- 1 user user  153 2009-08-03 22:42 localstore.rdf

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/defaults/profile/US/chrome:
total 16
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:55 ..
-rw-r--r-- 1 user user 1078 2009-08-03 22:42 userChrome-example.css
-rw-r--r-- 1 user user  663 2009-08-03 22:42 userContent-example.css

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/dictionaries:
total 608
drwxr-xr-x  2 user user   4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user   4096 2010-10-02 09:55 ..
-rw-r--r--  1 user user   3114 2009-08-03 22:42 en-US.aff
-rw-r--r--  1 user user 609731 2009-08-03 22:42 en-US.dic

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/greprefs:
total 92
drwxr-xr-x  2 user user  4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user  4096 2010-10-02 09:55 ..
-rw-r--r--  1 user user 77411 2009-08-03 22:42 all.js
-rw-r--r--  1 user user  3442 2009-08-03 22:42 security-prefs.js
-rw-r--r--  1 user user    85 2009-08-03 22:42 xpinstall.js

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/modules:
total 256
drwxr-xr-x  2 user user  4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user  4096 2010-10-02 09:55 ..
-rw-r--r--  1 user user  2730 2009-08-03 22:42 debug.js
-rw-r--r--  1 user user  2716 2009-08-03 22:42 DownloadLastDir.jsm
-rw-r--r--  1 user user 17316 2009-08-03 22:42 DownloadUtils.jsm
-rw-r--r--  1 user user  7039 2009-08-03 22:42 ISO8601DateUtils.jsm
-rw-r--r--  1 user user 66415 2009-08-03 22:42 Microformats.js
-rw-r--r--  1 user user  4354 2009-08-03 22:42 NetUtil.jsm
-rw-r--r--  1 user user 25737 2009-08-03 22:42 PlacesDBUtils.jsm
-rw-r--r--  1 user user  7691 2009-08-03 22:42 PluralForm.jsm
-rw-r--r--  1 user user 16019 2009-08-03 22:42 SpatialNavigation.js
-rw-r--r--  1 user user 68328 2009-08-03 22:42 utils.js
-rw-r--r--  1 user user  3607 2009-08-03 22:42 WindowDraggingUtils.jsm
-rw-r--r--  1 user user 10100 2009-08-03 22:42 XPCOMUtils.jsm

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/plugins:
total 68
drwxr-xr-x  2 user user  4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user  4096 2010-10-02 09:55 ..
-rw-r--r--  1 user user 60928 2009-08-03 22:42 npnul32.dll

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/res:
total 264
drwxr-xr-x  6 user user  4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user  4096 2010-10-02 09:55 ..
-rw-r--r--  1 user user    59 2009-08-03 22:42 arrowd.gif
-rw-r--r--  1 user user    56 2009-08-03 22:42 arrow.gif
-rw-r--r--  1 user user   253 2009-08-03 22:42 broken-image.png
-rw-r--r--  1 user user 11207 2009-08-03 22:42 charsetalias.properties
-rw-r--r--  1 user user  8845 2009-08-03 22:42 charsetData.properties
-rw-r--r--  1 user user 11637 2009-08-03 22:42 contenteditable.css
-rw-r--r--  1 user user  1861 2009-08-03 22:42 designmode.css
drwxr-xr-x  2 user user  4096 2010-10-02 09:55 dtd
-rw-r--r--  1 user user 10740 2009-08-03 22:42 EditorOverride.css
drwxr-xr-x  2 user user  4096 2010-10-02 09:55 entityTables
drwxr-xr-x  2 user user  4096 2010-10-02 09:55 fonts
-rw-r--r--  1 user user 16031 2009-08-03 22:42 forms.css
-rw-r--r--  1 user user   858 2009-08-03 22:42 grabber.gif
-rw-r--r--  1 user user   117 2009-08-03 22:42 hiddenWindow.html
drwxr-xr-x  2 user user  4096 2010-10-02 09:55 html
-rw-r--r--  1 user user 11373 2009-08-03 22:42 html.css
-rw-r--r--  1 user user  6079 2009-08-03 22:42 langGroups.properties
-rw-r--r--  1 user user  5528 2009-08-03 22:42 language.properties
-rw-r--r--  1 user user   268 2009-08-03 22:42 loading-image.png
-rw-r--r--  1 user user 14682 2009-08-03 22:42 mathml.css
-rw-r--r--  1 user user 11356 2009-08-03 22:42 quirk.css
-rw-r--r--  1 user user  2313 2009-08-03 22:42 svg.css
-rw-r--r--  1 user user    58 2009-08-03 22:42 table-add-column-after-active.gif
-rw-r--r--  1 user user   826 2009-08-03 22:42 table-add-column-after.gif
-rw-r--r--  1 user user   826 2009-08-03 22:42 table-add-column-after-hover.gif
-rw-r--r--  1 user user    57 2009-08-03 22:42 table-add-column-before-active.gif
-rw-r--r--  1 user user   825 2009-08-03 22:42 table-add-column-before.gif
-rw-r--r--  1 user user   825 2009-08-03 22:42 table-add-column-before-hover.gif
-rw-r--r--  1 user user    57 2009-08-03 22:42 table-add-row-after-active.gif
-rw-r--r--  1 user user   826 2009-08-03 22:42 table-add-row-after.gif
-rw-r--r--  1 user user   826 2009-08-03 22:42 table-add-row-after-hover.gif
-rw-r--r--  1 user user    57 2009-08-03 22:42 table-add-row-before-active.gif
-rw-r--r--  1 user user   825 2009-08-03 22:42 table-add-row-before.gif
-rw-r--r--  1 user user   825 2009-08-03 22:42 table-add-row-before-hover.gif
-rw-r--r--  1 user user   835 2009-08-03 22:42 table-remove-column-active.gif
-rw-r--r--  1 user user   841 2009-08-03 22:42 table-remove-column.gif
-rw-r--r--  1 user user   841 2009-08-03 22:42 table-remove-column-hover.gif
-rw-r--r--  1 user user   835 2009-08-03 22:42 table-remove-row-active.gif
-rw-r--r--  1 user user   841 2009-08-03 22:42 table-remove-row.gif
-rw-r--r--  1 user user   841 2009-08-03 22:42 table-remove-row-hover.gif
-rw-r--r--  1 user user  6580 2009-08-03 22:42 ua.css
-rw-r--r--  1 user user  3062 2009-08-03 22:42 viewsource.css
-rw-r--r--  1 user user  2080 2009-08-03 22:42 wincharset.properties

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/res/dtd:
total 84
drwxr-xr-x 2 user user  4096 2010-10-02 09:55 .
drwxr-xr-x 6 user user  4096 2010-10-02 09:55 ..
-rw-r--r-- 1 user user 63788 2009-08-03 22:42 mathml.dtd
-rw-r--r-- 1 user user  8427 2009-08-03 22:42 xhtml11.dtd

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/res/entityTables:
total 96
drwxr-xr-x 2 user user  4096 2010-10-02 09:55 .
drwxr-xr-x 6 user user  4096 2010-10-02 09:55 ..
-rw-r--r-- 1 user user  3690 2009-08-03 22:42 html40Latin1.properties
-rw-r--r-- 1 user user  2396 2009-08-03 22:42 html40Special.properties
-rw-r--r-- 1 user user  4090 2009-08-03 22:42 html40Symbols.properties
-rw-r--r-- 1 user user  1967 2009-08-03 22:42 htmlEntityVersions.properties
-rw-r--r-- 1 user user 30004 2009-08-03 22:42 mathml20.properties
-rw-r--r-- 1 user user 39989 2009-08-03 22:42 transliterate.properties

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/res/fonts:
total 92
drwxr-xr-x 2 user user  4096 2010-10-02 09:55 .
drwxr-xr-x 6 user user  4096 2010-10-02 09:55 ..
-rw-r--r-- 1 user user 56411 2009-08-03 22:42 mathfont.properties
-rw-r--r-- 1 user user  3902 2009-08-03 22:42 mathfontStandardSymbolsL.properties
-rw-r--r-- 1 user user  5493 2009-08-03 22:42 mathfontSTIXNonUnicode.properties
-rw-r--r-- 1 user user  3033 2009-08-03 22:42 mathfontSTIXSize1.properties
-rw-r--r-- 1 user user  3954 2009-08-03 22:42 mathfontSymbol.properties
-rw-r--r-- 1 user user  6719 2009-08-03 22:42 mathfontUnicode.properties

./.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/res/html:
total 12
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 6 user user 4096 2010-10-02 09:55 ..
-rw-r--r-- 1 user user  619 2009-08-03 22:42 folder.png

./.wine/drive_c/windows/system32/mui:
total 20
drwxr-xr-x 2 user user  4096 2010-10-02 09:55 .
drwxr-xr-x 7 user user 16384 2010-10-02 09:55 ..

./.wine/drive_c/windows/system32/spool:
total 28
drwxr-xr-x 4 user user  4096 2010-10-02 09:55 .
drwxr-xr-x 7 user user 16384 2010-10-02 09:55 ..
drwxr-xr-x 3 user user  4096 2010-10-02 09:55 drivers
drwxr-xr-x 2 user user  4096 2010-10-02 09:55 printers

./.wine/drive_c/windows/system32/spool/drivers:
total 12
drwxr-xr-x 3 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 4 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 color

./.wine/drive_c/windows/system32/spool/drivers/color:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/windows/system32/spool/printers:
total 8
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 4 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/windows/system32/wbem:
total 20
drwxr-xr-x 2 user user  4096 2010-10-02 09:55 .
drwxr-xr-x 7 user user 16384 2010-10-02 09:55 ..

./.wine/drive_c/windows/temp:
total 8
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user 4096 2010-10-02 09:55 ..

./.wine/drive_c/windows/winsxs:
total 12
drwxr-xr-x  3 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 10 user user 4096 2010-10-02 09:55 ..
drwxr-xr-x  2 user user 4096 2010-10-02 09:55 manifests

./.wine/drive_c/windows/winsxs/manifests:
total 12
drwxr-xr-x 2 user user 4096 2010-10-02 09:55 .
drwxr-xr-x 3 user user 4096 2010-10-02 09:55 ..
-rw-r--r-- 1 user user 1575 2010-10-02 09:55 x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.2600.2982_none_deadbeef.manifest

```
(Note: ls-lRa.txt text file was too big to be attached)

Apparently there are multiple "passphrases":
- There is the** login password **(for the user & for root which is the same) ... I know this
- There is apparently a **"login passphrase"** which ecryptfs-mount-private asks for (what's this?)
- There is also a **"mount passphrase"**, which I presume is the thing that was auto-generated by Ubuntu

What is the difference between them?

PS: I'm reading this reference which might help me access my encrypted data with just my login password (which is all I needed up 'till now anyway):
[http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu/](http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu/)

---

### Post by rocksockdoc on 2010-10-02
I'm soooo confused about what the difference is between:
- login password (which I KNOW)
- login passphrase (what is that?)
- mount passphrase (what is that?)

Following Irish Penguin instructions **"**[Accessing your encrypted home directory in Ubuntu]("http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu/")"

**Step 1: Getting the all-important mount passphrase**

```

ecryptfs-unwrap-passphrase /home/.ecryptfs/ubuntu_user/.ecryptfs/wrapped-passphrase

```

Unfortunately, I have NO IDEA what this guy is saying (is English his native language?) when he then says ... 
```

Then time your normal login passphrase to to reveal the mount passphrase and record it somewhere as you’ll need it later.

```

Since I have no idea what he's saying, I simply enter the only password I know, which is the user (and root) password I've been using for the past month.

Unfortunately, that gets the error:
```

user@donna:~$ pwd
/home/user
user@donna:~$ ecryptfs-unwrap-passphrase /home/.ecryptfs/ubuntu_user/.ecryptfs/wrapped-passphrase
Passphrase: 
Error: Unwrapping passphrase failed [-5]
Info: Check the system log for more information from libecryptfs

```

So, when I check the log files:
```

user@donna:~$ ls -ltr /var/log | tail -3
-rw-r----- 1 syslog            adm   353332 2010-10-02 16:02 daemon.log
-rw-r----- 1 syslog            adm    52322 2010-10-02 16:06 user.log
-rw-r----- 1 syslog            adm   530538 2010-10-02 16:06 syslog

```

I see "syslog" and "user.log" seem to be the last two files written:
```

user@donna:~$ tail -2 /var/log/syslog
Oct  2 16:04:41 donna ecryptfs-unwrap-passphrase: Error attempting to open [/home/.ecryptfs/ubuntu_user/.ecryptfs/wrapped-passphrase] for reading
Oct  2 16:06:03 donna ecryptfs-unwrap-passphrase: Error attempting to open [/home/.ecryptfs/ubuntu_user/.ecryptfs/wrapped-passphrase] for reading

```
```

user@donna:~$ tail -2 /var/log/user.log
Oct  2 16:04:41 donna ecryptfs-unwrap-passphrase: Error attempting to open [/home/.ecryptfs/ubuntu_user/.ecryptfs/wrapped-passphrase] for reading
Oct  2 16:06:03 donna ecryptfs-unwrap-passphrase: Error attempting to open [/home/.ecryptfs/ubuntu_user/.ecryptfs/wrapped-passphrase] for reading
user@donna:~$ 

```

So I'm back to PERMISSIONS ... 

Any idea how to solve this?

HERE IS WHAT I HAVE:
a) I have the user and root login (which is all I needed up 'till now)

HERE IS WHAT I DON'T HAVE:
a) I don't know what the "login passphrase" or "mount passphrase" is (I don't even know the difference between them)
b) I don't have the permissions right on my /home/user directory
c) At the moment, my real /home/user directory is not mounted!

---

### Post by rocksockdoc on 2010-10-02
Note: I just saw, after I posted, your posts (second time this happened), so, I will try what you suggested and report back.

I also just noticed in the above I should have literally substituted "user" for "ubuntu_user" ... so I will try again & report back.

Keep the ideas coming as there MUST be a way to get back to where I was!

---

### Post by rocksockdoc on 2010-10-02
PROGRESS!

I was able, using the cryptic command below, to re-generate a cryptic passphrase!

I have no idea what this passphrase is (login passphrase vs mount passphrase) but at least it's progress.

Following directions here ... 
```

user@donna:~$ pwd
/home/user
user@donna:~$ ecryptfs-unwrap-passphrase /home/.ecryptfs/user/.ecryptfs/wrapped-passphrase

```

That command asked me for "Passphrase" ... so I gave it the ONLY password I know, which is the user/root password and it GENERATED (something)!!!!!!!!!!
```

Passphrase: 
bfb3fc19842eade0b79ca4e7249ebe71
user@donna:~$ 

```

[COLOR=DarkRed]**I am not sure what to do NEXT ... but I made sure to WRITE this 32-bit number (whatever it is) down on my whiteboard!!!!!!!**[/COLOR]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171118&stc=1&d=1286061759[/IMG]

---

### Post by rocksockdoc on 2010-10-02
All I know, for sure, is the password for the user (and root which is the same).
The rest I'm generating with these commands:

```

user@donna:~$ **sudo ecryptfs-add-passphrase --fnek**

```That command asked for the user's password, which I entered:
```

[sudo] password for user: **foobar**

```Then, it asked for the "Passphrase" (which we generated in the prior post):
```

Passphrase: **bfb3fc19842eade0b79ca4e7249ebe71**
Inserted auth tok with sig [5eaa38e46b503148] into the user session keyring
Inserted auth tok with sig [**[COLOR=DarkRed]2a1860e7cb545c30[/COLOR]**] into the user session keyring
user@donna:~$ 

```

[COLOR=DarkRed]**According to the[ Irish Penguin]("http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu/comment-page-1/#comment-13741"), that second "FNEK signature" is needed later in the manual decryption process.**[/COLOR]

So, for cryptic terms we have the following terms used by the software:
- User's login password (this is all that I know) i.e.,** foobar**
- Mount passphrase (I just generated this in the prior post) **bfb3fc19842eade0b79ca4e7249ebe71**
- Login passphrase (this seems to be a bug in the Ubuntu gui in that it's the same, I think, as the login password)
- Signature (I just generated this now)[COLOR=Black]: **2a1860e7cb545c30**[/COLOR]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171120&stc=1&d=1286063094[/IMG]

---

### Post by rocksockdoc on 2010-10-02
> **nerdy_kid said:**
> 
- go into recovery mode by hitting shift as the system boots
- selecting recovery
- choose root prompt  (Netroot - Drop to root shell prompt with networking, give root password for maintenance)
- adduser help
- addgroup help admin
- then reboot
- login to the new user.


Now I am logged in as user "help" with admin privilages.

> **nerdy_kid said:**
> 
- open a terminal.
- go to the encypted home of the old user 
- do the ./ecryptfs-mount-private thing   (The passphrase is your original user's password)
- once it is mounted, switch to the orginal user in the terminal:
- sudo -i -u USER_NAME
- make sure you are in your $HOME.  then do 
- chmod -R u+rw *
- you should have write access again.  
- switch sessions and log in to the orginal user.  
- confirm that everything works right.  if not...
- go back to the help account and do
- chmod -R u+rw .*
- try again.


```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
help@donna:~$ cd ~user
help@donna:/home/user$ pwd
/home/user
help@donna:/home/user$ ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly
help@donna:/home/user$ 

```

Hmmmmmmmmm. I wonder why I get the Ubuntu error:
**[COLOR=DarkRed]ERROR: Encrypted private directory is not setup properly[/COLOR]**

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171122&stc=1&d=1286066056[/IMG]

---

### Post by rocksockdoc on 2010-10-02
> **rocksockdoc said:**
> **[COLOR=DarkRed]ERROR: Encrypted private directory is not setup properly[/COLOR]**

I'm a little confused why I get that error when I log in as "help" and then run the ecryptfs-mount-private command as login "help" in the "user" directory.

But both these references say that I have to actually boot from a different operating system:
[- Recovering Your Data Manually]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually")
[- Accessing your encrypted home directory in Ubuntu]("http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu/")

So I'll try that next.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171123&stc=1&d=1286067214[/IMG]

---

### Post by rocksockdoc on 2010-10-02
More progress ... 

Following the instructions verbatim at:
[http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu/](http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu/)
**Step 2: Accessing the encrypted home directory from another O.S.**

0. I hooked up a USB CDROM to the IBM X61 tablet PC & placed a Ubuntu 10.04 Live CD.
1. The laptop didn't boot to the CD so I pressed F1 at the Lenovo prompt to change the BIOS.
2. Then I booted to the Ubunto Live CD
3. My first task was to find the path to the ubuntu user home, which I found by:
```

ubuntu@ubuntu:~$ **pwd**
/home/ubuntu

```4. My second task was to create the mount point for the desired files:
```

**mkdir /home/ubuntu/OtherHome**

```5. My third task was to find the path to the "user" filesystem of interest.
6. In the Gnome GUI, I could see "media" -> "115 GB Filesystem" -> "home" -> "user"
7. Right click on "115 GB Filesystem"-> "Properties" revealed 9807531b-98b3-4fb0-9cd9-91e726e5ac68
8. That makes the path to the .Private directory the following:
/media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home/.ecryptfs/user/.Private/
9. My next task was to find if I needed to install the "ecryptfs-utils" with apt-get ... 
```

sudo apt-get install ecryptfs-utils

```It turned out that the ecryptfs-utils were already installed:
```

ubuntu@ubuntu:~$ **which ecryptfs-add-passphrase**
/usr/bin/ecryptfs-add-passphrase
ubuntu@ubuntu:~$ **which ecryptfs-mount-private**
/usr/bin/ecryptfs-mount-private
ubuntu@ubuntu:~$ 

```10. So, skipping that install step, I moved on by following instructions to mount the other home:
```

ubuntu@ubuntu:~$ **pwd**
/home/ubuntu
ubuntu@ubuntu:~$ **sudo mount -t ecryptfs /media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home/.ecryptfs/user/.Private/ /home/ubuntu/OtherHome**
Passphrase: **bfb3fc19842eade0b79ca4e7249ebe71**
**[COLOR=DarkRed]  Note: This is the 32-character "mount passphrase" obtained  from the prior post.[/COLOR]**
Select cipher:
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: **1**
Select key bytes:
 1) 16
 2) 32
 3) 24
Selection [16]: **1**
Enable plaintext passthrough (y/n) [n]:** n**
Enable filename encryption (y/n) [n]: **y**
Filename Encryption Key (FNEK) Signature [5eaa38e46b503148]: **0e2fdf879adf3e1e**
**[COLOR=DarkRed]  Note: This is the 16-character "FNEK Signature" obtained from the prior post.[/COLOR]**
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=0e2fdf879adf3e1e
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=5eaa38e46b503148
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key
before. This could mean that you have typed your
passphrase wrong.

Would you like to proceed with the mount (yes/no)? :** y**
Would you like to proceed with the mount (yes/no)? : **yes**
Would you like to append sig [5eaa38e46b503148] to
[/root/.ecryptfs/sig-cache.txt]
in order to avoid this warning in the future (yes/no)? : **no**
Not adding sig to user sig cache file; continuing with mount.
**[COLOR=DarkRed]Mounted eCryptfs[/COLOR]**
ubuntu@ubuntu:~$

```At this point, I still do NOT see the desired files, but, at least I have the old filesystem mounted and I can see the OtherHome. :(

The desired files are SUPPOSED to be unencrypted by now!
At this point, I need expert advice.

**[COLOR=DarkRed]WHY do I not see my files unencrypted at this point? (see screenshot below).[/COLOR]**

---

### Post by rocksockdoc on 2010-10-02
**[COLOR=DarkRed]Where did my data go?[/COLOR]**

While booted to the Ubuntu live CD, I then changed the permissions of the original /home/user to 777:

```

ubuntu@ubuntu:~$ **cd /media/*/home**
ubuntu@ubuntu:/media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home$** sudo chmod -R 777 user**
ubuntu@ubuntu:/media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home$** ls -l user**
total 796
lrwxrwxrwx 1 1000 1000     56 2010-08-12 11:26 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
drwxrwxrwx 2 1000 1000   4096 2010-10-02 14:43 Desktop
drwxrwxrwx 2 1000 1000   4096 2010-10-02 14:43 Documents
drwxrwxrwx 2 1000 1000   4096 2010-10-02 14:43 Downloads
-rwxrwxrwx 1 1000 1000 548864 2010-10-02 23:06 logfile.txt
-rwxrwxrwx 1 1000 1000 196897 2010-10-02 22:51 ls_-lRa.txt
-rwxrwxrwx 1 1000 1000  29925 2010-10-02 22:51 ls_-lRa.txt.tar.gz
drwxrwxrwx 2 1000 1000   4096 2010-10-02 14:43 Music
drwxrwxrwx 2 1000 1000   4096 2010-10-02 14:43 Pictures
drwxrwxrwx 2 1000 1000   4096 2010-10-02 14:43 Public
lrwxrwxrwx 1 1000 1000     52 2010-08-12 11:26 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
drwxrwxrwx 2 1000 1000   4096 2010-10-02 14:43 Templates
drwxrwxrwx 2 1000 1000   4096 2010-10-02 14:43 Videos
ubuntu@ubuntu:/media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home$ ls -alsF user
total 1144
  4 drwxrwxrwx 36 1000 1000   4096 2010-10-03 01:46 ./
  4 drwxr-xr-x  5 root root   4096 2010-10-02 23:58 ../
  0 lrwxrwxrwx  1 1000 1000     56 2010-08-12 11:26 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
  4 drwxrwxrwx  3 1000 1000   4096 2010-10-02 17:31 .adobe/
  4 -rwxrwxrwx  1 1000 1000   2340 2010-10-03 01:05 .bash_history*
  4 drwxrwxrwx  4 1000 1000   4096 2010-10-03 01:06 .cache/
  4 drwxrwxrwx  3 1000 1000   4096 2010-10-02 16:35 .compiz/
  4 drwxrwxrwx 12 1000 1000   4096 2010-10-02 21:49 .config/
  4 drwxrwxrwx  3 1000 1000   4096 2010-10-02 14:43 .dbus/
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 14:43 Desktop/
  4 -rwxrwxrwx  1 1000 1000     41 2010-10-03 01:06 .dmrc*
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 14:43 Documents/
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 14:43 Downloads/
  0 lrwxrwxrwx  1 1000 1000     30 2010-08-12 11:26 .ecryptfs -> /home/.ecryptfs/user/.ecryptfs
  4 -rwxrwxrwx  1 1000 1000     16 2010-10-02 14:43 .esd_auth*
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 17:12 .fontconfig/
  4 drwxrwxrwx  4 1000 1000   4096 2010-10-03 01:06 .gconf/
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-03 01:46 .gconfd/
  4 drwxrwxrwx  4 1000 1000   4096 2010-10-02 17:12 .gegl-0.0/
  4 drwxrwxrwx 22 1000 1000   4096 2010-10-02 18:23 .gimp-2.6/
  4 drwxrwxrwx  9 1000 1000   4096 2010-10-03 01:46 .gnome2/
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 14:55 .gnome2_private/
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 17:21 .gstreamer-0.10/
  4 -rwxrwxrwx  1 1000 1000    132 2010-10-03 01:06 .gtk-bookmarks*
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 14:43 .gvfs/
  4 -rwxrwxrwx  1 1000 1000   1884 2010-10-03 01:06 .ICEauthority*
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 16:45 .icons/
  4 drwxrwxrwx  3 1000 1000   4096 2010-10-02 14:47 .local/
536 -rwxrwxrwx  1 1000 1000 548864 2010-10-02 23:06 logfile.txt*
196 -rwxrwxrwx  1 1000 1000 196897 2010-10-02 22:51 ls_-lRa.txt*
 32 -rwxrwxrwx  1 1000 1000  29925 2010-10-02 22:51 ls_-lRa.txt.tar.gz*
  4 drwxrwxrwx  3 1000 1000   4096 2010-10-02 17:31 .macromedia/
  4 drwxrwxrwx  4 1000 1000   4096 2010-10-02 14:55 .mozilla/
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 14:43 Music/
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 14:43 .nautilus/
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 14:43 Pictures/
  0 lrwxrwxrwx  1 1000 1000     29 2010-08-12 11:26 .Private -> /home/.ecryptfs/user/.Private
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 14:43 Public/
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-03 01:06 .pulse/
  4 -rwxrwxrwx  1 1000 1000    256 2010-10-02 14:43 .pulse-cookie*
  0 lrwxrwxrwx  1 1000 1000     52 2010-08-12 11:26 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 17:05 .recently-used.xbel/
  0 -rwxrwxrwx  1 1000 1000      0 2010-10-02 14:49 .sudo_as_admin_successful*
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 14:43 Templates/
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 16:45 .themes/
  4 drwxrwxrwx  4 1000 1000   4096 2010-10-02 16:45 .thumbnails/
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 17:16 .TrueCrypt/
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-03 01:40 .update-notifier/
  4 drwxrwxrwx  2 1000 1000   4096 2010-10-02 14:43 Videos/
  4 -rwxrwxrwx  1 1000 1000   3628 2010-10-02 22:51 .viminfo*
  4 drwxrwxrwx  4 1000 1000   4096 2010-10-02 16:56 .wine/
  8 -rwxrwxrwx  1 1000 1000   4961 2010-10-03 01:46 .xsession-errors*
200 -rwxrwxrwx  1 1000 1000 197037 2010-10-02 23:51 .xsession-errors.old*
ubuntu@ubuntu:/media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home$ 

```[B]

But, my missing data is STILL missing (it was there before the reboot earlier this morning)![/B]

**[COLOR=DarkRed]There is something very fundamental I do not understand! :([/COLOR]**

Where is the missing data? It should no longer be encrypted! 

Just in case, I tried to run the decryption again (even though it should be decrypted already):
```

ubuntu@ubuntu:/media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home/user$** pwd**
/media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home/user
ubuntu@ubuntu:/media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home/user$ **cat README.txt**

 THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.
 From the graphical desktop, click on:
  "Access Your Private Data"
 or
 From the command line, run:
 
 ecryptfs-mount-private
ubuntu@ubuntu:/media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home/user$** ecryptfs-mount-private**
[COLOR=DarkRed]** ERROR: Encrypted private directory is not setup properly**[/COLOR]
ubuntu@ubuntu:/media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home/user$ 

```[B][COLOR=DarkRed]

I am stuck. What basic action am I missing? Where is my encrypted (should be decrypted) data hiding?
[/COLOR][/B]

---

### Post by rocksockdoc on 2010-10-03
As is common when things go wrong inexplicably, I'm looking for where things could have gone wrong.

One place that is confusing is the "FNEK Signature" input (which gives different output).

Sometimes when I ran the command below, it asked ONLY for the "mount passphrase":
```

sudo ecryptfs-add-passphrase --fnek

```Yet, other times, it asked for BOTH the "user password" and the "mount passphrase".

The output is different depending on what passphrase you feed it (see the two screenshots below).

How can that be that sometimes it asks for both the user & mount passphrase while at other times it only asks for the mount passphrase?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171143&stc=1&d=1286081039[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171144&stc=1&d=1286081042[/IMG]

---

### Post by rocksockdoc on 2010-10-03
As is normal with Operating Systems, when something goes wrong, you have to look at it critically.
I rebooted to the Ubuntu Live CD, and w/o even having to mount the original file system I switched user to root and tried th chmod it.

What does THIS tell you?
[B][COLOR=DarkRed]chmod: cannot operate on dangling symlink `.ecryptfs'
chmod: cannot operate on dangling symlink `.Private'[/COLOR][/B]

Do you think THAT is the reason this isn't working?

Specifically:
```

root@ubuntu:/media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home/user#** pwd**
/media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home/user

``````

root@ubuntu:/media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home/user# **chmod -R 777 .??***
chmod: cannot operate on dangling symlink `.ecryptfs'
chmod: cannot operate on dangling symlink `.Private'

```

---

### Post by rocksockdoc on 2010-10-03
This encryption stuff is complicated.  But if I knew the answer to simple questions, it would be a whole lot easier.

For example, WHERE are the encrypted files SUPPOSED to be?

For example:
```

** ls -alsF /media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home/user/.ecryptfs**
REPORTS:
0 lrwxrwxrwx 1 1000 1000 30 2010-08-12 11:26 /media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home/user/.ecryptfs -> /home/.ecryptfs/user/.ecryptfs

```

And, an ls of that symbolic link reveals a "No such file or directory" error:
```

**ls /home/.ecryptfs/user/.ecryptfs**
REPORTS:
[COLOR=DarkRed]**ls: cannot access /home/.ecryptfs/user/.ecryptfs: No such file or directory**[/COLOR]

```

But, if I ls the entire path, it finds stuff:
```

**ls -alsF /media/9807531b-98b3-4fb0-9cd9-91e726e5ac68/home/.ecryptfs/user/**
REPORTS:
total 32
 4 drwxrwxrwx  4 1000 1000  4096 2010-08-12 11:26 ./
 4 drwxrwxrwx  3 root root  4096 2010-08-12 11:26 ../
 4 drwxrwxrwx  2 1000 1000  4096 2010-10-02 16:42 .ecryptfs/
20 drwxrwxrwx 60 1000 1000 20480 2010-10-02 19:17 .Private/

```

Since "something" is not working ... I have to look for culprits ... 
Do you think the symbolic link to slash is cause for concern?

How would I fix that?

---

### Post by nerdy_kid on 2010-10-03
i am going to try and reproduce your problem.  my previous post was all from memory -- i had forgotten about the mount password.  I'll get back asap

---

### Post by rocksockdoc on 2010-10-03
> **nerdy_kid said:**
> i am going to try and reproduce your problem.

Thanks. 

When something goes wrong that should be working ... we have to dig into the smallest discrepancies.

I slept on it and I'm wondering if the reason the same commands ask different questions is that it might depend on the USER running the command. Can that be? Or if you've booted from a different operating system? (Note: I'm booting from the SAME liveCD that I used to install the operating system a month ago).

That is, if you're the original "user", maybe it asks for both the login password and the mount passphrase.
However, if you've booted from the live CD and now you're the "ubuntu" user, maybe that's why it skips asking for the login password and uses the mount password only.

Or ... maybe the timeout for the sudo password is still in effect so it's using a cached login password.

**[COLOR=DarkRed]The reason it matters is I need to get the right "FNEK Signature".[/COLOR]**

So far, there are TWO sets of FNEK Signatures ... and I'm not sure which is the right one.
- Inserted auth tok with sig [**5eaa38e46b503148**] into the user session keyring
- Inserted auth tok with sig [**2a1860e7cb545c30**] into the user session keyring

And ... 
- (I didn't write down the first FNEK signature )  
- Inserted auth tok with sig [0e2fdf879adf3e1e] into the user session  keyring

**[COLOR=DarkRed]Do you think all this "inserting of auth tok" is "damaging" my keyring?[/COLOR]**
**What ARE these two "signatures" anyway?**

---

### Post by rocksockdoc on 2010-10-03
More progress ... I think I'm back to the original problem now that I've detailed how to re-discover the often-lost encryption password. 

I rebooted back to the native Ubuntu on the PC, and followed the original directions. 
Given I now have all the data for the commands:
- User login passphrase (aka password) = **foobar**
- Mount passphrase = **bfb3fc19842eade0b79ca4e7249ebe71**
- Filename Encryption Key (FNEK) Signature = **2a1860e7cb545c30   **
I should be able to manually decrypt the home directory.

But, I still get a read-only error. For some reason, the missing encrypted file system refuses to mount - giving an error saying that it's read only - but I can't change the permissions until I can mount the file system.

I thought ROOT should get me out of this catch 22 ... Since I have total control over the machine, there MUST be SOMETHING I can do to change the file permissions!

Here's what transpired:
```

---
user@donna:~$ **pwd**
/home/user
---
user@donna:~$** ls**
Access-Your-Private-Data.desktop  Documents  Music     Public      Templates
Desktop                           Downloads  Pictures  README.txt  Videos
---
user@donna:~$ **cat README.txt**
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"
or
From the command line, run:
 ecryptfs-mount-private
---
user@donna:~$  **ecryptfs-mount-private**
Enter your login passphrase: **foobar**
Inserted auth tok with sig [2a1860e7cb545c30] into the user session keyring
open: Read-only file system
Error locking counteruser@donna:~$ 
---

```I'm brand new to Ubuntu ... 

[COLOR=DarkRed]**Do any longer-term Ubuntu users out there have a suggestion as to how I figure out why I don't have permission to mount the encrypted file system?**[/COLOR]

---

### Post by rocksockdoc on 2010-10-04
> **nerdy_kid said:**
> i am going to try and reproduce your problem. 

That got me thinking. If you could reproduce the problem, so could I. 

So, interestingly, while creating the "help" account worked flawlessly from the command line, I created two new encrypted home-directory accounts (user_encrypted & user_500) to test decryption and then changing of permissions.

Boy was I surprised!

The strangest thing happened upon my attempted (failed) logins to those new accounts!
I think this is the real problem as I remember similar errors (I did not write them down) initially when my problem occurred with the user account.

- Purple clouds for about a minute.
-- then --
- Could not update ICEauthority file /home/user_encrypted/.ICEauthority
- There is a problem with the configuration server. 
- (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)
-- then --
- Nautilus could not create the following required folders: 
- /home/user_encrypted/Desktop, /home/user_encrypted/.nautilus
- Before running Nautilus, please create these folders, or set permissions such that Nautulus can create them.
-- then --
- Purple clouds forever.

**[COLOR=DarkRed]Any idea how to debug ICEauthority?[/COLOR]**

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171273&stc=1&d=1286189118[/IMG]

---

### Post by rocksockdoc on 2010-10-05
For the first time, everything worked without error ... but I'm not sure what was the result!

[I followed the instructions here]("http://cole.mickens.us/blog/"):
[http://cole.mickens.us/blog/](http://cole.mickens.us/blog/)

The restult were files with the most cryptic names imaginable, e.g., 
```

ECRYPTFS_FNEK_ENCRYPTED.FWYC9xy5ahwy5URtWNEPHr7Vsl755ytfkYE4PyQxmou5O.F67Pdb0f0TXE--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtP04id5r5UWUe4v4I1zn2paE--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtP.2DnqyPIMAQW9MBV5BG9nE--
etc.

```Does anyone know how to convert these cryptic file names back to the originals?

Here is the entire sequence that generated those files:
```

----------------------------------------------------------------------------
user@donna:~$ id
uid=1000(user) gid=1000(user) groups=4(adm),20(dialout),24(cdrom),46(plugdev),
105(lpadmin),119(admin),122(sambashare),1000(user)
----------------------------------------------------------------------------
user@donna:~$ ecryptfs-unwrap-passphrase /home/.ecryptfs/user/.ecryptfs/wrapped-passphrase foobar
Passphrase: bfb3fc19842eade0b79ca4e7249ebe71
----------------------------------------------------------------------------
user@donna:~$ ecryptfs-add-passphrase --fnek
Passphrase: bfb3fc19842eade0b79ca4e7249ebe71
Inserted auth tok with sig [5eaa38e46b503148] into the user session keyring
Inserted auth tok with sig [2a1860e7cb545c30] into the user session keyring
----------------------------------------------------------------------------
mkdir /tmp/myfiles
user@donna:~$ sudo mount -t ecryptfs /home/.ecryptfs/user/.Private /tmp/myfiles
Passphrase: bfb3fc19842eade0b79ca4e7249ebe71
Select cipher:
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 1
Select key bytes:
 1) 16
 2) 32
 3) 24
Selection [16]: 1
Enable plaintext passthrough (y/n) [n]: n
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [5eaa38e46b503148]: 2a1860e7cb545c30
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=2a1860e7cb545c30
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=5eaa38e46b503148
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key
before. This could mean that you have typed your
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [5eaa38e46b503148] to
[/root/.ecryptfs/sig-cache.txt]
in order to avoid this warning in the future (yes/no)? : yes
Successfully appended new sig to user sig cache file
Mounted eCryptfs
user@donna:~$

```

However, this resulted in files of a very cryptic naming convention:
```

----------------------------------------------------------------------------
user@donna:~$ ls /tmp/myfiles
ECRYPTFS_FNEK_ENCRYPTED.FWYC9xy5ahwy5URtWNEPHr7Vsl755ytfkYE4PyQxmou5O.F67Pdb0f0TXE--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtP04id5r5UWUe4v4I1zn2paE--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtP.2DnqyPIMAQW9MBV5BG9nE--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtP2iuWNWyjF0Cnt8rPAN6tOk--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtP3HdWT-2-hzNkCQJ-5OVn9E--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtP4C..GDLstkI.o0-2MePWW---
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtP59TptupOgmVJZAvOCCFQf---
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtP-69btrX4bMpGl.4WPQQRx---
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtP6rsQK8qC73VJkWiGMPWIV---
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtP6X9e1sLg8254dAY9tRH2Ck--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtP6yMG9Ju1aNqvp2kZsMfEyU--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPAeu.avri7SlgkoElq5wnF---
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPAFMeLgSZBTj5huwBdt81T---
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPAhzqvRiyAupPshiHKCQuVE--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPBbcydJbr0zqSH0OmwQO9fU--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPBNU0tnuGbnmS6y8K4TknD---
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPc5pCQeHWPFFiFoCmsMBRc---
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPC8FLjTKF.u44YhddqCn6wU--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPc-CxZ02YMkjQVXwNXfiGEE--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPCdKm7g0BGRAzAhKvL7L1iE--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPchot4UQ9.iz..eWLqSARhE--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPcoJrqELsO52FnNo.K9Oygk--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPcw7bcsuSnNKv4AMwU0Pi1E--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPczFZaZ5FjaKi4tv69o.wS---
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPea7hYPaGayDcrhpvihWAbU--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPect2zSfjmzHUilxXHk0Xak--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPegJabJWk0nt0BhE6QEuNd---
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPf2Wp0GeduajHx7hIAPkwNk--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPGVci-yrtDom8XSZkTevPAU--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPGY61iZ7Nyn9bJAgksOmeX---
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPhbFgAUk3.F.7JKsOx9G-Sk--
ECRYPTFS_FNEK_ENCRYPTED.FWYe441bmpFQA-Q3ntUtDr5D4XKQJx0obEtPhbZGDYMo3ZPBr-dkGv9Chk--
etc.

```

Does anyone know why the file names are so cryptic?

---

### Post by rocksockdoc on 2010-10-05
Another reference: 
- [****Recovering Files From eCryptfs Encrypted Home]("http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/")** 	    **

In that reference, I found a good explanation of the fact that the SECOND key (the FNEK key) is what is needed to perform file name decryption, while the first key (the mount passphrase) is what is needed to decrypt the contents of the files.

So, I think I have a problem with that second key.

I also found that you can tell if you turned on filename encryption by looking at the file names inside the /home/user/.Private directory (which is a symbolic link to /home/.encryptfs/user/.Private ... but notice the leading slash which gets people in trouble when they boot from a Ubunto LiveCD). Better to always use the real path.

Looking in my .Private directory, I see the same weird file names so I have filename encryption turned on.

I also found that you must use "sudo" on the "ecryptfs-add-passphrase" command and on the "mount -t ecryptfs" command.

I wish people would be clear about this as you get DIFFERENT results depending upon whether you run the command as sudo or not but there is no error or warning! :(

So, I'm still not out of the woods, yet, but I'm slowly making progress.

My main problem now is that I can't read the filenames because they're encrypted so it's hard to tell what the files are (especially the binary files and directories).

---

### Post by nerdy_kid on 2010-10-08
sorry; I have been absurdly busy lately!  I haven't forgotten and will help asap

---

### Post by nerdy_kid on 2010-10-12
This thread should solve it for you: [http://ubuntuforums.org/showthread.php?t=1346854](http://ubuntuforums.org/showthread.php?t=1346854)

Your tmpfs is mounted read only (as I saw from your mount output) and it seems that that causes the "open: Read-only file system
Error locking counter" error that prevents your data from getting mounted.

---

### Post by COKEDUDE on 2010-12-12
Thank you for all this good information.

---

