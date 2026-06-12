---
title: "Network printer difficulty between two machines, with Ubuntu 14.04"
date: 2016-05-29
forum: Installation &amp; Upgrades
---

### Post by Shobuz99 on 2016-05-29
I'm using a Dell Inspiron 1300 laptop and Ubuntu 14.04; which I have installed over 10.04 LTS.
This machine has always been connected directly to my router eth0 AND enabled wlan0 as well. (Two separate IP addresses same port, same machine)
Before I erased 10.04 I backed it up using Deja-Dup.
Once 14.04 was fully installed, I restored my backup to the 14.04 machine.
I had forgotten that I had the hplip folder & apparently an installed hplip 3.12.2 version that got backed up from the 10.04 machine.
The 14.04 has hplip 3.14.3 when installed.

In the meantime, I set up a printer for the 14.04 machine, an HP-Deskjet 1050-J410 Series "All in One", via USB.
I also was able to make that printer a _network printer_ and got it to **work** even for two Windows machines via wifi, Windows 7 & Windows 8.1** with no problems**.

However, I also have another Dell Inspiron 1525 that I connect to my network wifi. 
But, I have tried for 3 days, to set up the network printer for the Dell Inspiron 1525 using the CUPS interface, or manually and continue to Fail.
I've tried different approaches; such as searching for the printer that is attached to the Dell 1300, entering the Device URI as 
```
 ipp://192.168.1.104:631/printers/HP-Deskjet 1050-J410 Series
```
or
```
 hp/usb/192.168.1.104:631/printers/HP-Deskjet 1050-J410 Series
```
But neither of those is ever recognized by the hplip device manager and says no printer exists on the network when I search from the Dell 1525.

I'm perplexed. I think it may be a conflict. I checked the hplip.conf file, on the Dell Inspiron 1300 14.04 where the printer is installed and works
and it still contains info for version _hplip 3.12.2_. EVEN THOUGH, *hplip 3.14.3* is installed on the machine!

My 2 questions: If I delete the hplip.conf file that refers to version hplip 3.12.2, Will I need to uninstall hplip 3.14.3 and reinstall it to get 
everything to work and be able to connect my Dell Inspiron 1525 to the network printer?
I don't want to delete anything, until I know it won't make matters worse.

Or, is there something else I should be be doing right, or that I'm already doing wrong?

Thank you for any advice or help you may have.
Shobuz99

---

### Post by DuckHook on 2016-05-29
From your description, I imagine that you overwrote some hplip 3.14.3 files when you restored your 10.04 settings from backup. I hope that you only restored your /home directory, because if you overwrote your / (root) directory, you are in trouble. Even restoring your whole /home directory is not good. You will be regressing some 10.04 config files that have long since been superseded and are wrong for 14.04, as you discovered the hard way with hplip. It is always necessary to pick and choose what to restore when pursuing an installation strategy such as yours. I would recommend the following (skipping the backup instructions since it is obvious that you are very thorough about backing up before installing anything):```
sudo apt-get purge hplip
``````
find $HOME -name '*hp*'
```Look for files and directories dealing with *hplip*. They will likely be under:```
/home/<your_name>/.hplip
```...where <your_name> is your name. The next step is very important and potentially dangerous if you get it wrong. If the .hplip directory exists, remove it with: ```
rm -rf ~/.hplip
```Reboot. Then reinstall hplip (the 3.14.3 version) with:```
sudo apt-get update && sudo apt-get install --reinstall hplip
```Case and precision are critical in Linux, so cut and paste these commands into a terminal instead of retyping them. If hplip installs without complaint, proceed with the usual printer setup. Tell us how it goes.

---

