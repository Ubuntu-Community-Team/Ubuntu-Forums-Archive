---
title: "I messed with Plymouth and now I'm paying for it..."
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by lifelike27 on 2010-11-09
First of all, I'm a ubuntu noob. I'm familiar with it, but that's all.

I tried changing my plymouth splash screen but it just ended up becoming pixelated so I reverted back to the original one. Now the original splash screen became pixelated as well.

Using Start-up Manager, the options I changed were:
- Checked 'Show boot splash'
- Changed the display resolution to '1600x1200'

After restarting I can't start up Ubuntu anymore. =\

I really need to get it back and running WITHOUT formatting of any sort because I can't re-install Ubuntu.

I'm a student living on-campus and there's only wireless. When installing Ubuntu I have to download my Broadcom drivers with an ethernet cable and all. Not possible here...

I'm running 10.10 on it.

Help is EXTREMELY appreciated!

---

### Post by garvinrick4 on 2010-11-09
> **lifelike27 said:**
> First of all, I'm a ubuntu noob. I'm familiar with it, but that's all.

I tried changing my plymouth splash screen but it just ended up becoming pixelated so I reverted back to the original one. Now the original splash screen became pixelated as well.

Using Start-up Manager, the options I changed were:
- Checked 'Show boot splash'
- Changed the display resolution to '1600x1200'

After restarting I can't start up Ubuntu anymore. =\

I really need to get it back and running WITHOUT formatting of any sort because I can't re-install Ubuntu.

I'm a student living on-campus and there's only wireless. When installing Ubuntu I have to download my Broadcom drivers with an ethernet cable and all. Not possible here...

I'm running 10.10 on it.

Help is EXTREMELY appreciated! It gets to boot menu and you choose Ubuntu and what does it do after that.

---

### Post by lifelike27 on 2010-11-09
> **garvinrick4 said:**
> It gets to boot menu and you choose Ubuntu and what does it do after that.

It says that my graphics card or screen couldn't be detected and that I would need to configure it myself. However, it freezes at that and I'm unable to click the Ok button.

---

### Post by garvinrick4 on 2010-11-09
You had a working system before you changed your resolution to 1600x1200?
The plymouth theme you tried to install was one of the Ubuntu themes?

---

### Post by lifelike27 on 2010-11-09
No it wasn't. 

I'm pretty sure it wasn't the theme that messed up my system. Since it was working fine before, it just had a bad looking splash screen. It only stopped working after I tried changing it.

Previously, I changed settings by editing the default.plymouth file. It wouldn't fix the pixelating problem, but I never had any problems like this. Only after I used the Start-Up Manager instead of editing, this happened...

---

### Post by garvinrick4 on 2010-11-09
Put in your install Cd and boot off of it and choose try ubuntu.
When it boots go to places and mount your linux partition open it
and go to files system. to path /etc/default/grub
Look here and see what it says: Post it.

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768

Post your output of :
```
sudo fdisk -l 
```
lower case L

---

### Post by garvinrick4 on 2010-11-09
If that has to be changed it has to also have to update-grub to make it save:
Which means we have to use the Live CD to chroot (get into root) into your Ubuntu partition so leave it in and work ubuntu forums off of it.

---

### Post by lifelike27 on 2010-11-09
I checked it and it turns out, the last time I edited that file, I put the resolution to 1366x768 (i.e. my resolution).

I changed it back and still isn't working. I think I need some way of recompiling plymouth.

---

### Post by garvinrick4 on 2010-11-09
You have to update-grub after you edit or it does no good. Everytime you change you have to update grub

---

### Post by garvinrick4 on 2010-11-09
> **lifelike27 said:**
> I checked it and it turns out, the last time I edited that file, I put the resolution to 1366x768 (i.e. my resolution).

I changed it back and still isn't working. I think I need some way of recompiling plymouth.plymouth you can always remove then reinstall new plymouth package.

---

### Post by lifelike27 on 2010-11-09
So if I run 'update-grub' in the live CD of ubuntu, it would work for my installed version of Ubuntu?

---

