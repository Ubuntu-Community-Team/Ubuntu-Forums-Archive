---
title: "error while trying to boot from a LiveUSB"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by agelos on 2010-01-27
hello,
  now for the past couple of days i've been having the worst time since i started using ubuntu,yes i'm still a newbie and i don't want to loose my faith on ubuntu not yet at least.
after some issue i had with my graphic card on my previous installation (i
 was running the 8.04 and everything was working great until i messed it up,my bad big time)i decided for an upgrade that i was thinking for some time now.
.
First of all i download the 9.10 iso which i installed on a usb using another pc in the house following guide from this website

**[http://www.pendrivelinux.com](http://www.pendrivelinux.com)**

 .That's been one of my guides since i started this mission.followed exactly the steps for the 9.10 installation on a usb key and minutes after it was done.then i unmounted the usb from the xp machine and started working on my machine.Resarted my computer with the usb mounted went through the bios boot option set that to my usb which was displaying fine on the menu and waiting for the installation menu to come up,that did happen but when i pressed to use the liveusb with no changes to my computer it generated a bit of code as noraml and then got stuck on this page:
[B]

[http://s702.photobucket.com/albums/ww29/aspilio/?action=view&current=2010-01-25132416.jpg](http://s702.photobucket.com/albums/ww29/aspilio/?action=view&current=2010-01-25132416.jpg)[/B] 
[IMG]http://s702.photobucket.com/albums/ww29/aspilio/?action=view&current=2010-01-25132416.jpg[/IMG][IMG]http://s702.photobucket.com/albums/ww29/aspilio/?action=view&current=2010-01-25132416.jpg[/IMG]

i then tried the option for checking for defects but had no luck there either.soon after i decided to give it a go with a 8.10 iso that i already had downloaded,followed the steps again from the **[http://www.pendrivelinux.com](http://www.pendrivelinux.com)** this time for the 8.10  iso and after couple of minutes i was ready to go.again.this time the liveusb booted just fine and i was for once in the process of installing the OS.Also i want to mention that before my installation i used to have a dual boot with a xp but i decided i didn't want them anymore as never used.
As i wanted to try the newest ubuntu out there and my graphic card still had issue with 8.10 i decided to do the upgrade from the update manager as i thought that would be the  more straightforward way to go.I went through the long procedure and then i was prompt to restart my computer for the installation to be completed,i did that and then after the first bit it got stuck while the loading bar was in the middle,i waited a bit with no luck,tried to restart the computer with no different outcome.then i decided to reinstall 8.10 as that was my only safe bet until now.
I still wanted to have an upgrade so i decided to try another way.this time i followed
 the guide from this website  **[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)** and decided to build up the liveusb not from windows but with ubuntu,i used the create a usb start up disc applications prompt under the administrator option.Again no luck ,i tried both 9.04 and 9.10 iso with similar results.(9.04 liveusb was getting stuck at the screen as it was happening when trying upgrade and 9.10 the same screen with the photo i posted before)

 please someone help,i don't know what  iam doing wrong,i also looked more thoroughly in my bios option but i couldn't find something,i also tried the liveusb on the other
 xp machine in the house and it's  booting fine so i know there is something wrong with my computer but then again why it went thought two times with installing 8.10 and get stuck with other releases ,is there any chance that is not working because i am not running windows anymore,
i also wanted to say that i was using two different usb keys for all this,one FREECOM 16gb and a 2gb KINGSTON

i'd really appreciate some replies,cheers.

---

### Post by Mighty_Joe on 2010-01-28
That image you posted sure makes it sound like you have some bad memory. Do you get the same errors with both USB drives in the same version of Ubuntu? It is interesting that you didn't get the same problem with the Live CD.
First, I'd try running memtest from the Live CD (select "Test Memory" from the boot menu).  It will take quite a while.
Next, I'd try a full install to the 16Gb flash drive.  Back up anything you want to save and give the whole drive to Ubuntu.

---

### Post by agelos on 2010-01-28
> **Mighty_Joe said:**
> That image you posted sure makes it sound like you have some bad memory. Do you get the same errors with both USB drives in the same version of Ubuntu? It is interesting that you didn't get the same problem with the Live CD.
First, I'd try running memtest from the Live CD (select "Test Memory" from the boot menu).  It will take quite a while.
Next, I'd try a full install to the 16Gb flash drive.  Back up anything you want to save and give the whole drive to Ubuntu.



i don't why i should have any bad memory as I've already formated the whole drive with ubuntu a couple of times the last days.

another thing that's really weird is that is getting stuck while booting from a restart(and never recovered had to fresh install again,probably there is a way of fixing the error with the liveusb again but for me being a newbie i can only fix that with a fresh install.) after making the first update on a fresh install with the 8.10,i haven't updated now being afraid that is gonna get stuck again.i'm really thinking of going back at 8.04 as i had no problems until i screwed something up.Anyway i'll try what you said with the same usb cause i think i did all the successful installs with the kinston and the errors with the freecom,i am not sure if i remember correct but i'll give it a go anyhow.if you can think of something else please let me know,cheers.

---

