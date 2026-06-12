---
title: "unable to update (could not resolve 'home')"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by loic_ on 2006-08-09
hello everybody

I post here because I couldn't solve my problem on [www.ubuntu-fr.org](www.ubuntu-fr.org) .

Well here it is : I've just upgraded from Breezy to Dapper, using [this]("https://help.ubuntu.com/community/DapperUpgrades") (actually [this]("http://doc.ubuntu-fr.org/installation/migration_breezy_dapper"), but it is roughly the same )

It seemed to work perfectly, got around 800 packages, installed it, have the 2.6.15-26-386 kernel, the new GNOME version, no problem with hardware...

BUT, update manager tells me I have 323 updates available, which means my upgrade is uncomplete. As I tried to download it (either with synaptics or apt-get), for EACH packages I got the message
```
unable to get http://archive.ubuntu.com/ubuntu/pool/***  Could not resolve « home »
```

As suggested in the tutorial, I did :
```
   sudo apt-get -f install
   sudo dpkg --configure -a 
```Nothing happened.
I tried again 'upgrade' and 'dist-update', but here it didn't work

At first I thought it was a problem with my permission in $HOME, because during login the message saying that .drmc have to be in 644, Well I sorted this out, but it seemed to be unrelated with the problem I am talking about.

Then I examined carefully all the packages I currently have, and realised I haven't the ubuntu-desktop package, even if the upgrade seemed to work.
Maybe I should download it, but without any apt manager it seems difficult:-? 

Does anyone have a clue ?

Thanks
Loic

---

### Post by randell6564 on 2006-08-09
Please post your /etc/apt/sources.list

---

### Post by loic_ on 2006-08-10
here it is :

```
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```

doesn't look too bad for me... does it ?

---

### Post by caffine_fizz on 2006-08-10
I had a similar problem to this yesterday, fix that worked for me explained in : [http://www.ubuntuforums.org/showthread.php?t=232720]("http://www.ubuntuforums.org/showthread.php?t=232720")

deleting the lines in the **/etc/apt/apt.conf** file fixed my problem.

i also deleted the line in my **/etc/apt/sources.list** that related to grabbing stuff of the cd, generally at the top.

I'm new to linux so take a back up of these files before you try this just incase i'm giving you the wrong info, but my servers been running sweet ever since.

let me know how you go

caffine_fizz

---

### Post by loic_ on 2006-08-10
gosh it looks like I don't have an apt.conf file ! :-?

---

### Post by caffine_fizz on 2006-08-10
That's strange, i'm usin 6.06 and i have one?

can you connect to the net, ping by ip and more so name?

It might be a problem with you dns, what is the contents of your **/etc/resolv.conf**

---

### Post by loic_ on 2006-08-10
I don't have other problem with the internet (I assume).

I don't think it is a problem with my DNS, anyway here it is : 

```
search mshome.net
nameserver 192.168.0.1
```
(the shorter the better ! ;))

my pc is currently connected to the internet *via*another PC which turns on winXP :-&

---

### Post by caffine_fizz on 2006-08-10
My understanding of it the /etc/resolv.conf file should contain the dns servers of your isp. the reason it'd work fine on your other machine is that you have got that configured correctly. 

the line: 
nameserver 192.168.0.1

i asume is your router, i'd replace that with the primary and secondary dns servers of your isp, this should fix it?

so 

nameserver ###.###.###.###
nameserver ###.###.###.###

if this doesn't fix it post your **/etc/network/interfaces**

let me know

---

### Post by loic_ on 2006-08-10
yes 192.*** is my router.

My router is configured in Windows as "obtain DNS server address automatically" (freely translated from the french, you got the idea I guess), So I can't see them
do you how to get it (yes this a question about Windows, some of you may have used it before... ;) )

---

### Post by caffine_fizz on 2006-08-10
are you on dial-up or broadband?

assuming broadband (because you have a router) you should be able to log into the modem/router using your browser in windows using:
**[http://###.###.###.###](http://###.###.###.###)** where #'s make up your router/modem ip address. it should be listed somewhere in this configuration.

The other place to try might be to log into your account with your isp's web site, where it should be also listed.

let me know

p.s. like i said ealier i'm still a linux noob, if anyone else is reading this and feels i'm givin the wrong info, please correct me (just want to give something back).

---

### Post by loic_ on 2006-08-10
Found them. Nothing's changed...

here is my interfaces  (comments are mine):

```
#loopback interface
auto lo
iface lo inet loopback 

auto eth2

iface eth0 inet dhcp #don't know wich one it is

iface eth2 inet dhcp #ethernet connection

iface eth1 inet dhcp #wifi connection, I don't use it currently

auto eth2
```

---

### Post by loic_ on 2006-08-10
well new stuff :

I tried to execute apt-get in a "Failsafe Terminal" Session : It worked ! :) So I downloaded ubuntu-desktop , as well as a 'dist-upgrade'. 
I have got a brand new ubuntu BUT I still can't install a new package in a "standard" session :(

---

