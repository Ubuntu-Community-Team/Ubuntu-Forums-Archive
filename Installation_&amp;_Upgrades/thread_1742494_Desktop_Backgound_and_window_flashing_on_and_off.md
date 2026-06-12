---
title: "Desktop Backgound and window flashing on and off"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by leopards on 2011-04-28
On boot into new 11.04 32bit system, the desktop background came up and nothing else, no panel no icons. Right clicking brings up the dialog box for create folder change background, etc. but it is flashing on and off, after a bit of effort used it to change the background, but still no panel and same thing with further mouse clicks! This was a semi-clean install from a LiveCD with download updates checked and a separate /home partition.

---

### Post by Hedgehog1 on 2011-04-28
> **leopards said:**
> On boot into new 11.04 32bit system, the desktop background came up and nothing else, no panel no icons. Right clicking brings up the dialog box for create folder change background, etc. but it is flashing on and off, after a bit of effort used it to change the background, but still no panel and same thing with further mouse clicks! This was a semi-clean install from a LiveCD with download updates checked and a separate /home partition.

I would suggest reinstalling, this time formatting the '/' (root) partition, but NOT FORMATTING the '/home' partition.  You will have to reinstall your applications, but you will be running again.

***The Hedge***

:KS

---

### Post by IPEX-731BA5DD06 on 2011-04-28
Same problem, different method to achieve.

I've installed the PAE 32 bit version of 11.04, worked fine WITHOUT upgrading the Video Driver for Nvidea to 173, just can't use Unity desktop. Ok :cry:

Upgrade Video driver to 173, as I've done sucessfully with 10.04.2 LTS Edition and wham, no Desktop, no Menu's, no icon's just pink fluffy clouds (default booting desktop I think)

Obviously its the Video driver upgrade didn't take, or is corrupted, done this 3 times now, twice in beta, once in release.

