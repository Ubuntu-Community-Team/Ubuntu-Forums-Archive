---
title: "Installations problems shortly after the 11.04 Ubuntu installation itself."
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by RaisenBran on 2011-07-30
Hello,

Was curious as to what the title should be..

> Installations problems shortly after the 11.04 Ubuntu installation itself.

However it explains all my problems.. A few days ago I put Ubuntu 11.04 on my usb drive and I liked it, **a lot**. Anyways I installed it besides Windows 7 and corrupted it by copy/pasting a system file I was trying to edit onto to the desktop. :o  (did i mention I had 4 code screens of death before I finished? Had to unplug my laptop's battery everytime one of them came up.. :o) So I decided I should format my usb drive for a fresh ubuntu installation. Booted up the usb drive, did the installation process and had ubuntu again. Now I wanted to add some apps and some websites told me to use commands like "sude apt add" in terminal. The first few installations were fine but now I receive this error:

[IMG]http://psp-source.lunarcp.com/datas/users/43-screenshot-untitled%20window.png[/IMG]

And it's not just certain apps, it's the whole software center! I tried Chromium and still same type of errors or similar ones..! So any help would be appreciated! :) Oh yeah in case you didn't know, I am a noob at linux for the moment since it's been less than a week of me using it. 

I get tech stuff, I am a tech wizard. I can do another install if I have to but I just kinda want to know what went wrong and if I can fix it..?

Thanks everyone :), popcorn? :popcorn:

Update: I also kinda noticed I am in the wrong place :o no topic move tool or deletion method for me to fix this, sorry 'bout that..

---

### Post by coffeecat on 2011-07-30
Hi, and welcome to the forum.

> **RaisenBran said:**
> I just kinda want to know what went wrong and if I can fix it..?

I have a feeling this was the cause of what went wrong...

> **RaisenBran said:**
> Now I wanted to add some apps and some websites told me to use commands like "sude apt add" in terminal. The first few installations were fine but now I receive this error:

I'm not trying to be unkind here, but running "sudo apt add" commands from some websites out there is just about as undesirable as downloading exe installers for Windows from websites you know nothing about and running them. You probably won't get viruses but you may get badly written software that breaks or damages your system. This could be what has happened here.

Correction - you won't get viruses, but you could get malware. There have been instances of very destructive malicious Ubuntu malware being posted on a well-known theming website in the guise of theme installers.

But back to your problem. What were the apt add commands you ran just before this error occurred? And what were the websites?

---

### Post by RaisenBran on 2011-07-30
Thanks for replying first of all.

Second of all, I kinda had a feeling that these websites aren't trustworthy but they had features I really needed and I couldn't find in the Ubuntu software center. Since I am fairly new to ubuntu I think it may have been my fault and I did something wrong in the terminal.

