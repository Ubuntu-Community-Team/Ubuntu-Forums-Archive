---
title: "Ubuntu Mate won't upgrade"
date: 2016-12-15
forum: Installation &amp; Upgrades
---

### Post by heroquestelf on 2016-12-15
I just put a fresh install of Ubuntu MATE (16.04.1) on my Toshiba laptop, and it will not update. The software updater errors out, and when I try and install from the terminal, it locks up almost immediately. 

Here is where it stops.

```
jonathan@jonathan-Satellite-P305:~$ sudo apt-get update
[sudo] password for jonathan: 
Hit:1 http://ppa.launchpad.net/ubuntu-mate-dev/welcome/ubuntu xenial InRelease 
0% [Connecting to us.archive.ubuntu.com (2001:67c:1562::19)] [Connecting to sec

```

suggestions?

---

### Post by heroquestelf on 2016-12-15
When I ping us.archive.ubuntu.com I get the following

```
64 bytes from economy.canonical.com (91.189.91.23): icmp_seq=105 ttl=49 time=50.3 ms
64 bytes from economy.canonical.com (91.189.91.23): icmp_seq=106 ttl=49 time=51.9 ms
64 bytes from economy.canonical.com (91.189.91.23): icmp_seq=107 ttl=49 time=51.8 ms
^C
--- us.archive.ubuntu.com ping statistics ---
107 packets transmitted, 107 received, 0% packet loss, time 106163ms
rtt min/avg/max/mdev = 49.898/130.649/339.625/79.744 ms


```

---

### Post by #&amp;thj^% on 2016-12-15
Did you add this PPA during the install?
> ppa:ubuntu-mate-dev/welcome

Also you could try changing US server to Main
EDIT: There seems to be a lot of update errors being posted as i type this...maybe let things settle for a bit of time and try again.