### Post by Shobuz99 on 2016-05-29
> **DuckHook said:**
> From your description, I imagine that you overwrote some hplip 3.14.3 files when you restored your 10.04 settings from backup. I hope that you only restored your /home directory, because if you overwrote your / (root) directory, you are in trouble. Even restoring your whole /home directory is not good. You will be regressing some 10.04 config files that have long since been superseded and are wrong for 14.04, as you discovered the hard way with hplip. It is always necessary to pick and choose what to restore when pursuing an installation strategy such as yours. I would recommend the following (skipping the backup instructions since it is obvious that you are very thorough about backing up before installing anything):```
sudo apt-get purge hplip
``````
find $HOME -name '*hp*'
```Look for files and directories dealing with *hplip*. They will likely be under:```
/home/<your_name>/.hplip
```...where <your_name> is your name. The next step is very important and potentially dangerous if you get it wrong. If the .hplip directory exists, remove it with: ```
rm -rf ~/.hplip
```Reboot. Then reinstall hplip (the 3.14.3 version) with:```
sudo apt-get update && sudo apt-get install --reinstall hplip
```Case and precision are critical in Linux, so cut and paste these commands into a terminal instead of retyping them. If hplip installs without complaint, proceed with the usual printer setup. Tell us how it goes.

Thank you DuckHook! I'm glad that I asked! I will do this tomorrow, very carefully and report back. 
I really appreciate the advice re: backup. I did NOT back up "root"....just the entire /home folder.
Even so, I can now appreciate that I was too quick and too certain that it would be sufficient to do the whole /home directory.
Of course, if I hadn't waited so long to upgrade from 10.04, I may not have had the same risks to deal with.... c'est la vie

Shobuz99

---

### Post by DuckHook on 2016-05-30
You shouldn't feel bad about the way you restored the entire /home directory. The fact that you thought through the whole process and made a backup at all is laudable. You make the message in my sig proud. \\:D/

You may wish to actually reinstall a fresh 14.04, but this time, create a separate *data* partition where you restore all of your old /home data to. This partition would then act as your permanent data repository. You then link back only those directories your want to your standard /home directory after each install. That way, you don't have to "restore" anything. Every install completely nukes the old OS including all config files. Directories like "Documents," "Videos", "Music", etc just get re-linked after each install. It's the strategy that I follow and is very convenient.

It goes without saying that this does not eliminate the need for routine backups, and especially before an OS upgrade or install.

---

### Post by Shobuz99 on 2016-05-30
> **DuckHook said:**
> You shouldn't feel bad about the way you restored the entire /home directory. The fact that you thought through the whole process and made a backup at all is laudable. You make the message in my sig proud. \\:D/

You may wish to actually reinstall a fresh 14.04, but this time, create a separate *data* partition where you restore all of your old /home data to. This partition would then act as your permanent data repository. You then link back only those directories your want to your standard /home directory after each install. That way, you don't have to "restore" anything. Every install completely nukes the old OS including all config files. Directories like "Documents," "Videos", "Music", etc just get re-linked after each install. It's the strategy that I follow and is very convenient.

It goes without saying that this does not eliminate the need for routine backups, and especially before an OS upgrade or install.

Welp... What *you* suggested seems to have worked. Here are the output results from terminal for the "purge":

```
 The following packages were automatically installed and are no longer required:
  libntdb1 linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
  python-ntdb
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  hplip* hplip-gui* printer-driver-postscript-hp*
0 upgraded, 0 newly installed, 3 to remove and 6 not upgraded.
After this operation, 1,631 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 238913 files and directories currently installed.)
Removing hplip-gui (3.14.3-0ubuntu3.4) ...
Purging configuration files for hplip-gui (3.14.3-0ubuntu3.4) ...
Removing printer-driver-postscript-hp (3.14.3-0ubuntu3.4) ...
Removing hplip (3.14.3-0ubuntu3.4) ...
Purging configuration files for hplip (3.14.3-0ubuntu3.4) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for cups (1.7.2-0ubuntu1.7) ...
robotics1@robotics1-ME051:~$ 
```

