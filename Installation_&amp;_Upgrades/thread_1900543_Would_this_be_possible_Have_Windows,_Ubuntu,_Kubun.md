---
title: "Would this be possible? Have Windows, Ubuntu, Kubuntu"
date: 2011-12-26
forum: Installation &amp; Upgrades
---

### Post by balkrish999 on 2011-12-26
Hello, I currently have Windows Vista, on a Partition, Windows 7 on another Partition and Ubuntu on another Partition ( Ubuntu is set up through Using WUbi )

My Question is that is it possible to Use Wubi and install Kubuntu?  so that i can have 4 OS's ? Is This Possible?

Thank You

---

### Post by MAFoElffen on 2011-12-26
> **balkrish999 said:**
> Hello, I currently have Windows Vista, on a Partition, Windows 7 on another Partition and Ubuntu on another Partition ( Ubuntu is set up through Using WUbi )

My Question is that is it possible to Use Wubi and install Kubuntu?  so that i can have 4 OS's ? Is This Possible?

Thank You
Kubuntu has a Wubi installer, but...

How about 2 flavors of Windows (you already have installed) and Ubuntu with different desktops? 

Linux is modular and has layers. You already have the Ubuntu base system installed with ubuntu-desktop installed. (most likely Unity and possibly Gnome 3.)

The other variants are all on the same base.  So to install a Kubuntu, Xubuntu or Lubuntu desktop in Ubuntu (respective commands):
```

sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install lubuntu-desktop

```Then to change from one desktop to another... at the login screen (11.10), click on the white Ubuntu Icon and it will drop down a menu to select the Desktop Environment.

Advantage of doing it this way? Less space than separate installs / One system to keep updated. Data and such is in one spot / easy to keep track of.  I test this with the Dev Builds and it works well for me.

Install what you want.  Good Luck.

---

### Post by GhostOfTomJoad on 2011-12-26
> **MAFoElffen said:**
> Kubuntu has a Wubi installer, but...

How about 2 flavors of Windows (you already have installed) and Ubuntu with different desktops? 

Linux is modular and has layers. You already have the Ubuntu base system installed with ubuntu-desktop installed. (most likely Unity and possibly Gnome 3.)

The other variants are all on the same base.  So to install a Kubuntu, Xubuntu or Lubuntu desktop in Ubuntu (respective commands):
```

sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install lubuntu-desktop

```Then to change from O'neill desktop to another... at the login screen (11.10), click on the white Ubuntu Icon and it will drop down a menu to select the Desktop Environment.

Advantage of doing it this way? Less space than separate installs / One system to keep updated. Data and such is in one spot / easy to keep track of.  I test this with the Dev Builds and it works well for me.

Install what you want.  Good Luck.

I actually have a followup question about different desktops. If it needs to be a new thread, I shall make one.

I ran the terminal installation for kubuntu and xubuntu. I like them both for different tasks but I want the standard ubuntu splash screen and loading screen back. I know it's aesthetic but, I prefer it.

I currently have the xubuntu loading screen and the kubuntu login splash. Also, I tried unity --replace, as was suggested in another thread but that fails on all fronts and basically just hangs the terminal after a while.

---

### Post by fantab on 2011-12-27
Why don't you try Multi-boot UBUNTU? It is a far better option than WUBI installs. Also you can have KUBUNTU as separate OS
And you will not only have independent OS files assigned to their own partitions you can also have your aesthetics.

---

### Post by balkrish999 on 2011-12-27
I dont want to install it as a seperate OS as i am a novice, and it will be very long 

- Cant i simply install, Kubuntu using Wubi?  through my Windows 7?

---

### Post by Elfy on 2011-12-27
As far as I am aware trying to install more than one wubi leads to is asking to uninstall the existing one, the wubi wiki says to do exactly the same as MAFoElffen suggests.

Not quite sure why you think it will be longer to install kubuntu inside the wubi installer than trying to install it seperately.

It might well be that you won't have room to do so anyway - running df -h from a terminal will give you more information about that.

Wubi is not intended to be a long term install anyway - not that people don't use it as such. 

Unless wubi has changed since the last time then I found it to be painfully slow installing that way anyway :)