See These fresh posts: [https://ubuntuforums.org/showthread.php?t=2346524](https://ubuntuforums.org/showthread.php?t=2346524)

[https://ubuntuforums.org/showthread.php?t=2346521](https://ubuntuforums.org/showthread.php?t=2346521)

---

### Post by heroquestelf on 2016-12-15
Actually, I discovered something. I tried to install something and got called away from the machine, and when I came back to it ten minutes later, I found it right in the middle of an install. 

So I tried the update process again, and this time it worked.... it just took for-[B]EVER.

[/B]I can install and update stuff, it just takes a tremendous amount of time.

---

### Post by oldrocker99 on 2016-12-15
It's possible to have problems with a mirror; I did on my fresh install. I did a ping test and found that the best mirror for me is tripadvisor.com. It works flawlessly for me and is quick.

---

### Post by heroquestelf on 2016-12-16
I did a little playing around. First I used the Software and Updates tool to automatically choose my best mirror. It told me to use mirror.symnds.com/ubuntu. So I did, and ran a 
```
sudo apt-get update
```

It was not significantly faster. 

I then installed Netselect and ran the following code: 
```

sudo netselect -v -s10 -t20 `wget -q -O- https://launchpad.net/ubuntu/+archivemirrors | grep -P -B8 "statusUP|statusSIX" | grep -o -P "(f|ht)tp.*\"" | tr '"\n' '  '`


```

Here was my result:
```

   49 http://mirror.network32.net/ubuntu/
   51 http://mirror.network32.net/ubuntu/
   92 http://ubuntu.osuosl.org/ubuntu/
   94 http://ubuntu.osuosl.org/ubuntu/
   96 http://ro-mirrors.evowise.com/ubuntu/
  101 http://mirror.atlantic.net/ubuntu/
  115 http://ubuntuarchive.mirror.nac.net/
  124 http://ubuntu.mirror.constant.com/
  127 http://mirror.umd.edu/ubuntu/
  135 http://mirrors.tripadvisor.com/ubuntu/


```

Unfortunately this was as far as I got because I did not understand what to *_**DO**_* with this information.

---

### Post by howefield on 2016-12-16
Load up Software & Updates and go select *Other* from the download field.. then *Select Best Mirror* from the next window, and you'll automatically get the fastest mirror.

---

### Post by heroquestelf on 2016-12-16
> **heroquestelf said:**
> I did a little playing around. First I used the Software and Updates tool to automatically choose my best mirror. It told me to use mirror.symnds.com/ubuntu. So I did, and ran a 
```
sudo apt-get update
```

It was not significantly faster. 

Did that. It didn't help.

---

### Post by heroquestelf on 2017-01-04
I am still having the same problem. My computer WILL connect, and it WILL upgrade, but it takes almost three minutes to do so. 

It also bears mentioning that I *WAS* running standard Ubuntu 14.04 LTS (Trusty) when I started noticing these problems, and these problems were the REASON I upgraded to the  16.04 LTS. 

When I first enter the sudo apt-get update command, it gives me the following feedback:

```

jonathan@jonathan-Satellite-P305:~$ sudo apt-get update
[sudo] password for jonathan: 
Hit:1 http://mirror.symnds.com/ubuntu xenial InRelease                         
Hit:2 http://ppa.launchpad.net/appgrid/stable/ubuntu xenial InRelease          
Get:3 http://mirror.symnds.com/ubuntu xenial-updates InRelease [102 kB]        
Get:4 http://mirror.symnds.com/ubuntu xenial-backports InRelease [102 kB]      
Hit:5 http://ppa.launchpad.net/atareao/atareao/ubuntu xenial InRelease         
Ign:6 http://download.ebz.epson.net/dsc/op/stable/debian lsb3.2 InRelease      
Get:7 http://mirror.symnds.com/ubuntu xenial-security InRelease [102 kB]       
Hit:8 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu xenial InRelease  
Hit:9 http://download.ebz.epson.net/dsc/op/stable/debian lsb3.2 Release        
Hit:10 http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu xenial InRelease
Hit:11 http://ppa.launchpad.net/stefansundin/truecrypt/ubuntu xenial InRelease 
Hit:12 http://ppa.launchpad.net/ubuntu-mate-dev/welcome/ubuntu xenial InRelease
Hit:13 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease       
0% [Connecting to archive.canonical.com (2001:67c:1360:8c01::16)] [Connecting t

```

It then sits there for almost two minutes before it connects to archive.canonical.com

Any suggestions for speeding this up?
----------------------------------------(edit)
WHOLLY SCHMOKES!! I FIXED IT!!

I'm going to mark this as solved, but I wanted to leave this posted just in case anybody else had the same problem. 

I solved my issue by running the following command series:

```

sudo apt-get clean
sudo mv /var/lib/apt/lists /tmp
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get clean 
sudo apt-get update

```

Now it updates at the correct speed.

---

### Post by heroquestelf on 2017-01-05
Well, it was nice while it lasted. Now my problem is back again, and now it's worse. I shut my laptop down last night, and after I rebooted it today I ran an update cycle again, and it went back to the same exact problem as before. As soon as it tried to connect to archive.canonical.com it locked up again, and again it sat there for **FOUR** minutes before the update cycle started back up again, only this time I got the following errors.

```

Fetched 3,651 B in 4min 0s (15 B/s)                              
Reading package lists... Done
W: http://download.ebz.epson.net/dsc/op/stable/debian/dists/lsb3.2/Release.gpg: Signature by key E5220FB7014D0FBDA50DFC2BE5E86C008AA65D56 uses weak digest algorithm (SHA1)
W: GPG error: https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 56A3DEF863961D39
W: The repository 'https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
jonathan@jonathan-Satellite-P305:~$

```

Can anyone bail me out please?

---

### Post by howefield on 2017-01-06
To get rid of the above key error you could try..

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 56A3DEF863961D39
```

---

### Post by heroquestelf on 2017-01-06
**Good news:** I figured out what was causing my five minute delay. It was apparently an IPV6 error. I opened up the /etc/gai.conf file and removed the "#" from line 54 so that it read "precedence ::ffff:0:0/96  100". I then rebooted my computer and now it updates in less than 10 seconds.

**BAD NEWS:** I'm still getting the key error, only now it's changed. When I entered in the command you gave me and ran an update cycle, this was the response:

```

Fetched 2,001 kB in 4min 5s (8,136 B/s)                          
Reading package lists... Done
W: http://download.ebz.epson.net/dsc/op/stable/debian/dists/lsb3.2/Release.gpg: Signature by key E5220FB7014D0FBDA50DFC2BE5E86C008AA65D56 uses weak digest algorithm (SHA1)
W: https://download.01.org/gfx/ubuntu/16.04/main/dists/xenial/InRelease: Signature by key 09D6EF97BFB38E916EF060E756A3DEF863961D39 uses weak digest algorithm (SHA1)
jonathan@jonathan-Satellite-P305:~$

```

---

### Post by howefield on 2017-01-06
It's not quite bad news, it just means that those repositories are signed with SHA-1 which was deprecated in Ubuntu some time last year. So whilst it's not great to see a warning like that, I wouldn't worry too much about it. 

I'd question whether or not you are getting any benefit from the repositories in any case, and perhaps they could be disabled ?

---

### Post by heroquestelf on 2017-01-06
It appears that the repositories are coming from "epson.net". Considering that I the only Epson product in my house is my wireless network printer, I'm assuming that I got that repository when I added my printer, and that the repository is somehow connected to my printer.

If this is true, and the printer has been correctly installed, could I just disable the repository?

---

### Post by howefield on 2017-01-06
> **heroquestelf said:**
> It appears that the repositories are coming from "epson.net". Considering that I the only Epson product in my house is my wireless network printer, I'm assuming that I got that repository when I added my printer, and that the repository is somehow connected to my printer.

If this is true, and the printer has been correctly installed, could I just disable the repository?

I would say yes, however it does mean that you may miss out on any updates to the printer driver that might be pushed to the repository. I'd suggest that printer drivers are seldom updated, I tend to download the deb packages and install them whilst periodically checking for a newer driver.

Shrug, your choice :)

As I said the SHA1 warning is just that, a warning :)

---

