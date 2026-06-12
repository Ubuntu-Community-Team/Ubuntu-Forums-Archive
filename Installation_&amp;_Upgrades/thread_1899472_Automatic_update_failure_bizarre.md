---
title: "Automatic update failure: bizarre"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by Total Noob on 2011-12-23
The update manager nagware finally got to me, so I tried - typing my password at the appropriate time -- only to have the update process crash and refuse to install the updates, with an error message saying the upgrades were not authorized.

How does Canonical send out automatic upgrades that won't take? I think it is pretty bizarre.

BTW, I tried on several occasions on the assumption that there was a transmission error with the upgrades, but it was useless. None of the five packages, including Chrome, would update for want of authorization.

Is there a workaround or is this just a lapse on the part of Canonical that can't be fixed?

Thanks.

---

### Post by dabl on 2011-12-23
Try it in a terminal with apt-get:

```
sudo apt-get update && sudo apt-get dist-upgrade
```


(make sure to shut down synaptic first)

---

### Post by Paddy Landau on 2011-12-23
Which version of Ubuntu are you using?

Please log out, log back in again, open a terminal, and type (or copy-and-paste) the following command.
```
sudo apt-get update && sudo apt-get upgrade
```Post the output here (between [FONT=Fixedsys][noparse]```
[/noparse][/FONT] and [FONT=Fixedsys][noparse]
```[/noparse][/FONT] tags, please).

---

### Post by Total Noob on 2011-12-23
> **Paddy Landau said:**
> Which version of Ubuntu are you using?

Please log out, log back in again, open a terminal, and type (or copy-and-paste) the following command.
```
sudo apt-get update && sudo apt-get upgrade
```Post the output here (between [FONT=Fixedsys][noparse]```
[/noparse][/FONT] and [FONT=Fixedsys][noparse]
```[/noparse][/FONT] tags, please).

That seemed to do it, at least no error messages. 

Definitely the hard way for me as I know little under the hood about this stuff, and it should not have taken advice to do a normal upgrade.

But thanks anyway.

Here's the output from the apt-get stuff.

