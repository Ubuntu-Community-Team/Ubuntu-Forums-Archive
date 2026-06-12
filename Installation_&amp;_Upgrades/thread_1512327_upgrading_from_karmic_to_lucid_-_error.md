---
title: "upgrading from karmic to lucid - error"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by mephist0pheles on 2010-06-18
Error during commit
'E:Internal Error, Could not perform immediate configuration (2) on mountall'
Restoring original system state


Yeah...that's what I get every time I try to upgrade to lucid lynx.

NOTE: I haven't updated for quite some time. I may have gotten one or two updates for karmic but that was it. Just thought it might be important....

NOTE: Also not sure if this is important, but karmic installed and did some funny stuff to itself. My desktop no longer exists. It just isn't there. Also, when I try to turn of my computer it gets all kinds of errors and eventually I have to just pull the plug....something about a dev loop0 right after is says its deactivating swap...

---

### Post by mephist0pheles on 2010-07-16
bump

I tried it again after quite a long wait...

**Could not install the upgrades**

[B]Error during commit
'E:Internal Error, Could not perform immediate configuration (2) on mountall'
Restoring original system state[/B]

anybody at all?

---

### Post by davidmohammed on 2010-07-16
you are probably suffering this[ bug]("https://bugs.launchpad.net/ubuntu/lucid/+source/mountall/+bug/559582")...

couple of suggested fixes in there

are you running 32bit or 64bit?

if 64bit possibly post 16 is that bug report will resolve your issue.

---

### Post by mephist0pheles on 2010-07-16
Stupid question...how do I figure out whether I'm running 64 or 32 bit? I knew how to do it on Windows but then I switched over and now there's a couple of basic things I can't seem to keep track of...

---

### Post by mephist0pheles on 2010-07-16
So I went to post 16 and...

mephisto@ubuntu:~$ sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list
[sudo] password for mephisto: 
mephisto@ubuntu:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Translation-en_US                       
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en_US                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Translation-en_US                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Translation-en_US         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                          
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                         
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg [189B]                     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_US                   
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [1,008B]                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Get:5 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release [1,019B]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources    
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources [426B]             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                    
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages
Fetched 59.2kB in 1s (40.6kB/s)
Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
mephisto@ubuntu:~$ wget [http://mirrors.kernel.org/ubuntu/pool/main/m/mountall/mountall_2.11_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/m/mountall/mountall_2.11_amd64.deb)
--2010-07-16 17:00:01--  [http://mirrors.kernel.org/ubuntu/pool/main/m/mountall/mountall_2.11_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/m/mountall/mountall_2.11_amd64.deb)
Resolving mirrors.kernel.org... 149.20.20.135, 204.152.191.39
Connecting to mirrors.kernel.org|149.20.20.135|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-07-16 17:00:02 ERROR 404: Not Found.

mephisto@ubuntu:~$  



^at that point I figured it was not working...does that mean I'm running 32?

---

### Post by davidmohammed on 2010-07-16
type uname -a

i686 means 32bit
x86-64 means 64bit  (I think)

---

### Post by davidmohammed on 2010-07-16
...

suggest go to administration - software sources

select the other software tab.  Untick ALL the sources there..

then run

sudo apt-get update
sudo apt-get upgrade.

hopefully you will get a clean update first before you try to upgrade.

---

### Post by mephist0pheles on 2010-07-16
Ok, I got that second part working after removing WineHQ from my software sources...but now I'm getting: 

mephisto@ubuntu:~$ wget [http://mirrors.kernel.org/ubuntu/pool/main/m/mountall/mountall_2.11_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/m/mountall/mountall_2.11_amd64.deb)
--2010-07-16 17:10:40--  [http://mirrors.kernel.org/ubuntu/pool/main/m/mountall/mountall_2.11_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/m/mountall/mountall_2.11_amd64.deb)
Resolving mirrors.kernel.org... 204.152.191.39, 149.20.20.135
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-07-16 17:10:41 ERROR 404: Not Found.



EDIT: It would seem I'm running 32-bit linux.

---

### Post by davidmohammed on 2010-07-16
...
try a different source location 

in the same software sources screen first tab click the drop down on download location - select other.

Choose another source location different from your current one.

---

### Post by davidmohammed on 2010-07-16
... by the way - your are 64bit - your error message says it was trying to download a 64bit deb file

---

### Post by mephist0pheles on 2010-07-16
When I untick all the sources in the other tab, I get:

mephisto@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


...and nothing happens.

---

### Post by davidmohammed on 2010-07-16
... no ignore what I just said - you are definitely 32bit?

then post 16 should be adjust slightly

instead of the 64bit mountall deb file use the file

mountall_2.15_i386.deb...

to clarify

sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list
sudo apt-get update
wget [http://mirrors.kernel.org/ubuntu/pool/main/m/mountall/mountall_2.15_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/m/mountall/mountall_2.15_i386.deb)
sudo dpkg --force-all -i /var/cache/apt/archives/mountall_2.15_i386.deb
sudo apt-get -f install
sudo apt-get dist-upgrade

---

### Post by mephist0pheles on 2010-07-16
By the way, while that's all going on in my terminal, I have another question to ask.

When I upgraded to karmic, my desktop disappeared. As in it just completely...went away. It's just blackness and when you try to move a window or something over it, that window lags a bit...probably because the background that's supposed to be there is just not there at all. This might have something to do with the fact that I first upgraded to one of the early beta builds of karmic as a tester way before it was released.

Will this upgrade by any chance get my desktop back?

---

### Post by davidmohammed on 2010-07-16
...

possibly.  However make sure you've got a good backup first of all of your critical data.

Some people recommend that for PCs in your situation, a fresh install would be better since obviously it will clear out any rubbish and corruption you may have.

---

### Post by mephist0pheles on 2010-07-16
A fresh install as in uninstall Ubuntu and then get a Lucid disk and install that from Windows? If so, that's a difficult proposition. I've got a whole ton of stuff I'd have to back up and at the moment I don't have the external memory to back it up. 

I suppose I could put my documents on Google documents but there's gigabytes of other stuff and I don't have a flash drive or external drive to take care of it at the moment.

This install is going to take a while, it seems, as I have not updated my system since about a month after karmic came out.  :P

---

### Post by davidmohammed on 2010-07-16
good luck!  You are braver than me - I always backup first.  It's worth investing in a external hard-drive to backup.  Just imagine what you will lose if your hard-drive decides to eat itself...!

---

### Post by mephist0pheles on 2010-07-16
Well thanks, that makes me feel so very confident...I didn't even know that could happen. I guess I just assumed my hard drive wasn't cannibalistic...or even carnivorous...




By the way, thanks in advance. I'm confident things will work out as things seem to be going smoothly. I appreciate your help.

---

