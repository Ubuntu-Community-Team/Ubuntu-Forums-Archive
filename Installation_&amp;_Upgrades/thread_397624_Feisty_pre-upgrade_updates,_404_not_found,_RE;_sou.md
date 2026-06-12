---
title: "Feisty pre-upgrade updates, 404 not found, RE; sources.list"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by Toadmund on 2007-03-30
I am trying to update to feisty, having problems with my sources.list listings, I get this when trying to update edgy:

[*url]http://ubuntusoftware.info/dists/edgy/all/binary-amd64/Packages.gz:[/url*] 404 Not Found

(* added to prevent linking)

So I deleted the last thing I entered, which was Givre's repos for the windows hard drive ntfs issue.
which starts here:
[http://www.ubuntuforums.org/showthread.php?t=217009]("http://www.ubuntuforums.org/showthread.php?t=217009") and branches off into the AMD64 department. I may have mucked things up, I don't think that was the problem?

So, looooong story short, could a knowledgeable enough person help me out with my issue?

Here is my sources.list (sudo gedit /etc/apt/sources.list)
> 
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
##deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
##deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb [http://ubuntusoftware.info/](http://ubuntusoftware.info/) edgy all
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END


deb-src [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main-all



Thanks.

---

### Post by qamelian on 2007-03-30
From the information at the top of the ubuntusoftware.info homepage, I'd say just wait it out and try again. It sounds like a new release of one of their projects generated too much interest and took them down.

---

### Post by Toadmund on 2007-03-30
So it's not me?

Another question, should I just ignore this 404 and upgrade to feisty anyway?
I have some small issues with edgy, I decided that instead of fighting and busting my brains over edgy, I may as well upgrade, in the thoughts that feisty will take care of some things I need that edgy may lack, like NTFS mounting. Can't seem to get mounted.
Mount me.
Ahem, No, not me, my HD's:)

---

### Post by qamelian on 2007-03-30
> **Toadmund said:**
> So it's not me?

Another question, should I just ignore this 404 and upgrade to feisty anyway?
I have some small issues with edgy, I decided that instead of fighting and busting my brains over edgy, I may as well upgrade, in the thoughts that feisty will take care of some things I need that edgy may lack, like NTFS mounting. Can't seem to get mounted.
Mount me.
Ahem, No, not me, my HD's:)

Edgy mounts my ntfs partitions fine on my desktop. I don't know how Feisty compares in that respect because my Laptop hasn't seen Windows since I installed Linux on it immediately after unpacking it!

If you are upgrading to Feisty through the update manager, you can probably ignore the error as Update Manager automatically disables all third party repos like this one. However, anytime you install software from sources outside the official repos, you run the risk of your upgrade going down in flames. 

That said, my laptop has a lot of non-official apps on it and it upgraded just fine. Just remember, if the Update Manager starts to complain about things during the upgrade, don't try to force it. Way a day or two and see if the issue resolves itself. 

ANd make sure you have a backup of anything valuable on you drive before even thinking about doing an upgrade!

---

### Post by Toadmund on 2007-03-30
Seems I get feisty on the go to update (decided to go ahead), the same message pops up and aborts me. (the 404 amd line)

---

### Post by Toadmund on 2007-03-31
Well I used this ubuntu linux for human beings -sources.list generator:
[HERE]("http://www.ubuntu-nl.org/source-o-matic/") 
and I replaced my sources.list by inputing ```
sudo gedit /etc/apt/sources.list
``` into the terminal. and deleting the old and pasting the new generated sources into the gedit page and saved it.
I'll see how it goes, it got rid of that particular mesage anyway.

---