### Post by garvinrick4 on 2010-11-09
> **lifelike27 said:**
> So if I run 'update-grub' in the live CD of ubuntu, it would work for my installed version of Ubuntu? You would have to give me the output of 
the (sudo fdisk -l) (earlier post) so we can chroot(get into root) into your install and update grub and remove plymouth and reinstall a new package from repositories. That is the only way I have ever had any success at updating grub in a particular install and making new config file in live cd.

---

### Post by lifelike27 on 2010-11-10
Alright I need you to explain it to me in a bit more detail how I'd get around to fixing this. I really don't know much about Ubuntu.

Sorry I didn't see the part about the fdisk command earlier:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4600c452

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        2300    18432000    7  HPFS/NTFS
/dev/sda3            2300       15354   104856576   83  Linux
/dev/sda4           15354       60802   365054976    7  HPFS/NTFS

---

### Post by garvinrick4 on 2010-11-10
Well if you say it was when you used startup manager and changed resolution to 1600x1200 and then attempted edit a plymouth file. So we fix those 2 things.
 To get into root in live cd because it will not boot and update the grub takes some commands in terminal, you have make directories and mount a few things and then
get into root and then we can repair the objects that are broken.
I would put the resolution at 800x600 to start with because that we will say works most
all the time. Can change after you can boot into your system.

#In live cd go to Places and to your linux install and mount your Linux partition as before.
Then hit Alt/F2 and box will open and type in gksudo nautilus and hit enter.
That will open file system in root so you can change and save.
Click on your Linux partition on left side of Window that opens and open file system and navigate
/etc/default/grub
change to 800x600 and hit save in upper left. As below is mine at 1024x768:

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768

Have to be in root to save file is why we do the "gksudo nautilus" part:
After saving you close everything and open a terminal and make sure your internet connection in upper right is connected and in next post will give you the commands to 
chroot into system and update your grub and remove and reinstall plymouth.
Will be maybe 10 commands just copy and paste into terminal one at a time.

---

### Post by garvinrick4 on 2010-11-10
```
Your Linux install is sda3: These commands one at a time:
                    [CODE]sudo mkdir /media/root
``````
sudo mkdir /media/root/proc
``````
sudo mkdir /media/root/dev
``````
sudo mkdir /media/root/etc
``````
sudo mount /dev/sda3 /media/root
```                   ```
sudo mount -o bind /proc /media/root/proc
``````
sudo mount -o bind /dev /media/root/dev
``````
sudo mount -o bind /dev/pts /media/root/dev/pts
``````
sudo cp /etc/resolv.conf /media/root/etc/resolv.conf
``````
sudo chroot /media/root
``````
apt-get remove plymouth
``````
apt-get install plymouth
``````
apt-get -f install
``````
dpkg --configure -a
``````
update-grub
``````
exit
``````
sudo umount /media/root/dev/pts
``````
sudo umount /media/root/dev
``````
sudo umount /media/root/proc
``````
sudo umount /media/root/etc
``````
sudo umount /media/root
```Boot back into Hard drive Ubuntu:
```
sudo update-grub
```[/CODE]

---

### Post by lifelike27 on 2010-11-10
At the command: sudo chroot /media/root

