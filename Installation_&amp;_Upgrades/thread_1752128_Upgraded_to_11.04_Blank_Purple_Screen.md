---
title: "Upgraded to 11.04 Blank Purple Screen"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by efituned on 2011-05-07
I upgraded from 10.10 to 11.04 and now I have a blank purple screen. I have searched and went through some of the steps members have been giving, but haven't been able to fix the problem. I can get into the computer going through the grub menu, but when I restart I go through the same problem. Can someone please guide me through step by step?

Here is the computer that I have: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01465973&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&site=null&key=null&product=3740326](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01465973&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&site=null&key=null&product=3740326)

Thanks in advance.

---

### Post by madjr on 2011-05-07
hi,

first i suggest burning a live-cd image or usb with the latest ubuntu and see if everything is working.

if everything seems to work you can let us know.

also it will come in handy in case you want to backup or reinstall.

---

### Post by efituned on 2011-05-07
I burned a cd, just like I did when I first switched to 10.04. I put the cd in and it does the same thing. I even burned a 10.10 cd to see if I could go back and same thing happens.

---

### Post by Blasphemist on 2011-05-07
What have you tried so far? Did you do this yet? This is from [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

> How to temporarily set kernel boot options on an installed OS (not wubi)

To set kernel boot options, you must edit your grub configuration. You can do this temporarily for a single boot by entering the grub menu. If you do not get to see the grub boot menu after the bios automatically, you may have to press SHIFT key after the bios logo to get in to grub:



Select the default ubuntu kernel (usually the top one), and rather than pressing enter, press E to edit.

Press DOWN ARROW until you get to the line that starts with

Code:
linux /boot
and press END keys to position your cursor at the end of the that line usually ending with “quiet splash”. 

Now you can type in additional kernel options like nomodeset (please dont make the same typing error I made for this screenshot  ):

[IMG]http://img26.imageshack.us/img26/3509/dgfdgrunningoraclevmvir.png[/IMG]

press control+X to boot the modified grub entry.

Important: setting boot options this way only applies to a single boot. If you reboot the machine, those settings will be lost, unless you make them permanent (see below)

Or this from here? [http://ubuntuforums.org/showthread.php?t=1743386&page=4](http://ubuntuforums.org/showthread.php?t=1743386&page=4)

> I got it working on mine. I purged all nvidia files and did a command line reintall again, had it save the xconf, restarted, and then opened the compiz fusion icon and made sure it was on "Compiz", then reloaded the file manager.

sudo apt-get remove --purge nvidia*
sudo apt-get install nvidia-current
sudo nvidia-settings

(saved xorg config here, said default device was not a valid field)

sudo update-grub
(had seen that this problem had once in the past been caused by grub booting the wrong kernel)
uname -a
(checked against the new grub file)


and then restarted and ran the "Compiz Fusion Icon" from applications->system tools
in the icon that appeared in the taskbar, i clicked and checked it was on compiz, then had it restart the file manager. It reloaded into Unity, with the side bar, and compiz effects working perfectly. I haven't restarted or anything to see how it works, but at worst I know I can get it to run more than likely by putting the command to reload the manager at startup.

---

### Post by cigtoxdoc on 2011-05-07
The information you gave us on your PC indicated nVidia graphics card.  I had same problem with my PC with nVidia graphics.  You need to use X.org drivers until nVidia driver you need is modified to work with 11.04

John

---

### Post by efituned on 2011-05-07
> **Blasphemist said:**
> What have you tried so far? Did you do this yet? This is from [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)


Or this from here? [http://ubuntuforums.org/showthread.php?t=1743386&page=4](http://ubuntuforums.org/showthread.php?t=1743386&page=4)

I'm trying this now.

> **cigtoxdoc said:**
> The information you gave us on your PC indicated nVidia graphics card.  I had same problem with my PC with nVidia graphics.  You need to use X.org drivers until nVidia driver you need is modified to work with 11.04

John

How do I do this?

---

### Post by efituned on 2011-05-07
How can I just go back to 10.10? This is really making me mad. I tried the nomodeset and when i tried booting, it asked me for my password. I put in the correct one and it kept saying incorrect.

---

### Post by Blasphemist on 2011-05-07
To go back you have to reinstall that version of ubuntu.

At what stage of the boot is it asking for the password? Do you have a different root password than user password?

---

### Post by efituned on 2011-05-07
> **Blasphemist said:**
> To go back you have to reinstall that version of ubuntu.

At what stage of the boot is it asking for the password? Do you have a different root password than user password?

I have tried installing an earlier version, it just goes to the same blank purple screen when use the cd. I am not sure what stage it is asking me for the password. I only have one password for the computer. 

It's also very hard to get to that grub menu by pressing "shift", I think i have restarted my computer about a 1000 times today.

---

### Post by efituned on 2011-05-07
The only way I can get into the computer is get into that menu by hitting "shift" and choosing to use the previous version.

---

### Post by Blasphemist on 2011-05-07
Please try to pass us more detailed and specific information on what you do, what exactly happens, what you see on the screen during the boot, etc. You've posted that you have both a 10.10 cd and a 11.04 cd. And that you started this all moving from 10.10 to 11.4. Did you or anyone else have to do anything at the time of the 10.10 install to resolve this issue? If not, it seems to me that booting to the 10.10 cd should work for you. It it doesn't, just what does happen? When you say you're prompted for a password and it doesn't accept your password, have you tried no password? And what is displayed prior to that prompt?

I'm really just trying to help. We need to be organized and show attention to detail to resolve this. I'm adding a link to the grub 2 documentation thinking maybe you'll see something in it that you have been seeing during these efforts.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by efituned on 2011-05-07
Okay. I turn on the computer. First I see the blue hp screen, then a blinking horizontal cursor, then a blank purple screen. Sometimes if I wait a few minutes the blank purple screen changes to a purple screen with the word ubuntu and five red dots under ubuntu. 

During the start-up if I press "shift" multiple times I get this screen: 
[IMG]http://i413.photobucket.com/albums/pp213/kte324/Misc/IMAG0047.jpg[/IMG]

When I hit "e" for the highlighted one above (which is the same line as the second, just with out (recovery mode)) I get this screen: 
 [IMG]http://i413.photobucket.com/albums/pp213/kte324/Misc/IMAG0048.jpg[/IMG]

---

### Post by Blasphemist on 2011-05-07
OK good, that helps. After you add the nomodeset and press Ctrl/X, what happens during the boot? You said you get prompted for a password. Do you get prompted for a user too or just password. Is there anything else that see from the time you press Ctrl/X until then? Do try no password if needed. Does nomodeset get you any further in the boot than without it? 

There is another option we might try but I would like to keep following on the nomodeset until we are sure it doesn't help. That next option is as follows.

> acpi_osi=
This option frequently solves problems with LCD backlight, fan control problems and misreporting of thermal events. What I understand it does (but corrections are welcome), is prevent the kernel from reporting to the bios that its any windows version the bios asks for. By default, the kernel pretends to be all windows versions, that way we are certain the bios executes all the code needed to initialize the hardware. Unfortunately, some bioses contain fixes to fix problems with specific windows versions (notably vista) that arent needed or dont work for other OS's. Setting
Code:
acpi_osi=
(nothing behind the = sign) as boot option makes the kernel not respond to osi queries.

If the bios has provisions for Linux, you can also try
Code:
acpi_osi="Linux"
Or you can try 
Code:
acpi_osi="Windows 2006"
To make the kernel pretend its vista and make the bios execute routines on machines that require them.

---

### Post by efituned on 2011-05-07
I finally figured out the password. After I did the nomodeset, I put in my password as you can see in the picture and got this: 

[IMG]http://i413.photobucket.com/albums/pp213/kte324/Misc/IMAG0050.jpg[/IMG]

---

### Post by MAFoElffen on 2011-05-07
> **efituned said:**
> I finally figured out the password. After I did the nomodeset, I put in my password as you can see in the picture and got this: 

Well, that is "somewhere."  So far your are booting grub, successfully booting the linux kernel and getting to a text console.  You didn't say "which" nvidia card...

Have you read this sticky?
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Go to post 1 near the end where I have my nvidia notes.  There you will find instructions on installing nvidia-current from console... Or if that doesn't immediately help, . read the first 3 posts.

---

### Post by efituned on 2011-05-07
> **MAFoElffen said:**
> Well, that is "somewhere."  So far your are booting grub, successfully booting the linux kernel and getting to a text console.  You didn't say "which" nvidia card...

Have you read this sticky?
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Go to post 1 near the end where I have my nvidia notes.  There you will find instructions on installing nvidia-current from console... Or if that doesn't immediately help, . read the first 3 posts.

Looking at the end of your first post, I am guessing you want me to try the part that titles: [B]Notes about nvidia cards and SL. 

[/B]Where do I add the word "text"? Do I still do the nomodeset thing or do I skip that part? Or do I put the word "text" instead of nomodeset?

---

### Post by diamond_D on 2011-05-07
I'm getting the same problem.

I just performed the network upgrade from 10.10 to 11.04.

I rebooted and initially was able to start properly and get to my desktop.

I then cloned a few of my partitions using the clonezilla live CD.

Rebooted again and it gets to the logon screen. I enter my password and it just hangs at the "purple screen". I tried rebooting a few times and at one point I got a black screen with a dump of data on it. A few of the messages that stand out are:

> udevd-work[86]: inotify_add_watch(6, /dev/sda5, 10) failed: No such file or directory> init: ureadahead main process (344) terminated with status 5> 101.540200] BUG: unable to handle kernel paging request at ffffc900119048a8
My /dev/sda5 is an LVM partition. I have to sata disks containing a mix of standard partitions and LVM volumes.

I'll post if I find anything to get it working. I've only been working with Linux and Ubuntu for about 6 months and this is my first major issue so it should be a great learning experience on how to fix a broken system. I'd appreciate a few tips. I'm downloading the live CD as we speak.

---

### Post by MAFoElffen on 2011-05-07
> **efituned said:**
> Looking at the end of your first post, I am guessing you want me to try the part that titles: [B]Notes about nvidia cards and SL. 

[/B]Where do I add the word "text"? Do I still do the nomodeset thing or do I skip that part? Or do I put the word "text" instead of nomodeset?
yes, that part... Basically, on nviidia cards, you need to intially boot up with a nomodeset, to turn off kms long enough to boot and install nvidia-current.  Once nvidia-current is installed and you then run nvidia-xconfig, that "should" be it.

There is instructions there on how to do it from the commandline.  

Note: There is currently some other challenges going on with some things... If that doesn't help things out... Tell me and we'll work through that.

@diamond_D:
You have problems going on that "are" different than "efituned".  Please post the results of the bootdisk script from my sig.  Press the " # " button and paste the results within the code tags.

---

### Post by efituned on 2011-05-07
Well now I have ran into another problem. The computer is like froze up, I can not do anything once I get to the menu after hitting "shift". I have tried restarting the computer multiple times, but it's like the keyboard doesn't work once the menu pops up. I know my keyboard is working, because it is recognizing the "shift".

***EDIT

I just tried starting the computer, with out pressing anything on the keyboard and the menu popped up on its own. Weird. So what now?

***EDIT again..
Unplugged the keyboard, started the computer, got the menu screen. Plugged the keyboard in while on the menu screen and I can now hit "e".

---

### Post by MAFoElffen on 2011-05-07
> **efituned said:**
> Well now I have ran into another problem. The computer is like froze up, I can not do anything once I get to the menu after hitting "shift". I have tried restarting the computer multiple times, but it's like the keyboard doesn't work once the menu pops up. I know my keyboard is working, because it is recognizing the "shift".

***EDIT

I just tried starting the computer, with out pressing anything on the keyboard and the menu popped up on its own. Weird. So what now?

***EDIT again..
Unplugged the keyboard, started the computer, got the menu screen. Plugged the keyboard in while on the menu screen and I can now hit "e".
LOL... so far so good.


Edit-- Know how you feel. Wires hanging on my own keyboard, but I just "love" this one! Wiggling wire every once in a while.  Should fix it some day, but...

---

### Post by efituned on 2011-05-07
> **MAFoElffen said:**
> LOL... so far so good.


Edit-- Know how you feel. Wires hanging on my own keyboard, but I just "love" this one! Wiggling wire every once in a while.  Should fix it some day, but...

I wish I had wires, the wireless keyboard is bs. Okay, so I did nomodeset, then got here:
[IMG]http://i413.photobucket.com/albums/pp213/kte324/Misc/IMAG0051.jpg[/IMG]

---

### Post by MAFoElffen on 2011-05-07
[QUOTE=efituned;10784581..then got here:
[/QUOTE]
```

sudo service gdm start

```Or 
```

sudo reboot

```Or just plain reboot it.  Meaning, try it and see what is does(?)

My burning question at the moment is... Is this comming up into a text console by your choice or not?

---

### Post by efituned on 2011-05-07
I did and it went right back to the blank purple screen after the blinking horizontal cursor.

---

### Post by MAFoElffen on 2011-05-07
> **efituned said:**
> I did and it went right back to the blank purple screen after the blink horizontal cursor.
So let's review... You have an Nvidia 9500GS right?

When you add nomodeset and when you boot it boots the kernel, but it "errors out" to the text console. Right?  

Then you installed the nvidia drivers and locked up in purple screen right?

Next 2 things to try:

1.  At the grub boot menu > edit > add to kernel boot line: " nomodeset vmalloc-192MB " and see if that works.

2, If not, try a different kernel... see post 2 here:[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by efituned on 2011-05-07
> **MAFoElffen said:**
> So let's review... You have an Nvidia 9500GS right?

When you add nomodeset and when you boot it boots the kernel, but it "errors out" to the text console. Right?  

Then you installed the nvidia drivers and locked up in purple screen right?

Next 2 things to try:

1.  At the grub boot menu > edit > add to kernel boot line: " nomodeset vmalloc-192MB " and see if that works.

2, If not, try a different kernel... see post 2 here:[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I tried the first thing you said and it went back the blank purple screen after it reboot. I don't even know where to begin in your post 2. 

How can I just go back to 10.10? Because I think trying to upgrade to this is beyond my level of experience. I don't mind loosing all my stuff as I have everything I need backed up on my external drive.

---

### Post by MAFoElffen on 2011-05-07
> **efituned said:**
> I don't even know where to begin in your post 2.
Lets make this really simple...

I'll give you the commandline commands, but first I need to know if you are 32bit or 64bit...

**EDIT** -- No answer so I'll just do for all;

If you could start in safe mode (low res) from the rescue mode option of grub menu:
Start Synaptic Package Manager > Settings > Repositories > Updates Tab > select the "Pre-released Updates (natty proposed) checkbox and close that dialog box.

Select the Reload button.

Select filter "Origin" > Select  "natty proposed maiin" > select package "linux-image-generic"

Current is 2.6.38.8.22, proposed is 2.6.38.9.23.

If you can't start any GUI in any mode...

**32bit**:
Download and install these 3 files in order:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37.6-natty/linux-headers-2.6.37-02063706_2.6.37-02063706.201103281005_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.37.6-natty/linux-headers-2.6.37-02063706_2.6.37-02063706.201103281005_all.deb")
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37.6-natty/linux-headers-2.6.37-02063706-generic_2.6.37-02063706.201103281005_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.37.6-natty/linux-headers-2.6.37-02063706-generic_2.6.37-02063706.201103281005_i386.deb")
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37.6-natty/linux-image-2.6.37-02063706-generic_2.6.37-02063706.201103281005_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.37.6-natty/linux-image-2.6.37-02063706-generic_2.6.37-02063706.201103281005_i386.deb")

**64bit**:
Download and install these files in order:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-natty/linux-headers-2.6.37-020637_2.6.37-020637.201101050908_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.37-natty/linux-headers-2.6.37-020637_2.6.37-020637.201101050908_all.deb")
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-natty/linux-headers-2.6.37-020637-generic_2.6.37-020637.201101050908_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.37-natty/linux-headers-2.6.37-020637-generic_2.6.37-020637.201101050908_amd64.deb")
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-natty/linux-image-2.6.37-020637-generic_2.6.37-020637.201101050908_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.37-natty/linux-image-2.6.37-020637-generic_2.6.37-020637.201101050908_amd64.deb")

(I know these older kernels have been working for natty, when other haven't)

Then after its installed, try to boot with the GUI.  If success, I would go to Sysnaptic and follow the instructions above to install the proposed to see if that works for you.

Why "madjr" asked below?  Because they made kernel/kms changes to improve the way Graphics displayed and for performance.  (Not me)  I'd say their still working on that... (As by the proposed kernel fixing some of those problems).  Just newer technology.

---

### Post by madjr on 2011-05-07
i find it weird that you are having these problems if 10.10 worked fine before.

---

### Post by MAFoElffen on 2011-05-07
> **madjr said:**
> i find it weird that you are having these problems if 10.10 worked fine before.
I've been helping people with these same problems since 10.04... just more with each newer release.  

At 10.04, Ubuntu implemented KMS, which now takes the graphics mode from the kernel and passes it to Xorg.  

Which in English means that "before" the kernel booted and then the Graphics Session started and  it used the Video Driver to find the resolution <> Since KMS, it finds and sets the graphics resolution by setting the kernel boot & setting the kernel from a mode found by grub, which then gets passed unchanged to the graphic session to use.

10.04 and 10.10 set it in the kernel.  Finds and sets as soon as from grub. (GNU Grub 1.99)  

Notice with Natty that they've been pushing the envelop a little more with graphics, even as soon as the Grub boot menu and the kernel boot?
I don't think they've worked out all the details yet --or-- I would not have so many people to help working these issues out now.

---

### Post by efituned on 2011-05-08
What do I do after I select this package?  select package "linux-image-generic"

I am in the process of downloading those three things. I am 32-bit.

---

### Post by MAFoElffen on 2011-05-08
> **efituned said:**
> What do I do after I select this package?  select package "linux-image-generic"
If you did this way, (after selecting the proposed repo)... then you would right-click on that package and mark as upgrade, then apply.

> **efituned said:**
> I am in the process of downloading those three things. [COLOR=Red]I am 32-bi[/COLOR]t.You woold not need this if you updated the above first.  But it you couldn't do the above update, you would install these files you downloaded... such as by:
```

sudo dpkg -i /path_to/package_name.deb

```in the order in that post.

This has been helping 32bit users.

---

### Post by efituned on 2011-05-08
> **MAFoElffen said:**
> If you did this way, (after selecting the proposed repo)... then you would right-click on that package and mark as upgrade, then apply.

You woold not need this if you updated the above first.  But it you couldn't do the above update, you would install these files you downloaded... such as by:
```

sudo dpkg -i /path_to/package_name.deb

```in the order in that post.

This has been helping 32bit users.

Okay, I tried that package again, then restarted the computer and went straight to the grub menu. So I'm guessing that doesn't work. 

Then I tried entering that you wrote above in the terminal and I got some error message. So I must be doing that wrong. Where do I go now? 

All I need is an undo button, because my computer has been down for about a week now and this sucks. At the beginning I thought switching to ubuntu from windows 7 was a good idea, but has been nothing but problems.

---

### Post by MAFoElffen on 2011-05-08
> **efituned said:**
> Okay, I tried that package again, then restarted the computer and went straight to the grub menu. So I'm guessing that doesn't work. 

Then I tried entering that you wrote above in the terminal and I got some error message. So I must be doing that wrong. Where do I go now? 

All I need is an undo button, because my computer has been down for about a week now and this sucks. At the beginning I thought switching to ubuntu from windows 7 was a good idea, but has been nothing but problems.
I wish I could just be there to see what is going on and try to fix it.

Post the results of this:
```

sudo hwinfo --framebuffer

```
```

sudo hwinfo --monitor

``````

xrandr

```and
```

xrandr -q

```

---

### Post by efituned on 2011-05-08
I inserted a 10.04 cd and completed the installation. After the installation was completed it asked me to restart. The cd tray opened and I took the cd out and hit enter and the computer began to restart. After I saw the blinking horizontal cursor, it went away and my monitor says no signal, like the computer is off or something. 

So I thought maybe it messed up somewhere during the installation and tried it again and the same thing happened.

---

### Post by efituned on 2011-05-08
Am I just doing everything wrong? This is ridiculous.

---

### Post by MAFoElffen on 2011-05-08
> **efituned said:**
> Am I just doing everything wrong? This is ridiculous.
LOL- No..... Remember, the support for your video chipset wasn't added until the recent kernels.  I know this is frustrating though.  Got me pulling my hair out.

Since you now have both disks, You can try to install Natty, then purge the grub (1. v99 ) and install the grub from Maverick ( v1.98 )... That should have the same affect of using natty with a diffrent kernel... Meaning Grub and the kernel will stop passing the bad parmeter that is causing the graphics lockup from being passed and try to let the Graphics session figure it out on it's own.

Here's a good post on how to do that:
[http://ubuntuforums.org/showpost.php?p=10778491&postcount=55 ]("http://ubuntuforums.org/showpost.php?p=10778491&postcount=55")

-- OR --
You could startup Maverick into a text console and do
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```And boot off one of the older kernels in the (then newer) matty grub menu.

---

### Post by madjr on 2011-05-08
the possibility of a hardware problem should not be discarded.

i have an nvidia 8400 desktop and nvidia G210m laptop, and everything seems to be working ok.

also you mention that booting on the live desktops from the CDs everything is ok, but once installed is when the problems start?

have you tried reseting your bios to defaults?

this is probably one of the weirdest cases i've seen. Have you opened a bug report on launchpad?

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by efituned on 2011-05-09
> **MAFoElffen said:**
> LOL- No..... Remember, the support for your video chipset wasn't added until the recent kernels.  I know this is frustrating though.  Got me pulling my hair out.

Since you now have both disks, You can try to install Natty, then purge the grub (1. v99 ) and install the grub from Maverick ( v1.98 )... That should have the same affect of using natty with a diffrent kernel... Meaning Grub and the kernel will stop passing the bad parmeter that is causing the graphics lockup from being passed and try to let the Graphics session figure it out on it's own.

Here's a good post on how to do that:
[http://ubuntuforums.org/showpost.php?p=10778491&postcount=55 ]("http://ubuntuforums.org/showpost.php?p=10778491&postcount=55")

-- OR --
You could startup Maverick into a text console and do
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```And boot off one of the older kernels in the (then newer) matty grub menu.

I am going to try this when I get home tomorrow night from work. Please don't give up on me. 

I am going to burn two new cd's tomorrow at work with 10.10 and 11.04. Is there a certain way I should be making these cd's instead of just going to the website and clicking download. I hear people talk about livecds, is that what I am making?

---

### Post by madjr on 2011-05-10
> **efituned said:**
> I am going to try this when I get home tomorrow night from work. Please don't give up on me. 

I am going to burn two new cd's tomorrow at work with 10.10 and 11.04. Is there a certain way I should be making these cd's instead of just going to the website and clicking download. I hear people talk about livecds, is that what I am making?

yes, you can also create live-usb.

and dont worry, we dont give up on anyone here :)

---

### Post by brian70809 on 2011-05-11
So I went through this whole thing.. and what worked for me..

I have a Toshiba I7 Laptop with an Nvidia320M video..

Went into safemode.. got to basic graphics environment..

Downloaded latest NVIDIA driver from NVIDIA website..  Shut down Xterm..   in terminal

sudo stop service gdm

when to my Nvidia file in the Downloads folder..

sudo sh NVIDIA*..   whatever the file name is..

let it redo my Kernel, and xconfig, etc..

reboot

and I'm up and running..

The Nvidia-current, etc.. did not work for me at all.

Good Luck!

---

### Post by efituned on 2011-05-11
> **brian70809 said:**
> So I went through this whole thing.. and what worked for me..

I have a Toshiba I7 Laptop with an Nvidia320M video..

Went into safemode.. got to basic graphics environment..

Downloaded latest NVIDIA driver from NVIDIA website..  Shut down Xterm..   in terminal

sudo stop service gdm

when to my Nvidia file in the Downloads folder..

sudo sh NVIDIA*..   whatever the file name is..

let it redo my Kernel, and xconfig, etc..

reboot

and I'm up and running..

The Nvidia-current, etc.. did not work for me at all.

Good Luck!

I will try that when I can get into the computer. 

Well I made two cd's 11.04 and 10.04LTS. I used the 10.04 first and I can complete the installation, but the problem is when I try and reboot the computer after the installation has been completed. I get passed the blue hp screen, then it goes to the blinking horizontal cursor screen, but after that my monitor says no signal as if the computer is turned off or something. 

So I try the 10.04 cd again and I can go through the whole installation process, but it does the same thing when I try and reboot. 

Then I try the 11.04 cd and it doesn't recognize the cd at all and does the same as if I was rebooting after the installation of 10.04.

---

### Post by efituned on 2011-05-11
After installing the 10.04 and not being able to reboot. I can get into the grub menu, I try booting in recovery mode and it still does the same thing. So then I press "e" while in the grub menu and add "nomodeset" to the end of kernel line and hit ctrl+x. The computer then goes to a blinking horizontal cursor, then to a purple screen with ubuntu and fiver red dots under ubuntu. Also while on that screen my Caps and Scroll Lock light on my keyboard is flashing.

---

### Post by erick404 on 2011-05-14
I got a similar problem. After inserting nomodeset in grub, Ubuntu started booting, and came to a screen where some checks were made (starting Apache, etc.)
Then it hung up on the line reading "Checking battery status..."

I have no idea why this happpens, Maverick run without problems.

---

### Post by MAFoElffen on 2011-05-14
> **erick404 said:**
> I got a similar problem. After inserting nomodeset in grub, Ubuntu started booting, and came to a screen where some checks were made (starting Apache, etc.)
Then it hung up on the line reading "Checking battery status..."

I have no idea why this happpens, Maverick run without problems.
Okay then... By the stepss.
```

cd /etc/default/
sudo gedit grub

```
Got to line
```

# GRUB_GFXMODE=640x480

```
Change to
```

GRUB_GFXMODE=640x480x24

```
Go the end and add a line that says
```

GRUB_GFXPAYLOAD=text

```
Save file. Close gedit. 
Run
```

sudo update-grub
sudo reboot

```
Tell me if it works.

---

### Post by erick404 on 2011-05-15
> **MAFoElffen said:**
> Okay then... By the stepss.
```

cd /etc/default/
sudo gedit grub

```
Got to line
```

# GRUB_GFXMODE=640x480

```
Change to
```

GRUB_GFXMODE=640x480x24

```
Go the end and add a line that says
```

GRUB_GFXPAYLOAD=text

```
Save file. Close gedit. 
Run
```

sudo update-grub
sudo reboot

```
Tell me if it works.

I actually can't do that. I'm using my Windows installation on this machine, I can't do anything in Ubuntu. It freezes on "checking battery status".

---

### Post by MAFoElffen on 2011-05-15
> **erick404 said:**
> I actually can't do that. I'm using my Windows installation on this machine, I can't do anything in Ubuntu. It freezes on "checking battery status".
1.  Do you have a Natty 11.04 LiveCD?
2.  Can you boot a LiveCD into any graphics mode?
3.  Can you boot a LiveCD into a text console mode?

If 2 or 3, you could use those instruction after a mount.

If not, you could use the LiveCD as a diagnostics tool to figure out what you need to succesfully boot the kernel or (later) a graphics session.

Instructions for "all" of those scenarios are in that sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
The where to go with it is based on the flowchart.

---

### Post by erick404 on 2011-05-15
> **MAFoElffen said:**
> 1.  Do you have a Natty 11.04 LiveCD?
2.  Can you boot a LiveCD into any graphics mode?
3.  Can you boot a LiveCD into a text console mode?


It's not getting any good... I tried to boot with 11.04 LiveCD, and it froze on the purple screen with the symbol (a battery?) and a human figure.

Come to think of it, I had some problems installing 10.10 from the LiveCD. I installed 10.04 first and then upgraded.

---

### Post by MAFoElffen on 2011-05-15
> **erick404 said:**
> It's not getting any good... I tried to boot with 11.04 LiveCD, and it froze on the purple screen with the symbol (a battery?) and a human figure.
LOL!!! That's a keyboard and human icon, asking for any "input"...

Press <Esc> then follow the instructions in this post (with pictures):
[http://ubuntuforums.org/showpost.php?p=10740097&postcount=3](http://ubuntuforums.org/showpost.php?p=10740097&postcount=3)
To use a "nomodeset" to start...

---

### Post by erick404 on 2011-05-15
> **MAFoElffen said:**
> LOL!!! That's a keyboard and human icon, asking for any "input"...

Press <Esc> then follow the instructions in this post (with pictures):
[http://ubuntuforums.org/showpost.php?p=10740097&postcount=3](http://ubuntuforums.org/showpost.php?p=10740097&postcount=3)
To use a "nomodeset" to start...

Yeah, I knew I should hit any key, but it didn't answer. Complete freze. However, I found that with the 10.04 CD, it works. I'm gonna try this.

---

### Post by MAFoElffen on 2011-05-16
> **efituned said:**
> The only way I can get into the computer is get into that menu by hitting "shift" and choosing to use the previous version.
Good, now you can get to the grub menu...

Please refer to this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Shortcut for you:
Now select the recovery mode from the boot menu> select safe mode (low graphics)
If it boots > select system > administration > find additional drivers

If it doesn't boot into a graphical desktop,
Reboot > Press shift to get back to the Grub Menu >
press "e" to get into an edit mode in the grub menu item >
Go down to the line that starts with "linux"
remove the end of that line that says
```

 quiet splash vt.handoff=7

```and replace with 
```

 nosplash --verbose nomodeset text

```Hit <cntrl><x> and it will try to boot into a text console > It will have verbose kernel messages turned on, so you can confirm that it is either not booting at an error or booting successfully...

If successful >
Enter userid and password >
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
cd /etc/default/
vi grub

```Go down to the line that says
```

# GRUB_GFXMODE=640x480

```And change to say
```

GRUB_GFXMODE=640x480x24

```Then add a line that says
```

GRUB_GFXPAYLOAD=text

```Save and exit.
Then run
```

sudo update-grub
sudo apt-get install nvidia-current
sudo nvidia-xconfig
sudo reboot

```Which should put the graphics mode of gnu grub 1.99~rc1 back to the same mode it is in 10.10, boot the current natty kernel in that same mode, install your nvidia drivers and confiure xorg for them...

Hope this info was helpful...

---

### Post by erick404 on 2011-05-17
I can't figure out how to solve my problem. I tried editing the line in GRUB, adding "nosplash --verbose nomodeset text", and again it froze when checking battery status.

I tried booting from 10.04 LiveCD (10.10 and 11.04 CDs freeze in my machine, I don't know why), and it went until the point with the Ubuntu name above five dots. After that, black screen.

I can only suppose that the new changes in how Ubuntu deals with graphic cards were only bad to my hardware.

---

### Post by madjr on 2011-05-18
> **erick404 said:**
> I can't figure out how to solve my problem. I tried editing the line in GRUB, adding "nosplash --verbose nomodeset text", and again it froze when checking battery status.

I tried booting from 10.04 LiveCD (10.10 and 11.04 CDs freeze in my machine, I don't know why), and it went until the point with the Ubuntu name above five dots. After that, black screen.

I can only suppose that the new changes in how Ubuntu deals with graphic cards were only bad to my hardware.

10.04 wont boot either?

you should let the developers know about this:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by erick404 on 2011-05-18
> **madjr said:**
> 10.04 wont boot either?

you should let the developers know about this:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

In fact it did boot in graphic mode, but not in text mode. Weird.
And when running from the CD, my wireless card didn't work.

---

### Post by efituned on 2011-05-25
So I gave the computer a break for a few weeks and have been using my laptop. 

I started it back up on the newly installed 10.04 and I had the same problem of no signal displayed on my monitor while using a hdmi cable. Then I switched to the regular blue monitor cable and everything works fine. 

Now that I have the computer up and running I really would like to upgrade to 11.04 if I can get it to work. The graphics car I have is a Nvidia 9500GS. Until I get a solution or an easier, more understanding way than the last time I will continue to use what I have.

---

