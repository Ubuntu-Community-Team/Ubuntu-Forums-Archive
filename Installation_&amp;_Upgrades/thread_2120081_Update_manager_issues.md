---
title: "Update manager issues"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by donaldt on 2013-02-25
OK, let's see if anyone knows what is happening with my update manager.

About 6 months ago, update manager stopped working.  It would start an update, but about half way through it would stop.  Clicking to kill it would cause it to expand to full screen.  The Ubuntu 12.04 LTS (32 bit) I am running stops dead and only a re-boot will cure the lock up.

Some on-line experts suggested I try using the terminal instead and this command. [sudo apt-get update && sudo apt-get dist-upgrade]  When I use the update/upgrade as quoted here, I am able to get a lot of activity and after hitting enter several times it will say END.  But a complete update/upgrade has apparently not taken place.

When I go back to update manager, it still shows all of the original updates/upgrades available and if I click on update, it completes the command, clens out the update files and announces that everything is up to date.  I've been limping along like this,but perhaps someone with greater knowledge of the process can help me get back to just using update manager.

Thanks in advance to anyone that cares to help!

Donaldt

---

### Post by Bashing-om on 2013-02-25
donaldt; Hi !

The base of the update manager is apt-get. If there exist problems within the update manager, the use of the terminal commands will show the relevant errors.

Post the output of terminal commands:
```
sudo apt-get update
sudo apt-get upgrade
```That will give us an idea as to what might be misshappening.
[INDENT]Further advise pending
 
[/INDENT]

---

### Post by donaldt on 2013-02-26
When I run the command, I get a bunch of hits and they conclude with this:

Reading package lists... Done
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
donald@donald-Aspire-3810T:~$ 


I seem to be chasing my tail.  Does this tell you anything?

thanks,

Donaldt

---

### Post by Bashing-om on 2013-02-26
donaldt;

 Semi so makes sense.
1. Not happy with your sources.list.d and maybe sources.list.
2. Is your box a 64 bit machine and running some 32 bit application (multi-arch - seen a few post in this regard) ?

For the sources, post the output of terminal commands:
```
ls -la /etc/apt/sources.list.d
cat /etc/apt/sources.list 
```Too see the kernel's architecture:
```
uname -a
```Fix these up and then maybe will fix the  /var/lib/apt/list -> duplication thing.
[INDENT][INDENT]a tale in the telling (files that is)

[/INDENT][/INDENT]

---

### Post by donaldt on 2013-02-27
Thanks!

My Ubuntu 12.04 is all 32 bit, as far as I know.

Here is the result of the commands you suggested:


donald@donald-Aspire-3810T:~$ cat /etc/apt/sources.list.d
cat: /etc/apt/sources.list.d: Is a directory
donald@donald-Aspire-3810T:~$ 
donald@donald-Aspire-3810T:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main #Third party developers repository


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) precise main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) precise universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) precise-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) precise-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) precise-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) precise-updates restricted main universe multiverse
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
# deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
donald@donald-Aspire-3810T:~$ 

donaldt

---

### Post by donaldt on 2013-02-27
Here is the result of the uname -d

donald@donald-Aspire-3810T:~$ uname -a
Linux donald-Aspire-3810T 3.2.0-38-generic-pae #61-Ubuntu SMP Tue Feb 19 12:39:51 UTC 2013 i686 i686 i386 GNU/Linux
donald@donald-Aspire-3810T:~$ 


What have we learned?

donaldt

---

### Post by plucky on 2013-02-27
> cat /etc/apt/sources.list.d
cat: /etc/apt/sources.list.d: Is a directory

That should be ```
cat /etc/apt/sources.list.d/*.list
```

and from your sources.list
> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

there seems to be two of these lines.Remove one using the # at the front of the line.
Also all your precise updates are commented out.

Good Luck

---

### Post by Bashing-om on 2013-02-27
@ plucky Thanks for catching my error.

@ donaldt; Hey we are learning... lets work on the sources.list file //You attention is invited to plucky's last//

I do not think you want to mix mirror sites in that sources.list file;
a) (un)comment " # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise XXXXX" lines;
b) comment out "deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) precise main XXXXXX' lines -so mirrors are not mixed
c) I would also suggest to comment out all the " deb-src " lines unless you intend to compile code from source.

Here is my  /etc/apt/sources.list file for comparison to yours... Be advised my system is AMD -64 and my closest/fastest mirror is in Texas.

```
sysop1@1204-a:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ftp.utexas.edu/ubuntu/ precise main restricted
#deb-src http://ftp.utexas.edu/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.utexas.edu/ubuntu/ precise-updates main restricted
#deb-src http://ftp.utexas.edu/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.utexas.edu/ubuntu/ precise universe
#deb-src http://ftp.utexas.edu/ubuntu/ precise universe
deb http://ftp.utexas.edu/ubuntu/ precise-updates universe
#deb-src http://ftp.utexas.edu/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.utexas.edu/ubuntu/ precise multiverse
#deb-src http://ftp.utexas.edu/ubuntu/ precise multiverse
deb http://ftp.utexas.edu/ubuntu/ precise-updates multiverse
#deb-src http://ftp.utexas.edu/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://ftp.utexas.edu/ubuntu/ precise-security main restricted
#deb-src http://ftp.utexas.edu/ubuntu/ precise-security main restricted
deb http://ftp.utexas.edu/ubuntu/ precise-security universe
#deb-src http://ftp.utexas.edu/ubuntu/ precise-security universe
deb http://ftp.utexas.edu/ubuntu/ precise-security multiverse
#deb-src http://ftp.utexas.edu/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
sysop1@1204-a:~$ 
```When you get this file in shape we will look at the files in the directory sources.list.d

And then do the update/upgrade.[INDENT]just try'n to help

[/INDENT]

---

### Post by matt_symes on 2013-02-27
Hi

Can we get clarification on the below please.

> About 6 months ago, update manager stopped working.  It would start an  update, but about half way through it would stop. Did it stop when downloading the software or installing ?

>  Clicking to kill it  would cause it to expand to full screen.Have you tried to close it any other way such as using xkill or from the command line ?

 > The Ubuntu 12.04 LTS (32 bit) I  am running stops dead and only a re-boot will cure the lock up.Can i understaand this. When you close Update-Manager that has stalled, by clicking on the close button update-manager goes full screen and Ubuntu itself freezes ? 

Is it ubuntu that freezes or is it because update-manager, that is now full screen, will not except any input ?

When you say full screen, do you mean maximized or actually taken over the entire display ?

Can you get to a console ? Does sysreq resiub reboot gracefully ?

Have you run update-manager from the terminal to get debug information ?

Kind regards

---

### Post by donaldt on 2013-02-28
I've been oout of touch.  First, I will answer the last questions, then attempt to correct the code as suggested.

The lock up occurrs during update/upgrade, i.e. during installation

No, I've not tried killing it via terminal.  

Yes, it appears to me that Ubuntu freezes as I can not get anything to operate without a re-boot

The screen (I have two)  is maximized and can be changed back to normal, but nothing else will run

