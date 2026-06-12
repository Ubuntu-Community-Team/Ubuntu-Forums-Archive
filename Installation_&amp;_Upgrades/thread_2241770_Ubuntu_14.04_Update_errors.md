---
title: "Ubuntu 14.04 Update errors"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by Allen Moretsky on 2014-08-28
Hi,
I'm running 14.04 on an HP G60 laptop. I'm having a bit of trouble with [B]apt-get update. 

[/B]Ultimately I'm hoping the update will fix my screen problem. 
I run an external monitor. The laptop shows the login screen until I login. After login on the laptop the laptop screen turns off which is correct. 
What should happen is that the login screen should display on the external monitor to begin with and then once logged in, the laptop screen should go blank.  

```
allen@allen-HP-G60-Notebook-PC:~$ sudo apt-get update
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise InRelease
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise Release.gpg
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise Release
Err cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/main Translation-en
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213) precise/restricted Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://mirror.umd.edu](http://mirror.umd.edu) trusty InRelease                                     
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://mirror.umd.edu](http://mirror.umd.edu) trusty-updates InRelease                             
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                          
Ign [http://mirror.umd.edu](http://mirror.umd.edu) trusty-security InRelease                  
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                   
Ign [http://mirror.umd.edu](http://mirror.umd.edu) trusty-backports InRelease                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                        
Hit [http://dl.google.com](http://dl.google.com) stable Release                              
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty Release.gpg                                   
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-updates Release.gpg                           
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                      
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-security Release.gpg                
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-backports Release.gpg                         
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty Release                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-updates Release                               
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-security Release                              
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-backports Release                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty/main i386 Packages                            
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty/universe i386 Packages                        
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty/multiverse i386 Packages                      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty/main Translation-en                           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty/multiverse Translation-en                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty/universe Translation-en                       
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-updates/main i386 Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages       
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty InRelease               
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-updates/universe i386 Packages                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-updates/multiverse i386 Packages              
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-updates/main Translation-en                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                  
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release.gpg                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-updates/multiverse Translation-en             
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                  
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-updates/universe Translation-en     
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-security/main i386 Packages         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-security/universe i386 Packages               
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-security/multiverse i386 Packages   
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-security/main Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-security/multiverse Translation-en  
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-security/universe Translation-en    
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-backports/universe i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-backports/main i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-backports/multiverse i386 Packages
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-backports/main Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-backports/multiverse Translation-en
Hit [http://mirror.umd.edu](http://mirror.umd.edu) trusty-backports/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
Ign [http://mirror.umd.edu](http://mirror.umd.edu) trusty/main Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) trusty/multiverse Translation-en_US
Ign [http://mirror.umd.edu](http://mirror.umd.edu) trusty/universe Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en
W: Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


E: Some index files failed to download. They have been ignored, or old ones used instead.
allen@allen-HP-G60-Notebook-PC:~$
```

---

### Post by slickymaster on 2014-08-28
Hi Allen Moretsky, welcome to the forums.

I've edited your post, adding code tags to it. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

As for your issue, you're trying to use the repositories on the CD you used to install Ubuntu but cannot access them (probably because the CD is not in the drive). So, what you have to do is to run the following in a terminal window:```
gksudo software-properties-gtk
```In the window that comes up you should be able to disable using the cdrom repositories by unchecking them in either the bottom of the "Ubuntu Software tab" or in the "Other software tab".

---

### Post by grahammechanical on 2014-08-28
Why would an update fix that monitor problem? If you are using a proprietary video driver then it will have a settings management utility. If you are using the open source video driver then System Settings has a Displays utility. There may be a setting there that will fix this.

---

### Post by Allen Moretsky on 2014-08-28
Hi,
I'm not loading from CD, but I seem to be getting a cdrom error message and it appears that my upgrade does not finish. 

The reason I suspect an upgrade to fix the video is that all was OK prior to my upgrade to 14.04. I've been hoping for a bug fix AND hoping that was what I was encountering. I wonder if there is backwards capability to the same laptop video drivers or is there some magic I can perform or is it that the upgrade does not finish? The upgrade seems to come from UMD's server, not a CD. Initially the bottom of the external monitor is scrambled, but that clears up after login. 

W: Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Bashing-om on 2014-08-28
Allen Moretsky; Hi !

Let us look.
> 
W: Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ 


Post back the output of terminal command:
```

