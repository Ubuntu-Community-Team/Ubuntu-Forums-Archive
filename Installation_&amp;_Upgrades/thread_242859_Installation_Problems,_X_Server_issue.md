---
title: "Installation Problems, X Server issue"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by killgoreph on 2006-08-24
Hi all,

I read about Ubuntu in Lifehacker and got intrigued.  So I downloaded the Desktop CD ISO (the AMD64 version) and proceeded with the install.

Booting up and reaching the Ubuntu install menu, i select the first option and it loads.  But before it installs, I get the dreaded "Failed to Start the X server..." message and being a total Linux Distribution Noob don't know how to fix this problem. (I tried to force the installation to use Vesa drivers, but dont know how to proceed when i reach the command line, after inputting video options and other options)  

This is my machine's specs:

Athlon 64 3000+ Venice Core
Epox 9NPA3 Ultra
Gecube ATI X800 GTO 256 mb
1 gb RAM
SATA HDD with Vista Beta 2 installed

P.S. - I did a quick search in the forums but didnt find any quick fix for my problems... I tried to do what was prescribed in these links but don't know how to proceed further...

[http://www.ubuntuforums.org/showthread.php?t=240038&highlight=server+ATI](http://www.ubuntuforums.org/showthread.php?t=240038&highlight=server+ATI)
[http://www.ubuntuforums.org/showthread.php?t=240888&highlight=server+ATI](http://www.ubuntuforums.org/showthread.php?t=240888&highlight=server+ATI)

---

### Post by tseliot on 2006-08-24
Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine. If it doesn't, repeat the process above and use "vga" instead of "vesa"

---

### Post by killgoreph on 2006-08-24
Many thanks for the quick response and i know i will sound like an arse asking this but, what buttons do i need to press to get to recovery mode?  please talk to me like im a 4 year old.  Im really ashamed :confused: for being a total noob.

anyway managed to run the live cd without a hitch on my toshiba m30 satellite laptop... but i want it on my desktop.

---

### Post by killgoreph on 2006-08-24
By the way, I realized that Im not sure what GRUB is... been reading the help docments in Ubuntu.com and is the GRUB the menu when you load up the Live CD? or is it something entirely different something i need to install first prior running Ubuntu installer?

---

### Post by Herman on 2006-08-24
Hello, killgoreph, I'm Herman, I'm run an unofficial website that has a lot of illustrations and comments to help explain things to people. Maybe it can  take some of the load off the experts and save them from the need for lengthy and detailed explanations.

Here's a link to my web page on Xservers, it is just an example of what my own experience was like and some things I googled up. I'm not an expert, just an ordinary user helping out, but you should be able to see from that apporximately what you can expect using sudo dpkg-reconfigure xserver-xorg will be like.
   sudo dpkg-reconfigure xserver-xorg...........................................................................[Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html")
   > what buttons do i need to press to get to recovery mode? > By the way, I realized that Im not sure what GRUB is... been reading the help docments in Ubuntu.com and is the GRUB the menu when you load up the Live CD? or is it something entirely different something i need to install first prior running Ubuntu installer?
           Here's a link to my Grub Page too,                       GRUB Bootloader Page.....................................................................................................[GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")  You won't need to know all that right away, but the Grub Menu is illustrated there in fig1 (the very first illustration you come to).  *If Ubuntu is the only operating system in your computer, the Grub menu might not show*, you computer probably skips it unless you press your 'Esc' key while you computer is booting up. (If I remember correctly).  Hopefuly then you'll see the grub menu and be able to  select  'Recovery Mode' as tseliot is suggesting, it's the second line down, as you can see in that illustration. 

I'm hoping maybe just seeing those illustrations will shed some light on the subject for you, If that doesn't work, or if you have more questions post back for more ideas.

Regards, Herman :D

---

### Post by killgoreph on 2006-08-24
Thanks for the response, Herman, great website! very helpful to noobs like me.

First off, i dont have GNU GRUB installed.  I only got Windows Vista Beta 2 (which i plan to totally switch to ubuntu) in my hard drive and Im not sure how to access and/or install GRUB. I've looked at the GRUB wikis online but there aren't one click installation versions of GRUB. So i guess before anything else, I need to know how one can install GRUB, as explained to a 5 year old.  My knowledge is limited to Windows software.  Anything beyond that is sketchy at best.   

Doh....... might be easier if i buy an nvidia card.  

Btw, After the x server gets disabled in the installation process, i managed to do the changes on the xserver (switching to Vesa, as described by mr. tseliot) and get to the command prompt.  To restart the installation i type in reboot, but  
when the system reboots, my changes arent implemented... :frown:

---

### Post by mgpower0 on 2006-08-24
so are you just trying to run off the live cd at the moment? If so on the boot screen first choose the function button listed down the bottom of the boot screen that allows you to adjust screen resolution and select a lower screen res 1024x720 or less. see if it boots up ok then.

---

### Post by Herman on 2006-08-24
> Btw, After the x server gets disabled in the installation process, i managed to do the changes on the xserver (switching to Vesa, as described by mr. tseliot) and get to the command prompt. To restart the installation i type in reboot, but  when the system reboots, my changes arent implemented... :frown:
What happens when you type the following command?
```
startx
```:D 
> First off, i dont have GNU GRUB installed. I only got Windows Vista Beta 2 (which i plan to totally switch to ubuntu) in my hard drive and Im not sure how to access and/or install GRUB. I've looked at the GRUB wikis online but there aren't one click installation versions of GRUB. So i guess before anything else, I need to know how one can install GRUB, as explained to a 5 year old. My knowledge is limited to Windows software. Anything beyond that is sketchy at best.  I'm sorry, I was presuming you already had Ubuntu installed, and just could not get the xserver to start up when you boot for the first time. Normally, that's the situation. If so, the Ubuntu installer you have would have already installed Grub for you automatically. It's very easy that way, you don't even need to point and click anything. Maybe you already did it and it was so easy you didn't even know it! :D

On re-reading your original post again, I realise now that mgpower0 has picked up on something I missed, are your having trouble at the start of the install process? Or at the end of it? Grub is installed close to the end of the install proces too, so if you are having problems before the install begins then that explains a lot when you say you haven't got Grub installed yet. That would be unusual though.

Also, this how-to might be helpful to you as well, 'DUAL BOOT VISTA and LINUX (Ubuntu 6.06) [B][http://tinyurl.com/hrbhy']("http://tinyurl.com/hrbhy")
[/B] 
Regards, Herman :D

---

### Post by killgoreph on 2006-08-24
Ah yes, that is the case, i haven't installed anything yet as X server fails when I attempt to load Live CD. (by choosing the first option, i get to an ubuntu loading screen, and as it loads X window, i get the x server video issue).  No Ubuntu installed in my Hard disk yet.

Anyway, tried using the command: startx  

After configuring dpkg xserver after changing it to Vesa drivers,and saying yes to everything else, i reached a command prompt and I typed in startx. But it just makes my screen go blank.

---

### Post by killgoreph on 2006-08-24
Yes, i tried using VGA mode too... but the xserver also fails.

anyway, to help illustrate my problem, i made a small and grainy video of my installation process, so hopefully, it can be useful in the diagnosis.

[http://smg.photobucket.com/albums/v731/deckchua/?action=view&current=MOV01220.flv](http://smg.photobucket.com/albums/v731/deckchua/?action=view&current=MOV01220.flv)

What i did here was boot using livecd, ran the installation of ubuntu, failed in x server, did the command dpkg reconfigure, changed to vesa, said yes to a bunch of options. returned to the command prompt. typed in startx.  get a blank screen.  

why does xserver hate ATI so? :biggrin:

---

### Post by Herman on 2006-08-25
>  why does xserver hate ATI so? Well, as you would have seen from my Xserver Page, I also use an ATI card and mine works under the standard ATI driver from Ubuntu, the generic vesa driver, or the special fglrx proprietary driver.
It does not really make sense that a video card would fail to function with a vga or vesa driver even. They wouldn't be able to sell video cards like that, because there would be lots of things like running Live CDs that such a video card would not support. So I imagine it must be some other problem.

killgoreph, did you take the time to run an [md5sum integrity check]("http://www.users.bigpond.net.au/hermanzone/p17.htm#Why_integrity_check_your_downloaded_.iso") on your downloaded .iso file? Sometimes (quite often in fact) the .iso is corrupted during downloading. Also, you should run the 'Check CD for Defects' option from the start menu where you select 'Start Ubuntu' before you boot the Live CD. That should check that there isn't some other defect, like a faulty burn or imperfection on the CD  disk of some kind or  other.  
Obviously, if you do discover a fault with one of those tests, you would either re-download or re-burn the .iso to a new disk, or both.

Otherwise, I can only think that maybe you should give the 'Alternate' Install CD .iso a try instead. (AMD64 version, there should be one available, I think). That often works if the 'Desktop' Install/LiveCD doesn't work for various reasons. 
If you want a preview of what the 'Alternate' install will be like, click on any of my three 'signature links' under this post. Maybe that will get Ubuntu installed and running for you.
Regards, Herman :D

---

### Post by killgoreph on 2006-08-25
I tried to check the cd of the amd64 version ait passed with an OK status.

Anyway, i'm glad to report that the 32bit version worked.  But a bunch of options like networking (im using wifi) is suspiciously missing from the system menu.

But that's for me searching these forums for an answer!

Thanks for all the help guys! i hope that this difficult installation process is not an idication of future painful ubuntu user experience!

---

### Post by susancragin on 2006-08-25
Go to the following

/etc/X11/
sudo nano xorg.conf


down near the end, add the following line:

Option        "MonitorLayout" "LVDS,AUTO"


Close nano (CTL X) and save the file. 

Reboot.

---

