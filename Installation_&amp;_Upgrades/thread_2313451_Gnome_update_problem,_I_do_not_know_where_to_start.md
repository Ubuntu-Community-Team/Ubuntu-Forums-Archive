---
title: "Gnome update problem, I do not know where to start."
date: 2016-02-12
forum: Installation &amp; Upgrades
---

### Post by RobertoRecordo on 2016-02-12
I am running Ubuntu Gnome 15.10, updated form 15.04 .

I have ignored errors while updating, perhaps I am paying the price now. Sorry if this post is full of irrelevant information, I really do not know what is pertinent.

The first time I realized I have a problem:
While trying to remove an ugly gtk3 theme that I had installed from gnome-look.org, I decided that tweak-tool might help. When I invoke it from the gui apps, it seems to try to load, the little circle the represents busy spins, then it goes away.
From the command line```
$ sudo gnome-tweak-tool
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 563, in <module>
    main()
  File "/usr/lib/python2.7/site.py", line 545, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/lib/python2.7/site.py", line 272, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/lib/python2.7/site.py", line 247, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/lib/python2.7/site.py", line 237, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/lib/python2.7/sysconfig.py", line 582, in get_config_var
    return get_config_vars().get(name)
  File "/usr/lib/python2.7/sysconfig.py", line 528, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/lib/python2.7/sysconfig.py", line 412, in _init_posix
    from _sysconfigdata import build_time_vars
  File "/usr/lib/python2.7/_sysconfigdata.py", line 6, in <module>
    from _sysconfigdata_nd import *
ImportError: No module named _sysconfigdata_nd
```

I think I ignored that, went about my business, but when I tried to use Meld, it failed to run in a similar way. Had I used it since I upgraded? couldn't remember, so I tried to remove and install it.
```
$ sudo apt-get remove meld
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  youtube-dl
The following packages will be REMOVED:
  meld
The following packages will be upgraded:
  youtube-dl
1 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/634 kB of archives.
After this operation, 3,078 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 594953 files and directories currently installed.)
Preparing to unpack .../youtube-dl_2016.01.27-1~webupd8~wily1_all.deb ...
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 563, in <module>
    main()
  File "/usr/lib/python2.7/site.py", line 545, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/lib/python2.7/site.py", line 272, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/lib/python2.7/site.py", line 247, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/lib/python2.7/site.py", line 237, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/lib/python2.7/sysconfig.py", line 582, in get_config_var
    return get_config_vars().get(name)
  File "/usr/lib/python2.7/sysconfig.py", line 528, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/lib/python2.7/sysconfig.py", line 412, in _init_posix
    from _sysconfigdata import build_time_vars
  File "/usr/lib/python2.7/_sysconfigdata.py", line 6, in <module>
    from _sysconfigdata_nd import *
ImportError: No module named _sysconfigdata_nd
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 563, in <module>
    main()
  File "/usr/lib/python2.7/site.py", line 545, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/lib/python2.7/site.py", line 272, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/lib/python2.7/site.py", line 247, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/lib/python2.7/site.py", line 237, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/lib/python2.7/sysconfig.py", line 582, in get_config_var
    return get_config_vars().get(name)
  File "/usr/lib/python2.7/sysconfig.py", line 528, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/lib/python2.7/sysconfig.py", line 412, in _init_posix
    from _sysconfigdata import build_time_vars
  File "/usr/lib/python2.7/_sysconfigdata.py", line 6, in <module>
    from _sysconfigdata_nd import *
ImportError: No module named _sysconfigdata_nd
dpkg: error processing archive /var/cache/apt/archives/youtube-dl_2016.01.27-1~webupd8~wily1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 563, in <module>
    main()
  File "/usr/lib/python2.7/site.py", line 545, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/lib/python2.7/site.py", line 272, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/lib/python2.7/site.py", line 247, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/lib/python2.7/site.py", line 237, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/lib/python2.7/sysconfig.py", line 582, in get_config_var
    return get_config_vars().get(name)
  File "/usr/lib/python2.7/sysconfig.py", line 528, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/lib/python2.7/sysconfig.py", line 412, in _init_posix
    from _sysconfigdata import build_time_vars
  File "/usr/lib/python2.7/_sysconfigdata.py", line 6, in <module>
    from _sysconfigdata_nd import *
ImportError: No module named _sysconfigdata_nd
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/youtube-dl_2016.01.27-1~webupd8~wily1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
It got worse, I recognized the "youtube-dl" business as one of the failures I had previously ignored ( Who cares about downloading Utube files?) , but I tried to delete that with similar results.

Two other things that may be relevant:
1) I recently had some system problems, reverted to an older kernel to get working again
[http://ubuntuforums.org/showthread.php?t=2312322](http://ubuntuforums.org/showthread.php?t=2312322)

2) I installed python 2.7.11 and created a link to it```
lrwxrwxrwx 1 root root      12 Jan 21 08:52 /usr/bin/python -> python2.7.11


