---
title: "Cannot boot after today's upgrade! Please help!"
date: 2010-01-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Pipps on 2010-01-06
I have run the latest automated updates today. I was asked to reboot at the end of the procedure.

On reboot, Ubuntu will now no longer boot. :(

When I boot in the alternative 'recovery mode' option in Grub, and I then select the option to repair broken packages, it is reported that there are no broken packages to repair.

How can this Ubuntu installation be repaired? :confused:

---

### Post by phillw on 2010-01-06
Hi,

Did you accept 'Partial Updates' ?

Regards,

Phill.

---

### Post by Pipps on 2010-01-06
At the update, I was not given the option for 'partial updates', as I remember I had done on a number of occasions previously.

I was given the list of available updates, and I accepted them.

What can this mean?

---

### Post by phillw on 2010-01-06
Hi, Pipps !!

I've been in 9.10 for the last couple of days, as am doing a major re-write of my Dad's company web-site. 

Hang on & see if any report similar issues, but you may be better doing a clean install as it's a very new system. But, do be real careful of partial updates (As in say **NO**) - they can bork a system. The sticky on the subject is required reading & you will also read **23meg** giving me some further guidance & how I check the partial ones, such as evolution (Use Synaptics Package mananger - It will let you know if an application is in the repositries.

Sorry I can't be of more help - I'm not due back on 10.04 until the w/end.

Regards,

Phill.

---

### Post by LKjell on 2010-01-06
> **Pipps said:**
> I have run the latest automated updates today. I was asked to reboot at the end of the procedure.

On reboot, Ubuntu will now no longer boot. :(

When I boot in the alternative 'recovery mode' option in Grub, and I then select the option to repair broken packages, it is reported that there are no broken packages to repair.

How can this Ubuntu installation be repaired? :confused:

Please be a bit more precise on no longer boot since you can boot to revocery mode...

What i mean is that can you still login?

---

### Post by Pipps on 2010-01-06
Thank you for your assistance. Allow me to provide more information.

After selecting Ubuntu 10.04 in GRUB2, the screen then goes black, in anticipation for Ubuntu to load.

I wait, and then I see the small flashing text icon appear at the top left corner of the screen, briefly, as usual.

Then the circular rotating cursor icons appears in the middle of the screen, as usual.

But it only appears for a split-second, before then flashing back to the text icon at the top left.

These two frames then flash back and forth repeatedly.

Ubuntu never boots.

What could be the problem? :confused:

Can it be fixed?

---

### Post by LKjell on 2010-01-06
You can press ctrl + alt + f1?

---

### Post by Pipps on 2010-01-06
Pressing CTRL+ALT+F1 does nothing, either when attempting to boot in kernel 2.6.32-9-generic or in its recovery mode option.

CTRL+ALT+DEL does nothing, similarly, either.

When I attempt to boot in recovery mode, I am asked for my login and password. When I then choose the option to attempt a normal boot, I am then presented with the following error message:

> 
rc-sysinit start/running, process 137

Ubuntu lucid (development branch) rp-desktop tty1

pipps-desktop login: pipps
Password:

Last login: Wed Jan 6 19:28;23 GMT 2010 on tty1run-parts: /etc/update-motd.d/91-release-upgrade exited with return code 1
Linux pipps-desktop 2.6.32-9-generic #13-Ubuntu SMP Thu Dec 17 17:01:59 UTC 2009 x86_64 GNU/Linux
pipps@pipps-desktop:

Is there any hope for me? :confused:

---

### Post by cariboo on 2010-01-06
It looks like you have a graphics problem, if you type **startx** at the prompt does it take you to the desktop?

---

### Post by Pipps on 2010-01-06
Hi Cariboo907, thank you for your input.

I typed 'startx' at the prompt, after attempting to resume a normal boot in recovery mode.

When I did, the following text ran down the screen. I took a photograph and have typed it out below:

> /urs/bing/startx: line 155: cannot create temp file for here-document: No space left on device
xauth: creating new authority file /home/pipps/.Xauthority
/urs/bin/startx: line 171: cannot create temp file for here-document: No space left on device
xauth: creating new authority file /home/pipps/.Xauthority
/usr/bin/startx: line 171: cannot create temp file for here-document: No space left on device

This is a pre-release version of the X server from the X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.7.3.901 (1.7.4 RC 1)
Release date: 2009-12-11
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux pipps-desktop 2.6.32-9-generic #13-Ubuntu SMP Thu Dec 17 17:01:59 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=//vmlinux-2.6.32-9-generic root=UUID =87732a5b-38cb-4548-b619-9a1dbed5827d ro single vga=775
Build Date: 24 December 2009 12:27:56PM
xord-server 2:1.7.3.901-1ubuntu4 (buildd@)
Current version of pixman: 0.16.2
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers:   [	0.000000] (--) proved, [	0.000020] (##) from config file, [	0.000039] (==) defailt setting,
	[0.000043] (++) from command line, [	0.000062] (!!) notice, [	0.000070] (II) informational,
	[	0.001707] (WW) warning, [	0.001723] (EE) error, [	0.001738] (MI) not implemented, [	0.001756] (??) unknown.
[	0.002646] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 6 22:21:10 2010
[	0.019569] (==) Using default built-in configuration (30 lines)
[	0.030813] (II) [KMS] Kernel modesetting enabled
record: RECORD extension enabled at configure time.
record: This extention is known to be broken, disabling extenstion now..
record [http://bugs.freedesktop.org/show_bug.cgi?id-20500](http://bugs.freedesktop.org/show_bug.cgi?id-20500)
The XKEYBOARD keymap compiler (xkbcomp) report:
> Error:		Cannot close "/tmp/file5VqPMP" properly (not enough space?)
>		Output file "/tmp/file5VqPMP" removed
Errors from xkbcomp are not fatal to the X server
[	0.287413] (EE) Error compiling keymap (-)
[	0.287443] (EE) XKB: Couldn't compile keymap
XKB: Failed to compile keymap
Keyboard initialization failed. This could be a missing or incorrect setup of xkeyboard-config.

Fatal server error:
Failed to activate core devices

Please consult the The X.Org  Foundation support
	at [http://wiki.x.org](http://wiki.x.org)
	for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information

 ddxSigGiveUp: Closing log

Backtrace:
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.
xauth: creating new authority file /home/pipps/.Xauthority
pipps@pipps-dekstop:~$
_

That is it, character for character.

What can it all mean? :confused:

---

### Post by VMC on 2010-01-06
> No space left on deviceThis looks suspicious. Type 'df' and see how much of your partition is used.

---

### Post by Pipps on 2010-01-06
On typing 'df', I am told that my Ubuntu filesystem, at sda2, is 100% full. How can this be? :confused:

I logged into LiveCD, entered sda2 as root, and deleted a 50MB file. I then emptied the LiveCD trash can. I then reboot in recovery mode again, but on typing df, I was given exact same report - 100% full... somehow! :confused:

Is there any way to delete all the temp files which may have been downloaded during the unsuccessful upgrade which I had been attempting prior to this problem arising?

Would these temp files be stored only in '/tmp' directory of sda2, and are there any which I should avoid deleting?

---

### Post by VMC on 2010-01-06
Use the following command to find large files

```
find . -xdev -printf '%s %p\n' |sort -nr|head -20
```

You can play around with the head count and replace the '.' with whatever directory you want.

---

### Post by phillw on 2010-01-06
> **Pipps said:**
> On typing 'df', I am told that my Ubuntu filesystem, at sda2, is 100% full. How can this be? :confused:

I logged into LiveCD, entered sda2 as root, and deleted a 50MB file. I then emptied the LiveCD trash can. I then reboot in recovery mode again, but on typing df, I was given exact same report - 100% full... somehow! :confused:

Is there any way to delete all the temp files which may have been downloaded during the unsuccessful upgrade which I had been attempting prior to this problem arising?

Would these temp files be stored only in '/tmp' directory of sda2, and are there any which I should avoid deleting?

Hi,

/tmp *should* clear itself out at a boot - if you look at the files, there should not be any 'old' files i.e., before your reboot.

But, that would only be on your partition that has 10.04 on it.

depending on what is going on ....

your trash could be under your user name, or under root.

                                  **Re: Cannot empty trash**             
                                                                What happened is you sent files to the trash that were owned by root (most likely). This happens a lot when you do a "sudo make install" and then trash the make directory.

Anyhow...

In a terminal:
     ```

     cd ~/.Trash 
``` and then
     ```

     sudo rm -r $FILENAME 
``` and replace $FILENAME with the name of the folder or file that refuses to be emptied from the trash.

Do bear in mind that ```
sudo rm -r
``` is **not** to be used at will, it is very dangerous, and if in *any* doubt, do not do it.

T.B.H  (IMHO) as your 10.04 install is only a couple of days old - rather than 'play' around, get a daily image & do re-install from that. If that fails, go back to alpha1 and take your time with the updates - - yeah .. pen & paper time, write them down as you put them on - one by one. Don't allow partial ones. If it then borks on you, you will know which one & be able to report it back. At least that way, we know that no 'partial' ones have sneaked on.

But, that's just IMHO - the others here are more experienced - I just do not know your base point of when it was last working and what you did (or it did) for it to break.

But, let the guyz and galz on here try to get it working 1st. A re-install from a known point is just how I would do it. :-|

Phill.

---

### Post by cariboo on 2010-01-06
I would also suggest at the prompt type:

```
sudo apt-get autoremove
```

the above command wil remove any unneeded dependencies.

And:

```
sudo apt-get clean
```

will remove archived packages from /var/cache/apt/archives.

---

### Post by phillw on 2010-01-07
+1 cariboo,

slap my wrist for not suggesting it :-\

---

### Post by tchoklat on 2010-01-07
I haver a similar issue after the upgrade , being left at a prompt. I log in and type startx only to be greeted with "exec: 3: /usr/bin/X: not found"

If I enter sudo start gdm at the prompt I get "gdm start/running, process 2232"


tony

---

### Post by Pipps on 2010-01-07
Dear Friends. Thank you so much for your prompt and expert support. I have attempted each of the following whilst LiveCD. I can report the following:

1. Visually checked the GUI trash can on the panel, which appears to be empty.

2. 'cd ~/.Trash' returns 'bash: cd: /root/.Trash: No such file or directory'. '/home/pipps/.local/share/Trash' contains three subdirectories - 'expunged', 'files' and 'info'; but  no files within those subdirectories.

3. The directory '/var/cache/apt/archives' contains two files: 'Partial' and 'lock'. Should I attempt to delete both of these?

4. Performing df in '/var/cache/apt/archives' returns the following:
> Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   1677576     49136   1628440   3% /
udev                   1677576       288   1677288   1% /dev
/dev/sdd1              1948040    706324   1241716  37% /cdrom
/dev/loop0              684032    684032         0 100% /rofs
none                   1677576       100   1677476   1% /dev/shm
tmpfs                  1677576        20   1677556   1% /tmp
none                   1677576        96   1677480   1% /var/run
none                   1677576         0   1677576   0% /var/lock
none                   1677576         0   1677576   0% /lib/init/rw
/dev/sda2              4981004   4961724         0 100% /media/87732a5b-38cb-4548-b619-9a1dbed5827d

5. The command 'sudo apt-get autoremove' returns the following:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

6. The command 'sudo apt-get clean' returns nothing.

7. The command 'find / -xdev -printf '%s %p\n' |sort -nr|head -20' returns the following:
> find: `/home/ubuntu/.gvfs': Permission denied
18597793 /usr/share/myspell/dicts/th_en_US_v2.dat
18545141 /usr/share/myspell/dicts/th_en_AU_v2.dat
13914676 /usr/lib/libicudata.so.40.1
13249170 /usr/share/fonts/truetype/wqy/wqy-zenhei.ttc
13139672 /usr/lib/xulrunner-1.9.1.3/libxul.so
12948624 /usr/lib/libwebkit-1.0.so.2.11.2
11323480 /usr/lib/openoffice/basis3.1/program/libswli.so
9531896 /usr/lib/openoffice/basis3.1/program/libscli.so
9407405 /var/cache/debconf/templates.dat
9231384 /usr/lib/openoffice/basis3.1/program/libsvxcoreli.so
9183232 /home/ubuntu/.mozilla/firefox/uktpjvzm.default/urlclassifier3.sqlite
8370720 /usr/lib/gcc/i486-linux-gnu/4.4/cc1
8292848 /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages
8220311 /var/lib/dpkg/info/ubiquity.templates
7000264 /usr/lib/libgs.so.8.70
6529024 /var/lib/apt-xapian-index/index.1/postlist.DB
6512224 /usr/bin/net.samba3
6402081 /usr/lib/openoffice/basis3.1/share/config/images_human.zip
5907648 /usr/lib/openoffice/basis3.1/program/libsdli.so
5750576 /usr/bin/rpcclient

What could be preventing Ubuntu from booting?

Would a fresh install just be best?

---

### Post by zika on 2010-01-07
> **tchoklat said:**
> I haver a similar issue after the upgrade , being left at a prompt. I log in and type startx only to be greeted with "exec: 3: /usr/bin/X: not found"

If I enter sudo start gdm at the prompt I get "gdm start/running, process 2232"
tony```
sudo srvice gdm restart
```
or```
sudo service gdm stop
sudo service gdm start
```

---

### Post by Tompalaz on 2010-01-07
Hi there, I had a similar problem that my / got full for no reason. This was in Ubuntu 9.10. I had to reinstall (and give / more space) everything as I couldn't find any solution, every time I removed something the disk was still full.

In our class we were doing some silly things with each others computers so I thought I might have got yes:ed:rolleyes:. Anyhow, as you reporting a similar problem I'd like to know how you fixed it, if you fix it.

---

### Post by KrazyPenguin on 2010-01-07
run xdiskusage and see what location the disk is full at (such as a log file) and delete it.

good luck!!

---

### Post by Pipps on 2010-01-07
Hi KrazyPenguin, thank you for your assistance.

1. At the recovery mode terminal, I run xdiskusage.
2. I am told that xdiskusage is current installed. I am invited to install it.
3. I install xdiskusage using the recommended command of 'sudo apt-get install xdiskusage'.
4. I receive the following output:

> Reading package lists... Done
Building dependencay tree
Reading state information... Done

The following packages were automatically installed and are no longer required:
 libopenal1 menu lives-data libsvga1 mplayer-nogui mplayer libweed0 mplayer-skins omgtools icedax.
Use apt-get autoremove to remove them.

The following extra packages will be installed:
 libfltk1.1
The following NEW packages will be installed:
 libfltk1.1 xdiskusage
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.

Need to get 489kb of archives.
After this operation, 2,162kb of additional disk space will be used.
Do you want to continue? 9y/n) Y
Get 1: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main libfltk1.1 1.1.9-6ubuntu2 [461kb]
Get 2: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe xdiskusage 1.48-8 [27.8kb]
Fethced 489kb in 1s (341kb/s)
Selecting previous deselected package libfltk1.1.
(Reading database ... 148114 files and directories currently installed.)
Unpacking libfltk1.1 (from .../libfltk1.1_1.1.9-6ubuntu2_amd64.deb) ...
Selecting previously deselected package xdiskusage.
Unpacking xdiskusage (from .../xdiskusage_1.48-8_amd64.dev) ...
Processing triggers for man-db ...
/usr/bing/mndb: can't write to /var/cache/man1760: No space left on device
Processing triggers for menu ...
Setting up libfltk1.1 (1.1.9-6ubuntu2) ...

Setting up xdiskusage (1.48-8) ...

Processing triggers for libc-bin ...
Idconfig deferred processing now taking place
Processing triggers for menu
pipps@pipps-desktop:~$ xdiskusage
Can't open display:
pipps@pipps-desktop:~$


What could all this mean: :confused:

---

### Post by Pipps on 2010-01-07
**Update:**
I have been successful in rebooting, thanks to the help so kindly provided on this thread, and to a little fearless tinkering around with it.

I will describe my journey as follows:

1. From the recovery mode command prompt, as detailed in my post directly above, attempting to run 'xdiskusage' returned a statement advising me to install it.
2. I tried to install it. It complained of no free space.
3. I ran 'sudo apt-get autoremove'.
4. I rebooted and re-entered the recovery mode command prompt. I attempted to reinstall xdiskusage again. Now confronted with the error message:
> Can't open display
5. I run 'startx' - no boot. Simply the same long error message as I detailed in Post#10 above.
6. I run 'sudo startx', and I then find Ubuntu boots successfully in recovery mode.
7. In recovery mode desktop, I open Firefox, and am immediately confronted with a GUI error message:
> **The volume 'Filesystem root' has only 0 bytes disk space remaining.**
You can free up disk space by removing unused programs or files, or by moving files to another disk or partition.
[Examine/Ignore]?
8. I then run 'sudo xdiskusage' from the terminal. It shows me that my 4.75GB Ubuntu partition is 91% full.
9. I shutdown, and attempt to reboot in full desktop mode, rather than recovery mode.
10. Reboot is successful! :D

**Questions**
1. What could have possibly been causing this problem all along?
2. Should I ever run an update again?!
3. How can I take steps to prevent this problem from ever arising again?

I am incredibly grateful for everyone's assistance in helping get back into my Ubuntu installation. 

Thank you! :D

---

### Post by Vanishing on 2010-01-07
> **Pipps said:**
> **Update:**
I have been successful in rebooting, thanks to the help so kindly provided on this thread, and to a little fearless tinkering around with it.

I will describe my journey as follows:

1. From the recovery mode command prompt, as detailed in my post directly above, attempting to run 'xdiskusage' returned a statement advising me to install it.
2. I tried to install it. It complained of no free space.
3. I ran 'sudo apt-get autoremove'.
4. I rebooted and re-entered the recovery mode command prompt. I attempted to reinstall xdiskusage again. Now confronted with the error message:

5. I run 'startx' - no boot. Simply the same long error message as I detailed in Post#10 above.
6. I run 'sudo startx', and I then find Ubuntu boots successfully in recovery mode.
7. In recovery mode desktop, I open Firefox, and am immediately confronted with a GUI error message:

8. I then run 'sudo xdiskusage' from the terminal. It shows me that my 4.75GB Ubuntu partition is 91% full.
9. I shutdown, and attempt to reboot in full desktop mode, rather than recovery mode.
10. Reboot is successful! :D

**Questions**
1. What could have possibly been causing this problem all along?
2. Should I ever run an update again?!
3. How can I take steps to prevent this problem from ever arising again?

I am incredibly grateful for everyone's assistance in helping get back into my Ubuntu installation. 

Thank you! :D

I think you should expand the drive a little bit..I remember theres 5% of space kept "secret" when installing the system, theres an option when you are at the step of "setting up the partition".

Happy new year!

---

### Post by Pipps on 2010-01-07
What would be a recommended safe minimum size for a Lucid partition?

---

### Post by KrazyPenguin on 2010-01-07
> **Pipps said:**
> What would be a recommended safe minimum size for a Lucid partition?

Depends how you setup your system:
root / 5GB
Swap - I don't use swap but 1GB is safe
/home - depends what you plan on storing here if anything 5GB-unlimited

How did you set up your partitions, is is 5GB for root home and swap??

---

### Post by KrazyPenguin on 2010-01-07
when you use xdiskusage type this in the bottom as well:

/home/username (whatever your username is)
and see if there are problems there.

You might have very little space left.

---

### Post by Pipps on 2010-01-07
> **KrazyPenguin said:**
> Depends how you setup your system:
root / 5GB
Swap - I don't use swap but 1GB is safe
/home - depends what you plan on storing here if anything 5GB-unlimited

How did you set up your partitions, is is 5GB for root home and swap??

Funnily enough, I currently have 5GB for root and home, and 1GB for swap!

---

### Post by ranch hand on 2010-01-07
I always like at least 10Gb for my / partition.  I admit that this is a left over from experience with MSdos and what ever they called the proto windows.  Things got slow if you had more than 50% used.

Drives are a lot faster now but I can still see the fall off in speed when over 50%.  I have, on my 9.04 that I use more than planned when it was installed, 40Gb for my /home.  It is 54% used and files are slower (not much) to open.  / is at 41% and I see no lack of speed on functions that just depend on that partition.

On my test platform  I have my / partitions at 10Gb and /home at 10 to 15Gb depending on how I think I am going to use it and how I feel when I install and how much space I have left.

I am running, on the other box, 8.10 on a 10Gb HDD with 2 partitions and .5Gb swap.  It runs alright.

I think cramping the pre-release OS' is asking for problems.  If you have the space, let the buggers breath a little.  Give them room to spradle out a bit.

---

### Post by VMC on 2010-01-07
I think its been hinted at, but you need to make sure no root Trash is left over. Enter the following and see how much, if any is there:

```
sudo ls -alRS /root/.local/share/Trash
```

---

### Post by ronacc on 2010-01-07
also it might be helpful to boot another install or the live cd and run fsck on your lucid partitions .

---

### Post by ranch hand on 2010-01-07
Well, this is an interesting thread.  I never knew there was a root trash.  How in tarnation does it normally get emptied?

I take it that this is supposed to be automatic at some point.

---

### Post by ronacc on 2010-01-07
one reason that I NEVER use the trash can , one of the very first things I do is to set nautilus to provide a "real" delete .

---

### Post by philinux on 2010-01-07
> **ranch hand said:**
> Well, this is an interesting thread.  I never knew there was a root trash.  How in tarnation does it normally get emptied?

I take it that this is supposed to be automatic at some point.

gksu nautilus or sudo rm to empty it. Stuff will get in root trash when using gksu nautilus to delete anything. It's not automated at all by the way. Maybe Computer Janitor can do it, never tried though.

Bleachbit can do it.

---

### Post by Pipps on 2010-01-07
> **VMC said:**
> I think its been hinted at, but you need to make sure no root Trash is left over. Enter the following and see how much, if any is there:

```
sudo ls -alRS /root/.local/share/Trash
```

Thank you for this advice. But I am having difficulty accessing that directory:

When I try to search for it in the terminal, I am given the following contents of its parent directory ('/root/.local/share/'):

> root@pipps-desktop:~/.local/share# **ls**
akonadi  gnome-do  gvfs-metadata  mime

What am I doing wrong? :confused:

---

### Post by ranch hand on 2010-01-07
Well I never.  I better check my 9.04 that I use at  night, I bet that bugger is full of old stuff.

---

### Post by ubername on 2010-01-07
I think this may have also been mentioned, but check /var/log for any large files. If something is wrong with your install (or the way the logs are being written) this can fill up quickly.

---

### Post by VMC on 2010-01-07
> **Pipps said:**
> Thank you for this advice. But I am having difficulty accessing that directory:

When I try to search for it in the terminal, I am given the following contents of its parent directory ('/root/.local/share/'):



What am I doing wrong? :confused:

It's not in your local directory at all. It's in roots directory.
Just open a terminal, then highlite this:

```
sudo ls -alRS /root/.local/share/Trash
```

Then paste it inside the terminal.

---

### Post by zika on 2010-01-07
> **VMC said:**
> It's not in your local directory at all. It's in roots directory.
Just open a terminal, then highlite this:

```
sudo ls -alRS /root/.local/share/Trash
```

Then paste it inside the terminal.My /root/ doesn't have .local/share/Trash either.

---

### Post by VMC on 2010-01-07
> **zika said:**
> My /root/ doesn't have .local either.

It does if you deleted files from root:

```
sudo ls -alRS /root/.local/share/Trash
/root/.local/share/Trash:
total 16
drwx------ 4 root root 4096 Dec 29 18:12 .
drwx------ 3 root root 4096 Dec 29 18:12 ..
drwx------ 2 root root 4096 Dec 29 18:12 files
drwx------ 2 root root 4096 Dec 29 18:12 info

/root/.local/share/Trash/files:
total 8
drwx------ 2 root root 4096 Dec 29 18:12 .
drwx------ 4 root root 4096 Dec 29 18:12 ..

/root/.local/share/Trash/info:
total 8
drwx------ 2 root root 4096 Dec 29 18:12 .
drwx------ 4 root root 4096 Dec 29 18:12 ..

```

edit: It looks like Pipps was in his root dir, so he also hasn't deleted files from root.

---

### Post by zika on 2010-01-07
> **VMC said:**
> It does if you deleted files from root:

```
sudo ls -alRS /root/.local/share/Trash
/root/.local/share/Trash:
total 16
drwx------ 4 root root 4096 Dec 29 18:12 .
drwx------ 3 root root 4096 Dec 29 18:12 ..
drwx------ 2 root root 4096 Dec 29 18:12 files
drwx------ 2 root root 4096 Dec 29 18:12 info

/root/.local/share/Trash/files:
total 8
drwx------ 2 root root 4096 Dec 29 18:12 .
drwx------ 4 root root 4096 Dec 29 18:12 ..

/root/.local/share/Trash/info:
total 8
drwx------ 2 root root 4096 Dec 29 18:12 .
drwx------ 4 root root 4096 Dec 29 18:12 ..

```

edit: It looks like Pipps was in his root dir, so he also hasn't deleted files from root.Maybe. I do not remember that I logged in root in this incarnation of my installation. But, my memory is not as good as it used to be.

---

### Post by ranch hand on 2010-01-07
If you are just looking in nautilus you will have to select to see hidden files or you will not see it.

You have a /root/.local directory.  /root/.local/share has more than /trash in it.

---

### Post by zika on 2010-01-07
> **ranch hand said:**
> If you are just looking in nautilus you will have to select to see hidden files or you will not see it.

You have a /root/.local directory.  /root/.local/share has more than /trash in it.No worry, I see all of those files in CLI. Just no /root/.local/share/Trash. I search there when I want to see synaptic log's for example. /root/ is interesting place... I do not like to visit /root/ with GUI, I prefer CLI for that job. But, that's just me...

---

### Post by ranch hand on 2010-01-07
OK, must have been a typo when you said you didn't have a .local.  I can understand that.  I am all thumbs on the keyboard and my mind gets way ahead of what I am typing.

---

### Post by Pipps on 2010-01-07
Would the following command do the trick?

> sudo rm -rf /root/.local/share/Trash/*/** &> /dev/null

Would it delete everything in both root trash folders?

---

### Post by BwackNinja on 2010-01-07
Try checking /home/<username>/.local/share/gvfs-metadata

I've had some problems with that off and on sometimes.

---

### Post by Pipps on 2010-01-07
The whole '/root/.local/share' now seems to be under control - it is now a total of 345.3KB. 

Thank you one and all, for all the help!

---

### Post by zika on 2010-01-08
> **ranch hand said:**
> OK, must have been a typo when you said you didn't have a .local.  I can understand that.  I am all thumbs on the keyboard and my mind gets way ahead of what I am typing.Yes, I see what You mean, that was my typo... Corrected...

---

### Post by Pipps on 2010-01-08
The only issue which now remains apparent is a slower system boot time.

From the moment the grub menu disappears, to the point of the Ubuntu desktop appearing, now takes at least twice as long as it did before. Over twenty seconds.

Is it likely that this earlier issue affected the permanent processes which allow Ubuntu to boot?

Is there any way that this slower booting could be returned to its previously speedier state?

---

### Post by ronacc on 2010-01-08
if you use bootchart you can check your before and after charts and see what has changed . But it has been my experience that boot times steadily get longer the further we get into the dev cycle .

---

### Post by phillw on 2010-01-08
> **Pipps said:**
> The only issue which now remains apparent is a slower system boot time.

From the moment the grub menu disappears, to the point of the Ubuntu desktop appearing, now takes at least twice as long as it did before. Over twenty seconds.

Is it likely that this earlier issue affected the permanent processes which allow Ubuntu to boot?

Is there any way that this slower booting could be returned to its previously speedier state?

Hi Pipps, I'm sorta back lurking .... Guess who nearly borked his system ... Pressed the wrong button !! - fortunately as there was 6 days of updates to do, it asked me if i *really* wanted to do it !!!

All updates installed (no partitial ones) there are a couple of application ones e.g. evolution, but I'll check synaptic package manager for those & update if it says there is a newer version (Still not heard if that is the *safe* way to do it - but it worked last time ;)  )

I can see everyone is looking after you - I did say that you needn't worry about being new to it all :D

I'm just catching up on some of the threads.

Apart from my minor heart-attack earlier - piglet resolutely refuses to be broken !!!

As for boot times, there is a thread comparing them - I'm just real grateful that it boots. I do recall, i think it was one of the QA guys, saying that me complaining at my having to reboot after several days of up-time was not quite in their top 10 list of priorities at the moment - lol

Regards,

Phill.

---

### Post by nanog on 2010-01-09
Pipps, if you want to fix your apparently full *boot* hard drive you need to mount is and chroot in from the live disk (see instruction here: [http://ubuntuforums.org/showthread.php?t=1374438](http://ubuntuforums.org/showthread.php?t=1374438)).

some useful commands:

[php]sudo fdisk -l[/php]
 provides a list of all volumes

[php]df -h[/php] 
 lists all mounted volumes in an understandable format

[php]sudo du -sh /*[/php]
lists directory file space. its slow in ubuntu because of dumb security nazi permissions issues but you can also use 
[php]du -sh /home; du -sh /root; du -sh /var; du -sh /usr[/php] etc...

full drives almost always become borked so an fsck (one of the worst expletives in *nix) is warranted:

[php]sudo touch /forcefsck; sudo reboot[/php]

it will take a while to run (fsck on \ext[234]\ is extremely annoying and the main reason i have switched to nfs-mounted zfs arrays for everything but boot). 

.
> sudo apt-get clean
this is, imo, bad advice when testing. the backed up debs in /var/cache/apt/archives saved my a** when the libc6 debacle happened. i now keep a *versioned* backup when i test.

---

