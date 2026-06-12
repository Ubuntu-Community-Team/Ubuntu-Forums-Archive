---
title: "Fiesty &quot;over the top&quot; of edgy (pics inside)"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Blindraven on 2007-04-21
Ok,
I was upgrading edgy last night when it came up with some pop-up about restarting services or some such and that i should reboot (there was still an hour left of updating to go mind you), to be honest it was a very un-informational pop-up and I had no idea what to do, So i typed "reboot" and it did just that.

Upon getting back in to the login screen for kde using kubuntu gdm, I logged in - a quick glimpse of my desktop and bang, it restarts back to gdm login again... and it does this over and over.
I hit alt-f2 and typed in dpkg --configure -a and it went through an enormous list of dependcy issues and that somehow failed.

I typed in sudo apt-get dist-upgrade and it nearly worked then scrolled through mass dependency issues again and went back to command.

I typed in sudo apt-get dist-upgrad -f and it kind of just went a-woll and failed in the *** worse then failure's very meaning...

My efty install is seemingly borked beyond all recognition - and EVERYTHING is on it..
So im sitting here using a fiesty cd I downloaded from upstairs and Ive just finished taking screen shots using the utilities on this cd so that everything is clear and you know what direction I want to take.

Unless you can suggest how i fix my screwed half edgy/half fiesty install I'd just like to install "over" it but keep all my files.

[IMG]http://i18.photobucket.com/albums/b143/blindraven/ubuntuissues/Screenshot.jpg[/IMG]

[IMG]http://i18.photobucket.com/albums/b143/blindraven/ubuntuissues/Screenshot-1.jpg[/IMG]

---

### Post by trippinnik on 2007-04-21
Well I would get some NFS or SAMBA action going with your upstairs computer and backup whatever you can to that.  You may have to try and backup only essentials if backup space is such a premium.  Also, definetly bzip2 that stuff, cause it really cuts those sizes down.  Goodluck.
I actually had a bit of a problem when I feisty over edgy too, it took like more than twelve hours,  and wasn't really done, so I had to dpkg --configure -a but it was fine after that...

---

### Post by Blindraven on 2007-04-21
> **trippinnik said:**
> Well I would get some NFS or SAMBA action going with your upstairs computer and backup whatever you can to that.  You may have to try and backup only essentials if backup space is such a premium.  Also, definetly bzip2 that stuff, cause it really cuts those sizes down.  Goodluck.
I actually had a bit of a problem when I feisty over edgy too, it took like more than twelve hours,  and wasn't really done, so I had to dpkg --configure -a but it was fine after that...

No can do unfortunately (though thanks for your reply), the pc upstairs is a 40 gig and mostly filled with my flatmates stuff.
Theres gotta be a way to do this...

---

### Post by trippinnik on 2007-04-21
Well, I'd recommend finding a way to backup the stuff you will really need before you continue much more... I've never seen anything like installing a new version over the existing version like I used to do in windows.  I am really surprised that dpkg --configure -a failed too though.  You said there were a lot of failed dependancies, how did you do the install over?  Did you disable custom repositories? maybe you could try aptitude upgrade

---

### Post by Blindraven on 2007-04-21
> **trippinnik said:**
> Well, I'd recommend finding a way to backup the stuff you will really need before you continue much more... I've never seen anything like installing a new version over the existing version like I used to do in windows.  I am really surprised that dpkg --configure -a failed too though.  You said there were a lot of failed dependancies, how did you do the install over?  Did you disable custom repositories? maybe you could try aptitude upgrade

If you meant how I chose to install from feisty - I chose "Upgrade" not "fresh install" - and that ran in to the problem of having to reboot half way through etc.

---

### Post by trippinnik on 2007-04-21
did you use the CD? Did you click upgrade in Synaptic? Did you type apt-get dist-upgrade? There all pretty similar but doing it from the cd, would probably be the most different.  I saw that you tried to do apt-get dist-upgrade, have you tried apt-get upgrade? and apt-get update?

---

### Post by trippinnik on 2007-04-21
try this apt-get -f install then dpkg --configure -a

---

### Post by Blindraven on 2007-04-22
No luck, just more dependency issues..

Anyone else got any ideas?

---

### Post by Blindraven on 2007-04-22
anyone :(

---

### Post by trippinnik on 2007-04-22
you've disabled your custom repositories right?

---

