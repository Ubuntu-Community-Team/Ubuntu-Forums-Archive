---
title: "Hoping to install Ubuntu - what about Network Manager?"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Cap'n Refsmmat on 2006-06-01
Right, I've just downloaded the LiveCD and its installer goodness, but I need to clear a few things up before I actually install.

First, I noticed that Network Manager was not installed on it by default. However, I am on a WPA-encrypted network, so I need some way of installing it without Internet access, then using it to configure the network later. Is it possible to stick a .deb or two on a USB stick and install it from a newly installed Ubuntu copy?

Second, I need to know if GParted would resize my NTFS partition safely. I will back up my data beforehand, but I'd rather not have to worry about needing to restore it. Oh yes, and how many partitions and of what type should they be? I don't care about technical details between speeds of filesystems, I'd have no problem with ext3... but do I need a swap partition or anything?

Finally, I have a Dell Inspiron 600m laptop, and I just need to know one other thing: does Suspend work properly on it? When I brought up the logoff menu, Suspend wasn't even there. Is it just not possible on this laptop, or do I need to do some tweaking? (Boot times are fast on here, though, so I won't need it as much as Windows. But it's nice to just hit Hibernate and close the lid in a few seconds.)

---

### Post by jobezone on 2006-06-02
Hm.. Try this out. Boot the ubuntu lts CD in a ethernet connected computer(like cable or with an adsl router). Open up synaptic package, and search for "network-manager-gnome". Mark it for instalation (it will want to install some more). Now, under synaptic choose File->Create a script to download packages (or simillar wording). Chose a name and place it on the desktop. Right-click the script, and make it executable. Run it (double-click it), and it will fetch network-manager-gnome and all the packages it needs. Copy all the .deb packages to a usb key.
After you've installed ubuntu, open up synaptic again, and choose File->Install  downloaded packages (or simillar wording).

P.S.-you could also do most of this in the command line. For example, to install many .deb packages, open the terminal, **cd** to the directory containing them, and do:
```
sudo dpkg -i *.deb
```
I haven't tested this in the LiveCD, but hopefully it works. If it does, do this for all the packages you think you might need to have wifi.

GParted and resizing ntfs... I would advise you to backup, because no program is bugless.
Resize your ntfs partition, then you can let ubuntu use the remaining space and he'll create the necessary partitions (/, swap, and optionally /home), if my memory servers me right.

About your laptop suspending, I really don't know. It could be that the Live ubuntu doesn't suspend, but the installed one does. You could see the ubuntu wikipage [http://wiki.ubuntu.com](http://wiki.ubuntu.com), or [http://www.linux-laptop.net/](http://www.linux-laptop.net/) for your specific laptop model. 
You'll find people's experiences with it and linux.

---

### Post by Cap'n Refsmmat on 2006-06-02
[QUOTE=jobezone]Hm.. Try this out. Boot the ubuntu lts CD in a ethernet connected computer(like cable or with an adsl router). Open up synaptic package, and search for "network-manager-gnome". Mark it for instalation (it will want to install some more). Now, under synaptic choose File->Create a script to download packages (or simillar wording). Chose a name and place it on the desktop. Right-click the script, and make it executable. Run it (double-click it), and it will fetch network-manager-gnome and all the packages it needs. Copy all the .deb packages to a usb key.
After you've installed ubuntu, open up synaptic again, and choose File->Install  downloaded packages (or simillar wording).[/quote]
Would it be possible to download the .debs in Windows or something and then stick them on the disk?

(Though I suppose I can just take this laptop down to the router and plug it in... easy enough.)

> GParted and resizing ntfs... I would advise you to backup, because no program is bugless.
Resize your ntfs partition, then you can let ubuntu use the remaining space and he'll create the necessary partitions (/, swap, and optionally /home), if my memory servers me right.
So the installer handles making the partitions itself, and all I have to do is shrink the NTFS partition to let Ubuntu have room?

> About your laptop suspending, I really don't know. It could be that the Live ubuntu doesn't suspend, but the installed one does. You could see the ubuntu wikipage [http://wiki.ubuntu.com](http://wiki.ubuntu.com), or [http://www.linux-laptop.net/](http://www.linux-laptop.net/) for your specific laptop model. 
You'll find people's experiences with it and linux.
Thanks for the links!

---

### Post by jobezone on 2006-06-02
[QUOTE=Cap'n Refsmmat]Would it be possible to download the .debs in Windows or something and then stick them on the disk?

(Though I suppose I can just take this laptop down to the router and plug it in... easy enough.)
[/QUOTE]
Copy the script to the windows machine, then place a windows wget executable on the same directory (search on the net for wget + windows). Add a .bat extension to the script, run it, and it should work (haven't tried it myself).

> So the installer handles making the partitions itself, and all I have to do is shrink the NTFS partition to let Ubuntu have room?
Thanks for the links!
I've never used that myself, but I think it does. You also have the option to resize the ntfs partition in the installer. But backup! Really, I've read some posts here of people having problems with the resizing of ntfs partitions...

---

### Post by adamonduty on 2006-06-05
Suspend does work on a Dell 600m. I actually have been using it for a while, and it worked fairly well on Breezy (would not resume once every 5 - 10 times) and seems to be working on Dapper. One word of information, suspend/hibernation works much better on Dell BIOS' A16 and less. I have A17 and it has troubles sometimes, so if you haven't upgraded, you might want to wait. Maybe those problems have been fixed in Dapper, I don't know.

I've safely resized NTFS partitions without data loss several times. But definitely backup! 

And yes, you can use synaptic or install .debs on the live cd. I've never had trouble doing that.

---

### Post by adamonduty on 2006-06-05
Oh, the easy way to enable suspend support is to click on the battery applet in the gnome panel (assumming you're running on battery) and open preferences. Then change the action to suspend, and it will ask you if you want to enable suspend support.

---

### Post by Cap'n Refsmmat on 2006-06-05
Okay, thanks. I'll have to get around to installing Dapper and make a post on how it goes.

---

