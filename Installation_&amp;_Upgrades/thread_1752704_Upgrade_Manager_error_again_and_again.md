---
title: "Upgrade Manager error again and again"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by emma00 on 2011-05-08
While upgrading ubuntu 10.10 to 11.04 from update manager i am getting always this error:

Could not initialize the package information
An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, Eroblem with MergeList /var/lib/apt/lists/pk.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by mörgæs on 2011-05-08
How does the machine behave if you boot it and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

?

---

### Post by emma00 on 2011-05-24
1. sudo apt-get clean
Than it request for password and nothing came on terminal than
2.sudo apt-get update
Media change: please insert the disc labeled                                   
 'Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1)'
in the drive '/cdrom/' and press enter

Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72B]                         
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) natty/main Translation-en                 
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) natty/main Translation-en_US              
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Media change: please insert the disc labeled                                   
 'Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1)'
in the drive '/cdrom/' and press enter

Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198B]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/main Translation-en      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/main Translation-en_US   
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en      
Media change: please insert the disc labeled                                   
 'Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1)'
in the drive '/cdrom/' and press enter

Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty Release.gpg                             
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty/main Translation-en             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/universe Translation-en  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/universe Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [23.2kB]               
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Get:6 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [764B]                    
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty/main Translation-en_US          
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty/multiverse Translation-en       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1)/ natty/main Translation-en
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1)/ natty/main Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1)/ natty/restricted Translation-en
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Beta 1 i386 (20110329.1)/ natty/restricted Translation-en_US
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [2,692B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [647B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [21.4kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [10.2kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [2,071B]
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [6,333B]         
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty/restricted Translation-en
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty/restricted Translation-en_US    
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty/universe Translation-en         
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty/universe Translation-en_US
Get:15 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty-updates Release.gpg [198B]
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty-updates/main Translation-en
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty-updates/main Translation-en_US
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty-updates/multiverse Translation-en
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty-updates/multiverse Translation-en_US
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty-updates/restricted Translation-en
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty-updates/restricted Translation-en_US
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty-updates/universe Translation-en
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) natty-updates/universe Translation-en_US
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty Release
Get:16 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty-updates Release [27.2kB]             
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty/main Sources                            
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty/universe Sources                        
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty/multiverse Sources
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty/main i386 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty/restricted i386 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty/universe i386 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty/multiverse i386 Packages
Get:17 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty-updates/main Sources [29.2kB]
Get:18 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty-updates/restricted Sources [14B]     
Get:19 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty-updates/universe Sources [7,344B]    
Get:20 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty-updates/multiverse Sources [1,362B]  
Get:21 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty-updates/main i386 Packages [103kB]   
Get:22 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty-updates/restricted i386 Packages [14B]
Get:23 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty-updates/universe i386 Packages [38.9kB]
Get:24 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) natty-updates/multiverse i386 Packages [3,754B]
Fetched 280kB in 4min 19s (1,079B/s)                                           
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/pk.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

3.sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/pk.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by mörgæs on 2011-05-24
What about 

```
sudo rm /var/lib/apt/lists/* -vf
```

followed by the three apt-commands?

---

### Post by emma00 on 2011-05-26
Hi, i have done what you have suggested thanks for that but after this the upgrading starts but after restarting the computer ubuntu freezes on splash screen and i have tried other grub options but same happens.... :)

---

### Post by mörgæs on 2011-05-26
I guess you have hit one of the display driver bugs in 11.04. This thread might help:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Another option is staying with 10.10 as long as it is supported (which I have decided to do).

---

### Post by emma00 on 2011-05-27
Thanks but my previous grub options are also not working and i can not log into ubuntu 10.10 my important files are there its first time i have got error during upgrading/installation ;P

---

### Post by shahverdy on 2011-05-27
well, I think you'd better change the repositories, to do so first run this:

```
sudo rm /var/lib/apt/lists/* -vf
```

then run :

```
sudo gedit /etc/apt/sources.list
```

and paste the bellow into it:

```


## these repositories work for me fine :)

deb http://www.linuxmint.com/repository/ daryna main upstream import
deb http://ir.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
deb-src http://ir.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ natty partner
deb-src http://archive.canonical.com/ubuntu/ natty partner
deb http://extras.ubuntu.com/ubuntu/ natty main
deb-src http://extras.ubuntu.com/ubuntu/ natty main
deb http://liveusb.info/multisystem/depot/ all main
deb http://archive.ubuntu.com/ubuntu/ natty main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ natty universe main multiverse restricted

```


if you can not log into your ubuntu use a live CD to get access to your imortant files, and then run these commands using live CD.
notice that if you are using a live CD, first goto places and mount your linux root partition, then commands will be like this : 

```
sudo rm /media/path-to-your-partition/var/lib/apt/lists/* -vf
```
and 
```
sudo gedit /media/path-to-your-partition/etc/apt/sources.list
```

after all, run update manager again and update your display driver easily : )

---

### Post by emma00 on 2011-05-29
I have done using commands and live cd but nothing has changed and my files are not showing up in documents folder using live cd....:(

---

### Post by shahverdy on 2011-05-29
> **emma00 said:**
> I have done using commands and live cd but nothing has changed and my files are not showing up in documents folder using live cd....:(

by documents folder you mean what?
when you are using live CD, the path to your documents folder is somthing else. do you consider that ?

---

### Post by emma00 on 2011-05-30
the default document folder which is pre built in ubuntu 10.10 and other likes music,videos etc nah i did not know that there path are changed can u tell me how to access them thanks.

---

### Post by shahverdy on 2011-05-30
well, you must go to "places" and then "your linux partition" witch your system has been installed on, then there you can see a folder named "home" : ) there you can find what ever you want  : )

---