``` I think the system will continue to use Python 2.7.10, although I don't think it makes a difference.

I do not know where to start, can I purge all of the updates and recover?  I can't find anything like the package manager in other versions of Ubuntu, you can view, add, remove repositories, etc.

Any help is appreciated.

---

### Post by kansasnoob on 2016-02-12
It would be interesting to see the output of these two commands:

```
sudo apt-get update
```

```
sudo apt-get -f install
```

That may provide some clues.

Just BTW, when i encounter a kernel that doesn't work properly I just unhide the grub menu (if hidden by default) and manually select the older kernel at each boot. I know that's a royal pain but it seems like when we purge the latest kernel the whole system may become unstable.

---

### Post by RobertoRecordo on 2016-02-13
kansanoob -

I know how to hold down the SHIFT key during boot, I am a little embarrased to admit (after 6 years using Ubuntu) that i had to google to find: "For permanent change you'll need to edit your /etc/default/grub file -- place a "#" symbol at the start of line GRUB_HIDDEN_TIMEOUT=0."

Yes, I removed the kernel because I grew tired of managing the boot. The offensive kernel got re-installed automatically, but the video driver problem did not recur.

I ran the commands you suggested and am posting the results.```
$ sudo apt-get update

Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Hit http://us.archive.ubuntu.com wily InRelease                                
Get:1 http://security.ubuntu.com wily-security InRelease [65.9 kB]             
Hit http://dl.google.com stable Release                                        
Get:2 http://us.archive.ubuntu.com wily-updates InRelease [65.9 kB]            
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://archive.canonical.com quantal InRelease                             
Hit http://ppa.launchpad.net wily InRelease                                    
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://archive.canonical.com quantal/partner Sources                       
Ign http://ppa.launchpad.net wily InRelease                                    
Get:3 http://security.ubuntu.com wily-security/main Sources [29.4 kB]          
Hit http://us.archive.ubuntu.com wily-backports InRelease                      
Get:4 http://security.ubuntu.com wily-security/restricted Sources [2,854 B]    
Hit http://ppa.launchpad.net wily/main amd64 Packages                          
Get:5 http://us.archive.ubuntu.com wily-security InRelease [65.9 kB]           
Get:6 http://security.ubuntu.com wily-security/universe Sources [7,420 B]      
Hit http://ppa.launchpad.net wily/main i386 Packages                           
Get:7 http://security.ubuntu.com wily-security/multiverse Sources [2,772 B]    
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Get:8 http://security.ubuntu.com wily-security/main amd64 Packages [93.1 kB]
Hit http://ppa.launchpad.net wily/main Translation-en                          
Hit http://ppa.launchpad.net wily Release.gpg                                  
Get:9 http://security.ubuntu.com wily-security/restricted amd64 Packages [10.9 kB]
Hit http://ppa.launchpad.net wily Release                                      
Get:10 http://security.ubuntu.com wily-security/universe amd64 Packages [38.7 kB]
Get:11 http://security.ubuntu.com wily-security/multiverse amd64 Packages [6,249 B]
Hit http://ppa.launchpad.net wily/main amd64 Packages                          
Get:12 http://security.ubuntu.com wily-security/main i386 Packages [91.0 kB]
Hit http://ppa.launchpad.net wily/main i386 Packages                           
Get:13 http://security.ubuntu.com wily-security/restricted i386 Packages [10.8 kB]
Hit http://ppa.launchpad.net wily/main Translation-en                          
Get:14 http://security.ubuntu.com wily-security/universe i386 Packages [38.7 kB]
Get:15 http://security.ubuntu.com wily-security/multiverse i386 Packages [6,434 B]
Hit http://us.archive.ubuntu.com wily/main Translation-en               
Hit http://security.ubuntu.com wily-security/main Translation-en     
Hit http://security.ubuntu.com wily-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com wily/multiverse Translation-en      
Hit http://security.ubuntu.com wily-security/restricted Translation-en
Hit http://us.archive.ubuntu.com wily/restricted Translation-en      
Hit http://security.ubuntu.com wily-security/universe Translation-en 
Hit http://us.archive.ubuntu.com wily/universe Translation-en
Get:16 http://us.archive.ubuntu.com wily-updates/main Sources [48.3 kB]
Get:17 http://us.archive.ubuntu.com wily-updates/restricted Sources [3,741 B]
Get:18 http://us.archive.ubuntu.com wily-updates/universe Sources [14.1 kB]
Get:19 http://us.archive.ubuntu.com wily-updates/multiverse Sources [2,772 B]
Get:20 http://us.archive.ubuntu.com wily-updates/main amd64 Packages [130 kB]
Get:21 http://us.archive.ubuntu.com wily-updates/restricted amd64 Packages [13.3 kB]
Get:22 http://us.archive.ubuntu.com wily-updates/universe amd64 Packages [60.2 kB]
Get:23 http://us.archive.ubuntu.com wily-updates/multiverse amd64 Packages [6,249 B]
Get:24 http://us.archive.ubuntu.com wily-updates/main i386 Packages [127 kB]
Get:25 http://us.archive.ubuntu.com wily-updates/restricted i386 Packages [13.4 kB]
Get:26 http://us.archive.ubuntu.com wily-updates/universe i386 Packages [57.2 kB]
Get:27 http://us.archive.ubuntu.com wily-updates/multiverse i386 Packages [6,434 B]
Hit http://us.archive.ubuntu.com wily-updates/main Translation-en
Hit http://us.archive.ubuntu.com wily-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com wily-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com wily-updates/universe Translation-en          
Hit http://us.archive.ubuntu.com wily-backports/restricted Sources             
Hit http://us.archive.ubuntu.com wily-backports/multiverse Sources             
Hit http://us.archive.ubuntu.com wily-backports/restricted amd64 Packages      
Hit http://us.archive.ubuntu.com wily-backports/multiverse amd64 Packages      
Hit http://us.archive.ubuntu.com wily-backports/restricted i386 Packages       
Hit http://us.archive.ubuntu.com wily-backports/multiverse i386 Packages       
Hit http://us.archive.ubuntu.com wily-backports/main Translation-en            
Hit http://us.archive.ubuntu.com wily-backports/multiverse Translation-en      
Hit http://us.archive.ubuntu.com wily-backports/restricted Translation-en      
Hit http://us.archive.ubuntu.com wily-backports/universe Translation-en        
Get:28 http://us.archive.ubuntu.com wily-security/main Sources [29.4 kB]       
Get:29 http://us.archive.ubuntu.com wily-security/restricted Sources [2,854 B] 
Get:30 http://us.archive.ubuntu.com wily-security/universe Sources [7,420 B]   
Get:31 http://us.archive.ubuntu.com wily-security/multiverse Sources [2,772 B] 
Get:32 http://us.archive.ubuntu.com wily-security/main amd64 Packages [93.1 kB]
Get:33 http://us.archive.ubuntu.com wily-security/restricted amd64 Packages [10.9 kB]
Get:34 http://us.archive.ubuntu.com wily-security/universe amd64 Packages [38.7 kB]
Get:35 http://us.archive.ubuntu.com wily-security/multiverse amd64 Packages [6,249 B]
Get:36 http://us.archive.ubuntu.com wily-security/main i386 Packages [91.0 kB] 
Get:37 http://us.archive.ubuntu.com wily-security/restricted i386 Packages [10.8 kB]
Get:38 http://us.archive.ubuntu.com wily-security/universe i386 Packages [38.7 kB]
Get:39 http://us.archive.ubuntu.com wily-security/multiverse i386 Packages [6,434 B]
Hit http://us.archive.ubuntu.com wily-security/main Translation-en             
Hit http://us.archive.ubuntu.com wily-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com wily-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com wily-security/universe Translation-en         
Hit http://us.archive.ubuntu.com wily/main Sources                             
Hit http://us.archive.ubuntu.com wily/restricted Sources                       
Hit http://us.archive.ubuntu.com wily/universe Sources                         
Hit http://us.archive.ubuntu.com wily/multiverse Sources                       
Hit http://us.archive.ubuntu.com wily/main amd64 Packages                      
Hit http://us.archive.ubuntu.com wily/restricted amd64 Packages                
Hit http://us.archive.ubuntu.com wily/universe amd64 Packages                  
Hit http://us.archive.ubuntu.com wily/multiverse amd64 Packages                
Hit http://us.archive.ubuntu.com wily/main i386 Packages                       
Hit http://us.archive.ubuntu.com wily/restricted i386 Packages                 
Hit http://us.archive.ubuntu.com wily/universe i386 Packages                   
Hit http://us.archive.ubuntu.com wily/multiverse i386 Packages                 
Hit http://us.archive.ubuntu.com wily-backports/main Sources                   
Hit http://us.archive.ubuntu.com wily-backports/universe Sources               
Hit http://us.archive.ubuntu.com wily-backports/main amd64 Packages            
Hit http://us.archive.ubuntu.com wily-backports/universe amd64 Packages        
Hit http://us.archive.ubuntu.com wily-backports/main i386 Packages             
Hit http://us.archive.ubuntu.com wily-backports/universe i386 Packages         
Fetched 1,357 kB in 12s (108 kB/s)                                             
Reading package lists... Done
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/universe amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/main amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/universe amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/multiverse amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/universe i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/main i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/universe i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/multiverse i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/main amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/universe amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/multiverse amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/main i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/universe i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/multiverse i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/main amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/universe amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/multiverse amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/main i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/universe i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/multiverse i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```
```
$ sudo apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  youtube-dl
The following packages will be upgraded:
  youtube-dl
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/634 kB of archives.
After this operation, 150 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 594953 files and directories currently installed.)
Preparing to unpack .../youtube-dl_2016.01.27-1~webupd8~wily1_all.deb ...
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 563, in <module>
    main()
  File "/usr/lib/python2.7/site.py", line 545, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/lib/python2.7/site.py", line 272, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/lib/python2.7/site.py", line 247, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/lib/python2.7/site.py", line 237, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/lib/python2.7/sysconfig.py", line 582, in get_config_var
    return get_config_vars().get(name)
  File "/usr/lib/python2.7/sysconfig.py", line 528, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/lib/python2.7/sysconfig.py", line 412, in _init_posix
    from _sysconfigdata import build_time_vars
  File "/usr/lib/python2.7/_sysconfigdata.py", line 6, in <module>
    from _sysconfigdata_nd import *
