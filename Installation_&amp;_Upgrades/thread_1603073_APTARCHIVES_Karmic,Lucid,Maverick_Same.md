---
title: "APT/ARCHIVES Karmic,Lucid,Maverick Same?"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by Sean Moran on 2010-10-22
I am still after all this time trying to build a nice custom distro of Ubuntu to suit these everchanging circumstances in which I continue to find myself.  What is troubling my 16Gb scratch partition now is the /var/cache/apt/archives or the size of them all when I am working with Karmic/Lucid/& Maverick for my foundations.

The question I wish to ask is: If I were to combine the three /var/cache/apt/archive dirs, then would they (if everything different and everything the same between the three was merged but all there), still find the packages they require?

I'm generally starting with standard Ubuntu, and adding some favourite system utilities, such as GParted, MountManager, Startup Manager, GnomeCommander, Fortunes, and a few more.  I add Seamonkey and Filezillla, Flash, Acrobat, Skype, (from separate source) and Galaga of all things, then the server stuff is Apache2, MySQL, PHP5, phpmyadmin and that about covers it apart from the Thai and Khmer language additions, if I remember.

Is it worth combining all these extgra .DEB files into one directory, or are they all different for each of these three distributions, (assuming I have the updates), for Karmic, Lucid and Maverick?


---o0o---

Put simply, do all these three distributions of Karmic, Lucid, and Maverick share some common .DEB files, or would a combination triple the size of the /var/cache/apt/archives files?  I can accept that there would be some spinover and that not All files are the same, (eg. linux-headers) but can anyone give me a rough guess on the percentage of .DEB files that are shared between distros, if any?

---

### Post by quequotion on 2010-10-22
> **Sean Moran said:**
> I am still after all this time trying to build a nice custom distro of Ubuntu to suit these everchanging circumstances in which I continue to find myself.  What is troubling my 16Gb scratch partition now is the /var/cache/apt/archives or the size of them all when I am working with Karmic/Lucid/& Maverick for my foundations.

The question I wish to ask is: If I were to combine the three /var/cache/apt/archive dirs, then would they (if everything different and everything the same between the three was merged but all there), still find the packages they require?

I'm generally starting with standard Ubuntu, and adding some favourite system utilities, such as GParted, MountManager, Startup Manager, GnomeCommander, Fortunes, and a few more.  I add Seamonkey and Filezillla, Flash, Acrobat, Skype, (from separate source) and Galaga of all things, then the server stuff is Apache2, MySQL, PHP5, phpmyadmin and that about covers it apart from the Thai and Khmer language additions, if I remember.

Is it worth combining all these extgra .DEB files into one directory, or are they all different for each of these three distributions, (assuming I have the updates), for Karmic, Lucid and Maverick?


---o0o---

Put simply, do all these three distributions of Karmic, Lucid, and Maverick share some common .DEB files, or would a combination triple the size of the /var/cache/apt/archives files?  I can accept that there would be some spinover and that not All files are the same, (eg. linux-headers) but can anyone give me a rough guess on the percentage of .DEB files that are shared between distros, if any?

I'm not entirely sure what you're trying to do...

Is there a reason why you'd want to make a single distro out of packages from three different distros?

They may share some packages of the same version number, but that doesn't mean the packages were built against the same libraries and they may in fact be quite different. Also, there are many packages that have been slightly renamed (ie library0, version 1.0 upgraded to library1, version 1.1) as they were upgraded, so you could end up with redundant packages. Furthermore, I don't think there's any simple way to combine apt archives from three different distros and keep "everything different and everything the same between the three". You're likely to end up with a mess of broken packages.

Am I way off base here?

---

### Post by Sean Moran on 2010-10-22
> **quequotion said:**
> I'm not entirely sure what you're trying to do...

Is there a reason why you'd want to make a single distro out of packages from three different distros?

They may share some packages of the same version number, but that doesn't mean the packages were built against the same libraries and they may in fact be quite different. Also, there are many packages that have been slightly renamed (ie library0, version 1.0 upgraded to library1, version 1.1) as they were upgraded, so you could end up with redundant packages. Furthermore, I don't think there's any simple way to combine apt archives from three different distros and keep "everything different and everything the same between the three". You're likely to end up with a mess of broken packages.

Am I way off base here?

You're spot on mate,  

I like Karmic, and I know that most people probably want the latest. so I'm not building one custom distro, but have to make my standard adjustments to my favourite Karmic, and then reproduce the same for Lucid and Maverick.  I'm running a new build for Meerkat right now, but I'm curious about how many .DEB files might be the same for all distros, (providing I use the latest updates for each package).