Haven't tried the Non PAE Version of Ubuntu, but I have 4 Gig of Ram,and it won't show [-(

will continue the search for solutions, starting with NON PAE version of software.

---

### Post by Montblanc_Kupo on 2011-04-29
Same behavior here. ubuntu 11.04 32 bit. Completely clean install. Wiped the entire hard drive and had it "use entire disk".

It boots up and I see the background and can move the mouse but there's no GUI. ctrl alt del or right click bring up brief glimpses of the appropriate windows but nothing sticks around for more than half a second. Never had a chance to install any drivers or whatnot... can't get it to go into the UI at all.

--edit--

I should say when I did the live boot, it worked fine... and this machine previously had 10.04 and 10.10 installed on it without any issues.

--update--
Using some kind of keyboard blackmagic... I managed to get the lock screen up (ctrl alt l) which displayed long enough to "switch user". I could then choose "safe mode" which loaded the desktop. I deleted the 173 nvidia driver (which must have been activated on install). I then got the option to choose the "experimental nvidia driver". This let me into the normal ubuntu unity interface... but the little quick bar at the left is completely black. I can see the names of stuff when I hover them... but no graphics. If I click the ubuntu logo I get a full screen with visible shortcuts. Not what I would call useful... but maybe that means something to someone.

---

### Post by leopards on 2011-04-29
I did a format of the / partition the first time. When I got to the desktop background screen if I waited long enough I got brief glimpses of the log-in screen, even succeeded to unlock, but it just seemed to go into a loop of hard drive access then back to the same log-in screen! Have wiped / again and re-installed 10.10, off of the second CD I tried as the first one was scratched and fail to fully install! Whew, I have NEVER had this much trouble with an Ubuntu install before. I hope someone comes up with a solution to this problem before to long, as I liked what I saw on the LiveCD, even if it was just the "Classic" version of 11.04!

---

### Post by hmariey on 2011-04-29
Exactly the same behavior here.  Also I am unable to login to previous installs via grub (get a purple screen that just sits there.)  Haven't managed to get anything to show long enough to click--though the icon blink  has a rather nice rhythm-- offffff, on,off,on, offff, on, offon --I would really rather this thing wasn't just an elaborate desk decoration. 

I am assuming it is a video driver issue?

Did an auto install via Ubuntu Update and just let it do its thing because in the past things have gone pretty well (though of course there was that one time when they upgraded grub where it tried to kill my computer.)  Will probably make a live cd and see what  I can do from there though I am really hoping someone who is more technical than I will step in with some real answers (all that voodoo is why I DON'T use Windows and here I am typing on a Vista machine.  Sigh.)

---

### Post by Johnsie on 2011-04-29
I had the same issue. It has made my computer unusable. 11.04 has been a disaster for me. I hope Fedora will work better.

---

### Post by Johnsie on 2011-04-29
double post

---

### Post by 1Nyco1 on 2011-04-29
Same problem.  Blank white screen, some menus appear but not others.  It seems to be using a driver other than the proprietary NVIDIA.  Cannot activate either proprietary driver.  Can change screen resolution with Monitor adjustment.  Some work better than others.  Huge disappointment.  Hope someone has a solution.

---

### Post by eino1953 on 2011-04-29
I had the same problem, I fixed the problem by selecting Ubuntu Classic at the log on. You will fine it at the bottom of your login screen.

---

### Post by Johnsie on 2011-04-29
I had my computer set up 'automatic login' so I don't get an opportunity to change the desktop environment. Is there a keyboard shutcust to log out?

---

### Post by hmariey on 2011-04-29
Same here.  Have auto login (bypassing the login screen.)

---

### Post by eino1953 on 2011-04-29
Give this a try, Press Ctrl+Alt+T to open the terminal 
code
 
> sudo apt-get install unity-2d

---

### Post by leopards on 2011-04-29
What I can't understand is that the LiveCD worked, just that it came up in classic mode. 
I wasn't all that interested in Unity in the first place, wouldn't mind trying it out, but classic with video acceleration and 3D, would have done me just fine! Supposedly the newer 173 driver from nvidia is "Supposed to work with 11.04, but did find any way to get to the gui so I could change to it! Me and CLI don't get along to well unless I either can cut and paste the commands or have them printed out and laboriously type them in one character at a time, Neither my typing skills nor my memory are up to inputting a long string perfectly first time! Was really looking forward to Firefox 4, but didn't want to go there before it was supported in the repositories!

---

### Post by hotbelgo on 2011-04-29
> **hmariey said:**
> Same here.  Have auto login (bypassing the login screen.)

Snap - right at the beginning of the install I did click the option to download proprietary software, which would have included the nvidia drivers - has anyone with an older nvidia card had success by NOT installing closed source drivers (and thus using the nv one)?

---

### Post by leopards on 2011-04-29
> **hotbelgo said:**
> Snap - right at the beginning of the install I did click the option to download proprietary software, which would have included the nvidia drivers - has anyone with an older nvidia card had success by NOT installing closed source drivers (and thus using the nv one)?

Darn that means I am going to have to make a small partition so that I can set up a dual boot with 10.10, just so I can try this out! If that doesn't work, I guess I just wait till this problem is fixed!

---

### Post by 1915flyer on 2011-04-29
Same problem with nvidia drivers. Even 2d. 

Works in classic mode only.

---

### Post by hmariey on 2011-04-30
Managed to login using safe mode, switch to show login screen and from there switch to classic view.  Was a mess but worked and now I can get in and use my computer again.

---

### Post by leopards on 2011-05-01
Have given up on 11,04 till they fix the nvidia 173 driver issue, have it set up to dual boot with 10.10, but plan on using that pretty much exclusively till things get straightened out! My computer only uses AGP video cards and Since it flies in 10.10 I can't see buying a new computer just to go to 11.04, since that is the MS way of things that i came to Ubuntu to get away from!

---

### Post by hotbelgo on 2011-05-07
> **leopards said:**
> Have given up on 11,04 till they fix the nvidia 173 driver issue
I realise now that I had not used the nVidia drivers on 10.10 either because they made the computer unusable.  I have a fx5200 card with TV tuner (that never worked at all - rivatv came to nothing). So, looks like unity is out of reach for me :(

---

### Post by leopards on 2011-05-07
> **hotbelgo said:**
> I realise now that I had not used the nVidia drivers on 10.10 either because they made the computer unusable.  I have a fx5200 card with TV tuner (that never worked at all - rivatv came to nothing). So, looks like unity is out of reach for me :(

Mine is the FX 5700 LE, my 256MB GeForce 5700's cooling fan died and I had to replace it with the LE 128MB version, it worked fine with full bells and whistle in 10.10, but so far no go in 11.04, though I can get it to boot in Classic mode but it still glitches all to heck if I try to turn on 3D effects!

---

### Post by IPEX-731BA5DD06 on 2011-05-07
[SIZE=4]Title: [SIZE=2]Part Fix of problem

I've been able to upgrade the drivers for my FX 5600 Nvidia graphics card to the latest beta drivers or development driver available through Synaptic 260.?? I think from memory, it still works in CLASSIC mode only though, no unity support. That's because its an OLD [-X video card ONLY!!!!

On using Unity desktop, well, if you don't have the hardware, it'll never work, will it.

173.22.14 the default Nvidia drivers, WON'T WORK in my case, and many others. I can only suggest trying the latest development release, install through synaptic, and if doesn't work, just remove Via Terminal. 

Commands I don't know, sorry, bad form I know, tell installation, but not removal. Not a big command line guru. 
[/SIZE][/SIZE]

---

### Post by leopards on 2011-05-07
> **IPEX-731BA5DD06 said:**
> [SIZE=4]Title: [SIZE=2]Part Fix of problem

I've been able to upgrade the drivers for my FX 5600 Nvidia graphics card to the latest beta drivers or development driver available through Synaptic 260.?? I think from memory, it still works in CLASSIC mode only though, no unity support. That's because its an OLD [-X video card ONLY!!!!

On using Unity desktop, well, if you don't have the hardware, it'll never work, will it.

173.22.14 the default Nvidia drivers, WON'T WORK in my case, and many others. I can only suggest trying the latest development release, install through synaptic, and if doesn't work, just remove Via Terminal. 

Commands I don't know, sorry, bad form I know, tell installation, but not removal. Not a big command line guru. 
[/SIZE][/SIZE]

If it doesn't work I'll just format the 13 GB partition I have been using to try out the different Distros trying to find a replacement for Ubuntu, so far have only tried Lubuntu, can't say much for the looks, but it is fast, and I did find out just how fast Chrome browser is, so that is the new default in Ubuntu 10.10! So not all bad!;) The one big worry is if they are even going to have the Classic desktop in 11.10![-o<

---

### Post by IPEX-731BA5DD06 on 2011-05-18
The solution actually works, believe it or not. HA HA :D

1. boot into safe mode.
2 Boot into command line with network support.
3 Sudo apt-get install unity-2d
4 sudo gdm desktop

It will now boot into your 11.04 operating system with a 2D unity desktop. Wooo Hoooo 1st time I've seen it.

Thanks for all input in this thread, I'll add a screen shot ):P

---

