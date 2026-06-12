---
title: "apt-get problems with Gusty server"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by danisheater on 2008-10-24
[FONT="Arial"]Hi-

Over past week I can not install new packages, update or upgrade Ubuntu 7.10 server (Gusty Gibbon).  Connection times out every time.  Have tried changing /etc/apt/sources.list to 2 different mirrors.  Originally was us.archive.ubuntu.com, also tried removing the us and then tried switching to Argonne National Lab mirrors.

Other machines (all desktop edition, coincidentally) are apt-get-ing okay with either gusty or hardy.

Any suggestions?  Read randomly something about gpg keys but I don't really know what that is.  Error and sources file below.

Thanks a bunch.

-Anders[/FONT]

[FONT="Arial Black"]Below is my "original" etc/apt/sources.list file:[/FONT]


[FONT="Courier New"]#
#deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted

#deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse[/FONT]

[FONT="Arial Black"]Error message:[/FONT]

[FONT="Courier New"]/etc/apt$ sudo apt-get update
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                                                                      
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                                                               
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US                                                        
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US                                                    
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg                                                                      
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45), connection timed out [IP: 91.189.88.45 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US                                
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US                                  
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US                                
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                                             
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45), connection timed out [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45), connection timed out [IP: 91.189.88.45 80]
0% [Connecting to us.archive.ubuntu.com (91.189.88.46)][/FONT]

---

### Post by dabl on 2008-10-24
Do you have ANY networking connectivity on that server?  One could wonder if ethernet is even working.

---

### Post by danisheater on 2008-10-24
Yeah.  I can access the server remotely, can view webpages served by it.  It can also ping outside sites sucessfully (google).  Interestingly, though, when I ping archive.ubuntu.com, for example, I get 100% packet loss.

When I ping from my desktop edition gusty or hardy machines, I can ping archive.ubuntu.com sucessfully.

So question is why repositories "don't like" my server.

Thanks for the suggestion though, dabl.  Certainly I've made many dumb mistakes like that in the past.

---

### Post by dabl on 2008-10-24
I dunno -- maybe a firewall setting?  Is there a place where you can set the types of protocols that are allowed?  Maybe it allows FTP but not HTTP or something like that.  Weird ....  :confused:

---

### Post by danisheater on 2008-10-24
> **dabl said:**
> Is there a place where you can set the types of protocols that are allowed?  

Now that is an excellent question.  I do not know the answer, but you are getting me thinking along the lines of where to look next.

The only caveat is that I haven't had problems in the past and don't know of any changes to my network, but guess I should bother the network admin guys again.

Thanks dabl.

---

### Post by danisheater on 2008-10-24
> **dabl said:**
> I dunno -- maybe a firewall setting?  Is there a place where you can set the types of protocols that are allowed?  Maybe it allows FTP but not HTTP or something like that.  Weird ....  :confused:

One other thing I should have mentioned.  The hardy and gutsy desktop editions that seem to update no problem are on the same network and hence should go through the same network firewall if one exists.  If I was mis-interpreting what you meant dabl about firewalls (I frankly don't know anything about setting up a machine firewall in ubuntu although I have tweaked some squid settings for who can access this server before), my apologies for the red herring here.

---

### Post by dabl on 2008-10-24
I truly don't know -- I was stabbing in the dark, in the absence of better help for you.  I'm not qualified to administer a server on a network, but I've played around on the home Linux system enough to encounter the occasional networking issue.  It seems as though there is something set on that server box, differently from your other desktops, that keeps it from accepting data from the ubuntu.com sites.

---

