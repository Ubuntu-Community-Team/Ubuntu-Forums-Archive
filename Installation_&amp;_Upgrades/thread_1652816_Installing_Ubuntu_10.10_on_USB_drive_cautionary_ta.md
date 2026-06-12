---
title: "Installing Ubuntu 10.10 on USB drive cautionary tale"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by jattman on 2010-12-25
Hello All

Let me tell you tale of woe...

I have XP  installed on my laptop, onto which I've downloaded the 10.10 install ISO  and burned to CD. Re-booted machine with said CD, and then chose to  install ubuntu from it onto a brand new 500GB portable USB drive.  Therefore picked option NOT to install alongside existing operating  system, but as sole new operating system on said hard drive. Everything  seemed to go swimmingly...So excitedly re-booted machine using USB drive  only for it to stop with a cursor flashing in the top left of the  screen :sad:

Then removed USB drive to re-boot back to XP - this time I get a "grub rescue" prompt  :eek: :sad:

Seems  my attempt at an install without touching the internal hard drive has  resulted in the MBR of this hard drive being overwritten. I have looked  at the USB drive, and it does appear to have all of the ubuntu files  installed on it - a little baffled as to why the boot files have been  written to the internal hard drive.

So...problem 1) My laptop is  given to me from my work and so the whole hard disk is encrypted with  Becrypt Disk Protect, which I believe replaces the XP MBR with its own  MBR as it does pre-boot authentication. So I think I'm royally screwed  here - I'll just have to hang my head in shame when I go back to work  and see if work IT support has a tool from Becrypt to re-instate their  MBR. Wont be messing about using my work machine again :rolleyes: !!
2)  Given that I am already screwed with regards to my XP installation, I  might as well try and get my ubuntu install working. Funny thing is that  I tried exactly the same type of install (albeit onto a 8GB pen drive)  using 10.04 a few months ago, and it all worked perfectly. Anybody got  any ideas on what I'm doing wrong?

Cheers

---

### Post by PRC09 on 2010-12-25
I believe there is a spot in the during the install process when you have finished with the partitioning section there is ,under advanced options where you can select which location or drive that you wish to install the bootloader,if you dont select the drive at that point I believe the default is the internal drive ....Been awhile since I have installed 10.10....

---

### Post by searchfgold6789 on 2010-12-25
Yeah, +1 for that. At the last step of the installation process, there is an option (you have to click an "Advanced..." button) to install the bootloader to so-and-so drive. I recommend that you install it to the hard disk with windows on it.
Also make sure your grub configuration files are correct. If you encounter any trouble, post back with the contents of the bootscript (available at sourceforge).

---

### Post by Quackers on 2010-12-25
You can probably fix Windows by repairing the mbr with a Windows repair disc.
Something else you could try is to set your bios so that the usb HDD (with Ubuntu on it) is the first boot device, then see if it boots up.
If neither works please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by jattman on 2010-12-26
Thanks Guys...

I've re-done the install, and now noticed the option for where to put the bootloader - damn, should have seen it first time. With that correctly selected, the install worked and I have a new 10.10 installation on my portable hard drive.

Quackers, thanks for the suggestion about the MBR, but I'm almost certain it won't work because Becrypt needs to have its own bootloader in the MBR so it can do pre-boot authentication, and this is the one I have overwritten. I'm hoping it'll be a case of running a Becrypt utility to re-write the MBR. Won't find out until I get back to work in the new year...

Thanks again ;)

---

### Post by josefnpat on 2010-12-28
Dear Jattman, 


This just happened to me, and not going to lie. Was kinda pissed that I was mislead to believe the bootloader would also be put on the drive I selected. Anyway, easy bloody fix :)

Short and sweet:
    ms-sys --mbr /dev/<device like hda sda>

Long and detailed:
    [http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

---

### Post by Stevens360 on 2011-01-02
i did the same thing but didn't have the ability to recover the mbr from windows so ended up installing windows 7 "YAY" :-( but now when i try to install putting the mbr for ubuntu on the portable where it should be the darned thing hangs on install and doesn't finish 
not sure what the deal is but ill try it agian after i get  this other pc up and running as i don't want to have to reinstall windows agian

---

### Post by GrumpyOleMan on 2011-03-12
Not that this will help a great deal, but I've been fighting this same thing ever since Ubuntu came out with the new GRUB2.  I did the whole thing with no problems with the 7.04 version, and had no reason to do it again until my son told me dad....this thing just corrupts my other installation and doesn't work.  Then I started seeing other references to the same problem.  I have still not found an acceptable solution to this problem, other than to find 7.04, install that one, then upgrade to 10.10.  This is NOT ACCEPTABLE.  

My recommendation until Ubuntu comes out with a system that works for installation other than rip out any other systems you have, is to just load 7.04 which seems to be the last issue that actually worked correctly.  I haven't noticed THAT much difference anyway.:confused:

---

### Post by GrumpyOleMan on 2011-03-27
> **GrumpyOleMan said:**
> Not that this will help a great deal, but I've been fighting this same thing ever since Ubuntu came out with the new GRUB2.  I did the whole thing with no problems with the 7.04 version, and had no reason to do it again until my son told me dad....this thing just corrupts my other installation and doesn't work.  Then I started seeing other references to the same problem.  I have still not found an acceptable solution to this problem, other than to find 7.04, install that one, then upgrade to 10.10.  This is NOT ACCEPTABLE.  

My recommendation until Ubuntu comes out with a system that works for installation other than rip out any other systems you have, is to just load 7.04 which seems to be the last issue that actually worked correctly.  I haven't noticed THAT much difference anyway.:confused:

Since the time I wrote this, I finally got an installation to work on my USB hard drive.  It worked really great until I did the first "update" and did the mandatory reboot to have changes and updates take effect.  It never booted again.  I personally believe that whoever at UBUNTU made the extremely bad decision to be the first and only Linux distro to force people to use Grub 2 should be first horse whipped, then shot, and finally hung until the birds and insects eat ever bit of flesh from his/her bones!  This is the most pi$$ poor boot system I've ever encountered, and I've been doing this since 1970!

---

### Post by Quackers on 2011-03-27
Not a big fan of grub2 then :-)  I am :-) Think it's great, actually.
What was the update or updates that broke grub - if that's what happened?

---

### Post by oldfred on 2011-03-27
I also like grub2. And I like Quackers updated avatar. He now is a little less grumpy.

What does this show?

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by Quackers on 2011-03-27
> **oldfred said:**
> I also like grub2. And I like Quackers updated avatar. He now is a little less grumpy.

What does this show?

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Lol, I just liked the colours of the old avatar. It did look a bit hostile though :-)
BTW congratulations on 10,000 posts! That's a lot! :-)

---

### Post by oldfred on 2011-03-27
Thanks, I did not notice I went over 10K. I knew I was near yesterday but thought it would be a few days.

@ Quackers
Are you cleaning up your act to get the Aflac job? They fired their old duck and are looking for a new one.

---

### Post by Quackers on 2011-03-27
Lol, but what's Aflac? Sorry, I'm in the UK and suspect you are referring to something in the US?
Aha! I googled it. Commercials eh? Is the money good :-)
Do they pay in fish?

---

### Post by oldfred on 2011-03-27
@ Quackers
I did not know a lot of their business is in Japan.

[http://www.ajc.com/business/aflac-seeks-new-spokesduck-883414.html](http://www.ajc.com/business/aflac-seeks-new-spokesduck-883414.html)

---