cat -n /etc/apt/sources.list

```
will see if we can get to the bottom of this.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Allen Moretsky on 2014-08-28
Thanks so much for this help:

allen@allen-HP-G60-Notebook-PC:~$ **cat -n /etc/apt/sources.list**
     1	deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)]/ precise main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://mirror.umd.edu/ubuntu/](http://mirror.umd.edu/ubuntu/) trusty main
     6	
     7	## Major bug fix updates produced after the final release of the
     8	## distribution.
     9	deb [http://mirror.umd.edu/ubuntu/](http://mirror.umd.edu/ubuntu/) trusty-updates main
    10	
    11	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12	## team. Also, please note that software in universe WILL NOT receive any
    13	## review or updates from the Ubuntu security team.
    14	deb [http://mirror.umd.edu/ubuntu/](http://mirror.umd.edu/ubuntu/) trusty universe
    15	deb [http://mirror.umd.edu/ubuntu/](http://mirror.umd.edu/ubuntu/) trusty-updates universe
    16	
    17	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    18	## team, and may not be under a free licence. Please satisfy yourself as to 
    19	## your rights to use the software. Also, please note that software in 
    20	## multiverse WILL NOT receive any review or updates from the Ubuntu
    21	## security team.
    22	deb [http://mirror.umd.edu/ubuntu/](http://mirror.umd.edu/ubuntu/) trusty multiverse
    23	deb [http://mirror.umd.edu/ubuntu/](http://mirror.umd.edu/ubuntu/) trusty-updates multiverse
    24	
    25	## N.B. software from this repository may not have been tested as
    26	## extensively as that contained in the main release, although it includes
    27	## newer versions of some applications which may provide useful features.
    28	## Also, please note that software in backports WILL NOT receive any review
    29	## or updates from the Ubuntu security team.
    30	
    31	deb [http://mirror.umd.edu/ubuntu/](http://mirror.umd.edu/ubuntu/) trusty-security main
    32	deb [http://mirror.umd.edu/ubuntu/](http://mirror.umd.edu/ubuntu/) trusty-security universe
    33	deb [http://mirror.umd.edu/ubuntu/](http://mirror.umd.edu/ubuntu/) trusty-security multiverse
    34	
    35	## Uncomment the following two lines to add software from Canonical's
    36	## 'partner' repository.
    37	## This software is not part of Ubuntu, but is offered by Canonical and the
    38	## respective vendors as a service to Ubuntu users.
    39	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    40	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    41	
    42	## This software is not part of Ubuntu, but is offered by third-party
    43	## developers who want to ship their latest software.
    44	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    45	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    46	deb [http://mirror.umd.edu/ubuntu/](http://mirror.umd.edu/ubuntu/) trusty-backports universe main multiverse
allen@allen-HP-G60-Notebook-PC:~$

---

### Post by Bashing-om on 2014-08-28
Allen Moretsky; Hey ;

OK, in the file " /etc/apt/sources.list " comment out that 1st line - 1	deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)]/ precise main restricted -

Now see that the update runs clean.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by Allen Moretsky on 2014-09-01
Commenting out the first line of /etc/apt/sources.list fixed my problem with update. This file was directing the update to pull that update from CD. 

-Allen

---

### Post by Bashing-om on 2014-09-01
Allen Moretsky; Hey, hey ;

Pleased that you are over that little bump. So how now with the rest of the system ?

Setting fat smart and happy ?

[INDENT][INDENT][INDENT]the care and feeding of your ubuntu
[/INDENT][/INDENT][/INDENT]

---

### Post by Allen Moretsky on 2014-09-02
Thanks, Bashing-om, for asking about the rest of the system. 
I'll create a new entry for the video problem so if someone else has the same problem they can easily find the answer.
Allen

---

### Post by Bashing-om on 2014-09-02
Allen Moretsky; OK !

As this little matter is concluded;
Please mark this thread solved; 
aides others seeking the solution,
 helps keep the forum clean and 
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Sometimes I can help with graphics issues, I will look into your new thread.

[INDENT][INDENT][INDENT]press on
[/INDENT][/INDENT][/INDENT]

---