Next the results for files that were listed on the search:
```
 robotics1@robotics1-ME051:~$ find $HOME -name 'hp*'
/home/robotics1/Downloads/hplip-3.12.2.run
/home/robotics1/Desktop/hplip.desktop
/home/robotics1/.local/share/applications/hplj1020.desktop
/home/robotics1/.wine/drive_c/Program Files/Macromedia/Dreamweaver MX/JVM/bin/hprof.dll
/home/robotics1/.wine/drive_c/Program Files/Macromedia/Dreamweaver MX/JVM/bin/hpi.dll
/home/robotics1/.wine/drive_c/users/rickwhite/Local Settings/Application Data/HP/AtInstall/001/hp-dqex5.log
/home/robotics1/.wine/drive_c/users/rickwhite/Local Settings/Application Data/HP/AtInstall/004/hp-dqex5.log
/home/robotics1/.wine/drive_c/windows/system32/DRVSTORE/hpvpl04_462C83F34A8C5BF8541794C5DC8DAAAE2144823A
/home/robotics1/.wine/drive_c/windows/system32/DRVSTORE/hpvpl04_462C83F34A8C5BF8541794C5DC8DAAAE2144823A/hpdj_2050_04.gpd
/home/robotics1/.wine/drive_c/windows/system32/DRVSTORE/hpvpl04_462C83F34A8C5BF8541794C5DC8DAAAE2144823A/hpvpl04.ini
/home/robotics1/.wine/drive_c/windows/system32/DRVSTORE/hpvpl04_462C83F34A8C5BF8541794C5DC8DAAAE2144823A/i386/hpinksts8911LM.dll
/home/robotics1/.wine/drive_c/windows/system32/DRVSTORE/hpvpl04_462C83F34A8C5BF8541794C5DC8DAAAE2144823A/i386/hpvplres04.dll
/home/robotics1/.wine/drive_c/windows/system32/DRVSTORE/hpvpl04_462C83F34A8C5BF8541794C5DC8DAAAE2144823A/i386/hpinkcoi8911.dll
/home/robotics1/.wine/drive_c/windows/system32/DRVSTORE/hpvpl04_462C83F34A8C5BF8541794C5DC8DAAAE2144823A/i386/hpvplui04.dll
/home/robotics1/.wine/drive_c/windows/system32/DRVSTORE/hpvpl04_462C83F34A8C5BF8541794C5DC8DAAAE2144823A/i386/hpinksts8911.dll
/home/robotics1/.wine/drive_c/windows/system32/DRVSTORE/hpvpl04_462C83F34A8C5BF8541794C5DC8DAAAE2144823A/i386/hpvpldrv04.dll
/home/robotics1/.wine/drive_c/windows/system32/DRVSTORE/hpvpl04_462C83F34A8C5BF8541794C5DC8DAAAE2144823A/i386/hpfime51.dll
/home/robotics1/.wine/drive_c/windows/system32/DRVSTORE/hpvpl04_462C83F34A8C5BF8541794C5DC8DAAAE2144823A/hpvpl04.cat
/home/robotics1/.wine/drive_c/windows/system32/DRVSTORE/hpvpl04_462C83F34A8C5BF8541794C5DC8DAAAE2144823A/hpvpl04.inf
/home/robotics1/.wine/drive_c/windows/system32/catroot/{f750e6c3-38ee-11d1-85e5-00c04fc295ee}/hpvpl04.cat
/home/robotics1/.wine/drive_c/windows/inf/hpvpl04.inf
/home/robotics1/.wine/drive_c/windows/twain_32/HP Deskjet 1050 J410 series/hpxsTwain.ds
[B]/home/robotics1/.hplip/hp-systray.lock
/home/robotics1/.hplip/hplip.conf
/home/robotics1/.hplip/hplip_queues.log[/B]
robotics1@robotics1-ME051:~$ 
```

I did not choose to remove any files that *could've* been hp related in the /.wine directory.
I also should've told you that the /.wine files were from the restore of the old 10.04 data.
After I did that initial restore, I had to reinstall Wine to make those files work.
Is it *possible* that these files also created issues, setting up a network printer?

I DID remove the highlighted files using the command you gave me and here are those results:
```
 robotics1@robotics1-ME051:~$ rm -rf ~/.hplip
robotics1@robotics1-ME051:~$ 
```

