---
title: "Ubuntu in, xp lost!"
date: 2004-12-21
forum: Installation &amp; Upgrades
---

### Post by fiddler on 2004-12-21
Hey guys,,
                 Ok, yesterday I installed ubuntu, so far so good.! Everything seemed to go just fine, In fact it went great, insofar as I was on the internet with Linux, woohoo!!!
                  This is a big deal for me, because although I dabbled with Linux  a couple of years ago,( Mandrake ,Redmond) I could never access the net, so that put an end to my Linux experience for a while.
                    Anyway, here I was, surfing away like a wild thing! 
                   So I decided to reboot and go into xp.........that's  when it all went pearshaped! Computer rebooted, up came grub, showing both of my xp partitions, I chose the first on the list and pressed the button........zap.......fatal error, computer has been shut down, eek! So I rebooted and chose the second xp,......pc goes into the grub command line thingy and just stares at me, oh great !
                      I throw every recovery and repair disc I can get my hands on into the beast, all to no avail. So I end up reinstalling one of my instances of xp ( the one with no apps on, that I installed the other day) and lo and behold, I have both my xp's back ( and win ME which I havn't mentioned yet) but no ubuntu......
                    According to partition magic, I still have ubuntu on, but I can't access it! 
                       My disc setup is as follows:-
                primary master hdd0  120gb maxtor with xp on a 15gb partition
                  primary slave   cd player
                   secondary master  hdd1 80gb excelstor  with winME, xp and ubuntu plus data partitons
                     secondary slave   cdrw
               Can anyone help me to be able to boot all my os's ????
               I really want to persevere with Linux this time, so any help will be gratefully received.         Thanks guys  :p   ;)

---

### Post by az on 2004-12-21
Perhaps grub got your disks' geometry wrong.  You can specify it by hand...

---

### Post by Glycerine on 2004-12-21
[QUOTE=fiddler]Hey guys,,
                 Ok, yesterday I installed ubuntu, so far so good.! Everything seemed to go just fine, In fact it went great, insofar as I was on the internet with Linux, woohoo!!!
                  This is a big deal for me, because although I dabbled with Linux  a couple of years ago,( Mandrake ,Redmond) I could never access the net, so that put an end to my Linux experience for a while.
                    Anyway, here I was, surfing away like a wild thing! 
                   So I decided to reboot and go into xp.........that's  when it all went pearshaped! Computer rebooted, up came grub, showing both of my xp partitions, I chose the first on the list and pressed the button........zap.......fatal error, computer has been shut down, eek! So I rebooted and chose the second xp,......pc goes into the grub command line thingy and just stares at me, oh great !
                      I throw every recovery and repair disc I can get my hands on into the beast, all to no avail. So I end up reinstalling one of my instances of xp ( the one with no apps on, that I installed the other day) and lo and behold, I have both my xp's back ( and win ME which I havn't mentioned yet) but no ubuntu......
                    According to partition magic, I still have ubuntu on, but I can't access it! 
                       My disc setup is as follows:-
                primary master hdd0  120gb maxtor with xp on a 15gb partition
                  primary slave   cd player
                   secondary master  hdd1 80gb excelstor  with winME, xp and ubuntu plus data partitons
                     secondary slave   cdrw
               Can anyone help me to be able to boot all my os's ????
               I really want to persevere with Linux this time, so any help will be gratefully received.         Thanks guys  :p   ;)[/QUOTE]
 Had a similar problem   Apparantly it's a known issue, not of ubuntu, but grub? i think?  Quick search on the forums brought up my solution:  Set your HD to LBA in bios.  

Since you've already written over your MBR with the XP disks, you're going to have to redo your grub install.  I can't tell you the particulars on that.  However, if you haven't already set everything up in ubuntu, it might be easier just to boot your ubuntu disc and reinstall it again.  Just make sure LBA is set and you'll be ok.

---

### Post by fiddler on 2004-12-24
Thanks guys. Azz, I don't know enough to do it manually  
                      Glycerine, I have changed the bios from 'Auto' to LBA, but havn't done a reinstall of Ubuntu, yet. Will let you know how it goes !
                                Thanks again. 8)

---

### Post by fiddler on 2004-12-28
Hi guys,
             Well, I have reinstalled ubuntu, but no different :sad: 
                Everything goes well until I reboot, I still can't boot into either of my xp's.
              I also got confused during the install with the username and password setup, when I rebooted into ubuntu I had forgotten which was which. My fault I know, and nothing to do with ubuntu per se.
              Do I have to have a user name and password? I can easily do without them both!
               It seems like I'm just not ready for linux. But I suspect that I'm not the only one out there who feels the same . If linux wants to woo people away from windows, they are going to have to come up with something a lot more user friendly than what is currently available. Linux is going to have to lose its 'geeky' reputation I think.
                Considering the time and energy  expended by the thousands of linux developers, is it being unrealistic to expect a really easy install process, and a bootloader that is not buggy?
                  Anyway that's my moan of the day. I'm still open to any suggestions regarding the install . I'm going to persevere for a while longer at least =D>

---

