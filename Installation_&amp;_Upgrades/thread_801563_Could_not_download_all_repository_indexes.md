---
title: "Could not download all repository indexes"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by globalhawk on 2008-05-20
[FONT="Lucida Console"]Hello  everyone,

It has been a couple of weeks and` I am not able to figure out whats going on.
I am trying to update / upgrade the OS  and I keep getting this constant error:
**"COULD NOT DOWNLOAD ALL REPOSITORY INDEXES"**

Please forgive my ignorance on the subject.....I switched to ubuntu in the hopes that it would be more user friendly but I just keep getting errors all over the place.
If anyone can help with some advice as to how to proceed it would be greatly appreciated.

Thanks..... :)[FONT="Lucida Console"][/FONT][/FONT]

---

### Post by MaindotC on 2008-05-20
Did you do this from the command line doing:
```

sudo apt-get update
sudo apt-get upgrade

```
Or did you do this using the Software Updater in System->Administration?

Also, please post the contents of the /etc/apt/sources.list file.

---

### Post by Pumalite on 2008-05-20
From Terminal: post:
cat /etc/apt/sources.list

---

### Post by globalhawk on 2008-05-20
Alan.....thanks for your prompt reply.
I ahve done this from the GUi itself.

---

### Post by globalhawk on 2008-05-20
Puma....couldn't agree more with you......but there was a time I would spend hours hacking at this.....today I don't have the time for that. With my XP machine I download the updates they install automatically and I keep going. I just don't have the time .

---

### Post by globalhawk on 2008-05-20
Find below contents of requested file:

#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

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

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy main universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main universe restricted
deb [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy-updates main universe restricted

---

### Post by Pumalite on 2008-05-20
Sorry to hear you are such a busy guy.

---

### Post by globalhawk on 2008-05-20
Please find contents below:
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

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

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy main universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main universe restricted
deb [ftp://ftp.gtlib.gatech.edu/pub/ubuntu](ftp://ftp.gtlib.gatech.edu/pub/ubuntu) gutsy-updates main universe restricted

---

### Post by Pumalite on 2008-05-20
Maybe gatech if giving you problems. Why don't you change them to the main stream repos?
Post the output of:
sudo aptitude update

---

### Post by globalhawk on 2008-05-20
Puma......I changed to the Main server and the below is the result. As a matter of fact I get these error on most of the servers I select.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done

---

### Post by Pumalite on 2008-05-20
Double check your connection.

---

### Post by globalhawk on 2008-05-20
Puma....I have.....! I am able to browse.....and communicate with you thru the machine in question and also to use other Internet related tools. I don't know why this particular appliaction/tool defaults to an error.

---

### Post by globalhawk on 2008-05-20
Puma...any other suggestions a to what I can check for.....?

---

### Post by globalhawk on 2008-05-20
Puma...I was able to do some additional checks and then re-ren the coomand you gave me from the promt and here are the results.Please let me know your thoughts.


gerardo@Massiach:/etc/apt$ sudo aptitude update
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not resolve 'localhost'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
  Could not resolve 'localhost'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
  Could not resolve 'localhost'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not resolve 'localhost'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
  Could not resolve 'localhost'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
  Could not resolve 'localhost'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
  Could not resolve 'localhost'
Hit [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy Release.gpg
Get:1 [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/main Translation-en_US
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/main Translation-en_US
Get:2 [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/universe Translation-en_US
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/universe Translation-en_US
Hit [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates Release.gpg
Get:3 [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/main Translation-en_US
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/main Translation-en_US
Get:4 [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/universe Translation-en_US
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/universe Translation-en_US
Get:5 [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/restricted Translation-en_US
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/restricted Translation-en_US
Get:6 [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy Release [65.9kB]
Get:7 [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates Release [58.5kB]
Hit [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/main Packages
Hit [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/universe Packages
Hit [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/main Packages
Hit [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/universe Packages
Hit [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/restricted Packages                    
Fetched 124kB in 13s (9498B/s)                                                       
Reading package lists... Done

---

### Post by MaindotC on 2008-05-20
post the output of 
```

cat /etc/resolv.conf