Now the results for the reinstall of hplip 3.14.3:
```
 robotics1@robotics1-ME051:~$ sudo apt-get update && sudo apt-get install --reinstall hplip
[sudo] password for robotics1: 
Ign http://us.archive.ubuntu.com trusty InRelease
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [65.9 kB]
Ign http://archive.canonical.com trusty InRelease                              
Hit http://security.ubuntu.com trusty-security InRelease                       
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://us.archive.ubuntu.com trusty-proposed InRelease                     
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://archive.canonical.com trusty Release                                
Hit http://extras.ubuntu.com trusty Release                                    
Get:2 http://us.archive.ubuntu.com trusty-updates/main Sources [275 kB]        
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Get:3 http://us.archive.ubuntu.com trusty-updates/universe Sources [155 kB]    
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://archive.canonical.com trusty/partner Sources                        
Get:4 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,939 B] 
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Get:5 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [736 kB]  
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Get:6 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [361 kB]
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Get:7 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.6 kB]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://us.archive.ubuntu.com trusty-proposed/universe i386 Packages    
Hit http://us.archive.ubuntu.com trusty-proposed/main i386 Packages        
Hit http://us.archive.ubuntu.com trusty-proposed/multiverse i386 Packages  
Hit http://us.archive.ubuntu.com trusty-proposed/main Translation-en       
Hit http://us.archive.ubuntu.com trusty-proposed/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-proposed/universe Translation-en   
Hit http://us.archive.ubuntu.com trusty/main Sources                       
Hit http://us.archive.ubuntu.com trusty/universe Sources                   
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                 
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages             
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages           
Hit http://us.archive.ubuntu.com trusty/main Translation-en                
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en          
Hit http://us.archive.ubuntu.com trusty/universe Translation-en            
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US             
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US       
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US         
Fetched 1,613 kB in 13s (116 kB/s)                                             
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libntdb1 linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
  python-ntdb
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  printer-driver-postscript-hp
Suggested packages:
  hplip-gui hplip-doc system-config-printer
The following NEW packages will be installed:
  hplip printer-driver-postscript-hp
0 upgraded, 2 newly installed, 0 to remove and 6 not upgraded.
Need to get 794 kB of archives.
After this operation, 1,464 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main hplip i386 3.14.3-0ubuntu3.4 [64.0 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main printer-driver-postscript-hp all 3.14.3-0ubuntu3.4 [729 kB]
Fetched 794 kB in 0s (1,321 kB/s)                
Selecting previously unselected package hplip.
(Reading database ... 238797 files and directories currently installed.)
Preparing to unpack .../hplip_3.14.3-0ubuntu3.4_i386.deb ...
Unpacking hplip (3.14.3-0ubuntu3.4) ...
Selecting previously unselected package printer-driver-postscript-hp.
Preparing to unpack .../printer-driver-postscript-hp_3.14.3-0ubuntu3.4_all.deb ...
Unpacking printer-driver-postscript-hp (3.14.3-0ubuntu3.4) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for cups (1.7.2-0ubuntu1.7) ...
Setting up hplip (3.14.3-0ubuntu3.4) ...
Creating/updating hplip user account...
dpkg-statoverride: warning: --update given but /var/run/hplip does not exist
 Removing any system startup links for /etc/init.d/hplip ...
Setting up printer-driver-postscript-hp (3.14.3-0ubuntu3.4) ...
robotics1@robotics1-ME051:~$ 
```

Once this was all complete I went to the task of "adding a printer" because before I did everything above,
I decided that I would need to remove the printer install that was there that didn't work anyway, for Network.
This is where I'm still unsuccessful. I'm starting to doubt that I'm doing the printer installation correctly, for 
a "network printer". I already had it setup for a "direct to local printer" with the USB connection, and it worked fine.
But I wanted to initially use that printer address for use as a network printer; however I realized that address would not work that way.
This is the address:
```
 Device URI:  hp:/usb/Deskjet_1050_J410_series?serial=CN17G13N0F05QT 
```

Since I've tried connecting via wifi from my Dell 1525 laptop, I have had NO success using this code:
```
 http://192.168.1.104:631/printers/Deskjet-1050-j410-series/ 
```
or this using ipp:
```
 ipp://192.168.1.104:631/printers/Deskjet-1050-j410-series/ 
```

When I put either of these addresses in the "Find a Host" section of the Dell 1525, it immediately jumps to the
"Enter URI" section and will *not* search for a network printer, using either of the above links.

