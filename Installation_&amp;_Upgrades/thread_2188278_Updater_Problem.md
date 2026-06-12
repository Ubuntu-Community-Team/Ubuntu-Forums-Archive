---
title: "Updater Problem"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by tschill on 2013-11-16
Hi, 

Not sure, this is the right category here, but wouldn't know where else to post it. I have two problems relating to updates of my Ubuntu 12.04LTS:

1) I removed everything Medibuntu with the Synaptic Package Manager. Nonetheless, whenever I check the update manager, it tells me it can't load new information, because there is no website connected to the Medibuntu repositories:

> W:Failed to fetch [http://packages.medibuntu.org/dists/natty/Release.gpg](http://packages.medibuntu.org/dists/natty/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/natty/free/binary-i386/Packages](http://packages.medibuntu.org/dists/natty/free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/natty/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/natty/non-free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/natty/free/i18n/Translation-en](http://packages.medibuntu.org/dists/natty/free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/natty/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/natty/non-free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

2) When I open the Synaptic Package Manager I get the following error message:

> W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)

I had a look at the file, but couldn't spot any duplicate entries. 

Any suggestions what to do to get rid of these error messages?

Thanks for taking the time to read it.

---

### Post by grahammechanical on 2013-11-16
You said that you removed everything Medibuntu with synaptic. Did you mean you removed the PPAs or repositories from Software Sources? I am just checking to avoid confusion.

There are a couple of commands that I have used to reset the sources lists when I have had issues like this.

```
sudo rm /var/lib/apt/lists/* -rf
```
```
sudo apt-get update
```

The first command removes or deletes all the files/lists in the lists directory, including any duplicated list. The second command will replace the sources lists with updated versions and that will let you update with Update Manager. Or you can do it with this command.

```
sudo apt-get upgrade
```

Synaptic and Update Manager provide GUI front-ends for the apt-get set of commands.

Regards.

---

### Post by Bucky Ball on 2013-11-16
Have you got them unticked in your software sources? You can remove them there too.

Update Manager>Settings (bottom left corner)>Other Software. You should see the PPA for Medibuntu there. Remove.

---

### Post by tschill on 2013-11-16
OMG, how stupid of me. I definitely don't speak Linux. Yes, I didn't do this. Removed the abandonded Medibuntu from Software Sources and problem #1 was solved. Plus I noticed there were several ticked Canonical Partner sources (though I don't understand why they appeared there), so I unticked all except one and problem #2 was solved. 

Thank you so much for your suggestions, this was really helpful.

---

### Post by Bucky Ball on 2013-11-16
All good. If happy please mark thread as solved to help others by following instructions in my signature. ;)

---

### Post by BikeRich on 2014-05-25
Bucky Ball :  

      Thank you. 

        BikeRich

---