ImportError: No module named _sysconfigdata_nd
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 563, in <module>
    main()
  File "/usr/lib/python2.7/site.py", line 545, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/lib/python2.7/site.py", line 272, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/lib/python2.7/site.py", line 247, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/lib/python2.7/site.py", line 237, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/lib/python2.7/sysconfig.py", line 582, in get_config_var
    return get_config_vars().get(name)
  File "/usr/lib/python2.7/sysconfig.py", line 528, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/lib/python2.7/sysconfig.py", line 412, in _init_posix
    from _sysconfigdata import build_time_vars
  File "/usr/lib/python2.7/_sysconfigdata.py", line 6, in <module>
    from _sysconfigdata_nd import *
ImportError: No module named _sysconfigdata_nd
dpkg: error processing archive /var/cache/apt/archives/youtube-dl_2016.01.27-1~webupd8~wily1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 563, in <module>
    main()
  File "/usr/lib/python2.7/site.py", line 545, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/lib/python2.7/site.py", line 272, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/lib/python2.7/site.py", line 247, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/lib/python2.7/site.py", line 237, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/lib/python2.7/sysconfig.py", line 582, in get_config_var
    return get_config_vars().get(name)
  File "/usr/lib/python2.7/sysconfig.py", line 528, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/lib/python2.7/sysconfig.py", line 412, in _init_posix
    from _sysconfigdata import build_time_vars
  File "/usr/lib/python2.7/_sysconfigdata.py", line 6, in <module>
    from _sysconfigdata_nd import *
