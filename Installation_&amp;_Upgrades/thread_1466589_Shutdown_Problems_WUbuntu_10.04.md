---
title: "Shutdown Problems W/Ubuntu 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by RichardSM on 2010-04-30
:confused:Is it I!. the only person with a shutdown problem with Ubuntu 10.04 this is day two for me and nobody yet has a shutting problem.See the thread I posted on day one. Thanks

My system is.

AMD Athlon 1400 Thunderbird
MSI Mother Board
GeForce 6200 256Kb
Ram 512Kb
52x33x52x CD Writer
350W Power Supply
Microsoft Wheel Mouse Optical 1.1A USB
Tower Case

Hello this was the fix for me give it a try.Just for the record I downloaded the latest copy of Ubuntu 10.04LTS and did all the updates too. Be sure save after change, to update sudo update-grubsome users have found a permanent tweak:

sudo gedit /etc/default/grub

change : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

by : GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"

may not work for everyone

--------------------------------------------------------------------------------
Last edited by RichardSM; 1 Day Ago at 06:22 AM.. Reason: Solved

---

### Post by sfarthing on 2010-04-30
I'll try and find your other thread.  U 10.04 won't shutdown for me.  Just goes to the login screen.

---

### Post by RichardSM on 2010-04-30
***[SIZE="2"]Sfarthing:[/SIZE]***
If you'll look in the Ubuntu Fourm under Installations & Upgrades or in New Posts for ***-Search-*** ***Shutdown Problems ***you will my other posted thread.

My system is.

AMD Athlon 1400 Thunderbird
MSI Mother Board
GeForce 6200 256Kb
Ram 512Kb
52x33x52x CD Writer
350W Power Supply
Microsoft Wheel Mouse Optical 1.1A USB
Tower Case

Hello this was the fix for me give it a try.Just for the record I downloaded the latest copy of Ubuntu 10.04LTS and did all the updates too. Be sure save after change, to update sudo update-grubsome users have found a permanent tweak:

sudo gedit /etc/default/grub

change : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

by : GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"

may not work for everyone

--------------------------------------------------------------------------------
Last edited by RichardSM; 1 Day Ago at 06:22 AM.. Reason: Solved

---

### Post by maburger on 2010-05-01
I am having the same issues.  It will not shutdown, it just goes to the login screen.  I am also having issues remaining connected to my home wifi network using WPA.  It keeps disconnecting and/or not picking up an IP address.  Wifi router is a generic Linksys WRT54GS.  Both problems were not present in beta2.

---

### Post by mbuller10 on 2010-05-02
I'm also having the exact same shutdown problem please help, it will shut down if on briefly but if my comp has been on for a while it won't shutdown or restart

---

### Post by showgun22 on 2010-05-03
same thing here here every once in a while my computer will not shutdown or restart.
IN my case I have identify my culprit seems to be Ooo quick starter if the shutdown does not work all I have to do is exit quick starter and shutdown and it works just fine

---

### Post by nitstorm on 2010-05-03
ubuntuforums.orgubuntuforums.org/newreply.php
Tried the command line for that?

for shutting down instantly:
```

sudo shutdown -P now
(or)
sudo poweroff

```

and for restart
```

sudo reboot

```

---

### Post by sveicken on 2010-05-03
> **showgun22 said:**
> same thing here here every once in a while my computer will not shutdown or restart.
IN my case I have identify my culprit seems to be Ooo quick starter if the shutdown does not work all I have to do is exit quick starter and shutdown and it works just fine

I have the same problem. But your hint (Ooo quick starter) works for me too! When I exit the quick starter, then I can shutdown the computer. Thanks for that hint. 

But: Whats wrong there? Something between Ooo quickstarter and ubuntu-shutdown?

Thanks for help. 

Sudo shutdown -P 0 ... works every time.

Sven

---

### Post by dino99 on 2010-05-03
some users have found a permanent tweak:

sudo gedit /etc/default/grub

change : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

by : GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"

may not work for everyone

---

### Post by sveicken on 2010-05-03
> **dino99 said:**
> some users have found a permanent tweak:

sudo gedit /etc/default/grub

change : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

by : GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"

may not work for everyone


I already tried it with "quiet splash acpi=force" but it doesn't work. Shout it work with "quiet acpi=force" (without "splash")?

Sven

---

### Post by alh on 2010-05-03
Same problem. Upgraded from karmic and have a shutdown problem intermittantly. When it wont shutdown via the menu it will on the power button on the computer as I have set that up in preferences. Might try the suggestion of stopping 'Oo quickstarter' and see if that helps.
Also when logging on a different user the keyboard sometimes won't work. I get round it buy unplugging and replugging the keyboard.
Just some frustrating stuff which is disapointing after the flawless performance of karmic. I wanted to get the latest LTS version so I would not have to worry about upgrades every six months. Should not rush things to meet a time table IMHO.:(

---

### Post by Bas232 on 2010-05-04
Doesn't work here either, nor does init 0
Last message (without splash) is power down but nothing happens after that, it just locks rock-solid.
Nor does sudo shutdown -P 0, same solid lock after power down message.

---

### Post by pete1983 on 2010-05-04
I have found that my video card was the problem.
 1) system 
 2)Administration 
 3)Hardware drivers 
 4)select a different NVIDIA driver or deactivate NVIDIA driver and        try to power off. This worked for me I switched drivers.
  
  If all else fails
  sudo poweroff worked for me as well.

---

### Post by Charlotte18 on 2010-05-05
It seems to me that various users have a problem shutting down from the GUI.  Ubuntu 10.04 has a bug.  From time to time, when someone chooses to shutdown, restart, or log off from the panel, nothing happens.

---

### Post by Merovius on 2010-05-05
Exact same issue here on my old Dell D600 laptop. Just goes to the login screen and sits there. ATI mobility video. No drivers listed in hardware drivers.

---

### Post by RichardSM on 2010-05-06
Sorry I have been out of town for the last week. Well I tried this to and it still did not shutdown all the way it still hangs at the splash screen, 10.04 LTS needs a lot work yet to solve these problems I even tried some of the fixes from 9.10 as well none of them worked either the shutdown issues Ubuntu has with shutting goes all the way back to 9.04 it seems like the folks in the UK needs to address this ***[SIZE="5"]PROBLEM[/SIZE]***.

---

### Post by danhrainey on 2010-05-06
I also had the shutdown problem. I disabled auto login in and that corrected my issue.
System
Administration
Login Screen

Drainey

---

### Post by JayPeters on 2010-05-06
I tried different suggestions, but none worked.*

I ended up doing a clean installation.

*I did not try turning off the automatic login.

---

### Post by alh on 2010-05-07
I had the same problem and killed the openoffice quickstarter (stop it from loading in pref or disable in system start programs section) and have had no problems since. Worked for me.

---

### Post by words1 on 2010-05-07
> **sveicken said:**
> I have the same problem. But your hint (Ooo quick starter) works for me too! When I exit the quick starter, then I can shutdown the computer. Thanks for that hint. 

But: Whats wrong there? Something between Ooo quickstarter and ubuntu-shutdown?

Thanks for help. 

Sudo shutdown -P 0 ... works every time.

Sven

Same here -- it was driving me crazy, but I disabled Open Office quickstart and no more problems.

---

### Post by jvbn on 2010-05-07
Well, I am having the same shutdown problem and even if by using some of the commands suggested I do finally succeed in shutting down my PC, I guess that should not be the way to do it all the time. So, I suppose that there is a little bug in Ubuntu 10.04, which should be fixed.

---

### Post by Eliot Rosewater on 2010-05-08
I'm having a shutdown problem too. Instead of shutting down and powering off my computer just restarts instead.

I've tried the command line alternatives, such as
```
# shutdown -P now
# poweroff
```

but the same problem occurs: my computer just restarts.


There's a bug report here, by the way: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/552316](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/552316)

---

### Post by RichardSM on 2010-05-08
> **sveicken said:**
> I already tried it with "quiet splash acpi=force" but it doesn't work. Shout it work with "quiet acpi=force" (without "splash")?

Sven

