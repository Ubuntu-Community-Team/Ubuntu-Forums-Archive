---
title: "Non-destructive install"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by NickFletcherCC on 2010-03-05
Hi all,
 
I have recently purchased an Asus 1008HA with Windows 7 pre-installed. Having no CD drive it comes with the installation media on the hard drive.
 
I wish to give UNR a try but would like to retain the option of reverting to Win 7 in the event that I either dislike it or have hardware issues.
 
All I am after is some measure of assurance that I will be able to do this if I follow the instructions as laid out on the UNR download page.
 
Many thanks for any help you can offer.

---

### Post by tommcd on 2010-03-05
> **NickFletcherCC said:**
> 
All I am after is some measure of assurance that I will be able to do this if I follow the instructions as laid out on the UNR download page.

Perhaps you could post a link to the instructions you are referring to, so we don't have to guess what you are looking at.
Here is the UNR dowload page from Ubuntu.com:
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)
You will need to shrink your Windows7 partition to make room for UNR. There should be an option for this in Windows 7. There is also an option for this on the Ubuntu installer. This will allow you to dual boot both UNR and Windows 7.

And welcome to the Ubuntu forums!

---

### Post by NickFletcherCC on 2010-03-05
> **tommcd said:**
> Perhaps you could post a link to the instructions you are referring to
 
My apologies, the page is here: [http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook). I will have a go at replacing the data partition with a Ubuntu partition as I do not keepany data on that at all. Thanks for the help just want to make sure that there is a way back in case of problems.
 
Thanks for the prompt reply.

---

### Post by SteveTPearce on 2010-03-06
Just in case you're still unsure, I've just done exactly what you're proposing on my (literally) shiny new 1008HA and it works like a charm.
I used the Windows partitioning tool to delete the data partition (why do they *do* that?) and re-size the Windows partition. That left me with a big chunk into which to install Ubuntu.

You have to go into the BIOS (frantically tap F2 on boot) to turn off the Boot-Buster (in the Boot menu), then frantically tap ESC on reboot to select the USB drive to boot.

All you need to remember then is to choose "Install into largest continuous free space" (or whatever it's called) rather than the default "side-by-side" option. Not that I think one could go far wrong without a pair of pliers and a blow torch, anyway;)

I haven't tried booting the windows restore option, but Windows 7 boots perfectly from GRUB. I might be inclined to hide the restore option just in case I get a bit clumsy with the keyboard one day..!

UNR seems much snapper that Windows 7, and I find the default GUI is much more appropriate to the smaller device format than standard Windows. It still has it's place of course (I'm Linux evangelist, not a zealot), but for day-to-day web stuff I doubt Windows will get much of a look in.

Hope it works out as well for you as it did for me...

---

### Post by NickFletcherCC on 2010-03-06
Thanks for the reply, if I can muster the courage to do it I'll have a go tomorrow morning. On the advice of a friend at work I have taken a Norton Ghost image of the drive so with luck there should always be a backout option. From what I have heard so far though I don't expect to be going back to Windows anyway.

---

### Post by tommcd on 2010-03-07
Here is an excellent site for getting started with Ubuntu. Although it deals with Ubuntu desktop version, and not UNR, it is still an excellent resource, and most of it will still be applicable to UNR:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
There is also the eee-user wiki and forum, in case you have not yet seen it. There is a lot of info about linux and Ubuntu there:
[http://www.eeeuser.com/](http://www.eeeuser.com/)
There are also numerous tutorials on installing UNR:
[http://alexsantidote.com/ubuntu/install-ubuntu-904-netbook-remix-dual-boot/](http://alexsantidote.com/ubuntu/install-ubuntu-904-netbook-remix-dual-boot/)
[http://www.jpierre.com/2009/04/installing-ubuntu-netbook-remix-904-jaunty-jackelope-on-eee-pc-the-howto-guide/](http://www.jpierre.com/2009/04/installing-ubuntu-netbook-remix-904-jaunty-jackelope-on-eee-pc-the-howto-guide/)
Write back if you need more help.

EDIT: By the way...
There is no reason that you can not install the standard Ubuntu desktop version on a netbook. Many people do this. You are not locked in to using UNR just because you have a netbook.
You would likely find that UNR is faster and lighter on your netbook, since it designed specifically for netbooks, and the standard Ubuntu desktop version has been getting rather bloated in my opinion, even on a desktop computer.
Many people also say that the UNR desktop interface is more suited to the small screen size of netbooks.

There is also the Moblin linux, developed by Intel for netbooks:
[http://moblin.org/](http://moblin.org/)
And there is Easy Peasey, which is based on Ubuntu, but is designed specifically for netbooks:
[http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)
As you can see, linux is all about choice and freedom. Welcome to the cool side of computing!

---

### Post by NickFletcherCC on 2010-03-07
Many thanks for all the help offered, UNR is now installed and working with no problems at all. I'll give it a try for a couple of weeks and see how I go.

---

### Post by tommcd on 2010-03-08
> **NickFletcherCC said:**
>  UNR is now installed and working with no problems at all. I'll give it a try for a couple of weeks and see how I go.
Glad you got UNR installed ok!
So did you manage to successfully setup a dual boot with UNR and Windows 7? Did everything turn out ok with this?

By the way #2 ....
Here is another excellent and comprehensive site for all things dual booting with Ubuntu:
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)
This site also focuses on dual booting with Ubuntu desktop version and not UNR. This is still a very good resource for anyone using Ubuntu that covers many different dual booting scenarios. I learned a lot from it. The tutorials there on grub-legacy and grub2 (specifically, grub 1.97 on Ubuntu 9.10) are the best grub tutorials I have ever found:
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
That site is maintained by Ubuntu forums member and grub guru Herman:
[http://ubuntuforums.org/member.php?u=31861](http://ubuntuforums.org/member.php?u=31861)

---

### Post by NickFletcherCC on 2010-03-08
> **tommcd said:**
> Glad you got UNR installed ok!
So did you manage to successfully setup a dual boot with UNR and Windows 7? 

 
I decided to take the plunge and go for a single Ubuntu install, but have left the recovery partition in place just in case. So far so good, I have even got my Vodafone Internet dongle working without any problems.

---

