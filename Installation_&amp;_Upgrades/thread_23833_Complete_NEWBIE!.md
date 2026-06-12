---
title: "Complete NEWBIE!"
date: 2005-04-04
forum: Installation &amp; Upgrades
---

### Post by Beebe on 2005-04-04
Hi

I installed Ubuntu over the weekend - being a complete and utter newbie to Linux, tho having a good general overall knowkledge or windows and PC's in gerenal.

MAN IS IT DIFFERENT!!

My first hurdle was installing aMSN - which i eventually untarred to a folder in home.

My question now is this: how do i add aMSN to the program menu - so that I don't have to goto the file broswer and manually run the launch script everytime?

Any other tips and advice wud also be welcome. What software would I find usefull to download? I use it to surf the net generally. 

Are all programs tricky to install using consoles or do most come with an windows stylie installation program?

Thanks

Paul

---

### Post by kuleali on 2005-04-04
For "most" programms you can use the apt-get install command and type the programm name. For instance check out the [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by lao_V on 2005-04-04
Say goodbye to the "windows style installation program" (for the moment anyway) and say hello to apt-get install!! 

You can have most of the software with one single command!!!

Adding it to the menu is slightly cumbersome with GNOME at the moment and you might have to manually create entries for some apps. With KDE, you can run kappfinder which will find all the apps on your system and add to the menu.

---

### Post by Beebe on 2005-04-04
[QUOTE=lao_V]Say goodbye to the "windows style installation program" (for the moment anyway) and say hello to apt-get install!! 

You can have most of the software with one single command!!!

Adding it to the menu is slightly cumbersome with GNOME at the moment and you might have to manually create entries for some apps. With KDE, you can run kappfinder which will find all the apps on your system and add to the menu.[/QUOTE]
 So using the guide I see i just activate the apt-get by un-commenting the servers.

Then i can just type apt-get aMSN for example?

---

### Post by Gandalf on 2005-04-04
[QUOTE=Beebe]So using the guide I see i just activate the apt-get by un-commenting the servers.

Then i can just type apt-get aMSN for example?[/QUOTE]
 exaclty, you uncomment the server, and
```

sudo apt-get update
sudo apt-get install amsn

```

and your msn will be in your Application -> Internet gnome menu

---

### Post by lao_V on 2005-04-04
[QUOTE=Beebe]So using the guide I see i just activate the apt-get by un-commenting the servers.

Then i can just type apt-get aMSN for example?[/QUOTE]

By uncommenting you don't activate apt-get but you enable the extra repositories. For a guide on repositories please see [here]("http://www.ubuntulinux.org/ubuntu/components/document_view")

---

### Post by Klimax on 2005-04-04
I only have a little thing to add:

I use menueditor to edit my GNOME menus, and even though it is really buggy, it is really useful for customization. Just apt-get install menueditor

---

### Post by jameswilhelm on 2005-04-04
Good to hear you aren't afraid to try. It will be useful to others if you get a chance to write up your experiences compared to using Windows - good and bad both ways. There are too many one-sided opinions and 'lets-bash-them' articles on both sides of the fence!

You could try GAIM as well. I've successfully used it for MSN, Yahoo Messenger and AIM - mainly on AIM. Can't say how it compares in functionality with aMSN.

Ubuntu is great and I plan to upgrade from Redhat9 in the next month or so. Let us know how you find it.

---

### Post by Beebe on 2005-04-04
[QUOTE=jameswilhelm]Good to hear you aren't afraid to try. It will be useful to others if you get a chance to write up your experiences compared to using Windows - good and bad both ways. There are too many one-sided opinions and 'lets-bash-them' articles on both sides of the fence!

You could try GAIM as well. I've successfully used it for MSN, Yahoo Messenger and AIM - mainly on AIM. Can't say how it compares in functionality with aMSN.

Ubuntu is great and I plan to upgrade from Redhat9 in the next month or so. Let us know how you find it.[/QUOTE]

Wow thanks for all the advice!! I sure will give it a few days and let you know how I get on!

---

