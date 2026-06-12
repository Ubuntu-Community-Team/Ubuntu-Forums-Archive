---
title: "Can't upgrad from ubuntu 10.10 to 11.04"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by jibon_24 on 2011-09-07
Hello everyone,

I am using ubuntu 10.10 in my laptop acer-4736z . Now i am trying to upgrade my system to ubuntu 11.04. For that I download iso file from ubuntu archive. But during installation I don't see any upgrade option:(. Anyone can help me.:([IMG]http://www.shrani.si/f/A/2e/ha0D7by/screenshot.png[/IMG]

---

### Post by jtmcc on 2011-09-07
You don't need the iso,in 10.10, go to system-administration-update manager. Somewhere at the top you will see "Update to 11.04".

---

### Post by jibon_24 on 2011-09-08
> **jtmcc said:**
> You don't need the iso,in 10.10, go to system-administration-update manager. Somewhere at the top you will see "Update to 11.04".

:pI know that. But internet connection is very slow in my location. For that I collected that iso from my friend. But during installation I am facing this problem. Please help meeeeeeeeeeeeeeee.:)

---

### Post by dbdexter on 2011-09-08
well, if you want to upgrade without erasing anything, I think the only thing you can do is to upgrade directly from ubuntu 10.10 that you have installed. If you just need to keep your documents, download Back In Time and do a backup with it. I suppose there's no way to save your downloaded applications. sorry:frown::frown:

---

### Post by jibon_24 on 2011-09-08
Thanks for reply. But I don't get an upgrade option from live cd.

---

### Post by mörgæs on 2011-09-08
Before going that far: 

Have you tested 11.04 thoroughly using the live CD? That is, are you sure that it works well on your computer?

---

### Post by jibon_24 on 2011-09-08
> **mörgæs said:**
> Before going that far: 

Have you tested 11.04 thoroughly using the live CD? That is, are you sure that it works well on your computer?

Yes it's worked nice.:D

---

### Post by mörgæs on 2011-09-09
Then I would suggest that you bring the computer to a place with wired (and fast) internet access and do a clean install from the CD. 

Upgrading in general is risky, and there is not much point in upgrading from the CD, because you have to download a lot of bugfixes anyway, which are not on the CD (as it was released in april).

---

### Post by jibon_24 on 2011-09-09
Oh it's too complicated for me :(. By the by what about ubuntu DVD. Is there all important software is included ??  Can someone give some hints of the software ?

---

### Post by mörgæs on 2011-09-09
It is far from complicated. You just answer some easy questions, as you go along. Here is an overview:

[http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/](http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/)

The process begins from step # 3.


The DVD and the CD contains the same release. No matter what you do, you need to let Ubuntu apply bug fixes (just approve, and then the process is automatic).

---

### Post by westie457 on 2011-09-09
Boot into your normal system put the cd in the drive. Autorun should give you the option to upgrade from the cd.

---

### Post by jibon_24 on 2011-09-09
> **mörgæs said:**
> It is far from complicated. You just answer some easy questions, as you go along. Here is an overview:

[http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/](http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/)

The process begins from step # 3.


The DVD and the CD contains the same release. No matter what you do, you need to let Ubuntu apply bug fixes (just approve, and then the process is automatic). 


Thanks for reply. I have follow the instruction but in step # 4 I can't see any upgrade option:confused:. It's look like the above screen shot. It seem to me that I have to erase 10.10 ,if I want to use 11.04. But I really don't want this>>>>>>>:(

---

### Post by westie457 on 2011-09-10
> **jibon_24 said:**
> Thanks for reply. I have follow the instruction but in step # 4 I can't see any upgrade option:confused:. It's look like the above screen shot. It seem to me that I have to erase 10.10 ,if I want to use 11.04. But I really don't want this>>>>>>>:(

Do you want to do this the easy way or the hard way?

The easy way is in my first reply in the thread.

