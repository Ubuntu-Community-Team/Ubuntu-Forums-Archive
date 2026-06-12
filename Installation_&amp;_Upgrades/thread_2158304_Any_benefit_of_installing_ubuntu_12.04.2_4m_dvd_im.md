---
title: "Any benefit of installing ubuntu 12.04.2 4m dvd image?"
date: 2013-06-28
forum: Installation &amp; Upgrades
---

### Post by ANiK3T on 2013-06-28
hello all
i m about to install ubuntu 12.04.2LTS
on my laptop
since i have an data usage limit i want to know
WILL I NEED TO GET "UPDATE&UPGRADE" if i install ubuntu 4m DVD image

or do i still ahve to  use "sudo-apt-get-update&&sudo-apt-get-upgrade" ??

also if there is more specialised benefit of downloading big ubuntu DVD image?

--an Eager ubuntu user

---

### Post by Bashing-om on 2013-06-28
ANiK3T; Hi ! Welcome to the forum.

That one is tough to respond to ... very subjective.
1. It is always recommended to keep the OS fully up-to-date. As the install medium was created at a past time, there will now be security updates if nothing else and updates to the libraries and image files. The first update will be large.
2. Cap on data usage: If you do not have the DVD presently on-hand ... might look into purchasing a install DVD .. shipping cost might be prohibitive. And again, the first update will be large.
3. If you have some experience with 'buntu one might consider downloading the "minimal" install, and only installing the extras, bells, and whistles one really wants. ...will save a lot on data rates ! The first update will be Very small.

[INDENT][INDENT]security is a prime considration of 'buntu[/INDENT][/INDENT]

---

### Post by ANiK3T on 2013-06-28
Thanxx
 buddy well actually my main concern was If i Install Ubuntu from DVD image , do i need to check for ''update n upgrade''??
 I mean does the dvd image will contain all NECESSARY packages like ''ubuntu-restricted-extras'' 
or any other package which are downloaded from AfterInstall Update? :)

---

### Post by Mark Phelps on 2013-06-28
I don't personally know which packages the DVD contains, but historically, where there were two disk sizes -- a CD and a DVD, folks just presumed that the DVD contained the full library of Ubuntu packages, when in fact, all it really contained (over the CD) was a bunch of language packs.

While it's likely to contain some extra packages, it's probably not going to contain apps you want to install.

There is the option of downloading packages on a different machine, one that is connected to the network in a way that data charges don't apply to you, but that is very difficult to do successfully because of the interdependency of packages.  When you copy those packages to your PC and try to install them, only then do you learn that other additional packages are needed.

Sorry, but Ubuntu was really designed to be connected to the Internet for regular security updates and application installation.

---

### Post by Bashing-om on 2013-06-28
ANiK3T; 

''ubuntu-restricted-extras'== is obtained when you check the box "3rd party software", If you want flash and the restricted codecs for audio and video then yes you will need them... and yes best to get them at install time. The installer will download and install them in that install process...and yeah eats into your data cap ...

On a fresh install I always check both boxes to install the system updates and the 3rd party software... less to do after the install.

[INDENT][INDENT]hope this helps too[/INDENT][/INDENT]

---

### Post by Cheesemill on 2013-06-28
> **Bashing-om said:**
> ''ubuntu-restricted-extras'== is obtained when you check the box "3rd party software", If you want flash and the restricted codecs for audio and video then yes you will need them... and yes best to get them at install time. The installer will download and install them in that install process...and yeah eats into your data cap ...

Not strictly true.
Checking the box during installation installs the [ubuntu-restricted-addons]("http://packages.ubuntu.com/raring/ubuntu-restricted-addons") package ***not*** [ubuntu-restricted-extras]("http://packages.ubuntu.com/raring/ubuntu-restricted-extras") (extras has 4 more packages in it)

@ANik3T
The only extras included on the DVD are all of the extra language packs, it doesn't contain any more applications than the CD.
Whichever one you use to install you will still need to update after you have installed.

---

### Post by grahammechanical on 2013-06-28
Those two commands are what is run when we want to update the OS. It is our choice to run those commands. Once 12.04.2 is installed go into Software Sources and open the Updates tab and set Automatically Check For Updates to Never and you will be left in piece. Or you can set it to Daily. The data download will be smaller if you update daily than if you update Every Fortnight. With 12.04.2 there will not be daily updates. And even if Update Manager alerts you to an update being available, you can always Cancel until a more favourable time. Such as the start of a new data usage period.

Regards.

---

### Post by Bashing-om on 2013-06-28
@ Cheesemill...appreciate that ... I stand further educated !

> Checking the box during installation installs the ubuntu-restricted-addons package not ubuntu-restricted-extras (extras has 4 more packages in it)

[INDENT]takes out the trash[/INDENT]

---

