---
title: "Can't upgrade to karmic RC - &quot;no new release found&quot;"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by humphreybc on 2009-10-24
Hi guys,

When I run update-manager -d as instructed, it doesn't tell me of any new releases available for upgrade.

When I run do-release-upgrade -d this is what it gives me:

```

benjamin@benjamin-laptop:~$ do-release-upgrade -d
Checking for a new ubuntu release
No new release found

```

Could you please help, as I'm keen to upgrade from Jaunty and test out the RC of Karmic.

Thanks!

EDIT:

I have all four software sources checked (updates, proposed, backports, security) and also the upgrades are set to "normal releases"

---

### Post by peakshysteria on 2009-10-24
Have you tried: System --> Administration --> Software Sources and changed **Download from** to another country than the default (Norway in my case) to the United States. Then once again I ran ALT + F2 --> update-manager -d est voila! :)

---

### Post by humphreybc on 2009-10-24
I changed it to the main server but that doesn't seem to make any difference....

---

### Post by jolx on 2009-10-24
> **humphreybc said:**
> the upgrades are set to "normal releases"

maybe the release candidate isn't a "normal release"

---

### Post by humphreybc on 2009-10-24
> **jolx said:**
> maybe the release candidate isn't a "normal release"

Well there are only three options for that field:

"Show new distribution releases:

Normal Releases
Long Term Support Releases only
Never"

---

### Post by jolx on 2009-10-24
okay maybe you have to wait until the final release

---

### Post by infinitejones on 2009-10-24
What happens when you do 
```
sudo aptitude update && sudo aptitude dist-upgrade
```

That won't upgrade you to Karmic, but it might show us if there's anything wrong with your repositories...

---

### Post by humphreybc on 2009-10-24
> **infinitejones said:**
> What happens when you do 
```
sudo aptitude update && sudo aptitude dist-upgrade
```

That won't upgrade you to Karmic, but it might show us if there's anything wrong with your repositories...

Seems to work fine. I'm behind a proxy, could that affect anything? (Everything is set up to use the proxy.)

```

enjamin@benjamin-laptop:~$ sudo aptitude update && sudo aptitude dist-upgrade
[sudo] password for benjamin: 
Writing extended state information... Done
Hit http://download.virtualbox.org jaunty Release.gpg
Get:1 http://dl.google.com stable Release.gpg [189B]                            
Ign http://download.virtualbox.org jaunty/non-free Translation-en_NZ            
Ign http://dl.google.com stable/main Translation-en_NZ                          
Hit http://download.virtualbox.org jaunty Release                               
Hit http://ppa.launchpad.net jaunty Release.gpg                                 
Hit http://archive.canonical.com jaunty Release.gpg                             
Get:2 http://dl.google.com stable Release [2540B]                               
Hit http://archive.ubuntu.com jaunty Release.gpg                                
Hit http://download.virtualbox.org jaunty/non-free Packages                     
Hit http://packages.medibuntu.org jaunty Release.gpg                            
Ign http://ppa.launchpad.net jaunty/main Translation-en_NZ                      
Ign http://archive.canonical.com jaunty/partner Translation-en_NZ               
Get:3 http://dl.google.com stable/main Packages [660B]                          
Ign http://archive.ubuntu.com jaunty/main Translation-en_NZ                     
Ign http://packages.medibuntu.org jaunty/free Translation-en_NZ                 
Hit http://ppa.launchpad.net jaunty Release                                     
Hit http://archive.canonical.com jaunty Release                                 
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_NZ               
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_NZ             
Hit http://ppa.launchpad.net jaunty/main Packages                               
Hit http://archive.canonical.com jaunty/partner Packages                        
Hit http://packages.medibuntu.org jaunty Release                     
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_NZ    
Hit http://ppa.launchpad.net jaunty/main Sources                                
Hit http://packages.medibuntu.org jaunty/free Packages                          
Ign http://archive.ubuntu.com jaunty/universe Translation-en_NZ
Hit http://packages.medibuntu.org jaunty/non-free Packages                      
Hit http://archive.ubuntu.com jaunty-updates Release.gpg                        
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_NZ
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_NZ
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_NZ
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_NZ
Hit http://archive.ubuntu.com jaunty-security Release.gpg    
Ign http://archive.ubuntu.com jaunty-security/main Translation-en_NZ
Ign http://archive.ubuntu.com jaunty-security/restricted Translation-en_NZ
Ign http://archive.ubuntu.com jaunty-security/multiverse Translation-en_NZ
Ign http://archive.ubuntu.com jaunty-security/universe Translation-en_NZ
Hit http://archive.ubuntu.com jaunty-proposed Release.gpg                       
Ign http://archive.ubuntu.com jaunty-proposed/restricted Translation-en_NZ      
Ign http://archive.ubuntu.com jaunty-proposed/main Translation-en_NZ            
Ign http://archive.ubuntu.com jaunty-proposed/multiverse Translation-en_NZ      
Ign http://archive.ubuntu.com jaunty-proposed/universe Translation-en_NZ        
Hit http://archive.ubuntu.com jaunty-backports Release.gpg                      
Ign http://archive.ubuntu.com jaunty-backports/restricted Translation-en_NZ     
Ign http://archive.ubuntu.com jaunty-backports/main Translation-en_NZ           
Ign http://archive.ubuntu.com jaunty-backports/multiverse Translation-en_NZ     
Ign http://archive.ubuntu.com jaunty-backports/universe Translation-en_NZ       
Hit http://archive.ubuntu.com jaunty Release                                    
Hit http://archive.ubuntu.com jaunty-updates Release                            
Hit http://archive.ubuntu.com jaunty-security Release                           
Hit http://archive.ubuntu.com jaunty-proposed Release                           
Hit http://archive.ubuntu.com jaunty-backports Release                          
Hit http://archive.ubuntu.com jaunty/main Packages                              
Hit http://archive.ubuntu.com jaunty/restricted Packages     
Hit http://archive.ubuntu.com jaunty/multiverse Packages     
Hit http://archive.ubuntu.com jaunty/main Sources            
Hit http://archive.ubuntu.com jaunty/universe Packages       
Hit http://archive.ubuntu.com jaunty/universe Sources        
Hit http://archive.ubuntu.com jaunty-updates/main Packages   
Hit http://archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://archive.ubuntu.com jaunty-updates/main Sources    
Hit http://archive.ubuntu.com jaunty-updates/universe Packages
Hit http://archive.ubuntu.com jaunty-updates/universe Sources
Hit http://archive.ubuntu.com jaunty-security/main Packages  
Hit http://archive.ubuntu.com jaunty-security/restricted Packages
Hit http://archive.ubuntu.com jaunty-security/multiverse Packages
Hit http://archive.ubuntu.com jaunty-security/main Sources   
Hit http://archive.ubuntu.com jaunty-security/universe Packages
Hit http://archive.ubuntu.com jaunty-security/universe Sources
Hit http://archive.ubuntu.com jaunty-proposed/restricted Packages
Hit http://archive.ubuntu.com jaunty-proposed/main Packages  
Hit http://archive.ubuntu.com jaunty-proposed/multiverse Packages
Hit http://archive.ubuntu.com jaunty-proposed/universe Packages
Hit http://archive.ubuntu.com jaunty-backports/restricted Packages
Hit http://archive.ubuntu.com jaunty-backports/main Packages 
Hit http://archive.ubuntu.com jaunty-backports/multiverse Packages
Hit http://archive.ubuntu.com jaunty-backports/universe Packages
Fetched 3389B in 22s (148B/s)                                
Reading package lists... Done             

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

benjamin@benjamin-laptop:~$ 

```