Yes give it a try and see if it works for you just remove the word ***[COLOR="Red"]Splash[/COLOR]*** Remember to update [COLOR="red"]***sudo update-grub***[/COLOR]

---

### Post by swadrob on 2010-05-12
My problem is similar to others mentioned as 10.04 shuts down ok but then immediately restarts. I can only shut down by by holding the on/off button. I upgraded from the previous ubuntu system 9.10

---

### Post by usion1977 on 2010-05-12
well I'm no ubuntu expert but the fix for me was uninstalling Ubuntu Tweak. I read there are some bugs in the latest Ubuntu tweak and Ubuntu 10.04. Not sure if the bugs are related but just thought I would put my 2 cents in.
thanks

---

### Post by usion1977 on 2010-05-12
Well sorry for the previous post. It was not ubuntu tweaks that did it for me. I forgot I also changed the Nvidea driver at the same time that I uninstall ubuntu tweaks. So it was the nvidea driver for me that was stopping ubuntu from restarting. When I tried to restart it would always go back to the login screen. Sorry for the confusion.
thanks

---

### Post by Eliot Rosewater on 2010-05-12
All suggestions are appreciated usion1977 :)

As was pointed out on the bugs page, there are too separate issues here. One group of people can't restart/shutdown, while for the other group, whenever they want to shutdown Ubuntu just restarts.

Unfortunately I've found no fix for this.

EDIT I got a new new kernel, -22-generic, but it still doesn't work.

---

### Post by Sigma1 on 2010-05-13
I too was unable to shutdown. Choosing "Shutdown" simply had no effect at all (likewise for "Reboot"). Killing the OpenOffice quickstarter seems to work. Is there someway of including this kill command as an option with the default GUI "Shutdown" command? (And, where do the commands associated with the graphic Shutdown menu hide?)
Thanks for any hints.

---

### Post by rdh61 on 2010-05-14
> **alh said:**
> I had the same problem and killed the openoffice quickstarter (stop it from loading in pref or disable in system start programs section) and have had no problems since. Worked for me.

Hi, not quite with you. Could you spell out for me in baby language how to stop or disable openoffice quickstarter? Thanks

---

### Post by showgun22 on 2010-05-14
Just click on the open-office quickstarter icon and select disable systray quickstarter

but you can also simply exit it when the shutdown does not work

---

### Post by rdh61 on 2010-05-15
Thanks!

---

