---
title: "Edgy does not shut down automatically"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by atari130xe on 2006-11-01
Hello forum,
After a clean Edgy installation, I got a problem: It does not shut down automatically,  need to press the power button, (I does all the shut down process but does not power off my pc) anyone has a suggestion, everything is fine on my system, the only problem I have is the above mentioned. (Im a newbie so be specific) thank´s in advance!:) [COLOR="Black"][/COLOR]

---

### Post by goldenatom on 2006-11-01
Have you tried to shut down again since you had to hold down the power button? I had the same problem, but after shutting it down manually once, it cleared itself up.

---

### Post by atari130xe on 2006-11-01
> **goldenatom said:**
> Have you tried to shut down again since you had to hold down the power button? I had the same problem, but after shutting it down manually once, it cleared itself up.

yes I Did, but still unsolved, it´s really strange, cause I haven´t any problem with Dapper, I see the orange bar and almost the end it stuck and I can hear the "click" of the system stopping and going off and that´s all. (The Hard disks stop spinning, etc (typical before power off) and that´s all, then I must push the power button to shut down.](*,) :-k

---

### Post by atari130xe on 2006-11-02
It´s a bit strange but I don´t think Im the only one with this problem, anyone to give me a hand?

---

### Post by atari130xe on 2006-11-03
:-? anybody?

---

### Post by wpshooter on 2006-11-03
Is this a Ubuntu only system ?

---

### Post by wounded on 2006-11-03
My XP/Edgy system does not shutdown/reboot when in linux either. Annoying :(

---

### Post by Colly on 2006-11-04
Same problem.  Under Dapper Drake 6.06 LTS, desktop versions, shutdown worked like it's supposed to.  By contrast, under Edgy desktop versions of Ubuntu, Kubuntu and Edubuntu, shutdown does NOT function correctly.
 Testing in terminal mode, I found that "shutdown" told me I had to be root.  Testing with "sudo shutdown -P 1" it STILL fails to completely power off the PC.

When explicit "shutdown" commands don't work with either the "power-off" or "restart" parameters for the root user, this is a major defect. I suspect this defect is also at the root of the problems people are having when the PC is supposed to restart after they remove the CD and press enter during the installation process.  The PC's will hang because the shutdown command doesn't go far enough for the restart to begin.  

I'm off to the launchpad.net to see what's mentioned about this in the bug lists.

Update: This problem is being tracked as bug #43961 at launchpad.net.  It's title is "Power down after shutdown does not work..." and it's listed as confirmed and high importance, so I guess someone is working on the problem already.  Also bugs 33775, 36158. I'm still looking around.  Apparently this bug was reported so many places, it may take me a while to find out which thread is the right one to track on.

---

### Post by atari130xe on 2006-11-04
> **Colly said:**
> Same problem.  Under Dapper Drake 6.06 LTS, desktop versions, shutdown worked like it's supposed to.  By contrast, under Edgy desktop versions of Ubuntu, Kubuntu and Edubuntu, shutdown does NOT function correctly.
 Testing in terminal mode, I found that "shutdown" told me I had to be root.  Testing with "sudo shutdown -P 1" it STILL fails to completely power off the PC.

When explicit "shutdown" commands don't work with either the "power-off" or "restart" parameters for the root user, this is a major defect. I suspect this defect is also at the root of the problems people are having when the PC is supposed to restart after they remove the CD and press enter during the installation process.  The PC's will hang because the shutdown command doesn't go far enough for the restart to begin.  

I'm off to the launchpad.net to see what's mentioned about this in the bug lists.

Update: This problem is being tracked as bug #43961 at launchpad.net.  It's title is "Power down after shutdown does not work..." and it's listed as confirmed and high importance, so I guess someone is working on the problem already.  Also bugs 33775, 36158. I'm still looking around.  Apparently this bug was reported so many places, it may take me a while to find out which thread is the right one to track on.

I got it!  have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody. :-D :mrgreen:

---

### Post by desicratn on 2006-11-09
Awesome. That worked great. Thank you so much. I was killing myself trying to figure out why my kids computer was on at 3 AM when I KNOW i shut it off last night.](*,)

---

### Post by JohnDMJ on 2006-11-17
I just joined this forum specifically for this problem - registered while the apm power_off suggestion was under test. Yup, it worked for my laptop too:mrgreen: 

Thanks!

---

### Post by lgambett on 2006-11-17
Unfortunately this did not work on my PC... I installed Edgy on two laptops and a desktop PC, everything went well on the laptops while the desktop PC refuses to shutdown. Note that sudo shutdown -h now works perfectly. Any idea ?
Thanks, Luca