I probably didn't explain this very well.  The only way I can get update manager to work is if I FIRST open terminal and use this command [sudo apt-get update && sudo apt-get dist-upgrade]  I get a lot of action in terminal but apparently it does not complete the update/upgrade.  When I go back to update manager, all of the same updates are still there.  I can then click on them and it will complete the update/upgrade and everything is normal.

Does this help?  Thanks for your help.  

donaldt

---

### Post by matt_symes on 2013-02-28
Hi

I would suggest cleaning out the list file cache as well as look at the sources like bashing-om suggested.

```
sudo rm -rf /var/lib/apt/lists/*
```

also clean the package cache

```
sudo apt-get clean
```

If you run it again and it freezes, try to get to a console.

Press ctrl + alt + F1 at the same time. If this gets you to a console, login with your user name and pasword.

You can then kill update-manager with

```
sudo killall update-manager
```

```
sudo kill $(pgrep update-manager)
```

If, after these two commands, it still wont die then use this.

```
sudo kill -9 $(pgrep update-manager)
```

You should try one of the first two commands first and check to see if it is dead by going to to the graphical display.

You can get back to the graphicak display by pressing ctrl + alt + F7 at the same time.

Only use the last command (SIGKILL) as a lsat resort.

If it does freeze after your sources have been checked and the caches cleaned then please post back stating if you could get to a console and kill update-manager that way and also state if you had to use a SIGKILL to kill it.

Kind regards

---

### Post by donaldt on 2013-03-01
OK.  I ran your commands.  Just got 13 new updates and tried install.  The updates stalled about half way.  I was able to open a terminal (so obviously the only lock-up is in update manager) and did the kill all command which got rid of update manager and left everything else working properly.

I'll go back to my usual method of using terminal [sudo apt-get update && sudo apt-get dist-upgrade]

After I run this command I will go back to update manager, and if it is the same as before, it will still have all 13 updates downloaded but not installed.  I can then click install and everything will be installed and the computer will be shown as up to date.

So, here goes.  I'll let you know what happens

OOPS!  that doesn't work any more.  I get this message [N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
donald@donald-Aspire-3810T:~$ 

donaldt

---

### Post by donaldt on 2013-03-01
I need help with text editing in terminal.  How do I get rid of the hash marks etc. to change the files, i.e. comment them out or make them available?  I am not a linux programmer.

Thanks!

donaldt

---

### Post by Bashing-om on 2013-03-01
donaldt;

Hanging in there with you and to the issue presently at hand:
edit /etc/apt/sources.list :
Open a terminal for a command line interface.
First make a backup copy of the current file --one never knows what can happen -power failure at any time or whatever.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list-old
``` password required.
Now to edit that database file; As we are working on a system file outside of your home directory and the application we are using is GUI based. You will elevate your privileges using "gksudo". Your password is required.Thus:
```
gksudo gedit /etc/apt/sources.list
```
enter your password in the authetication window.
"gedit" is a text editior and in this instance will be what-you-see-is-what-you-get editor. The file is opened for editing with the above command/password.
At this time use the arrow keys on the keyboard to place the "cursor" where you want it. Backspace or delete keys to "delete" text, any desired key to "insert" text.
Take your time, compare what you have after edits to the sources.list file I provided. Keep in mind my mirror will be different than yours and my operating system is (AMD-64) also different. Any line beginning with the "#" character will be ignored when the file is executed; as a future aid documentation is helpfull,detailing what and why you made changes to any given file. In "gedit" you may open additional files and drag the file to be side-by-side for comparrioson.

OK now you are happy with all the changes you have made. Save the file and exit back to the terminal.
Reboot the system and see what results.
```
sudo shutdown -r now
```

Ok back up from reboot: Lets see what the status is now and get some idea of what might remain to be done by looking at the errors "dpkg" generated with:
```
 sudo apt-get update
