---
title: "apt-get update &quot;connection refused&quot;"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by tr333 on 2007-07-24
I am getting connection errors while trying to update the package lists with "sudo apt-get update".  I am using Ubuntu Server 7.04, and haven't changed any apt settings or sources.list files.

```
Err http://au.archive.ubuntu.com feisty Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty/main Translation-en_AU
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty/restricted Translation-en_AU
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty/universe Translation-en_AU
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty/multiverse Translation-en_AU
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty-updates/main Translation-en_AU
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty-updates/restricted Translation-en_AU
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_AU
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_AU
Ign http://security.ubuntu.com feisty-security/universe Translation-en_AU
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_AU
Hit http://security.ubuntu.com feisty-security Release
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Fetched 1B in 1s (1B/s)  
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Can anyone identify the error that is causing this?

---

### Post by Pumalite on 2007-07-24
Packages are available. Check your ports. Your firewall if you have one. Your Router if you have one. Check with your provider.

---

### Post by Seisen on 2007-07-24
Those appear to be down at the moment, I tried putting one of the links in firefox and it came back as problem loading page. I would try it again tomorrow and if it still doesn't work I would consider using a different mirror.

---

### Post by Pumalite on 2007-07-24
pumalite@pumalite-desktop:~$ sudo apt-get update
Password:
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Get:2 [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty Release.gpg [191B]                   
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Get:4 [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports Release.gpg [189B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Get:6 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US       
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Ign [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports/main Translation-en_US             
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Hit [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports Release                            
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages                
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/restricted Translation-en_US           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages     
Ign [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports/main Packages            
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources             
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/universe Translation-en_US       
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/multiverse Translation-en_US     
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty Release                          
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/main Packages                    
Hit [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports/main Sources
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/restricted Packages
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/main Sources
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/restricted Sources
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/universe Packages
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/universe Sources
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://morgoth.free.fr](http://morgoth.free.fr) feisty-backports/main Packages
Fetched 7B in 3s (2B/s)  
Reading package lists... Done
pumalite@pumalite-desktop:~$

---

### Post by Ubuntiac on 2007-07-24
Seems to just be an Australian mirror thing. I updated yesterday fine, but now I have the same error, also using the en_AU one. I notice that the person who posted no problems was using a different mirror.

---

### Post by tr333 on 2007-07-24
au.archive.ubuntu.com seems to redirect to mirror.optus.net.  I can ping mirror.optus.net but not access via http.  The problem seems to be a dead mirror.  Hopefully they will have it back up soon.

---

### Post by spur on 2007-07-25
Regarding this. How would I change the mirror used?

---

### Post by spur on 2007-07-25
Ok I saw. How silly of me I just changed to 'main server' and it did what it should. I'll try the au mirror again tommorrow.

---

### Post by Fungyo on 2007-07-25
appears to still be unavailable.

---

### Post by jaywalker13 on 2007-07-25
Another Australian having the same problem
Jay

---

### Post by Seisen on 2007-07-25
Try the main servers or a different mirror.

---

### Post by tr333 on 2007-07-25
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/788957.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/788957.html)

Looks like the ext3 filesystem got corrupted on mirror.optus.net :(
Might take a while before it's useable again.

Does anyone know of another Australian mirror that can be used for the moment?

---

### Post by mikeyandmary on 2007-07-26
Had the same problem today. I changed to the main server and all is good again. Just a little slower. 

Someone asked before how to do this. 

System > Administration > Synaptic Package Manager > Settings > Repositories

In the centre of this box it says "Download From" choose Main server.

Hope the aussie one is back up soon.

---

### Post by MichaelSM on 2007-07-26
Thanks M&M. I've got the same problem with the server, but I'm using Dapper and your fix isn't available. Any ideas?
Thank you,
Michael.

---

### Post by OzPhoenix on 2007-07-26
I was just having the same problem, so seeing I'm with Internode I simply went through the /etc/apt/sources.list file and replaced all the:
[http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/)
with
[http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/)

I should have done this earlier (as that way it is quota free), but forgot. So if there are any 'node users out there, maybe that will help you.

---

### Post by Seisen on 2007-07-26
> **MichaelSM said:**
> Thanks M&M. I've got the same problem with the server, but I'm using Dapper and your fix isn't available. Any ideas?
Thank you,
Michael.

What you can do is take  the** au** out of all the repos you have that have it in them so they look like this 

```
http://archive.ubuntu.com/ubuntu/
```
instead of this
```
http://au.archive.ubuntu.com/ubuntu/
```
then do a ```
sudo apt-get update
```

---

### Post by tr333 on 2007-07-26
It looks like this filesystem problem on Optus has also affected the Optus sourceforge.net mirror :(

---

### Post by tr333 on 2007-07-26
> **Seisen said:**
> What you can do is take  the** au** out of all the repos you have that have it in them so they look like this 

```
http://.archive.ubuntu.com/ubuntu/
```
instead of this
```
http://au.archive.ubuntu.com/ubuntu/
```
then do a ```
sudo apt-get update
```

You left in the "." at the start of the url.
```
http://.archive.ubuntu.com/ubuntu/
```
```
http://archive.ubuntu.com/ubuntu/
```

since /etc/apt/sources.list is just a symlink to /etc/apt/sources.list.default you can copy the default list to another file, edit the new file, and change the symlink.

```

