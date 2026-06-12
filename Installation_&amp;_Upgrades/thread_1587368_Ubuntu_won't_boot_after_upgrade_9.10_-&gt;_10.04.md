---
title: "Ubuntu won't boot after upgrade 9.10 -&gt; 10.04"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by Floris- on 2010-10-03
I installed Ubuntu like 3 days ago with a cd I got when I bought a magazine about Ubuntu. That cd contained Ubuntu 9.10. After a couple of hours I desided to instal 9.10. After using 9.10 for 1 day and installing some programs like java and flash player, I checked for updates and desided to update to 10.04. The installation seemed to go all smooth, but after I clicked on the 'reboot now' button, my laptop couldn't boot no more. A little purple screen with "Ubuntu" written on it popped up for like 5 seconds and then it dissapeared, and there I had a nice black screen. I waited 4 hours, but still nothing. Yesterday I installed 9.10 again, and now I still want to update to 10.04 or 10.10. But I can't seem to use a Usb flash drive with my Toshiba laptop, and I only have 1 cd left. My rabbit kinda destroyed the 10.04 cd and now I only have 1 cd left. Shall I burn 10.10 on a cd and check if that one will work properly, or is my laptop just to old and slow ( Centrino 1.6ghz, 512mb ram ) to run one of those versions?
I'm really new to ubuntu and my English sucks as well, because I come from Holland.
Thanks already for reading my boring story and for any help you can provide me with.

---

### Post by drs305 on 2010-10-03
Floris,

Welcome to Ubuntu and the Ubuntu forums!

You can download the Desktop version of 10.04 and try running it from your USB drive to see how/if it performs. Here is a link to the download page:
[http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")

Also, here is a page discussing the hardware requirements:
[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")
I see they have raised the minimum *recommended* RAM to 1GB although later 512 is mentioned.

---

### Post by Floris- on 2010-10-03
> **drs305 said:**
> Floris,

Welcome to Ubuntu and the Ubuntu forums!

You can download the Desktop version of 10.04 and try running it from your USB drive to see how/if it performs. Here is a link to the download page:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)


Thanks =) But my old Toshiba laptop won't boot anything from an usb drive. :(

---

### Post by SaintDanBert on 2010-10-03
Sometimes we forget that we know what we mean and why we say what we do. **Drs305** recommended that you boot and try the Lucid live-CD.
One goal for these live-media editions is to allow folks a go/no-go trial (sic) of a new edition. 
[list]
[*]Will it boot?
[*]Do I get a desktop?
[*]Can I connect to the net by wire? wireless?
[*]Can I use a browser?
[*]Can I watch web video?
[*]Can I connect and see thumb drive files?
[*]Can I play my music files (from thumb drive)?
[*]Can I connect my printer and use it?
[/list]
You mileage may vary, but these things represent the middle 80% in my opinion. If these tests work for you, then the distro edition should work on hardware used to test.

Ubuntu has features that support "automatic update" from edition-N to edition-N+1. (You **cannot** skip editions to catch up.) Many postings recommend a "fresh install" instead of this sort of update. It is usually a good time to move to a larger drive. Your existing system has gathered various skid marks that benefit from clean-up. It is also a good opportunity to clean out (delete?) files and folders you no longer need and get an archival copy of files and folders you really want to save. Therefore:
[list=1]
[*]install your new drive
[*]dance with win-doze if you must
[*]spin the Ubuntu CD or DVD media installer
[*]boot your new Ubuntu
[*]restore your application files from backup copies or (my favorite) connect your olde drive using USB and copy from there.
[/list]

Bonne chance,
~~~ 0;-Dan

---

### Post by ivanovnegro on 2010-10-03
In your case I would download the Ubuntu 10.04 Live CD and boot from it to the desktop and test everything what Dan mentioned and if you can boot to the desktop and everything works in the Live environment you can install Ubuntu to your hard disk and thats all.
Be sure to make all back ups needed of yor data.
About yor hardware, maybe if the standard Gnome edition is to heavy for your machine look to the other ligthweight verions of Ubuntu like Lubuntu or Xubuntu.
In general there are more options of distributions if Ubuntu doesnt want to work on your computer because of the low specs of your hardware to use Linux.

---

### Post by Floris- on 2010-10-03
Ok, I burned another 10.04 cd with IsoRecorder. It has been showing a purple square with "Ubuntu" written on it and 5 white dots which are replaced by red dots every 5 sec's. After like 5 mins the purple square dissapeared and I got the same black screen as when I booted it after updating Ubuntu from Ubuntu itself. So I can't use any live cd to boot it at the moment. Any other helpfull tips, or should I just stick with 9.10?

---

### Post by ivanovnegro on 2010-10-03
> **Floris- said:**
> Ok, I burned another 10.04 cd with IsoRecorder. It has been showing a purple square with "Ubuntu" written on it and 5 white dots which are replaced by red dots every 5 sec's. After like 5 mins the purple square dissapeared and I got the same black screen as when I booted it after updating Ubuntu from Ubuntu itself. So I can't use any live cd to boot it at the moment. Any other helpfull tips, or should I just stick with 9.10?

Maybe its a problem with your graphic card.
There is a known bug with Nvidia cards or older Intel Cards that cause the black sreen I think. You can try to search in the forums about this.
If you want you can stick with 9.10., no problem. You will recieve security updates until next year of April.
But 10.04 e.g is an LTS version with "long term support" (3 years).

Edit: You could use 9.10 and wait to the next version of Ubuntu (10.10), in seven days it will come out and maybe you wont have the mentioned problems.