### Post by Sigma1 on 2010-05-16
Hi. I agree that you can just quit the quickstarter first, via the panel, then exit. It would be nice, though, if the GUI shutdown command forced quickstarter to exit, without having to work through things in two stages. Now, what I don't understand is how the command invoked by GUI shutdown differs from the command-line "halt" or "shutdown -P 0". The first obviously bugs because of OO Quickstarter, the second doesn't. If it were possible to personalise the command invoked by GUI shutdown, it ought to be possible to force the quickstarter to quit.
Hope things are clearer now!
(It's not a big bug, admittedly!)

---

### Post by badaveil on 2010-05-16
My dual boot office HP notebook (forgot what model, I'll check later) works fine with Ubuntu 9.10 but after a fresh installation of Ubuntu 10.4 LTS was made, 3 problems immediately surfaced:

1. Cannot surf the Internet although system monitor shows connection has been made;
2. Cannot open any thumbdrive;
3. Cannot shutdown after selecting shutdown button.

I asked my IT programmer for help and now everything works fine. I asked him to email me the command lines he did and I record them here to share: 

**To overcome thumbdrive that cannot open:**

dmesg

sudo su
mount -t vfat /dev/sdb1 /media/pendrive/

**To overcome internet linkages:**

/etc/init.d/networking restart

**To overcome shutdown that cannot shutdown: **

sudo su
init 0

---

### Post by pdadad on 2010-05-16
> **showgun22 said:**
> same thing here here every once in a while my computer will not shutdown or restart.
IN my case I have identify my culprit seems to be Ooo quick starter if the shutdown does not work all I have to do is exit quick starter and shutdown and it works just fine

Thanks Showgun.  This was a nice simple solution.

---

### Post by Sigma1 on 2010-05-16
> **To overcome shutdown that cannot shutdown: **

sudo su
init 0

Thanks for this post, but this doesn't look like a permanent fix, is it? By the way I think sudo init 0 should do the trick, without "sudo su". "sudo su" effectively transforms the user into superuser, which means that you can do anything without invoking sudo. Of course, if you're shutting down, it doesn't matter, but "sudo su" is a dangerous habit to get into, I think!
I imagine the answer for a permanent fix might be to edit /etc/init.d/halt but this lies beyond my capacities!

---

### Post by ChadBurr76 on 2010-05-19
> **RichardSM said:**
> :confused:Is it I!. the only person with a shutdown problem with Ubuntu 10.04 this is day two for me and nobody yet has a shutting problem.See the thread I posted on day one. Thanks

My system is.

AMD Athlon 1400 Thunderbird
MSI Mother Board
GeForce 6200 256Kb
Ram 512Kb
52x33x52x CD Writer
350W Power Supply
Microsoft Wheel Mouse Optical 1.1A USB
Tower Case

Hello this was the fix for me give it a try.Just for the record I downloaded the latest copy of Ubuntu 10.04LTS and did all the updates too. Be sure save after change, to update sudo update-grubsome users have found a permanent tweak:

sudo gedit /etc/default/grub

change : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

by : GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"

may not work for everyone

--------------------------------------------------------------------------------
Last edited by RichardSM; 1 Day Ago at 06:22 AM.. Reason: Solved

THANK YOU!
IBM Thinkpad R31
This solved my problem!

---

### Post by stephenjudge on 2010-06-12
There is a bug report on Launchpad for this, although it is marked Low importance and only affecting 31 people.  Everybody here should go to this but and mark it as affecting them.

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/562027]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/562027")

---

### Post by rejuvenate on 2010-06-26
the open office quick starter is never enabled in my system but still it is not shutting down, screen goes off and then i have to go for hard shutdown.....i do not have any problem with restart..i have edited the grub but it didn't worked...

---

### Post by rejuvenate on 2010-06-26
sry....i checked it now ..even my restart is not working and none of the command like
sudo halt
sudo init0
sudo poweroff..
for shutting down properly i need to log out then have to shut down..
the commands are working when i am logged in command line only

---

### Post by MrGoodDude on 2010-07-03
I have a Compaq Presario 6400nx.  "kinforcenter" reports the computer is: Compaq Presario 06 DA234A-ABA 6400nx NA910 (version On31411RE101SALSA).  "sudo lspci | grep VGA" reports: S3 Inc. VT8375 [ProSavage8 KM266/KL266] for the on-board video device.  You can install kinfocenter with apt-get if it is not loaded on your system.   Start kinfocenter from a terminal.

A solution that worked for me was to edit the /etc/X11/xorg.conf file.  You must su to root or use "sudo gedit" to change the xorg.conf file.  Make a backup first, so if something goes wrong, you can recover (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak).  In Section "Device", comment out or remove the line that contains "Driver "vesa".  Restart the system.  You may have to hold in the power button one last time to reboot.  From this point on you will notice you can reboot or shutdown the system.  The CPU will power down properly.  

I also reinstalled the xorg savage driver.  When I did, the system downloaded about 93K from the distribution site.  I assume it did a small update, but did not notice any change in video performance.
Please let me know if this works for you.  Good luck.

---

### Post by ashokmkd on 2010-08-01
I am having the same issue and none of the solutions said here work for me.. I haven't tried to disable the graphics drivers. i have ATI Mobility series graphics card. Since Karmic, ubuntu was not supplying any drivers for ATI or NVIDIA. But now i can see these drivers preinstalled.They are not the actual drivers supplied by ATI or NVIDIA. But i think its some open source variants and the problem can be with that drivers. I am so sad why ubuntu has not provided any patch yet after all these people having similar problems.

---

### Post by Emerson Prado on 2010-08-19
Hi all,
I had the frozen shutdown problem, and solved that by changing grub as indicated in the first post.
But I have an advise for newbies like me: after updating grub (sudo update-grub), you should restart your system once (if you like terminal: sudo shutdown -r now) before you can shutdown properly.
It may seem obvious for more experienced users, but not for starters: grub tells Ubuntu (well, any Linux) how to start. So, if you change grub, you should (re)start to activate any change.
Best regards,
Emerson

---

### Post by Bas232 on 2010-08-24
I changed it too, but it doesn't work.
Everything is shutdown, even the harddisks.
But video stay on telling me power is being cut....but one can wait for hours, nothing happens.

---

### Post by Esmeraldino on 2010-08-31
Hello, I am really noob in Linux and ubuntu. but, to me its work when i atived my driver ATI/AMB in System > administration > Hardware drivers, The driver don't was enable after installation . my pc is a HP tx 2500. Now it shutdown perfectly.

excuse me my English. i am not a English speaking.

---

### Post by zogg18 on 2010-09-07
> **pete1983 said:**
> I have found that my video card was the problem.
 1) system 
 2)Administration 
 3)Hardware drivers 
 4)select a different NVIDIA driver or deactivate NVIDIA driver and        try to power off. This worked for me I switched drivers.
  
  If all else fails
  sudo poweroff worked for me as well.
