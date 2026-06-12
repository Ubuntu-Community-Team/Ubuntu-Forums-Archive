---
title: "burn download to USB?"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by Camilia on 2012-04-25
I decide to restart ubuntu with a CD. The only CD that would work is 9.04. I was hoping to upgrade to supported version. There are no upgrades for it. I downloaded 11.04 to PC. The option to burn to CD won't work for PC doesn't recognize that I have a CD in it. 

How do I burn it to a USB?

---

### Post by wojox on 2012-04-25
Command line dd is good. Graphicaly unetbootin.

---

### Post by strask on 2012-04-25
> **wojox said:**
> Command line dd is good. Graphicaly unetbootin.
So if the iso is ubuntu.iso, and the usb thumb drive is /dev/sdg, would that be something like ```
dd if=./ubuntu.iso of=/dev/sdg
```
Or would you need other options? Is there any special magic to make a usb thumb drive bootable?

---

### Post by techsupport on 2012-04-25
> **Camilia said:**
> I decide to restart ubuntu with a CD. The only CD that would work is 9.04. I was hoping to upgrade to supported version. There are no upgrades for it. I downloaded 11.04 to PC. The option to burn to CD won't work for PC doesn't recognize that I have a CD in it. 

How do I burn it to a USB?

Here are instructions on how to get the Ubuntu ISO migrated to a USB Flash Drive:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

---

### Post by Camilia on 2012-04-25
> **strask said:**
> ```
dd if=./ubuntu.iso of=/dev/sdg
```

Do you mean to paste this in the terminal? Did so and got no file found.

---

### Post by wojox on 2012-04-25
> **strask said:**
> So if the iso is ubuntu.iso, and the usb thumb drive is /dev/sdg, would that be something like ```
dd if=./ubuntu.iso of=/dev/sdg
```
Or would you need other options? Is there any special magic to make a usb thumb drive bootable?

Just add sudo. to the dd command and maybe run fdisk -l to locate the drive. No special magic needed to make it bootable,

---

### Post by Camilia on 2012-04-25
> **techsupport said:**
> 
[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)
Went there. Still don't understand how to get file on download file to USB. Also it is a To Do List After installing Ubuntu 12.04 LTS aka. I haven't gotten there yet.

---

### Post by techsupport on 2012-04-25
> **Camilia said:**
> Went there. Still don't understand how to get file on download file to USB.

Instructions on how to migrate that image are there too. You need to click the link that takes you to the instructions on the Ubuntu Web Site. You really have to carefully read everything on that guide first.

Bookmark the link I gave you. You will need it when you are done.

:lolflag:

---

### Post by wojox on 2012-04-25
> **Camilia said:**
> Do you mean to paste this in the terminal? Did so and got no file found.

You definetly want unetbootin. It will even download the images for you. :)

---

### Post by Camilia on 2012-04-25
All of the suggestions are just confusing me.

I don't see the instructions to migrate.

What is unetbootin and where is it?

---

### Post by strask on 2012-04-25
> **wojox said:**
> Just add sudo. to the dd command and maybe run fdisk -l to locate the drive. No special magic needed to make it bootable,
Thanks wojox. :)

---

### Post by techsupport on 2012-04-25
> **Camilia said:**
> All of the suggestions are just confusing me.

Alright.

Here is the link on that guide that you need to read to find out how to make a USB Bootable Flash Drive:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

In the above link scroll down to 2. 

Select the radio button that says USB.

Select your current operating system you are running on your computer.

Here is what you need to migrate the ISO to a USB Flash Thumb Drive in Windows:

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by jadtech on 2012-04-25
go to software center type in  unetbootin

i dont find  any info there for making a bootble usb image  or a link i read the whole page, i am not doubting it is there just not clearly marked  ..

i tend to disagree with the link any how I vote  do the wubi install if you got that working its simple to migrate to a full install dual boot and  will be known ready working OS  wubi gives you the freedom to play no chance of messing up anything to do with windows install trying to get ubuntu going ..

---

### Post by techsupport on 2012-04-25
> **jadtech said:**
> go to software center type in  unetbootin

i dont find  any info there for making a bootble usb image  or a link i read the whole page, i am not doubting it is there just not clearly marked  ..

i tend to disagree with the link any how I vote go do the wubi install if you got that working its simple to migrate to a full install dual boot and  will be known ready working OS  wubi gives you the freedom to play no chance of messing up anything to do with windows install trying to get ubuntu going ..

Wubi sucks for the long term. Don't use it unless you want to be here all day getting help trying to recover your data when it crashes eventually. 

You would be better off installing Ubuntu in VMWare inside your existing Windows OS if you want to keep windows too.

I haven't needed Windows in over 4 years now after I installed Ubuntu. Go ahead and wipe Windows off your hard drive, and completely install Ubuntu 12.04 LTS. Yes, it takes some time to learn how to do everything you could in Windows, but whatever. That's why it is free.

---

### Post by jadtech on 2012-04-25
> **techsupport said:**
> Wubi sucks for the long term. Don't use it unless you want to be here all day getting help trying to recover your data when it crashes eventually. 

You would be better off installing Ubuntu in VMWare inside your existing Windows OS if you want to keep windows too.

I haven't needed Windows in over 4 years now after I installed Ubuntu. Go ahead and wipe Windows off your hard drive, and completely install Ubuntu 12.04 LTS. Yes, it takes some time to learn how to do everything you could in Windows, but whatever. That's why it is free.

