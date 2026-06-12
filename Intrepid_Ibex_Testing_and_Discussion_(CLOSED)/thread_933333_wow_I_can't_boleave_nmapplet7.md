---
title: "wow I can't boleave nmapplet7"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by subixonfire on 2008-09-29
Before some time i needed internet access in my grandmother's house on my old p2 1000mhz that to has dual boot! I em there for like 2 days in a month so i asked my frend that leaves across the street if i can connect using wlan to his adsl! Here starts the trouble, another fellow using wlan on the seame street, has seame ssid & seame channel! my frend didn't let me change his! so conecting was a real nightmare becouse the other network was sometimes stronger! 
- Windows xp failed & showed only one network!
- Ubuntu 8.4 the seame thing
- other live linux distros sometime showed bout of them but again had problems with connecting!


But now intrepid ibex alfa6 introduced me with nm7 & its showing me bout networks. I can ewen connect to bout of them widouth any problems!

I'l post a screenshot of kismet running on back track 3 to show the problem with gimp integrated screenshot of nm7 showing bouth networks!

[IMG]http://img100.imageshack.us/img100/7553/wownm7fx6.png[/IMG]

---

### Post by blakamin on 2008-10-01
I cant believe that people still do that! Who owns the un-encrypted one?
I'd be tempted to login and just change the ssid of it!
That would be a bit cheeky tho. Just mention to your friend the dangers of standard ssids and ask if he has even changed the default admin password. Might give him a wake-up to the stupidity.


Now, If only Network Manager remembered *my* WPA key every time I turned my laptop on...

---

### Post by plun on 2008-10-01
> **blakamin said:**
> I cant believe that people still do that! Who owns the un-encrypted one?
I'd be tempted to login and just change the ssid of it!
That would be a bit cheeky tho. Just mention to your friend the dangers of standard ssids and ask if he has even changed the default admin password. Might give him a wake-up to the stupidity.



Well this a world-wide challenge.....8)

Took a picture during a NM 0.7 test  

[http://pix.nofrag.com/b/6/f/be25546509417f30aac237c6966fd.html](http://pix.nofrag.com/b/6/f/be25546509417f30aac237c6966fd.html)


Users are more afraid of spying authority's then this challenge.:rolleyes:


And... mostly all workgroups are named "MSHOME"....:twisted:


Please check for bugs...!

---

### Post by alphacrucis2 on 2008-10-01
> **plun said:**
> Well this a world-wide challenge.....8)

Took a picture during a NM 0.7 test  

[http://pix.nofrag.com/b/6/f/be25546509417f30aac237c6966fd.html](http://pix.nofrag.com/b/6/f/be25546509417f30aac237c6966fd.html)


Users are more afraid of spying authority's then this challenge.:rolleyes:


And... mostly all workgroups are named "MSHOME"....:twisted:


Please check for bugs...!

A neighbour around here has the same brand of wireless access point as me but running completely open. It astonishes me that people install these things without using at least WPA encryption.

---

### Post by plun on 2008-10-01
> **alphacrucis2 said:**
> A neighbour around here has the same brand of wireless access point as me but running completely open. It astonishes me that people install these things without using at least WPA encryption.

Yes and this must be resolved...

Everyone within the cracking community also knows about [Aircrack]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=aircrack")

Strange app for forcing crypted networks but this is the case.


So its really important for everyone with bugs to file new ones or
add good comments... (not "+1"  :D)

This is the place for NM 0.7

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bugs](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bugs)

---

### Post by ronacc on 2008-10-01
> **alphacrucis2 said:**
> A neighbour around here has the same brand of wireless access point as me but running completely open. It astonishes me that people install these things without using at least WPA encryption.

not everyones wireless network extends into public areas and many of those that do wasted their money buying a router with way more range than they needed .

---

### Post by macroshaft on 2008-10-01
It's easy to criticize these people but I bet a lot of them had a hard enough time figuring out how to plug the router in! I see people every day who are set up like this and it's purely because the don't understand what they are doing!

I have friends who I'm still trying to teach the difference between the router password and the WPA key, the idea of it having 2 passwords just seems to confuse them.

It's hard to get everything right when you don't understand why you are doing it, if they can turn it on and read their email then to them it's working properly!!