```
Get:1 http://dl.google.com stable Release.gpg [198B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Get:2 http://dl.google.com stable Release.gpg [198B]                           
Ign http://dl.google.com/linux/earth/deb/ stable/main Translation-en           
Ign http://dl.google.com/linux/earth/deb/ stable/main Translation-en_US        
Get:3 http://us.archive.ubuntu.com maverick Release.gpg [198B]                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Get:4 http://archive.canonical.com maverick Release.gpg [198B]                 
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Get:5 http://dl.google.com stable Release.gpg [198B]                           
Get:6 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Get:7 http://security.ubuntu.com maverick-security Release.gpg [198B]          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en      
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Get:8 http://dl.google.com stable Release [1,347B]                             
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Get:9 http://archive.canonical.com maverick Release [5,925B]                   
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Get:10 http://dl.google.com stable Release [1,338B]                            
Get:11 http://dl.google.com stable Release [1,347B]                            
Get:12 http://dl.google.com stable/main i386 Packages [1,214B]                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Get:13 http://us.archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:14 http://dl.google.com stable/main i386 Packages [464B]                   
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Hit http://extras.ubuntu.com maverick/main Sources                             
Get:15 http://security.ubuntu.com maverick-security Release [31.4kB]           
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                              
Get:16 http://dl.google.com stable/main i386 Packages [765B]                   
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Get:17 http://archive.canonical.com maverick/partner i386 Packages [8,412B]    
Get:18 http://us.archive.ubuntu.com maverick-updates Release [31.4kB]          
Get:19 http://security.ubuntu.com maverick-security/main Sources [58.3kB]      
Hit http://us.archive.ubuntu.com maverick/main Sources                         
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Get:20 http://us.archive.ubuntu.com maverick-updates/main Sources [146kB]
Get:21 http://security.ubuntu.com maverick-security/restricted Sources [14B]
Get:22 http://security.ubuntu.com maverick-security/universe Sources [26.0kB]
Get:23 http://security.ubuntu.com maverick-security/multiverse Sources [1,760B]
Get:24 http://security.ubuntu.com maverick-security/main i386 Packages [204kB] 
Get:25 http://us.archive.ubuntu.com maverick-updates/restricted Sources [778B] 
Get:26 http://us.archive.ubuntu.com maverick-updates/universe Sources [55.0kB] 
Get:27 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:28 http://security.ubuntu.com maverick-security/universe i386 Packages [101kB]
Get:29 http://us.archive.ubuntu.com maverick-updates/multiverse Sources [2,513B]
Get:30 http://us.archive.ubuntu.com maverick-updates/main i386 Packages [397kB]
Get:31 http://security.ubuntu.com maverick-security/multiverse i386 Packages [3,756B]
Get:32 http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages [1,797B]
Get:33 http://us.archive.ubuntu.com maverick-updates/universe i386 Packages [184kB]
Get:34 http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages [5,213B]
Fetched 1,272kB in 3s (375kB/s)                         
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  acpid app-install-data-partner bzip2 google-chrome-stable libarchive1
  libbz2-1.0 libgweather-common libgweather1 libjasper1 libt1-5
  software-center
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 31.3MB of archives.
After this operation, 1,331kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable i386 16.0.912.63-r113337 [29.2MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main bzip2 i386 1.0.5-4ubuntu1.1 [47.3kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main libbz2-1.0 i386 1.0.5-4ubuntu1.1 [45.3kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main acpid i386 1.0.10-5ubuntu4.4 [47.3kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main app-install-data-partner all 12.10.10.4 [45.3kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main libarchive1 i386 2.8.4-1ubuntu0.10.10.1 [153kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main libjasper1 i386 1.900.1-7ubuntu0.10.10.1 [142kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main libt1-5 i386 5.1.2-3ubuntu0.10.10.1 [144kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main software-center all 3.0.11 [436kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main libgweather-common all 2.30.3-0ubuntu1.1 [1,010kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main libgweather1 i386 2.30.3-0ubuntu1.1 [43.9kB]
Fetched 31.3MB in 15s (2,040kB/s)                                              
(Reading database ... 218327 files and directories currently installed.)
Preparing to replace bzip2 1.0.5-4ubuntu1 (using .../bzip2_1.0.5-4ubuntu1.1_i386.deb) ...
Unpacking replacement bzip2 ...
Preparing to replace libbz2-1.0 1.0.5-4ubuntu1 (using .../libbz2-1.0_1.0.5-4ubuntu1.1_i386.deb) ...
Unpacking replacement libbz2-1.0 ...
Processing triggers for man-db ...
Setting up libbz2-1.0 (1.0.5-4ubuntu1.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 218327 files and directories currently installed.)
Preparing to replace google-chrome-stable 15.0.874.121-r109964 (using .../google-chrome-stable_16.0.912.63-r113337_i386.deb) ...
Unpacking replacement google-chrome-stable ...
Preparing to replace acpid 1.0.10-5ubuntu4.1 (using .../acpid_1.0.10-5ubuntu4.4_i386.deb) ...
acpid stop/waiting
Unpacking replacement acpid ...
Preparing to replace app-install-data-partner 12.10.10.3 (using .../app-install-data-partner_12.10.10.4_all.deb) ...
Unpacking replacement app-install-data-partner ...
Preparing to replace libarchive1 2.8.4-1 (using .../libarchive1_2.8.4-1ubuntu0.10.10.1_i386.deb) ...
Unpacking replacement libarchive1 ...
Preparing to replace libjasper1 1.900.1-7 (using .../libjasper1_1.900.1-7ubuntu0.10.10.1_i386.deb) ...
Unpacking replacement libjasper1 ...
Preparing to replace libt1-5 5.1.2-3build1 (using .../libt1-5_5.1.2-3ubuntu0.10.10.1_i386.deb) ...
Unpacking replacement libt1-5 ...
Preparing to replace software-center 3.0.10ubuntu0.1 (using .../software-center_3.0.11_all.deb) ...
Unpacking replacement software-center ...
Preparing to replace libgweather-common 2.30.3-0ubuntu1 (using .../libgweather-common_2.30.3-0ubuntu1.1_all.deb) ...
Unpacking replacement libgweather-common ...
Preparing to replace libgweather1 2.30.3-0ubuntu1 (using .../libgweather1_2.30.3-0ubuntu1.1_i386.deb) ...
Unpacking replacement libgweather1 ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for gnome-icon-theme ...
Processing triggers for python-support ...
Setting up bzip2 (1.0.5-4ubuntu1.1) ...
Setting up google-chrome-stable (16.0.912.63-r113337) ...
Setting up acpid (1.0.10-5ubuntu4.4) ...
Installing new version of config file /etc/acpi/powerbtn.sh ...
acpid start/running, process 10781
Setting up app-install-data-partner (12.10.10.4) ...
Setting up libarchive1 (2.8.4-1ubuntu0.10.10.1) ...
Setting up libjasper1 (1.900.1-7ubuntu0.10.10.1) ...
Setting up libt1-5 (5.1.2-3ubuntu0.10.10.1) ...
Setting up software-center (3.0.11) ...
Setting up libgweather-common (2.30.3-0ubuntu1.1) ...
Setting up libgweather1 (2.30.3-0ubuntu1.1) ...
Processing triggers for menu ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-central ...
```