I get the error: chroot: failed to run command `/bin/bash': Exec format error

---

### Post by lifelike27 on 2010-11-10
Typing: chroot --help 

Gives: Usage: chroot [OPTION] NEWROOT [COMMAND [ARG]...]
  or:  chroot OPTION
Run COMMAND with root directory set to NEWROOT.

  --userspec=USER:GROUP  specify user and group (ID or name) to use
  --groups=G_LIST        specify supplementary groups as g1,g2,..,gN
      --help     display this help and exit
      --version  output version information and exit

If no command is given, run ``${SHELL} -i'' (default: /bin/sh).

Report chroot bugs to [email]bug-coreutils@gnu.org[/email]
GNU coreutils home page: <http://www.gnu.org/software/coreutils/>
General help using GNU software: <http://www.gnu.org/gethelp/>
For complete documentation, run: info coreutils 'chroot invocation'


Don't know if that's any help...

---

### Post by garvinrick4 on 2010-11-10
I will explain the code to you later: It is not difficult to understand, you just have to mount certain things then run a few commands then unmount them. (umount is not a typo in code)

---

### Post by lifelike27 on 2010-11-10
I don't have a problem understanding it, it's just the error I'm getting from running that command.

---

### Post by garvinrick4 on 2010-11-10
Is the partition mounted on your desktop: Can you see the partition on desktop(should be)
```
sudo mount /dev/sda3 /media/root
```
was the command to mount.
```
sudo chroot /media/root
```
is the chroot command:

---

### Post by lifelike27 on 2010-11-10
Yes, it is mounted, I can see the icon there and running the first command said that it is already mounted. However, I still cannot run the chroot command (same error).

---

### Post by garvinrick4 on 2010-11-10
> **lifelike27 said:**
> Yes, it is mounted, I can see the icon there and running the first command said that it is already mounted. However, I still cannot run the chroot command (same error). Is the disk the same 32bit or 64 bit that you are running
on your machine. The only way I can reproduce is using 32 bit on 64 bit or vice versa. Only 1 32 bit install so?
other wise can chroot into 5 different installs.

---

### Post by garvinrick4 on 2010-11-10
```
sudo chroot /media/root /bin/sh
```puts you into root also. How ya doin.

---

### Post by lifelike27 on 2010-11-10
Nope, that last command didn't work either. Same error.

I believe they are both 64bit. The Live CD... should be.

---

### Post by garvinrick4 on 2010-11-10
Going to see if I can get a mod to see if cure for the chroot command, seems to be in googling alot. First time happened to me. Got to be a command for it by now. See ya few minutes.

---

### Post by lifelike27 on 2010-11-10
Alrighty, I'm just going to hang around with my buddy Google.

---

### Post by garvinrick4 on 2010-11-10
> **lifelike27 said:**
> Alrighty, I'm just going to hang around with my buddy Google. Asked a Mod by the name of artificial inteligence to see if he had a cure
for that error message.

---

### Post by garvinrick4 on 2010-11-10
Ran the whole code string on 2 different installs and worked like it is suppose to.
It is tried and true code not anything that I made up. I only use stuff that has been
known to work and I have tried on my own machines. I feel bad it is taking so long
to find out what your error code in chroot means. I am sticking around also.

---

### Post by lifelike27 on 2010-11-10
Thanks a lot. I really appreciate it! =)

But if you have to, you can always find out tomorrow. I have a backup system that'll last me a few days.

---

### Post by garvinrick4 on 2010-11-10
**Troubleshooting **

 **[[edit]("http://en.gentoo-wiki.com/w/index.php?title=Chroot_from_a_livecd&action=edit&section=10")]  Exec format error **

 If the chroot command returns with the error "[FONT=monospace]chroot: cannot run command `/bin/bash': Exec format error[/FONT]", this usually indicates that the livecd environment is not compatible with that of the installed system. 
For example, the error is most frequently seen when trying to chroot to a 64-bit system (eg. **amd64**) from a 32-bit livecd (eg. **x86**). 
The solution is to use a livecd which is using the same architecture as the installed system.

This is what I get but can you do me a favor if you are still around: Post this for me please. This is going to bug me till fix is in.
```
sudo parted -l
```lower case L

```
uname -a
```
Tell you 64 or 32 bit.

---

### Post by lifelike27 on 2010-11-10
There ya go:

Model: ATA ST9500420AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary  fat16        diag
 2      41.1MB  18.9GB  18.9GB  primary  ntfs         boot
 3      18.9GB  126GB   107GB   primary  ext4
 4      126GB   500GB   374GB   primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label

---

### Post by lifelike27 on 2010-11-10
And this:

Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux

---

### Post by garvinrick4 on 2010-11-10
> **lifelike27 said:**
> And this:

Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux 32 bit Live Cd and you are running 64 bit on your machine.
You need a 64 bit live Cd. That should clear up the inability to chroot into your install.

---

### Post by lifelike27 on 2010-11-10
Damn, why would Ubuntu send me a 32-bit version...

Thanks a lot. I'm going to try this in a while when I get back. I hope it works!

---

