---
title: "Unable to set up user"
date: 2004-10-23
forum: Installation &amp; Upgrades
---

### Post by steffen on 2004-10-23
I just set up Ubuntu on a formatted hardrive. However, I am not able to define a user.

When asked for the name of the account, I write 'steffen'. When asked for the username, I write 'steftorp'. Then Im asked to define the password, which I do, and then confirm it. After having done this Im just returned to the new account screen again, to go through the same procedure.

After having done this a couple of times, I decided that the account was probably set up, so I just continued the install. However, now Im not able to log in to with either my username or 'root'. I've tried all possible combinations.

If I go commandline I see that no user exists for the computer. And I'm not able to operate as root, superuser or sudo...

Anyone have any idea?

---

### Post by steffen on 2004-10-23
Just attempted a second time...still same problem. I try to set up a user, but it won't accept it. And no user, and no root is set up.

Is this a bug, or do I just not understand sudo?

---

### Post by arctic on 2004-10-23
have you checked the md5sum of your isos before burning the cd's? maybe you got a bad burn. i just installed ubuntu on another of my boxes and i never had this kind of problem. and i have done it the same way as you.

btw. there is no "root" by default in ubuntu, thus you can not log in as root unless you set up root later, once you are logged into your system.

---

### Post by steffen on 2004-10-24
I've downloaded a new file, and I'm about to burn it from command line in the Ubuntu rescue boot mode.

How do I check the md5sum before I burn the new ISO image?

---

### Post by jmings on 2004-10-24
[QUOTE=steffen]I've downloaded a new file, and I'm about to burn it from command line in the Ubuntu rescue boot mode.

How do I check the md5sum before I burn the new ISO image?[/QUOTE]

Here's burnubuntu.sh
===================================================
#!/bin/bash
grep 'warty-release-install-i386.iso$' MD5SUMS
md5sum warty-release-install-i386.iso
echo Cntl-C to abort, Enter to bu7rn CD.; read nada
cdrecord dev=/dev/hdc speed=12 -v -raw -data warty-release-install-i386.iso
warty-release-install-i386.iso
md5sum </dev/hdc
grep 'warty-release-install-i386.iso$' MD5SUMS

---

### Post by steffen on 2004-10-24
Will I be able to use this (burn CD) even though I don't have a root user, or any sudoers?

I really hope so, if not, I'm screwed...

---

### Post by steffen on 2004-10-24
Think this post might help me (putting the ISO on a separate HD partition): 

[http://www.ubuntuforums.org/showthread.php?t=880](http://www.ubuntuforums.org/showthread.php?t=880)

I partitioned a large fat32 part on my HD, and I'll stick it onto it, if cdburn doesn't work...

---

### Post by steffen on 2004-10-24
This is not a fault on the CD, it seems to be a bug in the system... Don't know how or what, thought.

Md5sums are correct, I formatted the hardrive and installed Ubuntu over again from the new CD.

Anyway, the exact same thing happens again. Get to setting up users, and I insert really simple names and passwords, but just get reverted back to setting up the username again, with the error that the username must start with a lowercase alphacharacter. 

Don't know if it matters, but I'm setting up my system with Norwegian language and keyboard layout. Other than that, it's a fairly standard laptop, Fujitsu-Siemens Amilo M, which according to other postings on the web should work with Ubuntu and Debian.

---

### Post by jdong on 2004-10-24
Boot GRUB with <b>rw init=/bin/bash</b> appended to the kernel (use the "e" key to edit the boot command).


use <b>passwd</b> to set a password for root, then reboot.


If Ubuntu's UI still doesn't work, log in as root and use useradd to make the user.

---

### Post by steffen on 2004-10-24
If I start a shell during my setup, and write 'adduser steffen' -- >Ubuntu sets up new user, new group (steffen 1000) new user (steffen 1000 with user steffen) and home directory /home/steffen

Then I receive error:
'chown 1000:1000 /home/steffen: Operation not permitted'

Then Ubuntu cleans up the directories and groups, printing only error (groupdel: group steffen does not exist)

This is all I can think of doing...

---

### Post by steffen on 2004-10-24
[QUOTE=jdong]Boot GRUB with <b>rw init=/bin/bash</b> appended to the kernel (use the "e" key to edit the boot command).


use <b>passwd</b> to set a password for root, then reboot.


If Ubuntu's UI still doesn't work, log in as root and use useradd to make the user.[/QUOTE]

Appended to kernel... How?

Thanks, by the way :)

---

### Post by steffen on 2004-10-24
OK, now I pushed e when entering Grub, entered the kernel setup, entered rw init=/bin/bash after whatever was in appended to the kernel boot (after something about splash, etc), booted the kernel (hit 'b'), and when entering shell, I did 'pwd newpass'

