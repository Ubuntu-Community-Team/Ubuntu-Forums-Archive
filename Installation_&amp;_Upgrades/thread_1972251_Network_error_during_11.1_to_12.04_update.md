---
title: "Network error during 11.1 to 12.04 update"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by X10A on 2012-05-03
I get the following message:

Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.192 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.192 80]
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Does anyone know how can I solve this?

---

### Post by X10A on 2012-05-03
I also cannot install via the Live CD/DVD. For some reason, the installation does not detect my version of ubuntu 11.1 and I do not get the "upgrade" option.

---

### Post by mips on 2012-05-03
> **X10A said:**
> I also cannot install via the Live CD/DVD. For some reason, the installation does not detect my version of ubuntu 11.1 and I do not get the "upgrade" option.

Did you add the CD/DVD to your repos?

If I was you I would backup /home and do a fresh install rather as I'm seeing a lot of upgrades going wrong on 12.04.

---

### Post by X10A on 2012-05-03
> **mips said:**
> Did you add the CD/DVD to your repos?

If I was you I would backup /home and do a fresh install rather as I'm seeing a lot of upgrades going wrong on 12.04.

Thanks for the advice! How do I do that? Add the CD/DVD to the repo, and why?

I run a dual-boot, so given that the installation package does not recognise my prior ubuntu 11.1, I'd have to further divide my linux partition if I did a fresh install.

---

### Post by X10A on 2012-05-07
Is there a way to upgrade straight from the terminal?

sudo apt-get release-upgrade

does not work.

---

### Post by afrazin on 2012-05-07
I'm having this problem too.  I'm getting:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources)   404 Not Found [IP: 91.189.92.193:80]

any suggestions?

---

### Post by X10A on 2012-05-09
Does it have to do with whether we're using a wired/wireless connection?

Or is it a choice in the ubuntu server?

I've tried alternating to no avail.

---

### Post by jadtech on 2012-05-09
try a different server   any time you have a 404  the server is down or missing ..

change it in the software manager in settings .. 

then type these in order .. 

```
 sudo apt-get update

   do-release-upgrade 


```

---

### Post by afrazin on 2012-05-10
My problem doesn't have anything to do with the wired/wireless connection.  i have an internet connection on the machine other than the updates.

i don't mind trying another server, but is there a list of servers somewhere?  i couldn't find it.

thanks!

---