---

### Post by SaintDanBert on 2010-10-03
Let's consider some basic details (is it plugged in) before we open the bonnet.

So you power-on your workstation, interrupt the automatic boot sequence, load your CD or DVD and then boot. Are you certain starting from your media? Many workstations have start-up options, magic keystrokes, and friends to enable boot from CD or DVD. It is possible that these options are trying to use something different from what you expect.

When you download a distro, you get  **something-edition.iso** on your workstation HDD. Now you want to burn CD or DVD using that iso. Everyone makes a common mistake at least a few times. The mistake simply drags the iso file onto the blank media then burns. You get media tha happily holds a copy of the ISO, but its contents are not available for system startup. You want to make your media using the _**contents**_ of the ISO file.

Most distros are set so that you right-click an ISO file on your desktop or in a file manager window. The context menu then asks, "Burn using _____" where you will have some default app and a list of other apps that registered with the context menu for ISO files. **Brasero** and **k3b** are common choices.

Another potential trouble spot involves the quality of the ISO itself. Each ISO has an MD5 or similar signature that you can use to compare that you have (a) an accurate copy, and (b) an un-tampered copy. When you burn the contents of the ISO, most burn applications check this signature for you. When you boot your media, you will also see an option to verify the media. It really helps to know you have a sane file and a sane burn before you start trying to use the media contents.

If you get a menu when you try the live-CD, consider testing or installing without using the graphical interface. This is another go/no-go test. If things start-up without graphics, that mostly nails one source of your troubles. Ubuntu Lucid uses X11 parts that are mostly new in several wonderful ways. Many of the tinker-and-pray issues are gone. A couple of very rare trouble spots remain -- some for older hardware; some for screaming edge.

Is this helping at all,
~~~ 0;-Dan

---

### Post by santana007 on 2010-10-03
> **Floris- said:**
> I installed Ubuntu like 3 days ago with a cd I got when I bought a magazine about Ubuntu. That cd contained Ubuntu 9.10. After a couple of hours I desided to instal 9.10. After using 9.10 for 1 day and installing some programs like java and flash player, I checked for updates and desided to update to 10.04. The installation seemed to go all smooth, but after I clicked on the 'reboot now' button, my laptop couldn't boot no more. A little purple screen with "Ubuntu" written on it popped up for like 5 seconds and then it dissapeared, and there I had a nice black screen. I waited 4 hours, but still nothing. Yesterday I installed 9.10 again, and now I still want to update to 10.04 or 10.10. But I can't seem to use a Usb flash drive with my Toshiba laptop, and I only have 1 cd left. My rabbit kinda destroyed the 10.04 cd and now I only have 1 cd left. Shall I burn 10.10 on a cd and check if that one will work properly, or is my laptop just to old and slow ( Centrino 1.6ghz, 512mb ram ) to run one of those versions?
I'm really new to ubuntu and my English sucks as well, because I come from Holland.
Thanks already for reading my boring story and for any help you can provide me with.

I had a similar problem. I made a post and got an answer that worked. You can read it here: ```
http://ubuntuforums.org/showthread.php?t=1584931
```
You are not alone with this problem. I'm reading a lot of posts like yours and mine. BTW, my mother came from Holland after the War. My father was in the Canadian Army and fought in the liberation for Holland.
I would be interested in knowing if this helps. Cheers

---

### Post by Floris- on 2010-10-04
> **santana007 said:**
> I had a similar problem. I made a post and got an answer that worked. You can read it here: ```
http://ubuntuforums.org/showthread.php?t=1584931
```You are not alone with this problem. I'm reading a lot of posts like yours and mine. BTW, my mother came from Holland after the War. My father was in the Canadian Army and fought in the liberation for Holland.
I would be interested in knowing if this helps. Cheers

Thanks for the link, but it doesn't work for me. I can run every command untill the configure -a. I tried your version with the --configure and without the --'s. 
I'm becoming a little desperate right now, I want to update the system badly lol. Not that I don't like 9.10, but 10.04 seems to be a lot better from what I read from people. :p

---

### Post by mörgæs on 2010-10-04
I would for sure stick to 9.10, but it sounds like it is not possible to convince you to do so :-) 

If you have firmly decided upon 10.04 or 10.10, I guess it is best to go for Lubuntu rather than Ubuntu. There is a guide here:
[http://ubuntuforums.org/showpost.php?p=9834517&postcount=261](http://ubuntuforums.org/showpost.php?p=9834517&postcount=261)

---

### Post by Jolicoeur on 2010-10-04
> **ivanovnegro said:**
> Maybe its a problem with your graphic card.
There is a known bug with Nvidia cards or older Intel Cards that cause the black sreen I think. You can try to search in the forums about this.
If you want you can stick with 9.10., no problem. You will recieve security updates until next year of April.
But 10.04 e.g is an LTS version with "long term support" (3 years).

Edit: You could use 9.10 and wait to the next version of Ubuntu (10.10), in seven days it will come out and maybe you wont have the mentioned problems.


That's what I am trying. I am stuck at 9.10, live update for 10.04 failed, cd for 10.04 failed.  I am hoping that 10.10 will install and I will be back in the game. By the way mint 9, same thing won't install.

---

### Post by ivanovnegro on 2010-10-05
> **Jolicoeur said:**
> That's what I am trying. I am stuck at 9.10, live update for 10.04 failed, cd for 10.04 failed.  I am hoping that 10.10 will install and I will be back in the game. By the way mint 9, same thing won't install.

Mint 9, that was what I wanted to suggest you now, but it happened the same I see.

---