When I entered 'halt' afterwards to shut down my system to reboot, it didn't work, and after a while, I just hit Ctrl+Alt+Del.

My system rebooted, but when I got to X and was to key in my user and password, I entered 'root' as user and newpass as password, but it still didn't work.

Am I still doing something wrong, or should I attempt some other way?

---

### Post by jdong on 2004-10-24
Congrats on figuring out how to edit GRUB, it's a very useful technique to learn!

GNOME's GDM (Gnome Display Manager) still won't allow root logins, by feature.

Press CTRL+ALT+F1 to get to a console, log in as root. If you can figure out useradd, go ahead. If not, you may run **startx -- :1** to start Gnome at ALT+F8, then use System Configuration's User and Groups editor. Careful not to break anything as root! LOL

---

### Post by steffen on 2004-10-24
Wuhu! I managed it. Thanks for *great* help!

And I have to say, at first glance, the system doesn't seem overrated. Don't know why, but the Gnome is a lot more responsive than that of Fedora 2. The only thing that one might look into in the future is the partition wizard at the beginning, which is too week, and the little bug I managed with lots of help, to get through in this thread.

What I did:
- Tried useradd, but didn't know which groups to add, and how to assign a homedir to the user, etc. so Gnome wouldn't start.
- Then I tried startx, opened Gnome, added the user, and logged back in, without problems.

Good stuff!

Thanks! :) I'm looking forward to actually using this system.

By the way - I've now actually set a password for a root user on this system. If I was paranoid (if) ;), would someone be able to use the root account on my system, if they knew the password? And would the default Ubuntu have a working password for root? Why I'm asking? ...well, I gave root a very obvious password... ;)

---

### Post by steffen on 2004-10-24
Ohh, actually, one more hurdle...

I probably shouldn't work as root for forever, and when I'm trying to log in to my new user account, X isn't able to start, because it doesn't have permissions to write to .gnome

When I look at it, the home directory of my user is actually set to user and group 'root', but user root is not able to change this, either from Nautilus, bash or the startup rescue. Apparently, root cannot change ownership of '/home/user'. I get error 'Operation not permitted' every time, in all interfaces. Which is pretty odd, since 'root' should really be able to set the ownership of a dir that belongs to 'root'.

I also try doing this is bash with sudo chown, but I still don't manage, even after I've managed to add 'user' to /etc/sudoers with visudo and all permissions.

...and root is never asked for the password when I use sudo at all. Don't know if this is a sudo problem, or if there is another problem to give /home/user the correct ownership...?

---

### Post by steffen on 2004-10-25
I finally figured out what the problem's been all the time...

During Ubuntu setup, I partitioned the HD to have a large Fat32 partition, to contain all my documents, files, etc. I didn't bother looking into the details for this, I just specified it as a Fat32 partition, and thought I could change the specs later in fstab.

However, what I didn't know, and haven't found documentation for anywhere, is that Ubuntu automatically mounted my large Fat32 partition to /home. Of course, this is a stroke of genius, when I think about it, because it's the natural place to store all my personal files, and I won't need to go through the symlink I put in 
/home/user to get to my files.

This is slightly premature, however, because the permissions for this partition is set to defaults, which means I haven't been able to read, write or do anything to /home.

When I figured it out, I tried to change the values in /etc/fstab, and as soon as I manage to get that up and running, it should work allright.

Currently, I get the following error when trying to log into Gnome:
"Could not set mode 07000 on private user specific configuration catalog, "home
/user/.gnome2_private/". Operation not permitted."

My fstab entry for this partition looks like the following:
/dev/hda6  /home   vfat   auto,utf8,umask=0000,gid=users   0   0

Anyone know how I can make this Fat32 partition workable as /home?

---

### Post by wheatpuppet on 2005-02-22
Steffen, I've had *exactly* the same problem, described in [this thread](http://www.ubuntuforums.org/showthread.php?t=16507). I, too, suspected the fat32 partition. Good work tracking it down! Does anyone know the solution to this particularly strange problem?

---

### Post by codemac on 2005-03-20
I have the same problem as well.  Has anyone found a solution?

---

### Post by gogodidi on 2005-03-24
to set up root

open users and groups
 tick show all users
modify root to whatever
done

---

### Post by bahumbug on 2005-05-08
Hey, i had exactly the same problems and after looking around the forums, I came to the conclusion  that fat32 is not a good place to put your /home... because, from what i've learned (correct me if i'm wrong), fat32 does not have any file permission settings built in, so it causes problems setting permissions and the like in your /home (so every account will be able to see other people's accounts).  this is also the reason why i couldn't log in to gnome either i believe.

for now i think the best option is to just create a link to your fat32 partition in your /home

PEACE

---

