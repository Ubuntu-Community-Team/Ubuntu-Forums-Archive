---
title: "log in lubuntu"
date: 2017-02-17
forum: Installation &amp; Upgrades
---

### Post by oneleded on 2017-02-17
i got lubuntu 16.04, on 2nd hard drive. i log out when i'm done.. when i access it again, i dont have to log in.   Grub lets me have a choice, to let 2nd drive go first. that is not the problem. I want the log-in password function restored, for lubuntu. that way, when the kid's get by my PC, they cant access it. kid's dont know enough to scroll down till you get to XP-1st hard drive, then push enter. How do i restore the password sigh-in for lubuntu? I want to make the sign-in necessary for lubuntu, to open.  //Ed

---

### Post by howefield on 2017-02-18
Have you looked in System Settings > User accounts ?

---

### Post by oneleded on 2017-02-18
i have not. i'll give it a try.  //Ed   1 day later. i cant seem to find system settings, or even settings. i have been to settings before. what am i doing wrong?  //Ed

---

### Post by oneleded on 2017-03-01
> **howefield said:**
> Have you looked in System Settings > User accounts ?

took words to literal. went to system tools/users and groups, i finally might be in the right place. tried to change password with no luck. maybe i should check the administrator account box. right now im not. i'll get back to you in a minute i forgot the other words. a stroke thing  //Ed   OK im back. i have a custom user account. i can check administrator account, or desktop user account in settings.  i have been using a three digit password to keep kids off the PC.  even being a custom user i can download programs, updates, and apply.   other than custom user being the problem, i cant think of anything else that might cause problem[of not having to log in],  except a download i did.  //Ed

---

### Post by oneleded on 2017-03-03
1st.. as far as user goes,, should i be custom, administrator, or desktop user? now im custom. i just cant change password.  2nd.. two part question; if i change to administrator, then change pass word,,should i go back to custom?, and/or can i?   im the only one that uses the 2nd HD with lubuntu, 3rd.. if im in the wrong forum, please say so,  to me, i just installed lubuntu, a bit ago. it is 16.04. i upgraded months ago from 14.04.   thanks,  //Ed

---

### Post by oneleded on 2017-03-10
> **howefield said:**
> Have you looked in System Settings > User accounts ?

i did, plus many other things. bottom line is i tried to uninstall and reinstall  lubuntu on the second hard drive. grub2 does not work the same with bad install, though i still can boot xp on 1st HD.  if i wipe second hard drive that has non-working lubuntu, will grub be a problem on first hard drive XP?  i cant believe first HD was not wiped out with my mistakes. i want to save 1st HD it if i can. i can use windows to wipe second HD and start over, if grub2 is not a problem.   in the meantime, i best do what i can with XP while it still works. the problem seemed to be[superblock last mount time is in the future, superblock last write time is in the future]., i have been having trouble with time between HD's, this is something else...     //Ed
[additional];  xp is working better. it's on the 1st HD. some sort of unintended side effect..
 i have to rewrite this, for those of you who have not banned me[ more or less], i appreciate your patience.  //Ed

---

### Post by oneleded on 2017-03-18
i reformatted sdb1 and reinstalled 14.04 LTS. it was the only solution i could come up with. problem was resolved, i will mark this solved though  //Ed

---

### Post by mörgæs on 2017-03-18
Yes, please do if you consider this a solution. Be aware that Lubuntu 14.04 only has a month of support left, though.

---

### Post by oneleded on 2017-03-18
i am going to 16.04 LTS one way or another. 14.04lts said i could upgrade to 16.04 lts. some how i ended with 16.10. dont know how that happened. i appreciate your comment, thanks   //Ed

---

### Post by howefield on 2017-03-18
> **oneleded said:**
> .... some how i ended with 16.10. dont know how that happened. i appreciate your comment, thanks   //Ed

The default setting seems to be to advise of any new version.. so 16.10 being the newest means that is what you got. Opening the Software & Updates application and changing that setting to "For Long term supprt versions" would probably have gotten you 16.04

[ATTACH=CONFIG]274205[/ATTACH]

16.10 being supported till July this year means that you will be prompted to upgrade to 17.04 once it is ready for upgrade.

---

### Post by oneleded on 2017-03-21
just what i needed. thanks  //Ed

---

