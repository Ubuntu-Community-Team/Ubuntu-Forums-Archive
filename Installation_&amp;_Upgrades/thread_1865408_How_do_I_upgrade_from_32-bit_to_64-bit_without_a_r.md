---
title: "How do I upgrade from 32-bit to 64-bit without a rebuild?"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2011-10-20
I have just noticed that one of my machines, which is a 64-bit dual core is actually running 32-bit Ubuntu 10.04. :o Which is odd, because I was sure I used the same CD to install 64-bit as I had on other machines, but anyway it is not what it should be.:confused:

How do I upgrade it without having to do a fresh install and loosing all my settings?  Anyone able to help me?

---

### Post by Grenage on 2011-10-20
As far as I am aware, you can't.  You could take the /home folder across if you wanted to preserve many of your settings?

---

### Post by Jonners59 on 2011-10-20
I am very optimistic.  I am sure someone has an idea.

---

### Post by Frogs Hair on 2011-10-20
Grenage is correct a re-installation would be required . Unless you have memory that you can't be used due to having 32 bit installed it may not be worth the trouble .

---

### Post by haqking on 2011-10-20
> **Jonners59 said:**
> I am very optimistic.  I am sure someone has an idea.

dont be, you need to do a fresh install

---

### Post by Jonners59 on 2012-01-02
Can a 64 bit and a 32-bit install share the same HOME directory?  And if so what other Directories can be shared?  I.e.
I have three partitions on my Hard drive.  One for Windows, one for my main OS (Ubuntu and the third for a back up OS (Ubuntu....)  In this latter case as I have my prime install all set up and working as I want it, I want to take my time and install a new instance of 64-bit in the third partition.  It would make sense to use the same HOME folder and it there are certain files/configs that would be common, such as fstab which would save a lot of time and trouble if I could re-use/share, which the begs the question, could etc, for instance be shared or copied over, thus saving all the work of setting that up....

I am surprised no-one has come up with a 32-bit to 64-bit upgrade app...  I know I am not a developer and know squat about programing but I would have thought with the move to 64-bit that something working in DOS could not lookup installed components in an OS/Apps and replace them with 64-bit alternatives.  I have seen back/hard drive duplicator apps that do this.  Anyway - maybe I am just fanciful. :o

Seems it can be done, but these are a bit technical for me.  I need a step by step for Noddies version.!
[http://anthonyrhook.com/blog/2010/01/05/upgrade-ubuntu-karmic-koala-from-32bit-to-64bit-with-encrypted-home/](http://anthonyrhook.com/blog/2010/01/05/upgrade-ubuntu-karmic-koala-from-32bit-to-64bit-with-encrypted-home/)
[http://ubuntuforums.org/showthread.php?t=1749180](http://ubuntuforums.org/showthread.php?t=1749180)

Seems it's about using HOME and etc Directories....  Something about one of the other directories to protect the installed apps...  Once yo have those bvack up and running, any wanted in 64-bit can be uninstalled and re-installed from what I can tell.  The configs and settings would be retained.

---

### Post by oldfred on 2012-01-03
The kernel & all the apps are different, so in effect the whole system is different.

But you can reuse /home but probably should not share a /home as settings in one versions may be different from the other and eventually conflict. Reuse of /home is for upgrade as software is designed for upgrading but not usually downgrading.

I converted to 64bit with 9.10 and that worked so well, I now only do clean installs but use a new partition for the new install. Since I at same time got a new 640GB drive which was huge for me, I keep installing to a new partition and have all my installs and a few others for testing. I use a 25GB / (root) partition with /home still in root. But my /home only has the hidden folders & settings and any folder in /home that has data gets moved to a shared data partition. All my installs use the same data partitions.

My backup is so I can do a clean reinstall and restore /home, some settings from /etc (but not copy any of /etc back), and a list of installed applications to install.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

Other applications if data not separate
apache, any sqldb, tomcat 
Document system backup or for multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)
Screen for multiple SSHs
[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

Files to include or exclude from full system backup.
[http://ubuntuforums.org/showthread.php?t=1903085](http://ubuntuforums.org/showthread.php?t=1903085)

---

### Post by Jonners59 on 2012-01-03
Hello Oldfred
It has been a long time.  Glad you took a look and are keeping an eye on me.
 Yes, the difference between the 32 and 64 in etc was a slight worry, but from what you have high-lighted I think I am quite safe.  I am going to just copy over the few etc config files, fstab (modified), smb and repositories...

Home I was and in fact am going to change location.  Did a light boob and missed a step and so trying to get at it from another angle as I type...  I was not confident just pointing the install at HOME.  I worried it might delete the directory, but from what you have stated it would seem it keeps the directory and just updates and adds to what is in there provided it is not formatted.  That is good to know.  Shame I had not realised when I installed the OS.

I have been doing a fair amount of Googling and it seems that this is quite doable.  I read on a forum that in all other Linux, bar Ubuntu, it can be done by just changing the kernel...

Anyway, please keep an eye on me.  You have bailed me out so many times before.  If I go wrong I may need your help.

PS:  Happy New Year

---

### Post by oldfred on 2012-01-03
Yes it is easy to reuse /home on a new install if it is a separate partition. But it is very important to make sure not to format it or choose a different type of partition.

If it is a separate partition, you should be able to just add a new entry to fstab to mount your old /home. The new on it creates inside / (root) will just have the defaults. Then you can compare (hidden) settings to see if you want any new ones or keep the old.

If already a separate /home, you just need the last steps to add to fstab:
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by ottosykora on 2012-01-04
I have 'upgraded' from 32 to 64 on one particular machine for som especific reasons.

I had separate /home, so this did help somehow.
I did not copy or rescue any other things from the 32 root except some very special settings to my gpg and java install.

The install went ok, I just specified in the installer GUI of ubuntu that the /home ahould be again a /home and not be partitioned, the / should be what it is and can be partitioned and probably also useful is to choose same user name as then the /home partition 'imports' seamless .

Some people tried to do new install, have chosen new user name and were surprised that they can not access their home data...

---

### Post by ottosykora on 2012-01-04
>I read on a forum that in all other Linux, bar Ubuntu, it can be done by just changing the kernel...<

no way, the apps also have to be compiled for the 64.
On my 32 machines, I had a 3rd party lib just to operate the legacy gpg keys with IDEA algo. No way it would work on x64, it had to be recompiled for that. Also any thigs like drivers for my scanner which are also 3rd party items had to be recompiled.
Canonical presents most apps in the 64 version in the repository, so most will then work fine.

There might come up some problems with small things like flash, as this is in some kind of beta state from the adobe, but when you install the flashaid extension, you can pick the install from adobe directly.

I still met some apps which have only 32 version, but now I think is all available what people needs.

---

### Post by Jonners59 on 2012-01-04
Hi Guys - Done the swap, and all almost works well.  I am missing my Thunderbird and Evolution settings, and my browsers are on default too....  So need to find their stuff, probably in etc, I guess.  I found that installing the 64-bit it would not allow me to call the PC what it was origionally called (I refer to ottosykora comment).  This may be the issue I have.  I am going to try and rename my PC first.

ottosykora
No, I agree re some apps need to change, and to make full use of 64 many shall anyway, but once installed, any particular or those that don't play well can be un-installed and re-installed - I assume picking up the 64-bit version along the way but using the existing config as happens now under 32-bit when an app is un-installed and reinstalled.

Did also read that for some 32-bit apps to run on 64-bit they need ia23 -libs  Just about to check this out whilst completing the install...

I guess the point is that an upgrade from 32-bit to 64-bit can be done, and I guess a script could be written to do it automatically, likewise it could be part of Update Manager - as I also saw in the "futures" discussion.

---

### Post by ottosykora on 2012-01-04
>I am missing my Thunderbird and Evolution settings, and my browsers are on default too.... So need to find their stuff, probably in etc, I guess.<

negative, they all are in your /home. You have to have the **same** user on the new install , only this way you can have your settings and other data available.
So when I do such thing, I note down all and also export things like thunderbird folder still with the original user to some safe place.
Why it did not allow??? you to call it ?? During the install, you are asked for a user name and password etc, this is where your /home access and ownership is defined. The settings are then just taken and all programs work as usual. 
You can  now try to change the ownership of all the folders in the /home (chown command), but in fat that is what has to be done on install.
So you could try to change the owner of crucial thigs like thunderbird settings (will also contain mails etc.
You can run the install again, and this time enter the right user name amd password as used in the original installation. This will bring your user settings back.

as from 32 to 64, we are here not on windows, which has number of compatibility mechanisms.
Here, all parts of the install, also any parts doing the actual GUI etc have to be completely replaced. And this can not be done while running, so the whole thing has to be simply overwritten/replaced as it is. You can not just look to change some part here and there, replace some program and other not etc.
And yes, there are some libs to help run some not properly done software on x64, but a script? I doubt it. The script has to run on some operating system and this has to be present and running and it is then supposed to replace itself while running?

---

### Post by ottosykora on 2012-01-04
>This may be the issue I have. I am going to try and rename my PC first.
<

It is not about the name of the PC.

It is about the name of the user. Renaming the PC does not help, this can be done any time and is mainly for the the network. You have to have exactly same user for that.
Try instead to set up an additional user with same name as before and then log in with this user. This should bring your settings and data back.

---

### Post by Jonners59 on 2012-01-04
> **ottosykora said:**
> >This may be the issue I have. I am going to try and rename my PC first.
<

It is not about the name of the PC.

It is about the name of the user. Renaming the PC does not help, this can be done any time and is mainly for the the network. You have to have exactly same user for that.
Try instead to set up an additional user with same name as before and then log in with this user. This should bring your settings and data back.

Thanks ottosykora
Glad you are about as I have a few issues showing themselves.
I change the details in Ubuntu Tweak, so Host name and User name are correct and it shows up in terminal as correct too...  I'll try another reboot before I complain anymore and see what that does, if not I;ll try a new account as you suggest.

Some of the issues:
If I open my HOME directory it shows my user Directory as it should, but I note when in that the Folder address shows Home/Home/, and not Home/username

Switching desktops and I am stuck.  The desktop items disappear and panel and keyboard (more limited function than stops) stop working

Thunderbird still does not pick up the account settings

Docs on my desktop do not show an icon...  I.e. Libra docs do not show up as a Libra doc, just a named object.

Anyway I shall try a restart now...  You can tell me what a mess I have made in the mean time.

---

### Post by ottosykora on 2012-01-04
>If I open my HOME directory it shows my user Directory as it should, but I note when in that the Folder address shows Home/Home/, and not Home/username<

well this is kind of wrong as you assume. It created a new home directory inside the home apparently. 

To copy all setup-configs you may try to copy those items from the /home/home/user to /home/user with the following rather simle method:


copy those items (like thunderbird profile) by any user (incl root) to a drive formated in fat32.
By that any rights and property bits are lost as fat32 does not have any means to store such info.
Later copy them from the fat32 drive to the proper place under the current user which they should work with.
This way those files become property of current user and nothing more has to be done.


I did this on numberof installs, just copied all the needed things to an usb stick and transfered them this way.


BTW: how Ubuntu Tweak? This is not supposed to work on the latest versions or not correctly at least.

Thunderbird will be looking in the home directory for thunderbird and will try to get the data from there. If such dir is not there it might be created, but then you need to transfer all your data to it from where ever they are located now.

Note also all desktop configs are in your personal home folder and if this is not on the correct path, it will not be found.

---

### Post by Jonners59 on 2012-01-04
Thanks for the reply ottosykora
I had been bevering away in the background...
I have recreated the accounts in Thunderbird, though this is quite different to the 32-bit version and I can not seem to get my addressbooks installed.  I use gmail....

Still have the "Desktop" issue.  I can move to a new desktop but can't do anything when I am there, and the apps don't appear their either.

I am am not quite sure if it has confused the install or not.  I have taken a screen shot fyi.  The upper window is /home and the lower is /home/baronipc  The directory name changes once entered.  Maybe that is what you mean.  I am a bit worried about playing anymore, just trying to fix what I can.  I should have installed using the same HOME.  Once this is dobne and I am reasonable happy with it and it is usable I shall rebuild the other image (my fallback) and make it my prime using the current HOME Directory.

The above two items are my big concern.
Adding addressbooks to Thunderbird and the Desktops.  Get those done I shall feel "vindicated".

Sorry, you asked about Ubuntu Tweaks...  Yes both 5 and 6 work, though 5 is better than 6.  I only have 1 issue with it and that is in my 32-bit OS and that is it says there are 3,600 items in cache that can be deleted, but it just hangs - that is using v6 in 32-bit.  In the 64-bit I have installed v5.  It is better.

---

### Post by oldfred on 2012-01-04
Post your fstab just to see what is mounted where.

All your Thunderbird & Firefox settings are in your /home/$USER/.mozilla or .thunderbird.
Where $USER is your login or your old login. You should not have /home/home? You show two users baronip and barionipc?

What does this show?
echo $USER

That is your login user.

---

### Post by ottosykora on 2012-01-04
@oldfred

how does one produce the 'double' home during install?
For this one would have to set the home to /home/ somehow or what? 
I can not figure out how this can happen with the installer as the mounting points are given  there in kind of dropdown menu.

---

### Post by Jonners59 on 2012-01-04
I'll try and get back tonight, but otherwise it shall be tomorrow AM - the monsters have taken over my PC tonight!!!!  If I am not too tired after they have finished I'll try the code and send the fstb (there are two, one for each OS.

---

### Post by oldfred on 2012-01-04
I do not think you can have a /home/home, so that is why I wanted to see fstab to see if there were 2 entries, one wrong.

Possibly just copying all the folders would create a /home/home. Or a user named home?

 I did find that somehow I had moved Desktop into another folder and it created a new default but all my additions were in the moved one (for a long time until I discovered that, I wondered what had happened).

---

### Post by Jonners59 on 2012-01-04
OK, here is what I have
```
baronipc@baronipc:~$ echo $USER
baronipc
baronipc@baronipc:~$ 
```

The user account and machine are baronipc

And both fstab as screen-shots

I have ALSO just noticed that since I created the second account to run the test, I have had no log-in screen.  It booted straight in to the new account - which I shall now delete - which scared the pants off me as I thought I had gone back to base!!!!:shock:

---

### Post by oldfred on 2012-01-04
I am no expert on mount parameters, but I would use defaults or relatime for /home. Not sure what defaults system normally uses. Your first fstab has defaults but your second does not. Are these two different installs?

.# The fourth field, (fs_mntops), describes the mount options associated with the filesystem.
defaults = rw, suid, dev, exec, auto, nouser and async

Since Hardy (or Intrepid), Ubuntu adds the relatime option by default.
relatime = relatime + defaults = relatime, rw, suid, dev, exec, auto, nouser and async

I do see settings similar to your second fstab here but think defaults is better unless someone knows more.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Note easier to read terminal output if you just copy & paste, if more than a few lines put into # code tags.

---

### Post by Jonners59 on 2012-01-04
Cheers oldfriend
I got the settings from that very article...  copy n pasted the line virtually.

I have just changed the line to default and shall boot up and see what happens, but I am not confident as the same error appears on both OS...  FYI I have my sda HD partitioned as such:
sda 1 Windows7
sda 2 SWAP
sda 3 Ubuntu 64-bit
sda 4 Ubuntu 32-bit

sdb5 = HOME
there are also a Directory for Documents on sdb and another for local Backup.....  Everything is then stored/backed up on another machine....

FYI another thing.  The fstab config for sdb 3, the one i am working on (64-bit) gave the following error messages in Terminal:

```
baronipc@baronipc:~$ sudo gedit /etc/fstab
[sudo] password for baronipc: 

(gedit:8659): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.F5SN7V': No such file or directory

(gedit:8659): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:8659): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.83GK7V': No such file or directory

(gedit:8659): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:8659): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.LPWM7V': No such file or directory

(gedit:8659): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:8659): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.UDWG7V': No such file or directory

(gedit:8659): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:8659): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.0ZQW7V': No such file or directory

(gedit:8659): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
baronipc@baronipc:~$
```  Is this nothing?

---

### Post by Jonners59 on 2012-01-04
OK, just did a re-boot...  Must get rid of that second account!
The desktop switching is better, but it has not solved the problem mentioned.  See screenshot.  It is the same.

Also, since the change to 64-bit the desktop quality is poor.  Not the windows, but the tabs, and panel text.  See screen shot of window

Any more ideas, please?

---

### Post by oldfred on 2012-01-04
Some of the gtk errors are normal or a bug, but you should always use gksudo or gksu with graphical apps and sudo with terminal apps. You kinda have to know which is which to know which sudo to use.

See Graphical sudo about half way down.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You may not have updated settings for video in your new install. What video card/chip do you have?

#To see video:
sudo lshw | grep -A 11 display

My laptop with Intel chip just works on 64 bit and it is 5-6 years old. My desktop is just as old but I have a somewhat newer nVidia 9600 card that needs nomodeset to boot, then the install of the default nVidia driver & it works just fine.

---

### Post by Jonners59 on 2012-01-05
> **oldfred said:**
> Some of the gtk errors are normal or a bug, but you should always use gksudo or gksu with graphical apps and sudo with terminal apps. You kinda have to know which is which to know which sudo to use.

See Graphical sudo about half way down.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You may not have updated settings for video in your new install. What video card/chip do you have?

#To see video:
sudo lshw | grep -A 11 display

My laptop with Intel chip just works on 64 bit and it is 5-6 years old. My desktop is just as old but I have a somewhat newer nVidia 9600 card that needs nomodeset to boot, then the install of the default nVidia driver & it works just fine.

OK, here's what I got....

```
sudo lshw | grep -A 11 display
: 
           *-display
                description: VGA compatible controller
                product: GF108 [GeForce GT 430]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fa000000-faffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:fb000000-fb07ffff
```

---

### Post by ottosykora on 2012-01-05
Oh, I seem to understand now:

you have two installs on two separate partitions and both are trying to use the same /home !!!!

Yes some people claimed to have run this successfully, but in general this is very bad idea. Two still 'living' installs should not try to use same home completely, this will lead to chaos definitely.

---

### Post by Jonners59 on 2012-01-05
OH, I thought you could.  I thought that was the point.  Home could be shared, but others, not, although some elements of etc could such as most of the fstb config (bar the root setting)

Anyway, today she seems better.  I have just the two issues left and some settings to play with:

1. The HOME folder showing as Home/Home in the address bar - if that is an issue.
2. The warning message on my graphics.

Evolution - well that started to fail before the build, so I had moved to Thunderbird, so not fussed about that, but Thunderbird is now running.  I just added the accounts and my prefs and some add-ons, and it's OK now.
Browsers.  Can't find my old settings, so have started the Firefox and Chrome sync accounts and shall setup on my other PCs/Laptops.  That way I shall capture some of the settings and protect from future issues - assuming it does what it says on the tin.

---

### Post by ottosykora on 2012-01-05
>OH, I thought you could. I thought that was the point. Home could be shared,<

no, definitely not

The thing with the sharing home is, that people have then more accounts and thus have more user subfolders in the whole home.
But in you case I understood that you wanted only to install x64 instead of the 32. You did not mention to keep the whole 32 install attached to the same home. This is definitely not what should be made. 

Your setting for firefox might be found in something like .mozilla or in some cases it is also under .firefox or .firefox8 etc.

---

### Post by Jonners59 on 2012-01-05
The plan is NOT to keep the 32-bit, that install was an error, because the Ubuntu CDs and the install do not say which OS they are, so it all got mixed up.

The history of this was that I had a similar setup in 32-bit, but my cpu started showing errors, so I replaced it and upgraded the MB, RAM, etc at the same time (a new machine almost).  I got the Ubuntu up and running no probs, but the WIndows7 was, as usual a pig.  As I only use it for 1 app (Serif X5, a great web design tool), I sat on it until Christmas, when I tried to fix the Windows.  As usual Windows never fixes well, and it screwed up the HD, which then had to be reformatted and started from scratch.

Installed Windows, all OK, then Ubuntu, but had the wrong CD.  I started from 9.10 as it was/is the most reliable and worked my way up.  Then discovered it was a 34-bit.  I downloaded an 11.10 64-bit image and used that for the 2nd partition.  The plan being that when happy with this install I shall rebuild the other with the CD.  The HOME should work as I intend to keep them both at the same level and use the 2nd OS as a backup...  Will the HOME work in this scenario?

Besides HOME, and Documents, what I need is a list of the files, folders, directories that need backing up.  Then I just need the discipline to set up the damned thing and keep it maintained.  I have LOADS of HW space to do this, so it is no excuse.  I have local space, a networked server with space and then I can also use the Firefox and Chrome sync (as examples).

Plan for today is:
Keep an eye out for the fixes to the two items I mentioned below.
Add the new auto-signatures to my eMail accounts.  Thunderbird is not as flexible in this as either Outlook or Evolution, but I am having a go.

Then I need to think about and set up my backup schedules.

---

### Post by ottosykora on 2012-01-05
>2nd OS as a backup... Will the HOME work in this scenario?<

no, unless there are separate user account for each version. It may kind of seem to work first , but resulting in chaos very soon.
If you have two different user folders however for each install, it can be used such way.

To backup: you need to backup the home only. Your settings are inside there.
If you have some special software which not from the ubuntu repository and is entirely installed somewhere like in /opt then you may backup this as well. The rest of the files in the / partition is taken care by the update service of ubuntu. Updates are frequent and so it would be quite difficult for you to keep track of everything and back up some specific files.
You might as well do full backup of the partition (image), some people do it with clonzilla, I use other (commercial) software for that.

---

### Post by oldfred on 2012-01-05
Some like full image backup and others just backup /home. It depends on importance of data. 

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

For me, I just plan on a new clean install, so I do not back up system. I do a resync of /home and a few other things to another drive. But even that can overwrite with the wrong file, so I copy the most important data to DVDs periodically. 

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

Files to include or exclude from full system backup.
[http://ubuntuforums.org/showthread.php?t=1903085](http://ubuntuforums.org/showthread.php?t=1903085)

Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by Jonners59 on 2012-01-05
Cheers Guys
I'll look into these backups and follow through.

I am having some issues with Thunderbird and the auto signature - lucky I have not had to send out anything important.  Sounds like another thread or forum!

If you have any ideas on the two issues below, help shall be warmly received.

Next step shall be to re-install the 32-bit partition.  I think that should be quite easy if I keep the HOME.

Best wishes.

---

### Post by ottosykora on 2012-01-05
> **Jonners59 said:**
> Cheers Guys
I'll look into these backups and follow through.

I am having some issues with Thunderbird and the auto signature - lucky I have not had to send out anything important.  Sounds like another thread or forum!

If you have any ideas on the two issues below, help shall be warmly received.

Next step shall be to re-install the 32-bit partition.  I think that should be quite easy if I keep the HOME.

Best wishes.


under account settings,  you have to set up the signature file first.
Best is to create a file and then you have to tick the 'attach signature from file instead'
From there on the sig will be attached to any new message.


then under composition and addressing, you can tick the include signature in replies, so when you reply, the default sig is automatically added.


as far as the playing with two installs sharing the same home, well you have been warned, do not complain later when all ends up in a disaster and chaos which might be difficult to sort out.
Using two separate user accounts for each distro will work, sharing the same account between two installs will end in chaos for sure.
Note that in the home, there are not just your data files, but also any config settings  and so on. 
Main Q is also what do you need now the 32bit partition when you have your x64 now? 

I would complete the setup of the x64 install, make all work properly and then go and delete the partition with the 32bit install so it will not interfere with the new install.

---

### Post by Rebelli0us on 2012-01-05
You can copy the existing 64-bit installation from another machine.

---

### Post by Jonners59 on 2012-01-06
> **ottosykora said:**
> under account settings,  you have to set up the signature file first.
Best is to create a file and then you have to tick the 'attach signature from file instead'
From there on the sig will be attached to any new message.

That's my problem.  Done all that and it does not work or should I say it is not working.

> **ottosykora said:**
> 
as far as the playing with two installs sharing the same home, well you  have been warned, do not complain later when all ends up in a disaster  and chaos which might be difficult to sort out.
Using two separate user accounts for each distro will work, sharing the  same account between two installs will end in chaos for sure.
Note that in the home, there are not just your data files, but also any config settings  and so on. 
Main Q is also what do you need now the 32bit partition when you have your x64 now? 

I would complete the setup of the x64 install, make all work properly  and then go and delete the partition with the 32bit install so it will  not interfere with the new install..

I do not need the 32-bit so was going to change that to 64-bit too, but my Windows7 is filling up and so I shall need to expand it.  I am seriously thinking of doing as you say, just deleting the partition.  I still have these silly issues in the build though, that I would like fixed.

> **Rebelli0us said:**
> You can copy the existing 64-bit installation from another machine.

How would that work.  Things like the fstab would be wrong and it would not boot??????  In principle, yes, but with so many bits here and there needing mods and changes....

---

### Post by ottosykora on 2012-01-06
as far as Thunderbird sig:
you have to take care that the siganture file is really creeated and the path to it in the setting is correct and also it need to be in some useful format, try with simple text first before creating some fancy html as this might end up in some cases inserting the sig , but it is 'invisible'.
So create some simple text file, with text editor of your choice, store it somewhere in your home folder (your home folder, not the one of the 32bit user or so ;-) ) and point the sig fetcher to it. Leave that signature composing window empty for that for the moment.


copy from other install:
well unlike windows, linux tends to try to configure many things just during start up, so if an install is simply copied , some things get configured on the first run, but with present day computers lot of things is selcted and configured during install, the right drivers downloaded from repos, fstab and other things set up, the bootmanager configured and many other thigngs.
Therefore simple copy can work ins some special cases, where whole setup is very similar. 
Example you have experinced just recently: one install has home in a home folder other install needs home in a separate partition and other install might need separate boot partition, some people have usr and var in separate partitions... complications never end.
So basically just copying an install from different system is not an option as to configure it later 'by hand' can be very complex indeed and real chance that such thing will boot from begining is rather zero.

---

### Post by Jonners59 on 2012-01-06
> **ottosykora said:**
> as far as Thunderbird sig:
you have to take care that the siganture file is really creeated and the path to it in the setting is correct and also it need to be in some useful format, try with simple text first before creating some fancy html as this might end up in some cases inserting the sig , but it is 'invisible'.
So create some simple text file, with text editor of your choice, store it somewhere in your home folder (your home folder, not the one of the 32bit user or so ;-) ) and point the sig fetcher to it. Leave that signature composing window empty for that for the moment.

I have spent hours on this - absolute RUBBISH.  Either txt - which is stupid or HTML which means being a developer, which most of us are not.  And then it is one sig per account.   Pathetic.
I have created HTML files from my docx by doing a Save As, but the images do not show up and all the links were lost.  Managed to recreate the links, but the images just do not know enough.

> **ottosykora said:**
> copy from other install:
well unlike windows, linux tends to try to configure many things just  during start up, so if an install is simply copied , some things get  configured on the first run, but with present day computers lot of  things is selcted and configured during install, the right drivers  downloaded from repos, fstab and other things set up, the bootmanager  configured and many other thigngs.
Therefore simple copy can work ins some special cases, where whole setup is very similar. 
Example you have experinced just recently: one install has home in a  home folder other install needs home in a separate partition and other  install might need separate boot partition, some people have usr and var  in separate partitions... complications never end.
So basically just copying an install from different system is not an  option as to configure it later 'by hand' can be very complex indeed and  real chance that such thing will boot from begining is rather  zero.

I agree.  FYI I have deleted my second partition.

---

### Post by ottosykora on 2012-01-06
>I have spent hours on this - absolute RUBBISH. Either txt - which is stupid or HTML which means being a developer, which most of us are not. And then it is one sig per account. Pathetic.
I have created HTML files from my docx by doing a Save As, but the images do not show up and all the links were lost. Managed to recreate the links, but the images just do not know enough.<

well as I never ever use anything else for e-mails then plain text, I even leave filters on my transfer mail servers remove any mails with html in it, I found it always good enough. 
The company I work for will even filter out all mails with graphics in body as unwanted potential spam or malware and this was in last 3 companies I worked for similar.
So take it easy with forcing graphics to be embeded in each mail. ;-)

**Thunderbird does use one sig per identity ( ***not one per account***)**

In the main configuration page for the account, you will find a button named manage identities.
Click on that one and you have set of forms where you can fill in all sorts of personal details and one of them is also the path to your signature for that identity. As there can not be anyone to have more then one signature for a given identity, this is far enough.
You can then simply change identities when creating a mail, this will then pick the right sig for that identity automatically.

---

### Post by Jonners59 on 2012-01-07
> **ottosykora said:**
> >I have spent hours on this - absolute RUBBISH. Either txt - which is stupid or HTML which means being a developer, which most of us are not. And then it is one sig per account. Pathetic.
I have created HTML files from my docx by doing a Save As, but the images do not show up and all the links were lost. Managed to recreate the links, but the images just do not know enough.<

well as I never ever use anything else for e-mails then plain text, I even leave filters on my transfer mail servers remove any mails with html in it, I found it always good enough. 
The company I work for will even filter out all mails with graphics in body as unwanted potential spam or malware and this was in last 3 companies I worked for similar.
So take it easy with forcing graphics to be embeded in each mail. ;-)

Gosh you must have filtered out a lot of business.  In my 30 years in ICT sales and 3,000 companies, global enterprises and governments I have worked for and with in one way or other I have only come across 1 that only dealt in TxT and he was an it guru, and the other two blocked but sent back a warning that they had been blocked and gave the it dept details so that the receiver could get the domain added to the firewall list of safe addresses.  So much, especially today is done with high graphics.  I want my government authorised partner badge.  It is my credibility and code of practice.  Nearly all the eMails I get from whatever size company or organisation has rich text or graphics.  Don;t care if it was created by HTML or not.  The only exception is the large % who have not set up the auto sig on their mobiles.

Thinking about it, it maybe because of the areas of the business we both work in.  You seem to be in IT from what you are sayng, I have been in selling ICT and dealing at the board, sales, and operational and business end.  I would imagine they have different needs. Maybe.

I think this is more about choice and meeting the needs and wishes of the users, not imposing.  Outlook has been offering this since I can remember and Evolution offers it too.

> **ottosykora said:**
> 
**Thunderbird does use one sig per identity ( ***not one per account***)**

I know, but like most I do not always send out the same sig for every eMail.  Most are informal so a simple sig is all that is required.  And for quotes and intros and sending out details then a nice rich sig is used, and sometimes a half way house if someone who is formal, but I don't need the full regalia.  Again the other two clients cater for this.

> **ottosykora said:**
> 
In the main configuration page for the account, you will find a button named manage identities.
Click on that one and you have set of forms where you can fill in all sorts of personal details and one of them is also the path to your signature for that identity. As there can not be anyone to have more then one signature for a given identity, this is far enough.
You can then simply change identities when creating a mail, this will then pick the right sig for that identity automatically.
Yes, I know about all this.  It isn't enough, as explained above.

If I could fix my Evolution I'd use that, but it decided to break and won't load two of my accounts for some reason.  Better still, if Outlook with Google and IMAP worked on Ubuntu I'd use that, but it doesn't, sadly.

Sorry, if I sound a bit curt, but this thing has taken up so much time and to do something so basic, it is frustrating and annoying beyond belief, and I do not mean to take it out on you, you have been kind enough to try and help me.

---

### Post by Jonners59 on 2012-01-10
> **Jonners59 said:**
> Gosh you must have filtered out a lot of business.  In my 30 years in ICT sales and 3,000 companies, global enterprises and governments I have worked for and with in one way or other I have only come across 1 that only dealt in TxT and he was an it guru, and the other two blocked but sent back a warning that they had been blocked and gave the it dept details so that the receiver could get the domain added to the firewall list of safe addresses.  So much, especially today is done with high graphics.  I want my government authorised partner badge.  It is my credibility and code of practice.  Nearly all the eMails I get from whatever size company or organisation has rich text or graphics.  Don;t care if it was created by HTML or not.  The only exception is the large % who have not set up the auto sig on their mobiles.

Thinking about it, it maybe because of the areas of the business we both work in.  You seem to be in IT from what you are sayng, I have been in selling ICT and dealing at the board, sales, and operational and business end.  I would imagine they have different needs. Maybe.

I think this is more about choice and meeting the needs and wishes of the users, not imposing.  Outlook has been offering this since I can remember and Evolution offers it too.



I know, but like most I do not always send out the same sig for every eMail.  Most are informal so a simple sig is all that is required.  And for quotes and intros and sending out details then a nice rich sig is used, and sometimes a half way house if someone who is formal, but I don't need the full regalia.  Again the other two clients cater for this.


Yes, I know about all this.  It isn't enough, as explained above.

If I could fix my Evolution I'd use that, but it decided to break and won't load two of my accounts for some reason.  Better still, if Outlook with Google and IMAP worked on Ubuntu I'd use that, but it doesn't, sadly.

Sorry, if I sound a bit curt, but this thing has taken up so much time and to do something so basic, it is frustrating and annoying beyond belief, and I do not mean to take it out on you, you have been kind enough to try and help me.

Managed to fix this.  It is not for the average user, but can be done quite simply.

I created all the signatures I wanted in word.  I am guessing Libera or OpenOffice would also work, and then did a "save as html"...  That created a folder with the images in and a txt doc with the html code.  Not being an HTML developer it was a case of reading through the html and recognizing the patterns...

When the html doc was clicked it opened in my browser and the image was great, but when I opened in Thunderbird the images were missing and in their place a description text.

Reverting back to the txt document the description seems to be after ```
alt="
``` and can be changed to whatever I wanted.  To get the address for the image, I went into the browser and copied the image (right click "copy image location") and pasted that into the txt document where the address goes, which seems to be after ```
src="
```.  Save and it works.

Here is my new text for one of the images
[HTML]<a href="http://www.ukan.uktradeinvest.gov.uk/investors-directory/companies/baroni-limited-840?category=10644"> 
<span style='color:windowtext;text-decoration:none'><img border=0 width=116 height=62 id=Picture src="file:///media/Documents/Dropbox/Images for appearence/UKTI_UKAN_Member.jpg" alt="UKTi; UK Trade & Investment.  British Government"></span> 
<br>[/HTML]

I had an issue with one image that it appeared at a given point on a page, which meant that with different page sizes it could cover up other text.  I fixed this by just using the fist part of the above text and replacing the equivalent in the incorrect text.

I am now left with one problem and that is I have an underscore running along all my text after the url in the signature...  I do not know the code for that.

And Signature Switch 1.6.9 as an add-on allows me to have more than one signature per account again, though this should not need to be an add-on.

Hope this helps someone else.

Still need to sort out these two issues, which are more on track and in keeping with the subject:
1. The HOME folder showing as Home/Home in the address bar - if that is an issue.
2. The warning message on my graphics.

Any ideas?

---

### Post by ottosykora on 2012-01-10
>1. The HOME folder showing as Home/Home in the address bar - if that is an issue.
2. The warning message on my graphics.<


well the home/home thing is an issue, but solution is only that all contents would be copied and the proper permissions set etc as it should, but this is rather lot of work and as long as the system knows where to find your home folder, it is ok. In fact it can be even home/home/home/nothome/nothome/myname and if the system knows that this is the place, then nothing spectacular will happen if all used normal way.
Normal way I mean, if someone starts producing some extremely long path, then well one never knows what unpredictable results will occur. 


Relating the warning of graphics, no idea what it is about.

Clear, with the html sig, you can not have just alt empty and and src kind of empty or pointing to unknown place. 

BTW: your src is poniting to the local folder of dropbox and in case this file gets 'malsynched' this can be rather an issue as this will the mean you have an external content in your mail which will definitely trigger malware checks on many servers.
You better place those graphics to some place which will stay fixed and the contents too.
I work for .gov and in case someone sends me such mail, my boss gets an e-mail stating that attack via mail might be going on. (my customers tend to wear green close often)

As far as the sigs concerned, I probably will never understand how can someone need more then one signature with same identity, as the signature is the identity itself, so different signature means different identity..., but well world is full of strange things

---

### Post by Jonners59 on 2012-01-10
Thanks for getting back, ottosykora

> **ottosykora said:**
> >1. The HOME folder showing as Home/Home in the address bar - if that is an issue.
2. The warning message on my graphics.<


well the home/home thing is an issue, but solution is only that all contents would be copied and the proper permissions set etc as it should, but this is rather lot of work and as long as the system knows where to find your home folder, it is ok. In fact it can be even home/home/home/nothome/nothome/myname and if the system knows that this is the place, then nothing spectacular will happen if all used normal way.
Normal way I mean, if someone starts producing some extremely long path, then well one never knows what unpredictable results will occur. 

It doesn't seem to cause any issues, so I shall leave well alone.  No point making further mess.

Re graphics, It had nothing to do with the migration, so i may open a seperate thread.

> **ottosykora said:**
> >Clear, with the html sig, you can not have just alt empty and and src kind of empty or pointing to unknown place. 

BTW: your src is poniting to the local folder of dropbox and in case  this file gets 'malsynched' this can be rather an issue as this will the  mean you have an external content in your mail which will definitely  trigger malware checks on many servers.
You better place those graphics to some place which will stay fixed and the contents too.
I work for .gov and in case someone sends me such mail, my boss gets an  e-mail stating that attack via mail might be going on. (my customers  tend to wear green close often)

As far as the sigs concerned, I probably will never understand how can  someone need more then one signature with same identity, as the  signature is the identity itself, so different signature means different  identity..., but well world is full of strange thing 

Thanks for the tip on the Dropbox file.  I store centrally so I can share amongst other machines, so I can maintain the branding/governance.  I'll look in to changing this.

I use multiple sigs for obvious reasons.  I find it hard to see why it is strange.  Most users who know their clients use multiple.  It is not split personalities.

When sending to a well known person or in replies, etc a simple reply is all that is needed, but in a proposal/bid or addressing a senior official or exec or the like then a more detailed sig with more information would be included.

The first I cameaccross it was with Texaco (EXON in the US) when their Group VP commented about the length of eMail sigs on replies when he knew the sender, and suggested the staff used smaller sigs for internal replies etc, and when mailing well know contacts.  That was in the 80s, and almost everyone I know uses it.  Maybe your just filtering them out before they get to you so you don't see them????

---

### Post by ottosykora on 2012-01-11
>Maybe your just filtering them out before they get to you so you don't see them????<

yes , I have to do so, otherwise IT dept of the company and also at customers side will make my life hell.
At most big companies I used to work during the last 10 years with either as employee or supplier the mails get 'stripped' in a way that the text was extracted and delivered, the rest trashed. This is also here.
As my boss gets notices about filtering events of mails of each of his team, I have to simply guide also my mails via an external filter to strip them myself so to avoid any problems when forwarding them to my account.
All contents needing some external readers etc here will be removed, also any office documents will arrive as text extracts ( you should see an excel sheet made of text.. :-)  ). 
and no zip or what ever, only pdf will arrive as attachment. Picts has to come in the form of a link, which we have to copy/paste to a browser first to get to it, no direct click in the mail client etc.

I remember how some of my colleagues from some german companies get into problems where they had to have in their correspondence all sorts of things, incl exact name and address of the court where the company was registered etc.(legal requirement there). This they tried to include in nice templates in outlook and ware surprised that their mails arrived very mutilated at the customer side who was a major transportation company there. 
So well, I had to adapt to the situation.

---