ImportError: No module named _sysconfigdata_nd
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/youtube-dl_2016.01.27-1~webupd8~wily1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Some of the things that I  have recently tried : most all end with errors:
```
 1630  sudo apt-get autoremove
 1832  history |grep apt-get-install
 1833  history |grep apt-get
 1890  sudo apt-get update
 1891  sudo apt-get install meld
 1893  sudo apt-get remove meld
 1895  sudo apt-get remove meld
 1896  sudo apt-get clean && sudo apt-get autoremove
 1897  sudo apt-get update
 1898  sudo apt-get -f install
 1899  sudo apt-get remove youtube-dl
 1900  sudo apt-get install youtube-dl  
 1901  sudo apt-get remove youtube-dl | grep err
 1902  sudo apt-get install youtube-dl  | grep err
 1947  sudo apt-get remove meld
 1979  sudo apt-get update
 1980  sudo apt-get -f install

```

Thank you for your efforst in helping to identify this problem,

-Rob

---

### Post by ian-weisser on 2016-02-13
> **RobertoRecordo said:**
> 
  File "/usr/lib/python2.7/_sysconfigdata.py", line 6, in <module>
    from _sysconfigdata_nd import *
ImportError: No module named _sysconfigdata_nd


Well, _sysconfigdata_nd is provided by the libpython2.7-minimal package.
You can try:
```
sudo apt-get install --reinstall libpython2.7-minimal
```