### Post by oneleded on 2017-03-26
> **howefield said:**
> The default setting seems to be to advise of any new version.. so 16.10 being the newest means that is what you got. Opening the Software & Updates application and changing that setting to "For Long term supprt versions" would probably have gotten you 16.04

[ATTACH=CONFIG]274205[/ATTACH]

16.10 being supported till July this year means that you will be prompted to upgrade to 17.04 once it is ready for upgrade. 
that is where i got hung up. if it had said only be able to get LTS version's. i could have understood better. [my language barrier]. if i might,, should the default settings be OK when downloading updates. for instance, main, universe, and multiverse? some are way different as far as effects go of downloading, and i was not sure if i should leave things alone, or protect myself from accepting downloads that might not be OK. if they are OK, i have to restore settings back to where i started. i dont remember what they were exactly.  //Ed

---

### Post by howefield on 2017-03-26
The settings in the image are the default settings which is probably what you would want.

Being on 16.10 you probably would want to be notified of the next release which will be soon after 17.04 is released on April 13th. Once you get back to an LTS release, the next one being 18.04 you may choose to change it to stay on LTS.

---

### Post by oneleded on 2017-03-28
i went back to 14.04 lTS so i could upgrade to 16.04LTS. i could not upgrade from 14.04 LTS because i was missing a file or two. i watched the log download, but, it went faster that i could write anything on paper. 1 line that was missing i needed was [>=1.01ubuntu2.13].. just to get that, is the command line,, [sudo apt-get >=1.01lubuntu2.13]?.. i am also trying to figure out how to access log files, so i can do see the mistakes. i have seen how to do it before, i just dont remember where. my download of lubuntu 16.04 didnt take to well. the check-sum worked out but buning the iso to disk, not so much. probable the same when i burned 14.04.. i used free burncdcc to burn iso., and may have not used the right speed. next time i get to town i will try a download from the library internet. it runs much faster that the satellite we got in the boonies, so to speak..  April, 13 is not that far away. i will go to a better download site, and start over from there. i do appreciate your help, and still dont know if i got anything truly solved as yet. //Ed

---

### Post by howefield on 2017-03-29
> **oneleded said:**
> .. i am also trying to figure out how to access log files, so i can do see the mistakes. i have seen how to do it before, i just dont remember where. 

There is a log viewer included by default in Ubuntu, not sure if it is also present in Lubuntu. In any event the logs can be found in.. 

```
/var/log/
```

They are for the most part text files that will load into your default text editor when double clicked on.

---

### Post by oneleded on 2017-04-04
/var/log/ said it was a directory. maybe i need the space behind the slash...  / var/ log/   ...   also, i haven't used double click in a while, due to windows/logitech settings. is it 2 right clicks on the mouse? my setting on mouse are use single click.  //Ed

---

### Post by howefield on 2017-04-05
> **oneleded said:**
> /var/log/ said it was a directory. maybe i need the space behind the slash...  / var/ log/   ...   also, i haven't used double click in a while, due to windows/logitech settings. is it 2 right clicks on the mouse? my setting on mouse are use single click.  //Ed

That's correct.. /var/log/ is a directory, the various log files are inside it.

---

### Post by oneleded on 2017-04-22
i could not figure out how to open the../var/log/ directory. i tried many commands i found on line, most, near all, came from this site. in the long
run, i am going to get the latest LTS download.   when 14.04 did try to down load, it said 14.04 was corrupt. maybe i could have downloaded from 16.04, when it was there, an still got the new version, LTS. i got yet how to get past; its a directory(14.04), as far as commands go, i got a long way to go. Appreciate the help.  //Ed

---

### Post by howefield on 2017-04-23
> **oneleded said:**
> i could not figure out how to open the../var/log/ directory.

Well if you were using the terminal..

```
cd /var/log/
```

and ls to list the files contained within, eg

```
hugh@zesty:~$ cd /var/log/
hugh@zesty:/var/log$ ls
alternatives.log  apt         bootstrap.log  dpkg.log        gpu-manager.log  kern.log.1         syslog.1
apport.log        auth.log    btmp           faillog         hp               lastlog            syslog.2.gz
apport.log.1      auth.log.1  cups           fontconfig.log  installer        speech-dispatcher  syslog.3.gz
apport.log.2.gz   boot.log    dist-upgrade   gdm3            kern.log         syslog             wtmp
```