```

I'm going to bed so I'll continue this tomorrow.

---

### Post by globalhawk on 2008-05-20
No Problem my friend.......sleep good and thanks again for your assistance. Find below requested info:
gerardo@Massiach:/etc$ cat resolv.conf
nameserver 68.87.74.162
nameserver 68.87.68.162
gerardo@Massiach:/etc$

---

### Post by globalhawk on 2008-05-21
Alan....good morning!
I am able to surf and use other tools that require outside connectivity without any problems. But as soon as "SOFTWARE SOURCES" or if I run the "ADEPT MANAGER"  I get erors. I just ran the Adept Manager to do a VERSION UPGRADE  and I see network activity on the screen (progress bar) and in Wireshark protocol analyzer I see traffic to and fro.
Below is the error message I get when I try to do a Version Upgrade.


Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

Alan...where does port 4001 and IP address 127.0.0.1 come from......? becuase I am setup up for DHCP and my router dispenses IP addresses and I am able to cummunicate nevertheless.

Thanks for your input.

---

### Post by Pumalite on 2008-05-21
Hi:
Check /etc/localhost

---

### Post by MaindotC on 2008-05-21
I dunno if you knew this but I had you post resolv.conf because that stores the address of DNS servers you use for name resolution and they're usually assigned by DHCP.  I checked the addresses and they seem fine - comcast's DNS servers in Naples.

Hawk do you have a network proxy address defined in System -> Preferences -> Network Proxy?

---

### Post by MaindotC on 2008-05-21
Oh I just now saw your post an hour ago.  I can answer those questions.  127.0.0.1 is called the "loopback" address and is the address that the machine uses to refer to itself.  I can explain in more detail if you wish.  Yes your router does dispense addresses, and a lot of other information such as DNS, and typically the way this happens is the router says "look anything you need, send it to me and I'll handle the request for you."  

What strikes me as odd is that your router assigned your machine the DNS addresses of Comcast.  There's nothing wrong with this, but typically the router gives its own address as the DNS server and then once it receives a DNS request it does the name lookup and sends back the information.

I'm not sure about port 4001 because I did an apt-get update/upgrade and mine was through port 37228 (I also used wireshark to verify).

---

### Post by MaindotC on 2008-05-21
You know since you're behind a router, I wonder if you have any ports shut off on the router that apt-get needs to use.  Can you try logging into your router and opening port 4001?  This port may be randomized so I'm not sure if it'll be the same each time.  If that's not working, please try plugging directly into your cable modem (or whatever you have) and doing an apt-get update that way.

---

### Post by Pumalite on 2008-05-21
If you have a router: set it to give you DHCP and a dynamic address at boot. Tht's in my opinion the best way.

---

### Post by globalhawk on 2008-05-21
Puma.....I DON"T have a localhost under /etc directory.

---

### Post by Pumalite on 2008-05-21
Sorry; /etc/hosts
[http://ubuntuforums.org/showthread.php?t=778605&page=5](http://ubuntuforums.org/showthread.php?t=778605&page=5)

---

### Post by globalhawk on 2008-05-21
Puma....below is the data for file "hosts"

gerardo@Massiach:/etc$ cat hosts

# The following lines are desirable for IPv6 capable hosts
192.168.1.12 Massiach
127.0.0.1 localhost
gerardo@Massiach:/etc$

---

### Post by globalhawk on 2008-05-21
No I don't. I am conigured for a "direct connection" to the internet.

---

### Post by globalhawk on 2008-05-22
Good morning guys......to be honest I don't know what else to check. I 've gone through all the network setting options and they all look ok.
Alan....I did what you suggested i.e I connected straight to the cable modem and I am still getting the same results. I see traffic to n fro on Wireshark when I try to initiate and OS UPGRADE on the download Progress Bars and then it times out. Below is the results of latest attempt connected to cable modem.

Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

Alan....where is she getting  info that port 4001 IP 127.0.0.0.1 is to be used?

Hawk

---

### Post by globalhawk on 2008-05-22
Good morning guys......to be honest I don't know what else to check. I 've gone through all the network setting options and they all look ok.
Alan....I did what you suggested i.e I connected straight to the cable modem and I am still getting the same results. I see traffic to n fro on Wireshark when I try to initiate and OS UPGRADE on the download Progress Bars and then it times out. Below is the results of latest attempt connected to cable modem.

Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

Alan....where is she getting  info that port 4001 IP 127.0.0.0.1 is to be used?

Hawk

---

### Post by MaindotC on 2008-05-22
[QUOTE=globalhawk]
Alan....where is she getting  info that port 4001 IP 127.0.0.0.1 is to be used?

Hawk[/QUOTE]

Wow this is frustrating.  It seems that your distribution has decided to use port 4001 to connect to the ubuntu repositories.  I'm not precisely sure what's going on here - for example it may standard procedure for the apt-get function to refer to a service running on itself (127.0.0.1) at port 4001 and then that service goes out and issues the update.

I know I asked you this before but did you try doing an apt-get update from the command line, and then an apt-get upgrade?  This isn't the command for a distribution upgrade, just update the current packages for your current system.

Another option is to try a different sources.list.  Save a copy of your sources.list - I recommend the following command:
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup

```
I'm attaching my copy of sources.list.  I'm using 7.10 so if you're using Hardy just replace any word that says "gutsy" with "hardy".  I couldn't upload the file as it was because the forum won't allow it so I renamed it .deb.  Remove the .deb and name it sources.list and give that a try.

---

### Post by globalhawk on 2008-05-22
Frustrating....tell me about it.
You know I've been wanting to migrate to Linux for some years now...Alan.....and I just get discouraged.
There was a time in my life where I would not mind spending the time and energy hacking around this......but those days are over. We live in a different world today. Today I just don't have the time for this. I want to move away from Windows and when I make the step I encounter this any many other issues with Linux. If Linux is going to come into the arena they have to come better than this. I've trien Red Hat, SUSE and now Ubuntu and there is always some issue arising. I am not saying that WINDOWS doesn't have its issues but at least I have some smooth saling going on. If I am going to down load applications or software for Linux that turns into a night mare to install. With Windows I click a couple of buttons and thats it......I keep on moving. I hope you get my point.

