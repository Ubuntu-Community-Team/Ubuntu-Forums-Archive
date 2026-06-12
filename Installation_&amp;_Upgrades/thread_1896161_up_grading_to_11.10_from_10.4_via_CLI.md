---
title: "up grading to 11.10 from 10.4 via CLI???"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by beanco on 2011-12-16
So, I have a new laptop from work... an HP ProBook 4330s.

the IT guys were nice enough to copy all the stuff off the old laptop. They did not have time to upgrade.

there are some problems, most annoying of which is I cannot connect to our Novell network and sys-op says to upgrade ot the newest Ubuntu then he can help me....

so, whats the fastest, safest way to do it form the CL?

I'd like to do it ASAP.

Thanks....

Robi

---

### Post by SlugSlug on 2011-12-16
sudo vi /etc/update-manager/release-upgrades


change prompt=lts
to prompt=normal

sudo apt-get update && sudo do-release-upgrade

---

### Post by beanco on 2011-12-16
Hey Slug Slug,


Thanks... but where can I change prompts....?

robi

---

### Post by SlugSlug on 2011-12-16
> **beanco said:**
> Hey Slug Slug,


Thanks... but where can I change prompts....?

robi


when you edit  /etc/update-manager/release-upgrades


you will see that line to edit

you maybe better trying

sudo nano  /etc/update-manager/release-upgrades

as vi can be tricky

---

### Post by beanco on 2011-12-16
What's the difference between the two?


Thanks


Rob

---

### Post by SlugSlug on 2011-12-17
I use vi, but thats just because it was the first cli text editor I was show,
nano is meant to be easier as it more gedit like where as vi has 2 modes, a moving around text mode and a editing mode, 

have a play?

nano /tmp/tmpfilenano

vi /tmp/tmpfilevi

---

### Post by matt_symes on 2011-12-17
Hi

Ouch. Vi (or emacs) is a bit of a learning curve for someone that has never used them just to change a single line in a file. Nano or gedit are better choices.

Might i suggest a sed command instead ?

```
sudo sed -i 's/Prompt=lts/Prompt=normal/g' /etc/update-manager/release-upgrades
```Kind regards

---

### Post by SlugSlug on 2011-12-17
> **matt_symes said:**
> Hi

Ouch. Vi (or emacs) is a bit of a learning curve for someone that has never used them just to change a single line in a file. Nano or gedit are better choices.

Might i suggest a sed command instead ?

```
sudo sed -i 's/Prompt=lts/Prompt=normal/g' /etc/update-manager/release-upgrades
```Kind regards

seds the way to go but all the slashs makes my head hurt

---

### Post by beanco on 2011-12-17
I have said it before and I will say it again... one of the reasons I love using Linux and in particular Ubuntu is the feeling of freedom I get by being able to change, alter, things to my liking.... the choices are left in my hands.. and the folks here on this forum are more helpful than anywhere else..

Slug Slug, I will try the editors later on... 

Gedit, I have used...

Matt, I have no idea what SED means, but I may try that if it is the easiest way... that is enough for me for now..  

robi

---

### Post by beanco on 2011-12-17
I am a noob and I cannot get anything done.

I guess I need more help ...

so, guys, if you do not mind... give me a play by play on how to do this...

any of the methods listed are fine. I have tried all but failed.. I really am a Noob!

Robi

---

### Post by matt_symes on 2011-12-17
Hi

SED is the stream editor. It let's you edit character streams, one such stream being from a file. It allows you to change files.

Copy and paste (or type - but copy and paste is safer) into a terminal
[FONT=monospace]
[/FONT]```
sudo sed -i 's/Prompt=lts/Prompt=normal/g' /etc/update-manager/release-upgrades
```

Enter your password. It will not be echoed to the screen. 

This will change the file for you.

Then copy and paste (as SlugSlug suggested)

```
sudo apt-get update && sudo do-release-upgrade
```

Then put the kettle on as it may take a while :)

Can i also recommend backing up your hard drive first by either making an image or tarring your files.

Kind regards

---

