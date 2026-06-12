---
title: "APPROX causes '404 Not Found' when 'apt-get update' runs"
date: 2013-03-14
forum: Installation &amp; Upgrades
---

### Post by ecowan on 2013-03-14
For weeks I have been struggling with complaints from synaptic>refresh or 'apt-get update' or Software Updater when I run them with approx. If I run directly, no problem. I attach my /etc/approx/approx.conf and /etc/apt/sources.list.

I have tried 'sudo approx-gc' and 'sudo rm /var/lib/apt/lists/partial/*' innumerable times. My last attempted remedy was to create a completely empty sources.list and in synaptic to check all the proffered options under Settings/Repositories and to pick 'Server for Canada'.  Synaptic did a refresh just fine. 'apt-get update' was happy as well. I also ran 'sudo approx-gc'. But when I plugged approx back in by replacing 'ca.archive.ubuntu.com/ubuntu' with 'localhost:9999/base', I got:
 
> Hit [http://localhost](http://localhost) precise-updates/multiverse Translation-en                                             
Hit [http://localhost](http://localhost) precise-updates/restricted Translation-en                                             
Hit [http://localhost](http://localhost) precise-updates/universe Translation-en_CA                                            
Hit [http://localhost](http://localhost) precise-updates/universe Translation-en                                               
Err [http://localhost](http://localhost) precise/universe Sources                                                              
  404  Not Found
Err [http://localhost](http://localhost) precise/multiverse Sources                                                            
  404  Not Found
Err [http://localhost](http://localhost) precise/main i386 Packages                                                            
  404  Not Found
Err [http://localhost](http://localhost) precise/universe i386 Packages                                                        
  404  Not Found
Err [http://localhost](http://localhost) precise/restricted i386 Packages                                                      
  404  Not Found
Err [http://localhost](http://localhost) precise/multiverse i386 Packages                                                      
  404  Not Found
Ign [http://localhost](http://localhost) precise/multiverse Translation-en_CA                                                  
Ign [http://localhost](http://localhost) precise/restricted Translation-en_CA                                                  
Fetched 261 kB in 9s (27.0 kB/s)                                                                           
W: Failed to fetch [http://localhost:9999/base/dists/precise/universe/source/Sources](http://localhost:9999/base/dists/precise/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://localhost:9999/base/dists/precise/multiverse/source/Sources](http://localhost:9999/base/dists/precise/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://localhost:9999/base/dists/precise/main/binary-i386/Packages](http://localhost:9999/base/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://localhost:9999/base/dists/precise/universe/binary-i386/Packages](http://localhost:9999/base/dists/precise/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://localhost:9999/base/dists/precise/restricted/binary-i386/Packages](http://localhost:9999/base/dists/precise/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://localhost:9999/base/dists/precise/multiverse/binary-i386/Packages](http://localhost:9999/base/dists/precise/multiverse/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


I'm sure it's something I did incorrectly, but what?

I have a small network of three laptops and two servers, so approx is really useful.

Thanks. - Erny

/etc/approx/approx.conf:

> #$cache         /var/cache/approx
#$interval      60
#$max_rate      unlimited
#$max_redirects 5
#$user          approx
#$group         approx
#$syslog        daemon
#$pdiffs        true
#$offline       false

# 20130314 ecowan added/changed

$cache		/media/Buster/approx-cache

# base
base		[http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu)

# security
security	[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)


> # 20130314 ecowan adapted to work with approx
#                 original as built by synaptic is in sources.orgnl

deb [http://localhost:9999/base/](http://localhost:9999/base/) precise main universe restricted multiverse
deb-src [http://localhost:9999/base/](http://localhost:9999/base/) precise main universe restricted multiverse 
#Added by software-properties
deb [http://localhost:9999/security/](http://localhost:9999/security/) precise-security universe main multiverse restricted
deb [http://localhost:9999/base/](http://localhost:9999/base/) precise-updates universe main multiverse restricted


---

### Post by ecowan on 2013-03-15
So this was my work-around.
I deleted the contents of my approx-cache (actually, I moved them.), and ran approx-gc. On my server and main laptop  ran apt-get update, software updater, and synaptic reload.
That seems to have cleaned things up.
- Erny

---

### Post by ecowan on 2013-07-04
I have figured out where approx is failing, and devised a less drastic work around.
It happens that, somehow, some of the files in the approx-cache get set 'access: none'. My work around is to go to Nautilus through GKSU and apply 'Access: read and write' to all the enclosed folders and files.

---

