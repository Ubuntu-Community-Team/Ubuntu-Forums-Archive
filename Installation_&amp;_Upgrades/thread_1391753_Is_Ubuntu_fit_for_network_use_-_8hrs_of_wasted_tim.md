---
title: "Is Ubuntu fit for network use - 8hrs of wasted time later - maybe"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by isonomia on 2010-01-27
First let me say I've heard about linux for years and did look at getting a linux machine around two years ago, but I couldn't find anything that said "this or that machine will certainly work with linux", so I had to assume there would be problems. And, because I didn't know anyone with linux (except a hard drive unit that turned out to have linux - and I was glad I once learnt unix) - well it might be aright for the nerds like me, but would my wife sleep with me again if she got so angry with a half baked operating system.
 
 Well - micro$oft did their bit - the mouse stopped working and it is certainly microsoft's driver and will they fix the problem? And will their latest next upgrade to slow the machine even more fix anything except force people to buy new software? No!
 
 So, the machine operating system had to be changed from vista, and since micro$oft caused the problem, I didn't want to install XP ... and so that is why I tried Ubuntu (I think it was my preferred choice 2 years ago).
 
 PROBLEM 1 - I could not make a CD that would boot up. Eventually solved by downloading a new version and using a DVD instad of the CDs.
 
 PROBLEM 2 - when it said "use documents and settings from windows" during the install, it never occurred to me that it would try to download the 60gbytes of photos on the network drive onto the 12gbit partition. THIS HAS GOT TO BE FIXED, because I ended up having to reformat the partition 
 
 PROBLEM 3 - How do you uninstall Ubuntu? A great operating system lets people stop using it giving them that feeling "Hey they over excelled at the end ... perhaps I'll give it another try". 
 
 PROBLEM 4 - When it loaded it kept saying there was a problem with the power settings and then just after the login it would turn off and come back to the login, and then you log in and then it would turn off and come back to the log in. HENCE THE CLEAN INSTALL - and this time I quickly realised it ran out of disc space and removed all the photos it had taken an hour downloading which it shouldn't. (since the latter reinstall, the problem seems to have disappear - I assume essential system information couldn't be stored cause basically the entire space was taken up with pictures of birthday parties)
 
 PROBLEM 5 - Is that it keeps saying the battery is 49.8% of capacity - do I really care? It's a laptop, not a portable - sound suspiciously close to 50% like a software error!
 
 PROBLEM 6 - I went to runescape to test the performance against the vista, and what the **CKing *ell was that parlava? I had to drop out of the windows into command line, and thank god I'd had all that experience, because if I hadn't I'd have turned tail and gone and bought a windows machine. Sun/Java are such idiots.
 
 PROBLEM 7 - NETWORK DRIVES- NETWORK DRIVES- NETWORK DRIVES- NETWORK DRIVES- NETWORK DRIVES- NETWORK DRIVES- NETWORK DRIVES- NETWORK DRIVES- NETWORK DRIVES- NETWORK DRIVES- NETWORK DRIVES- NETWORK DRIVES.
 
 First, (and in retrospect) I remember I could see the various "sub-drives" on the fsg, until the software upgraded to 0.14 to 0.17 -- then they disappeared (but who knows, it did object because so many mounts)
 
 And this is really why I'm writing, because I had expected some problems (which I didn't get many), but to be honest, given the huge number of linux machines running on servers, it had never occurred to me that linux itself would be such a pig of a system for network drives.
 
 It boils down to this. Our family, each has their own space on the network drives, which they could in windows access as //fsg/<name>. The kids couldn't read/write to each other's drives, but the parents can. There is a family drive (i.e. it is mapped to a drive on each login) and there is an "adults" drive which contains all the porn ... no just joking ... contains all the downloaded software, backups etc, which are part of the system, and there's a drive which is a home webpage - on which I test webpages.
 
 So, we all have our own signin, and the benefit of that, is that the kids only see their own drive and the family's and there is no hassle that "freddy's reading my ... or " ... it's their own private space, which I can backup - and they can all use any machine for homework, without fighting over the fastest machine - cause someone has to have it because they are "doing homework".
 
 So, obviously one of the first things I tried to do was to map a network drive to a local ... So that the correct network drives appeared on the desktop as folders "My_Network", "Family_Network". Could I do it?
 
 I searched for "map network drive on linux" ... for what I believe is an NTFS formatted drive (I don't need to know on windows) and the information seemed to suggest I had to use Mountmanager or NTFS configuration tool. Well, what crap advice that was, because I couldn't see any way to configure anything except an internal drive - so that was wasted time.
 
 So I found a simple suggestion of creating an sh file with the lines gvfs-mount smb://fsg/<name> and putting it in my startup applications. Well, it worked fine when I ran it from the command line, but did it work when it put it in the list of applications on startup ... and can pigs fly? 
 
 So, after a couple of hours of trying to mount drives with no success and then trying to mount drives with getting blank folder contents, I worked out that I needed something in fstab of the form (and I leave this here in case it helps):-
 
 //fsg.lan/<name>  /media/<name> sbmfs _netdev,username=obama,password=peanuts,auto,file_mode=0777,dir_mode=0777,gid=1001
 
 Where fsg.lan is the network name assigned by the internal dns to the fsg drive (which used to be reached by simply fsg in windows)
 <name> is the name of the person/drive,username, password are (one of the valid) names supplied to the fsg device, and gid is the group id of a new group which everyone was assigned to as part of the family ... which lets everyone view the network drive.
 
 This worked OK, for the first "family" drive, it appeared like magic on the desktop of everyone, but obviously, because the drive was being assigned a single user/passwd, obviously either everyone could use the drive or no one!
 
 So, next I tried setting fstab to "noauto", which in theory should allow me to put "sudo mount  /media/<name>" in a config file for each person, which as I thought would have only shown the drives that had been mounted. But of course, when I put such a file in the list of startup tasks, no the **** it wouldn't work, and in any case, even the drives which hadn't been mounted appeared on the desktop (and it's difficult enough explaining to kids about their network drive, without making it more complicated by putting a load of mess on the desktop --- a bit like buying a brand new car, and then having someone liberally paint diskdrive icons all over it.
 
 Anyway I tried putting the "sudo mount" commands that worked on the desktop, in the .profile and various other files and of course none of it worked.
 
 Finally, I spotted that I could mount the drive by using the places->connect to a server, selecting windows share as the type.
 
 UNFORTUNATELY, UNFORTUNATELY, UNFORTUNATELY, UNFORTUNATELY, UNFORTUNATELY,
 
 That is all but
 
 USELESS, USELESS, USELESS, USELESS, USELESS, USELESS, USELESS, USELESS,
 
 because, when I mount a drive that way, I can't see the files under e.g. gimp or several other applications like audacity, so whilst that "works" as far as the file viewers are concerned, basically my conclusion after 8 hours meddling with Ubuntu is that 
 
 [U][B]UBUNTU/LINUX, isn't fit for use on a network. (but see later)
[/B][/U]
 The solutions to this are pretty simple:
 
 1. The fstab, has to be able to accept username and password based on the user. E.g. $USER, $PASSWD, or at least default with a "user", parameter to the user's username and password.
 
 2. The fstab, must make use of the "~", so that the credentials can be stored in a user file.
 
 3. There has to be an option/correction to Ubuntu so that Drives that are listing in fstab, which are not yet mounted, are not displayed. 
 
 4. AND (Or), the mount command has to work on some batch on startup, and this batch must be different for each, and the mount command must use a credentials file with a password that can be hidden.
 
 _**But hey, it's looks wonderful, the kids are really impressed - and already addicted to nibbles - but is it fit for purpose - NO!**_
 
 In short, I can see no way of e.g. attaching a network drive which allows me to edit pictures from the laptop, which doesn't also require everyone to have the same access, and potentially have whole directories of e.g. backup work pictures mistakenly deleted by children.
 
 
 .... But the mouse is working!!
 
 ..... but it now crashes every time I shut down 
 
 Ubuntu 9.10 <computer> tty1
 <computer? login: init: statd main process (2182) killed by KILL signal
 init: stad main process ended, respawning
 [   759.280050] CIFS VFS: No response for cmd 50 mid 63
 [   815.296055] CIFS VFS: No response for cmd 50 mid 39
  {{Funny there was many more last time - so many I powered off
 Could this link to the number of CIFS I have in fstab!!!!!! I.e. two!}}
 
 Possibly it's because one post told me to use a commandline command to add something to the system list of things to do, and now I've got to go back through about 100 sites finding the one that mentioned that .... or possibly quicker, just reinstall ubuntu for the third time! .... Or perhaps just uninstall, altogether - and put in an operating system that does work with network drives like XP, or perhaps better 2000!!!!
 
 _**Correction**_
 
 It does work on the network with gimp. Perhaps it didn't work on 9.14, and then it does on 9.17, but it is working today. IT DOESN'T WORK on compizConfig SettingManager ... which is what the kids were mucking about on for a while, and was why I needed gimp to make some pictures.
 
 _**Conclusion**_
 
 1. I am now sitting writing on a windows machine, with a linux machine with four drives. Two are automatically loaded as I require - but I should be able to have different drives on each user's desktop.
 
 2. The two other drives, which I've clicked on the bookmark, now appear to be almost what I wanted, and if I could only work out how to create a bookmark with the same actions on the desktop, I might conclude Ubuntu is fit for purpose (except the way you have to install java for runescape)
 
 3. Setting up disk drives should be included in the installation of ubuntu. Not necessarily because it has to be included at this stage, but because if you search for help on "mounting a drive in ubuntu" ... it takes you down a blind alley, and having the user presented with the question "do you wish to bookmark server (or whatever is ubuntu terminology) ... you can do this later under places->connect to server. The point is that YOU HAVE to stop people going down this blind alleyway. Firstly by telling the terminology for "mount a drive" which is the windows term and secondly by telling them it is possible to do it in Ubuntu (unless you know, reading the internet suggests it isn't possible).
 
 4. Talk to sun about java install ... it's crap!
 
 5. _**WHEN YOU ASK DO YOU WANT TO TRANSFER DOCUMENTS AND SETTINGS**_, just remember that not everyone keeps their documents on the local drive, ***PUT A NOTE ... THIS INCLUDES DOCUMENTS ON NETWORK DRIVES ... INCLUDE AN OPTION: settings only ... I will transfer documents myself. ... better still give a tick list with sizes of the various pictures, documents etc.***
 ... and that I was thinking (the computer doesn't have any documents on it, so a few personal settings, like email wouldn't do any harm)
 
 [I]Finally well done! It actually went a lot better than I thought (except obviously the network ... which may be lack of communication more than software), and it's so close to being a hassle free install that if I were microsoft I would be seriously worried!

--------------------------
postscript:

1. I shoud mention that if you bookmark you do get drives to appear on the desktop, but they disappear when the machine is switched off/on

2. I removed the two drives from fstab, rebooted, and I still cannot see any contents on the FSG (freecom unit with linux, discs formatted to work with windows - shouldn't be a problem!) -  I can however see the contents of shared drives on other PCs on the network - AND THEY ASK FOR A LOGIN USERNAME/PASSWORD. 

Checked Mtab ... no mention of fsg (I thought an entry there might confuse something) ... checked another user login ... still can't see the contents!

3. I still get the delay at switchoff with "<computer> login", but the other two errors have gone away, so it's likely these are a result of the config in fstab.

4. And why is there no way to go to the network when you open up the file view? ... that's partly what led me to believe it wasn't useable with a network, and so I had to mount the drives before use, rather than access them at the point of trying to save my latest artwork!


[/I]

---

### Post by chewearn on 2010-01-27
I am sorry to read about your tough experience setting up samba shares.  For future reference, I suggest install "system-config-samba".  It's a GUI which could do what you wanted.  And there is no need for edit fstab, add mount commands to startup list, etc.

---

### Post by isonomia on 2010-01-28
> **chewearn said:**
> I am sorry to read about your tough experience setting up samba shares.  For future reference, I suggest install "system-config-samba".  It's a GUI which could do what you wanted.  And there is no need for edit fstab, add mount commands to startup list, etc.

thanks!

**WHILST STILL NOT PERFECT** 
(I NOW GET TWO LOTS OF ICONS RATHER THAN A SINGLE ICON WHICH CHANGES WHEN CONNECTED)

What I did (for all the rest like me):

I right clicked on the decktop, selecte "create launcher", typed in the name of the drive (it doesn't matter what you call, same for the comment" and the command was:-

smb://fsg/family/

or

smb://user@fsg/family

Where fsg is the network computer unit name, and family is the - 'thing' on it, and user is your username on the drive.

The icon is bog awful so I used /usr/share/icons/humanity/places/48/folder.svg.

**N.B. whilst gimp works, the disks configured this way do not work with firefox ftp, nor do they work with either of the other ftp applications. However I did manage to connect and transfer something using ftp as a prefix.**

---