### Post by beanco on 2011-12-17
Sorry what  meant to say is.... that it already says prompt=normal


so I did this: rob@rob-laptop:~$ sudo apt-get update && sudo do-release-upgrade

And got this:```

Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release.gpg
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/ karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/ karmic/restricted Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                       
Get:1 http://dl.google.com stable Release.gpg [198B]                 
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://archive.ubuntu.com lucid Release.gpg                                
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US   
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Ign http://ppa.launchpad.net/glasen/intel-driver/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg 
Ign http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/ lucid/main Translation-en_US
Get:2 http://dl.google.com stable Release.gpg [198B]                 
Hit http://ppa.launchpad.net lucid Release                                     
Ign http://dl.google.com/linux/earth/deb/ stable/main Translation-en_US        
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US         
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US       
Hit http://archive.ubuntu.com lucid-updates Release.gpg                        
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US     
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US 
Get:3 http://dl.google.com stable Release [1,347B]                             
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.canonical.com lucid Release                                 
Hit http://archive.ubuntu.com lucid-security Release.gpg                       
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Get:4 http://dl.google.com stable Release [1,338B]                             
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid Release                          
Hit http://archive.ubuntu.com lucid-updates Release                            
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://archive.ubuntu.com lucid-security Release                           
Get:5 http://dl.google.com stable/main Packages [1,214B]                       
Hit http://archive.canonical.com lucid/partner Sources                         
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://archive.ubuntu.com lucid/main Packages                    
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/universe Sources
Get:6 http://dl.google.com stable/main Packages [464B]
Hit http://archive.ubuntu.com lucid/multiverse Packages
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/restricted Sources
Hit http://archive.ubuntu.com lucid-security/universe Packages
Hit http://archive.ubuntu.com lucid-security/universe Sources
Hit http://archive.ubuntu.com lucid-security/multiverse Packages
Hit http://archive.ubuntu.com lucid-security/multiverse Sources
Fetched 4,759B in 1s (2,843B/s)
W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.



```

not sure why, but that's what I got....

Robi

---

### Post by matt_symes on 2011-12-17
Hi

It's looking the CD disc for Karmic. Another quick command will disable that for you.

From the terminal...

```
sudo sed -i 's/deb cdrom/#deb cdrom/g' /etc/apt/sources.list
```then 

```
sudo apt-get update && sudo do-release-upgrade
```Kind regards

---

### Post by beanco on 2011-12-17
well, now I am not 10.10 Meerkat.... nice step up, just have to keep on plugging at it...

---

### Post by matt_symes on 2011-12-18
Hi 

> **beanco said:**
> well, now I am not 10.10 Meerkat.... nice step up, just have to keep on plugging at it...

Keep chugging at it an let us know how you get on.

Kind regards

---

### Post by beanco on 2011-12-18
> **matt_symes said:**
> Hi 



Keep chugging at it an let us know how you get on.

Kind regards

things are not so good after all.... I had been at a party while Meerkat was downloading, came in, saw it was no longer loading, or at least it seemed so...

posted here, turned off the computer went to bed.


got up and tried to fire it up... well I get an error message.

Gnome Power Management not properly installed . See Systems administrator or sg like that...

I cannot get past that... 

no idea what happened or what I should do....

robi

---

### Post by beanco on 2011-12-18
looking roudn the forums I found info on this error.. seems like I have likely run out space...


so, the question is how do i get into  HDD to delete stuff and then try reinstalling Meerkat?

Thanks

Robi

---

### Post by matt_symes on 2011-12-18
Hi

Try booting into a root console You can check the space on the mounted partitions there with

```
df -h
```and 

```
du -s
```You can also delete files from that console.

If you can't boot into a root console then try a LiveCD/USB and remove files that way.

Kind regards

---

### Post by beanco on 2011-12-19
I ended up going into MC.. it just occured to me afte a good night's sleep and I was able to delet stuff, make enough room...

Then at work the sys-op helped and all is working now... sort of....

there are some keyboard layout problems... but i will start a new thread for that....

thanks everybody for the help....

---

