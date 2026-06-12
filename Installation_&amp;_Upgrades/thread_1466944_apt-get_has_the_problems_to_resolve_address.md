---
title: "apt-get has the problems to resolve address"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by ravi.xolve on 2010-04-30
I installed Lucid. I am sitting behind a passworded proxy therefore I set up this proxy variable:

```
http://user:password@host:port/
```

When I try use apt-get upgrade it shows the following error:

```
Err http://us.archive.ubuntu.com lucid Release.gpg                          
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com lucid-security Release.gpg                   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

.....
```

But when I try to use:

```
wget www.google.com
```

it just works fine and gets me the desired page. Looks like there is some problem. I tried using KPackagekit and installed Synaptic manually to resolve it but no help.

Please help me out of this. My PC is just plain OS with no applications I need.

---

### Post by ravi.xolve on 2010-04-30
Ok now I manually updated the apt-get lists (yeah it was very tiresome). And now when I want to install a package I get the same error:


```
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe linuxdcpp 1.0.3-1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/l/linuxdcpp/linuxdcpp_1.0.3-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/l/linuxdcpp/linuxdcpp_1.0.3-1_i386.deb)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
```

Well whats the problem? Bug with apt-get?

---

### Post by ravi.xolve on 2010-04-30
here is a snapshot of my sources: [http://pastebin.com/EDYcMMC5](http://pastebin.com/EDYcMMC5)
Its unmodified and the original one from the installation.

---

### Post by ThatBum on 2010-04-30
I have the exact same problem, error -5 and everything. It has been present since I got the pre-release of Lucid; the first one I got was Beta 1, and, on my machine, it has been present through Beta 2 and RC. I wasn't going to say anything because I thought it would be caught before it went final, but i guess it didn't.

Now, the behavior, at least for me. it's behaving pretty erratically. If apt-get update is run a bunch of times, eventually it will complete with no errors, but the next time through more than one server might not resolve.

My network connection is working fine (3008kbps down/512kbps up ADSL), and I checked, I don't have packet loss or anything.. Also apt-get install x works fine once the package lists are downloaded, and every other Internet related program works fine. It's ONLY apt-get update, or something that uses it, like Update Manager's "Check" function, or aptitude updating the lists.

A notable thing is that the offending server (whatever it might be, it's completely random) sometimes sits at "Waiting for headers" for a awhile before petering out. This means it's probably timing out for some reason. Then again, it's sometimes instant. Like I said, it's very erratic.

Anyway, yes, that's it, Lucid is awesome, I have no other problems it, except for the Nvidia/plymouth problem, but I've rectified that with the Grub hack.

Hope this gets fixed soon.

---

### Post by ravi.xolve on 2010-05-01
This is just unexplainable how can this major functionality go undetected during alphas, betas and RC's. I don't know what to do except the manual installtion.

---

### Post by Gone fishing on 2010-05-02
Ah! This is similar to the problem I'm having:

[http://ubuntuforums.org/showthread.php?t=1468738&highlight=proxy+lucid](http://ubuntuforums.org/showthread.php?t=1468738&highlight=proxy+lucid)

but it's odder if you sudo -i than put in the command it works but sudo doesn't. For example:

```
sudo -i
``` then ```
apt-get install flashplugin-nonfree
``` works
```
sudo apt-get install flashplugin-nonfree
``` fails

or

```
sudo i
``` then  ```
wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
``` works

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
``` fails



Although with me sudo apt-get update works

---

### Post by ravi.xolve on 2010-05-02
@[Gone fishing]("http://ubuntuforums.org/member.php?u=313801") how is your reply related to this post.

---

### Post by Gone fishing on 2010-05-02
Well we both seem to be having resolve issues through a proxy server. I'm finding that when I use sudo it fails to use the proxy for eg the message from a terminal command

> sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for john: 
--2010-05-02 10:54:39--  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `[www.medibuntu.org](www.medibuntu.org)
However, it finds the proxy setting with sudo -i then the the command

---

### Post by ravi.xolve on 2010-05-02
Thanks, your tip did the work. Earlier I thought that some ways its a bug in apt-get. However, if there is any way to make the behavior of sudo again as earlier, it would be cool.

---

### Post by Gone fishing on 2010-05-02
Thanks

This is a bug - but I'm not sure how. The proxy settings with apt, and wget? are being applied inconsistently with sudo. 

I haven't quite got my head round what isn't working and why. Certainly it all works with sudo -i and only some of it works with sudo.

---

### Post by ThatBum on 2010-05-02
Actually, Medibuntu is down AGAIN, it's serverside on this one. It was down just a few weeks ago. I wonder what's going on over there?

**E:** It's back up now.

---

### Post by ThatBum on 2010-05-02
NEWS: I garbage picked a computer and put Xubuntu 10.04 on it. Xubuntu 10.04 does NOT seem to have this problem, all servers resolve after repeated attempts to reproduce. This means that whatever is happening with apt-get update is Ubuntu-specific.

---

### Post by r_vigneswaran on 2010-05-03
Thank you Gone fishing! This solved my problem.

I think the problem occurs when 1. we are behind a proxy server, *and* 2. we specify the proxy information in the environment variable (http_proxy, ftp_proxy etc.). This is because, when we use sudo, it is not using the current user's environment (completely). So, the exported variables are not available in the "sudo" environment.

The ways to solve this,
1. use "sudo -E apt-get update". (preserves the current environment).
(OR)
2. export the variables in /root/.profile, then "sudo -i apt-get update".
(OR)
3. do a "sudo su -", then export the proxy information to the environment and do "apt-get update".

Vignesh

---

### Post by ThatBum on 2010-05-03
I do not use a proxy here.

```
sudo -i apt-get update
```OR

```
sudo su
AND
apt-get update
```doesn't work for me.

So this still applies.

The only thing between me and the Internet is my 2wire router, which didn't cause any apt-get update related problems in any other Ubuntu release.

---

### Post by r_vigneswaran on 2010-05-03
Oh... Sorry, ThatBum. Actually, I intend to reply "ravi.xolve" and "GoneFishing". I have no clue about your problem :-(.

---

### Post by Gone fishing on 2010-05-03
The problem wasn't mediubuntu being down - that was another small problem and so I change to this mirror

deb [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free
deb-src [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free

I note that UCT also has an RSA mirror

deb [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free
deb-src [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free

r_vigneswaran I don't think the specifying variables is it as I just use 192.168.4.1:8024 for all protocols

Thatbum I think your problem is quite different - did you specify a DNS in Network connections have you got the gateway IP right?

---

### Post by ThatBum on 2010-05-03
Yeah, I have a DNS, PPPoE set up, NAT working, gateway IP, and all that. It was all preconfigured by SBC when it came here...I knew that for awhile, I configured the wireless in there and came across it. Granted my line is a little noisy because of some bad phone line, or the cheapness of the router, or both, but it didn't cause any problems before.

And I think Medibuntu did go down briefly. medibuntu.org was not found for awhile.

This is the contents of my sources.list:

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner
deb http://mirrors.us.kernel.org/ubuntu/ lucid main universe restricted multiverse
deb-src http://mirrors.us.kernel.org/ubuntu/ lucid main universe restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ lucid-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ lucid-security universe main multiverse restricted #Added by software-properties
deb http://mirrors.us.kernel.org/ubuntu/ lucid-updates universe main multiverse restricted
deb-src http://mirrors.us.kernel.org/ubuntu/ lucid-updates universe main multiverse restricted #Added by software-properties
deb http://mirrors.us.kernel.org/ubuntu/ lucid-proposed universe main multiverse restricted
deb-src http://mirrors.us.kernel.org/ubuntu/ lucid-proposed universe main multiverse restricted #Added by software-properties
deb http://mirrors.us.kernel.org/ubuntu/ lucid-backports universe main multiverse restricted
deb-src http://mirrors.us.kernel.org/ubuntu/ lucid-backports universe main multiverse restricted #Added by software-properties
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```I have noticed that it always happens with the servers near the end of the update, never the beginning.

Example:

```
justyn@FrontRoomBoxLucid:~$ sudo apt-get update

Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/ all/main Translation-en_US
Hit http://archive.ubuntu.com lucid Release.gpg                                
Hit http://archive.ubuntu.com lucid Release                                    
Hit http://archive.ubuntu.com lucid/main Sources                               
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Hit http://archive.getdeb.net lucid-getdeb Release.gpg                         
Hit http://archive.ubuntu.com lucid/restricted Sources                         
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/main Sources                     
Hit http://security.ubuntu.com lucid-security/multiverse Sources               
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Ign http://archive.getdeb.net/ubuntu/ lucid-getdeb/apps Translation-en_US      
Hit http://archive.getdeb.net lucid-getdeb Release                             
Hit http://archive.getdeb.net lucid-getdeb/apps Packages                       
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Hit http://archive.canonical.com lucid Release                                 
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://archive.canonical.com lucid/partner Sources                         
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/psyke83/ppa/ubuntu/ lucid/main Translation-en_US  
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://mirrors.us.kernel.org lucid Release.gpg                             
Ign http://mirrors.us.kernel.org/ubuntu/ lucid/main Translation-en_US          
Ign http://mirrors.us.kernel.org/ubuntu/ lucid/universe Translation-en_US      
Ign http://mirrors.us.kernel.org/ubuntu/ lucid/restricted Translation-en_US    
Ign http://mirrors.us.kernel.org/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://mirrors.us.kernel.org lucid-updates Release.gpg                     
Ign http://mirrors.us.kernel.org/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://mirrors.us.kernel.org/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://mirrors.us.kernel.org/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://mirrors.us.kernel.org/ubuntu/ lucid-updates/restricted Translation-en_US
Hit http://mirrors.us.kernel.org lucid-proposed Release.gpg                    
Ign http://mirrors.us.kernel.org/ubuntu/ lucid-proposed/universe Translation-en_US
Ign http://mirrors.us.kernel.org/ubuntu/ lucid-proposed/main Translation-en_US 
Ign http://mirrors.us.kernel.org/ubuntu/ lucid-proposed/multiverse Translation-en_US
Ign http://mirrors.us.kernel.org/ubuntu/ lucid-proposed/restricted Translation-en_US
Hit http://mirrors.us.kernel.org lucid-backports Release.gpg                   
Ign http://mirrors.us.kernel.org/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://mirrors.us.kernel.org/ubuntu/ lucid-backports/main Translation-en_US
Ign http://mirrors.us.kernel.org/ubuntu/ lucid-backports/multiverse Translation-en_US
Ign http://mirrors.us.kernel.org/ubuntu/ lucid-backports/restricted Translation-en_US
Hit http://mirrors.us.kernel.org lucid Release                                 
Hit http://mirrors.us.kernel.org lucid-updates Release                         
Hit http://mirrors.us.kernel.org lucid-proposed Release                        
Hit http://mirrors.us.kernel.org lucid-backports Release                       
Get:1 http://downloads.sourceforge.net all Release.gpg [197B]                  
Hit http://mirrors.us.kernel.org lucid/main Packages                           
Hit http://mirrors.us.kernel.org lucid/universe Packages                       
Hit http://mirrors.us.kernel.org lucid/restricted Packages                     
Hit http://mirrors.us.kernel.org lucid/multiverse Packages                     
Hit http://mirrors.us.kernel.org lucid/main Sources                            
Hit http://mirrors.us.kernel.org lucid/universe Sources                        
Hit http://mirrors.us.kernel.org lucid/restricted Sources                      
Hit http://mirrors.us.kernel.org lucid/multiverse Sources                      
Hit http://mirrors.us.kernel.org lucid-updates/universe Packages               
Hit http://mirrors.us.kernel.org lucid-updates/main Packages                   
Hit http://mirrors.us.kernel.org lucid-updates/multiverse Packages             
Hit http://mirrors.us.kernel.org lucid-updates/restricted Packages             
Hit http://mirrors.us.kernel.org lucid-updates/universe Sources                
Hit http://mirrors.us.kernel.org lucid-updates/main Sources                    
Hit http://mirrors.us.kernel.org lucid-updates/multiverse Sources              
Hit http://mirrors.us.kernel.org lucid-updates/restricted Sources              
Hit http://mirrors.us.kernel.org lucid-proposed/universe Packages              
Hit http://mirrors.us.kernel.org lucid-proposed/main Packages                  
Hit http://mirrors.us.kernel.org lucid-proposed/multiverse Packages            
Hit http://mirrors.us.kernel.org lucid-proposed/restricted Packages            
Hit http://mirrors.us.kernel.org lucid-proposed/universe Sources               
Hit http://mirrors.us.kernel.org lucid-proposed/main Sources                   
Hit http://mirrors.us.kernel.org lucid-proposed/multiverse Sources             
Hit http://mirrors.us.kernel.org lucid-proposed/restricted Sources             
Hit http://mirrors.us.kernel.org lucid-backports/universe Packages             
Hit http://mirrors.us.kernel.org lucid-backports/main Packages                 
Hit http://mirrors.us.kernel.org lucid-backports/multiverse Packages           
Hit http://mirrors.us.kernel.org lucid-backports/restricted Packages           
Hit http://mirrors.us.kernel.org lucid-backports/universe Sources              
Hit http://mirrors.us.kernel.org lucid-backports/main Sources                  
Hit http://mirrors.us.kernel.org lucid-backports/multiverse Sources            
Hit http://mirrors.us.kernel.org lucid-backports/restricted Sources            
Err http://linux.dropbox.com lucid Release.gpg                                 
  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Err http://packages.medibuntu.org lucid Release.gpg                            
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US              
Hit http://linux.dropbox.com lucid Release                                     
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US            
Hit http://linux.dropbox.com lucid/main Packages                               
Hit http://packages.medibuntu.org lucid Release                                
Hit http://packages.medibuntu.org lucid/free Packages                          
Hit http://packages.medibuntu.org lucid/non-free Packages
Hit http://packages.medibuntu.org lucid/free Sources              
Hit http://packages.medibuntu.org lucid/non-free Sources          
Hit http://downloads.sourceforge.net all Release                               
Ign http://downloads.sourceforge.net all/main Packages                         
Ign http://downloads.sourceforge.net all/main Packages                         
Hit http://downloads.sourceforge.net all/main Packages                         
Fetched 197B in 18s (11B/s)                                                    
W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/lucid/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

It's always is like that, around 90%. Again, it's not only the dropbox and medibuntu entries that are giving me trouble. However, I've found that it's not *completely* random. It never happens to mirrors.us.kernel.org or security.ubuntu.com. Maybe it's a third party repo thing?

I pinged security.ubuntu.com. I got 158, 156, 160, 160, and 156 ms. I then pinged packages.medibuntu.org, 166, 169, 165, 165, 164 ms. linux.dropbox.com, 60.3, 60.10, 60.3, 60.5, 61.9 ms. Fine. But another thing, is that both the graphical ping in Network Tools, and command ping took a REALLY long time to get a result of these pings, like a minute, but this time wasn't reported in the latency. The graphical ping in Network Tools just hung (greyed itself out) for that time and reported all the results at once instead of one by one most of the time, and command ping did one ping, sat there for a few seconds doing nothing, did another ping, sat there for a few seconds, etc.

Also for both, it reported some packet loss, but the pings that made it through were at a fine latency. This is really getting my goat, I know I don't have packet loss. I tested it with pingtest.net, and ordinary Skype calls don't have any loss. Maybe my machine is too old? It's been 6 years since I got it, after all...I have upgraded the memory, graphics card, etc, but the processor is a Pentium D 820. That doesn't explain why it can't run ping, though! Ping worked fine in Karmic and Jaunty (command).

Also, I have wireless (g), but that's been working fine for years, never less than 70% signal strength.

I'm at a loss. Is my networking misconfigured?

I hope this information can help. Thanks all. Ask me for more logs if it's required.

---

### Post by LostInBrittany on 2010-05-04
> **ThatBum said:**
> Yeah, I have a DNS, PPPoE set up, NAT working, gateway IP, and all that. It was all preconfigured by SBC when it came here...I knew that for awhile, I configured the wireless in there and came across it. Granted my line is a little noisy because of some bad phone line, or the cheapness of the router, or both, but it didn't cause any problems before.

And I think Medibuntu did go down briefly. medibuntu.org was not found for awhile.

[...]

Example:

```
justyn@FrontRoomBoxLucid:~$ sudo apt-get update

[...]
                                           
W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/lucid/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

It's always is like that, around 90%. Again, it's not only the dropbox and medibuntu entries that are giving me trouble. However, I've found that it's not *completely* random. It never happens to mirrors.us.kernel.org or security.ubuntu.com. Maybe it's a third party repo thing?

I pinged security.ubuntu.com. I got 158, 156, 160, 160, and 156 ms. I then pinged packages.medibuntu.org, 166, 169, 165, 165, 164 ms. linux.dropbox.com, 60.3, 60.10, 60.3, 60.5, 61.9 ms. Fine. But another thing, is that both the graphical ping in Network Tools, and command ping took a REALLY long time to get a result of these pings, like a minute, but this time wasn't reported in the latency. The graphical ping in Network Tools just hung (greyed itself out) for that time and reported all the results at once instead of one by one most of the time, and command ping did one ping, sat there for a few seconds doing nothing, did another ping, sat there for a few seconds, etc.

Also for both, it reported some packet loss, but the pings that made it through were at a fine latency. This is really getting my goat, I know I don't have packet loss. I tested it with pingtest.net, and ordinary Skype calls don't have any loss. Maybe my machine is too old? It's been 6 years since I got it, after all...I have upgraded the memory, graphics card, etc, but the processor is a Pentium D 820. That doesn't explain why it can't run ping, though! Ping worked fine in Karmic and Jaunty (command).

Also, I have wireless (g), but that's been working fine for years, never less than 70% signal strength.

I'm at a loss. Is my networking misconfigured?

I hope this information can help. Thanks all. Ask me for more logs if it's required.

I have often that problem, and the only way out I've found it's to force apt-get to clean its cache :

sudo apt-get update -o Acquire::http::No-Cache=True

---

### Post by Gone fishing on 2010-05-04
My sources.list

> #deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

and

> deb [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free
deb-src [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free

in the mediubuntu.list

Obviously the dropping packets is bad and the taking seconds before being able to ping is bad.

I think you need to find at what places the packets are being dropped. Between the PC and the router, router and ISPs gateway etc.

On my system I get a little packet loss 

PC -> wirelessaccess pt-> wirelessaccess pt  (150m through trees) -> proxyserver -> ADSL router (1 meg for 30+ PCs and Lesotho telephone lines) ->ISPs gateway but I never get more than 3-4% packet loss. If you get more than that you have a problem and it will be unstable on large downloads.

---

### Post by ThatBum on 2010-05-04
> **Gone fishing said:**
> 
Obviously the dropping packets is bad and the taking seconds before being able to ping is bad.

That's the thing, I think nothing is actually dropping. ping just seems to be hanging. The reported ping time is not actually seconds, but the usual millisecond values, for some reason.

My router is a 2wire 2700HG-B. Through the advanced configuration ([http://gateway.2wire.net/mdc](http://gateway.2wire.net/mdc) on my router) shows this (partial):

```
DSL Line (Wire Pair):Line 1 (inner pair)
Downstream Rate Cap: 3008 kbps
Downstream Atten. at 300kHz: 40.8 dB
Uncancelled Echo: 18.5 dB  Suspicious - check phone filters and alarm
VCXO Frequency Offset: -1.8 ppm Ok
Final Rx Gain: 16.9 dB Ok
Impulse Noise Comp. Tones: 0 Ok
Excessive Impulse Noise: 0 Ok
Impulse noise protection: 0.00
Delay of latency path: 0.25 ms
```I see the uncanceled echo. I am told this means I don't have phone filters on something. The check alarm bit is if you have some kind of paging or alarm system that uses the phone line, but that's moot because I don't have one. This has been there since I got the router, and, yes, I'm sure I have filters on everything. The house is from the 50's, and the wiring has never been replaced, so it might just be that. But anyway, this hasn't been a problem before.

More importantly, through bumbling through the router's config, I found a BUILT-IN PING utility. The utility pings directly from the router and not through my computer. I pinged packages.medibuntu.org with it and got this:

```
Pinging [88.191.82.11] 30 times with: 64 bytes of data

ping successful: icmp_seq=0 time=166 ms
ping successful: icmp_seq=1 time=165 ms
ping successful: icmp_seq=2 time=166 ms
ping successful: icmp_seq=3 time=165 ms
ping successful: icmp_seq=4 time=166 ms
ping successful: icmp_seq=5 time=165 ms
ping successful: icmp_seq=6 time=164 ms
ping successful: icmp_seq=7 time=163 ms
ping successful: icmp_seq=8 time=165 ms
ping successful: icmp_seq=9 time=164 ms
ping successful: icmp_seq=10 time=165 ms
ping successful: icmp_seq=11 time=164 ms
ping successful: icmp_seq=12 time=164 ms
ping successful: icmp_seq=13 time=164 ms
ping successful: icmp_seq=14 time=165 ms
ping successful: icmp_seq=15 time=164 ms
ping successful: icmp_seq=16 time=165 ms
ping successful: icmp_seq=17 time=162 ms
ping successful: icmp_seq=18 time=164 ms
ping successful: icmp_seq=19 time=165 ms
ping successful: icmp_seq=20 time=165 ms
ping successful: icmp_seq=21 time=165 ms
ping successful: icmp_seq=22 time=164 ms
ping successful: icmp_seq=23 time=165 ms
ping successful: icmp_seq=24 time=164 ms
ping successful: icmp_seq=25 time=165 ms
ping successful: icmp_seq=26 time=164 ms
ping successful: icmp_seq=27 time=163 ms
ping successful: icmp_seq=28 time=166 ms
ping successful: icmp_seq=29 time=165 ms

```These were ALL INSTANT. Also, by testing with repeated trials, there was no lost packets. This reinforces that there is a problem with the client/router interface, or a bug somewhere. I'm tending to think the latter, because this never happened in Karmic, and I didn't change anything with the router upgrading from Karmic to Lucid. The only thing of significance was that the service was upgraded from 160kBps down/40kBps up to 315kBps down/50kBps up a awhile ago, but, again, this was before Lucid.

Some more router stuff of interest:

```
Current Noise Margin: 20.0 dB/19.0 dB( down/up)
Current Attenuation: 31.6 dB/27.0 dB (down/up)
Current Output Power: 7.9 dBm/2.9 dBm (down/up)
```

```
Collected for 3 days

(Since Reset/Current 24-Hour Interval/Current 15-Minute Interval/Time Since Last Event)

Cell Header Errors:         2612         93         13         0:00:07
Loss of Cell Delineation:         966         56         0         2:39:45
Link Retrains:         13         1         0         2:39:44
DSL Training Errors:         0         0         0         0:00:00
Training Timeouts:         0         0         0         0:00:00
Loss of Framing Failures:         22         1         0         2:39:45
Loss of Signal Failures:         22         1         0         2:39:45
Loss of Power Failures:         0         0         0         0:00:00
Loss of Margin Failures:         22         1         0         2:39:45
Cumulative Seconds w/Errors:         1365         88         26         0:00:07
Cumulative Sec. w/Severe Errors:         39         1         0         2:39:45
Corrected Blocks:         0         0         0         0:00:00
Uncorrectable Blocks:         4031         159         35         0:00:07
DSL Unavailable Seconds:         372         25         0         2:39:21
```

^ This worries me. This has increased since I last checked it. This might be the cause of all this, my bad line quality. I've been wanting to get cable for a long, LONG time, but the only cable provider near my location, Comcast, doesn't have service here. Damn AT&T, or SBC, or Yahoo. They've bought each other out so many times I don't know what they're even calling themselves anymore.

```
NAT Sessions

current secs since boot: 270714
session table 1004/1024 available, 0/512 used in inbound sessions:
sess[24746]: bkt 2, flags: 0x000081a1, proto: 17, cnt: 86
  l: 192.168.1.66:123, f: 208.43.238.3:123, n: 71.134.233.218:123
  lnd: (60,0), fnd: (44,0)
  last used 270651, max_idle: 600
sess[24747]: bkt 2, flags: 0x000081a1, proto: 17, cnt: 86
  l: 192.168.1.66:123, f: 207.171.7.152:123, n: 71.134.233.218:123
  lnd: (60,0), fnd: (44,0)
  last used 270666, max_idle: 600
sess[24748]: bkt 2, flags: 0x000081a1, proto: 17, cnt: 84
  l: 192.168.1.66:123, f: 74.63.201.10:123, n: 71.134.233.218:123
  lnd: (60,0), fnd: (44,0)
  last used 270668, max_idle: 600
sess[24749]: bkt 2, flags: 0x000081a1, proto: 17, cnt: 84
  l: 192.168.1.66:123, f: 207.7.148.214:123, n: 71.134.233.218:123
  lnd: (60,0), fnd: (44,0)
  last used 270703, max_idle: 600
sess[24732]: bkt 4, flags: 0x00000190, proto: 17, cnt: 4638
  l: 71.134.233.218:49172, f: 68.94.156.1:53, n: 71.134.233.218:49172
  lnd: (0,0), fnd: (44,0)
  last used 270711, max_idle: 600
sess[25509]: bkt 4, flags: 0x00008190, proto: 17, cnt: 297
  l: 71.134.233.218:49172, f: 68.94.157.1:53, n: 71.134.233.218:49172
  lnd: (0,0), fnd: (44,0)
  last used 270584, max_idle: 600
sess[24799]: bkt 25, flags: 0x000001a1, proto: 6, cnt: 122
  l: 192.168.1.66:36925, f: 174.36.30.44:80, n: 71.134.233.218:36925
  lnd: (60,0), fnd: (44,0)
  last used 270662, max_idle: 86400
  TCP state ESTABLISHED
  TCP IN: is: 3462921545, sent: 7129, unack'd 0, mss 0, windows_scale 0 
  TCP OUT: is: 1890217321, sent: 6143, unack'd 0, mss 0, windows_scale 0 
sess[25703]: bkt 65, flags: 0x00000190, proto: 17, cnt: 2
  l: 71.134.233.218:12222, f: 68.94.156.1:53, n: 71.134.233.218:12222
  lnd: (0,0), fnd: (44,0)
  last used 270710, max_idle: 600
sess[25704]: bkt 200, flags: 0x000001a1, proto: 6, cnt: 15
  l: 192.168.1.66:57334, f: 75.126.110.108:443, n: 71.134.233.218:57334
  lnd: (60,0), fnd: (44,0)
  last used 270711, max_idle: 86400
  TCP state ESTABLISHED
  TCP IN: is: 2573245654, sent: 1664, unack'd 0, mss 0, windows_scale 0 
  TCP OUT: is: 1318338257, sent: 791, unack'd 0, mss 0, windows_scale 0 
sess[25666]: bkt 212, flags: 0x000085a1, proto: 17, cnt: 2
  l: 192.168.1.66:7094, f: 128.135.138.162:60491, n: 71.134.233.218:7094
  lnd: (60,0), fnd: (44,0)
  last used 270427, max_idle: 600
sess[25667]: bkt 212, flags: 0x000085a1, proto: 17, cnt: 2
  l: 192.168.1.66:7094, f: 24.23.208.118:45679, n: 71.134.233.218:7094
  lnd: (60,0), fnd: (44,0)
  last used 270427, max_idle: 600
sess[25671]: bkt 212, flags: 0x000085a1, proto: 17, cnt: 2
  l: 192.168.1.66:7094, f: 98.244.178.116:57172, n: 71.134.233.218:7094
  lnd: (60,0), fnd: (44,0)
  last used 270473, max_idle: 600
sess[25672]: bkt 212, flags: 0x000085a1, proto: 17, cnt: 2
  l: 192.168.1.66:7094, f: 75.18.166.214:18577, n: 71.134.233.218:7094
  lnd: (60,0), fnd: (44,0)
  last used 270473, max_idle: 600
sess[25675]: bkt 212, flags: 0x000085a1, proto: 17, cnt: 2
  l: 192.168.1.66:7094, f: 114.45.51.228:37544, n: 71.134.233.218:7094
  lnd: (60,0), fnd: (44,0)
  last used 270550, max_idle: 600
sess[25689]: bkt 212, flags: 0x000085a1, proto: 17, cnt: 4
  l: 192.168.1.66:7094, f: 71.143.0.85:2791, n: 71.134.233.218:7094
  lnd: (60,0), fnd: (44,0)
  last used 270630, max_idle: 600
sess[25692]: bkt 212, flags: 0x000085a1, proto: 17, cnt: 2
  l: 192.168.1.66:7094, f: 95.27.81.27:26465, n: 71.134.233.218:7094
  lnd: (60,0), fnd: (44,0)
  last used 270651, max_idle: 600
sess[25693]: bkt 212, flags: 0x000085a1, proto: 17, cnt: 2
  l: 192.168.1.66:7094, f: 140.115.206.40:60384, n: 71.134.233.218:7094
  lnd: (60,0), fnd: (44,0)
  last used 270651, max_idle: 600
sess[25694]: bkt 212, flags: 0x000085a1, proto: 17, cnt: 2
  l: 192.168.1.66:7094, f: 173.2.146.81:5732, n: 71.134.233.218:7094
  lnd: (60,0), fnd: (44,0)
  last used 270651, max_idle: 600
sess[25696]: bkt 212, flags: 0x000085a1, proto: 17, cnt: 2
  l: 192.168.1.66:7094, f: 94.192.245.199:5735, n: 71.134.233.218:7094
  lnd: (60,0), fnd: (44,0)
  last used 270681, max_idle: 600
sess[24763]: bkt 230, flags: 0x000001a1, proto: 6, cnt: 211
  l: 192.168.1.66:46985, f: 71.237.226.138:63973, n: 71.134.233.218:46985
  lnd: (60,0), fnd: (44,0)
  last used 270705, max_idle: 86400
  TCP state ESTABLISHED
  TCP IN: is: 1041512636, sent: 1883, unack'd 0, mss 0, windows_scale 0 
  TCP OUT: is: 1833099151, sent: 4983, unack'd 0, mss 0, windows_scale 0 
```

^The router has a hardware firewall, but I don't think that's doing anything here.

Thanks for sticking with me on this problem.

Oh, and clearing the apt-get cache didn't work. Thanks, though.

---

### Post by pemadorje on 2010-05-05
I believe I might be experiencing a similar issue and it's driving me a little batty.... I did a fresh install of Lucid over the weekend on two different machines and I'm NOT using a proxy. But sudo apt-get update is giving me errors like the following: 

W: Failed to fetch [http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

The thing is, it does appear a little random, as for example, the above ppa may give me the above error and then the next time I run apt-get update it will fail to connect to a different repository. I'm seeing this behavior on two different machines. 

I'm not sure how to resolve this (no pun intended). It's strange as I never saw this issue in either Karmic or Jaunty. I even made a backup of my sources.list after installing and went back to that. It updated fine, I then added the one "docky" ppa above and then the issue starts again. 

I would very much appreciate any advice.

---

### Post by ThatBum on 2010-05-05
> **pemadorje said:**
> I'm not sure how to resolve this

Oh god. That's a groaner, man.

Anyway, yes, same problem. It does seem to be only the repos that are added in addition to the default ones that are causing the problem. That makes sense with only the ones at the end of my updating causing me trouble, because that's where they all are on my sources.list.

---

### Post by pemadorje on 2010-05-05
Sorry, couldn't resist :D

I've been experimenting a little with this tonight and I agree that the issue seems to be only with repos that are added. I'm really lost on this one. I'm also surprised that it's not happening to more people... Or maybe it is...

---

### Post by ravi.xolve on 2010-05-07
@r_vigneshwaran thanks for the tip

---

### Post by pemadorje on 2010-05-07
This issue may be the result of the following bug:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886)

It is also being described in this thread:
[http://ubuntuforums.org/showthread.php?t=1475399&page=2](http://ubuntuforums.org/showthread.php?t=1475399&page=2)

---

### Post by ThatBum on 2010-05-12
Methinks this DOES have to do with my connection, but not by packet loss or latency. Last night my uncanceled echo jumped to 32.9 dB for some inexplicable reason (it's                26.0 dB now). It was so bad that the modem in the router lost the carrier and reset 5 times in a 15 minute time period. Bad.

I learned what uncanceled echo actually is. To quote Wikipedia:

> DSL signals find an impedance discontinuity at the unterminated end,  which reflects back through the cable pair, much like a tennis ball  against a brick wall. The echoed signal is now out of phase and mixed  with the original, creating, among other impairments, attenuation distortion__. The modem  receives both signals, gets confused and "takes errors" or cannot sync.

I probably have a wiring problem, but do to circumstances I cannot fix it. However, I did have uncanceled echo before (albeit not so severe). Some value in apt-get update's config might have changed to reduce the timeout time.

My specific model router is 2700HG-B.

Someone who knows anything about fixing DSL, please, help!

Also, what kind of connections do all of you have?

---

### Post by pemadorje on 2010-05-12
@ThatBum

I’m on AT&T Uverse which I believe is essentially DSL. At first I was thinking, why would the issue just surface in Lucid (since it never occurred before when I was using Karmic) but if some timeout setting was changed (like you suggested), then that would explain it.

I’d like to test this at a friend’s house this weekend (who uses Comcast cable) to see if it exhibits the same behavior.

---

### Post by ThatBum on 2010-05-12
> **pemadorje said:**
> I&#8217;d like to test this at a friend&#8217;s house this weekend (who uses Comcast cable) to see if it exhibits the same behavior.

Good. I have cable at my other house, but it's not my machine and has Windows on it. I'll bring a Live CD and see what happens.

Also, my uncanceled echo has dropped to 7.1 dB. This is the value that it used to be, but the problem still exists. My echo problem is intermittent, apparently. Maybe I have a loose wire somewhere.

Also, do you have a 2wire gateway? AT&T seems fond of giving them out.

There are some useful stats & settings in the "Management and Diagnostic Console" if you do. It's at [http://homeportal/mdc](http://homeportal/mdc) (if you have a password, you need to enter it). The thing that's been bugging me is in the DSL Diagnostics link in the Troubleshooting section.

**EDIT**: Uverse is NOT DSL. According to [this]("http://www.att.com/u-verse/explore/what-is-u-verse.jsp?wtSlotClick=1-002TN9-0-2"), it's fiber optic, or at least part fiber optic. You lucky dog you.

> AT&T U-verse® uses fiber optic* technology  and computer networking to bring you:
  
[LIST]
[*]Advanced digital TV
[*]High speed Internet
[*]Digital home phone service
[/LIST]
> * Fiber optics may apply to all or part of the network,  depending on your location.So it's that kind of service that you get phone, TV, and Internet through one device. That's kinda hard to confuse with DSL, eh? :P This is similar to Comcast Triple Play (which I have at the aftermentioned house), except with fiber, I suppose.

Good luck, yo.

---

### Post by pemadorje on 2010-05-13
> Also, do you have a 2wire gateway? AT&T seems fond of giving them out.

Yes, it's a 2Wire 3800HGV-B.

---

### Post by ThatBum on 2010-05-14
> **pemadorje said:**
> Yes, it's a 2Wire 3800HGV-B.

Yep, it's most certainly not DSL. I think there's a MDC for it, not sure. Go digging around in it and see if you find anything anomalous.

Again, it should be at [http://homeportal/mdc](http://homeportal/mdc). The more user-friendly but less informative interface is the router's internal IP. On mine, for some reason, it's an oddball 192.168.1.254. For most routers, it's 192.164.1.1.

---

### Post by pemadorje on 2010-05-17
@ThatBum

Tested on Comcast this weekend and there were no issues, no "wicked" errors, nothing.... apt-get updated as it should. 

So it does point to an issue with my router or ISP but it's still odd that I never experienced this in Karmic.


Next, I am curious to try "newb85's" suggestion. 

[http://ubuntuforums.org/showthread.php?t=1475399&page=2](http://ubuntuforums.org/showthread.php?t=1475399&page=2)
post #17.

---

### Post by ThatBum on 2010-05-18
> **pemadorje said:**
> @ThatBum
[http://ubuntuforums.org/showthread.php?t=1475399&page=2](http://ubuntuforums.org/showthread.php?t=1475399&page=2)
post #17.

HOLY GOD IT WORKED!

Thank you 6.02x10^23 times!

Well, actually, I didn't use my ISP's DNS, I decided to use OpenDNS. But hey! No more problems with apt-get update!

This must be fixed in some kind update, as many people are experiencing it.

Again, thank you for finding it.

---

### Post by pemadorje on 2010-05-18
Cool!Worked for me also, using OpenDNS.

---

### Post by ThatBum on 2010-05-20
Hey, it seems that there is all sorts of problems with DNS here. Not OpenDNS specifically, I shall describe my problem (which I have fixed).

Again, it has to do with my router. The IP of the gateway fr this router is 192.168.1.254. But, it is also accessible through gateway.2wire.net, which is used for places that are not external sites (they are driven by the router), but it USES the Internet, for example, the router's built-in firmware update function. While trying to do just that, Firefox said it didn't exist. I tried pinging it, and ping said it didn't exist.

I fixed this by going into my /etc/hosts and putting this in:

```
# Lookup for router
192.168.1.254 gateway.2wire.net
```Now it works perfectly. Before Lucid, it worked without modification.

So the whole thing is decidedly not a bug in apt. It appears to be some problem with DNS lookups. It doesn't seem to discriminate between external and internal (private) IPs. A very strange problem indeed.

I got the idea from [this]("http://www.idnetters.co.uk/forums/index.php?action=printpage;topic=10846.0"), a guy who has a similar problem in XP, of all things.

Too lazy to go tell launchpad about this, and I'm starting to think I'm becoming a nuisance there. :)

---

### Post by pemadorje on 2010-05-20
@ThatBum

You may be on to something. I'm not much of a "network guy" and I don't know if this is related to what you're describing.... but I also had an issue after applying the solution of changing my DNS. 

After the change, I wasn't able to access my samba shares with my usual url (smb://hostname/share)... Once I changed it to smb://ipaddress/share, it started working again.

---

### Post by evencoil on 2010-06-10
> **ThatBum said:**
> 
Again, it has to do with my router. The IP of the gateway fr this router is 192.168.1.254. But, it is also accessible through gateway.2wire.net, which is used for places that are not external sites (they are driven by the router), but it USES the Internet, for example, the router's built-in firmware update function. While trying to do just that, Firefox said it didn't exist. I tried pinging it, and ping said it didn't exist.

I fixed this by going into my /etc/hosts and putting this in:

```
# Lookup for router
192.168.1.254 gateway.2wire.net
```Now it works perfectly. Before Lucid, it worked without modification.


I have the same router and your solution worked for me. Thanks! Remember to restart polipo (say if you have Tor installed):
```

sudo service polipo restart

```

---

### Post by ThatBum on 2010-06-11
> **evencoil said:**
> Thanks! Remember to restart polipo (say if you have Tor installed)

My bandwidth is too crap to use Tor effectively, as a client or a relay, but that's good to know I guess, because I do run Tor on my other machine that's on cable.

---

### Post by evencoil on 2010-06-22
Well it worked for a while--then suddenly returned to the old behavior. Hmm...:confused:

---

### Post by ThatBum on 2010-06-25
> **evencoil said:**
> Well it worked for a while--then suddenly returned to the old behavior. Hmm...:confused:

Odd, the DNS shouldn't just change itself...if you're using your ISP's DNS, try using a public DNS, for example, Google's at 8.8.8.8 and 8.8.4.4.

---

### Post by evencoil on 2010-06-25
I think it was due to the symptoms being spotty to begin with...so a solution that looked like a solution wasn't really.

In any case using Google's DNS server works great, thanks!

---

### Post by swajime on 2010-07-02
The sudo -i worked for me ...

I was logged in as root in the first place ... so I don't understand what "sudo -i" has to do with it !!!

```
root@system76-pc:~# aptitude update
Get:1 http://archive.canonical.com lucid Release.gpg [189B]                                                     
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                                        
Get:2 http://archive.ubuntu.com lucid Release.gpg [189B]                             
Hit http://archive.canonical.com lucid Release                 
Hit http://archive.ubuntu.com lucid Release                                        
Hit http://archive.canonical.com lucid/partner Packages                             
Hit http://archive.ubuntu.com lucid/main Sources               
Hit http://archive.canonical.com lucid/partner Sources         
Hit http://archive.ubuntu.com lucid/restricted Sources         
Err http://us.archive.ubuntu.com lucid Release.gpg                                                                           
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates Release.gpg
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-security Release.gpg
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

   <snipped>

Fetched 378B in 3min 57s (2B/s)
Reading package lists... Done

root@system76-pc:~# **[COLOR="Red"]sudo -i[/COLOR]**
root@system76-pc:~# aptitude update

  <snipped ... no errors>

Fetched 567B in 3s (187B/s)
Reading package lists... Done

```

---

### Post by ravi.xolve on 2010-07-03
set the http_proxy variable and the use sudo -E apt-get update.

---

### Post by swajime on 2010-07-03
> **ravi.xolve said:**
> set the http_proxy variable and the use sudo -E apt-get update.

I am sorry, but I don't understand.
Set the http_proxy variable to what value?
I've never (to the best of my knowledge) needed or used a proxy of any sort.

---

### Post by ravi.xolve on 2010-07-03
see the first post. the thread is about it can't resolve address when you access the Internet through a proxy server. If you are accessing directly or through NAT then its not a problem.

to set http_proxy variable on shell:
```

export http_proxy=http://server:port/
```

---

### Post by swajime on 2010-07-03
> **ravi.xolve said:**
> see the first post. the thread is about it can't resolve address when you access the Internet through a proxy server. If you are accessing directly or through NAT then its not a problem.

to set http_proxy variable on shell:
```

export http_proxy=http://server:port/
```

[COLOR="Red"]**Ok ... maybe I left out a detail.**[/COLOR]

> **ravi.xolve said:**
> I installed Lucid. I am sitting behind a passworded proxy therefore I set up this proxy variable:

```
http://user:password@host:port/
```
I also installed Lucid.  **[COLOR="Red"]I don't have a proxy server. I do have a direct connection.[/COLOR]**

> **ravi.xolve said:**
> When I try use apt-get upgrade it shows the following error:

```
Err http://us.archive.ubuntu.com lucid Release.gpg                          
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com lucid-security Release.gpg                   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

.....
```
**[COLOR="Red"]I got exactly the same error[/COLOR]**:
```
Err http://us.archive.ubuntu.com lucid Release.gpg                                                                           
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
```

> **ravi.xolve said:**
> But when I try to use:

```
wget www.google.com
```

it just works fine and gets me the desired page. Looks like there is some problem. I tried using KPackagekit and installed Synaptic manually to resolve it but no help.

Please help me out of this. My PC is just plain OS with no applications I need.
This code also works for me:```
wget www.google.com
```

The reason I posted in the first place was to confirm the workaround given earlier:
> **Gone fishing said:**
>     **[COLOR="Red"]if you sudo -i than put in the command it works[/COLOR]** but sudo doesn't.
I did not have this issue prior to my upgrade to Lucid.  I am content with the fact that I found the workaround in this thread that allowed me to do what I wanted to do.

---

### Post by ThatBum on 2010-07-04
> **swajime said:**
> I also installed Lucid.  **[COLOR="Red"]I don't have a proxy server. I do have a direct connection.[/COLOR]**

Do you have an actual out-of-the-modem direct connection, or is it through a router with NAT? That is, is the machine's local IP in the 192.168/16 block? The problem seems to be that Ubuntu, or at least aptitude, is unable to fetch or is not aware of the DNS addresses from the router, because Network Manager has the router's IP under the DNS addreess field...although this was also the case in Karmic (and in Windows, for that matter), so I don't really know what's going on. People without routers don't seem to have this problem. I can't say about proxies, as I don't use one.

---

### Post by gtmarks on 2011-06-16
I have the same problem (but with update rather than upgrade).  This isn't exactly a solution, but the following bash script makes the problem less annoying:

```

#! /bin/bash
#
# Run sudo apt-get update until success.
#
echo "sudo apt-get update"
echo ""
EXITSTATUS=1
until [ ${EXITSTATUS} -eq 0 ]
   do
      sudo apt-get update
      EXITSTATUS=$?
      if [ ${EXITSTATUS} -ne 0 ]
         then
            echo ""
            echo "Exit status nonzero.  Retrying in three seconds."
            echo ""
            sleep 3
      fi
done
```

(As written, the script could run forever, but I have not yet seen this happen.)

---