---

### Post by ronacc on 2008-10-01
> **macroshaft said:**
> if they can turn it on and read their email then to them it's working properly!!
if they can turn it on and read their email it IS working properly. The person accessing the network without authorization is the one acting IMPROPERLY . Securing your network and the method to use is a choice , the problem is as you note one of education .

---

### Post by plun on 2008-10-01
> **ronacc said:**
> if they can turn it on and read their email it IS working properly. The person accessing the network without authorization is the one acting IMPROPERLY . Securing your network and the method to use is a choice , the problem is as you note one of education .

The Ubuntu community can be smart and learn users about this.

NM 0.7 shows users a lot.  :D


And such bug as this IS "**critical**"....  IMHO

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/36651](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/36651)


Also to use MSHOME as workgroup for a samba share...but its another "mess".

---

### Post by volanin on 2008-10-01
> **plun said:**
> And... mostly all workgroups are named "MSHOME"....:twisted:

Ok... naive question comming!
I completely understand the problems involved with default SSIDs and,
even worse, default factory router passwords. But what's the problem
in leaving the workgroup name as the default MSHOME?
:confused:

---

### Post by plun on 2008-10-01
> **volanin said:**
> Ok... naive question comming!
I completely understand the problems involved with default SSIDs and,
even worse, default factory router passwords. But what's the problem
in leaving the workgroup name as the default MSHOME?
:confused:

Because its the workgroup name for all "default" Windoooze PCs.

You have directly access to all shares if a owner doesn't crypt his
network or a little mistake with something.

So its smarter to change workgroup name for Samba shares and all PCs.

Now we also have a challenge with this mess..
[http://ubuntuforums.org/showthread.php?t=932208](http://ubuntuforums.org/showthread.php?t=932208) 
 
Edit smb.conf is not a good solution....

---

### Post by volanin on 2008-10-01
> **plun said:**
> Because its the workgroup name for all "default" Windoooze PCs.

You have directly access to all shares if a owner doesn't crypt his
network or a little mistake with something.

Ok.
But don't you have access to all shares independent of the workgroup name?
I mean, if I select PLACES > NETWORK, I see a list of all the workgroup
names in my network. Just enter a workgroup and access the share.
Am I missing something?

---

### Post by plun on 2008-10-01
> **volanin said:**
> Ok.
But don't you have access to all shares independent of the workgroup name?
I mean, if I select PLACES > NETWORK, I see a list of all the workgroup
names in my network. Just enter a workgroup and access the share.
Am I missing something?

A Windows PC must have correct workgroup or domain name otherwise
you don't have access to a network and shares.

Something is totally wrong with Nautilus Samba sharing from a GUI in Intrepid. I cannot connect to a Ubuntu share (client) from a Windows PC.
Ok to my Ubuntu server... (manual howto)

About this:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

> Windows XP Server

This section enables Windows XP as a samba file server.

Sharing a Folder

1. On the Windows server, browse in explorer ("My Computer") to the location of the folder you wish to share (C:\Documents and Settings for example). Next right click on the folder to share and select "Sharing and Security...". In the pop-up dialog box click the "Sharing" tab. Click the "Network Setup Wizard" to configure your network to allow shares. Work your way through the wizard. **Note the default workgroup is MSHOME. You may change this value if you like but all your computers should be in the same workgroup. Eventually you will be given the option to "Turn on file and printer sharing". This is the option you want, continue with the network wizard. **You will have to restart your computer for the settings to take effect -> Restart Windows.

2. After rebooting, again open explorer ("My Computer") and navigate to the folder you wish to share. Again right click on the folder and select "Sharing and Security...". In the pop-up dialog box click the "Sharing" tab. In the "Network sharing and security" box, tic (select with the mouse) the "Share this folder on the network" box. Give the folder a share name. This will give read only access to Ubuntu computers via samba. To allow read/write access tic (select with the mouse) the "Allow network users to change my files" box. Click the "Apply" button and close the dialog box. 



My workgroup name is "HEMMA"  and SSID  "hemma", "hemma" means "at home".. 

So I cannot see it so smart to use MSHOME as workgroup.... but maybe I am wrong.


I am also using WEP because I live in a area which I feels is safe from "lurkers"...:D

---

