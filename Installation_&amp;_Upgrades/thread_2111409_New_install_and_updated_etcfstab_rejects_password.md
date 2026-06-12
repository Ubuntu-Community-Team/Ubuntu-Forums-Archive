---
title: "New install and updated /etc/fstab rejects password"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by qianian on 2013-02-01
After cloning my / and /home to a new hard drive, I updated the /etc/fstab UUIDs and installed the drive. Now I can't log in. The login page rejects my password. I even dropped to root in recovery mode and changed the passwords from there.

Any help?

---

### Post by darkod on 2013-02-02
Hmm, if you correctly replaced the UUIDs that should be it. I would double check it again.

Also, when you say "clone" I wonder what process did you use exactly. Something like copying a partition with Gparted, or simply copying the files with cp or rsync. I would do the latter, I don't really like copying partitions in Gparted yet there seems to be many tutorials using that.

I think the UUID stays the same in that case. So, you might have double UUIDs on the system.

---

### Post by qianian on 2013-02-02
Alright... I used Clonezilla. Is /etc/fstab the only place I need to change things?

---

### Post by steeldriver on 2013-02-02
can you login via a virtual terminal (ctrl-alt-F1 etc.) or ssh session?

that will narrow it down to a true auth issue versus a X session startup issue

---

### Post by darkod on 2013-02-02
Boot the machine into live session, and in terminal check the UUIDs with:
sudo blkid

Then mount the root partition and check the content of /etc/fstab.

EDIT PS: On another note, I don't know how clonezilla clones the partition exactly, personally I wouldn't used it. With linux it's very easy to copy the files, you don't need tools like clonezilla which have limitations especially if restoring on hdd of different size.

In your place, I would check the partitions too with like:
sudo parted -l

If you still have the old disk I would consider doing it differently again. It will probably be faster than sorting this out. Is this a laptop or you can connect both disks at the same time?

---

### Post by qianian on 2013-02-02
I can log in successfully in a virtual terminal! 

I can connect externally to my original drive. I initially used fsarchiver but didn't think to update UUIDs so it couldn't mount /home.

What are my options?

---

### Post by steeldriver on 2013-02-02
> **qianian said:**
> I can log in successfully in a virtual terminal! 

so maybe permissions on your home dir got screwed up? that would prevent your GUI session from starting

```
ls -ld ~
ls -l ~/.{ICE,X}authority
```

---

### Post by qianian on 2013-02-02
Strange, I had used cp -ax for the /home contents (under a separate partition)

$ls -ld ~
drwxr-xr-x 3 1000 user 4096 Feb 1 07:29 /home/user
$ls -l ~/.{ICE,X}authority
ls : Cannot access /home/user/.ICEauthority: No such file or directory
ls : Cannot access /home/user/.Xauthority: No such file or directory

Same result with sudo ls. Should I re-copy /home contents using something else?

---

### Post by darkod on 2013-02-02
I recently moved from hdd to ssd and used cp -ax to copy my /home partition. It worked perfectly.

Since you have the old disk at hand, I suggest to:
1. Format the root partition on the new disk.
2. Use cp -ax to copy the root partition too.
3. Edit the /etc/fstab to change the root and /home UUID.
4. Chroot into the new install and run update-grub (to capture the new UUID).

That should be it I guess. You might need to also reinstall grub2 on the MBR but that's easy.

The cp -ax is sufficient from my experience. You have another issue. It might be much faster redoing everything, including copying /home again if you used clonezilla for it too.

---

### Post by qianian on 2013-02-02
Done but now the new drive doesn't boot at all. After the select which version (normal, repair) to boot it goes to black screen and says what looks like an old UUID does not exist. What am I doing wrong?

% blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="/" UUID="a2720060-831e-4003-ad00-b448a945c9f2" TYPE="ext4" 
/dev/sda5: LABEL="home" UUID="18eecef8-913b-4019-abce-3e06f69b10df" TYPE="ext4" 
/dev/sda6: UUID="af6172b2-c4a3-443b-8a40-b21fb3cb6a97" TYPE="swap" 
/dev/sr0: LABEL="sysrcd-3.0.0" TYPE="iso9660" 