---

### Post by dartakaum on 2006-11-17
same here.

---

### Post by sabitha on 2006-11-17
> **atari130xe said:**
> I got it!  have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody. :-D :mrgreen:

worked great fo me. thanks :D

---

### Post by viking777 on 2006-11-25
> **sabitha said:**
> worked great fo me. thanks :D

Wish I could say the same but I can't. The only function that works on my laptop is reboot all the others end the line 'Power Down' and then hang.

Incidentally I am on Dapper Drake at the moment but it was exactly the same on Edgy.

Gotta keep looking I suppose, still that problem along with the complete lack of any sound and the inability to use anything other than a vesa graphics driver will keep me busy these long winter nights!!

---

### Post by morgs on 2006-12-06
AFAIK [bug 43961]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961") is the correct bug report for this, and it has been reported as a bug in the upstream kernel versions. The bug has the link to bugzilla.kernel.org where upstream is tracking this.

It has prevented my Sony Vaio S460 from shutting down in both Dapper and Edgy.

---

### Post by TheForkOfJustice on 2006-12-07
I can't wait to try this when I get my systems back. It has been extremely annoying on both my laptop and desktop. I'm used to my laptop 
'halting' but its weird on my desktop. Thanks for the solution. I hope both start behaving now.

---

### Post by lgambett on 2006-12-08
I have read all the comments on the kernel bugzilla and decided to disable ACPI on my desktop PC via BIOS configuration. It worked ! Now my PC shuts down correctly. I know, it is only a workaround, but in some situation (like mine) can help.

---

### Post by dmizer on 2006-12-14
> **atari130xe said:**
> I got it!  have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody. :-D :mrgreen:

you are my new hero.  this problem has been plaguing me for months, through multiple kernel updates and with no resolution.

i am running dapper kernel 2.6.15-27-686 on a 2.6ghz p4 desktop.

thank you.

---

### Post by dartakaum on 2006-12-15
with me didn't work...

---

### Post by w_m0zart on 2007-02-28
Solved!
I use xubuntu 6.10, with that the shutdown problem was similar: no power down after shut down. My hardware was an Intel 440BX chipset on a clevo 3100c laptop.

Only difference to ubuntu is that xubuntu has no gedit. Use mousepad instead:

```
sudo mousepad /etc/modules

add a new line with the following statement:
apm power_off=1

Save and quit.

```

This solved the problem.

---

### Post by getaboat on 2007-03-07
Hooray - me sorted as well!

(odd on my other Edgy box it is OK - both installed off the same disk - one has Beryl, one does not (Beryl one OK - no change required))

---

### Post by dommyOZ on 2007-03-13
I've tried all the above and my desktop edgy still refuses to power off completely, mine is a desktop Edgy reinstall, my original install worked like a charm in this area, and the only thing that works is "shutdown -h now" ](*,)

---

### Post by majabl on 2007-04-08
> **atari130xe said:**
> I got it!  have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody. :-D :mrgreen:

Just to say, this also worked for me, and I'm running the 686 kernel of Dapper Drake (6.06).  Yay!  On the 386 kernel there was no problem, but when I upgraded to the 686 kernel, my computer would shut down but not switch itself off.  After adding this line, it switches itself off when it completes its shut-down procedures, as it should.  Thank you!
:guitar:

---

### Post by Ganda_Melga on 2007-04-24
> **atari130xe said:**
> I got it!  have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody. :-D :mrgreen:


I have this problem too! Is doesn't shut down. I tried your command but didn't worked:

sudo: gedit: command not found


Why doesn't it works on my PC???

---

### Post by dommyOZ on 2007-04-25
> **Ganda_Melga said:**
> I have this problem too! Is doesn't shut down. I tried your command but didn't worked:

sudo: gedit: command not found


Why doesn't it works on my PC???

Did you actually type in "sudo: gedit" ? or is that just a typo? there is no colon in the command string.
You should also be able to navigate to the file in Konqueror rightclick -> Actions->Edit as Root

In my case it turns out that my Edgy will randomly shut down completely, so I added a couple of icons which run the appropriate commands and modified the sudoers file so that I didn't have to add my passwd :),  one to shutdown and one to restart works like a charm

---

### Post by Ganda_Melga on 2007-04-29
> **dommyOZ said:**
> Did you actually type in "sudo: gedit" ? or is that just a typo? there is no colon in the command string.
You should also be able to navigate to the file in Konqueror rightclick -> Actions->Edit as Root

