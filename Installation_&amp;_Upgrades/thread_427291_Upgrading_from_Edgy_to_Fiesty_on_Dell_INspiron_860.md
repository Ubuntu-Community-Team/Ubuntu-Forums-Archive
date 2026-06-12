---
title: "Upgrading from Edgy to Fiesty on Dell INspiron 8600. Any help appreciated!"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by Cyphurnz on 2007-04-29
Hey Guys,

Terribly sorry for joining the mess but Im running a dell inspiron 8600. Previous debian user running Edgy with Beryl/ nvidia drivers etc no problems.

The laptops packed with university work and I have no way to access it other than recovery mode  for 2.6.17-10-generic kernel

I stupidly decided that I would risk clicking the upgrade managers UPDATE TO FIESTY button on my otherwise perfectly working lappy. THe installed completed successfully but on reboot to the new 2.6.20 kernel / fiesty the computer fails to boot.

Im assuming that its in realtion to the problems people are having with the 2.6.20-14 kernel however Im unable to update to 2.6.20-15 as people seem to suggest as when I run apt-get update It simply returns a pile of 302 errors.

As I understand a 302 is  http redirect but what I cant understand is why apt worked before the update, and now doesnt.

I am behind the Oxford unveristy firewall but previously it has had no effect on my ability to run apt

Any help regarding the fixing of Apt, suggestions on what to do once apt is running or failing any of that a simple suggestion of how I can do a clean reinstall with downloaded ubuntu cds without harming my home partition would be awesome.  

Other info that woudl be awesome would be a sources.list that someone knows works for them as I can start eliminating sources of my problems

---

### Post by Cyphurnz on 2007-04-29
hmm well as Im looking around I thought I might as well update incase anyone else has a similar problem that needs fixing.

[http://ubuntuforums.org/showthread.php?t=113219&page=2&highlight=plf](http://ubuntuforums.org/showthread.php?t=113219&page=2&highlight=plf)

seems to sugges tthat the 302 errors are comming because my apt source is a mirror. Why it doesnt like mirrors I have no idea. 

Tried changing from my original 

[http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) fiesty

to 

[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) fiesty 

but made no difference

also tried modifying it to look back at the old edgy version 
with 

[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy etc

however it still gives me a bunch of 302s

---

### Post by zvacet on 2007-04-29
Put all your repositories to feisty.No edgy repos in source list.Go to the system>administration>software properties and try to use main server.If still no luck back to your local server and in terminal type this


```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by Cyphurnz on 2007-04-29
Cheers for that info. 

i should have mentioned that the sources.list file was already full of references to fiesty as it should be after and upgrade. Thats when the 302 errors began. 

I changed to edgy just too see if the reference o fiesty was the problem.

On another note, when I say I had to drop to recovery kernel mode, that means X wont start.  So theres no using your pretty little package manegment programs and the like.

Also When I say Apt-get update returns 302 errors it means I cant update at all

---

### Post by Cyphurnz on 2007-04-29
I think you misunderstood the problem entirely. 

sudo aptitude update will do jack all other than return the same errors.

Does anyone have a sources.list file that uses the root servers as opposed to package mirrors?

---

