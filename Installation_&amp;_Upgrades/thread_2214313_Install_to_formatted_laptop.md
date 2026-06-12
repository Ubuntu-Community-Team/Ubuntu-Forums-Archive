---
title: "Install to formatted laptop"
date: 2014-03-31
forum: Installation &amp; Upgrades
---

### Post by Shoalster on 2014-03-31
A friend of mine says he's going to trash his laptop.   It has Windows  XP which is going to be extinct and it's all bogged down with malware  most likely because he knows nothing about OS maintenance.  I told him  to just hold up on that and I would format his HD and install Ubuntu on  it .   He only needs it for email and a few maintenance records he keeps  on his truck.   I have been reading posts here for an hour and "think" I  know how to do it.  Just wanted to ask and check for any dos   and don'ts  that someone may have .  I have been using Ubuntu for over a year now  and LOVE it.   Any advice and tips would be much appreciated.

---

### Post by 23dornot23d on 2014-03-31
Find out which laptop it is and do some quick searches on the Net for  common problems to do with installing Linux on it ..........

Just  so you have a rough idea of what if any problems you may run into  ......... but if there are few problems to do with that laptop

Search  on the laptop name and solved too .......... its sometimes as well to  know what sort of information is already out there and

whether or not it will fail ....... graphics cards and network cards ....... are things to check out too ...........

But  run a livecd on it and see if it works ok from that first ....... that  should give you a good indication of the possibility of it running well  or not.

( there are many other linux systems too - so if one does  not work - try a livecd for one that has been reported to work ok on  that laptop )

Do some recon ........ get some information about  it ....... do some research on problems ...... then if all is ok try the  livecd after all

it will run even if there is nothing on the  hard drive at all ........ * ( usually press something like (f8) the  function button at start up [depending on which laptop it is - again a 
google  search should soon let you know how to set it to boot from cd   ) or go  into the  setup screen at boot and change it to boot from cd and then  usb and then ide0 ................. depending on how you want to boot  ubuntu ....... the install to the main drive should be easy if you  intend to use the full hard drive ......... but ensure that
the laptop is not one that is known to have any major issues with Linux .....

---

### Post by mastablasta on 2014-04-01
dependign on the system specs you might want to explore lighter alternatives such as Lubutnu or Xubuntu 

otherwise doing a reformat and install is the easiest thing to do. the first option in installer will do most things automaticly you just need to confirm a few things (language,timezone,  keyboard etc.) and select user name and password.

---

### Post by Shoalster on 2014-04-01
OK.. Thanks.  I'll be picking up his laptop tomorrow and do some research.

---

### Post by Shoalster on 2014-04-14
I'm just now finding time to work on this.  It is a Dell Inspiron 1505E.   Research indicates I shouldn't have any problem installing Linux except maybe with the graphics card.  My problem at the moment is trying to format.   I'm going to try DBAN and hopefully if that works then will install Linux from a flashdrive.

---

### Post by sudodus on 2014-04-14
Who is going to use the computer after installing Ubuntu? If it is the same guy (your friend), you need not DBAN it. The Ubuntu installer will make new partitions (one for the root file system, and one for swap). Just let the installer use the whole internal hard disk drive :-)

---

### Post by sudodus on 2014-04-14
If the specs of this link are correct