/etc/fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a2720060-831e-4003-ad00-b448a945c9f2 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=18eecef8-913b-4019-abce-3e06f69b10df /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=af6172b2-c4a3-443b-8a40-b21fb3cb6a97 none            swap    sw              0       0

---

### Post by darkod on 2013-02-02
Did you do the chroot and update-grub? On another thread few weeks ago I noticed it gets stuck on the new vs old UUID when copying the root partition too (I copied only /home in my case). The grub.cfg and the grub2 on the MBR might point to the old UUID.

I would do a chroot and even reinstalling grub2 to the MBR so that it "gets" the new partitions correctly:
```
sudo mount /dev/sda1 /mnt
sudo chroot /mnt
update-grub
grub-install /dev/sda
exit
sudo umount /mnt
```

This is a short chroot version, not sure if you need the longer one just for update-grub. In case it complains about something, like missing /dev, try inserting these lines between the first mount and the chroot command:
```
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
```

That is what needs mounting and binding for full chroot and it has to work.

---

### Post by qianian on 2013-02-02
I couldn't boot into the new install so I had done update-grub from the original drive. 

Now from live disk with the target drive, I get:

% chroot
% mount /dev/sda1 /mnt
% chroot /mnt                 
chroot: failed to run command `/bin/zsh': No such file or directory

Should I try this from the original drive?

EDIT: okay, I did it from the original drive. The only part that didn't look right was umount at the end, /mnt: device is busy.

---

### Post by darkod on 2013-02-02
Hold on, what is that chroot command first? And don't run update-grub before you are "inside" the chroot successfully. It doesn't work in the live session, and it's pointless to run it from the original disk too. You want the new disk working.

Boot the machine with the ubuntu cd in live session, open terminal and execute one by one to enter the chroot into sda1 which is your root partition on the new disk I believe (note, before you start running this all should be unmounted, if either mounting of sda1 was done, unmount or use that mount point instead of /mnt):
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
update-grub
grub-install /dev/sda
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

That is the full list, run it one by one and carefully with the spelling.
Also, the cd you use doesn't need to be the exact same version of ubuntu but it does need to be the same architecture. If the installed OS is 64bit, the cd has to be of 64bit version.
The error you mention in your last post when trying chroot I think happens if you try to use different architecture.

---

### Post by qianian on 2013-02-02
Okay, I see what you mean about being in chroot now.

I ran it again from live CD and properly unmounted everything, then reboot. I now get the login screen, which goes black with "Checking battery state", then returns to the login screen.

---

### Post by darkod on 2013-02-02
OK, so it has nothing to do with grub now. When it returns to the login screen, can you log in or not?

I have seen that message about batery state mentioned, but don't know exactly when it shows. If you search the forum or google it should turn up some threads.

---

### Post by qianian on 2013-02-02
Bummer! No, it repeats it every time I enter my password.

This is one suggestion I found: [http://askubuntu.com/questions/223501/ubuntu-12-10-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-12-10-gets-stuck-in-a-login-loop)

---

### Post by steeldriver on 2013-02-02
I may be wrong about this but I *think* 'Checking battery state' just happens to be the last thing that happens before switching to the GUI session on vt7 - I don't think the it has any particular significance apart from that

At this point I would be looking at ~/.xsession-errors and possibly the /var/log/lightdm/x-0-greeter.log file for clues

---

### Post by qianian on 2013-02-02
I'm not sure how to show the /var/log/lightdm/x-0-greeter.log to you because I have to be in the virtual terminal to sudo.

Okay, what do you think of:

~/.xsession-errors
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
I/O warning : failed to load external entity "/tmp/guest-vysQPZ/.compiz/session/102212cffc3180992b135985424626766800000018540036"
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...** Message: applet now removed from the notification area
done
Initializing fade options...done
** Message: using fallback from indicator to GtkStatusIcon
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:1926): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing cube options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing mag options...done
Initializing neg options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing screenshot options...done
Initializing shift options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing thumbnail options...done
Initializing water options...done
Initializing winrules options...done
Initializing wobbly options...done
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
Setting Update "autoraise"
Setting Update "autoraise_delay"
Setting Update "toggle_window_shaded_key"
Setting Update "fullscreen_visual_bell"
Setting Update "autoraise"
Setting Update "autoraise_delay"
Setting Update "toggle_window_shaded_key"
Setting Update "fullscreen_visual_bell"
Setting Update "main_menu_key"
Setting Update "run_command_terminal_key"
Setting Update "run_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1600004

** Message: moving back from GtkStatusIcon to indicator

---

### Post by qianian on 2013-02-04
I still can't log in in the graphical session, only Guest user and the other Ctrl+Alt+Fn sessions. Any help?

---

### Post by qianian on 2013-02-08
Anyone think it might be different if I install from Live Disk while the drive is installed rather than on a USB adapter? I really need to log in.

---

### Post by qianian on 2013-02-11
I just discovered in a Guest session I can still make administrator changes by entering my user password at the prompt. I've changed my settings to automatic login=on but still get the login screen at startup. This setting is preserved after reboot. 

Any idea how to let me get in to my account in a graphical session? The other virtual sessions log in as normal and I can view my user folder and files.

---

### Post by steeldriver on 2013-02-11
> **qianian said:**
> 
$ls -ld ~
drwxr-xr-x 3 **[COLOR=Red]1000 user[/COLOR] **4096 Feb 1 07:29 /home/user


It looks like your UIDs got screwed up so that 'your' home dir no longer belongs to 'you' - that's probably preventing the X server from writing its .Xauthority file

It *may* be as simple as chown'ing /home/user - but I would recommend that you check exactly what users / UIDs /GIDs are defined and if necessary using usermod to get them all back in line (i.e. 1000 == your 'primary' user, 1001 == 'next' user etc.) otherwise you may tie yourself in more knots

You can use the 'id' command (with sudo to see other user's IDs) and/or cat the /etc/passwd and /etc/group files

---

### Post by qianian on 2013-02-14
Okay, before I try that would it make sense that the virtual sessions behave normally and I can use my user password to do su level tasks once I'm in the Guest session? I was even able to create new users in the Guest session but I can't log in to those accounts from the login screen either.

---

### Post by qianian on 2013-02-14
How do I find out what the UID and GID are right now? I see a usermod tutorial here: [http://manpages.ubuntu.com/manpages/hardy/man8/usermod.8.html]("http://manpages.ubuntu.com/manpages/hardy/man8/usermod.8.html")

Is it advisable to fix the startup login problem using adduser?

---

### Post by steeldriver on 2013-02-14
As I mentioned above, you can use the id command

```
$ sudo id steeldriver
uid=1003(steeldriver) gid=1003(steeldriver) groups=1003(steeldriver),4(adm),24(cdrom),30(dip),46(plugdev),50(staff),109(lpadmin)

```and/or look at UIDs / GIDs in the 1000's in the /etc/passwd and /etc/group files

```
$ grep '100[0-9]' /etc/passwd
``````
$ grep '100[0-9]' /etc/group
```It *looks* like you have an 'orphaned' UID (1000 - presumably the original primary user) that is no longer associated with a login name, but owns your /home/user directory

---

### Post by qianian on 2013-02-15
I think that's it! I get:

uid=501(qian) gid=1000(qian) groups=1000(qian),4adm [...]

What chmod should I run, and on any specific file in /home?

---

### Post by qianian on 2013-02-17
I also get:

$ grep '100[0-9]' /etc/passwd
qian:x:501:1000:Full Name,,,:/home/qian:/bin/bash

$ grep '100[0-9]' /etc/group
qian:x:1000:

I found [this page]("http://askubuntu.com/questions/16700/how-can-i-change-my-own-user-id") and was only able to change my UID from 501 to 1000 in /etc/passwd. I got permission denied on the commands starting with "find." Then I rebooted and am in! I'd love it if someone would explain why this mismatch was on my old drive in the first place, and why the old drive works. If there are any pitfalls from what I did please let me know too.

---