### Post by garvinrick4 on 2010-11-10
> **lifelike27 said:**
> Damn, why would Ubuntu send me a 32-bit version...

Thanks a lot. I'm going to try this in a while when I get back. I hope it works!where is the 64 bit cd you installed in your machine?

---

### Post by ezsit on 2010-11-10
> Damn, why would Ubuntu send me a 32-bit version...

Because that is the only version they print to CD. If you want 64bit version you need to download it.

---

### Post by lifelike27 on 2010-11-10
> **garvinrick4 said:**
> where is the 64 bit cd you installed in your machine?

I have the 64-bit somewhere. Will have to find it soon. I live off Ubuntu, but it's sad that I know so little about how it works. =\

When I have free time I shall explore into the depths of the Linux world! 

Again, will test with the 64-bit soon. Today or tomorrow.

---

### Post by lifelike27 on 2010-11-11
So I tried all those commands and it didn't work. I had another problem at un-mounting all the files. It said the drive was in use, so I just restarted. 

It also removed my Win7 boot menu and that scared me because that was my backup option. But I got the Ubuntu safe mode from the installed Ubuntu to recompile grub. I forgot to mention that it works. At least I think it does.

Let me restart and check out all the options it has.

---

### Post by lifelike27 on 2010-11-11
I get a menu showing Resume, Clean, dpkg, failsafex, grub, netroot, root. I feel like this was information that would have saved us a lot of time...

---

### Post by garvinrick4 on 2010-11-11
I am glad you have a working system one way or the other and
enjoy your Ubuntu.

---

### Post by lifelike27 on 2010-11-11
I don't think you understood what I was trying to say. My Ubuntu is still not working. It erased my grub menu but I got that fixed. 

No idea what to do to fix Ubuntu...

---

### Post by garvinrick4 on 2010-11-11
> **lifelike27 said:**
> I don't think you understood what I was trying to say. My Ubuntu is still not working. It erased my grub menu but I got that fixed. 

No idea what to do to fix Ubuntu... You can boot into Windows but not Ubuntu? It starts to boot Ubuntu and then gives graphics errors?

---

### Post by garvinrick4 on 2010-11-11
So we changed  what you did in start-up manager back to when it was a working system and we updated grub to apply it and we removed and reinstalled plymouth
because you attempted to install a theme that was not in Synaptics. You replaced grub2 into the mbr. The first 2 were the last 2 things you did before it stopped booting.
  Well we better look at grub. This will give you the whole grub config in a file on your desktop to post here. Lots of users can read.
Download this to desktop and then run the code below takes about 30 seconds. Will tell everything about grub2 in your system. 
Must be Downloaded or on Desktop and easier to read when you post (is long) put code tags   before first and after last words or highlight and hit # sign in upper right.

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
 ```
sudo bash ~/Desktop/boot_info_script*.sh
```And you have started in recovery-mode in low graphics mode?

And this below will give all your cards including graphics to other users to help get
you running. Dells have proprietary drivers and lots of Dell users out there.
                     ```
sudo lspci -v | less
```Post these boot script and cards. There are a lot of excellent users on these forums and these will give them the info needed.

---

### Post by garvinrick4 on 2010-11-11
> **lifelike27 said:**
> I don't think you understood what I was trying to say. My Ubuntu is still not working. It erased my grub menu but I got that fixed. 

No idea what to do to fix Ubuntu... Am very sorry if the chroot code did anything to grub: It is code that has been around for years and just to mount partition in Live CD, install internet connection, install package from repository or update and upgrade a system and update the grub, no code to remove anything except replace plymouth. Have run 10 times since your post and have not been able to duplicate any problems.

---

### Post by lifelike27 on 2010-11-11
Alright then, I think it's best that I just reinstall Ubuntu and not try to change the splash screen again. I need it up and running soon and the fix seems to be taking longer than I have time. =\

Thanks a bunch, I've heard bad things about the Ubuntu community before, but I guess that's all wrong. =)

To the drawing board!

---

### Post by lifelike27 on 2011-01-18
I just thought I'd mention that it worked out successfully. Thankfully I was able to use GParted from Ubuntu itself instead of having to use it from a bootable disk. 

Thanks again!

---

