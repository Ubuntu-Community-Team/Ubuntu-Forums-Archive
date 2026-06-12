---
title: "All Flash Drives Don't Work - Coding For Driver? After HP Printer Broke"
date: 2014-11-14
forum: Installation &amp; Upgrades
---

### Post by skyesharica on 2014-11-14
TIME TO CHANGE TO XUBUNTU?  

Major software error?  Is it time to do a system restore i.e. change to Xubuntu from Ubuntu 14.04 LTS?

I've had this PC and Ubuntu for just over a year.  It hasn't been really thrashed i.e. I haven't downloaded many movies, or made a film on it.  It's a great laptop.

Anyway my backup was on CDs (old), spare Seagate hard drive (appears to be fine) and FLASH DRIVES (here's hoping .... NOT!)

The flash drives all break - not exactly when I insert them, but when I try to do something with them.  I have had all of these errors.  From struggling terribly with forums - I think it's got something to do with drivers.  I just rolled back to an earlier version of Hewlett Packard printer, and it blew up my printer.  I did a lot of stuff with friends here and decided to never buy HP again.  The older version on 14.04 LTS really DID blow up the printer.  And they left the (essential fax & fun) scanner software out, before that ... not nice friends.  I very much doubt it was anything my friends did here.  I wouldn't buy them, would you?  :guitar:

Anyway, here are the error messages for the FLASH DRIVES.:

ALL THE FLASH DRIVES BROKE AT ONCE - ALL BACKUP DATA

[ATTACH=CONFIG]257946[/ATTACH]

Another weird error message.

[ATTACH=CONFIG]257947[/ATTACH]

Just Didn't Get Anywhere Near All Files!

[ATTACH=CONFIG]257949[/ATTACH]

Lots of Eject Error Messages - $100-150 of Flash Drives Wasted

[ATTACH=CONFIG]257951[/ATTACH]

Unable to Format on Ubuntu - Cannot Delete This TEMPORARY Folder - See Detail

[ATTACH=CONFIG]257952[/ATTACH]

I KNOW THE QUESTION IS IMPRESSIVE - I'M DESPERATE - I AM NOT IMPRESSIVE IN BRAINS, LIKE YOU - PLEASE ONLY GIVE CLEAR ANSWERS ***and I will not follow any programming instructions at all***.

---

### Post by The Cog on 2014-11-14
That sounds like your USB isn't working to me. 

Try the flash drives in a different computer to see if they are usable there. If they are, then the problem is in your laptop somewhere.

Try using an Ubuntu live CD in your laptop and see if that can see them. If so, it's the Ubuntu on disk that's got problems. The easiest approach then might be to reinstall, because debugging and fixing a borked install can be hard work.

Changing to Xubuntu won't help this, except that a clean install of Xubuntu will replace any mangled driver config just as a clean Ubuntu install will. But then you would have an unfamiliar GUI to contend with, so I don't recommend changing at the moment.

---

### Post by QIII on 2014-11-14
Please also bear in mind that we don't give "programming instructions".  We wouldn't ask you to program anything.

You may be conflating programming with issuing commands in the terminal.  The latter is not programming.

You do not necessarily need to know anything at all about using the terminal.  All you need to be able to do is cut and paste -- trying to retype things is fraught with the danger of typos that may cause problems.

The reason many of us ask you to run commands in the terminal is that they are a common "language" that is independent of any particular Desktop Environment (DE) and, with a few dialectical exceptions, any particular Linux distribution.  It would be nearly impossible for all of us to remember every detail of which menus to select and buttons to click in every possible DE, particularly when people can modify them.  There are many users who do not use the Unity interface (some actually use other distributions more often than any flavor of Ubuntu) and cannot tell you the exact series of button clicks to provide help.  They could, nonetheless, help by directing you through issuing commands in the terminal.

Furthermore, some of the commands suggested would provide the prospective helper with a great deal of diagnostic information that would otherwise not be available through a Graphical User Interface (GUI). Specifying that you do not want to use the terminal may actually complicate things unnecessarily rather than helping you get to the bottom of your problem.  A specification such as yours may cause others who would be able to help to just move on. 

Again:  No "programming" is involved.  Cutting and pasting commands serves to make helping you more efficient and it can provide important diagnostic information.  Specifying the form of the answer to be given will limit the number of those willing to help.

We are happy to help.  Please allow us to do so.

---

### Post by skyesharica on 2014-11-18
> **The Cog said:**
>  ... except that a clean install of Xubuntu will replace any mangled driver config just as a clean Ubuntu install will. But then you would have an unfamiliar GUI to contend with, so I don't recommend changing at the moment.

Thanks so much.  How difficult is it to get used to Xubuntu?  Do I need any special programming?  Is a lot of useful stuff missing ... or is it just plainer?

Thankyou very much Qlll.  I am very ignorant of even the simplest command prompts, but I understand a bit more about Linux and commands (not programming) now.  And their universal use by Linus friends here.  As you say, it helps to be super accurate, and "cut and paste", and that is why I decided to refuse to do this as well.  I don't mean it in anyway offensively towards this generous community ... I just know how easy it is for human error to occur.  And I am completely and utterly out of my depth with commands.  So I have to stick to my resolve and ask for simple solutions.  If you read my previous threads about the Hewlett Packard printer (see links below), you would see my opinion about what has gone wrong.  I believe that their software (an older version) ruined my printer altogether.  They are under no obligation, commercially, to be overly careful.  Before that, they left out the scanner function too!  And after the first damage, why wouldn't the damage to one driver, clash against another driver, like the USB Flash Drive?  It is a competitive world.  I don't think any of the advice I've received here, at Ubuntu, was very wrong (there could have been a tiny area for human error) ... I think Hewlett Packard caused this problem.  Now I have to go back to Microsoft.  So help me!  This is very painful.  But I will keep watching the Ubuntu news.  And see what sort of support they have for peripherals, and popularity, and overseas sales.  Once they are more popular, the other companies will have to support them better, and stick to their reputations, to bolster their sales.  I'll try to put this laptop into Xubuntu - a clean install - and keep it for eBooks etc.  Or a spare.  Is Xubuntu very different to Ubuntu ... are a lot of features missing?  I thought it would be a good system for using minimum resources.  Is it drastically different?

[http://ubuntuforums.org/showthread.php?t=2242381](http://ubuntuforums.org/showthread.php?t=2242381)

[http://ubuntuforums.org/showthread.php?t=2242660](http://ubuntuforums.org/showthread.php?t=2242660)

---

### Post by sudodus on 2014-11-18
> **skyesharica said:**
> Thankyou very much Qlll.  I am very ignorant of even the simplest command prompts, but I understand a bit more about Linux and commands (not programming) now.  And their universal use by Linus friends here.  As you say, it helps to be super accurate, and "cut and paste", and that is why I decided to refuse to do this as well.  I don't mean it in anyway offensively towards this generous community ... I just know how easy it is for human error to occur.  And I am completely and utterly out of my depth with commands.  So I have to stick to my resolve and ask for simple solutions.  If you read my previous threads about the Hewlett Packard printer (see links below), you would see my opinion about what has gone wrong.  I believe that their software (an older version) ruined my printer altogether.  They are under no obligation, commercially, to be overly careful.  Before that, they left out the scanner function too!  And after the first damage, why wouldn't the damage to one driver, clash against another driver, like the USB Flash Drive?  It is a competitive world.  I don't think any of the advice I've received here, at Ubuntu, was very wrong (there could have been a tiny area for human error) ... I think Hewlett Packard caused this problem.  Now I have to go back to Microsoft.

Many of us were running Windows and linux side by side for years before moving completely to linux. Some of us will keep running both systems 'forever'.

It can be done using two different computers, or dual booting one computer (deciding what to run when starting the computer) or running one main operating system, and running the other one in a virtual machine 'inside the other operating system'.

I think the support for peripheral devices like printers and scanners will continue to be better for Windows (and MacOS) - simply for commercial reasons. The manufacturers will make more money that way, or at least they think so. Another reason for keeping Windows is that you might need an application program, that has no version for linux.
> 
So help me!  This is very painful.  But I will keep watching the Ubuntu news.  And see what sort of support they have for peripherals, and popularity, and overseas sales.  Once they are more popular, the other companies will have to support them better, and stick to their reputations, to bolster their sales.  I'll try to put this laptop into Xubuntu - a clean install - and keep it for eBooks etc.  Or a spare.  Is Xubuntu very different to Ubuntu ... are a lot of features missing?  I thought it would be a good system for using minimum resources.  Is it drastically different?

[http://ubuntuforums.org/showthread.php?t=2242381](http://ubuntuforums.org/showthread.php?t=2242381)

[http://ubuntuforums.org/showthread.php?t=2242660](http://ubuntuforums.org/showthread.php?t=2242660)

Xubuntu has the same engine under the hood as Ubuntu. Only the desktop environment and the default programs are different. The desktop environment of Xubuntu is more like that of Windows (than Unity of standard Ubuntu). And Xubuntu has a lighter footprint (needs less memory and processor power) than standard Ubuntu.

 The same application programs can be installed into Xubuntu, Ubuntu and all the other 'flavours' and 'community re-spins' of Ubuntu. There are thousands of them available via the Software Center or Synaptic or terminal window commands. Use the tool that you prefer to install and uninstall program packages.

---

### Post by skyesharica on 2014-11-20
> **sudodus said:**
> Many of us were running Windows and linux side by side for years before moving completely to linux. Some of us will keep running both systems 'forever'.

It can be done using two different computers, or dual booting one computer (deciding what to run when starting the computer) or running one main operating system, and running the other one in a virtual machine 'inside the other operating system'.

I think the support for peripheral devices like printers and scanners will continue to be better for Windows (and MacOS) - simply for commercial reasons. The manufacturers will make more money that way, or at least they think so. Another reason for keeping Windows is that you might need an application program, that has no version for linux.


Xubuntu has the same engine under the hood as Ubuntu. Only the desktop environment and the default programs are different. The desktop environment of Xubuntu is more like that of Windows (than Unity of standard Ubuntu). And Xubuntu has a lighter footprint (needs less memory and processor power) than standard Ubuntu.

 The same application programs can be installed into Xubuntu, Ubuntu and all the other 'flavours' and 'community re-spins' of Ubuntu. There are thousands of them available via the Software Center or Synaptic or terminal window commands. Use the tool that you prefer to install and uninstall program packages.

Wow, what an awesome answer.  It is very kind of you and thorough.  That's why it's all in quotes.

I don't think I'll ever be able to do that advanced dual OS stuff ... but I know of it.  I'm not a specialist ... it's just an essential tool.

Yer must be dead on about where the buck ends ... when it comes to not getting the driver up to scratch.  As if they care.  Though drivers are renowned for blowing up systems!!!  But they must care about the boss--MS.  S:

Xubuntu sounds good ... minimum resources.  It's my understanding that software is the main culprit of a computer's demise.  I would like to keep this laptop for a spare, peace of mind, carry it with me sometimes, just use it for an email, or reading an ebook in bed.  I'd love to see a computer last longer than it's worst expected date ... for once in my life.  I bet Linux can do that.  Linux is very hard to get in Australia.  But I got a little netbook with some form of Linux on it.  You can't update it, but you can still go online or do an email or a text doco, on the tiny thing, after years!!!  I have it plugged in with speakers, next to my bed, for music ... it beats an iPod.  I just keep it for one purpose.  I know the governments once had a scheme called something like "One Computer For Each Child" and it was on Linux.  I'll never forget the joy I felt when it started up and I saw the orange and purple positivity.:popcorn:

I hope I'm not boring you.  I have overcome the initial agony, and am going to try to scape together the funds for another Apple.  Apple versus MS?  Similar machines have one vast difference ... MS only gives 1 year warranty (basically it's expected lifetime) and Apple will allow for an upgrade of 3 years.  Apple just always works, hardly ever crashes, and has no viruses (software that costs too) ... and so it adds up in the long term.  But I am struggling so I have to be really really careful with my budget.

> **The Cog said:**
> The easiest approach then might be to reinstall ... 

That is a great idea ... but what is a "re-install".  If I put in a bootable USB flash drive with the same version of Ubuntu 14.04 LTS, it doesn't install from the boot up menu.  How do I do it?  I have these resources on me.:

**1.**  A broken software which won't make a bootable USB flash drive.
**2.**  *BUT* I do have old CD with the older version of Ubuntu on it.  I think it's also a "live CD" something or other?
**3.**  One bootable USB flash drive with Xubuntu on it ... I didn't do anything to this flash drive, except to put it in the hub, and notice it was still full of the same looking folders and files.  The flash drives didn't break immediately ... they broke after I tried to move, format etc. [I] So I think it will still work ... pray so.  :eek:
[/I]

---

### Post by sudodus on 2014-11-20
A re-install is to start with a new installation (rather than to try to upgrade or repair the current installation).

-o-

0. We can help you step by step to get things right in order to boot from a DVD or USB drive with Ubuntu or Xubuntu. So decide what you want to do :-)

1. Check that the download was good. Use ***md5sum*** in a terminal window (in linux) or install and use ***md5summer*** in Windows

```
md5sum filename
```

where filename is the name of the iso file so for example

```
md5sum xubuntu-14.04.1-desktop-i386.iso
```
  
2a. Make the USB drive bootable with a good tool, for example ***Unetbootin*** in linux, MacOS and Windows, or ***mkusb*** in linux or*** Win32 Disk Imager*** in Windows
[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

The following link and links from it may help you with more tips

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

2b. or make a boot DVD - ***burn an image*** (do not make a data-DVD with the iso file on it).

3. Make the computer boot from USB. Try according to this paragraph

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

4. [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by skyesharica on 2014-11-22
> **sudodus said:**
> A re-install is to start with a new installation (rather than to try to upgrade or repair the current installation).

-o-

Thanks a lot.  But I have tried to put a bootable USB with the same version of Ubuntu on it and it just says fault, fault.

> **sudodus said:**
> 1. Check that the download was good. Use ***md5sum*** in a terminal window (in linux) or install and use ***md5summer*** in Windows

Thanks but I'd rather not put it back into the flash drive, in case it is working, and that destroys it.  I wouldn't know what to look for in the terminal.

However, could I DOWN-grade?  Could I put the DVD disc I purchased with the older version of Ubuntu on it ... and boot up with that?  Can you roll back a version?  Then I could fix the flash drive.  And boot back into Ubuntu 14.04 LTS.
  
> **sudodus said:**
> 2a. Make the USB drive bootable with a good tool, for example ***Unetbootin*** in linux, MacOS and Windows, or ***mkusb*** in linux or*** Win32 Disk Imager*** in Windows
[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

The following link and links from it may help you with more tips

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I can't understand this, sorry.

> **sudodus said:**
> 2b. or make a boot DVD - ***burn an image*** (do not make a data-DVD with the iso file on it).

Is there a link to show you how to do this?  How to put the bootable files on a DVD?

Thanking you again.  :)

---

### Post by sudodus on 2014-11-22
> **skyesharica said:**
> [QUOTE=sudodus;13171072]A re-install is to start with a new installation  (rather than to try to upgrade or repair the current installation).

-o-

Thanks a lot.  But I have tried to put a bootable USB with the same version of Ubuntu on it and it just says fault, fault.
[/QUOTE]
If you give us (me and other people with some experience) some hints, we can try to help. So please describe with as many details as possible what happens, what you see and hear :-)
> 
> **sudodus said:**
> 1. Check that the download was good. Use ***md5sum*** in a terminal window (in linux) or install and use ***md5summer*** in Windows

Thanks but I'd rather not put it back into the flash drive, in case it  is working, and that destroys it.  I wouldn't know what to look for in  the terminal.

OK
> 
However, could I DOWN-grade?  Could I put the DVD disc I purchased with  the older version of Ubuntu on it ... and boot up with that?  Can you  roll back a version?  Then I could fix the flash drive.  And boot back  into Ubuntu 14.04 LTS.
  
Yes, you can run a 'live session' booted from the DVD, and you can install Ubuntu from the DVD (re-install).

Remember to ***backup your data***, alias to save all your important personal files (documents, pictures, video-clips etc) before re-installing.
> 
> **sudodus said:**
> 2a. Make the USB drive bootable with a good tool, for example ***Unetbootin*** in linux, MacOS and Windows, or ***mkusb*** in linux or*** Win32 Disk Imager*** in Windows
[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

The following link and links from it may help you with more tips

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I can't understand this, sorry.

The red lines are clickable links to help pages, that try to describe how to do. Instead of giving up, please look at those pages, and select the one, that you think is easiest to use. Then I can help you, if you still need some help.
> 

> **sudodus said:**
> 2b. or make a boot DVD - ***burn an image*** (do not make a data-DVD with the iso file on it).

Is there a link to show you how to do this?  How to put the bootable files on a DVD?

Thanking you again.  :smile:

In Ubuntu, you can install ***k3b***, which is a robust and easy to use program for burning CDs and DVDs. There are several tools in Windows, that can do it. There is a built-in tool in Windows 7 and there is for example [http://www.freeisoburner.com/](http://www.freeisoburner.com/). The important thing is to ***burn an image*** (do not make a data-DVD with the iso file on it).

You wrote that you live in Australia. There are many Ubuntu members, and  at least one of the moderators of the Ubuntu Forums, who also live in  your beautiful country. (I live in Sweden (at the opposite side of the  Earth)). An alternative might be to ***ask someone in your country*** to burn  images of a couple of iso files onto DVDs and send them to you with  regular old-fashioned mail.

---

### Post by skyesharica on 2014-11-23
> **sudodus said:**
> If you give us (me and other people with some experience) some hints, we can try to help. So please describe with as many details as possible what happens, what you see and hear :-)

Well, it was a fair while ago when I tried to do this.  But I got to the boot menu.  I tried to install.  But I got stopped and there was an error message.  The bootable USB flash was fine.  So I assumed you can't install the same systems on top of each other.  I also got a strange different desktop for a while but I was all fine after a restart.  So I don't want to risk that.

> **sudodus said:**
> Yes, you can run a 'live session' booted from the DVD, and you can install Ubuntu from the DVD (re-install).

Great, well I'll do this.  I was just worried that it wouldn't be possible to roll back to an earlier version.  

From there I can check if the USB flash drives are working.  If so, I can make another bootable USB flash drive of Ubuntu 14.04 LTS.  And re-install.

> **sudodus said:**
> The red lines are clickable links to help pages, that try to describe how to do. Instead of giving up, please look at those pages, and select the one, that you think is easiest to use. Then I can help you, if you still need some help.

Well, I have a simple print out about how to do this.  So I'll try that first.

> **sudodus said:**
> In Ubuntu, you can install ***k3b***, which is a robust and easy to use program for burning CDs and DVDs. There are several tools in Windows, that can do it. There is a built-in tool in Windows 7 and there is for example [http://www.freeisoburner.com/](http://www.freeisoburner.com/). The important thing is to ***burn an image*** (do not make a data-DVD with the iso file on it).

Oh I am sorry but that is too hard.  What I will do is try to buy it online from an eBay seller, like I did before.

> **sudodus said:**
> You wrote that you live in Australia. There are many Ubuntu members, and  at least one of the moderators of the Ubuntu Forums, who also live in  your beautiful country. (I live in Sweden (at the opposite side of the  Earth)). An alternative might be to ***ask someone in your country*** to burn  images of a couple of iso files onto DVDs and send them to you with  regular old-fashioned mail.

Yes, that is an option too.  Thankyou my friend.  It is a very time consuming option, however, considering, the few Ubuntu contacts I have.  I am hoping on a much bigger Ubuntu PLANET when I return.  Thankyou again for all your marvellous help, a way up there in Sweden.  I have been very ill and the loss of a PC is a disaster to me.  So thankyou kindly and warmly.  ):P

---

### Post by sudodus on 2014-11-23
Good luck :-)

And welcome back if you have new questions.

---

### Post by skyesharica on 2014-11-23
> **sudodus said:**
> OK

Yes, you can run a 'live session' booted from the DVD, and you can install Ubuntu from the DVD (re-install).

Are you sure rolling back to the earlier version of Ubuntu will work?  I vaguely recall something bad about this ... when I was on Windows???

---

### Post by sudodus on 2014-11-23
> **skyesharica said:**
> [QUOTE=sudodus;13172180]OK

Yes, you can run a 'live session' booted from the DVD, and you can install Ubuntu from the DVD (re-install).

Are you sure rolling back to the earlier version of Ubuntu will work?  I  vaguely recall something bad about this ... when I was on Windows???[/QUOTE]

Once an installed system is upgraded to a new version, it cannot be reversed to the previous version, unless you have a full backup, and restore the system from that backup.

But you can save your personal files (a partial backup), re-install from a DVD or USB drive, and restore your personal files from the partial backup. This is what many people do.

---

### Post by skyesharica on 2014-11-24
> **sudodus said:**
> But you can save your personal files (a partial backup), re-install from a DVD or USB drive, and restore your personal files from the partial backup. This is what many people do.

Great - thanks sudodus - I will try that.  Hope you have a beautiful white Xmas in Sweden.  Ours is stinking hot.  S:  ):P

---

### Post by sudodus on 2014-11-24
Good luck :-)

-o-

I hope we'll get a white Christmas too, but with the global heating, the margin is smaller each year. It is snowing now (wet snow), but this snow might melt away. I hope your weather will not be too hot, and that there will be no bush-fires around your place this year.

---

### Post by skyesharica on 2014-11-24
That's so sweet.  It's more flooding that we are holding out about.  There were a lot of severe tropical floods in our area in the last few years.  This turned into an earthquake in NZ and the Japanese Tsunami.  Weather is everybody's Xmas present this year.  Sorry about your 'snow man melting'.  Maybe Linux will make all the food grow underground, in the Australian desert, one day - wow!  Have to rush off.

---

