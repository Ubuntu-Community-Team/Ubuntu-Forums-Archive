---
title: "How can I update repositories?"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dadedo123 on 2009-09-22
Can't really understand why I get lots and lots of errors in the repositories in the update manager. I fix them, and then I get more errors next time I try to update. Is there a command or anything that I can do so that I will not get these errors every time I try to update?

---

### Post by taavikko on 2009-09-22
Would be a lot informative if you'd tell us the errors?

---

### Post by slakkie on 2009-09-22
What kind of errors are e talking about?

---

### Post by snowpine on 2009-09-22
Can you copy and paste the errors, so we don't have to guess how to best help you? :)

---

### Post by dadedo123 on 2009-09-22
> **taavikko said:**
> Would be a lot informative if you'd tell us the errors?
It's not just this error that I want to fix. I want to stop getting these.
This is the one I get right now:
"W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"

I don't know how repositories work. Can you please tell me how I'd be able to fix them without needing to open a new thread everytime I get an error?

---

### Post by dadedo123 on 2009-09-22
I'm not really an ubuntu expert, been using it for less than a year. I just know the basics.

---

### Post by snowpine on 2009-09-22
> **dadedo123 said:**
> It's not just this error that I want to fix. I want to stop getting these.
This is the one I get right now:
"W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"

I don't know how repositories work. Can you please tell me how I'd be able to fix them without needing to open a new thread everytime I get an error?

This error tells me two things:

1. You are using the unstable, testing Karmic 9.10 release instead of the current, stable 9.04 Jaunty release... not a good idea if you are an inexperienced user!
2. You added one (or more) repositories to your sources.list without understanding what you were doing or following the instructions. 

I recommend you edit your sources:

```
gksu gedit /etc/apt/sources.list
```

and comment out (by typing the # symbol at the beginning of the line) any repositories that you added. Then try updating again and post any error messages here.

Then, at your leisure, you can read the instructions on how to correctly add a repository, paying special attention to the instructions on authentication keys.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Sorry to be blunt; but you need to know what you're doing before you edit these important system files. :)

Most software that you need should be in the standard repositories, you shouldn't need to add any extra repositories unless you have a specific software need.

---

### Post by dadedo123 on 2009-09-22
> **snowpine said:**
> This error tells me two things:

1. You are using the unstable, testing Karmic 9.10 release instead of the current, stable 9.04 Jaunty release... not a good idea if you are an inexperienced user!
2. You added one (or more) repositories to your sources.list without understanding what you were doing or following the instructions. 

I recommend you edit your sources:

```
gksu gedit /etc/apt/sources.list
```

and comment out (by typing the # symbol at the beginning of the line) any repositories that you added. Then try updating again and post any error messages here.

Then, at your leisure, you can read the instructions on how to correctly add a repository, paying special attention to the instructions on authentication keys.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Sorry to be blunt; but you need to know what you're doing before you edit these important system files. :)

Most software that you need should be in the standard repositories, you shouldn't need to add any extra repositories unless you have a specific software need.
So I should remove the repositories that I am having problems with?

---

### Post by snowpine on 2009-09-22
> **dadedo123 said:**
> So I should remove the repositories that I am having problems with?

I recommend simply commenting them out with a # symbol at the start of the line. That way, you can add them back in one by one after you've added the key.

Good luck! Post back if you need any more help. :)

---

### Post by dadedo123 on 2009-09-22
Sorry I am lost, I don't know what to do. This is what I get when I type this in the terminal. :

> # deb cdrom:[Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Alpha i386 (20090917)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://bh.archive.ubuntu.com/ubuntu/](http://bh.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://bh.archive.ubuntu.com/ubuntu/](http://bh.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse

---

### Post by snowpine on 2009-09-22
Whoa, your list looks totally normal, doesn't look like you added anything it at all... so sorry if I was harsh with you earlier. :)

Can you try running this command from the terminal and post the output:

```
sudo apt-get update
```

---

### Post by taavikko on 2009-09-22
> **dadedo123 said:**
> It's not just this error that I want to fix. I want to stop getting these.
This is the one I get right now:
"W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"

I don't know how repositories work. Can you please tell me how I'd be able to fix them without needing to open a new thread everytime I get an error?

Hmm. that's the corrct key for ubuntu's repositories...
I would remove the key and re-add it.

Use seahorse (Applications->accessories->passwords -->> other keys)
and remove the "Ubuntu archive automatic..." key.
the we re-add it using the terminal.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key 437D05B5
```

It should clear the issue...

Your sources.list is fine at quick look.

---

### Post by dadedo123 on 2009-09-22
> **snowpine said:**
> Whoa, your list looks totally normal, doesn't look like you added anything it at all... so sorry if I was harsh with you earlier. :)

Can you try running this command from the terminal and post the output:

```
sudo apt-get update
```

> hassan@HassanX2008:~$ sudo apt-get update
[sudo] password for hassan: 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release [65.9kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages   
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages [7311B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources [635kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources                                                                     
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages [5132kB]                                                           
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources [2769kB]                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages                                                            

btw thanks for helping me! :D

---

### Post by snowpine on 2009-09-22
Yay! Sorry for the tone of my earlier post. :)

---

### Post by shakaran on 2009-09-23
keyserver.ubuntu.com is down? I cant connect for keys.

---

