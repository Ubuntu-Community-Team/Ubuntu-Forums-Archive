---
title: "Update Manager will not install 3 updates"
date: 2015-02-04
forum: Installation &amp; Upgrades
---

### Post by Bill Dubinski on 2015-02-04
Good Day, 
Been using Ubuntu 5 or so years now. I try to solve my own issues, but this one has not been addressed yet atleast not in Ubuntu 12.04. Who knows, it may be they way I Googled the issue, who knows. 

I think this is the correct location for this question, if not, mods please help to move to correct. But my issue is "updates" versus "upgrades". But to some, the term can be interchangable. 

Here is my issue. I am running 12.04 Precise  A couple weeks ago the update manager opened up. I selected to install updates. 
Here were/are the four updates. 

Both groups of Two of which "seem" to be the same update. 3k in size and both are a new Kernel and as per the "description of the update" for 2 of 4 say in "Changes for the version" section of update manager:
Installed version: 3.13.0.43.37
Available version: 3.13.0.45.39

Version 3.13.0.45.39: 

And the last update

The other 2 of 4 seem to be duplicates also and read. "Mesa Off- screen rendering extension" and read in "Changes for the version" section of update manager: Changes for the versions:
Installed version: 8.0.4-0ubuntu0.7
Available version: 9.2.0~git20131002+9.2.2eb55601-0ubuntu0sarvatt~precise

This update does not come from a source that supports changelogs.

Since that day I "tried" to install these 4 updates, now everytime the updats manager opens and closes, this box pops up that says, "NOT ALL UPDATES CAN BE INSTALLED" and goes on to say, "Run a partial upgrade, to install as many updates as possible. "This could be caused by: 
A previous update that did not complete (but does not tell you which one, fix it or do anything to lead you in a direction to fix it)
Problems with some of the installed software (but does not tell you what software so it can be fixed)
Unofficial software packages not provided by Ubuntu
Normal changes of a pre released version of Ubuntu. 

Then via buttons, asks me to "Patrial upgrade" or close. 

This "Partial upgrade" is another thing that makes me feel uncomfortable. "Upgrade"? Nobody asked for an "upgrade" and what will happen if I press it? The upgrade I think it means is doing something I did not ask and that likely will be "upgrading" to 14.04 which I do not want that. Ubuntu still has not worked the bugs out of 12.04 yet, why do I want new problems? 

This dumb box pops up upon opening the update manager and after updates are done and does not allow me to select, install or anything on those updates. They are just sitting there wasting space and annoying me with that error box because it pops up and does not leave your vision until you stop what your reading to exit out of it unlike the update box its self.  

1/4 of me wants to "upgrade" to 14.04, but two reasons, defeats the purpose of a LTS release that is still not at EOL yet. And 14.04 is still in Beta 1 and I do not use OS's in Beta, too many issues. I do not "upgrade" atleast until Beta 2 or when EOL happens. 

So I would like to fix this issue. Today, I did receive a Kernal update just before typing this. This Kernel (today) was a different Kernel then the two already in the manager and was "selectable" to be installed. However, it did not "seem" to have installed because the system did not ask for a restart and my power button is not/has not turned red indicating a restart needed. 
So this is why I don't "think" it actually installed, but the 4 (unselectable) ones still show upin the update manager. 

This issue does not go away when I change the servers from U.S. to main except for the two "Mesa Off- screen" updates go away when switching to main but come back after switching back to U.S. 

Hwo do I either install these, get rid of these from the manager and or resolve this issue?

The currect kernel I am running is Kernel Linux 3.13.0-43-generic (as per System Monitor)

Thank you in advance for your time. 

Bill[ATTACH=CONFIG]259714[/ATTACH][ATTACH=CONFIG]259715[/ATTACH][ATTACH=CONFIG]259716[/ATTACH][ATTACH=CONFIG]259717[/ATTACH]

---

### Post by deadflowr on 2015-02-04
You have the xorg-edgers ppa, and they don't usually produce a changelog. Normal per any ppa.

A partial Upgrade is not a release upgrade, but rather something did not or can not be install normally on the current system, so the system needs to do something beyond a normal update.

