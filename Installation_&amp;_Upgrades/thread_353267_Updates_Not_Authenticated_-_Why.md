---
title: "Updates Not Authenticated - Why?"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2007-02-04
This is the first time ever that I am receiving the "Updates Not Authenticated" warning from my update manager. Why?

I didn't change anything in my repositories configuration. Here is the contents of my system's  **/etc/apt/sources.list**:


> # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


Any idea what happened?

Thanks,
Alex

---

### Post by taurus on 2007-02-04
Paste the output of these two commands from a terminal here.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by xp_newbie on 2007-02-04
Thanks for the quick reply.

For 'sudo aptitude update' I get:

> Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done      
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources                              
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]                                                                                 
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]                                                                                           
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [50.9kB]                                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages                                                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages                                                                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages                                                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages                                                                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources                                                                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources                                                                                   
Fetched 51.3kB in 11s (4591B/s)                                                                                                                     
Reading package lists... Done


As for 'sudo aptitude upgrade' - isn't this going to actually circumvent the nice warning propmt about authentication? I don't want to upgrade before I understand why, after months of nicely behaving updates, I suddenly getting this warning.

Thanks,
Alex

---

### Post by taurus on 2007-02-04
You still get a chance to cancel the upgrade with a **n** if you want to.  Just want to see the exact error message and from what repo but again, it's up to you.

---

### Post by xp_newbie on 2007-02-04
OK. I didn't know that I get a confirmation prompt after typing this command (I try to be consistent with my install/update methodology and so I solely use synaptic/update manager).

Here is the output of ' sudo aptitude upgrade':

> Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done      
The following packages will be upgraded:
  app-install-data-commercial gtk2-engines-pixbuf libc6 libc6-dev libc6-i686 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common 
  synaptic 
9 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.4MB of archives. After unpacking 4096B will be used.
Do you want to continue? [Y/n/?] n
Abort.


Thanks,
Alex

---

### Post by taurus on 2007-02-04
Those seem to be some standard packages and I don't see any error message about them.  So, do you want to update those packages?

---

### Post by xp_newbie on 2007-02-04
> **taurus said:**
> So, do you want to update those packages?

Not as long as I keep getting the "not authenticated" warning message. You see, I trust Synaptic's judgement. :)

I will wait until the warning disappears (seems to me like a bug or a temporary problem) - or until someone comes with a satisfactory explanation.

Thanks,
Alex

---

### Post by xp_newbie on 2007-02-06
OK - problem solved. O:) 

How?  Very simple:** I just waited until the problem would go away by itself **- without me doing anything.

As I suspected, there was nothing wrong on my side, but rather a temporary bug or glitch in the Ubuntu Updates distribution system. The updates were not authenticated and once somebody out there noticed that, they fixed it.

I am wondering now how they learned about the problem, since I certainly wasn't the one who brought this to their attention. How does one contact the developers or the "package authenticators" anyway?

---

### Post by xp_newbie on 2007-04-04
Actually, the problem re-appeared. :(

This time I couldn't just wait and let the system "fix itself". I compare /etc/apt/sources.list to another one in a system that does not exhibit the problem. The difference was obvious:

Replace
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
With
> deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted

That's it. Problem solved. I have no idea why and I have a feeling that anyone who reads this post doesn't understand why either (otherwhise s/he would have come with an answer long ago).

---

### Post by jocko on 2007-04-04
> Replace
 	Quote:
 	 	 		 			 				deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted 			 		 	 	 
With
 	Quote:
 	 	 		 			 				deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted 			 		 	 	 
That's it.

Why would you want to replace dapper-updates with dapper-security?
Those are different repos, meaning that they will probably contain different packages and you'll probably need both to avoid problems in the future.
The result of doing this is that you will never get any updates from dapper-updates, plus you'll probably get an error message about duplicate sources in your list (dapper-security should already be there, unless you have removed it.)

About the authentication problem: All your repos (as far as I can see in your first post) are from the official Ubuntu repositories.
I have noticed authentication problems from the official repos a few times, but I have chosen to trust the maintainers of those repos.
If you can't trust the official repos, who can you trust?

---

### Post by xp_newbie on 2007-04-04
> **jocko said:**
> Why would you want to replace dapper-updates with dapper-security?
To get rid of the "Updates Not Authenticated" warning message.

> **jocko said:**
> If you can't trust the official repos, who can you trust?
I trust Ubuntu's Update Manager. If it tells me that the updates are not authenticated, why shouldn't I trust it?

---

### Post by vierdreieins on 2007-04-05
I'm having the same issue, and am hoping it'll just go away on its own. So far I've just been ignoring any updates because I'm unsure which one/s isn't/aren't authenticated.

Edit: Just found out it's because one of them is Automatix. #-o

---

### Post by ianmac on 2007-04-10
> **xp_newbie said:**
> To get rid of the "Updates Not Authenticated" warning message.


I trust Ubuntu's Update Manager. If it tells me that the updates are not authenticated, why shouldn't I trust it?

But I think all you are doing by switching from dapper-update to dapper-security is telling synaptic to look in a different place so that it won't find the updates that were not authenticated.  Those updates might be important.

Ian

---

### Post by xp_newbie on 2007-04-12
> **ianmac said:**
> But I think all you are doing by switching from dapper-update to dapper-security is telling synaptic to look in a different place so that it won't find the **updates that were not authenticated**.  Those updates might be important.

I agree that the unauthenticated updates might be important, but this is starting to look like a catch 22 situation...

On one hand, Ubuntu provides a mechanism to authenticate updates, so that I don't have to apply my own (ignorant) judgement for each and every update.

On the other hand, I am expected to ignore the "Updates Not Authenticated" message when it pops up, thus applying my own (ignorant) judgement???

Pleeeeeeeeeeease... 

Regards,
Alex

---