### Post by alpha on 2004-12-28
[QUOTE=fiddler]Hi guys,
             Well, I have reinstalled ubuntu, but no different :sad: 
                Everything goes well until I reboot, I still can't boot into either of my xp's.
              I also got confused during the install with the username and password setup, when I rebooted into ubuntu I had forgotten which was which. My fault I know, and nothing to do with ubuntu per se.
              Do I have to have a user name and password? I can easily do without them both!
               It seems like I'm just not ready for linux. But I suspect that I'm not the only one out there who feels the same . If linux wants to woo people away from windows, they are going to have to come up with something a lot more user friendly than what is currently available. Linux is going to have to lose its 'geeky' reputation I think.
                Considering the time and energy  expended by the thousands of linux developers, is it being unrealistic to expect a really easy install process, and a bootloader that is not buggy?
                  Anyway that's my moan of the day. I'm still open to any suggestions regarding the install . I'm going to persevere for a while longer at least =D>[/QUOTE]
 Fiddler,

Why the defeatist attitude? I have seen this before, people have problems with Linux, then give up with an excuse blaming Linux because they are stumped on an issue.

I don't use Linux at the moment, but will be in the new year.

You should see this as a learning experience and not give up. Look at when windows 3.1 came out people had to adjust from using DOS for years.

---

### Post by fiddler on 2004-12-28
Hey  alpha, 
                   Yeah you're right ,it is showing a defeatist attitude, but I was quite frustrated, so put my feelings on air, so to speak. But as I said, I havn't given up on linux, yet, by a long shot. I am determined to get this blasted os up and running, if it kills me. There, that's not so defeatist now is it, lol?
                   Seriously, I have had linux dual or multi booting in the past ok, so it must be something I am doing wrong, it's just that.....ok, I've said all that. 
                 Anyway , I'll keep on trying.     Thanks for the pep talk. All taken in the right spirit! ;-)

---

### Post by alpha on 2004-12-28
[QUOTE=fiddler]Hey  alpha, 
                   Yeah you're right ,it is showing a defeatist attitude, but I was quite frustrated, so put my feelings on air, so to speak. But as I said, I havn't given up on linux, yet, by a long shot. I am determined to get this blasted os up and running, if it kills me. There, that's not so defeatist now is it, lol?
                   Seriously, I have had linux dual or multi booting in the past ok, so it must be something I am doing wrong, it's just that.....ok, I've said all that. 
                 Anyway , I'll keep on trying.     Thanks for the pep talk. All taken in the right spirit! ;-)[/QUOTE]

Glad you took it the right way. :)

---

### Post by jmike1 on 2004-12-29
What version of Partition Magic are you using? It is my understanding that you need at least version 8 to work with multiple installlations of XP. If you have more than one XP OS installed on your machine I remember reading that version 7 won't support that.

---

### Post by jmike1 on 2004-12-29
[QUOTE=alpha]Fiddler,

Why the defeatist attitude? I have seen this before, people have problems with Linux, then give up with an excuse blaming Linux because they are stumped on an issue.

I don't use Linux at the moment, but will be in the new year.

You should see this as a learning experience and not give up. Look at when windows 3.1 came out people had to adjust from using DOS for years.[/QUOTE]

Are you sure you are not being a little bit defensive at somebody making a valid criticism of what you consider to be "the coolest" OS? I've been wrestling with the problem of safely installing ubantu linux as a second OS on a dual-boot system for a couple of days now and just what I read on the Linux community websites is indicating to me that it is a very byzantine and risky process. 
I am currently going into my 3rd term as a grad student pursuing my masters in computer science. I have extensive experience programming in the UNIX environment, have installed solaris more than once and have installed numerous flavors of Windows OS's to dual-boot configurations. If I find linux installation difficult, how is average Joe User going to react to it? 
I think that Fiddler's points are well-taken.

---

### Post by ubuntu4everyone on 2004-12-29
You could just only have one OS (Ubuntu)
Or you could put  windows xp and linux on the same disk (but only one copy of XP) and use the other HD as swap and /home etc

---

### Post by fiddler on 2005-01-03
I am using Patition Magic v.8.......thanks for all the input guys  =D>

---

### Post by fiddler on 2005-01-03
Why only one copy of xp ?? :confused:

---

### Post by PeP on 2005-08-14
Why one copy of Xp only?
It is just an XP issue... But since there is only one XP why get two?

---

### Post by ArtLeo3703 on 2007-05-15
> **alpha said:**
> Fiddler,

Why the defeatist attitude? I have seen this before, people have problems with Linux, then give up with an excuse blaming Linux because they are stumped on an issue.

I don't use Linux at the moment, but will be in the new year.

You should see this as a learning experience and not give up. Look at when windows 3.1 came out people had to adjust from using DOS for years.


[Tsunami plants solar Credit Cards Debt Consolidation](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/latin-porn.html)

---

### Post by cuznecik6202 on 2007-05-15
> **Glycerine said:**
> Had a similar problem   Apparantly it's a known issue, not of ubuntu, but grub? i think?  Quick search on the forums brought up my solution:  Set your HD to LBA in bios.  

Since you've already written over your MBR with the XP disks, you're going to have to redo your grub install.  I can't tell you the particulars on that.  However, if you haven't already set everything up in ubuntu, it might be easier just to boot your ubuntu disc and reinstall it again.  Just make sure LBA is set and you'll be ok.


[weather Mortgages generator plants Equity Line Credit](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---