> i tried many commands i found on line, most, near all, came from this site. in the long run, i am going to get the latest LTS download.   when 14.04 did try to down load, it said 14.04 was corrupt. maybe i could have downloaded from 16.04, when it was there, an still got the new version, LTS. i got yet how to get past; its a directory(14.04), as far as commands go, i got a long way to go. Appreciate the help.  //Ed

I'm not sure what you are asking here, but if you use the torrent links to download your iso image there is a better chance of a successful download.

From here : [http://releases.ubuntu.com/xenial/](http://releases.ubuntu.com/xenial/)

click on the torrent link ubuntu-16.04.2-desktop-amd64.iso.torrent (assuming that it is 64 version wanted) and then double click on the downloaded file which should open up the Transmission torrent client, if it is the first time of using Transmission you will get an agreement dialogue box to accept, then a torrent details window, press the Open button and after a few seconds the download should start.

---

### Post by oneleded on 2017-04-30
sorry for a round about way of asking a question... i wanted to see why 14.04LTS failed to download 16.04LTS.. its in the log somewhere.. in the meantime, i should be able to download 17.04, an add it on 2nd hard drive. i will add a partition, for it,  so i can still study 14.04 logs to determine why previous update was a failure, an be able to use 17.04 on different partition. hopefully grub2 will still work, and let me chose, between 14.04, an 17.04 in the meantime, on linux 2nd hard drive. 1st HD is windows.

---

### Post by mörgæs on 2017-05-01
Why do you keep the obsolete Lubuntu 14.04? 
I would guess that Windows and 17.04 should be enough.

---

### Post by howefield on 2017-05-01
> **oneleded said:**
> i wanted to see why 14.04LTS failed to download 16.04LTS.. its in the log somewhere..

If there is an issue, attempting the upgrade from the terminal would probably give you the failure feedback without having to search the logs. To be honest, I'd just download 16.04.2 and install it clean.

> in the meantime, i should be able to download 17.04, an add it on 2nd hard drive. i will add a partition, for it,  so i can still study 14.04 logs to determine why previous update was a failure, an be able to use 17.04 on different partition. hopefully grub2 will still work, and let me chose, between 14.04, an 17.04 in the meantime, on linux 2nd hard drive. 1st HD is windows.

Yep, should work :)

---

### Post by oneleded on 2017-05-26
i just want to study it.   windows and 17.04 is plenty.  my attempt at upgrading 14.04 failed. i thought i might be able to learn why. i am a hard study though. only the school of hard knocks works.  //Ed

i did download torrent 17.04.  plus i tried the commands you gave me.  i am still studying 14.04, for my previous upgrade problems. i found a site,, [linux basics - manuals, UCR.edu,, institute for integrative genome biology], it has much linux info., which i like, lots of info, it says though, i need to use terminal to log into the remote linux shell. if it is true, or not, i still gots lot more research. 
What i was asking was to be able to view the upgrade failed log of 14.04. i should just use 17.04, and forget it.  i have to know how and why, of things. //Ed

i am using burncdcc to burn dvd-r. it has worked before. i got dvd-r, dvd+r disks.  i have also seen on some sites where recommended speed is 16X.  i may have the wrong disk, or free burner.  //Ed

---

### Post by oneleded on 2017-12-17
> **mörgæs said:**
> Why do you keep the obsolete Lubuntu 14.04? 
I would guess that Windows and 17.04 should be enough.

keeping 14.04, was a waste of time. i should have listened. just now replying, i did play around a bit with it. didnt learn nothing. thanks:redface:

---

### Post by oneleded on 2017-12-17
> **oneleded said:**
> /var/log/ said it was a directory. maybe i need the space behind the slash...  / var/ log/   ...   also, i haven't used double click in a while, due to windows/logitech settings. is it 2 right clicks on the mouse? my setting on mouse are use single click.  //Ed

windows settings dont have anything to do with linux settings. that is probably where i failed.oh well.. i did download 16.04 LTS twice at different speeds, even with checksum OK, they would not take. soo, i put 17.10 on the disk, updated to latest LTS version, and got 16.04 LTS. not the correct way to do it, but it worked for me. thanks for your help.  //Ed

---

