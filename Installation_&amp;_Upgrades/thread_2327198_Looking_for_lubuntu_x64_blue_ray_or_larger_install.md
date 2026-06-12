---
title: "Looking for lubuntu x64 blue ray or larger install image"
date: 2016-06-08
forum: Installation &amp; Upgrades
---

### Post by a.dusty.trail on 2016-06-08
I'm looking for ubuntu or lubuntu(preferred) blue ray or larger install image.
Under 32 gigs but at least blue ray sized (20 gigs+ preferred but I will take larger if that's all there is)
64 bit
Preferably in jigdo download format.

Thank you for any info

(I have a butt load of off line installs to do and need as many popular files as possible to save the package hunting later)
Yes I know where the 2g and smaller images are, no I don't want them.please don't reply telling me where small boot images are

---

### Post by sudodus on 2016-06-09
Welcome to the Ubuntu Forums :-)


***Alternative 1***

I think you should create an [OEM install system](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview) and make it portable. Install the program packages you want into a 'master system' and {make it / keep it} portable by avoiding proprietary drivers. Then you can clone your system, for example with [Clonezilla](clonezilla.org), and install cloned copies to the other computers.

See the following links, if you want to take a short-cut to a system, that works in both UEFI and BIOS mode. You still need to install the program packages you want into your 'master system'.

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[Another new, simpler and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13468260#post13468260)


***Alternative 2***

Get the 64-bit iso file of [LXLE](http://www.lxle.net/), which is a community re-spin of Lubuntu. It contains many more program packages than the corresponding iso files of Lubuntu, but is still very far from the size you want. I may be wrong but I don't think that LXLE works in UEFI mode.

You might find other unofficial re-spins, that contain a lot of program packages.

---

### Post by a.dusty.trail on 2016-06-09
the hard ware is all different from computer to computer. in many different locations none with internet access. all with different installed application requirements. i have been using the Debian bluray jigdo image to install before but the group consensus is towards moving to LUbuntu 16.04.  that is assuming that i can get everything to install and update from a usb drive on a regular basis.
which was quite easy with Debian and the bluray install media.
LXLE is too old and once again lacking in files accessible offline.

im hoping this is possible with my limited Linux skills. and lack of internet at the install locations.

---

### Post by sudodus on 2016-06-09
Unfortunately I don't know of any corresponding Ubuntu or Lubuntu huge image.

Maybe you can make an own mirror with the relevant program packages, and bring it with you (in a laptop). I don't know how big it would be, or how difficult to make it.

I think you should try with an installed system. Linux is much more flexible than Windows, and quite different PC computers can boot from the same installed system from USB or SATA or eSATA.

Would it be possible to make an installed system with all the possible program packages installed? Then you could remove/purge the packages, that are not needed in each case and after that clean the system.

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

and do the final tweaking.

-o-

- What kind of applications are there?
- What kind of computers?
- What kind of end users?
- Which country or region is it and what infrastructure is available?

If you tell us about these things, maybe people with experience of similar tasks will see it and help you make this possible with Lubuntu :-)

Maybe they will tell you to stay with your old method and Debian ;-)

---

### Post by ubfan1 on 2016-06-09
+1 on the setting up your own mirror suggestion.  Google Ubuntu apt-mirror for many articles on this subject.  It's not even that difficult to just download everything yourself, but keeping it up to date would be made easier (I guess) using the apt-mirror approach.

---

### Post by oldfred on 2016-06-09
I have never tried this:
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by a.dusty.trail on 2016-06-10
> I think you should try with an installed system. Linux is much more  flexible than Windows, and quite different PC computers can boot from  the same installed system from USB or SATA or eSATA.

Would it be possible to make an installed system with all the possible  program packages installed? Then you could remove/purge the packages,  that are not needed in each case and after that clean the system.
as for what computers are involved  think of 75 friends who have home computers from the last 8 years..
the different hardware and software they have installed on their home systems. then think they all wanted to dual boot
into  one system with as much of their personal preferences for software  installed..( and they all have a list of their must have choices. ie  some have amiword over office, gnomepad over leafpad  etc)

