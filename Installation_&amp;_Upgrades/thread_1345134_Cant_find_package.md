---
title: "Cant find package"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by fr3w on 2009-12-03
Hello!
I am kinda new to the linux OP's. I've got it running like i want it to 90%, one thing i miss i the music. Currently im tryin to use the Amarok audio-player, but it wont play my mp3 files. 
I found a few answers when i googled for a solution, the mmost common one i found was to install the "gstreamer0.8-mad" package, and this is where my real problem starts.
 I cant find this package:/ I can only seem to find "gstreamer0.8-tools";which i cant even install...
I have been googling and looking through forums but havent really found any answer, atleast any that i could understand:P
So it would be awesome if someone could lend me a  hand on how to solve this problem? :)

---

### Post by phillw on 2009-12-03
> **fr3w said:**
> Hello!
I am kinda new to the linux OP's. I've got it running like i want it to 90%, one thing i miss i the music. Currently im tryin to use the Amarok audio-player, but it wont play my mp3 files. 
I found a few answers when i googled for a solution, the mmost common one i found was to install the "gstreamer0.8-mad" package, and this is where my real problem starts.
 I cant find this package:/ I can only seem to find "gstreamer0.8-tools";which i cant even install...
I have been googling and looking through forums but havent really found any answer, atleast any that i could understand:P
So it would be awesome if someone could lend me a  hand on how to solve this problem? :)

Hi and welcome - I had a 'play' with amarok earlier tonight - it was not happy - wouldn't load my mp3 music files etc.
So, I went and got Audacious2 -- works like a dream :-)
Applications --> Ubuntu Software Center --> Sound & Video
(I have a low threshold of 'sod it - I'll go and get a programme that works' level for any packages that don't go get their dependencies when gotten via the likes of software center, or synaptics)
Phill.

---

### Post by presence1960 on 2009-12-03
> **fr3w said:**
> Hello!
I am kinda new to the linux OP's. I've got it running like i want it to 90%, one thing i miss i the music. Currently im tryin to use the Amarok audio-player, but it wont play my mp3 files. 
I found a few answers when i googled for a solution, the mmost common one i found was to install the "gstreamer0.8-mad" package, and this is where my real problem starts.
 I cant find this package:/ I can only seem to find "gstreamer0.8-tools";which i cant even install...
I have been googling and looking through forums but havent really found any answer, atleast any that i could understand:P
So it would be awesome if someone could lend me a  hand on how to solve this problem? :)

With the Medibuntu repositories enabled open a terminal and run:

```
sudo apt-get install w32codecs
```for 32 bit ubuntu

OR

```
sudo apt-get install w64codecs
```for 64 bit Ubuntu

This will allow playback of MP3, WMA, Real and Apple QuickTime Files in Ubuntu.

P.S. I always do this after an install:

Medibutu stands for Multimedia, Entertainment & Distractions In Ubuntu and is a repository of packages that cannot be included in Ubuntu due to legal reasons. We need to add this repository to enable MP3, DVD playback, install certain codecs etc.

Take a terminal and enter:

```
sudo wget http://www.medibuntu.org/sources.list.d/[COLOR="Red"]jaunty[/COLOR].list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

for the red "jaunty" above just substitute your ubuntu version for "jaunty".

Now we’ll enable all repositories (including Universe and Multiverse repositories) that Ubuntu provides. Take a terminal and enter:

    ```
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list && sudo apt-get update
```

2. Enable Playback of Encrypted DVDs 

Once the Medibuntu repository has been added as said above, take a terminal and enter:

    ```
sudo apt-get install libdvdcss2
```

3. Playing MP3, WMA, Real and Apple QuickTime Files in Ubuntu 

Once the Medibuntu repository has been added as said above, take a terminal and enter:

For a 32 bit machine:

    sudo apt-get install w32codecs

For a 64 bit machine:

    sudo apt-get install w64codecs

For a PPC machine:

    sudo apt-get install ppc-codecs

---

### Post by phillw on 2009-12-03
> **presence1960 said:**
> With the Medibuntu repositories enabled open a terminal and run:

```
sudo apt-get install w32codecs
```for 32 bit ubuntu

OR

```
sudo apt-get install w64codecs
```for 64 bit Ubuntu

This will allow playback of MP3, WMA, Real and Apple QuickTime Files in Ubuntu

Now, you'll have to remind even me, where do i do that from ?

Phill.

---

### Post by presence1960 on 2009-12-03
> **phillw said:**
> Now, you'll have to remind even me, where do i do that from ?

Phill.

see the P.S. I added to my original post

---

### Post by wojox on 2009-12-03
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

Should help as well.

---

### Post by phillw on 2009-12-03
> **presence1960 said:**
> see the P.S. I added to my original post

> sudo wget [http://www.medibuntu.org/sources.list.d/](http://www.medibuntu.org/sources.list.d/)[COLOR=Red]karmic[/COLOR].list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get updateAhhhh......  Now I recall why I hate adding repositries

> W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release Candidate i386 (20091020.3)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
> E: Some index files failed to download, they have been ignored, or old ones used instead.
I *think* I remember how to turn off my cd !!!

/edit NOW I deffinately remember why I hate messing with repositiries --- there goes my Update Manager :-(

Phill.

---

### Post by phillw on 2009-12-03
```

Failed to fetch http://download.bitdefender.com/repos/deb/dists/bitdefender/non-free/i18n/Translation-en_GB.bz2  
Failed to fetch http://download.bitdefender.com/repos/deb/dists/bitdefender/Release  
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

```

Any ideas ?

---

### Post by phillw on 2009-12-03
> **phillw said:**
> ```

Failed to fetch http://download.bitdefender.com/repos/deb/dists/bitdefender/non-free/i18n/Translation-en_GB.bz2  
Failed to fetch http://download.bitdefender.com/repos/deb/dists/bitdefender/Release  
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

```Any ideas ?


/edit never mind  [https://help.ubuntu.com/community/Repositories/Ubuntu#Removing%20&%20Disabling%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing%20&%20Disabling%20Repositories)

I think just downloading Audacious2 is the method i will advise. ;)

Phill.

---

### Post by Hath1 on 2009-12-03
I'm new to Ubuntu, but I was already a big fan of VLC Media Player from my Windows experience, and it's available right from the Ubuntu Software Center, so you might give that a try if you haven't already got it working with the other suggestions (or even if you have, as VLC is completely self-contained).

---

### Post by phillw on 2009-12-03
> **wojox said:**
> ```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```Should help as well.

Thanks - that one went smoothly :-)

Phill.

---

### Post by fr3w on 2009-12-04
Fist of all I'd like to thank you all for your help and suggestions :)
But unfortunately none of them worked for me :/
I'm able to play mp3 from just about all audio-players accept Amarok, so I'm starting to think this problem is directly related to Amarok?
And I also thought that perhaps it is a repository thing that is making me unable to find the "gstreamer0.8-mad" package?
Hopefully someone can clear all this up for me :P

---

### Post by fr3w on 2009-12-05
-bump-

---