Anyway...enough of that. I tried your suggestions a ran the ADEPT MANAGER  with YOUR sources.list file and these are the results:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) Could not resolve 'localhost'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2) Could not resolve 'localhost'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg) Could not resolve 'localhost'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2) Could not resolve 'localhost'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg) Could not resolve 'localhost'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2) Could not resolve 'localhost'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg) Could not resolve 'localhost'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2) Could not resolve 'localhost'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz) Could not resolve 'localhost'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz) Could not resolve 'localhost'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz) Could not resolve 'localhost'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz) Could not resolve 'localhost'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz) Could not resolve 'localhost'


Don't know what else to try.....I guess I'll just order the 8.04 CDs and to a fresh install from them.

---

### Post by MaindotC on 2008-05-22
I really think that router is a problem - it doesn't seem to be forwarding your requests properly.  Move your old source.list back in there, connect directly to your internet connection, then reboot.  Try the apt-get update again.

---

### Post by globalhawk on 2008-05-22
Alan......did that....restored my original sources.list file and connected staright to the cable modem bypassing the router and I am still not able to Upgrade. I am able to use OTHER internet related programs without any problems with the above scenario.

---

### Post by MaindotC on 2008-05-22
When you did that did you renew your DHCP settings?  If you can still use other services, then you shouldn't be having a problem with name resolution.  It sounds to me like there's a problem with apt.  I don't know why - or how - because it's standard on all debian distributions - and I doubt you did anything with it like configured it manually or something, but my opinion is there's a problem with apt.

The problem I have is once you uninstall apt, I'm not really sure how you install it because you'll need apt to re-download and configure apt.  Check with some other users, but my suggestions is to find out how to uninstall apt, then re-install it from the CD.  I don't know how to do this.

---

### Post by globalhawk on 2008-05-28
Thnks for all your input....Buddy...! I'll see what I can dco.

---

### Post by MaindotC on 2008-05-29
I just recently found a resolution to a problem using "aptitude" instead of "apt".  Can you try using it instead?  Try:
```

sudo aptitude update
sudo aptitude safe-upgrade

```

---

### Post by gary vollink on 2008-06-03
This is just a guess...

It looks like you are trying to connect to a proxy server on your local host that isn't working... [ export http_proxy=http://localhost:4001 ] or similar is probably set up in your user profile.

---

### Post by MaindotC on 2008-06-03
globalhawk what's the status on this problem?

---

### Post by hasqual on 2008-06-05
I just followed and read this post because I am experiencing a similar problem (although maybe mine's easier?).  Whenever I try to update now I get the following errors:

*********************************************************************

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

***********************************************************************

Any thoughts?  Just for the record, I upgraded from 7.10 to 8.04, perhaps this is a known issue or not.  I'm no computer genius, so the things I notice may be dumb.  I'm a comcast customer and currently behind a router.  I tried the "aptitude" thing, but I still get the same error.  

I know I jumped in late, and if my problem is addressed elsewhere, sorry about that and if you'd point me in the right direction I'd be grateful.  Alternatively, if you have thoughts on how to solve this and want me to try things and post back, I'll be glad to also.  Thanks!

~Jack

---

### Post by iaculallad on 2008-06-05
> **hasqual said:**
> I just followed and read this post because I am experiencing a similar problem (although maybe mine's easier?).  Whenever I try to update now I get the following errors:

*********************************************************************

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

***********************************************************************

Any thoughts?  Just for the record, I upgraded from 7.10 to 8.04, perhaps this is a known issue or not.  I'm no computer genius, so the things I notice may be dumb.  I'm a comcast customer and currently behind a router.  I tried the "aptitude" thing, but I still get the same error.  

I know I jumped in late, and if my problem is addressed elsewhere, sorry about that and if you'd point me in the right direction I'd be grateful.  Alternatively, if you have thoughts on how to solve this and want me to try things and post back, I'll be glad to also.  Thanks!

~Jack

Navigate to System->Administration-Software Sources, and under the "Ubuntu Software" tab, uncheck the checkbox for  "Installable from CD-ROM/DVD" option. And be sure to check all the Main, Universe, Restricted, and Multiverse.

Drop to your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by hasqual on 2008-06-05
Well crap and no crap.  

Before I saw the response I continued my hunt and found this thread:

[http://ubuntuforums.org/showthread.php?t=753668&page=2](http://ubuntuforums.org/showthread.php?t=753668&page=2)

I copied the sources.list file in the page (not sure at all if it's a "complete" file, or a good one or not), saved a backup of my original, and ran it and VOILA ... it upgraded then.  I checked to make sure the install from CDROM was unchecked like you mentioned, and it was.  

So, the other page solved my issue, and I'm unsure if the proposed solution here would have or not ... got by it though.  If you have any comments on the sources file being good or bad or any other thoughts, I'm all ears (or eyes or whatever).  Thanks!

~Jack

---

### Post by MaindotC on 2008-06-06
I don't know what the hell is going on with globalhawk but I'm unsubscribing.  Can't have this jamming up my subscription folder.

---

