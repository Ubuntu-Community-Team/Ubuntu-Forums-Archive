---
title: "installing softwares without internet"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by dhruva023 on 2007-10-22
hi,

i am going to install ubuntu on one of my friends computer.

he doesn't have internet.

how can i install softwares ( mp3 codecs , and other software ) withount internet?

i mean, what should i do to get deb files for those softwares?

---

### Post by seldenthuis on 2007-10-22
You can download the Ubuntu DVD from:
[http://cdimages.ubuntu.com/releases/7.10/release/]("http://cdimages.ubuntu.com/releases/7.10/release/")

It contains all supported packages, which you can install by using the DVD as a repository.  I don't know if things like the mp3 codecs are on there though.

---

### Post by ruibernardo on 2007-10-22
To install other packages that aren't on the DVD, you could try [nonetdebs]("http://ubuntuforums.org/showthread.php?t=572819"), a script I've made to download packages you need (updates) or want (install new packages) on another X/K/Ubuntu without internet. 

The connected computer doesn't need to be the same release of the offline computer (you can even run it in a LiveCD), but you will need a file from the offline computer and a USB pen (or be able to burn an ISO file on the connected computer) to save the packages and take them to the other computer.

---

### Post by dhruva023 on 2007-10-22
thanks,

i will be trying it tomorrow.

---

### Post by iblazev on 2007-11-28
> **seldenthuis said:**
> You can download the Ubuntu DVD from:
[http://cdimages.ubuntu.com/releases/7.10/release/]("http://cdimages.ubuntu.com/releases/7.10/release/")

It contains all supported packages, which you can install by using the DVD as a repository.  I don't know if things like the mp3 codecs are on there though.

Hello :)
I have a similar problem BUT I do have a Kubuntu DVD (managed to get me one by net from work :)). 
Now, when trying to install MP3 libs for Amarok, nothing happens (don't have Internet connection at home). In the repository settings in Add/Remove programs dvd is listed for a third party software repository. 
I tried searching for missing files for Amarok on DVD but haven't found any. Guess it doesn't come on it. 
So, HOW to check and get those files from internet? NoNetDebs that epimeteo suggested won't work cause I don't have any comp with Internet connection that I can boot with Live cd or USB stick.
Is there a DVD collection available with libs and stuff? I remember that DEBIAN 3.0 Woody did have almost everything on CD's...

---

### Post by ruibernardo on 2007-11-28
Hi iblazev,

there is a website version of nonetdebs since 30th October. You can use it from any Windows machine (or other connected computer with an internet browser) on a library, from work, etc. You will need to upload the status file (~1MB). More info on the thread I pointed on my previous post.

Good luck.

---

### Post by waffen on 2007-11-28
Hello,

You have two choices:

1. Download the Ubuntu Alternate
2. Create a CD Repository with APTonCD

Mario

---

### Post by ruibernardo on 2007-11-28
Hi waffen, 

both iblahzev and dhruva023 said that they have the DVD, which includes the alternate CD and still they can't reproduce mp3 files. The alternate CD doesn't have the packages for mp3. They are on the repositories (multiverse and medibuntu).

After downloading the links of the packages they need from nonetdebs, they can create a CD repository with aptoncd to make the installation of the packages more easy and graphical. Still they need to install aptoncd, which they can get the links to download it from nonetdebs.

nonetdebs is only a way to get the links of the packages they need from the repositories from another computer.

---

### Post by iblazev on 2007-11-29
epimeteo
there seems to be a problem when trying to get new packages with nonetdebs. I did everything from the help on the pages but when I tried to get aptoncd I got this massage:
*E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). *

Should I first get all the files that aptoncd depends on?

---

### Post by ruibernardo on 2007-11-29
iblazev, you need to enable the repositories where the dependencies of aptoncd are. Try to enable the "Main" and "Universe" repository as minimum (aptoncd is on "Universe", but some dependencies are on "Main"). That should do.

If that error continues, then some dependencies might be in "Multiverse" and/or "Restricted" repos (very unlikely for aptoncd, but can happen for other packages).

---

### Post by iblazev on 2007-11-29
I did. First I did only with universe repo and then I included multiverse, main and restricted even. Same error. Don't have a clue why cause I followed the instructions to the letter. 
Will try again.

---

### Post by ruibernardo on 2007-11-29
Strange, that happen to me too when I tried it.

I've then unchecked the medibuntu and canonical repos and enabled main/universe only, clicked "new packages" and it worked.

---

### Post by iblazev on 2007-11-29
Tried again just now and it worked! I first deselected every repo that has been selected, submited then selected only main and universe and it worked:) Strange though..
Anyways, will get me some packages and I'll tell u tomorrow how it all went :)))
Thanx for the link epimeteo!

---

### Post by ruibernardo on 2007-11-29
Glad it worked. 

I have to check why it happened. Maybe I have to clear the apt-get cache in the chroot between users.

---

### Post by iblazev on 2007-11-30
Glad to say that all worked well after downloading packages with nonetdebs:) Good work epimeteo!
Only one package was a problem - aptoncd (I also downloaded kmplayer and xine libs for mp3 and that went well). Aptoncd missed some dependencies that weren't in status file but nonetdebs didn't noticed that./
Anyways, this helps a lot! Thanx again for the effort:)

One more thing, it a bit OT but.. I have x86_64 version of kubuntu, can I use i386 and amd64 packages together? Like half of one and half of the other for the one program that needs them? Or must they all be the same version? I ask this cause I've noticed that all packages downloaded were i386 versions...

---

### Post by ruibernardo on 2007-11-30
> **iblazev said:**
> Glad to say that all worked well after downloading packages with nonetdebs:) Good work epimeteo!
Only one package was a problem - aptoncd (I also downloaded kmplayer and xine libs for mp3 and that went well). Aptoncd missed some dependencies that weren't in status file but nonetdebs didn't noticed that./
Anyways, this helps a lot! Thanx again for the effort:)

One more thing, it a bit OT but.. I have x86_64 version of kubuntu, can I use i386 and amd64 packages together? Like half of one and half of the other for the one program that needs them? Or must they all be the same version? I ask this cause I've noticed that all packages downloaded were i386 versions...

Glad it worked and was useful for your, iblazev.

About the amd64 packages, unfortunately nonetdebs isn't prepared to other computer architectures but i386 for now. I will change it. It is doable because apt-get has "super cow powers" and I think that there are options to work with other architectures.

I think that generally the packages are compiled from the same sources, just optimized for the target architecture (you can compile programs for PPC on a i386 for example), but some packages can have different sources for amd64/PPC/i386/etc and/or have different dependencies. Others don't even exist in the amd64 and PPC repositories. For most of the packages this means that you shouldn't have any problem, but for some packages it can mean that they will not work on amd64 -- Can anybody confirm this?

This might imply that, after I make the changes to enable other architectures in nonetdebs, you'll need to uninstall the packages you installed and install new ones - sorry about that, you were the first user that brought up this issue.

I'll reply when I enable other architectures on the website (in 1 day or 2). Until then do not click "Upgrade" on the website and please reply if you encounter any problems with the installed packages.

PS: please save a copy of the first status file you used. It might be needed to track which packages you downloaded for i386 and to know which amd64 packages you need to replace them.

---

### Post by ruibernardo on 2007-11-30
Done. Now users must select the architecture of the offline computer.

---

