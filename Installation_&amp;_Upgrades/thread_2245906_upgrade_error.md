---
title: "upgrade error"
date: 2014-09-27
forum: Installation &amp; Upgrades
---

### Post by cicada2 on 2014-09-27
I was running 12.04 and recently rebooted to find I had no wireless connection. I was researching that problem when I accessed the update manager and it offered 14.04... so I took it. It seems this was a big mistake. The installing update froze. Now I can only get a partial update no matter what I do. I checked and I am now running 14.04. But I am sure it's not complete (unstable my guess). 

When I run the update manager, I am now getting this error message
> Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.


Any suggestions are greatly appreciated.

---

### Post by ibjsb4 on 2014-09-27
And you ran "sudo apt-get install -f" in terminal?  What were the results?

---

### Post by Bucky Ball on 2014-09-27
If you have no internet connection you can't upgrade.

Totally confused by your post: You say wireless stopped working so you did an OS upgrade to 14.04. How? Did you plug an ethernet cable in?

> It is impossible to install or remove any software. 

Makes a lot of sense if you have no internet connection ... :-k

---

### Post by cicada2 on 2014-09-27
Sorry for the confusion. I moved to a wired connection so that I could troubleshoot. 2 other computers are connected to the wireless rouer, so I know that the problem is with this laptop. 

ibjsb4 - here is the output
> cicada@cicada-Presario-R3000-DS514U-ABL:~$ sudo apt-get install -f[sudo] password for cicada: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
cicada@cicada-Presario-R3000-DS514U-ABL:~$ 

---

### Post by ibjsb4 on 2014-09-27
> is another process using it?

If you have a package manager open, you must first close it and then re-run the command.

---

### Post by cicada2 on 2014-09-27
I just re-booted and tried again. Here are the results.

> cicada@cicada-Presario-R3000-DS514U-ABL:~$ sudo apt-get install -f[sudo] password for cicada: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

So I ran this and now get a new error...
> xscreensaver and xlockmore must be restarted before upgrading             &#9474;   &#9474;                                                                           &#9474;  
 &#9474; One or more running instances of xscreensaver or xlockmore have been      &#9474;  
 &#9474; detected on this system. Because of incompatible library changes, the     &#9474;  
 &#9474; upgrade of the GNU libc library will leave you unable to authenticate to  &#9474;  
 &#9474; these programs. You should arrange for these programs to be restarted or  &#9474;  
 &#9474; stopped before continuing this upgrade, to avoid locking your users out   &#9474;  
 &#9474; of their current sessions.

---

### Post by ibjsb4 on 2014-09-27
Thats a confusing message, so we will just play it safe and remove both of them for the moment.  They can be reinstalled after your up and running.  In terminal:
```
sudo apt-get remove xscreensaver xlockmore
```
Then reboot and do:
```
sudo dpkg --configure -a && sudo apt-get install -f
```
And we'll see what happens next :)

---

### Post by cicada2 on 2014-09-27
Here is the output

> cicada@cicada-Presario-R3000-DS514U-ABL:~$ sudo dpkg --configure -a && sudo apt-get install -f[sudo] password for cicada: 
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.19-0ubuntu6.3); however:
  Package libc6 is not installed.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libudev1:
 libudev1 depends on libc6 (>= 2.17); however:
  Package libc6 is not installed.
dpkg: error processing libudev1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc-dev-bin:
 libc-dev-bin depends on libc6 (>> 2.19); however:
  Package libc6 is not installed.
 libc-dev-bin depends on libc6 (<< 2.20); however:
  Package libc6 is not installed.
dpkg: error processing libc-dev-bin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev
 libudev1
 libc-dev-bin

---

### Post by ibjsb4 on 2014-09-27
```
sudo apt-get install libc6
```

---