In both cases, I am unable to get a successful install and print remotely from my Dell 1525 wifi.
To add insult to injury, all the setups I did with the Windows machines are now inoperable.
This is frustrating. :-(
I suspect there may be more problems associated with my "restore" move, that I have yet to realize.

I think your suggestion to do a clean install of 14.04 and make 2 partitions, 1 for the distro and 1 for the restored files,
is a great idea. It may be the only solution left for me at this point.
Unless you have some additional suggestions before I do that? :-)

Shobuz99

---

### Post by DuckHook on 2016-05-30
Let's back up a bit.

[LIST=1]
[*]I take it that you were using the 1300 as a printer server. That's why it was connected to the router by ethernet and to the printer by USB?
[*]But if so, why does it have WINE installed? WINE is pretty serious business for such an old machine (10+ yrs) and it's the first time you've mentioned WINE.
[*]How did you get network printing to work in the 10.04 days? For both the Dell 1525 and for the Windows machines?
[*]I'm guessing (it's only a guess) that you installed WINE to enable Windows printer sharing (which isn't the best way to go about things, frankly). Am I correct?
[*]
[/LIST]
Anyway, it's a good idea, when asking for help, to paint as clear a picture as possible of your absolute end goal, rather than just trying to solve a perceived problem that occurs in some middle step. Often, there's a better solution involving far less complexity.

If my guesses above are totally out to lunch, then my apologies, but the larger picture was never given, thus the guesses.

---

### Post by Shobuz99 on 2016-05-31
> **DuckHook said:**
> Let's back up a bit.

[LIST=1]
[*]I take it that you were using the 1300 as a printer server. That's why it was connected to the router by ethernet and to the printer by USB?
[*]But if so, why does it have WINE installed? WINE is pretty serious business for such an old machine (10+ yrs) and it's the first time you've mentioned WINE.
[*]How did you get network printing to work in the 10.04 days? For both the Dell 1525 and for the Windows machines?
[*]I'm guessing (it's only a guess) that you installed WINE to enable Windows printer sharing (which isn't the best way to go about things, frankly). Am I correct?
[*]
[/LIST]
Anyway, it's a good idea, when asking for help, to paint as clear a picture as possible of your absolute end goal, rather than just trying to solve a perceived problem that occurs in some middle step. Often, there's a better solution involving far less complexity.

If my guesses above are totally out to lunch, then my apologies, but the larger picture was never given, thus the guesses.

**1** - Yes. I have been using the Dell 1300 for a print server for some time, connected to the router, by ethernet cable and the printer connected by USB.
**2** - It had WINE installed long before I decided to use it as a print server. 
     I installed WINE, 10 years ago to accommodate my Web Development software, Dreamweaver MX 2004. 
     I was in the web design business personally AND I also managed and developed a web site for my former union local, as IT Admin from 2001 to 2015. 
     I began using Dreamweaver around 2006. I used that software on a daily basis for about 10 years, and frankly I still do use it to periodically update my personal website 
     re: my 52 years in the music business as a musician and vocalist for several bands, some of which have made recordings during the 1960's that were hits...
     I didn't tell you that back story previously because I didn't think you would want to hear my reasons for using antiquated software. 
     I used 10.04 LTS for much longer than it was intended, and I was *strongly urged* to upgrade by other Ubuntu forum personnel.
     I didn't really want to tell you a life history of that machine, because I figured you'd be bored and ultimately condescending about it. I apologize.
**3** - I got it working for both Windows and Linux machines using the method that I'm using now, only it's not working this time. 
     I suspect that i have done something wrong over the course of this upgrade from 10.04 to 14.04, and I admit I've forgotten how I originally had success, 
     such a long time ago getting  the printer set up to be local & network with one "add a printer" process. 
     For some reason, I've failed to recall the steps I took, back then that allowed it to work without the struggle I'm having now.
**4** - No. I did not install WINE to enable Windows printer sharing. See Item #2.

I agree that jumping in the middle of a situation and trying to solve it with "unknowns" lurking in the shadows is not the best way to go.
I know that from experience, because I've also been a computer tech as well as an Optical & Electrical Test Engineer at IBM for 28 years.
I'm retired now (66 yrs old) and I pursue helping people with far less computer knowledge than I have. 
They do the same thing: they don't give me enough information because there is so much they really don't understand. 
I try very hard not to scold them when they say "it won't work' and expect me to figure it all out on my own because I'm the computer tech and that's what they're paying me for...
So I get it, DuckHook. I really do. I owe you another apology for being a hypocrite to my own frustration. I apologize.

Now...if you still want to help, that's great; but if not, I understand. 

And that said, I may just wipe the drive, start over and install 14.04 clean and partition the little 40GB PATA drive as you suggested and then restore the backup to a separate partition, 
and gradually install one piece at a time until I get it back to where I want it.
Let me know what you decide, and if you'd prefer I'll request this thread to be closed and/or deleted, because it won't be of much use to anyone.
Thank you for your help, thus far.

Shobuz99

---

### Post by DuckHook on 2016-05-31
My sincerest apologies. Had no idea I came across that way. It was not my remotest intent to suggest that your info was deficient and the last thing I want to do is come across as a scold. I was just surmising why WINE was installed and making some assumptions. Purely a technical approach that missed sight of how lack of body language in this medium can lead to misunderstanding.

Continue to want to help if I haven't peeved you off with unintended insult.

---

### Post by DuckHook on 2016-05-31
As partial amends, please allow me to present the following options:

Now I understand why WINE is installed. If you are using Windows apps, then its continued presence is necessary and useful. As an aside, I am amazed that you have gotten it to work. It is notoriously fickle, but good on you that you've tamed it.

Re network printing: your install of 14.04 probably nixed your old share settings. To re-enable them, go into Printers app > servers > and turn on "Publish shared printers connected to this system" A graphical walk-through is probably helpful, as follows:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

The same wiki page shows you how to set up the Windows machines again as well.

It is also possible that your new install has forced your dhcp server (usually your router) to assign a new IP address. If that is so, then your old settings in your other computers won't work as they will be pointing to the old address. To find your new address (it *might* be same as the old), do:```
ifconfig
```You are looking for the IP string after "inet addr"

It is a good idea to go into your router and set the MAC address of your Dell 1300 up as a reserved static IP. That way, it will be assigned the same IP address no matter what OS you install on it, and your other machines will always find it (provided it has been set up to share printers as per instructions above). The MAC address can also be found from ifconfig. It is the string after "HWaddr". Enter this string into your router's static IP page, assign it the IP you want, and then, every time you boot up your computer it will have that and only that IP address.

I don't know how to advise you about another reinstall. It is possible that you've clobbered other config files with 10.04 versions, but if you no longer use the machine for anything else other than a printer server, and you get it working as such, then it seems unnecessary work to do yet another install. On the other hand, a lot of people like things all trim and proper (I'm like that) and can't stand the idea of wonky configs, so would choose to reinstall almost as a matter of principle. To be fair, there is a practical element: some configs may not come into play until a few months from now, at which point you might be scratching your head wondering why something doesn't work when it is actually the result of a forgotten clobbered config file.

Why don't you try reactivating printer sharing first? If that solves your printing issues, then you have the luxury of choice and can decide later whether you want to go to the trouble of reinstalling.

---

### Post by Shobuz99 on 2016-05-31
I sent similar information to you via PM. I will take your advice and review everything in an "order and step" procedure, and then do each thing step by step until I get a fail.
That fail should expose what the problem is, and then maybe we can get this resolved. :-) Thank you!

shobuz99

**UPDATE Edit!!!!**

**It's Working!!!!!** 
Here is all I did: I gave up trying to create a separate "network printer" for the same printer I had setup as a direct USB on the Dell 1300.
Then I went to the Windows Vista machine (wifi) and added a network access to that printer on the Dell 1300. It worked!!!
Next I went to the Dell 1525, opened the printer section, and deleted everything. I then added one printer as being the network printer
on the Dell 1300. Once I finished that, I ran a test page. At first it gave me a "blue & white information" icon over the printer icon in that section...
I thought that meant that once again, it could not connect...but I was wrong this time.. That "blue & white information" icon disappeared and turned into
a "red & white" minus or negative sign for a moment...then that disappeared and the test page began to print!! 
I tested it again, to make sure. The same thing happened with the "blue & white information" icon and then the "red & white" minus or negative sign...
But it printed again!! It works!!!
However, I need to investigate why I get any little error icons at all. It should not be doing that.
That's the best description and solution that I can provide at this point. I know it's not much help to others;
so if you want me to, I'll mark this solved and you can delete the thread or change it to "closed"... Whatever you feel is the best thing to do.
I *did* want to resolve this with a clearer understanding of what I may have done wrong or what may have caused the problem from a software/hardware perspective.
I guess that remains for me to clearly understand, at a later time.

All in all, I sincerely THANK You for your patience and support throughout this. You have given me food for thought on a better way to diagnose
this problem, if I for some reason "forget" what I did, this time. ;-)
Also, I want to look into making the MAC address a static IP address on the Dell 1300, so that no matter what, it will ALWAYS connect through my network
to that printer.
Again, THANK You sincerely for all your help. I couldn't have done it without you. :-)

Shobuz99

---

### Post by DuckHook on 2016-05-31
Very happy that things worked out Shobuz99. Can't say I contributed much. You worked this one out for yourself.

Marking the thread *solved* is more than sufficient. No need to close it. If you run into problems in the next few weeks, you may wish to post to it again. And despite your guess, others could very well find a lot of useful things in here.

---

### Post by Shobuz99 on 2016-06-05
> **DuckHook said:**
> Very happy that things worked out Shobuz99. Can't say I contributed much. You worked this one out for yourself.

Marking the thread *solved* is more than sufficient. No need to close it. If you run into problems in the next few weeks, you may wish to post to it again. And despite your guess, others could very well find a lot of useful things in here.
You're too modest, DuckHook. Seriously.
Meanwhile back at the "Old Geek" ranch, I've discovered that I've not really figured it out permanently... :confused: :(
It turns out that I got the printer to work, using one connection to the printer by usb, and my wireless Dell could see it and connect to it because
I wasn't using HPLIP Device Manager. 
So, ever curious and not prone to "leave well enough alone"....I installed and loaded HPLIP Device Manager (hplip-gui) via Synaptic Pkg mgr, 
and it came up saying I had NO Devices installed on the Dell 1300 that was ethernet connected AND wireless connected to my router.. But it IS connected!

I've tried everything to get the HPLIP Device Manager to "find" the printer that's connected by usb to the Dell 1300; whether I'm trying it from the Dell 1525 wirelessly OR
even via the Dell 1300 that actually IS connected to the printer by usb! The HPLIP Device Manager simply does not find it.

I've tried ALL the options it recommends, whether manually, and giving it an IP address, an http: // 192.168.1.xxx, an ipp://192.168.1.xxx or using the Auto search... 
No matter what I choose, the printer does not exist according to HPLIP Device Manager, when loaded on either the Dell 1300 or Dell 1525.
One exception is that CUPS (localhost:631) _does see_ the printer but it says 'Held", when I try to print a document and releasing doesn't help when in the Queue section. 
I got an error message during some of this rampage of setup denials and searching:
"HPLIP Device Status:
Deskjet_1050_J410_series Printer (CN17G13N0F05QT)
Device communication error (5012)" 
I haven't looked this error up yet....

_BUT_, if I don't use HPLIP Device Manager, and I just setup the printer using the "Printing" feature that comes with Ubuntu 14.04, I can search and find it
and it is there. My Windows Vista tower also recognizes it. So that's why I assumed that I had fixed the problem. I didn't. I just circumvented HPLIP Device Manager.
How this makes any sense, I'll never know.
BTW... I am also trying to use Samba on the Dell 1300, just in case that will help matters. It doesn't seem to though..
Anyway, I'm considering what you said about "restoring" the 10.04 LTS version Data that I backed up, as the *potential culprit*.
I think you're right about a possible "mess" that is weaved into the 14.04 LTS on the Dell 1300, where 10.04 LTS used to reside.
I'm going to try and figure this out before I give up and do a clean reinstall of 14.04 to the Dell 1300 and partitioning the drive
so the backup can be restored to one partition and the clean Ubuntu 14.04 can be installed on the other.
But I'll exhaust all my "detective work" first. Then I'll report back here.
if you have suggestions or if you think I should start a new thread, please say so. I'd be ever so grateful. :D 

best,
Shobuz99

---