Now to expand on this. When the CD is detected by a running system autorun opens a window which says something like 'A Medium has been detected with software on it. Do you want to install?' Yes or No.

Yes will start the upgrade process taking the necessary files from the CD. Any further Updates can be applied after the upgrade. If the CD is less than a week old there will be very few as the ISO will be up to date.

The hard way is to do again what you started and when you get to the install screen (as in your screenshot) select the option 'Something Else' and in the next screen you will see all your partitions. Choose the one that matches your current system. A new window opens.

In this window the first box with numbers in it is the size of the partition. DO NOT CHANGE ANYTHING in this box. Underneath this is another box saying 'Do not use'. Click on this a menu opens with several options. Select the option that matches the file-system you already have (EXT3 for example). The small box under this marked 'Format'. LEAVE THIS BLANK.
The next box should have 'Use As'. Click this, select '/'

Under this window should be the option of where to install Grub. You should be okay going with the defaults you are given. Click 'Okay/Forward/Continue'. The Upgrade will go ahead and should keep your personal files intact. Also it should keep your installed programs and apps unless they are no longer used in the newer version.

Hope this is helpful to you and Good Luck.

---

### Post by jibon_24 on 2011-09-10
thanks a lot @ [westie457]("http://ubuntuforums.org/member.php?u=970779")

You steps worked fine.:p But I have lost most of my software. Ok now one question can I reinstall the previous software that I used in ubuntu 11.10. I have made a backup file before. It's about 2GB. How I could restore it should I use dpkg. If it then what will be code.
[PHP]    sudo dpkg -EG -i *.deb.   [/PHP]

Please help me):P.

---

### Post by westie457 on 2011-09-10
> **jibon_24 said:**
> thanks a lot @ [westie457]("http://ubuntuforums.org/member.php?u=970779")

You steps worked fine.:p But I have lost most of my software. Ok now one question can I reinstall the previous software that I used in ubuntu 11.10. I have made a backup file before. It's about 2GB. How I could restore it should I use dpkg. If it then what will be code.
[PHP]    sudo dpkg -EG -i *.deb.   [/PHP]

Please help me):P.

To be honest I have no idea about restoring from a backup because personally I don't have one. The only things I keep are personal files and they are stored as is on a separate partition.

If you can remember which programs you had installed probably the quickest way for you to reinstall them would be through Synaptic Package Manager. In the main pane of Synaptic type the first letters of a package. click on each to install, Synaptic will suggest the dependencies for you, accept these and when you are ready click Apply.

As I do not use a backup and do not know how you created yours this thread here might be of some use to you. [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by jibon_24 on 2011-09-10
Thanks again for reply. But your given link isn't usable for me because all of my files are .deb format. My question is can I use them in my new version 11.04 ?

I know about Synaptic Package Manager issue but I have already told that I have a limitation to use internet. Any idea.>>>>>>>>>

---

### Post by westie457 on 2011-09-10
Did you use 'gdebi' to make your backup?

If so reinstall that and point it at your backup media to move things to their new home.

I really am guessing at this for the reasons stated previously

---

### Post by jibon_24 on 2011-09-10
> **westie457 said:**
> Did you use 'gdebi' to make your backup?

If so reinstall that and point it at your backup media to move things to their new home.

I really am guessing at this for the reasons stated previously

Thanks  again for reply. No I am not using 'gdebi'. I just copy all the file  from /var/cache/apt/archives & stored it into my local folder. 

I think it is not possible to install them all. But if there is any way to use at least some file
 it will be very helpful for me.

Oh another problem my laptop light become off when I start ubuntu. I solved this problem by using this code: 
[PHP]
sudo setpci -s 00:03.0 F4.B=00
[/PHP]

But  now problem is when the laptop go to sleep mood I need to enter it  again into terminal. Sometime it become impossible because of no light.  Can any one help me to fixed it ? I want make a corn job so that  I will  be able to run this line for every 2 minutes. Have any idea ??:wink:
Thanks you all.

---