---

### Post by humphreybc on 2009-10-24
Anyone else? The reason I seem to be impatient is that I'm at Uni and connected to the uni internet, which is only fast on the weekend (it's exam time so everyone uses it during the week). We also don't have internet at home and I don't bring my laptop into uni very often!

---

### Post by hotstyle765 on 2009-10-24
I just ran sudo do-release-upgrade -d

and it worked fine... I am currently updating. Sure you are still on Jaunty?

run 
cat /etc/issue 

and what is the output?

---

### Post by humphreybc on 2009-10-24
> **hotstyle765 said:**
> I just ran sudo do-release-upgrade -d

and it worked fine... I am currently updating. Sure you are still on Jaunty?

run 
cat /etc/issue 

and what is the output?

Definitely still on Jaunty. Weird huh. I remember upgrading from Intrepid to Jaunty beta was fine earlier this year using the update-manager -d. But then I did a fresh re-install of Jaunty about 4 weeks ago.

benjamin@benjamin-laptop:~$ cat /etc/issue
Ubuntu 9.04 \n \l

benjamin@benjamin-laptop:~$

---

### Post by humphreybc on 2009-10-24
Bump!

---

### Post by winotree on 2009-10-24
Being behind that proxy may prevent you from using this [http://cdimages.ubuntu.com/daily-live/current/](http://cdimages.ubuntu.com/daily-live/current/)

---

### Post by williejones on 2009-10-24
How about downloading a daily CD to get started?

---

### Post by humphreybc on 2009-10-24
> **winotree said:**
> Being behind that proxy may prevent you from using this [http://cdimages.ubuntu.com/daily-live/current/](http://cdimages.ubuntu.com/daily-live/current/)

Yeah you're right, I just ran update-manager -d while connected to a friends' wireless that isn't behind a proxy, and it said that a new distro is available.

@ williejones

Can you _upgrade_ off a CD image? ie, not re-installing completely, but actually upgrading your computer as if you were to do it through update manager.

I say this because then I could download a CD image at university on their hard-wired computers and then USB pen drive it across to my laptop. The hard-wired computers download so much faster than my laptop connected to uni wireless, especially around exam time.

EDIT: It appears you can update [using the Alternate CD]("http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD")

---

### Post by winotree on 2009-10-25
I really don't know *if* you'll be able to *upgrade* from a CD -- after some more reading last night and this morning it seems the Koala comes with GRUB2 and ext4.  These can be added later to an existing set-up however only the newer files, etc will reflect that addition, *not* what was there previously.  Using the daily-build as many of us did, with a clean-installation, would seem to be the preferred route for that reason.  Regardless of what you choose to do here's hoping your results are satisfying.  ;)

---

### Post by humphreybc on 2009-10-26
I managed to upgrade using the alternate CD. I just downloaded the iso, put it on a pen drive, then mounted it in Jaunty. Then all I had to do was run the script on the alternate CD to upgrade.

After the distro upgrade, a lot of packages were out of date, so I spent a few hours upgrading packages on a very slow internet connection.

Now I'm on Karmic RC. Yay!

Just a comment on startup/shutdown: Boot times seem a bit longer than Jaunty which is worrying, perhaps it seems that way because of the two boot screens now (The icon in the middle on its own, and then the animated screen). Why are there two screens?? Unneccesary perhaps? After the first screen, I expect the login window to come up, but there's another boot splash screen!

And a note on shutdown times: Holy crap is it fast. My laptop shuts down in under 5 seconds, no kidding. It renders hibernate useless, because a shutdown and then boot is about 2x as fast as hibernating and then waking up!

---