Thanks a million. Changing my drivers to version 96 worked

---

### Post by oneguycoding on 2010-10-06
setting acpi=force caused my machine to panic on boot.

Running *shutdown -h now *does work, but poweroff leaves the box running after halt.

Don't forget to run 'update-grub2' after changing /etc/default/grub.

---

### Post by BenjaminKohl on 2010-10-13
> **maburger said:**
> I am having the same issues.  It will not shutdown, it just goes to the login screen.  I am also having issues remaining connected to my home wifi network using WPA.  It keeps disconnecting and/or not picking up an IP address.  Wifi router is a generic Linksys WRT54GS.  Both problems were not present in beta2.
What you have just described has been an ongoing problem for me as well.  I don't think the router is the problem.  I think it might be the network adapter.  I forget the model number because I am not at home right now, but I am using a Linksys USB wireless ethernet adapter.  I lose my connection every once and awhile and I can "fix" it by unplugging the adapter and plugging it back in.  I purchased a Rosewill USB wireless adapter and that one completely freezes Ubuntu when I try to use it following the instructions I found online.

---

### Post by cunobu2010 on 2010-11-06
Hello

I'm the first time user of Ubuntu. 

I have just completed the first installation of 10.04 last week using WUBI . After struggling through the environment setup (missing panel, desktop, empty menu under App/Sys etc.), I have spent a few hours and managed to get it to a point to start exploring the OS.  

However I have run into the same issue that I can't shut down Ubuntu and have to power it down everytime.. This sometimes leaves the file system in the weird state and it has tough time to restart (black screen, lock-up after logging in etc..) . When it manages to come up sometime there is a messaging on the screen saying "scanning monitor ..changing setup. I have followed the thread here trying to get it shutdown and made a few changes tbut no avail.