In my case it turns out that my Edgy will randomly shut down completely, so I added a couple of icons which run the appropriate commands and modified the sudoers file so that I didn't have to add my passwd :),  one to shutdown and one to restart works like a charm


I got it! In xubuntu it's not GEDIT, but instead is MOUSEPAD.

Thank's a lot for your help :guitar:

---

### Post by aufumy on 2007-05-11
> **atari130xe said:**
> I got it!  have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody. :-D :mrgreen:

Had the same problem with my xubuntu install on an ancient Compaq computer, and the above worked for me too.

---

### Post by linuxmangr on 2007-05-15
> **aufumy said:**
> Had the same problem with my xubuntu install on an ancient Compaq computer, and the above worked for me too.
Hi to All USERS.
I'am not sure but I think I find the solution for this "bug" , ok I have this problem not on Edgy but Feisty Fawn.
I make 3 fresh Install but I can't understand why  if I push Shutdwon bottun PC not power off automatically but still after go back.
I try the solution on this thread with edit /etc/modules  and add apm power_off=1 but is not work .
After I think to try search solution on my pc some time to seach on my system and start up scrpts and I see in **System->System Administration->BootUp-Manager **, I click it and when  I click ** Advanced** I see all scripts when startup on boot 
Here I think to try enable one off 2 script in **Services**  when the information about it say is shutdown .
I enable this :
[COLOR="Red"][B] bootclean: Scripts for initializing and shutting down the system
[/B][/COLOR]
 [B][I]The scripts in this package initialize a standard Debian
 GNU/Linux system at boot time and finalize it at halt or
 reboot time.[/I][/B]

Ok, to see this you need to find on AddRemove programs or Synaptic BootUp-Manager package click to advanced and to  bootclen click with right mous button and click on Start now.
After this try to shutdown the pc.



P.S. Please send my if is works because on my System is work.
I think is some new bug after the fresh install this script is removed from strart up or is never existed in start up.
I don't know why.

---

### Post by Belohin on 2007-05-17
I have the same problem on Feisty. And there is some funny about the System Services. Several services are set to start at system boot up, but are not running when I am looking in the service manager. For example this bootclean. If I write the command explicitly in consol:
# sudo /etc/init.d/bootclean
it does not say anything (as used to when it is all right), but it is not running.
Same is the situation with the acpid and that is suspicious too.

---

### Post by linuxmangr on 2007-05-17
I don't know if is the way but...
I try to find the problem but for now I use not Shutdown button but Inactivation button and the PC shutdown ok, power off automaticaly without not problem.
But the problem with normaly Shutdown is still problem!

---

### Post by chewjoel on 2007-05-17
I can't find 'Bootup manager' in my feisty... :(

---

### Post by linuxmangr on 2007-05-17
Please download Automatix for Feisty [www.getautomatix.com](www.getautomatix.com) or from console type sudo apt-get install bm
and try to find Boot Manager.

---

### Post by leona on 2007-05-17
Got the same problem with my Ibm thinkpad notebook, with Drapper 6.06 it worked fine, but with 7.04 FF its not working, the notebook doesn't power off.

---

### Post by linuxmangr on 2007-05-17
Try to use this like me :
I try to find the problem but for now I use not Shutdown button but Inactivation button and the PC shutdown ok, power off automaticaly without not problem.

P.S. If I find solution I post it here.

---

### Post by Paul Mitchell on 2007-05-28
> **atari130xe said:**
> I got it!  have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody. :-D :mrgreen:

Thanks. That worked a treat with my Fiesty install (and 1999 BIOS).

---

### Post by eggdeng on 2007-05-28
Worked for my Edgy install too.

---

### Post by leona on 2007-05-28
> **atari130xe said:**
> I got it!  have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody. :-D :mrgreen:
Excellent, that worked on my thinkpad 7.04 install too, great thanks :)

---

### Post by Pho House on 2007-05-30
Hi everyone,

This is my first post after joining this forum. Just want to add that I have this problem too and none of the solutions presented work for me. I get the ubuntu shutdown screen with the progress bar all black, and I hear the hard drive stop, but the screen just hangs and the desktop pc stays on. Although, rebooting is not a problem. 

version: 7.04

---

### Post by tk03759 on 2007-06-07
Okay, so before, I had the above mentioned problem. The computer would show the orange progress bar at shutdown and the entire thing would progress to black. The disk would stop spinning, and the computer would remain on. I'm using Feisty, btw.

