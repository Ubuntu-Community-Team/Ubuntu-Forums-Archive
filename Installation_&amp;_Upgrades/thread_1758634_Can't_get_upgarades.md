---
title: "Can't get upgarades?"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by ClientAlive on 2011-05-14
I'm running Ubuntu 10.04 LTS

I run:

```

sudo apt-get updat

```

And I get the following:

```

~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Get:2 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]                       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg [198B]          
Get:7 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [189B]                           
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Get:8 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release [38.5kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                               
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources                         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages             
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages [12.2kB]     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                                
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages [14B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages [32.3kB] 
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages [1,378B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Sources      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Sources  
Fetched 85.9kB in 2s (32.2kB/s)                           
Reading package lists... Done

```

I look through the list and see what looks like all kinds of important stuff, backports and all kinds of stuff.

I run:

```

sudo apt-get upgrade

```

and I get

```

~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

What the hell!

Can anyone help me understand why I can't get these upgrades I clearly need? Better than that, can anyone help me see how to get them?

Thanks in advance guys.

:confused:

---

### Post by lindsay7 on 2011-05-14
Check your "software sources" setting and see if you have them marked the way you want them.  See attached for example.

[ATTACH]192185[/ATTACH]

---

### Post by scubajgp on 2011-05-14
Crap, I tried to download the new release (11.04).  When re-booting I get the message 

GNU GRUB version 1.97~beta 4

[Minimal BASH-like line editing is supported.  For the first work, TAB lists possible command completions.  Anywhare else TAB lists possible device/file completions.}

What the hell am I suppose to do with this?  

Back to Windows?

I am trying to re-load 8.04 (the last version CD I have), then will try to update to 10.

Good Grief, Ubuntu!

Jerry

---

### Post by ClientAlive on 2011-05-15
Cute. Synaptic wouldn't launch. I went to the command line and launched it from there but it does so w/o administrative priveledges. All kinds of crap is messing up on my computer now. Copy/ Paste is acting up. Love it.

Does everything about linux have to be difficult?

---

### Post by ClientAlive on 2011-05-17
Yeah. This thing acts wierd sometimes; then, later, it goes away. I don't know what the deal is. Maybe someone is screwing with me. Maybe I got cracked. idk.

I get error messages all over the place as I do various things on the computer. Probably half the things I run on the command line bring up some kind of errors. It's nuts. I wouldn't even know where to begin tightening this wreck up.

The next day synaptic didn't have any problems like it had when I wrote the last post. When I looked at what you mentioned all the right stuff was checked/ ticked. Doesn't make sense to me why I wouldn't get those things listed with upgrade then.

I'm just gonna mark this one solved for now and reassess the situation.

---

### Post by ClientAlive on 2011-05-17
> **scubajgp said:**
> Crap, I tried to download the new release (11.04).  When re-booting I get the message 

GNU GRUB version 1.97~beta 4

[Minimal BASH-like line editing is supported.  For the first work, TAB lists possible command completions.  Anywhare else TAB lists possible device/file completions.}

What the hell am I suppose to do with this?  

Back to Windows?

I am trying to re-load 8.04 (the last version CD I have), then will try to update to 10.

Good Grief, Ubuntu!

Jerry


I'm really sorry to hear that man. I used 11.04 from alpha 3 through release. It was my first exper with Ubuntu (or with any Linux for that matter). I was stubborn and wouldn't listen to people who suggested I go with an earlier release. Finally, after a total debacle with 11.04 (it was my own fault though) I let my friend talk me into going with 10.04. I'm sooooo glad I did. I love 10.04 and feel like an idiot for not running it sooner.

Best of luck man. If I knew what to tell you I would. What I wrote above pretty much says it all though - I guess.

---

