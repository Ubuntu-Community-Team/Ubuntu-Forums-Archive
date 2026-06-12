---
title: "Ubuntu 10.04 Update?"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TheNerdAL on 2010-03-20
I was just wondering if I will be able to update to Ubuntu 10.04 with Update  Manager. I did that when I updated from 9.04 to 9.10. Thanks! :D I also would love to test out the beta, although I don't have no blank Cd's or a free USB flash drive. :/

---

### Post by 3rdalbum on 2010-03-20
Yes, you can update right now:

```
update-manager -d
```

But it might be safer to wait until things have settled down after the release (at which point, you can just run update-manager normally and it will give you the option to go to Lucid).

Buy some blank CDs and help test Lucid. We need all the testers we can get - I've been testing, but have barely reported any bugs because there are so few that I've seen!

---

### Post by linden940 on 2010-03-20
> **3rdalbum said:**
> Yes, you can update right now:

```
update-manager -d
```

But it might be safer to wait until things have settled down after the release (at which point, you can just run update-manager normally and it will give you the option to go to Lucid).

Buy some blank CDs and help test Lucid. We need all the testers we can get - I've been testing, but have barely reported any bugs because there are so few that I've seen!


I need to get another computer to run full testing...not so good to do it on vbox...but yea from what i hear Lucid is very clean...

---

### Post by TheNerdAL on 2010-03-21
> **3rdalbum said:**
> Yes, you can update right now:

```
update-manager -d
```

But it might be safer to wait until things have settled down after the release (at which point, you can just run update-manager normally and it will give you the option to go to Lucid).

Buy some blank CDs and help test Lucid. We need all the testers we can get - I've been testing, but have barely reported any bugs because there are so few that I've seen!

Yeah, you are totally right. It said my computer might not be able to start again and I had to do a fresh install. Luckily I wanted that because my old Ubuntu 9.10 was messed up because I think I messed with the terminal. lol

---

### Post by Sef on 2010-03-21
Moved to Lucid.

---

### Post by TheNerdAL on 2010-03-21
> **Sef said:**
> Moved to Lucid.

How is it? I want to upgrade but It's the first beta which means it has bugs.

---

### Post by Zayfox on 2010-03-21
> **TheNerdAL said:**
> How is it? I want to upgrade but It's the first beta which means it has bugs.
Hahaha Sef means the topic was moved to the Lucid section.

---

### Post by Mercury_Alpha on 2010-03-21
Have you used VirtualBox before? It will boot an ISO that's located on your hard drive.

---

### Post by Neo23x0 on 2010-03-21
My Upgrade in VBox fails. 
I started the upgrade with 

```
update-manager -d
```

After the upgrade I did a restart and the startup completely fails to initialize the graphic card. It switches from black to khaki and black and khaki.
After a while it shows the graphic card error screen.

It also tried a 
```
dpkg-reconfigure xserver-xorg
```  
but this does nothing at least shows nothing in the console. 
I also installed the vbox utilities again after upgrade. 

[IMG]http://home.arcor.de/mapache14/u1.png[/IMG]
[IMG]http://home.arcor.de/mapache14/u2.png[/IMG]
[IMG]http://home.arcor.de/mapache14/u3.png[/IMG]
[IMG]http://home.arcor.de/mapache14/u4.png[/IMG]
[IMG]http://home.arcor.de/mapache14/u5.png[/IMG]
[IMG]http://home.arcor.de/mapache14/u6.png[/IMG]

---

### Post by Mercury_Alpha on 2010-03-21
> **Neo23x0 said:**
> My Upgrade in VBox fails. 
I started the upgrade with 

```
update-manager -d
```

After the upgrade I did a restart and the startup completely fails to initialize the graphic card. It switches from black to khaki and black and khaki.
After a while it shows the graphic card error screen.

It also tried a 
```
dpkg-reconfigure xserver-xorg
```  
but this does nothing at least shows nothing in the console. 
I also installed the vbox utilities again after upgrade.


That appears to be a new glitch with Guest Additions. Select "Run Ubuntu in low graphics mode," then try [the fix on this page](http://maxolasersquad.blogspot.com/2010/03/ubuntu-1004-lucid-lynx-alpha-in.html).

When you are done editing that file, it should look like this:

[img]http://ubuntuforums.org/attachment.php?attachmentid=150918&stc=1&d=1269208022[/img]

After you have finished with the instructions in that link, restart Lucid in VirtualBox, and you should be able to get to your desktop without trouble.

I recommend creating a new discussion thread, if that doesn't work for you.

---

### Post by mattisking on 2010-03-22
I really appreciate everyone's help in this. I just got Lucid running properly under VMLite Workstation (based on Virtualbox 3.1.2 - ose) using these instructions (with the 3.1.4 additions).

---