---

### Post by kansasnoob on 2016-02-14
There are a number of issues, I'd start with all the duplicates:

```
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/universe amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/main amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/universe amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/multiverse amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/universe i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/main i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/universe i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily/multiverse i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/main amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/universe amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/multiverse amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/main i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/universe i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-updates/multiverse i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/main amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/universe amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/multiverse amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/main i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/universe i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ wily-backports/multiverse i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_wily-backports_multiverse_binary-i386_Packages)
```

Two worries there; obviously the duplicates but second I also wonder about the mix of i386 and amd64. We need to see a few things to be sure what we're working with so please post the output of the following:

```
lsb_release -a
```

```
cat /etc/apt/sources.list
```

The output of this command will help us figure out the next step in this process (what ppa's are installed):

```
ls /etc/apt/sources.list.d
```

---

### Post by RobertoRecordo on 2016-02-14
> **kansasnoob said:**
> There are a number of issues, I'd start with all the duplicates:

  I can't find anything like the package manager in other versions of Ubuntu, you can view, add, remove repositories, etc. How do I remove duplicates?

> **kansasnoob said:**
> Two worries there; obviously the duplicates but second I also wonder about the mix of i386 and amd64. We need to see a few things to be sure what we're working with so please post the output of the following:```
lsb_release -a
``````
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily
```

> **kansasnoob said:**
> ```
cat /etc/apt/sources.list
``````
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-GNOME 15.04 _Vivid Vervet_ - Release amd64 (20150422)]/ vivid main multiverse restricted universe
# deb cdrom:[Ubuntu-Studio 12.10 _Quantal Quetzal_ - Release amd64 (20121017.1)]/ quantal main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu wily main restricted
deb-src http://us.archive.ubuntu.com/ubuntu wily main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu wily-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu wily-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu wily universe
deb-src http://us.archive.ubuntu.com/ubuntu wily universe
deb http://us.archive.ubuntu.com/ubuntu wily-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu wily multiverse
deb-src http://us.archive.ubuntu.com/ubuntu wily multiverse
deb http://us.archive.ubuntu.com/ubuntu wily-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu wily-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu wily-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu wily-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu wily-security main restricted
deb http://us.archive.ubuntu.com/ubuntu wily-security universe
deb-src http://us.archive.ubuntu.com/ubuntu wily-security universe
deb http://us.archive.ubuntu.com/ubuntu wily-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
# deb http://ppa.launchpad.net/gwendal-lebihan-dev/hexchat-stable/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/hexchat-stable/ubuntu wily main # disabled on upgrade to wily
deb http://us.archive.ubuntu.com/ubuntu wily universe
# deb http://archive.getdeb.net/ubuntu wily apps # disabled on upgrade to wily
# deb-src http://archive.getdeb.net/ubuntu wily apps # disabled on upgrade to wily


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ wily main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ wily main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ wily universe
deb-src http://us.archive.ubuntu.com/ubuntu/ wily universe
deb http://us.archive.ubuntu.com/ubuntu/ wily-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ wily multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ wily multiverse
deb http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu wily-security main restricted
deb-src http://security.ubuntu.com/ubuntu wily-security main restricted
deb http://security.ubuntu.com/ubuntu wily-security universe
deb-src http://security.ubuntu.com/ubuntu wily-security universe
deb http://security.ubuntu.com/ubuntu wily-security multiverse
deb-src http://security.ubuntu.com/ubuntu wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu vivid partner
# deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu vivid main
# deb-src http://archive.canonical.com/ubuntu vivid partner
```

> **kansasnoob said:**
> The output of this command will help us figure out the next step in this process (what ppa's are installed):CODE]ls /etc/apt/sources.list.d[/CODE]```
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-GNOME 15.04 _Vivid Vervet_ - Release amd64 (20150422)]/ vivid main multiverse restricted universe
# deb cdrom:[Ubuntu-Studio 12.10 _Quantal Quetzal_ - Release amd64 (20121017.1)]/ quantal main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu wily main restricted
deb-src http://us.archive.ubuntu.com/ubuntu wily main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu wily-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu wily-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu wily universe
deb-src http://us.archive.ubuntu.com/ubuntu wily universe
deb http://us.archive.ubuntu.com/ubuntu wily-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu wily multiverse
deb-src http://us.archive.ubuntu.com/ubuntu wily multiverse
deb http://us.archive.ubuntu.com/ubuntu wily-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu wily-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu wily-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu wily-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu wily-security main restricted
deb http://us.archive.ubuntu.com/ubuntu wily-security universe
deb-src http://us.archive.ubuntu.com/ubuntu wily-security universe
deb http://us.archive.ubuntu.com/ubuntu wily-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
# deb http://ppa.launchpad.net/gwendal-lebihan-dev/hexchat-stable/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/hexchat-stable/ubuntu wily main # disabled on upgrade to wily
deb http://us.archive.ubuntu.com/ubuntu wily universe
# deb http://archive.getdeb.net/ubuntu wily apps # disabled on upgrade to wily
# deb-src http://archive.getdeb.net/ubuntu wily apps # disabled on upgrade to wily


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ wily main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ wily main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ wily universe
deb-src http://us.archive.ubuntu.com/ubuntu/ wily universe
deb http://us.archive.ubuntu.com/ubuntu/ wily-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ wily multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ wily multiverse
deb http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu wily-security main restricted
deb-src http://security.ubuntu.com/ubuntu wily-security main restricted
deb http://security.ubuntu.com/ubuntu wily-security universe
deb-src http://security.ubuntu.com/ubuntu wily-security universe
deb http://security.ubuntu.com/ubuntu wily-security multiverse
deb-src http://security.ubuntu.com/ubuntu wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu vivid partner
# deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu vivid main
# deb-src http://archive.canonical.com/ubuntu vivid partner
```

Thank you for your help -  will drop out off the forum later today ( 2PM pacific time ) return from vacation Late Wednesday  17 February.
I will check in later today.

---

### Post by RobertoRecordo on 2016-02-14
> **ian-weisser said:**
> Well, _sysconfigdata_nd is provided by the libpython2.7-minimal package.
You can try:
```
sudo apt-get install --reinstall libpython2.7-minimal
```

Ian - Thank you for taking the time to respond to my question. Because kansasnoob is looking at information from my system I am hesitant to make changes at the moment. I did run that code, but aborted before changes were made:
```
$ sudo apt-get install --reinstall libpython2.7-minimal
[sudo] password for robmilby: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  youtube-dl
The following packages will be upgraded:
  youtube-dl