i been using a wubi install nearly 3 months now even just upgrade it to 12.04 and have not had to ask a single question here on how to recover or  fix myself from a crash its been running  solid other then once I messed it up myself and had to do some work to get things going again ..

I am pretty much ready to migraqte wubi set up to a full install on it own partition I know I havea working OS here on my lap top ..

what sucks about that ???

---

### Post by techsupport on 2012-04-25
> **jadtech said:**
> i been using a wubi install nearly 3 months now even just upgrade it to 12.04 and have not had to ask a single question here on how to recover or  fix myself from a crash its been running  solid other then once I messed it up myself and had to do some work to get things going again ..

I am pretty much ready to migraqte wubi set up to a full install on it own partition I know I havea working OS here on my lap top ..

what sucks about that ???

I just read a thread yesturday in this very forum about how someone lost all their data on it. Yeah, that sucks man. Can't imagine much worse than that. lol.  Don't use Wubi for the long term. Better way is to take the time to install VMWARE in Windows, and install Ubuntu OS virtually.  Wubi is for test drives only. Using it for longer is just plain foolish and lazy in my opinion. It is great for learning about Ubuntu. It isn't great for using Ubuntu for years and years.  Just install Ubuntu to your hard drive permanently, or use VMware to install it within Windows or Mac iOS, if you want it to function for extended period of time.

---

### Post by jadtech on 2012-04-25
i read that too how ever they lost there data in wubi by useing the uninstall in widows to uninstall wubi an the data file and such werent lost they were still there  just had to load a live CD and get them out of the uninstalled  program ..

you can mount the drive of wubi with live cd the same as you can a full install ..

the problem come when  other come  wanting to try ubuntu half prepared they have no window recovery cd no windows CD if they install wubi from window down load they don't read the info that tells them clearly to make a bootble cd or USB as well :) 

i have been using linux since 94 -95 the thing I see here in the last months is that many  seem to feel an interest in ubuntu but no interest in dealing with linux the 2 dont go together ubuntu is linux :)

---

### Post by techsupport on 2012-04-25
> **jadtech said:**
> i read that too how ever they lost there data in wubi by useing the uninstall in widows to uninstall wubi an the data file and such werent lost they were still there  just had to load a live CD and get them out of the uninstalled  program ..

you can mount the drive of wubi with live cd the same as you can a full install ..

They wouldn't have lost all their data if they had just used Vmware to install Ubuntu virtually.   You said you hadn't seen any reports of -any- issues, well, we saw one just yesterday, and I am just not going to recommend it for the long term.  That would suck to lose everything you have worked on.

:lolflag:

---

### Post by jadtech on 2012-04-25
they had both a full install and wubi they had just finished  there partitioning and set up and choose to uninstall wubi a little to soon maybe we have to different post but there is a big differnce in losing your data and choosing to uninstall a program ..

either way the data was not lost in that case just needed a little more effort to get it back ..

pictures and stuff  are rarely lost if you set ubuntu to do auto updates to ubuntu one they give you 5 GB of space free if its updated there it can be gotten back from any computer using any OS as long as you have the user name and password :)

---

### Post by techsupport on 2012-04-25
> **jadtech said:**
> they had both a full install and wubi they had just finished  there partitioning and set up and choose to uninstall wubi a little to soon maybe we have to different post but there is a big differnce in losing your data and choosing to uninstall a program ..

either way the data was not lost in that case just needed a little more effort to get it back ..

Little more effort? If they spent more effort and had something that really works on the long term like VMware in Windows and virtualize their Ubuntu OS installation, they wouldn't have to worry about anything like that happening. ):P

Wubi is a learning tool. That's how it should be imagined. It is not something you continually run for years and years and expect not to have issues develop eventually in Windows.

There is a whole thread devoted to Wubi issues in these forums. Just read through and see all the problems users have had with their Wubi installations.  I'm not going to recommend it for anything other than a classroom type of environment.

---

### Post by jadtech on 2012-04-25
there is a whole forum with many catagories devoted to issue with Ubuntu !! whats that prove ??

---

### Post by Camilia on 2012-04-27
Thanks for all of your replies.

While I was visiting my daughter my son in-law offered to burn 11.10 onto a CD for me. Of course I took him up on it.

---

### Post by kurt18947 on 2012-04-27
> **Camilia said:**
> Thanks for all of your replies.

While I was visiting my daughter my son in-law offered to burn 11.10 onto a CD for me. Of course I took him up on it.

That works! :lolflag:.   One advantage of a USB drive over CD is that USB can be created so as to remember settings, data etc.  It's called persistence.  I find a USB install speedier as well.  Older machines may or may not boot from USB.  If you know how to get to your BIOS there's usually a menu about boot order.  IF USB HDD (hard disk drive) is listed, you can choose that as the first option, then CD then HDD.  Your machine can check for them in order,


[LIST=1]
[*]Try to boot from a USB stick.  No USB boot device found?  Go to
[*]CD/DVD.  If found, boot from that.  If not found, go to
[*]Hard drive.
[/LIST]
If you want to play around with making your own USB install, you can google "Unetbootin".  It's available for Windows or Linux.  It's easier to install in windows, just click on the .exe file.  If your 11.10 CD loads you can also use the "startup disk creator" (or whatever it's called) on the CD to create a bootable USB drive.

---