---

### Post by Paddy Landau on 2011-12-24
Well, I have not seen those error messages ("Unknown media type in type 'all/allfiles'", etc.) before. Unfortunately, I don't know what they mean. Googling it, however, indicates that they are spurious messages and -- I believe -- you can ignore them.

Please run the command that I gave you again.

[LIST]
[*]If you still see errors, post them here.
[*]If there are no errors, run Update Manager again (there should be no more updates). Wait a couple of days until there are more updates, and post back here if you still get errors with Update Manager.
[/LIST]

---

### Post by Total Noob on 2012-01-22
> **Paddy Landau said:**
> Well, I have not seen those error messages ("Unknown media type in type 'all/allfiles'", etc.) before. Unfortunately, I don't know what they mean. Googling it, however, indicates that they are spurious messages and -- I believe -- you can ignore them.



I appreciated your help then and again now. 

This time, I tried a nagware update of 11.10 on a different computer with a different chip (not a Celeron) and still had a major install error that was very confounding -- the update was "not authenticated." Right from the maker, the update wouldn't even begin to launch and I needed to use the special typed instructions that you provided before to get the update in. 

 [[IMG]http://img172.imagevenue.com/loc588/th_59690_Screenshot_122_588lo.jpg[/IMG]](http://img172.imagevenue.com/img.php?image=59690_Screenshot_122_588lo.jpg)

It is messed up that Canonical can't send out a routine update that doesn't require a user to practically be a computer programmer knowledgeable in Unix code or force him to a forum once a month to get installed.

---

### Post by matt_symes on 2012-01-22
Hi

Have you added any PPA's ? Did you import their keys ?

Kind regards

---

### Post by Paddy Landau on 2012-01-22
> **Total Noob said:**
> It is messed up that Canonical can't send out a routine update that doesn't require a user to practically be a computer programmer knowledgeable in Unix code or force him to a forum once a month to get installed.
What you are seeing is quite different from what most people see. Therefore, there is something going on with your set-up that others don't have.

Let's see if we can figure it out, shall we?
> **matt_symes said:**
> Have you added any PPA's ? Did you import their keys?
The error message in your screen-shot indicates that this is possibly the case.

---

### Post by Total Noob on 2012-01-25
> **Paddy Landau said:**
> What you are seeing is quite different from what most people see. Therefore, there is something going on with your set-up that others don't have.

Let's see if we can figure it out, shall we?

The error message in your screen-shot indicates that this is possibly the case.

What is a PPA? How would I know if it is in or out? 

AFAIK, I didn't install anything on that computer that wasn't from the repository, if I installed anything at all. I'm not really handy enough with Linux to do that. So could the PPA, whatever it is, be a pollutant in the repository?

Plus, I have two installations with different versions of Ubuntu running and different computer manufacturers, ages, chips, and so on, both with the same grief. I don't know whether or not I put PPA on that one either, and am very confident I did not install any non-repository software in at least a year (Google Earth). 

What's up with that?

---

### Post by Paddy Landau on 2012-01-25
Looking at your screen shot, there is a "Details" button. That will give us much more information.

Please press the Details button. Highlight all the text, right-click and select Copy, then paste it here. (Or just post a screen-shot if the entire text fits in the window -- you can resize the window.)

Then we can see which PPA it is complaining about.

(To explain: A PPA is a *Personal Package Archive*; in other words a place where programs are stored so you don't have to download them as you would in, say, Windows. PPA's are *signed* to verify their validity. If you have a PPA for which you don't have a signature, it is *untrusted*. That is why the Update Manager is warning you. If you knew the PPA is valid, you could just go ahead anyway. But as you are not aware of adding any PPA, let's check in order to be certain.)

---

### Post by Total Noob on 2012-01-26
> **Paddy Landau said:**
> Looking at your screen shot, there is a "Details" button. That will give us much more information.

Please press the Details button. Highlight all the text, right-click and select Copy, then paste it here. (Or just post a screen-shot if the entire text fits in the window -- you can resize the window.)

Then we can see which PPA it is complaining about.



Would if I could, but will have to wait until next nag. I installed the last nagware using terminal (something I don't wish on my enemies b/c it is a PITA). 

Still wondering how someone can fall into this trap without knowing it, assuming your diagnosis is correct. Potentially a major flaw in a system supposedly intended to be noob friendly, if a noob user can go awry with no advance warning.

---

### Post by Paddy Landau on 2012-01-26
> **Total Noob said:**
> Would if I could, but will have to wait until next nag. I installed the last nagware using terminal (something I don't wish on my enemies b/c it is a PITA).
What nagware did you install? Why don't you uninstall it if you don't like it? Perhaps that is what is causing the problem.

> **Total Noob said:**
>  Still wondering how someone can fall into this trap without knowing it, assuming your diagnosis is correct. Potentially a major flaw in a system supposedly intended to be noob friendly, if a noob user can go awry with no advance warning.
We will find out what you did when we see the details.

---

### Post by Total Noob on 2012-04-03
> **Paddy Landau said:**
> Looking at your screen shot, there is a "Details" button. That will give us much more information.

Please press the Details button. Highlight all the text, right-click and select Copy, then paste it here. (Or just post a screen-shot if the entire text fits in the window -- you can resize the window.)

Then we can see which PPA it is complaining about.

(To explain: A PPA is a *Personal Package Archive*; in other words a place where programs are stored so you don't have to download them as you would in, say, Windows. PPA's are *signed* to verify their validity. If you have a PPA for which you don't have a signature, it is *untrusted*. That is why the Update Manager is warning you. If you knew the PPA is valid, you could just go ahead anyway. But as you are not aware of adding any PPA, let's check in order to be certain.)

Sorry, but I wasn't able to reproduce the phenomenon after installing the programs through the terminal. 

It worked for a while until I was again nagged to update. I am using 10.4 on a Celeron. 

I tried to install the current update and the download began and moments later I got an error message saying my Internet connection needed to be checked. It happened over and over despite the fact that I was on line normally before during and after attempts to install the update.

Could some of that have to do with the fact I'm now past the end of LTS? If so, then I'm disappointed because newer versions overpower that Celeron and if I'm not safe as possible with updates, then maybe my time with Ubuntu on that computer is done.

---

### Post by Paddy Landau on 2012-04-03
10.04 is still within its LTS. There is another year to go.

There is no "nagging" for updates. If you don't like automatic prompts for updates, just turn them off.

I am not sure what you have done to your system, but I think you need to start a new thread for your Internet connection problem. Or, perhaps, wait until May and do a fresh installation of 12.04 LTS; be sure to back up all your data first.

---

### Post by Kees Vaan Loo-Macklin on 2012-04-04
I was having similar issues with a new install of 11.10 via VMware fusion today where I simply could not get Update Manager to download and run updates. Then I tried via Terminal: sudo apt-get update && sudo apt-get upgrade

I was able to get most of the files except 50 Mb worth and the following error message:

 GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Opinions?

---

### Post by Kees Vaan Loo-Macklin on 2012-04-04
This is the code I got after running sudo apt-get update && sudo apt-get upgrade in Terminal:

```
Ign http://security.ubuntu.com oneiric-security InRelease
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://us.archive.ubuntu.com oneiric InRelease
Ign http://us.archive.ubuntu.com oneiric-updates InRelease
Hit http://security.ubuntu.com oneiric-security Release.gpg
Hit http://extras.ubuntu.com oneiric Release.gpg
Get:1 http://us.archive.ubuntu.com oneiric-backports InRelease [198 B]
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://extras.ubuntu.com oneiric Release                          
Hit http://us.archive.ubuntu.com oneiric Release.gpg                  
Hit http://security.ubuntu.com oneiric-security/main Sources          
Ign http://us.archive.ubuntu.com oneiric-updates Release.gpg
Ign http://us.archive.ubuntu.com oneiric-backports/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-backports/universe Sources/DiffIndex
Hit http://extras.ubuntu.com oneiric/main Sources                    
Hit http://security.ubuntu.com oneiric-security/restricted Sources   
Hit http://security.ubuntu.com oneiric-security/universe Sources     
Hit http://security.ubuntu.com oneiric-security/multiverse Sources   
Hit http://security.ubuntu.com oneiric-security/main i386 Packages   
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-backports/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages/DiffIndex
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages/DiffIndex
W: GPG error: http://us.archive.ubuntu.com oneiric-backports InRelease: File /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-backports_InRelease doesn't start with a clearsigned message
E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_binary-i386_Packages.IndexDiff - open (2: No such file or directory)

```

---

### Post by Kees Vaan Loo-Macklin on 2012-04-04
Solved! I simply changed to a different mirror for the updates.

---

