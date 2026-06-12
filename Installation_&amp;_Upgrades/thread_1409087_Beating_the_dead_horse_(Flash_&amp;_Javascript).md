---
title: "Beating the dead horse (Flash &amp; Javascript)"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by 1337sauce on 2010-02-17
Ok so I've been searching these forums for about 2 hours now, trying nearly everything I've come across to make these two things work... all I want to do is watch some damn youtube videos and maybe some videos off break.com. 
Someone please.. in n00b terms.... help me figure out how to make these two things work.. I am using Xubuntu 9.10 i386

Keep in mind i've been using Xubuntu for a total of 2 days.

---

### Post by zvacet on 2010-02-17
System>admin>software sources>check all under ubuntut software and first two under updates tab.Reload.Go to the applicastions>software center and find and install **xubuntu restricted extras**.

---

### Post by 1337sauce on 2010-02-17
when i did the first thing you said to do I got this when trying to reload

Failed to fetch cdrom://Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.3)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.3)/dists/karmic/multiverse/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.3)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.3)/dists/karmic/universe/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

And I see no Software Center... I remember that in ubuntu but Im not seeing it here in Xubuntu

---

### Post by octaedro7 on 2010-02-17
You are getting those fetch errors because either you haven't enable the proper sources in the **Ubuntu Software **tab of **Software Sources** or you are not connected to the internet, hence the software sources cannot be updated.
Go to the System submenu in the Xubuntu startmenu, look for Software Sources. Check the first 4 checkboxes under **Downloadable from Internet** (Main, Universe, Restricted and Multiverse) click Close (of course check that you do have internet connection) then  it will tell you that it needs to reload the sources and after that you're done. 
In the very same System submenu open up Synaptic and search for Xubuntu restricted extras, mark it for installation, apply and voila.
Other way is to go through Add/Remove Applications, selecting *All*/*All available applications*, just type java or flash and mark for installation the corresponding packages.

Is that simple. You better use the first method as it will install all codecs needed for multimedia.

---

### Post by zvacet on 2010-02-18
In system>admin>software sources uncheck CD rom as  repository.Reload.In terminal type

```
sudo apt-get install xubuntu-restricted-extras
```

you will be asked for your password so type it (you will not see anything but that is normal).

---