1 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 337 kB/971 kB of archives.
After this operation, 150 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
```
Perhaps the item " 1 not fully installed or removed." is part of the problem.What do you think?

-Rob

---

### Post by ian-weisser on 2016-02-14
As kansasnoob has pointed out, there are a number of issues.
The 'not fully installed or removed' package is probably youtube-dl.

---

### Post by RobertoRecordo on 2016-02-14
Yes, and I had thrashed around trying to remove youtube-dl previously. It seem there are a number of packages in limbo, or perhaps more accurately we could call them "The Undead".

-Rob

---

### Post by matt_symes on 2016-02-14
Hi

To fix your sources, open a terminal and copy and paste these commands into it

Make a backup of your old sources file

```
sudo mv /etc/apt/sources.list{,.broke}
```

Copy and paste this whole block below into the terminal. Hit <enter> and enter your password if asked.

It will create a new sources file for you.

```
cat <<'EOF' | sudo tee /etc/apt/sources.list
deb http://security.ubuntu.com/ubuntu wily-security main restricted
deb http://security.ubuntu.com/ubuntu wily-security multiverse
deb http://security.ubuntu.com/ubuntu wily-security universe
deb http://us.archive.ubuntu.com/ubuntu wily-backports main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu wily main restricted
deb http://us.archive.ubuntu.com/ubuntu wily multiverse
deb http://us.archive.ubuntu.com/ubuntu wily universe
deb http://us.archive.ubuntu.com/ubuntu wily-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu wily-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu wily-updates universe
EOF
```

Remove the old list cache.
```
sudo rm -r /var/lib/apt/lists/*
```

The above should get you nearer.

Then please post the output of these command for further diagnostics.

This will update your sources and check for broken dependencies.

```
sudo apt-get check
```

This is audit dpkg.
```
dpkg -C
```

```
apt-cache policy libpython2.7-minimal
```

This will simulate an install to show us what will happen when you reinstall libpython2.7-minimal. As Ian said, this is the package that contains _sysconfigdata_nd.py.
```
sudo apt-get -s -qqq install --reinstall libpython2.7-minimal
```

Update you search database
```
sudo updatedb
```

Search for _sysconfigdata_nd.py
```
locate _sysconfigdata_nd.py
```

Kind regards

---

### Post by ian-weisser on 2016-02-14
They are 'undead' becasue apt remembers what you asked of it before, and keep trying at every opportunity until it accomplishes what you told it to do.
We understand the youtube-dl issue - a dependency that should be satisfied is not, causing an error. Reinstalling the relevant package should fix that particular error.

As we progress down the rabbit-hole of old problems, we may encounter other problems.
Example: Did you figure out how to de-duplicate your /etc/apt/sources.list ?

---

### Post by RobertoRecordo on 2016-02-14
Ian -

Thank you for all your help so far - I am going to be offline ( camping vacation ) until Late Wednesday  17 February. 
When I tried to fix youtube-dl I got errors```
$ sudo apt-get remove youtube-dl
[sudo] password for robmilby: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mplayer2 rtmpdump
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  youtube-dl
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 3,284 kB disk space will be freed.
Do you want to continue? [Y/n] Y
dpkg: error processing package youtube-dl (--remove):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 youtube-dl
E: Sub-process /usr/bin/dpkg returned an error code (1)
$
$ sudo apt-get install youtube-dl  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  youtube-dl
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/634 kB of archives.
After this operation, 150 kB of additional disk space will be used.
Selecting previously unselected package youtube-dl.
(Reading database ... 594953 files and directories currently installed.)
Preparing to unpack .../youtube-dl_2016.01.27-1~webupd8~wily1_all.deb ...
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 563, in <module>
    main()
  File "/usr/lib/python2.7/site.py", line 545, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/lib/python2.7/site.py", line 272, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/lib/python2.7/site.py", line 247, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/lib/python2.7/site.py", line 237, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/lib/python2.7/sysconfig.py", line 582, in get_config_var
    return get_config_vars().get(name)
  File "/usr/lib/python2.7/sysconfig.py", line 528, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/lib/python2.7/sysconfig.py", line 412, in _init_posix
    from _sysconfigdata import build_time_vars
  File "/usr/lib/python2.7/_sysconfigdata.py", line 6, in <module>
    from _sysconfigdata_nd import *
ImportError: No module named _sysconfigdata_nd
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 563, in <module>
    main()
  File "/usr/lib/python2.7/site.py", line 545, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/lib/python2.7/site.py", line 272, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/lib/python2.7/site.py", line 247, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/lib/python2.7/site.py", line 237, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/lib/python2.7/sysconfig.py", line 582, in get_config_var
    return get_config_vars().get(name)
  File "/usr/lib/python2.7/sysconfig.py", line 528, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/lib/python2.7/sysconfig.py", line 412, in _init_posix
    from _sysconfigdata import build_time_vars
  File "/usr/lib/python2.7/_sysconfigdata.py", line 6, in <module>
    from _sysconfigdata_nd import *
ImportError: No module named _sysconfigdata_nd
dpkg: error processing archive /var/cache/apt/archives/youtube-dl_2016.01.27-1~webupd8~wily1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 563, in <module>
    main()
  File "/usr/lib/python2.7/site.py", line 545, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/lib/python2.7/site.py", line 272, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/lib/python2.7/site.py", line 247, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/lib/python2.7/site.py", line 237, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/lib/python2.7/sysconfig.py", line 582, in get_config_var
    return get_config_vars().get(name)
  File "/usr/lib/python2.7/sysconfig.py", line 528, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/lib/python2.7/sysconfig.py", line 412, in _init_posix
    from _sysconfigdata import build_time_vars
  File "/usr/lib/python2.7/_sysconfigdata.py", line 6, in <module>
    from _sysconfigdata_nd import *
ImportError: No module named _sysconfigdata_nd
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/youtube-dl_2016.01.27-1~webupd8~wily1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
$ 
$ $ youtube-dl --version
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 563, in <module>
    main()
  File "/usr/lib/python2.7/site.py", line 545, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/lib/python2.7/site.py", line 272, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/lib/python2.7/site.py", line 247, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/lib/python2.7/site.py", line 237, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/lib/python2.7/sysconfig.py", line 582, in get_config_var
    return get_config_vars().get(name)
  File "/usr/lib/python2.7/sysconfig.py", line 528, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/lib/python2.7/sysconfig.py", line 412, in _init_posix
    from _sysconfigdata import build_time_vars
  File "/usr/lib/python2.7/_sysconfigdata.py", line 6, in <module>
    from _sysconfigdata_nd import *
ImportError: No module named _sysconfigdata_nd

```
As I said previously "I can't find anything like the package manager in other versions of  Ubuntu, you can view, add, remove repositories, etc. How do I remove  duplicates?"

I willl check in Thursday AM, but won't be able to respond before then.

Regards,

-Rob

---

### Post by ian-weisser on 2016-02-14
Hope you had a good time camping.

Not sure how Gnome does it. One way to de-duplicate is to edit /etc/apt/sources.list.
It's a root-owned file, so the safest way to do it is:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak        ## Make a backup of the file
sudo nano /etc/apt/sources.list                                ## Edit the original
```    
Use your normal arrow keys to maneuver, and your delete key to...well, you know.
Alternately, you can merely comment out duplicate lines by adding a '#' to the beginning of the line.
Use CTRL+O to save your work.
Use CRTL+X to exit.

There's nothing magic about the file. Apt ignores the comments and parses the URIs to determine the sources to get packages from.
If you really screw up...well, that's why you made a backup.

---

### Post by RobertoRecordo on 2016-02-15
I said I was staying away, this is more fun than packing.

I took a bash scripting class two years ago at my community college. The instructor was excellent, and even though I am experienced programmer, the class was hard! I leaned to do all kinds of things from the command line (bash is a huge improvement over DOS!), but as we were on a Unix system, I learned nothing about Linux administration. In particular, I am a newb when it comes to how Ubuntu updates work, and when it comes to using apt-get, I just type like a monkey. When I installed Ubuntu 15.04 I partitioned my hard drive so both of the user accounts are on separate partitions. Re-installing is a fairly low risk option, but fixing this problem is a learning opportunity.

When I return I will back up and edit 
/etc/apt/sources.list


Thank you , Ian,

-Rob

---

### Post by RobertoRecordo on 2016-08-29
Thanks to all that tried to help with this, 6 months have passed, and I am sorry that I disappeared.

The result is that I am still using a system that can not be updated, and intend to install Ubuntu 16.04, but I am having trouble making time to do that, we are remodelling!

I marked this solved -  the solution being to do a fresh install.

I appreciate all the attempt to help me with this. It was educational, thank you all. 

Regards,

Rob

---