If I could combine it all (the three different /var/cache/apt/archive/ dirs into one, would that cut down the total number of files and Gb? If most app .debs are okay between all three, it would ease my pain, but how many of Karmic's .DEB files can run across to Maverick?

---

### Post by quequotion on 2010-10-23
> **Sean Moran said:**
> You're spot on mate,  
If I could combine it all (the three different /var/cache/apt/archive/ dirs into one, would that cut down the total number of files and Gb? If most app .debs are okay between all three, it would ease my pain, but how many of Karmic's .DEB files can run across to Maverick?

The answer this question, being seriously complex, could most likely summed up as "No..."

I think you could save yourself a lot of trouble with online installation.

How's this for a theory:

1. Get the package list in your customized Karmic.

2. Collect all of your custom configurations.

3. Make a script to apply your custom configurations.

4. Upgrade to Lucid and get the package list again.

5. Make a diff of the package list for Karmic to Lucid.

6. Upgrade to Maverick and get the package list again.

7. Make a diff of the package list for Karmic to Maverick.

8. Spin your own LiveCD/DVD with a customised installer (***not easy***). On this disc will be Ubuntu Karmic Koala with all of your customizations; if that includes any packages that are not available from a deb repository, you'll have to make sure they are on the disc.


Here's how such an installer could work, given it asks the end user which version of Ubuntu they want (this is really not code, just logic)```
if (selected version != Karmic)

     if (selected version == Lucid)
          apply Lucid diff to SeanMoranPackagelist
          use Lucid repositories # (and disc)
     fi

     if (selected version == Maverick)
          apply Maverick diff to SeanMoranPackagelist
          use Maverick repositories # (and disc)
     fi

     else
          Error: invalid version
     esle

fi

install SeanMoranPackagelist

apply SeanMoranConfig
```

As an alternative, you could make a script that installs your selected packages and applies your configurations to existing Ubuntu installations (a la Ubuntu Studio).

Please don't take any of this as discouragement! 

Actually I'm interested in making a distribution myself (emUbuntu/gameUbuntu/fUnbuntu), but it seems to make one well takes a serious dedication of time and effort and then a commitment to maintain that distribution...

---

### Post by Sean Moran on 2010-10-23
> **quequotion said:**
> The answer this question, being seriously complex, could most likely summed up as "No..."

I think you could save yourself a lot of trouble with online installation.

How's this for a theory:

1. Get the package list in your customized Karmic.

2. Collect all of your custom configurations.

3. Make a script to apply your custom configurations.

4. Upgrade to Lucid and get the package list again.

5. Make a diff of the package list for Karmic to Lucid.

6. Upgrade to Maverick and get the package list again.

7. Make a diff of the package list for Karmic to Maverick.

8. Spin your own LiveCD/DVD with a customised installer (***not easy***). On this disc will be Ubuntu Karmic Koala with all of your customizations; if that includes any packages that are not available from a deb repository, you'll have to make sure they are on the disc.


Here's how such an installer could work, given it asks the end user which version of Ubuntu they want (this is really not code, just logic)```
if (selected version != Karmic)

     if (selected version == Lucid)
          apply Lucid diff to SeanMoranPackagelist
          use Lucid repositories # (and disc)
     fi

     if (selected version == Maverick)
          apply Maverick diff to SeanMoranPackagelist
          use Maverick repositories # (and disc)
     fi

     else
          Error: invalid version
     esle

fi

install SeanMoranPackagelist

apply SeanMoranConfig
```As an alternative, you could make a script that installs your selected packages and applies your configurations to existing Ubuntu installations (a la Ubuntu Studio).

Please don't take any of this as discouragement! 

Actually I'm interested in making a distribution myself (emUbuntu/gameUbuntu/fUnbuntu), but **it seems to make one well takes a serious dedication of time and effort and then a commitment to maintain that distribution..**.

That is precisely why I thread this question my friend.

My objective is a bit like Linux Mint, with Skype et al. but now I'm trying ti run my bash shel script which calls on chroot to do the adjustments on these three different distros, and my script saves the chroot/var/cache/apt/archives/ files from one build, and then copies the same back to the next to reduce download times.  If I could combime the .deb files from Karmic with the deb files from Lucid and Maverick, and let's take a guess at around 700Mb each to a total of 2Gb, would there be any use in putting all of thed archives in one common directory, even if it made it a little bigger?  

I hope that Karmic and Lucid and Maverick might share some commoln .DEB diles if we maintain our updates, and that is what I seek to ask, because it will take a long time to work this out by myself, and I take a guess that others have the answer that I will need three or four mkore days to discover.

---