$ cd /etc/apt/
$ sudo cp sources.list.default sources.list.modified
$ sudoedit sources.list.modified      # change the URLs in this file
$ sudo rm sources.list
$ sudo ln -s sources.list.modified sources.list

```

After doing this, run the normal apt-get update and apt-get upgrade.

---

### Post by EMoShunz on 2007-07-26
I read this, and went hunting.  I am using Kubuntu, and had a hard time connecting...
Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10), connection timed out
so I went in manage repos and there was an option to use the main server instead of the Canadian server, and voila!

---

### Post by Seisen on 2007-07-26
> **EMoShunz said:**
> I read this, and went hunting.  I am using Kubuntu, and had a hard time connecting...
Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10), connection timed out
so I went in manage repos and there was an option to use the main server instead of the Canadian server, and voila!

People are also having problems with those to for some reason.

---

### Post by Tecguy2 on 2007-07-26
Still down im aussie

---

### Post by Jest3r on 2007-07-26
Yep, I am just using the main server,,,
 Im not getting the 150kb/s(ADSL 1.5),, but 115kb/s, will do for now.

---

### Post by MichaelSM on 2007-07-26
Hello Seisen..

I altered the repos as you suggested and at first it was a disaster. However, I noticed that  the updates for securities have  no 'au' in the first place, and no '.' before 'archive'. If you look at your examples, you've removed the au and left the full stop. The full stop before 'archive' has to be deleted along with the with the 'au.' That's all.

Everything fine now.
Thanks for the help.
Mike.

---

### Post by Apocrypha on 2007-07-27
Canadian with the same problem (except CA instead of AU).

---

### Post by MichaelSM on 2007-07-27
Hi Apocrypha.  Did the full-stop removal fix? Looks like there's some mirror server issues around. Are you with Optus?
Cheers,
Mike.

---

### Post by deanjm1963 on 2007-07-27
It's sort of off-topic but not, the Australian repos are just a joke, some days they work, some days they don't. The last 2 days I've wanted to install ubuntu on 3 different machines, with the aussie repos down I had to go with debian etch. I might have the knowledge to edit sources.lists, play around etc, but the people who had new linux installs do not, they wanted something they could "just turn on, update if needed and not worry about it". I'd like to offer Ubuntu to my clients as an "alternative to the OTHER OS", but I can't. Until the repos are stable a lot of people are not willing to use it.

If they got their act together I'd be installing feisty instead of etch....

---

### Post by brettg on 2007-07-27
It's true, the aussie mirrors are a joke. I hope ubuntu gets thier hosting from optus for free, because optus have to be the most incompetant ISP in the country. They are simply incapable of making anything work properly. 

My advice is to just stick with the main mirror.

---

### Post by MichaelSM on 2007-07-27
Hi deanjm1963. I share your frustrations. I'm slowly assembling boxes and monitors which are basically free to me, so as I can donate running units to elderlies etc. up here in the boonies. Windows is completely out of the question as we all know becos of the cost factor, let alone virus crap.
It's fairly simple to organise security updates wih Feisty and make them automatic. It's just another silly episode to have to fiddle with each box (thank Goodness I haven't put any out there yet) at home and keep them updated before they go out. Some boxes are Dapper for those only with dial-up, and others  are Feisty. 
I've switched them all over to the non AU (main) server so that shouldn't be a difficulty any more. I checked last night using a box with Dapper and all is well. 
The problem would appear to be with the Optus mirror, though I might mention that last night, trying to download a Debian package, only ONE Aussie mirror was up. One out of about SEVEN, if I recall...
Maybe Ubuntu is behind in paying their bills!
Cheers,
Mike.

---

### Post by Seisen on 2007-07-27
> **MichaelSM said:**
> Hello Seisen..

I altered the repos as you suggested and at first it was a disaster. However, I noticed that  the updates for securities have  no 'au' in the first place, and no '.' before 'archive'. If you look at your examples, you've removed the au and left the full stop. The full stop before 'archive' has to be deleted along with the with the 'au.' That's all.

Everything fine now.
Thanks for the help.
Mike.

I fixed it I don't know why I left it in their. :lolflag:

---

### Post by tr333 on 2007-07-27
It looks like the Australian mirror is back up again, but not on optus this time :D

---

