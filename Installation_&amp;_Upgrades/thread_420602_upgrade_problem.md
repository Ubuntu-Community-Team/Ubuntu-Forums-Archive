---
title: "upgrade problem"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by curtk69 on 2007-04-23
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

i keep getting this error only i have no apparent problem with my network as i connect directly to the net

---

### Post by zvacet on 2007-04-23
```
sudo aptitude update
```

---

### Post by cdrom600 on 2007-04-23
I get the same problem whenever I try to upgrade; I've already tried sudo aptitude update.

I also get this problem when I click "Check" in the Update Manager:
```
Could not download all repository indexes:
http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
```

---

### Post by marcjboudreau on 2007-04-23
That's the same error I've been getting for days. I've tried a bunch of the solutions offered but haven't figured out how to fix it? Is it just server overload?

---

### Post by cdrom600 on 2007-04-23
Which solutions have you tried?  I don't think it's just server overload anymore; it's been out for a few days now.  Plus, it always fails on the same two files, which suggests to me that it isn't something simple like server overload.

---

### Post by derbium on 2007-04-23
Same problem here!
running sudo aptitude update results in the following errors:

```
          
Get:12 http://archive.canonical.com edgy-commercial/main Packages [1066B]       
99% [12 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fbzip2: (stdin) is not a bzip2 file.
Err http://archive.canonical.com edgy-commercial/main Packages                  
  Sub-process bzip2 returned an error code (2)

...

Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com edgy-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_edgy-commercial_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these proble
```


sudo apt-get update results in:
```
     
99% [8 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fobzip2: (stdin) is not a bzip2 file.
Err http://archive.canonical.com edgy-commercial/main Packages                  
  Sub-process bzip2 returned an error code (2)
...                       
99% [11 Packages bzip2 0] [Release gpgv 38398] [Waiting for headers] [Waiting fobzip2: (stdin) is not a bzip2 file.
Err http://archive.canonical.com edgy-commercial/main Packages                  
  Sub-process bzip2 returned an error code (2)

Failed to fetch http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Any ideas?

---

### Post by marcjboudreau on 2007-04-23
I've tried changing servers, I've tried editing my sources list from http to ftp. I've tried to update through the terminal a few times. I found a thread that showed how to edit the sources list and I've tried that too.
There maybe a few other things I've tried as well. 
This seems to be a pretty common error, as there are multiple threads on it, but I haven't found a thread on here yet, that's offered a solution that works for me.

---

### Post by cdrom600 on 2007-04-23
I really won't have time tonight to work on this; tomorrow I might get a chance.  Otherwise, I might have time this weekend.
Everything I've read seems to indicate that the problem is caused by some sort of conflict in apt lists and source lists.  Third-party repositories could also be involved.  That's as far as I've gotten, and all the time I have to spend on the problem tonight.
Also, I'm now downloading the alternate install CD to see if I can upgrade from it.

---

### Post by pimpmagnum on 2007-04-23
I just removed my 3rd party sources and that fixed the problem right up.

---

### Post by marcjboudreau on 2007-04-23
Sigh, the good times never end. I'm not sure what I've done now but I can't even get it to open the udate manager anymore.
I'm getting this error.

```
marc@marc-desktop:/$ sudo aptitude update
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: The list of sources could not be read.

```

Sweet, friggin' sweet.:confused:

---

### Post by dermanus on 2007-04-23
Disabling third party software worked for me too. Update is running now.

Remains to be seen if there will be any problems post-upgrade...

---

### Post by Michl on 2007-04-24
So you can;t upgrade via internet if, say, you have Shredder Chess installed?

---

### Post by curtk69 on 2007-04-24
PIMPMAGANUM, you said in a post aboutUPGRADE PROBLEM that you just removed your 3rd party sources and it worked.

do i assume u were getting the same errors?
when i try to upgrade ubuntu says 3rd party sources were disabled for me but the install still fails

any ideas?

---

### Post by passioncycles on 2007-04-24
Hello I am in the middle of upgrading to Fiesty....  i have rebooted  once the upgrade was completed the splash screen has changed  and now all my menu and files on the desktop are all buggered up ...all the text is white rectangles.....any thoughts suggestions

---

### Post by Michl on 2007-04-24
> **passioncycles said:**
> Hello I am in the middle of upgrading to Fiesty....  i have rebooted  once the upgrade was completed the splash screen has changed  and now all my menu and files on the desktop are all buggered up ...all the text is white rectangles.....any thoughts suggestions

Did you start from an updated edgy?  just wondering.  It seems like the updating to Feisty is a huge risk
and I decided against it on the computers I really need for work and have configured for my needs.
I did a clean install on a computer without much on it and it went smoothly, but all these troubles with upgrading frighten me.  I actually started to upgrade, but immediately ran into trouble with some error commands, and
so I said whoah -- this is can be one of those bug-laden unpredictable experiences that seems to dog the linux experience.  I don't have the time to search the forums for days, edit this and that config file and then break down and do a clean install anyway.

M

---

### Post by dmargerum on 2007-04-26
I.m a newbie, but I was having the same issue until i disabled third party sources (under system,administration,synaptic package manager,settings,repositories,third party apps). I unchecked all third party sources and the upgrade proceeded fine.

---

### Post by cdrom600 on 2007-04-26
Editing my /etc/apt/sources.list and commenting out the third-party repositories seems to have worked for me this time.  Best of luck to everybody.

---

### Post by curtk69 on 2007-04-27
> **dmargerum said:**
> I.m a newbie, but I was having the same issue until i disabled third party sources (under system,administration,synaptic package manager,settings,repositories,third party apps). I unchecked all third party sources and the upgrade proceeded fine.

that seems to have been my problem, as soon as i manually disabled these 3rd party sources my update started.

now i cross my fingers and hope the upgrade doesnt break anything? !!

---