it would be a night mare to get the graphic drivers and hardware drivers for all the different systems working properly..
while the applications, are a part of the issue the drivers are a larger part..and we all know how fun it is to track down drivers with out internet..
 its one of the reasons i was using the debian jigdo blueray install media..






> **oldfred said:**
> I have never tried this:
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

if im going to have mirror the entire Ubuntu repository to do this...
thats a little insane..

and its going to hammer the ubuntu servers to get 100+gigs just so i can have offline access to 10 or 12 gigs of software i need..

but hey.. i have access to a few very high speed internet connections  so i could just download everything every other week
and stick it on a portable drive...(it will have to be wiped from the downloading computer when im done)

just seems a little excessive ..... and a waste of ubuntu bandwith...

but then i would have no worrys about  not having offline access..

if i cant find a better way... ill have to appmirror  ubuntu every other week.

---

### Post by sudodus on 2016-06-10
So it is not an organisation or company, but private persons and their computers. Then I agree that there will be very different hardware as well as software, and not much room for compromises.

- I would say that a local mirror is an alternative, but in most cases I would say, that it is not necessary to renew it every other week, if the computers will not connect to the internet.

- It the friends or customers have slow and expensive connections to the internet, and need your mirror to update & dist-upgrade, then I think it is worth the effort. After a while you will probably find that refreshing the mirror will not need too much bandwidth.

---

### Post by a.dusty.trail on 2016-06-10
> **sudodus said:**
> So it is not an organisation or company, but private persons and their computers. Then I agree that there will be very different hardware as well as software, and not much room for compromises.

- I would say that a local mirror is an alternative, but in most cases I would say, that it is not necessary to renew it every other week, if the computers will not connect to the internet.

- It the friends or customers have slow and expensive connections to the internet, and need your mirror to update & dist-upgrade, then I think it is worth the effort. After a while you will probably find that refreshing the mirror will not need too much bandwidth.

sadly i cant keep that much data on the downloading computers for any length of time.
i will not know my route so cant leave the usb drive hooked up as storage.
so i will have to set it up to download the night before i go there(remotely).. then copy everything to a usb drive and
wipe it from the computer before i go..
so it will be a full download of everything. every time..
a lot of wasted bandwidth..

i will have to take a while and research how to build my own jigdo massive ubuntu install.. 
but in the mean time lots of downloading.

---

### Post by sudodus on 2016-06-10
That way does not look good. Would it be possible to get a new USB drive dedicated for this purpose?

I think the best alternative is to stay with your old method and Debian, at least until you find a better alternative than to re-create a mirror twice a month.

---

### Post by a.dusty.trail on 2016-06-10
> **sudodus said:**
> That way does not look good. Would it be possible to get a new USB drive dedicated for this purpose?

I think the best alternative is to stay with your old method and Debian, at least until you find a better alternative than to re-create a mirror twice a month.

there are about 10 access points where i can mirror the repository.
i can never tell which one i will be travelling to first when i start making my rounds to visit people and update the systems  while im there.
so i would have to have 11 usb disks. one each installed on all those computers, and have all of them keep their mirror up to date, so i can come by once in a while and swap out my current travelling usb drive for the updated one.

since the access points are all high speed and have virtually unlimited bandwidth to play with..
it would be far for cost effective on my end to just have one stick and download all the updates once a month minimum at those access points.

sadly it appears Ubuntu and the community has stopped developing methods of keeping Ubuntu updated in a off line state in any other way other than massive personal mirrors.

---

### Post by sudodus on 2016-06-10
What about bringing an external drive and connecting it at those access points when you arrive there? Updating the mirror should be possible overnight while you are sleeping (if you can sleep near the access-points).

---

### Post by a.dusty.trail on 2016-06-10
i dont stay at the access points overnight..
i can remotely connect to them and have them start a mirror
then copy it while i visit to a usb stick..
do the updates and changes to the computer as requested..
then delete it from the computer..
then move on to the next visit with the mirror ready to use.. when needed

rinse and repeat every time i need to updated 
and its better to have the updated files than not have them..
so at least once a month i would have to mirror every thing..
to be on the safe side.

---