It was an very trial experience to say the least and I'm at the point thinking that it's not worth it (deinstall..it's another story I have heard :).  I will keep at it for a few more days...but it's past my patience .

If anyone have other ideas how to shut it down gracefully, please let me know
I have tried to change the grub file to have quiet splash apci= force and few other things..
not working for me..Probably something to do with the video card or sound cards (no sound on my system..next on the list)

I have an old desktop HP Pavilion 6785 with only 325M of memory and 30G hard drive..

Thanks folks

---

### Post by darkdawn on 2010-11-08
I have the same problem, i will try and do some of the advices here, but this is not acceptable, this is an LTS release, if LTS isn't stable, then i dont know what is!!!!
I hope they fix this, and i think every bug is important to be resolved even if there is only 31 persons that reported the problem. which is a big problem when a new user (which Ubuntu is targeted for) cant shutdown his computer!!!! 
Just my Idea.

---

### Post by 6fish on 2010-11-19
Yep same problem here. Surprised this hasn't been taken care of with the updates. Especially since it must have been an update that caused the problem in the first place. Pretty major problem in my view.

---

### Post by KrzysiekSX on 2010-12-07
I had problem with unclean shutdown and disk checking at boot time. Solved by installing nvidia drivers using this guide:

[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

Cris

---

### Post by anne sol on 2010-12-12
Hy guys, this is my first time on the forums and I am very new to Terminal, but here goes...
 
I'm running 10.04 on a Dell Inspiron, dual boot with Windows. I've done all the updates. Since installing 10.04 I haven't been able to shutdown Ubuntu. When i press the Power icon in the top right corner of the desktop toolbar, it goes to the purple screen with the Ubuntu name and five circles down the bottom, which show a bit of progression, then freeze. I have to press the power button on the laptop to get it to power off. 
 
I tried the fix mentioned in this thread - i opened Terminal, typed "sudo gedit /etc/default/grub", entered my password when prompted, and a new window popped up titled "grub (/etc/default) - gedit. I changed the second last line to:
     GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"  
as suggested in the thread. 
the top of the window says "If you change this file, run 'update-grub' afterwards to update /boot/grub/grub/cfg.  " 
so i go back to terminal and type "update-grub"
and i get: "/usr/sbin/grub-mkconfig: You must run this as root"
 
can someone please tell me how to "run this as root"?
 
cheers, anne

---

### Post by Merovius on 2010-12-13
I believe you want "sudo update-grub" Give that a try.

---

### Post by anne sol on 2011-01-01
Cheers Merovius,  "sudo update-grub" worked a treat.

---

### Post by RussellEngland on 2011-03-23
Tried that

GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"  
sudo update-grub

But didn't work for me :(

I'm on Ubuntu 10.10 with nvidia

---

### Post by ibomb on 2011-04-07
> **anne sol said:**
> Hy guys, this is my first time on the forums and I am very new to Terminal, but here goes...
 
I'm running 10.04 on a Dell Inspiron, dual boot with Windows. I've done all the updates. Since installing 10.04 I haven't been able to shutdown Ubuntu. When i press the Power icon in the top right corner of the desktop toolbar, it goes to the purple screen with the Ubuntu name and five circles down the bottom, which show a bit of progression, then freeze. I have to press the power button on the laptop to get it to power off. 
 
I tried the fix mentioned in this thread - i opened Terminal, typed "sudo gedit /etc/default/grub", entered my password when prompted, and a new window popped up titled "grub (/etc/default) - gedit. I changed the second last line to:
     GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"  
as suggested in the thread. 
the top of the window says "If you change this file, run 'update-grub' afterwards to update /boot/grub/grub/cfg.  " 
so i go back to terminal and type "update-grub"
and i get: "/usr/sbin/grub-mkconfig: You must run this as root"
 
can someone please tell me how to "run this as root"?
 
cheers, anne

worked like a charm on acer travelmate 4002 wlmi with ati mobility radeon 9700 graphics :lolflag: thank you anne\\:D/

---

### Post by aas452 on 2011-08-02
> **RussellEngland said:**
> Tried that

GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"  
sudo update-grub

But didn't work for me :(

I'm on Ubuntu 10.10 with nvidia


Also same issue, this did not work for me also, I tried everything from shutdown commands, to reloading my graphic card drivers, but still restarts when I select shutdown...

ubuntu 10.04 LTS 
Nvidia GTX 570,
GIGABYTE|GA-Z68XP-UD3P - MotherBoard

Driving me nuts, any help would be much appreciated

---

### Post by flybyspam on 2013-02-07
This was "solved?"  Not from what i'm reading.   I've tried changing the etc/default/grub acpi setting....it does not solve the issue.  Also,  the menu link for installed drivers no longer works!   My machine used to shut down just fine....and NOW it has started this "new," behaviour of not shutting down (just returning to the login screen).  And, no one is knowledgeable enough (at least on this site) to offer any solution that works.   I'm done with Ubuntu.   It looked great at first.  But,  i'm not moving off of 10.04 cuz i'm not going to be cattle-penned into using the crappy Unity desktop by injected bugs.  Moving on to linux mint.

---

### Post by scy on 2013-04-13
Having the exact same problem with 12.10 and the computer restarts when it is supposed to shut down.

---

### Post by Nicram on 2013-05-08
The same problem here. Just to get them know. :)

---

