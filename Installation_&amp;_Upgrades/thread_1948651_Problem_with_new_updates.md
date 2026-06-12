---
title: "Problem with new updates"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by WaNaBePi on 2012-03-28
I'm using ubuntu 11.10.

One of the following updates(see attachment screen shot) seems to not let my laptop boot.

I have been using the older linux version 3.0.0-16 as 3.0.0-17 wont boot.

The boot stops seemingly at the black "ubuntu" screen. I waited 10 min for it to load with no signs of progress.

Any advice?

---

### Post by Paddy Landau on 2012-03-29
I'm not sure what you can do about that.

Try the following commands from a terminal -- they probably won't help, but it's worth trying.
```
sudo apt-get update
sudo apt-get dist-upgrade
```Which version of Ubuntu are you using?

---

### Post by WaNaBePi on 2012-03-29
I'm using: **ubuntu 11.10**.

To further disambiguate see screen shot.

after those commands I got:

```
default@default-laptop:~$ sudo apt-get update
[sudo] password for default: 
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://us.archive.ubuntu.com oneiric Release.gpg                           
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://archive.canonical.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://us.archive.ubuntu.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://archive.canonical.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://us.archive.ubuntu.com oneiric-updates Release                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://us.archive.ubuntu.com oneiric/main amd64 Packages                   
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com oneiric/universe amd64 Packages               
Hit http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages           
Hit http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages       
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en       
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://archive.canonical.com oneiric/partner Translation-en              
Ign http://ppa.launchpad.net oneiric/main Translation-en                     
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                  
Ign http://ppa.launchpad.net oneiric/main Translation-en                     
Ign http://security.ubuntu.com oneiric-security InRelease
Hit http://security.ubuntu.com oneiric-security Release.gpg
Hit http://security.ubuntu.com oneiric-security Release
Hit http://security.ubuntu.com oneiric-security/main Sources
Hit http://security.ubuntu.com oneiric-security/restricted Sources
Hit http://security.ubuntu.com oneiric-security/universe Sources
Hit http://security.ubuntu.com oneiric-security/multiverse Sources
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://security.ubuntu.com oneiric-security/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://security.ubuntu.com oneiric-security/main Translation-en
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Reading package lists... Done
default@default-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Nothing unexpected there. I also waited 30 min for it to boot another time, no signs of progress.

I'm a little worried that an upgrade to ubuntu 12.04(I think it is, the next release) won't stop this as it will likely be using the same lunix 3.0.0-17("kernal" right?)

Well I'm gonna try a restart now and see if those commands did anything, just in case.

Thanks for your help.

Waited for 10min... no change still have to boot in 3.0.0-16

Advice anyone?

---

### Post by Paddy Landau on 2012-03-29
No, the commands did nothing.

Version 12.04 will most likely have the [noparse]3.2.0-20.33[/noparse] kernel (based on 3.2.12 -- don't ask me to explain the numbering).

May I suggest that you wait for the release of 12.04 (in a month or so). Make a full backup of your data, do a clean installation, and restore your data.

Before you do so, you can [download the Beta release of 12.04]("http://www.ubuntu.com/testing/download") and run it from a Live CD to see how well it runs (as it is a beta, you can expect some problems).

---

### Post by WaNaBePi on 2012-03-30
Well the news about 12.04 is good I suppose... Ah the waiting game.

Just for clarification: was I supposed to run 3.0.0-17 in recovery mode and enter the commands there? Me thinks no, but I'm not sure. Guess it couldn't hurt to try that variation.(Sorry for being a noob.)

I successfully upgraded from ubuntu 10.04 to 11.10 using the GUI with no major hitches. Given this do you still think I should do a fresh install?

---

### Post by Paddy Landau on 2012-03-30
> **WaNaBePi said:**
> ... was I supposed to run 3.0.0-17 in recovery mode and enter the commands there?
No; what you did was just fine.

> **WaNaBePi said:**
> I successfully upgraded from ubuntu 10.04 to 11.10 using the GUI with no major hitches. Given this do you still think I should do a fresh install?
Yes, I do think a fresh installation would be better. Many people find it less problematic than upgrades.

If you require stability, stick with 12.04 until the next LTS, which will be 14.04.

---

### Post by WaNaBePi on 2012-03-30
Any idea what would have caused this boot problem; just out of curiosity?

Thank you for your help and advice.

---

### Post by Paddy Landau on 2012-03-30
I'm sorry, I don't know. I thought it might have been a failed update, but it wasn't.

---

### Post by WaNaBePi on 2012-03-31
Cool my computer stumped the forums.

Seriously, thank you so much.

---

### Post by raja.genupula on 2012-04-01
> **WaNaBePi said:**
> I'm using ubuntu 11.10.

One of the following updates(see attachment screen shot) seems to not let my laptop boot.

I have been using the older linux version 3.0.0-16 as 3.0.0-17 wont boot.

The boot stops seemingly at the black "ubuntu" screen. I waited 10 min for it to load with no signs of progress.

Any advice?

Have you tried   by reinstalling your graphics drivers?

---

### Post by WaNaBePi on 2012-04-01
How would I go about doing that? 

My known options(see screen shot)

Maybe I could switch as I have options for graphics drivers? (go agaisnt what is "*recommended*")

I'll give it a go.

How would I find more options if switching doesn't work?

Thank you.

~~~~~~~~~~~~~~~~~~~~~~~~~~
Cool switching it worked! Solved!

How did you know or think to try that? I'm trying to do my own trouble shooting. I did Google searches for this. usually I can find something on my problem. In this case I couldn't any trouble shooting tips, so I was up sh1ts creek. How would I figure this on my own? Any good books for ubuntu newbs?

---

### Post by raja.genupula on 2012-04-02
yeah here some links for you

[http://www.makeuseof.com/tag/5-downloadable-books-to-teach-yourself-linux/](http://www.makeuseof.com/tag/5-downloadable-books-to-teach-yourself-linux/)

[http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html](http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html)

---

### Post by WaNaBePi on 2012-04-02
Cool. Thank you!

---