sudo apt-get upgrade
``` There is likely to be errors. Post the output of the above so we can see.[INDENT=2]further advise pending[/INDENT]

---

### Post by donaldt on 2013-03-01
Hello...and thanks for staying with me.  I believe I did what you asked.  I printed out the changes so they can be reversed if needed.

Here is the consecutive output from "sudo apt-get update" and "sudo apt-get upgrade.

donald@donald-Aspire-3810T:~$ sudo apt-get update
[sudo] password for donald: 
Ign [http://mirrors.rit.edu](http://mirrors.rit.edu) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) precise Release.gpg                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security InRelease                    
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) precise Release                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease                            
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release.gpg [198 B]        
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) precise/main i386 Packages                          
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) precise/restricted i386 Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Sources                         
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) precise/multiverse i386 Packages                    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) precise/universe i386 Packages                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) precise/main TranslationIndex                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release [49.6 kB]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Sources                     
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) precise/multiverse TranslationIndex                 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) precise/restricted TranslationIndex                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) precise/universe TranslationIndex                   
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) precise/main Translation-en                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) precise/multiverse Translation-en                   
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise InRelease                        
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) precise/restricted Translation-en                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) precise/universe Translation-en                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en  
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg 
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release     
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex            
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]  
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en                  
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en              
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]  
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex [3,706 B]    
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex [2,676 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex [2,596 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex [2,922 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [594 kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en              
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [9,503 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [184 kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [10.4 kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main i386 Packages [239 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe i386 Packages [69.9 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse i386 Packages [2,362 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en [726 kB]       
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en [2,395 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en [3,341 kB] 
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [260 kB]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en [5,694 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en [2,328 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [108 kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Translation-en [112 kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse Translation-en [995 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted Translation-en [978 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe Translation-en [43.2 kB]
Fetched 12.2 MB in 28s (430 kB/s)                                              
Reading package lists... Done
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
donald@donald-Aspire-3810T:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa libssl1.0.0
  libxatracker1 openssl sudo xserver-xorg-video-nouveau
13 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/30.2 MB of archives.
After this operation, 4,096 B disk space will be freed.
Do you want to continue [Y/n]? y
Reading changelogs... Done
Preconfiguring packages ...
(Reading database ... 510544 files and directories currently installed.)
Preparing to replace libssl1.0.0 1.0.1-4ubuntu5.6 (using .../libssl1.0.0_1.0.1-4ubuntu5.7_i386.deb) ...
Unpacking replacement libssl1.0.0 ...
Setting up libssl1.0.0 (1.0.1-4ubuntu5.7) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 510544 files and directories currently installed.)
Preparing to replace libgl1-mesa-dri 8.0.4-0ubuntu0.3 (using .../libgl1-mesa-dri_8.0.4-0ubuntu0.4_i386.deb) ...
Unpacking replacement libgl1-mesa-dri ...
Preparing to replace libgl1-mesa-glx 8.0.4-0ubuntu0.3 (using .../libgl1-mesa-glx_8.0.4-0ubuntu0.4_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
Preparing to replace libglapi-mesa 8.0.4-0ubuntu0.3 (using .../libglapi-mesa_8.0.4-0ubuntu0.4_i386.deb) ...
Unpacking replacement libglapi-mesa ...
Preparing to replace libxatracker1 8.0.4-0ubuntu0.3 (using .../libxatracker1_8.0.4-0ubuntu0.4_i386.deb) ...
Unpacking replacement libxatracker1 ...
Preparing to replace libglu1-mesa 8.0.4-0ubuntu0.3 (using .../libglu1-mesa_8.0.4-0ubuntu0.4_i386.deb) ...
Unpacking replacement libglu1-mesa ...
Preparing to replace sudo 1.8.3p1-1ubuntu3.3 (using .../sudo_1.8.3p1-1ubuntu3.4_i386.deb) ...
Unpacking replacement sudo ...
Preparing to replace openssl 1.0.1-4ubuntu5.6 (using .../openssl_1.0.1-4ubuntu5.7_i386.deb) ...
Unpacking replacement openssl ...
Preparing to replace firefox-globalmenu 19.0+build1-0ubuntu0.12.04.1 (using .../firefox-globalmenu_19.0+build1-0ubuntu0.12.04.2_i386.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox 19.0+build1-0ubuntu0.12.04.1 (using .../firefox_19.0+build1-0ubuntu0.12.04.2_i386.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-gnome-support 19.0+build1-0ubuntu0.12.04.1 (using .../firefox-gnome-support_19.0+build1-0ubuntu0.12.04.2_i386.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace firefox-locale-en 19.0+build1-0ubuntu0.12.04.1 (using .../firefox-locale-en_19.0+build1-0ubuntu0.12.04.2_i386.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace xserver-xorg-video-nouveau 1:0.0.16+git20111201+b5534a1-1build2 (using .../xserver-xorg-video-nouveau_1%3a0.0.16+git20111201+b5534a1-1build3_i386.deb) ...
Unpacking replacement xserver-xorg-video-nouveau ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up libgl1-mesa-dri (8.0.4-0ubuntu0.4) ...
Setting up libglapi-mesa (8.0.4-0ubuntu0.4) ...
Setting up libgl1-mesa-glx (8.0.4-0ubuntu0.4) ...
Setting up libxatracker1 (8.0.4-0ubuntu0.4) ...
Setting up libglu1-mesa (8.0.4-0ubuntu0.4) ...
Setting up sudo (1.8.3p1-1ubuntu3.4) ...
Setting up openssl (1.0.1-4ubuntu5.7) ...
Setting up firefox (19.0+build1-0ubuntu0.12.04.2) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (19.0+build1-0ubuntu0.12.04.2) ...
Setting up firefox-gnome-support (19.0+build1-0ubuntu0.12.04.2) ...
Setting up firefox-locale-en (19.0+build1-0ubuntu0.12.04.2) ...
Setting up xserver-xorg-video-nouveau (1:0.0.16+git20111201+b5534a1-1build3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

---

### Post by matt_symes on 2013-03-01
Hi

The good thing is that Ubutnu is not locking up !

You can still get to a console and kill update-manager so it was just update-manager that was locking up by the looks of it.

You just updated and upgraded correctly.

Remove that file giving the warning.

```
sudo rm /etc/apt/sources.list.d/getdeb.list.bck
```

```
sudo apt-get clean
```

```
sudo rm -rf /var/lib/apt/lists/*
```

After that try update-manager.

Does it still lockup ?

Kind regards

---

### Post by donaldt on 2013-03-01
All 13 updates were installed by the terminal command.  Update Manager has nothing left to install.

When I run [cat /etc/apt/sources.list.d/*.list]  this is what I get in terminal:

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
donald@donald-Aspire-3810T:~$ 

Is there another way to check out "Update Manager"??

I really appreciate all the help on this.  It was driving me nutty, but seems to be nearly normal again.  Is there any other file clean up that I need to do, or just wait until I have updates to try out in update manager?

best regards,

donaldt

---

### Post by Bashing-om on 2013-03-01
Matt & donaldt; 
I do not understand why this:
> N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension from "apt-get update"
is not reflected in the out put of "cat /etc/apt/sources.list.d/*.list".
What am I not seeing ?[INDENT=2]a step in the process of learning

[/INDENT]

---

### Post by matt_symes on 2013-03-01
Hi

@bashing-om. 

I told him to delete that file in post #16 and he posted his sources.list.d/* files after (#17). That is why that file had gone.

BTW: Great work with the sources file :D

@OP.

You will need to wait for new updates to see if update-manager is still stalling.

Kind regards

---

### Post by Bashing-om on 2013-03-02
@ matt_symes Thanks for that -- I was beginning to wonder deeper about my troubleshooting techniques.

@ donaldt, As Matt advises situation should now be resolved, Wait and do updates when they become available and remember to mark this thread as "solved"; aids all in look'n at solutiuons.[INDENT]
Good things do happen

[/INDENT]

---

### Post by donaldt on 2013-03-02
Thank you, sir, for the good advice and also for your diligence in getting my update manager working (at least we think it is working.  I'm still standing by for new updates to try it out).

Your help and expertise is very much appreciated.  I'll be sure to mark it solved as soon as it is "testable".

donaldt

---

### Post by donaldt on 2013-03-04
Greetings to all,

Sorry to report NO CHANGE in update manager.  Only 3 updates showed up, but they stalled once again in the middle of the install process.  Same problem with the update manager program freezing up and needing to re-boot.

I went back to:  [sudo apt-get update && sudo apt-get dist-upgrade]  After running this command in terminal, I went back to the 3 updates (they were still there in update manager) and clicked on update and they all installed normally.

In other words, we did a lot of file changes, but nothing has changed with the original problem.

Sorry to report the bad news!  Don't shoot the messenger...

donaldt

---

### Post by Bashing-om on 2013-03-04
donaldt; shucks ....

Ok back up 2 yards and punt. Let's see what your sources.list file and sources.list.d directory hold.

Post your updated /etc/apt/sources.list and the directory contents.
```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
```[INDENT=2]
solid foundations are important

[/INDENT]

---

### Post by matt_symes on 2013-03-05
Hi

Next time it offers you updates click cancel (don't install them).

Open a terminal and type

```
update-manager
```

This will run it from the terminal and hopefully give us some debug information.

Post that information back here.

Kind regards

---

### Post by donaldt on 2013-03-05
Okay.  Here is the sources list:

donald@donald-Aspire-3810T:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main #Third party developers repository


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse #deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

# deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) precise-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
# deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) precise-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
# deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) precise-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) precise-updates restricted main universe multiverse
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
# deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
donald@donald-Aspire-3810T:~$ 

And here is the @.list:

donald@donald-Aspire-3810T:~$ cat /etc/apt/sources.list.d/*.list
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
donald@donald-Aspire-3810T:~$ 

I will try the update-manager trick as soon as I get the next load of updates.


Let me know what else I need to try.  

Thanks!

donaldt

---

### Post by matt_symes on 2013-03-05
Hi

Try disabling all the ppa's, especially this one....

> deb [https://private-ppa.launchpad.net/co...aserver/ubuntu]("https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu") precise main #Added by software-center;

The ppa wants a password and that may very well cause update-manabger to hang.

Kind regards

---

### Post by donaldt on 2013-03-06
OK, back for another try.

I tried running update manager from the terminal.  [update-manager]  That opened it.  I hit install and once again it stalled about half way through.  I killed it in terminal.  When I re-opened update manager, all of the same 5 updates are still shown as downloaded and available for installation.  

I tried to get gksudo to open the files with ppa but can't seem to get to the right files so I can comment them out.  I probably need a better command to open the proper list.

I will leave the updates downloaded but not installed so we can try whatever else is needed.

Any thoughts?

donaldt

---

### Post by matt_symes on 2013-03-06
Hi

Did you disable the ppa i highlighted in post #26 ?

When i click on the link in firefox it is asking for a password. This may be stalling update-manager.

Kind regards

---

### Post by schragge on 2013-03-06
@**donaldt**
If you have trouble disabling the PPA, try this:
```

sudo sed -i -e '/plexmediaserver/s/^deb/# deb/' /etc/apt/sources.list.d/*.list

```
@**Bashing-om**
[SIZE=-1][COLOR=grey]That's why I prefer *grep* over *cat*: besides the output being more concise, it would give you the file name. Here we only have three of them in */etc/apt/sources.list.d/* and the string *plexmediaserver* only occurs once, so **.list* is safe, but I wouldn't do it on a directory with lots of PPAs.[/COLOR][/SIZE]

---

### Post by donaldt on 2013-03-06
I tried the sudo command in terminal.  Nothing happens.  It returns me to the command line.

donaldt

---

### Post by schragge on 2013-03-06
So it should. Now, run ```
update-manager
```

---

### Post by donaldt on 2013-03-06
I launched update-manager again from the terminal (after using your sudo command) and it locks up even earlier now.  It is stuck on "applying changes".  I'll cancel out and see where it goes.

It just goes back to update manager.  All of the 5 downloads are still "downloaded but not installed" as before.

Thanks for trying!

donaldt

---

### Post by donaldt on 2013-03-06
Hello again

I finally got editing access to the file and hashed out the 3 ppa lines, as suggested by Matt.  I then tried [sudo apt-get update && sudo apt-get dist-upgrade]  I got this from terminal:

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
donald@donald-Aspire-3810T:~$ 

Is this because I am using part of the resource it is looking for?  I'm still stumped and unable to use update manager.

Thanks!

donaldt

---

### Post by matt_symes on 2013-03-06
Hi

```
/var/lib/apt/lists/lock
```

That is because dpkg is running and has a lock on the file. A reboot is the easiest way to fix it.

```
sudo sed -i -e '/google/s/^deb/# deb/' /etc/apt/sources.list.d/*.list
```

```
sudo apt-get clean
```

```
sudo rm -rf /var/lib/apt/lists/*
``` ```
gksudo update-manager
```

Post back any terminal output from the last command.

The only other thing i can suggest is running an strace on update manager when yu have updates.

```
sudo strace -o ~/tmp.txt update-manager
```

The above command will run update-manager. Run update manager as normal up to when it hangs. kill update manager.

The above command will produce a file in your home directory called tmp.txt.

```
tail -n500 ~/tmp.txt > tmp2.txt
```

This will get the last 500 line.

```
zip update-mgr tmp2.txt
```

This will create a file called update-mgr.zip.

Post the zip file here.

Kind regards

---

### Post by donaldt on 2013-03-07
Good morning,

Back at trying to cure update manager.

I got nothing back in terminal from your command:  gksudo update-manager

I found 5 new updates on update manager and so I ran this command:  sudo strace -o ~/tmp.txt update-manager

Update manager started and ran to the end of this line:   /tmp/tmppuf4gs (end)

I tried 3 commands to kill it but none of the 3 worked.  It is still sitting on my desk top, but now that I have finished this message I will do a re-start and will expect update manager to retain the 5 updates when we re-start. 

I hope this is clear and will be of some help.  If not, let me know if I need to clarify.

donaldt

---

### Post by donaldt on 2013-03-07
OK, back from re-boot.  Update Manager now shows 7 updates available.  Harking back to my original problem, I believe I can still go to terminal and use this command:  [sudo apt-get update && sudo apt-get upgrade]

This is how I was able to use update manager for the past 6 months before I started down this path to fix the program.  If I run this first, update manager will still have all the original updates listed as available; and clicking on update will install them without any problem.

I believe I should now try this once again and see if that still works.  Is there any reason doing so would be a problem for continued trouble shooting?

Thanks!

donaldt

---

### Post by donaldt on 2013-03-07
OK, all of the changes we have made have not killed the ability to make update manager work via terminal.  This command:  [sudo apt-get update && sudo apt-get upgrade]  run in terminal does something (all I have to do is choose "yes" to continue) that allows update manager to work as it should.  I don't know what that is, but it works.

First, I ran the terminal program and after closing it down, opened update manager and it completed a total of 12 updates flawlessly and without hesitation and now my computer is once again, officially, up to date on all downloads.

I don't know if this helps, but that is where we are.

donaldt

---

### Post by donaldt on 2013-03-08
Friday morning,

Today there were more new updates to install.  I ran update manager with your command (sudo trace) and it ran.  It stopped in the middle and once again it would not die with the two commands, so here is what it shows in terminal:

donald@donald-Aspire-3810T:~$ sudo strace -o ~/tmp.txt update-manager
[sudo] password for donald: 
Home directory /home/donald not ours.
Home directory /home/donald not ours.
Home directory /home/donald not ours.
Home directory /home/donald not ours.
Home directory /home/donald not ours.
sudo killall update-manager
sudo kill $(pgrep update-manager)

I'll try to copy where we are in update manager and post that if I can, then will do a re-boot to get rid of update manager.

Tried but can't copy the update manager screen.  Going down with re-boot.


donaldt

---

### Post by donaldt on 2013-03-10
Anyone still willing to help with my update manager issues?  I had a lot of ideas passed along earlier, but they seem to have dried up.  Would still appreciate any help from any source.

Thanks!

donaldt

---

### Post by arpanaut on 2013-03-10
> Home directory /home/donald not ours.

Looks like some permission problem with your /home directory
Post the results of this command.
```
ls -l
```

But I have never seen that error before.
Seems unusual, Have you used chmod or chown on any of your home or system directories?

---

### Post by Bashing-om on 2013-03-10
donaldt;
Still hang'n in there with you and the others helping you. Your attention is invited to          arpanaut;s response.
Mine is the same, I have never seen such an error and had no idea as to how to proceed.          arpanaut's approach is reasonable. See if the advise clears up that issue.[INDENT=2]
try'n to help


[/INDENT]

---

### Post by donaldt on 2013-03-10
Here is the output from your  ls -l command:

total 1258088
-rw-rw-r--  1 donald donald         0 May 28  2012 192.168.1.11
drwx------  4 donald donald      4096 Jan 27  2012 AMUR
-rw-r--r--  1 donald donald      1844 Apr 12  2010 beatles.m3u
-rw-r--r--  1 donald donald      1844 Apr 12  2010 Beatles.m3u
drwxr-xr-x  2 donald donald      4096 Jun 25  2010 bin
-rw-r--r--  1 donald donald     20992 May 28  2012 Bio_2011_Don Taylor.doc
-rw-------  1 donald donald    187254 May 24  2008 biz card 4.bmp
-rw-------  1 donald donald 632603328 Feb 11 15:16 brasero-0.bin
-rw-------  1 donald donald      1789 Feb 11 15:16 brasero-0.cue
-rw-r--r--  1 donald donald   3112960 Jun 16  2010 brasero-0.iso
-rw-r--r--  1 donald donald    133120 Aug 24  2010 brasero-1.iso
-rw-r--r--  1 donald donald    133120 Aug 24  2010 brasero-2.iso
-rw-r--r--  1 donald donald    133120 Aug 24  2010 brasero-3.iso
-rw-------  1 donald donald 632603328 Feb 11 15:04 brasero.bin
-rw-------  1 donald donald      1787 Feb 11 15:04 brasero.cue
-rw-r--r--  1 donald donald   3112960 Jun 11  2010 brasero.iso
-rw-r--r--  1 donald donald     18432 Oct  8  2011 Buyers Agent Agreement.doc
-rw-r--r--  1 root   root           0 Mar  6 15:32 cat
-rw-r--r--  1 donald donald     22528 Apr  4  2010 Class _of_48.doc
-rw-r--r--  1 donald donald    358522 May  7  2012 C:\nppdf32Log\debuglog.txt
drwxr-xr-x 11 donald donald      4096 Mar 10 10:18 Desktop
drwxr-xr-x  3 donald donald      4096 Feb 25 13:11 Documents
drwxr-xr-x  3 donald donald      4096 Dec  9 08:13 Downloads
drwxr-xr-x  2 donald donald      4096 Dec 27  2011 dropbox
-rw-r--r--  1 donald donald         0 Apr 20  2010 evo.log
-rw-r--r--  1 donald donald       167 Dec 29  2009 examples.desktop
-rw-r--r--  1 donald donald     30819 Jan  2  2012 Firefox_wallpaper.png
-rw-r--r--  1 root   root           0 Mar  6 15:32 gedit
-rw-r--r--  1 root   root           0 Mar  6 15:32 gksudo
drwxrwxrwx  8 donald donald      4096 Jul 19  2010 gtkpod-1.0.0
-rw-rw-r--  1 donald donald     12888 Oct 22  2009 hard_light.ttf
-rw-r--r--  1 donald donald    397448 Jan 25  2011 hpsc4.pdf
-rw-r--r--  1 donald donald     43173 Jun 11  2010 inbox.txt
-rw-r--r--  1 donald donald     56751 Dec 10  2011 installed-software
lrwxrwxrwx  1 donald donald        34 Dec  6 10:18 Link to Firefox_wallpaper.png -> /home/donald/Firefox_wallpaper.png
drwx------ 13 donald donald      4096 Feb 11 14:23 Memorex_1G_USB
-rw-r--r--  1 donald donald       569 Mar 27  2010 more atunes.m3u
-rw-r--r--  1 donald donald         0 Mar 20  2010 msic084.tmp
-rw-r--r--  1 donald donald         0 Mar 20  2010 msic672.tmp
-rw-r--r--  1 donald donald         0 Mar 20  2010 msic6a2.tmp
drwxr-xr-x  2 donald donald     12288 Nov 22 13:07 Music
drwx------  2 donald donald      4096 May 29  2012 PDF
drwxr-xr-x  2 donald donald      4096 May  9  2011 Photo folder
drwxr-xr-x  5 donald donald      4096 May 21  2012 Pictures
drwxr-xr-x  2 donald donald      4096 Dec 29  2009 Public
-rw-rw-r--  1 donald donald    254381 Sep 10 16:23 Quabain.pdf
-rw-r--r--  1 donald donald       365 Mar 27  2010 random aTunes songs.m3u
drwxr-xr-x  3 donald donald      4096 Jan 23  2012 scandocs_#214
-rw-r--r--  1 donald donald      1538 Mar 27  2010 still more atunes.m3u
drwxr-xr-x  2 donald donald      4096 Dec 29  2009 Templates
-rw-r--r--  1 root   root        3872 May 12  2010 testdisk.log
-rw-r--r--  1 root   root    13568059 Mar  8 08:58 tmp.txt
drwxrwxr-x  2 donald donald      4096 Apr 27  2010 Ubuntu One
drwx------  4 donald donald      4096 Jan 27  2012 UHWW_summer_2011
drwxrwxr-x  2 donald donald      4096 Sep 15 16:11 Untitled Folder
drwxr-xr-x  2 donald donald      4096 Nov 28 16:31 Videos
drwxr-xr-x  3 donald donald      4096 Jun 11  2011 VirtualBox VMs
drwxr-xr-x  2 donald donald      4096 Feb 25  2010 WAC photos
donald@donald-Aspire-3810T:~$ 

I have never knowingly used chmod or chown on my home files.

Thanks!

donaldt

---

### Post by schragge on 2013-03-11
Well, the right command here would be not *ls -l*, but *ls -ld* or *ls -l /home*. Anyway, try
```
sudo chown donald: .
```
There are also some files owned by root in your home directory. To change ownership of them, try
```
sudo chown donald: *
``` Some of those files were clearly created by mistake, after changing their ownership, you may as well remove them:
```
rm cat gedit gksudo
```

---

### Post by donaldt on 2013-03-11
I will try that and wait for more updates to see if anything changes.

Thanks for the help!

donaldt

---

### Post by donaldt on 2013-03-11
I just had 3 updates show up in update manager, so I tried it again.  There is no change.  When I click update it locks up update manager about 50% toward completion.


Basically, nothing has changed with update manager for all the file examining and checking of files we have done so far.

What is next??

thanks,

donaldt

---

### Post by schragge on 2013-03-12
I noticed there's tmp.txt in your home folder. I guess it's the output of *strace*. Could you please proceed with the file like **matt_symes** suggested in [post=12545241]that post[/post], and make its contents available to us?

---

### Post by donaldt on 2013-03-12
Per your request, here is the output requested in that post:

donald@donald-Aspire-3810T:~$ sudo sed -i -e '/google/s/^deb/# deb/' /etc/apt/sources.list.d/*.list
[sudo] password for donald: 
donald@donald-Aspire-3810T:~$ sudo apt-get clean
donald@donald-Aspire-3810T:~$ sudo rm -rf /var/lib/apt/lists/*
donald@donald-Aspire-3810T:~$ 
donald@donald-Aspire-3810T:~$ gksudo update-manager

Update manager opened, but there were no updates available, so it just said the software on this computer is up to date

donaldt

---

### Post by schragge on 2013-03-12
Sorry, I meant the last part of Matt's post, i.e.
```
tail -n500 ~/tmp.txt > tmp2.txt
```
```
zip update-mgr tmp2.txt
```
and posting update-mgr.zip here as an attachment.

---

### Post by donaldt on 2013-03-12
OK, I found that file in the home directory.  I zipped it.  Here is the link.


file:///home/donald/Desktop/update-mgr.zip

---

### Post by Bashing-om on 2013-03-12
donaldt; As I continue to monitor this thread;
The file "file:///home/donald/Desktop/update-mgr.zip 		"
needs to be posted to this thread as an "attachment" so that the file is downladed to the thread,[INDENT=2]my small effort to help

[/INDENT]

---

### Post by donaldt on 2013-03-12
I thought I uploaded it as an attachment.  I shall try again.

donaldt

---

### Post by donaldt on 2013-03-13
I tried once more to attach the update-magr.zip file.  I'll see if it works this time.

donaldt

---

### Post by schragge on 2013-03-13
Yep, it's worked.

FYI, LP#[lpbug]1014888   [/lpbug]. From the bug description on LP it looks like another aptdaemon problem. Next time when update-manager stucks, try to run this (no sudo needed, run it as a regular user)
```
aptdcon -d --upgrade-system
```Another thing to try is starting aptdaemon directly from a terminal in debug mode and capturing its output while running update manager:
```
sudo aptd --debug --replace --disable-timeout
```Then start update-manager and watch the messages in terminal window running aptd, specifically, those that are being shown there after pressing *Install Updates* button in update-manager.

A somewhat related question: aptdaemon is a python app. There's a possibility that some another python application interferes with it. Could you please post the output of the following:
```
dpkg -l|grep -o '^i.. *python[^ ]*'
```This will show all python modules installed on your system.

---

### Post by donaldt on 2013-03-13
I found 11 updates available in update manager.  Setting that aside, I tried the commands you suggested above.  Update Manager stalls 1/2 way through, just as before.  I was unable to shut it down from terminal, which was still accessible, but the commands did nothing.  

I needed to re-boot to kill update manager, so I did that and when I re-started all of the original 11 updates were still available.

I tried your other commands and nothing happened.  Here is the output of :
Code:  dpkg -l|grep -o '^i.. *python[^ ]*

donald@donald-Aspire-3810T:~$ dpkg -l|grep -o '^i.. *python[^ ]*'
ii  python
ii  python-appindicator
ii  python-apport
ii  python-apt
ii  python-apt-common
ii  python-apt-dbg
ii  python-apt-doc
ii  python-aptdaemon
ii  python-aptdaemon.gtk3widgets
ii  python-aptdaemon.pkcompat
ii  python-brlapi
ii  python-cairo
ii  python-central
ii  python-chardet
ii  python-compizconfig
ii  python-configglue
ii  python-crypto
ii  python-cups
ii  python-cupshelpers
ii  python-dateutil
ii  python-dbg
ii  python-dbus
ii  python-dbus-dev
ii  python-debian
ii  python-debtagshw
ii  python-defer
ii  python-dirspec
ii  python-egenix-mxdatetime
ii  python-egenix-mxtools
ii  python-gconf
ii  python-gdata
ii  python-gdbm
ii  python-germinate
ii  python-gi
ii  python-gi-cairo
ii  python-glade2
ii  python-gnomekeyring
ii  python-gnupginterface
ii  python-gobject
ii  python-gobject-2
ii  python-gst0.10
ii  python-gtk2
ii  python-httplib2
ii  python-ibus
ii  python-imaging
ii  python-keyring
ii  python-launchpadlib
ii  python-lazr.restfulclient
ii  python-lazr.uri
ii  python-libproxy
ii  python-libxml2
ii  python-louis
ii  python-mako
ii  python-markupsafe
ii  python-minimal
ii  python-notify
ii  python-oauth
ii  python-openssl
ii  python-packagekit
ii  python-pam
ii  python-pexpect
ii  python-piston-mini-client
ii  python-pkg-resources
ii  python-problem-report
ii  python-protobuf
ii  python-pyatspi2
ii  python-pycurl
ii  python-pyinotify
ii  python-qt4
ii  python-qt4-dbus
ii  python-renderpm
ii  python-reportlab
ii  python-reportlab-accel
ii  python-serial
ii  python-simplejson
ii  python-sip
ii  python-smbc
ii  python-software-properties
ii  python-speechd
ii  python-support
ii  python-twisted-bin
ii  python-twisted-core
ii  python-twisted-names
ii  python-twisted-web
ii  python-ubuntu-sso-client
ii  python-ubuntuone-client
ii  python-ubuntuone-control-panel
ii  python-ubuntuone-storageprotocol
ii  python-uno
ii  python-virtkey
ii  python-vte
ii  python-wadllib
ii  python-xapian
ii  python-xdg
ii  python-xkit
ii  python-zeitgeist
ii  python-zope.interface
ii  python2.7
ii  python2.7-dbg
ii  python2.7-minimal
ii  python3
ii  python3-apt
ii  python3-minimal
ii  python3.2

---

### Post by donaldt on 2013-03-13
donald@donald-Aspire-3810T:~$ aptdcon -d --upgrade-system
The following packages will be upgraded (11):                                   
  apt-doc=0.8.16~exp12ubuntu10.9 apt-transport-https=0.8.16~exp12ubuntu10.9
  apt-utils=0.8.16~exp12ubuntu10.9 apt=0.8.16~exp12ubuntu10.9
  libapt-inst1.4=0.8.16~exp12ubuntu10.9 libapt-pkg4.12=0.8.16~exp12ubuntu10.9
  thunderbird-globalmenu=17.0.4+build1-0ubuntu0.12.04.1
  thunderbird-gnome-support=17.0.4+build1-0ubuntu0.12.04.1
  thunderbird-locale-en-us=1:17.0.4+build1-0ubuntu0.12.04.1
  thunderbird-locale-en=1:17.0.4+build1-0ubuntu0.12.04.1
  thunderbird=17.0.4+build1-0ubuntu0.12.04.1
The following package has been kept back (1):
  libpurple0=1:2.10.3-1~getdeb1
After this operation, 13.3 kB of additional disk space will be used.
Do you want to continue [Y/n]?y
[\]   0% Waiting

---

### Post by donaldt on 2013-03-13
More readouts as requested.  I now have a "crash report" on my screen.  Update Manager will not launch, it is stuck right after hitting "install updates".  I will cancel it out to save the updates for further experimentation.

Are we learning anything?

donaldt


donald@donald-Aspire-3810T:~$ sudo killall update-manager
[sudo] password for donald: 
donald@donald-Aspire-3810T:~$ sudo aptd --debug --replace --disable-timeout
16:34:43 AptDaemon [INFO]: Initializing daemon
16:34:43 AptDaemon [WARNING]: Replacing already running daemon
Traceback (most recent call last):
  File "/usr/sbin/aptd", line 28, in <module>
    aptdaemon.core.main()
  File "/usr/lib/python2.7/dist-packages/aptdaemon/core.py", line 2203, in main
    daemon = AptDaemon(options, bus=bus)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/core.py", line 1397, in __init__
    do_not_queue=True)
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 142, in __new__
    raise NameExistsException(name)
dbus.exceptions.NameExistsException: Bus name already exists: org.debian.apt
donald@donald-Aspire-3810T:~$

---

### Post by Bashing-om on 2013-03-13
Pardon me if I am interrupting, on the installed python modules the output on my system has some differences. I am running 12.04.1 on AMD64, standard install fully updated - and most significant is I do not have the latter python3 versions installed. This for comparison IRT python module conflicts. (donaldt is running 32 bit)

---

### Post by donaldt on 2013-03-13
Bashing-om,

We may be comparing apples and oranges, but thanks for the suggestion.  Any help at all is appreciated.

donaldt

---

### Post by schragge on 2013-03-14
Thank you, **Bashing-om**, your input is very welcome here.
Well, python3 is certainly not required to run your system as default python on precise is 2.7. *python3-apt* is even more suspicious. I don't run Ubuntu myself, but on my system (Debian wheezy) the only two packages that require it, *wajig* and *germinate*, are certainly not part of the standard install. Looks like you have [wajig]("http://manpages.ubuntu.com/manpages/precise/en/man1/wajig.1.html") installed. Don't get me wrong, *wajig* is a very nice tool, I used it myself in the past when *apt-get* and *aptitude* were not so poweful as they are now, but are you really using it? Anyway, for the sake of clarity, let's try removing the python3 stuff. You can reinstall it later if it's not guilty.
```
sudo apt-get remove wajig ^python3
```

---

### Post by donaldt on 2013-03-14
Up and after the update manager again...

This morning I removed the python 3 files.  My update manager had by then accumulated more updates, 15 to be exact.  After the removal I tried an update and it still stalled out.  Update Manager always goes through a list of names and after charles coulsen at canonical it says "end".  Today I was able to kill update manager with "killall" in terminal.

After killing the application, if I try update manager again, it will not check the updates or even start updating the applications.  It just stops.  I don't know if this is important, but want to provide any data that might help.  

Standing by for more wisdom from online...

Thanks for the help!

donaldt

---

### Post by donaldt on 2013-03-16
This is week 4 of trying to cure the problem with my Update Manager.  I've had help, but now it seems my helpers have lost interest.  Anyone care to tackle the problem of a broken update manager?  My problem is the same as at the beginning of this thread.

Thanks if you can help!

donaldt

---

### Post by donaldt on 2013-03-21
I need to get back on the first page.

The issue is an inoperative update manager on Ubuntu 12.04, 32bit.  Lot's of help early on and much background information earlier in this thread, but none of late.  

Can anyone please help get the program working again?  

donaldt

---

### Post by Bashing-om on 2013-03-21
donaldt;

I am still here... but to be honest I do not know how to fix your update manager //This has already progressed beyond my ability/knowledge.
With the bump perhaps the thread will be picked back up.[INDENT=2]
I do wish I had the ability to help further.
[/INDENT]

---

### Post by matt_symes on 2013-03-22
Hi

I have not been on the forums much over the last couple of weeks, that is why i have not responded.

From your strace output
```

clock_gettime(CLOCK_MONOTONIC, {55180, 44940362}) = 0
sendmsg(3, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\0\1\"\0\0\0\2\0\0\0\177\0\0\0\1\1o\0\25\0\0\0/org/fre"..., 144}, {"\35\0\0\0org.freedesktop.UpdateManage"..., 34}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 178
clock_gettime(CLOCK_MONOTONIC, {55180, 45232997}) = 0
poll([{fd=3, events=POLLIN}], 1, 25000) = 1 ([{fd=3, revents=POLLIN}])
recvmsg(3, {msg_name(0)=NULL, msg_iov(1)=[{"l\2\1\1\t\0\0\0\3\0\0\0=\0\0\0\6\1s\0\4\0\0\0:1.4\0\0\0\0"..., 2048}], msg_controllen=0, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 89
write(4, "\1\0\0\0\0\0\0\0", 8)         = 8
recvmsg(3, 0xbfd50738, MSG_CMSG_CLOEXEC) = -1 EAGAIN (Resource temporarily unavailable)
clock_gettime(CLOCK_MONOTONIC, {55180, 45725309}) = 0
sendmsg(3, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\0\1\0\0\0\0\3\0\0\0\203\0\0\0\1\1o\0$\0\0\0/org/fre"..., 152}, {"", 0}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 152
clock_gettime(CLOCK_MONOTONIC, {55180, 46591272}) = 0
poll([{fd=3, events=POLLIN}], 1, 25000) = 1 ([{fd=3, revents=POLLIN}])
recvmsg(3, {msg_name(0)=NULL, msg_iov(1)=[{"l\2\1\1\204\2\0\0\5\0\0\0-\0\0\0\6\1s\0\4\0\0\0:1.4\0\0\0\0"..., 2048}], msg_controllen=0, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 708
write(4, "\1\0\0\0\0\0\0\0", 8)         = 8
recvmsg(3, 0xbfd50bf8, MSG_CMSG_CLOEXEC) = -1 EAGAIN (Resource temporarily unavailable)
time(NULL)                              = 1363115580
clock_gettime(CLOCK_MONOTONIC, {55180, 47418612}) = 0
sendmsg(3, {msg_name(0)=NULL, msg_iov(2)=[{"l\1\0\1\0\0\0\0\4\0\0\0\205\0\0\0\1\1o\0$\0\0\0/org/fre"..., 152}, {"", 0}], msg_controllen=0, msg_flags=0}, MSG_NOSIGNAL) = 152
clock_gettime(CLOCK_MONOTONIC, {55180, 57013546}) = 0
poll([{fd=3, events=POLLIN}], 1, 25000) = 1 ([{fd=3, revents=POLLIN}])
recvmsg(3, {msg_name(0)=NULL, msg_iov(1)=[{"l\2\1\1\4\0\0\0\6\0\0\0-\0\0\0\6\1s\0\4\0\0\0:1.4\0\0\0\0"..., 2048}], msg_controllen=0, msg_flags=MSG_CMSG_CLOEXEC}, MSG_CMSG_CLOEXEC) = 68
write(4, "\1\0\0\0\0\0\0\0", 8)         = 8
recvmsg(3, 0xbfd50558, MSG_CMSG_CLOEXEC) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGINT, {SIG_DFL, [], 0}, {0x8148260, [], 0}, 8) = 0
exit_group(0)                           = ?
```

It seems to be trying to get the bus org.freedesktop.UpdateManager from dbus. It is getting a response but i don't know if this response is valid or not.

Either way, if you check the output from clock_gettime(), this seems to be where it is hanging.

I don't know much about update manager as i never use it, but i am having a look at the code to try to see what is going on.

Did you ever try purging and reinstalling update-manager ?

Kind regards

---

### Post by schragge on 2013-03-22
Unfortunately, I don't use update-manager either. From the output of strace above it's not clear what responses update-manager gets from DBus as only the first 32 characters are preserved. So, maybe try strace once again, this time only on sendmsg and recvmsg calls, but with string size increased to say 256:
```

sudo strace -s256 -e trace=sendmsg,recvmsg -o ~/tmp.txt update-manager

```

---

### Post by donaldt on 2013-03-22
All,

Thanks for the help!  I tried removing and re-installing update manager.  I should have thought of that long ago, but unfortunately, that didn't change anything.

I will try some of the other suggestions.

donaldt

---

### Post by Bashing-om on 2013-03-22
all:

I too had considered (re)installing update manager, but do not know how deeply ingrained it is into the kernel. What procedure would one employ if apt-get were not available to obtain the updates for (re)installation ?-> LiveCD and chroot ?

Thus far this thread has taught me lots - a primary reason I frequent and support this forum.

I would appreciate some enlightenment to my experience.

---

### Post by schragge on 2013-03-22
> **Bashing-om said:**
> What procedure would one employ if apt-get were not available to obtain the updates for (re)installation ?-> LiveCD and chroot ?If only apt-get is unavailable, but the rest of the system works, I'd download deb packages with wget or through the web browser and install them with dpkg. Usually it's only a couple of packages that need to be (re-)installed. The hard part is to find out which they are.

---

### Post by schragge on 2013-03-22
Just for reference, I also want to post this link: [uwiki]DebuggingUpdateManager#Debugging_Procedures[/uwiki]

---

### Post by donaldt on 2013-03-22
All,

Below the results of the "sudo strace...command.

After this, it launched update manager in it's still non functioning state

donald@donald-Aspire-3810T:~$ sudo strace -s256 -e trace=sendmsg,recvmsg -o ~/tmp.txt update-manager
[sudo] password for donald: 
Home directory /home/donald not ours.
Home directory /home/donald not ours.
Home directory /home/donald not ours.
Home directory /home/donald not ours.
Home directory /home/donald not ours.
Home directory /home/donald not ours.
Home directory /home/donald not ours.
Home directory /home/donald not ours.
donald@donald-Aspire-3810T:~$

---

### Post by schragge on 2013-03-22
First this > **donaldt said:**
> Home directory /home/donald not ours. Just to be sure, please post the output of
```
ls -ld ~
``` I hope those messages are really not result of wrong permissions/ownership, but just a manifestation of running update-manager with sudo.

Secondly, please reduce, compress and upload the new results of strace (tmp.txt) as described in [post=12554386]that post[/post]

---

### Post by donaldt on 2013-03-22
donald@donald-Aspire-3810T:~$ ls -ld ~
drwxr-xr-x 104 donald donald 12288 Mar 22 10:00 /home/donald
donald@donald-Aspire-3810T:~$

---

### Post by donaldt on 2013-03-23
[ATTACH]240453[/ATTACH][ATTACH]240453[/ATTACH]

---

### Post by matt_symes on 2013-03-23
Hi

Well i have to say i'm really not sure what is going on in your system.

The second trace you posted looks different from the first. 

One thing of note is that it is never using the dbus apt interface. I would expect to see some references to

```

org.debian.apt
org.debian.apt.transaction
```

Can you post the output of

```
dpkg -l python-aptdaemon
```

It's not often i say this (in fact very, very infrequently) but it may be a quicker fix to back up your data and reinstall as i don't think the people helping you in this thread are that familiar with update manager and nobody else more familiar with it has jumped in to help.

Post the output of the above command first though.

Kind regards

---

### Post by donaldt on 2013-03-23
Here is the post you requested:

donald@donald-Aspire-3810T:~$ dpkg -l python-aptdaemon
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  python-aptdaem 0.43+bzr805-0u Python module for the server and client of a
donald@donald-Aspire-3810T:~$ 

Since our last session, I purged and re-installed update-manager again, but nothing changed.

I have been looking at the upgrade to 12.10, available on update-manager for the past few months.  Would it be a good idea to upgrade and see if it clears up the problem?  Or is it best to re-install from a CD?

Your diligence in chasing this problem is much appreciated.

Thanks a lot!

donaldt

---

### Post by matt_symes on 2013-03-24
Hi

> Would it be a good idea to upgrade and see if it clears up the problem?

You could certainly trying upgrading your current installation. You can do this from the command line.

Close any open programs you may have open. Press CTRL + ALT + F1 at the same time to get to a console.

Login by typing your user name and password. Then type...

```
sudo service lightdm stop
```

The above command will stop X. Then type...

```
sudo do-release-upgrade
```

That should kick off the update process and update to 12.10 for you.

If that does not fix the update-manager issue then backup your data and perform a fresh install.

Kind regards

---

### Post by donaldt on 2013-03-24
Matt,

I decided to try the update to 12.10.  I got as far as stopping X, but [sudo do-release-upgrade] said command not found, so no upgrade from the terminal.  BTW, I used synaptic package manager to remove update-manager and associated files, so they are no longer on my computer.

Thanks!

donaldt

---

### Post by schragge on 2013-03-24
Command *do-release-upgrade* is provided by package *update-manager-core*, so if you removed that package, it wouldn't work.

---

### Post by matt_symes on 2013-03-24
Hi

There is another method you can use to upgrade from the terminal.

Stop X as before. Then from a console (CTRL + ALT + F1)

```
sudo sed -i 's/precise/quantal/g' /etc/apt/sources.list{,.d/*}
```

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

Kind regards

---

### Post by donaldt on 2013-03-25
Matt,

I did your upgrade.  It went ok last night, but this morning there was a big bunch of updates to install. They took 1:30 to install and then the system crashed.  This message is coming from my IPad as I cannot get past the wallpaper page.  The page is devoid of anything except the background.  Also, i see references to 64 bit and I have been running a 32 bit system.

Can you point me to a way out of this??

Thanks

donaldt

---

### Post by matt_symes on 2013-03-25
Hi

Honestly after all the troubles you have had, backup and reinstall.

You're very unlikely to get this fixed via forum help. You'll need someone at your computer to actually see what is going on without the issue of time zones, miscommunication and lack of immediacy.

Upgrades are never guaranteed to be 100% successful and as you had problems before that may have exacerbated the upgrade process and you still have problems then ......

Kind regards

---

### Post by donaldt on 2013-03-27
Matt_Symes,

Yes, you were right.  We had reached the stage where a re-install was appropriate.  Fortunately, prior to the crash of the update to 12.10 I had done a complete back-up of my system.  I did a live cd to re-install 12.04 and it went very well.  I'm now up and running with the new installation and have wireless and e-mail operating.  This is coming to you from the new 12.04 install.  Update Manager worked very well last night.  After installing the new system there were 527 updates waiting to be installed.  That took about 30 minutes, but they all worked and now I am up to date with an operative "Update Manager" program working again.

I don't believe we should list this as an issue that was "solved" (because it really never was) but the original issue is no longer valid and should be closed out.  One last question for you.  Can I selectively restore my backed up files?  There are some I would not restore if I had a way to do that.  I have an operating system, so am in no hurry to get everything restored from my previous back-up.

I owe you for your help.  You were the only one that stuck with me when the problem got tough and we were running out of ideas about what to do.  Thanks very much.  Haven't been to the UK for several years, but flew an Eclipse 500 twin jet from Geneva,Sw. to Oxford airport near London a few years back.  Spent two weeks there doing demo flights.  The Pub crawling was great!

Thanks again for your assistance!

donaldt

---

### Post by matt_symes on 2013-03-27
Hi

It's not very often i suggest a reinstall, but in this case i think it was the best option; especially as this issue had been going on for a month.

I am sure the problem was fixable without a reinstallation, however there did not seem to be a major pattern to the problem apart from the fact update manager was hanging. 

Getting the information to fix it may have been tough and as was stated we don't use update manager. Not a great help for you there :)

> Can I selectively restore my backed up files?

How did you backup your files ?

I'm also glad you enjoyed your stay in England :)

Kind regards

---