### Post by cicada2 on 2014-09-27
Sigh... the old message came up again
> [COLOR=#000000]*xscreensaver and xlockmore must be restarted before upgrading &#9474; &#9474; &#9474; *[/COLOR]
[COLOR=#000000]*&#9474; One or more running instances of xscreensaver or xlockmore have been &#9474; *[/COLOR]
[COLOR=#000000]*&#9474; detected on this system. Because of incompatible library changes, the &#9474; *[/COLOR]
[COLOR=#000000]*&#9474; upgrade of the GNU libc library will leave you unable to authenticate to &#9474; *[/COLOR]
[COLOR=#000000]*&#9474; these programs. You should arrange for these programs to be restarted or &#9474; *[/COLOR]
[COLOR=#000000]*&#9474; stopped before continuing this upgrade, to avoid locking your users out &#9474; *[/COLOR]
[COLOR=#000000]*&#9474; of their current sessions.*[/COLOR]

So I ran 
> [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get remove xscreensaver xlockmore[/FONT][/COLOR]

Here is the message...
> cicada@cicada-Presario-R3000-DS514U-ABL:~$ sudo apt-get remove xscreensaver xlockmore[sudo] password for cicada: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


I will reboot to see if I can remove xscreensaver xlockmore. Stand by 1 min

---

### Post by ibjsb4 on 2014-09-27
Ok, give it a try.  Standing by.

---

### Post by cicada2 on 2014-09-27
I'm stuck in a bit of a "loop". Here's the message (from before). 
> cicada@cicada-Presario-R3000-DS514U-ABL:~$ sudo apt-get remove xscreensaver xlockmore[sudo] password for cicada: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by ibjsb4 on 2014-09-27
Lets take a look at your sources list.  Please post:
```
cat /etc/apt/sources.list
```
and
```
ls /etc/apt/sources.list.d/*.list
```
Also code tags work better then quote tags.
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

---

### Post by cicada2 on 2014-09-27
While I am thinking about it, thanks for your help!

Here we go
> cicada@cicada-Presario-R3000-DS514U-ABL:~$ cat /etc/apt/sources.list# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423)]/ precise main multiverse restricted universe


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

and this one!
> cicada@cicada-Presario-R3000-DS514U-ABL:~$ ls /etc/apt/sources.list.d/*.list
ls: cannot access /etc/apt/sources.list.d/*.list: No such file or directory

---

### Post by ibjsb4 on 2014-09-27
Ok, those are good.  I have made a request to a friend for some help on this.  Lets stand by and let him chime in.

---

### Post by Bashing-om on 2014-09-27
cicada2 -> ibjsb4 ; Hello !

Boy, this too is a 1st.
Is xscreensaver and xlockmore still a problem ? I do agree that this must be dealt with before we can pursue completing the upgrade.
what returns from terminal command:
```

sudo lsof /var/lib/dpkg/lock
sudo lsof /var/lib/apt/lists/lock

``` maybe once known 'fuser' will deal with it for us.

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2014-09-27
Thanks Bashing :)

---

### Post by Bashing-om on 2014-09-27
> **ibjsb4 said:**
> Thanks Bashing :)

Yeah, well, this may be another case of us floundering our way through, But, I bet we come out in the end.

[INDENT]this is another fine mess you got me into
LOL[/INDENT]

---

### Post by ibjsb4 on 2014-09-27
> this is another fine mess you got me into
Your just too good at it :)

---

### Post by cicada2 on 2014-09-27
Here is...
> lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/cicada/.gvfs      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF   NODE NAME
dpkg    1769 root    3uW  REG    8,5        0 141493 /var/lib/dpkg/lock

and then:
> cicada@cicada-Presario-R3000-DS514U-ABL:~$ sudo lsof /var/lib/apt/lists/locklsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/cicada/.gvfs
      Output information may be incomplete.

---

### Post by Bashing-om on 2014-09-27
cicada2; Pardon me

For the delay, but but .. I do not know what to make of the second output - lsof /var/lib/apt/lists/lock -;
Considering what could cause such an advisory.

Let's give it a poke and see if it bites:
```

sudo fuser -cuk /var/lib/dpkg/lock
sudo rm -f /var/lib/dpkg/lock
sudo fuser -cuk /var/cache/apt/archives/lock
sudo rm -f /var/cache/apt/archives/lock
sudo apt-get update

```
What are the outputs?

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT][INDENT]other times I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cicada2 on 2014-09-27
Not the best result. I ran the first command and the screen went completely black. It didn't come back so I re-booted. I haven't tried #2-#5 in your list.

Edit: just a reminder from my first post... the installation of 14.04 froze and was never completed. Just sayin'

---

### Post by Bashing-om on 2014-09-27
cicada2; Well ---

Not tooo bad, but
let's see if:
```

sudo fuser -vvv /var/lib/dpkg/lock
sudo rm /var/lib/apt/lists/lock

```
tells us anything.
And yeah, we get over this hump, we see what can be done to complete the release upgrade.

It has gotten late here, my time, and my think'n has become forced and not too reliable. Will continue to consider and see what conclusions I (we) have in the AM.

[INDENT][INDENT]ain't nothing but a thing
[INDENT][INDENT][INDENT]maybe this time a BIG thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cicada2 on 2014-09-28
Thanks Bashing-om. I ran those commands and got not much. Check it out.
> cicada@cicada-Presario-R3000-DS514U-ABL:~$ sudo fuser -vvv /var/lib/dpkg/lock[sudo] password for cicada: 
cicada@cicada-Presario-R3000-DS514U-ABL:~$ sudo rm /var/lib/apt/lists/lock
cicada@cicada-Presario-R3000-DS514U-ABL:~$

I'll check back in the am. Bye for now.

---

### Post by Bashing-om on 2014-09-28
cicada2; Good morning !

OK, that looks good that 'dpkg' is now unlocked. Maybe also 'apt' can now work.
Let's see :
```

sudo apt-get update

```
Then if that runs, we get an updated status/condition and make sure we are ready to try and upgrade.

[INDENT][INDENT]moving along smartly ?[/INDENT][/INDENT]

---

### Post by cicada2 on 2014-09-28
Ran it and here is the result.
> cicada@cicada-Presario-R3000-DS514U-ABL:~$ sudo apt-get update[sudo] password for cicada: 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [59.7 kB]             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release.gpg                            
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports Release.gpg [933 B]        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release                                
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates Release [59.7 kB]   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [45.3 kB]        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main TranslationIndex                      
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]     
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [10.8 kB]    
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [700 B]    
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [136 kB]  
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports Release [59.7 kB]         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Sources                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main TranslationIndex                  
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [48.8 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse TranslationIndex            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted TranslationIndex            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe TranslationIndex              
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Sources [121 kB]       
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1,398 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main TranslationIndex [73 B] 
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse TranslationIndex [71 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted TranslationIndex [70 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe TranslationIndex [73 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_CA                     
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Sources [1,408 B]
Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Sources [85.1 kB]  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:22 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Sources [3,527 B]
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main i386 Packages [318 kB]
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted i386 Packages [5,820 B]
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe i386 Packages [206 kB]
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [9,545 B]
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main TranslationIndex [74 B]
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse TranslationIndex [72 B]
Get:29 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted TranslationIndex [72 B]
Get:30 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe TranslationIndex [74 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en_CA                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en
Get:31 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Sources [4,760 B]
Get:32 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Sources [14 B]
Get:33 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Sources [13.7 kB]
Get:34 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Sources [1,315 B]
Get:35 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main i386 Packages [6,379 B]
Get:36 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted i386 Packages [14 B]
Get:37 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe i386 Packages [16.8 kB]
Get:38 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [945 B]
Get:39 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main TranslationIndex [72 B]
Get:40 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse TranslationIndex [71 B]
Get:41 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted TranslationIndex [70 B]
Get:42 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe TranslationIndex [73 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en_CA  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Translation-en 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Translation-en
Get:43 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Translation-en [14.3 kB]
Fetched 1,235 kB in 16s (75.0 kB/s)                                            
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by Bashing-om on 2014-09-28
cicada2; -> ibjsb4; Hey hey ;

Looks good to me, Let's proceed and try and clean the system up, and have the package manager try and fix it's self . Don't you think ?
let's do:
where '#' are my comments, not to be entered into the terminal -
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages. A dist-upgrade will install new dependencies for #packages already installed and may remove packages if they are no longer needed. This will not bring you to a new release of ubuntu. 
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

```

If when all these run clean, we are home free; setting pretty on 14.04 .

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by cicada2 on 2014-09-28
I get the same response for each command. Exception: sudo apt-get update #resync package index << seemed to actually work

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. cicada@cicada-Presario-R3000-DS514U-ABL:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.19-0ubuntu6.3); however:
  Package libc6 is not installed.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libudev1:
 libudev1 depends on libc6 (>= 2.17); however:
  Package libc6 is not installed.
dpkg: error processing libudev1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc-dev-bin:
 libc-dev-bin depends on libc6 (>> 2.19); however:
  Package libc6 is not installed.
 libc-dev-bin depends on libc6 (<< 2.20); however:
  Package libc6 is not installed.
dpkg: error processing libc-dev-bin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev
 libudev1
 libc-dev-bin

---

### Post by Bashing-om on 2014-09-28
cicada2; OK,

No step for a stepper, let's fix it as the package manager advises:
```

sudo apt-get install libc6

```

Depending on this result, is what we do next.

[INDENT]looking brighter,
[INDENT][INDENT][INDENT]are sun glasses handy 
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cicada2 on 2014-09-28
and this again is the result... 
> xscreensaver and xlockmore must be restarted before upgrading             &#9474;   &#9474;                                                                           &#9474;  
 &#9474; One or more running instances of xscreensaver or xlockmore have been      &#9474;  
 &#9474; detected on this system. Because of incompatible library changes, the     &#9474;  
 &#9474; upgrade of the GNU libc library will leave you unable to authenticate to  &#9474;  
 &#9474; these programs. You should arrange for these programs to be restarted or  &#9474;  
 &#9474; stopped before continuing this upgrade, to avoid locking your users out   &#9474;  
 &#9474; of their current sessions.

---

### Post by Bashing-om on 2014-09-28
cicada2; Welp:

We can take a hint:
Let's check:
```

dpkg -l xscreensaver 
dpkg -l xlockmore

```

[INDENT][INDENT]what does it take
[INDENT][INDENT][INDENT]to keep and dependency like you
[INDENT][INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cicada2 on 2014-09-28
thanks thanks

> cicada@cicada-Presario-R3000-DS514U-ABL:~$ dpkg -l xscreensaverDesired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  xscreensaver   5.15-2ubuntu1  Automatic screensaver for X
cicada@cicada-Presario-R3000-DS514U-ABL:~$ dpkg -l xlockmore
No packages found matching xlockmore.


---

### Post by Bashing-om on 2014-09-28
cicada2; Well.


'xscreensaver' is installed .. Is it running ( as the package manager indicates ) ?
```

ps -e | grep xscreensaver

```
IF so, we need to find a means to stop it from terminal ( get the PID, and kill it ).

Then we address also the xlockmore situation/ Do not know what to make of it - yet - or where it is coming from. It does not exist as a package in 14.04's repository.
Let's try this:
```

sudo find / -name xlockmore

```
If such a file exist, will take the system a bit of time to find it, patience.

I am also interested to know if your system sees it as a component of 'xscrensaver':
```

apt-cache depends xscreensaver
apt-cache rdepends xscreensaver

```

[INDENT][INDENT]as around and round we go, but
[INDENT][INDENT][INDENT]find a place to stop
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cicada2 on 2014-09-28
I am headed out for a few hours of "family time" with Mrs cicada. I will resurface later this afternoon (pacific time). Thanks! Here are the results so far.

> cicada@cicada-Presario-R3000-DS514U-ABL:~$ ps -e | grep xscreensaver 1335 ?        00:00:01 xscreensaver
cicada@cicada-Presario-R3000-DS514U-ABL:~$ sudo find / -name xlockmore
[sudo] password for cicada: 
cicada@cicada-Presario-R3000-DS514U-ABL:~$ apt-cache depends xscreensaver
xscreensaver
  Depends: libatk1.0-0
  Depends: libc6
  Depends: libglade2-0
  Depends: libglib2.0-0
  Depends: libgtk2.0-0
  Depends: libpam0g
  Depends: libpango-1.0-0
  Depends: libx11-6
  Depends: libxext6
  Depends: libxi6
  Depends: libxinerama1
  Depends: libxml2
  Depends: libxmu6
  Depends: libxrandr2
  Depends: libxt6
  Depends: libxxf86vm1
  Depends: xscreensaver-data
  Suggests: xfishtank
  Suggests: xdaliclock
  Suggests: xscreensaver-gl
  Suggests: <fortune>
    fortune-mod
  Suggests: <www-browser>
    arora
    dillo
    dwb
    lynx-cur
    netsurf
    netsurf-fb
    netsurf-gtk
    uzbl
    chimera2
    chromium-browser
    elinks
    epiphany-browser
    firefox
    konqueror
    links
    links2
    midori
    netrik
    rekonq
    surf
    w3m
    xemacs21-mule
    xemacs21-mule-canna-wnn
    xemacs21-nomule
 |Suggests: <qcam>
  Suggests: streamer
 |Suggests: <gdm3>
  Suggests: kdm-gdmcompat
  Recommends: libjpeg-progs
    libjpeg-turbo-progs
  Recommends: <perl5>
    perl
 |Recommends: miscfiles
  Recommends: <wordlist>
    wcatalan
    miscfiles
    wamerican
    wamerican-huge
    wamerican-insane
    wamerican-large
    wamerican-small
    wbrazilian
    wbritish
    wbritish-huge
    wbritish-insane
    wbritish-large
    wbritish-small
    wbulgarian
    wcanadian
    wcanadian-huge
    wcanadian-insane
    wcanadian-large
    wcanadian-small
    wdanish
    wdutch
    wfaroese
    wfrench
    wgalician-minimos
    wgerman-medical
    witalian
    wngerman
    wnorwegian
    wogerman
    wpolish
    wportuguese
    wspanish
    wswedish
    wswiss
    wukrainian
  Conflicts: funny-manpages
  Conflicts: gnome-control-center
  Conflicts: <suidmanager>
  Conflicts: <xscreensaver-gnome>
  Conflicts: <xscreensaver-nognome>
cicada@cicada-Presario-R3000-DS514U-ABL:~$ apt-cache rdepends xscreensave
E: No packages found




---

### Post by Bashing-om on 2014-09-28
cicada2; Hey !

Looky what I discovered !
3rd party software !
[http://www.tux.org/~bagleyd/xlockmore.html](http://www.tux.org/~bagleyd/xlockmore.html)

Now let's look and see what is:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
see what we have to work with and get a notion of what we can do !

[INDENT][INDENT]now that I can believe
[/INDENT][/INDENT]

---

### Post by cicada2 on 2014-09-28
hmmm - not sure what to say. Thanks for all your patience, Basjong-om!


>      1	# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423)]/ precise main multiverse restricted universe     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty main restricted
     6	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    11	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty universe
    17	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty universe
    18	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates universe
    19	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty multiverse
    27	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty multiverse
    28	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    29	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    37	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    38	
    39	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    40	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    41	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    42	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    43	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    44	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    51	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    56	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
cicada@cicada-Presario-R3000-DS514U-ABL:~$ tail -v -n +1 /etc/apt/sources.list.d/*
tail: cannot open `/etc/apt/sources.list.d/*' for reading: No such file or directory




---

### Post by Bashing-om on 2014-09-28
cicada2; Hummm ..

> 
hmmm - not sure what to say. ->


Me too ! .. Now I am stuck as there is no source here either for xlockmore.
Lemme have a bit more time to study about this and what to do about it .. 
> 
xscreensaver and xlockmore must be restarted before upgrading &#9474; &#9474; &#9474; 
&#9474; One or more running instances of xscreensaver or xlockmore have been &#9474; 
&#9474; detected on this system. <snip>


The system thinks something is up, and I sure would like to know what !

[INDENT][INDENT]meanwhile;
[INDENT][INDENT][INDENT]back at the ranch[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-09-28
cicada2; Hey !

Now that is quick ! Experience counts ! Looky looky :
> 
You have searched for files named xlockmore in suite precise, all sections, and all architectures. Found 2 results.

File	Packages
/etc/X11/Xresources/xlockmore	xlockmore, xlockmore-gl
/etc/logcheck/ignore.d.workstation/xlockmore	logcheck-database


Now that package DOES exist for precise, but NOT in trusty.
SO, where is it ?
```

ls -al /etc/X11/Xresources/xlockmore
ls -al /etc/logcheck/ ##and then follow this path to it's end##
dpkg -l xlockmore
dpkg -l xlockmore-gl
dpkg -l logcheck-database

```
And to follow through with my thought process; is the /etc directory installed within 'root' ?Once I know where it is we will run 'lsof' once more and see what files are open that pertain to our issue.
```

sudo fdisk -lu

```

By golly, May flounder through this yet !

[INDENT][INDENT][INDENT]pound on it long 'nuff
[INDENT][INDENT][INDENT]something is gonna give
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cicada2 on 2014-09-28
pounding away

> cicada@cicada-Presario-R3000-DS514U-ABL:~$ ls -al /etc/X11/Xresources/xlockmorels: cannot access /etc/X11/Xresources/xlockmore: No such file or directory
cicada@cicada-Presario-R3000-DS514U-ABL:~$ ls -al /etc/logcheck/ ##and then follow this path to it's end##
total 20
drwxr-xr-x   3 root root  4096 Apr 23  2012 .
drwxr-xr-x 119 root root 12288 Sep 27 20:42 ..
drwxr-xr-x   2 root root  4096 Sep  8 15:52 ignore.d.server
cicada@cicada-Presario-R3000-DS514U-ABL:~$ dpkg -l xlockmore
No packages found matching xlockmore.
cicada@cicada-Presario-R3000-DS514U-ABL:~$ dpkg -l xlockmore-gl
No packages found matching xlockmore-gl.
cicada@cicada-Presario-R3000-DS514U-ABL:~$ dpkg -l logcheck-database
No packages found matching logcheck-database.
cicada@cicada-Presario-R3000-DS514U-ABL:~$ sudo fdisk -lu
[sudo] password for cicada: 


Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x994a994a


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    47706054    23852996    7  HPFS/NTFS/exFAT
/dev/sda2        47706110    78139391    15216641    5  Extended
/dev/sda5        47706112    76603391    14448640   83  Linux
/dev/sda6        76605440    78139391      766976   82  Linux swap / Solaris
cicada@cicada-Presario-R3000-DS514U-ABL:~$ 




---

### Post by Bashing-om on 2014-09-28
cicada2; Welp;

again, Which way did he go. George ?
What now returns from:
```

ls -al /etc/logcheck/ignore.d.server

```
will want to 'file' this output IF it is the terminal end of the path.

Now let's see what files are open in /etc; Close out everything that you possibly can, down to just the system running and no applications.
What then returns:
```

lsof /etc

```
IF all is good, there is no output ( see I did test !) - but could be that xlockmore or xscreensaver "was" writing to a file, And that process is still pending.

[INDENT][INDENT]once again - sometimes I do wonder
[INDENT][INDENT][INDENT][INDENT][INDENT]othertimes I do not know[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][/INDENT][/INDENT]

---

### Post by cicada2 on 2014-09-28
Here is the answer (or maybe the question)
> cicada@cicada-Presario-R3000-DS514U-ABL:~$ ls -al /etc/logcheck/ignore.d.servertotal 16
drwxr-xr-x 2 root root 4096 Sep  8 15:52 .
drwxr-xr-x 3 root root 4096 Apr 23  2012 ..
-rw-r--r-- 1 root root  115 Mar  6  2012 ntpdate
-rw-r--r-- 1 root root  653 Mar 30  2012 rsyslog
cicada@cicada-Presario-R3000-DS514U-ABL:~$ lsof /etc

---

### Post by Bashing-om on 2014-09-28
cicada2; UHMMPPHH;

Probably another dead end, but:
```

cat /etc/logcheck/ignore.d.servertotal/ntpdate
cat /etc/logcheck/ignore.d.servertotal/rsyslog

```
Let's look and see IF either have been writing to the files.
And yep nothing writing to /etc now !

Looks like I am going to have to sleep on this, see what comes to me in my dreams.
Consider looking through /var/lib/dpkg/status, see if a search on these file names reveal anything ?
Consider:
```

ls -al /var/lib/dpkg/info/xlockmore.list
ls -al /var/lib/dpkg/info/xlockmore-gl.list
ls -al /var/lib/dpkg/info/logcheck-database.list

```
Has to be something somewhere that has the package manager's attention.

[INDENT][INDENT]now this is
[INDENT][INDENT][INDENT]getting my goat
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-09-28
Could be jumping in where unwanted, and Bashing-om may know better, but did you actually run this command?

```
sudo dpkg --configure -a
```

I may have missed something and it may make no difference (the command above, not that I've missed something!). Synaptics may give some clues, but using a straight Ubuntu, that wouldn't be installed by default ... Broken packages? I'll read through again and see if there's something else I've missed ...

---

### Post by ian-weisser on 2014-09-28
Try 'dpkg -S /path/to/any/xlockname/file' to find the package name.  -S for 'search'; very handy to find packages from a file path.
Since it is merely informational, it does not require sudo.

---

### Post by cicada2 on 2014-09-29
Ok, in order. This for Basing-om

> cicada@cicada-Presario-R3000-DS514U-ABL:~$ cat /etc/logcheck/ignore.d.servertotal/ntpdatecat: /etc/logcheck/ignore.d.servertotal/ntpdate: No such file or directory
cicada@cicada-Presario-R3000-DS514U-ABL:~$ cat /etc/logcheck/ignore.d.servertotal/rsyslog
cat: /etc/logcheck/ignore.d.servertotal/rsyslog: No such file or directory
cicada@cicada-Presario-R3000-DS514U-ABL:~$ ls -al /var/lib/dpkg/info/xlockmore.list
ls: cannot access /var/lib/dpkg/info/xlockmore.list: No such file or directory
cicada@cicada-Presario-R3000-DS514U-ABL:~$ ls -al /var/lib/dpkg/info/xlockmore-gl.list
ls: cannot access /var/lib/dpkg/info/xlockmore-gl.list: No such file or directory
cicada@cicada-Presario-R3000-DS514U-ABL:~$ ls -al /var/lib/dpkg/info/logcheck-database.list
ls: cannot access /var/lib/dpkg/info/logcheck-database.list: No such file or directory

Bucky Ball - I tried that a get the same result each time (thanks for hanging in there)

> dpkg: error: dpkg status database is locked by another process

... and thanks to ian-weisser, too! Here it is:

> cicada@cicada-Presario-R3000-DS514U-ABL:~$ dpkg -S /path/to/any/xlockname/file
dpkg-query: no path found matching pattern /path/to/any/xlockname/file.

---

### Post by Bucky Ball on 2014-09-29
'Database is locked by another process' is possibly the clue. What the heck is going on there? A stumper. Ideas?

---

### Post by Bashing-om on 2014-09-29
@ Bucky ... This one my friend has got me stumped as to what is going on.

@Ian, Sure glad again you are looking over our shoulder, can use all the help here we can get, But, situations such as this is where I learn the most !

OK, We cleared that lock once before - unknown at this time what prompted the lock once more - let's make sure it is not a normal condition of "dpkg' not finishing a process prior to starting another;
What results now when running:
```

sudo dpkg --configure -a

```
If it still errors out with the lock condition, Yeah .. a great hint that we need to go looking and find out the where/why !

[INDENT][INDENT]all in a process, somewhere
[/INDENT][/INDENT]

---

### Post by cicada2 on 2014-09-29
Seems to be

> dpkg: error: dpkg status database is locked by another process



---

### Post by ian-weisser on 2014-09-29
> dpkg: error: dpkg status database is locked by another process

Means the system thinks another package manager is open. Synaptic, Software Center, another apt-get window. 
Usually, the system is right. Wait for the other application to complete any actions, then close it.

If you are _really_ sure the system is mistaken, then reboot.
If, after a reboot, you still get the same message, then clear the lockfile.
The same way you did using the second command of Post #22 of this thread.

---

### Post by cicada2 on 2014-09-29
I have not initiated anything and constantly reboot, so I am sure the system is mistaken. I did what you suggested: fresh reboot. I had the same exact results that happened in Post #22. I entered the first command and the screen blacked out. 

> [COLOR=#000000][FONT=Ubuntu Mono]sudo fuser -cuk /var/lib/dpkg/lock[/FONT][/COLOR] 

I did a forced shutdown and the computer rebooted with no issues. Sigh

---

### Post by cicada2 on 2014-09-29
I just rebooted and tried command from Post #47. This is the result.
> cicada@cicada-Presario-R3000-DS514U-ABL:~$ sudo dpkg --configure -a[sudo] password for cicada: 
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.19-0ubuntu6.3); however:
  Package libc6 is not installed.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libudev1:
 libudev1 depends on libc6 (>= 2.17); however:
  Package libc6 is not installed.
dpkg: error processing libudev1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc-dev-bin:
 libc-dev-bin depends on libc6 (>> 2.19); however:
  Package libc6 is not installed.
 libc-dev-bin depends on libc6 (<< 2.20); however:
  Package libc6 is not installed.
dpkg: error processing libc-dev-bin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev
 libudev1
 libc-dev-bin




---

### Post by Bashing-om on 2014-09-29
cicada2; sigh, me too !

Let's give the system a gentle poke and see what happens:
```

sudo apt-get update
sudo apt-get upgrade

```
IF that goes well. let's prod on it now:
```

sudo dpkg -C
sudo apt-get -f install

```
Still fat smart and happy ?
```

sudo dpkg --configure -a

```

[INDENT][INDENT]an inquiring mind
[INDENT][INDENT][INDENT]still wants to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cicada2 on 2014-09-29
The update seemed to work fine. The upgrade was chugging along fine and then...
>  Configuring libc6 &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;   &#9474;                                                                           &#9474;  
 &#9474; xscreensaver and xlockmore must be restarted before upgrading             &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; One or more running instances of xscreensaver or xlockmore have been      &#9474;  
 &#9474; detected on this system. Because of incompatible library changes, the     &#9474;  
 &#9474; upgrade of the GNU libc library will leave you unable to authenticate to  &#9474;  
 &#9474; these programs. You should arrange for these programs to be restarted or  &#9474;  
 &#9474; stopped before continuing this upgrade, to avoid locking your users out   &#9474;  
 &#9474; of their current sessions.   

---

### Post by Bashing-om on 2014-09-29
cicada2; Why am I not surprised ?

```

sudo lsof /var/lib/dpkg/lock

```

and ahunt'n we will go

---

### Post by cicada2 on 2014-09-29
Now posting from my windoze 7 laptop. Prior to your last post, I rebooted and the computer never came back. I got a black screen. After a few min.s I got some message like...
> General error mounting filesystems.
maintenance shell will now be started.
Control-d will terminate this shell and re-try.

---

### Post by cicada2 on 2014-09-29
If I understand correctly, I should never have accepted the offer to upgrade to 14.04. Each new version must be upgraded in sequence - right? This was my error. 

The fix is probably to start fresh. I could look up the instructions to uninstall Ubuntu. Make a fresh installation DVD. Start fresh. Let me know if you disagree.

---

### Post by Bashing-om on 2014-09-29
cicada2; Hey;

Regretful it has taken this long to get back to you. I have been a busy little boy.
> 
If I understand correctly, I should never have accepted the offer to upgrade to 14.04.

No, not at all, The thing is in order to on-line upgrade one must be as close to default as possible, and the screensaver turned off. I "think" this is the downfall here that you had your screensaver active. Now why this is a problem I do not understand fully. In my experience IF the screensaver is enabled the upgrade will not proceed, and there is an advisory to the effect to turn the screen saver off. On-line upgrading from 12.04 to 14.04 is perfectly acceptable when the requisits are met - mainly that the update manager is set to "LTS", no proprietary driver is installed, 3rd party software sources disabled ( the installer will try and disable them, but also try and enable them again in the upgrade process - the problem comes in when that 3rd party software has no support in 14.04.

At this time, when your aggravation factor is exceeded you may do a clean install of 14.04. Generally with good backups it is but a matter of minutes and up and running. Stick in the liveDVD -> "erase disk and install ubuntu" Done !
20 minutes to install and a few more to copy backup files back in place. It is your call IF/When you want to do the clean install. I DO prefer to fix the problem, but honestly I am running out of ideas as to how to find this bottleneck. It is but such a small thing once the source is identified and libc6 properly installed. Will then be but a matter of minutes to have the system all cleaned up and spiffy.
------------------
Presently -2+ hours later, still having the file system mounting issue ? 
Will require a liveDVD of 14.04 to run the file system repair utility.- Humm, that might even fix our dpkg issue !! ?
Else; Then it is back on course to track down the xscreensaver/xlockmore bottleneck.

[INDENT][INDENT]you the man
[INDENT][INDENT][INDENT]your call
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cicada2 on 2014-09-29
Bashing-om 
and my other helpers...
Thanks for your patience and kind help. It is really wonderful to meet so many nice people who care enough to hang in there. Especially when no money is involved (you guys weren't planning to send me a bill - I hope). Joking aside - thanks a million!!

---

### Post by Bashing-om on 2014-09-29
cicada2; Shucks !

We do this because we want to; our way of giving back to what has been given by others .. now 50 some odd years, and Millions of programmers and other contributers' efforts. Hang in here and one day it will be you on the end of this stick.

OK, what are we going to do, keep pounding away, or throw in the towel and take the easy way out -> The nuclear solution -> (RE-)install ?
( or the best of both worlds -> set up your system to dual boot 14.04 'buntus !!)
[If you want to learn the OS, break one, still have another to work with - I learned this the hard way in them early days - broke mine numerous times]
hey !
[INDENT]it is 'buntu
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-09-29
Bashing doesn't know how to quit, cicada2. Not in their vocabulary, lucky for the rest of us! A true rock and legend, not a rock legend (but might be in their other life!). ;)

I would say pity to blow things up and reinstall, generally considered a last resort round here, but things are messy and I, for one, can see few clues ... 

As BOm has mentioned, possibly, and probably, caused by having something third-party, and possibly even a third-party repo, still up and running whilst the install was going ... or the screensaver. Never knew about that. Learn something everyday.

---

### Post by vasa1 on 2014-09-29
> **cicada2 said:**
> If I understand correctly, I should never have accepted the offer to upgrade to 14.04. Each new version must be upgraded in sequence - right? This was my error. ....
Theoretically, you should be able to upgrade from one LTS to the next. As Bashing-om's post indicates, certain precautions should be taken. If you start with a non-LTS version, you would need to proceed sequentially, upgrading from one non-LTS to the next, to the next, ... 

Facts on risks associated with a upgrade versus a clean install aren't abundant. Canonical feels upgrades rather than a clean install are the way forward. They've felt this way for quite some time.

My take is that whatever the risk of each individual upgrade is, it is bigger going from one LTS to the next because of the two-year gap whereas sequential upgrades deal with just six months.

As for whether to just start with a new installation, the choice is yours. People are ready to try to help you salvage your current install. Personally, I'd go with a new installation.

---

### Post by vasa1 on 2014-09-29
> **cicada2 said:**
> Bashing-om 
and my other helpers...
Thanks for your patience and kind help. It is really wonderful to meet so many nice people who care enough to hang in there. Especially when no money is involved (you guys weren't planning to send me a bill - I hope). Joking aside - thanks a million!!

Hey, even though I haven't helped in any way, I think you deserve some (a lot!) credit as well. You've been totally polite through difficult times :) That's says a lot about you. No wonder people are encouraged to help you as long as you need.

---

### Post by Bucky Ball on 2014-09-29
I never upgrade, personally. I always use the LTS as my main squeeze (and fool about with the interim releases on a spare partition) and do a clean install when the time comes. I've found upgrades to be problematic, even when I've taken precautions, but I haven't even attempted one in about five years. I gave up on them. Like vasa mentions, LTS to LTS is a big two year gap. A lot can change in techno-time in two years ...

Anyhow, bit off-topic, but thought I'd throw in my two cents ... ;)

---