[http://www.notebookreview.com/notebookreview/dell-inspiron-e1505-review-pics-specs/](http://www.notebookreview.com/notebookreview/dell-inspiron-e1505-review-pics-specs/)

and there is only 512 MB RAM, I'd recommend Lubuntu. If 1GB RAM you can try Xubuntu. Standard Ubuntu will work but slowly with those hardware specs.

---

### Post by RadicaX on 2014-04-14
I format normally with ease with Gparted. So like Sudodus said, you should be able to just use the Ubuntu installer. I would recommend you do the restricted extra download when you do install it, and make sure it can play dvds, he might use his computer for really nothing. But quickly you find out they might use it for a few more things, normally watching dvds, and boy, they get upset if they can not play dvd out of the box.

---

### Post by Shoalster on 2014-04-14
That would be perfectly fine.  I want to use the whole disk.   I still have Ubuntu 12.10 on flashdrive from when I installed it on my system so, I stuck it in his laptop and selected the "Try First" option.  The desktop loaded up but soon froze up .  That's why I thought I was going to have to wipe out the HD before I could do  ANYTHING.  I could try the Install option from the flashdrive if that will work.  Also,  I'm fine with downloading a lighter version like Lubuntu to flashdrive and load it to the laptop and see what happens.

---

### Post by RadicaX on 2014-04-14
Your best option is to go with the Lubuntu on the flashdrive route and seeing what happens. I have 1 GB of Ram, and while it worked better than Windows on here, (Ran much faster), I found normal Ubuntu time from time to freeze. I have found Xubuntu to work fine, but after extented use, sometimes programs do slow down. (Especially if use on facebook is done) But nothing to much. Really, I find that to be more a problem with how facebook runs. So try Lubuntu on a flash drive, do somethings, see if you can get it to freeze, if not, wonderful! If it seems to be causing problems, you could like said before, try other linux.

---

### Post by 23dornot23d on 2014-04-14
Lubuntu or Xubuntu 12.04 are better for that machine IMHO

[http://www.linlap.com/dell_inspiron_e1505](http://www.linlap.com/dell_inspiron_e1505)

GraphicsATI Mobility Radeon X1300 ( maybe ) just what I see on the above spec ...

**The support for 12.10 runs out in April 2014**

Also I have a feeling that 12.04 might just pick up the Graphics better too ...... as 12.04 LTS support also lasts to April 2017
( that means with 12.04 that the repositories and updates will be available through another 3 years ) 
where with 12.10 you have but a few more days.

Check the link below to see the support and end of life for each version of Ubuntu .......

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by pfeiffep on 2014-04-14
> **sudodus said:**
> If the specs of this link are correct

[http://www.notebookreview.com/notebookreview/dell-inspiron-e1505-review-pics-specs/](http://www.notebookreview.com/notebookreview/dell-inspiron-e1505-review-pics-specs/)

and there is only 512 MB RAM, I'd recommend Lubuntu. If 1GB RAM you can try Xubuntu. Standard Ubuntu will work but slowly with those hardware specs.
My older Dell had only 512 MB and really was a dog - I upgraded it to 2 GB (max for my machine) ~ $30. Now I'm running Ubuntu 14.04 beta with gnome flash back installed - all works great.

---

### Post by sudodus on 2014-04-14
The only current standard Lubuntu is 13.10. But very soon Lubuntu 14.04 LTS will be released, the first version of Lubuntu will long time support.

Xubuntu 12.04 LTS is supported until April 2015. And there is a community re-spin of Lubuntu 12.04, LXLE, with support promised until April 2017.

I agree, that it is a good idea to invest in more RAM, up to 2 GB.

---

### Post by Shoalster on 2014-04-14
I agree.  512 MB is too light.  I'll ask if he wants to add some memory.  In the meantime I'll try to install 12.04 and see if it will take.   I will leave this thread open for a little while if that's OK until I see the fruits (or cow pies) of my efforts.    Thanks to all.

---

### Post by RadicaX on 2014-04-14
Anytime, I do hope it goes good for you.

---

### Post by Shoalster on 2014-04-17
Installed Xubuntu 13.10  All went well but I have no network wired or wireless.   Seems to be a driver problem as I recieved the result "unclaimed" after network check.  Also, system will not shut down.

---

### Post by 23dornot23d on 2014-04-18
You could try this now ...... see if it does any better ....... [http://xubuntu.org/news/14-04-release/](http://xubuntu.org/news/14-04-release/)

---

### Post by Shoalster on 2014-04-18
OK  thanks.   Will try it tomorrow.

---

### Post by Shoalster on 2014-04-18
Nice !   14.04 is working nicely.  I have ethernet and system shuts down now.  Still no wireless though.  Is there a way to troubleshoot it in Terminal?

---

### Post by 23dornot23d on 2014-04-18
Raise it as a new question in here

 [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

**Networks and wireless** ...... the people hang out in there solve that sort of problem all the time.

__________________________

**iwconfig**

Should return something if the wireless is seen by the system ..... but that is about the extent of the commands I know for checking
to see if the wireless picks up ok using the command line .

So maybe best to go see the people in Networks and wireless - on the forum

This is about the best I found on the answers on the web 
[http://substack.net/wireless_from_the_command_line_in_linux](http://substack.net/wireless_from_the_command_line_in_linux)

---

### Post by Shoalster on 2014-04-18
OK.  Thanks.  I figured I would look through the forums.  I appreciate your help.

---

