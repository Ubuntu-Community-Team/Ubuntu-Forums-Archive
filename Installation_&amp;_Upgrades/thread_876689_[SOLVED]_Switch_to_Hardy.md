---
title: "[SOLVED] Switch to Hardy"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by terrordrone on 2008-08-01
Hi,

i'm planning to switch to Hardy from Gutsy..
i tried openSuse11 and im a bit pissed off with it.
i miss the forum here...

coming back to the issue..
i'd like to ask a few questions..

1) i used the attached doc to configure my wireless ... will the same procedure work with Hardy as well ? i have a broadcomm wireless card on my laptop

2) wats the open office version by default in hardy ?

3) heard that there are issues with the network manager in hardy... any other app that'll help manage networks better.

---

### Post by Sef on 2008-08-01
> 2) wats the open office version by default in hardy ?

version 2.4

---

### Post by terrordrone on 2008-08-01
thanks
wat abt Q 1 and 3 ?

---

### Post by iaculallad on 2008-08-01
An advice: If you're happy with using Gutsy (with everything working flawlessly including your wireless and nothing breaks) , try not to upgrade to Hardy. You just have to download and install every available updates/patches for Gutsy.
But if you want to have fun, Insert your Hardy desktop CD, install it and experiment.

---

### Post by terrordrone on 2008-08-01
i have uninstalled gutsy now...

but the problem with gutsy is (atleast for me) .. the repositories do not have the latest version of applications..

1) open office is at 2.3
2) firefox is still in 2
...

also hardy is LTS.. 

this is why i need to shift to hardy...

---

### Post by iaculallad on 2008-08-01
To install OO v2.4.x in your Gutsy system:

-Open your Synaptics Package Manager and manually remove OO's previous version installed.

-Download the tarball file from this [link]("http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.1").

-Say you downloaded it in your Desktop, Open your terminal and change directory to your Desktop.

```
cd ~/Desktop
```

-Extract the tarball:

```
tar -vxzf OOo_2.4.1_LinuxIntel_install_en-US_deb.tar.gz
```

-Change directory to the extracted folder:

```
cd Extracted_Folder_Name/DEBS
```

-Install the file:

```
sudo dpkg -i *.deb
```

-Update your GNOME menu:

```
cd desktop-integration
sudo dpkg -i *.deb

```

---

### Post by terrordrone on 2008-08-01
like i said ive already formatted my drive and im on opensuse11 ..  and i'm finding it hard without as good a forum as this.. 

now.. should i go back to gutsy.. even when a newer version is out which has all the stuff built into the repos? i have a cd of hardy right in front of me.. 

my only issue is that of wireless configuration.. if anyone can confirm that the procedure in the doc works.. or give me a link to setup broadcomm wireless card for hardy.. ill be ever grateful

---

### Post by Kevbert on 2008-08-01
For wireless you could try [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13").  If that doesn't work (it will in many cases) the best post is [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560") using ndiswrapper.

---

### Post by terrordrone on 2008-08-01
thanks for the link...  the doc says something very similar thank you..

guess ill install hardy now

thanks a lot all of you

is there a better network manager than the regular one ?

---

### Post by terrordrone on 2008-08-01
Thank you all..

i'm on Hardy and it rocks :D

wireless is working as well... :guitar:

thanks again

---

