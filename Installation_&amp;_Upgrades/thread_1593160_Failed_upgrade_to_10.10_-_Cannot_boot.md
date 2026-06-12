---
title: "Failed upgrade to 10.10 - Cannot boot"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by or1onas on 2010-10-11
Greetings to all,

I tried to do an upgrade yesterday to 10.10 (from 10.04).
It showed some errors while installing the packages and finished with messages about a failed upgrade.

I tried to re-run aptitude but it said it could not locate the file (probably messed up everything).

I then tried to reboot and now all that i get is a 'stoned' GUI with just the Ubuntu Desktop wallpaper and a popup on the bottom right corner about a Gnome Power Manager Configuration problem.
Keyboard and mouse is stoned also.

I cannot change to a console login (CTRL-ALT-F1 or anything else).

I cannot also seem to edit GRUB correctly in order to boot to another runlevel (i tried to add 1 at the end of 'linux' path but yet nothing happens).

Any ideas on how i could possibly deal with the issue would be greatly appreciated...

---

### Post by mörgæs on 2010-10-11
Does it work when booted with a live 10.10 CD?

---

### Post by or1onas on 2010-10-12
To whom it may concern:

I managed to solve the problems with the upgrade and now the system is completely stable (and upgraded to 10.10).

1. I booted from live cd and chrooted to my 'real' root path.

2. I tried to re-run "apt-get dist-upgrade" and faced multiple errors like the following:

"unable to make backup link of `./bin/ps' before installing new version: Operation not permitted"

3. For each of the files stated, (eg. /bin/ps above), i had to give a: "sudo chattr -sia /bin/ps"

4. I then restarted "apt-get dist-upgrade" and went on to the next file error, fixed it with chattr, then rerun dist-upgrade,...an so on...

After a while i managed to bypass all the above type errors.

5. The next error i had to face was the 'dbus' dependencies which could not be solved:

The 'dbus' package could not be upgraded too, so i had to remove it ("sudo apt-get remove dbus").

6. It's removal uninstalled almost everything else (ubuntu-desktop, etc).

7. During it's run, i lost GUI and had to switch to a console login (CTRL-ALT-F1).

8. When the "sudo apt-get remove dbus" command was completed, i re-run once again "apt-get dist-upgrade".

9. This time, the whole stuff was re-installed correctly (ps. GUI was not installed automatically, so i also had to run "sudo apt-get install ubuntu-desktop" afterwards).

I hope the above could help someone in the same position ;-)

---

### Post by Hamishfox on 2010-10-14
Hi,

I'm super bad at computers. Can someone tell me where my original root path would be? I think I can work out the rest of the stuff (aka google it).

I'm trying to do the thing that or1onas suggested to fix a bad upgrade.

Thanks many,

Hamish

EDIT: Never mind - I think I found it. Wish me luck.

---

### Post by Hamishfox on 2010-10-15
Ok, I give up. Can someone hold my hand and walk me through step 1 ;p

Here's where I've got so far :


I try to make a mount point - I assume this is supposed to be my root folder (/media/posey for me)

```
$ sudo mkdir /media/posey 
```This seems to work. The terminal doesn't say anything went wrong. It doesn't say anything, actually.

next I do this:

```
$ sudo mount -o bind /proc /media/posey/proc
```which returns this:

```
mount: mount point /media/posey/proc does not exist
```Here's the instructions I'm working from [http://ubuntuforums.org/showthread.php?t=1156240](http://ubuntuforums.org/showthread.php?t=1156240)

---

### Post by wilee-nilee on 2010-10-15
[QUOTE=Hamishfox;9974806]Ok, I give up. Can someone hold my hand and walk me through step 1.

Your more likely to get help if you start your own thread with a corresponding title of the problem. 

You also might checkout the bootscript in my signature, many use it to find problems and just isolate what is where. If you start a thread the script might be helpful, so if you post it put it in code tags in the reply. You just click on the # in the reply panel and code tags are generated put the code in between them.;)

---

### Post by Hamishfox on 2010-10-15
Ok thanks. I'll make a new thread now.

---