---

### Post by balkrish999 on 2011-12-27
> **forestpiskie said:**
> As far as I am aware trying to install more than one wubi leads to is asking to uninstall the existing one, the wubi wiki says to do exactly the same as MAFoElffen suggests.

Not quite sure why you think it will be longer to install kubuntu inside the wubi installer than trying to install it seperately.

It might well be that you won't have room to do so anyway - running df -h from a terminal will give you more information about that.

Wubi is not intended to be a long term install anyway - not that people don't use it as such. 

Unless wubi has changed since the last time then I found it to be painfully slow installing that way anyway :)



No, I know that it says when you want to install kubuntu it says uninstall ubuntu first 

However 

i have installed , Ubuntu using wubi on windows Vista

Would it be possible to Go On Windows 7 - Then install Wubi Kubuntu from there?

---

### Post by Elfy on 2011-12-27
Yes.

---

### Post by balkrish999 on 2011-12-27
> **forestpiskie said:**
> Yes.

OK Thank You
, 

Shall i change the Wubi bootloader name - to Ubuntu 1 

just to be on the safe side? 

so if i install kunbtu there is a less chance of failure

---

### Post by Elfy on 2011-12-27
Sorry - I've no idea. 

Not sure how it will pan out - wubi in vista is going to be completely seperate to wubi in win7. 

It's probable that you'll have some fun trying to get them both showing in whichever bootloader you have.

---

### Post by balkrish999 on 2011-12-27
> **forestpiskie said:**
> Sorry - I've no idea. 

Not sure how it will pan out - wubi in vista is going to be completely seperate to wubi in win7. 

It's probable that you'll have some fun trying to get them both showing in whichever bootloader you have.

OK Thanks for all your help! :)

---

### Post by balkrish999 on 2011-12-27
Yes I Have Successfully have a Quadrupole Boot. Windows 7, Vista , Ubuntu and Kubuntu :)
If anyone else would like to do this or for Future infomation 
I Already have Ubuntu installed using Wubi on a Partion - i used Easy BCD to change the boot name to something else 
I then went on Windows 7 and Installed Wubi/Kubuntu from there on a different partion :) and it works 
Thank You :)

[SIZE=3]Edit: This does not work :( so DO NOT TRY [/SIZE]

---

### Post by balkrish999 on 2011-12-27
Sadly - the Quadruple boot does not work - and i dont think it will :(  Anyone else - Please DO NOT TRY THAT !

I get a error when booting Kubuntu saying a partion is already installed and it needs to be uninstalled - Please try Again

---

### Post by bcbc on 2011-12-28
Wubi boots by locating a file: /ubuntu/disks/root.disk

It looks in all partitions until it finds it. So... installing it on different partitions won't matter: the first one it finds, it boots.

There are various ways to 'save' a Wubi install while trying others, and you can also manually boot different Wubi installs, but none of it is that straightforward.

---

### Post by kurt18947 on 2011-12-28
> **balkrish999 said:**
> Sadly - the Quadruple boot does not work - and i dont think it will :(  Anyone else - Please DO NOT TRY THAT !

I get a error when booting Kubuntu saying a partion is already installed and it needs to be uninstalled - Please try Again

I don't know if you're trying to do what I'm going.  I have multiple operating systems installed.  I used a boot manager, bootitbm from Terabyteunlimited.  Google will find it.  If I want to, I can install Ubuntu, Kubuntu, Xubuntu, different Fedora installs, Arch, Windows etc. etc. each in its own partition up to the capacity of the hard drive(s).  There is no 4 primary partitions limitation, you can have over 100 primary partitions spread over multiple disks. Each O.S. partition 'thinks' it's the only operating system on the machine.  If that's what you're trying to do, Bootitbm is one option, there are others.  

If multiple partitions, each with its own O.S. isn't what you have in mind, how about Virtualbox or Vmware?  I just installed Win7 on an Ubuntu 11.10 host as an experiment.  It was surprisingly easy and not all that demanding of hardware.  Having both OSs running, each with a Firefox browser window open required about 1 gig of RAM. A boot manager will run one O.S. at a time, I guess the number of VMs running simultaneously is limited only by available RAM.

---