The url: [http://www.techdrivein.com/2011/05/10-useful-application-indicators-for.html](http://www.techdrivein.com/2011/05/10-useful-application-indicators-for.html)

I strongly believe whatever I have done cannot be un-done, thanks for the help! In addition, with my link provided, if there is any other dash applications that are similar to the ones in the link, I would very much appreciate it if someone could provide alternatives.

---

### Post by coffeecat on 2011-07-31
> **RaisenBran said:**
> Second of all, I kinda had a feeling that these websites aren't trustworthy but they had features I really needed and I couldn't find in the Ubuntu software center. Since I am fairly new to ubuntu I think it may have been my fault and I did something wrong in the terminal.

The url: [http://www.techdrivein.com/2011/05/10-useful-application-indicators-for.html](http://www.techdrivein.com/2011/05/10-useful-application-indicators-for.html)

That link tells you to enable a load of ppa (a type of 3rd party) repositories. I doubt whether any of those are malicious, but ppa repos are of variable quality and can create dependency problems when trying to install from the official repositories. I don't think you did anything wrong in the terminal, but something is very odd. I've had a closer look at your screenshot and the package manager simply shouldn't be fussing at you like that. The first three dependency packages that it wants to install are the current versions in the repository and do satisfy chromium-browser's dependency so, on the face of it, the error looks absurd. And it gives no reason why it is not going to install libnss3-1d.

I suspect that one of the ppa repositories - or the packages you have installed from it - may have created a dependency conflict. Try this command in the terminal:

```
sudo apt-get -f install
```

Post the output that you get, including any error messages. It may give us a clue as to what has gone wrong.

---

### Post by RaisenBran on 2011-07-31
Okay,

I did do what you said and entered "sudo apt-get -f install" and then terminal asked me to use another sudo apt to achieve your action. It had about 20 lines of code, basically lines that look like a setup. I copied and pasted it but I somehow managed to loose it on my clipboard :( it looks meaningless anyways..

Then I tried your code again and it gave me an agreement located on this page: [http://www.microsoft.com/typography/fontpack/eula.htm](http://www.microsoft.com/typography/fontpack/eula.htm) except it came in terminal and this has happened before.

It tells me to agree but I see no agreement button but would there even be one, some type of command to accept? Anyways now it says: 

"E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

I think E is my cd drive if I remember correctly..

---

### Post by coffeecat on 2011-08-01
> **RaisenBran said:**
> Then I tried your code again and it gave me an agreement located on this page: [http://www.microsoft.com/typography/fontpack/eula.htm](http://www.microsoft.com/typography/fontpack/eula.htm) except it came in terminal and this has happened before.

It tells me to agree but I see no agreement button but would there even be one, some type of command to accept?

The system is trying to install the microsoft corefonts installer. There must have been an aborted installation before for this for it to come up with apt-get -f install. I guess you may have tried to install the package ubuntu-restricted-extras, but something came unstuck. Anyway, signing the EULA is possible in the terminal. When you get the request to sign the EULA in the terminal simply press the tab key and OK will be highlighted. Then press enter.

> **RaisenBran said:**
>  Anyways now it says: 

"E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

You have a package manager open when you are trying to run apt-get in the terminal. Make sure Synaptic, Update Manager and/or Software Centre are all closed before running apt-get.

---

### Post by RaisenBran on 2011-08-01
Did you just make me install fonts? Looks like it..How is that supposed to help?

Throughout the process just jumbos of code came and then at the end it said:

"All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts"

I accepted the EULA agreement by the way..

And nothing was open while I was using terminal, besides firefox..

---

### Post by coffeecat on 2011-08-01
> **RaisenBran said:**
> Did you just make me install fonts? Looks like it..How is that supposed to help?


No, I did not make you install fonts. Had you read my previous post you would have understood the situation. **You** had previously tried to install a fonts package, possibly included in the ubuntu-restricted-extras package, but got stuck with the EULA.

For the record. The command "sudo apt-get -f install" does this: (from the apt-get manual):

> -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution.

I suggested that to try to resolve your original dependency problem but clearly it also picked up an earlier incomplete package installation, specifically the microsoft corefonts installer.

**EDIT:**

> **RaisenBran said:**
> And nothing was open while I was using terminal, besides firefox..

No. If you got the 

> "E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

I think E is my cd drive if I remember correctly..

...message, then one of Synaptic, Software Centre, or Update Manager was open. Depending on your settings, it's quite possible that Update Manager had opened itself to check for updates without you noticing. It has a habit of doing that at inopportune moments - just like, but not quite as irritating, the Java updater in Windows.

By the way, the "E:" in that message is nothing to do with your Windows E: drive. Drive C:/D:/E: designations belong firmly in the Windows world and have no meaning in Unix OSs such as Linux and MacOS.

---

### Post by RaisenBran on 2011-08-03
Okay so what do I do now..?

---

### Post by coffeecat on 2011-08-03
> **RaisenBran said:**
> Okay so what do I do now..?

I'm not really sure where your system is now, so run these commands one after the other:

```
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
```

No guarantees that that will fix anything, but I'm just suggesting things to try to get your package manager into a consistent state after the combination of a ppa repository and an aborted installation of the corefonts installer - well - borked it.

If the above run without error, all good and well. If there are any errors, post them. Then try to install chromium again. I only hold out faint hope that chromium will install without those dependency issues because I'm sure a ppa has introduced problems that wouldn't otherwise be there. But you never know - you might get lucky.

---

### Post by RaisenBran on 2011-08-03
!st one:
 ```
brandon@brandon-Satellite-L655:~$ sudo apt-get -f install
[sudo] password for brandon: 
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```2nd one:
```
brandon@brandon-Satellite-L655:~$ sudo apt-get update
Ign http://archive.canonical.com natty InRelease                               
Get:1 http://archive.canonical.com natty Release.gpg [198 B]                                  
Get:2 http://archive.canonical.com natty Release [5,916 B]                                    
Get:3 http://archive.canonical.com natty/partner i386 Packages [8,648 B]                      
Ign http://archive.canonical.com natty/partner TranslationIndex                               
Ign http://archive.canonical.com natty/partner Translation-en_US                              
Ign http://archive.canonical.com natty/partner Translation-en                                 
Ign http://security.ubuntu.com natty-security InRelease                                       
Ign http://us.archive.ubuntu.com natty InRelease                                              
Ign http://us.archive.ubuntu.com natty-updates InRelease                                      
Ign http://ppa.launchpad.net natty InRelease                                                  
Ign http://ppa.launchpad.net natty InRelease                                                  
Ign http://ppa.launchpad.net natty InRelease                                                  
Ign http://extras.ubuntu.com natty InRelease                                                  
Get:4 http://security.ubuntu.com natty-security Release.gpg [198 B]                                                                                    
Get:5 http://us.archive.ubuntu.com natty Release.gpg [198 B]                                                                                           
Ign http://ppa.launchpad.net natty InRelease                                                                                                           
Get:6 http://ppa.launchpad.net natty Release.gpg [316 B]                                                                                               
Get:7 http://extras.ubuntu.com natty Release.gpg [72 B]                                                                                                
Get:8 http://security.ubuntu.com natty-security Release [27.2 kB]                                                                                      
Get:9 http://ppa.launchpad.net natty Release.gpg [316 B]                                                                                               
Get:10 http://ppa.launchpad.net natty Release.gpg [316 B]                                                                                              
Get:11 http://us.archive.ubuntu.com natty-updates Release.gpg [198 B]                                                                                  
Get:12 http://security.ubuntu.com natty-security/main Sources [63.5 kB]                                                                                
Get:13 http://extras.ubuntu.com natty Release [9,753 B]                                                                                                
Get:14 http://ppa.launchpad.net natty Release.gpg [316 B]                                                                                              
Get:15 http://us.archive.ubuntu.com natty Release [39.8 kB]                                                                                            
Get:16 http://ppa.launchpad.net natty Release [9,726 B]                                                                                                
Get:17 http://extras.ubuntu.com natty/main Sources [14 B]                                                                                              
Get:18 http://ppa.launchpad.net natty Release [9,731 B]                                                                                                
Get:19 http://security.ubuntu.com natty-security/restricted Sources [14 B]                                                                             
Get:20 http://security.ubuntu.com natty-security/universe Sources [9,829 B]                                                                            
Get:21 http://security.ubuntu.com natty-security/multiverse Sources [658 B]                                                                            
Get:22 http://security.ubuntu.com natty-security/main i386 Packages [165 kB]                                                                           
Get:23 http://extras.ubuntu.com natty/main i386 Packages [14 B]                                                                                        
Ign http://extras.ubuntu.com natty/main TranslationIndex                                                                                               
Get:24 http://ppa.launchpad.net natty Release [9,749 B]                                                                                                
Get:25 http://ppa.launchpad.net natty Release [9,744 B]                                                                                                
Get:26 http://us.archive.ubuntu.com natty-updates Release [27.2 kB]                                                                                    
Get:27 http://security.ubuntu.com natty-security/restricted i386 Packages [14 B]                                                                       
Get:28 http://security.ubuntu.com natty-security/universe i386 Packages [31.9 kB]                                                                      
Get:29 http://security.ubuntu.com natty-security/multiverse i386 Packages [2,074 B]                                                                    
Ign http://security.ubuntu.com natty-security/main TranslationIndex                                                                                    
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex                                                                              
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex                                                                              
Get:30 http://ppa.launchpad.net natty/main Sources [464 B]                                                                                             
Get:31 http://ppa.launchpad.net natty/main i386 Packages [352 B]                                                                                       
Ign http://ppa.launchpad.net natty/main TranslationIndex                                                                                               
Ign http://security.ubuntu.com natty-security/universe TranslationIndex                                                                                
Get:32 http://us.archive.ubuntu.com natty/main Sources [862 kB]                                                                                        
Get:33 http://ppa.launchpad.net natty/main Sources [463 B]                                                                                             
Get:34 http://ppa.launchpad.net natty/main i386 Packages [405 B]                                                                                       
Ign http://ppa.launchpad.net natty/main TranslationIndex                                                                                               
Get:35 http://ppa.launchpad.net natty/main Sources [652 B]                                                                                             
Get:36 http://ppa.launchpad.net natty/main i386 Packages [550 B]                                                                                       
Ign http://ppa.launchpad.net natty/main TranslationIndex                                                                                               
Get:37 http://ppa.launchpad.net natty/main Sources [1,938 B]                                                                                           
Get:38 http://ppa.launchpad.net natty/main i386 Packages [3,187 B]                                                                                     
Ign http://ppa.launchpad.net natty/main TranslationIndex                                                                                               
Get:39 http://us.archive.ubuntu.com natty/restricted Sources [4,104 B]                                                                                 
Get:40 http://us.archive.ubuntu.com natty/universe Sources [4,380 kB]                                                                                  
Ign http://extras.ubuntu.com natty/main Translation-en_US                                                                                              
Ign http://extras.ubuntu.com natty/main Translation-en                                                                                                 
Ign http://ppa.launchpad.net natty/main Translation-en_US                                                                                              
Ign http://ppa.launchpad.net natty/main Translation-en                                                                                                 
Ign http://security.ubuntu.com natty-security/main Translation-en_US                                                                                   
Ign http://security.ubuntu.com natty-security/main Translation-en                                                                                      
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US                                                                             
Ign http://security.ubuntu.com natty-security/multiverse Translation-en                                                                                
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US                                                                             
Ign http://ppa.launchpad.net natty/main Translation-en_US                                                                                              
Ign http://ppa.launchpad.net natty/main Translation-en                                                                                                 
Ign http://ppa.launchpad.net natty/main Translation-en_US                                                                                              
Ign http://security.ubuntu.com natty-security/restricted Translation-en                                                                                
Ign http://security.ubuntu.com natty-security/universe Translation-en_US                                                                               
Ign http://security.ubuntu.com natty-security/universe Translation-en                                                                                  
Ign http://ppa.launchpad.net natty/main Translation-en                                                                                                 
Ign http://ppa.launchpad.net natty/main Translation-en_US                                                                                              
Ign http://ppa.launchpad.net natty/main Translation-en                                                                                                 
Get:41 http://us.archive.ubuntu.com natty/multiverse Sources [155 kB]                                                                                  
Get:42 http://us.archive.ubuntu.com natty/main i386 Packages [1,550 kB]                                                                                
Get:43 http://us.archive.ubuntu.com natty/restricted i386 Packages [8,986 B]                                                                           
Get:44 http://us.archive.ubuntu.com natty/universe i386 Packages [6,021 kB]                                                                            
Get:45 http://us.archive.ubuntu.com natty/multiverse i386 Packages [183 kB]                                                                            
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                                                                                           
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex                                                                                     
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex                                                                                     
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex                                                                                       
Get:46 http://us.archive.ubuntu.com natty-updates/main Sources [98.1 kB]                                                                               
Get:47 http://us.archive.ubuntu.com natty-updates/restricted Sources [14 B]                                                                            
Get:48 http://us.archive.ubuntu.com natty-updates/universe Sources [22.1 kB]                                                                           
Get:49 http://us.archive.ubuntu.com natty-updates/multiverse Sources [1,893 B]                                                                         
Get:50 http://us.archive.ubuntu.com natty-updates/main i386 Packages [286 kB]                                                                          
Get:51 http://us.archive.ubuntu.com natty-updates/restricted i386 Packages [14 B]                                                                      
Get:52 http://us.archive.ubuntu.com natty-updates/universe i386 Packages [80.2 kB]                                                                     
Get:53 http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages [4,267 B]                                                                   
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex                                                                                   
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex                                                                             
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex                                                                             
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex                                                                               
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                                                                                          
Ign http://us.archive.ubuntu.com natty/main Translation-en                                                                                             
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US                                                                                    
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en                                                                                       
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US                                                                                    
Ign http://us.archive.ubuntu.com natty/restricted Translation-en                                                                                       
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US                                                                                      
Ign http://us.archive.ubuntu.com natty/universe Translation-en                                                                                         
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US                                                                                  
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en                                                                                     
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US                                                                            
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en                                                                               
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US                                                                            
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en                                                                               
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US                                                                              
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en                                                                                 
Fetched 14.1 MB in 48s (291 kB/s)                                                                                                                      
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```3rd one: ```
brandon@brandon-Satellite-L655:~$ sudo apt-get dist-upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```Monday, I kept getting these errors so I looked them up and on other forums they said to delete the files so I did so. And now instead of saying "locked" or something similar it now says "no such file or directory"..because I deleted the files and directories..

CoffeeCat, is their a way to reinstall Ubuntu onto my laptop? I have not started any important work so if I have to reinstall Ubuntu and it deletes any files I'll be okay. Do I just get my usb and go through the process again? It was something wrong I did in the terminal and I already killed Ubuntu once before coming here... This sucks..

---

### Post by coffeecat on 2011-08-03
> **RaisenBran said:**
> Do I just get my usb and go through the process again? 

More or less. When you get to the partitioning stage of the installer choose the "Something else" option. You can then designate which partitions to use, so that you can re-use the partitions presently occupied by your problematic install and overwrite them.

Do you know which is your Ubuntu root (/) partition? Click on that, choose "edit" or "change" (I'm going from memory here) and then choose ext4 for filesystem, tick the reformat box and "/" for mountpoint. You don't have to do anything about the swap partition - the installer will pick your pre-existing one up automatically.

If you have any other partitions separate from your root (such as a home partition) you need to do the same, but adjust the mountpoint accordingly. But you may not need to worry about any separate partitions. If you let the installer do its thing automatically first time around, you'll have only a main root partition and a swap partition.

---

### Post by RaisenBran on 2011-08-04
Ok thanks so much for everything, gonna try tomorrow.

---