Well, I added that line to the modules file and shut down the computer. It didn't turn off again, so I let it sit for about 8 minutes while I read the rest of the replies in the forum. When I came back and hit restart, I didn't get grub and instead got a nasty little blinking underscore. I restarted again, checked my boot options, and saw that my hard drives weren't being listed. I turned it off, let it sit for about 10 minutes, and started again. It recognized my hard drives, I changed the boot order, and it started up normally. I'm assuming it overheated, meaning that the fan turned off, but the disk was left running.

I took a guess that it might be an acpi problem, so I added some options with grub at boot time. I tried acpi=force, apm=on, apm=power-off, and I tried some of them in combination. Nothing's helped. I'm kinda concerned because I'm afraid that if someone forgets to hit the power button, that the system could stay on for long periods of time and possibly overheat. Any more solutions? .... I'm ALMOST considering updating my bios. :/

Edit---
Any time I hit restart after I see the shutdown progress bar, I have to change the boot order. I'm thinking it might just be the battery?

---

### Post by Dimension7 on 2007-06-08
> **atari130xe said:**
> I got it!  have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody. :-D :mrgreen:


Holy cow!  IT WORKED!  After 3 annoying months of waiting for the OS to completely shutdown  before pushing the power button to turn the system off, now I can just walk away after shuting down Ubuntu.

---

### Post by tk03759 on 2007-06-08
To anybody that couldn't get this to work, you can try this:
[http://ubuntuforums.org/showthread.php?t=237264&highlight=shutdown]("http://ubuntuforums.org/showthread.php?t=237264&highlight=shutdown")

It solved a couple problems for me, but it still refuses to turn off. :-s

---

### Post by dommyOZ on 2007-07-02
> **tk03759 said:**
> To anybody that couldn't get this to work, you can try this:
[http://ubuntuforums.org/showthread.php?t=237264&highlight=shutdown]("http://ubuntuforums.org/showthread.php?t=237264&highlight=shutdown")

It solved a couple problems for me, but it still refuses to turn off. :-s

Tried all that and still wouldn't shutdown my pc. I tried turning on the bootclean service as mentioned two pages back and that did work, sort of, my pc would shutdown correctly :D  but when I started again I would get the X screen on ok but no kde, after a while the gui would restart and I would get a login screen :( so I have two choices I can either shutdown using my own shutdown icon and restart correctly or I use the shutdown method provided by KDE and then have to wait for the gui to start the next morning. I think my way is better

---

### Post by thefirstcalled on 2007-08-04
> **atari130xe said:**
> I got it!  have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody. :-D :mrgreen:

I am so happy that I found this thread - thanks - it works for me too in Feisty! (except use /etc/modules in lower case)

---

### Post by Albinodrew on 2007-09-06
> **atari130xe said:**
> I got it!  have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody. :-D :mrgreen:

HI, and thanks, I had the same problem on my Compaq Presario SR1010NX, and the simplicity of your solution does it perfectly. 

Once again thanks you.:)

---

### Post by geraner on 2007-09-09
> **atari130xe said:**
> I got it!  have found a solution (at least for my PC)
type:
SUDO GEDIT /ETC/MODULES
add a new line with the following statement:
apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.
I hope it helps to everybody. :-D :mrgreen:

Great!
I'm running 6.06 LTS Server (2.6.15-29-server) and had the same problem.
Using your idea soved the problem for me.
Thanks!

---

### Post by gargouille on 2007-12-17
I had a problem with my laptop not shutting down.  It would just display the Xubuntu "splash" screen.  I had to unplug the laptop and battery to turn it off.

Hardware:
HP OmniBook 4150
128MB RAM
10GB HD
PIII

In case someone else has this problem, this is the solution that I found.  I have slightly altered instructions from the post that I found for Dapper Drake 6.06.

type:
SUDO mousepad /ETC/MODULES

add a new line to the end of the file (unsure if needs to be at the end) with the following statement:

apm power_off=1

Save the file  and reboot.


> **atari130xe said:**
> I got it!  have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody. :-D :mrgreen:

---

### Post by Mortuis on 2008-05-28
> **atari130xe said:**
> I got it!  have found a solution (at least for my PC)

type:
SUDO GEDIT /ETC/MODULES

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer shut down correctly.

I hope it helps to everybody. :-D :mrgreen:

I was having this problem in hardy on my Thinkpad T20, adding "apm power_off=1" to /etc/modules did the trick.  I'd love to know how you figured this out in the first place.

---