You CAN actually click on that partial upgrade button and then it'll go through a few steps first, and you will end on a page with a Details dropdown button.
(You need to look in the main window area of this page for the Details button/dropdown.
This page is where you would actually start the partial upgrade, but first you can look over what packages are going to be installed, removed or upgraded.
This page to start the upgrade should list stuff up top like how much will be downloaded and how long it should take. 
You can still cancel the partial upgrade on this page, as well.

The key is to look over what the Details tells you.
see what will be installed, what will be removed and what will be upgraded.
If you are unsure about what it means toggle the dropdowns and take a screenie.

EDIT: I should point out that when you first click on the partial upgrade option it'll ask for your password and then open a window that looks has a few entries and a strobe-like bar moving from side to side.
Do not worry about that, it's only probing/setting up your packages and the network connection, nothing is being downloaded or installed.
When it finishes, that'll be when the Details page will show.
(I didn't want you to think that when that strobe-bar window opens, the upgrade is started. So don't worry, it will not.)

Hope some of this helps.

---

### Post by Bill Dubinski on 2015-02-04
Thank you so very much for your time and reply. 

I will work right now and perform the tasks you advised. 

Thank you for "explaining" the meaning of "partial updrade". I have wondered that since running 10.04 (Lucid) where I wish I was still running that OS and had the same issue with 10.04 just before switching to 12.04 well after 10.04's EOL. 

Again, thank you so much and I will get back when finished either way the outcome is and "solve" the thread if worked. Give me a little bit. Thanks.

---

### Post by Bill Dubinski on 2015-02-04
Okay, I did what you advised, and I do have some progress and some new developments. 

Screenshots are enclosed but I will explain also. 

The two Kernel updates were either removed or installed after hitting "Partial upgrade". 

In that process, it did acknowledge the Mesa Off-screen dependency and advised me it was not needed and was supposed to be removed. 

It  asked for a restart, completed the restart and upon bring the system  back up, opening update manager, noticed Mesa off screen dependency was  still there but only one this time and NOT the second. It still won't  let me do anything with it. Meaning click-on-able but not tick-able. 

So  it did away with 2 of 2 kernal updates, but only one of the Mesa off  screen updates. (Sorry, title says 3 updates, there was 4. Title typo)
 
the  new thing is since then, I am now getting a dialog box upon opening  update manager that says "Failed to download repository information"  Please check your internet connection. 

Then after I closed that  box out, hit "check" it downloads them fine and there was a handful of  updates that came in just after the initial restart from the initial  updates or "partial upgrade" process. 
I have seen that "check  internet connection" (which I know is a lie) when I ran 10.04 and to fix  that I switched from the main server to the U.S. server and cleared  that up. Just now in 12.04 that did not fix that issue, plus it is on  U.S. server anyways, but tried anyways. 

Also the update manager is not giving me an option for another "partial upgrade", thinking maybe to run it again, maybe it did not address all problems on the first try. 
Any advise? 

Thanks again in advance.

---

### Post by Bill Dubinski on 2015-02-06
Mods, Is it okay to bump a thread if if has not been solved or replied upon?

---

### Post by ian-weisser on 2015-02-06
I don't understand your description of the current problem.
Would you be willing to do an apt-get update and apt-get upgrade using the shell, so we can see useful output, complete with error messages in context?

---

### Post by deadflowr on 2015-02-06
> **Bill Dubinski said:**
> Mods, Is it okay to bump a thread if if has not been solved or replied upon?
Yes, perfectly fine to bump a thread, every so often. Not too often, but you can(are allowed) to bump threads every few hours, if need be. (We take into consideration that the users who might best help you may not be online when you first post, and your thread may dropdown the page, where it would go under-noticed)
> **ian-weisser said:**
> I don't understand your description of the current problem.
Would you be willing to do an apt-get update and apt-get upgrade using the shell, so we can see useful output, complete with error messages in context?

+1
I would also stop short of installing the upgrades and simply copy and paste the output here (use code tags, please)
(you need to select y/n anyway, when applying the updates so no need to worry that running the upgrade command will actually start it)

---

### Post by Bill Dubinski on 2015-06-25
Out put of apt-get update:

```
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1) dists/precise/restricted/binary-i386/ Release
Err cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1) dists/precise/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1) dists/precise/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1) dists/precise/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1) dists/precise/restricted/binary-i386/ Translation-en
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release.gpg [198 B]        
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [196 kB]            
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Get:4 [http://repository.spotify.com](http://repository.spotify.com) stable Release.gpg [819 B]                 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg                               
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric Release.gpg                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise Release                                   
Get:5 [http://repository.spotify.com](http://repository.spotify.com) stable Release [2,419 B]                   
Err [http://repository.spotify.com](http://repository.spotify.com) stable Release                               
  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages                        
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                     
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main amd64 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release [54.3 kB]          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main i386 Packages                      
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main TranslationIndex                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [490 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,981 B]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [120 kB]   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [9,730 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [908 kB]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en_US                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en                       
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [13.6 kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [267 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [16.5 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [959 kB]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Get:16 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex [370 B] 
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex            
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main Translation-en_US                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [13.6 kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [276 kB]
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main Translation-en                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [16.7 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Sources [130 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted Sources [3,759 B]
Get:22 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex [359 B] 
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex            
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe Sources [43.0 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse Sources [2,186 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main amd64 Packages [525 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted amd64 Packages [8,943 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe amd64 Packages [123 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse amd64 Packages [2,689 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main i386 Packages [566 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted i386 Packages [8,939 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe i386 Packages [131 kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse i386 Packages [2,876 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe TranslationIndex    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe Translation-en      
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                   
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Fetched 4,896 kB in 4s (997 kB/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 13B00F1FD2C19886

W: Failed to fetch cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://repository.spotify.com/dists/stable/Release](http://repository.spotify.com/dists/stable/Release)  

W: Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.
```



The out put of apt-get upgrade:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libosmesa6:i386
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

---

### Post by deadflowr on 2015-06-25
So you have several parts that need to be disabled in your sources.

First you will have to disable the cdrom source.
Second disable thew spotify ppa.
Third, disable the canon ppa.

All of these can be disabled in the software sources, whichcan be opened by pressing the "Settings" button in the update manager.
I believe they can all be unchecked to disable in the tab/section marked "Other Software"
(Though, the cdrom source might be in the other tab marked Ubuntu software, cannot remember off the top of my head)

 Now you should be able to fix the canon ppa by changing to either of these
[https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk](https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk)
[https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-stable](https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-stable)
The current ppa you have for canon drivers did not get updated to precise, while these others are.
(Personally I would go with the stable ppa, over the daily ppa)

Unfortunately I do not know what the status is for spotify, as I have seen over time several instances of it's ppa breaking...

---

