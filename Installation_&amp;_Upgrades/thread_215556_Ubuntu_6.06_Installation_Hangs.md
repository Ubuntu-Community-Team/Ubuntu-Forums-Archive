---
title: "Ubuntu 6.06 Installation Hangs"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by sarangbapat on 2006-07-14
[FONT="Trebuchet MS"]Hi All,

I ordered the Ubuntu 6.06 (Dapper) CD and recieved it 2 days back. I could not resist the temptation to install in at once so I created the following partition layout on my 40GB disk:
1. partition 1(20GB - primary), or root partition, where I have installed M$ OS.
2.  partition 2 (19 GB - primary), formatted with ext3 filesystem, on which I want to install ubuntu. 
3. partition 3(512MB - primary), for swap.

Now, I configured my BIOS to boot up from the CD Drive, and restarted the PC with the Dapper CD in my CD Drive. After selecting defaults, I arrived at shiny, new ubuntu desktop in Live CD mode, with an icon to install it permanently on my system. Without wasting much time, I clicked on the Install icon on the desktop. It started the graphical install, and I was asked the language(English), keyboard(Eng-US), timezone(Calcutta/India), and created user name and set the system name. Then it came to partitioning section, where I selected "Manually Edit partition", and later on it just hanged. No errors, I waited for more than 45 minutes, nothing was working, keyboard hanged, mouse was irresponsive, so i didnt have any option but to cold reboot. I tried again, thinking that it might be something wrong at that instance, but in vain. After trying for 2-3 times, I decided to repeat the same procedure in safe mode. But same problem persisted. So I gave up, and installed Ubuntu 5.10("breezy") on the same partition, which got installed without any problem. STRANGE, huh, breezy installs, but dapper does not, on the same machine!! 
Giving up, I decided to post this in this forum. Can anybody help me out to install Ubuntu 6.06? Is there a TEXT-only installation of Ubuntu 6.06, just like in 5.10? Is there any other way out?

I am sorry if somebody has already posted same problem here, as I didnt read the earlier posts. 

My PC configuration: 
Intel 845 Motherboard with onboard graphics controller.
LG 440Si 14" monitor, 1024x768 max resolution. 
256 MB RAM
40GB HDD

NOTE: Ubuntu 6.06 LIVE works fine, without any problem. This is an INSTALLATION issue.[/FONT]

---

### Post by Malac on 2006-07-14
[COLOR=Black]I had the same problem with Dapper.
I got round it by letting the partitioner do guided partitioning then going back and re-doing them manually. I can't remember the exact sequence of keys pressed or choices but that is the gist of it.
This worked for me.

[/COLOR][COLOR=Black]You could try a dist-upgrade to get you to Dapper level once you have installed Breezy. Do a search for "dist-uprade" on the forum.

Hope this helps.

[/COLOR]

---

### Post by raldz on 2006-07-14
If it is a problem with the graphical installer, you may download the "alternate" CD-ISO from Ubuntu's download page.. It will run Dapper in text mode installation similar to Breezy..

---

### Post by sarangbapat on 2006-07-14
[FONT="Trebuchet MS"]Hi Guys,

Thanks for the quick responses. I really appreciate the responsiveness of these forums. But, both the solutions are not of much use to me. :( 

**Malac:** I cant do guided partitioning, since it will destroy my windows partition, too. I strictly want to stick to the existing partitioning scheme. Sorry for being such a damp squib!! But my reasoning is if Ubuntu 5.10(breezy) can install under the same scheme, then this version should install too. dist-update, I guess will require high speed internet connection, which I dont have. Anything more than 20MB download is too much for me. Any other options, that I can use. Anything with the CD that came to me?

**Raldz:** I cant download 690 MB ISO. It will take ages for me. Thats why I ordered pressed CDs. :) Any other options? Cant I upgrade Ubuntu 5.10 using this CD to Ubuntu 6.06? 

[/FONT]

---

### Post by cotcot on 2006-07-14
I think yes. If you add the CD entry in the /etc/apt/sources.list.

There is probably an entry for the Breezy CD. I installed dapper and erased this ressource because I do not want apt asking for the CD when I install packages. I also used the alternative installCD.



For breezy it looks like this : 
> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

For dapper you should adapt to the version of your CD. Release i386 can be something else for instance when you have an AMD chip. 
> deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

---

### Post by Malac on 2006-07-14
Sorry sarangbapat, should have explained a little better.
I think you choose "manual partition" then there is an "automatic" or "suggested" partition option after that, this is what I meant.
Let it workout the partitions but don't commit them to disk then go back in to "manual" and re-do the partitions how you would like them.

Remember it doesn't actually write anything to disk until you do "finish partitioning".

---

### Post by swamytk on 2006-07-18
Hi Sarangbapat,

I too faced the same problem yesterday, I managed to install. Here is a simple HOWTO on that. Definitely it will solve your problem. 

HOWTO: Ubuntu 6.06 installation on Legacy PC (low RAM)
[http://www.ubuntuforums.org/showthread.php?t=218036](http://www.ubuntuforums.org/showthread.php?t=218036)

---

### Post by sarangbapat on 2006-07-20
[FONT="Trebuchet MS"]Hi Swamytk, 
Your solution looks quite promising. Thanks for the information. It is quite detailed and self explainatory. I will try this out soon & post the results back on the same thread. Thanks again. 
- SarangBapat[/FONT]

---

