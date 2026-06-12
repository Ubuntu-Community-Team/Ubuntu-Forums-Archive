---
title: "Fresh install problems - freezing on format / copying files"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by apieroux on 2008-04-27
Hi

New to Linux/Ubuntu here.  I've trawled through the forums for this issue, but none seem to be quite like it, or with a solution that works.  If anyone can point me in the right direction I'd appreciate it.

Decided to take the plunge with Linux yesterday and I'm struggling.  I'm trying Ubuntu 8.04 desktop i386 live cd, although have tried the Kubuntu iso too with no success.

Was originally trying to install alongside an XP install on a Vaio PCG FR102 512mb ram with 60GB HD and inbuilt Nvida GeForce Go 7400 video card.  The XP install has no significant data on it that couldnt be lost (luckily!)

First attempt (Kubuntu disk) the CD booted but did not go further than the non-GUI first screen where you choose language.

I redownloaded ubuntu (version as above) and set about the install via the live cd - went for a full install.  All went well (after using safe video option - mad green and yellow patterns were pretty but not practical)

I told it where i was, keyboard settings etc and then elected to go for a guided install on the primary hard disk - after that, entered my name and password and left it to go.

It froze on the 'partitions formatting' screen - no mouse, no cd or hd activity.  After 20 mins+ I rebooted and unsurprisingly XP wouldnt boot - no major loss for me at this stage - was happy to experiment and I still have my orginal XP disks if I need to go back.

Since then I've spent the last 24+ hours trying to get something to work.

Here's what I've tried - not strictly in order, but as a variety of routes with much repetition!:-
Have re burnt the ubuntu iso at a slower speed.
Have gone into bios and disabled my floppy disk
Have redownloaded the iso and reburnt at 4x
Have blanked the whole HD using Pmagic (it found another NTFS partition) and tried to install on a completely blank HD
Have manually set up my own partitions (Ext 3 + 1 swap partition) and tried to manually set the mount points
Have  tried all settings on the partioning dialogue box that there are (Guided, manual etc)
Have taken out my wireless card, USB Mouse, USB Keyboard - everything that might be a conflict - only thing possibly removable now is the monitor (I know its a laptop, but the screen died a while ago so I removed it and use ext monitor only!)
Have booted in ubuntu without installing (looks lovely by the way, wish I could install it!), which worked fine most of the time - tried to use gParted from there to reset the partitions.

Basically, everytime gParted or the installer gets going it gets so far (either to partitions formatting - if I've chosen that or theres partition work, or through to "copying files" if theres not - somewhere between 5 and 22% -  then it  freezes - again, no mouse no cd or hd activity.  

Occasionally it doesnt even get as far as the installer before crashing.  I've run disk checks, memory checks and I haven't had any problems in Windows.

I'd love to move to open source, and I don't mind getting my fingers dirty up to a point, and I like what little I've seen of the interface, but am starting to think it might be something fundamental about my slightly old and worn system?

Can anyone prove me wrong, show me that its something I can affect and get me going again, otherwise XPs reclaiming a user - at least until I get a new system and i hear more good things about Ubuntu/Linux! 

Based on what I've said here the only other things that I've thought of are to try the alternate installer CD - will try and download that now, so theres a few hours to go before I revert to XP if that doesnt work - or maybe trying a V7 release - would that make any difference?

So let's see how good this famed support community really is!!

Thank you for listening... any thoughts?

---

### Post by apieroux on 2008-04-27
OK - brief update.

I downloaded the alternate CD install iso, burned that nice and slowly and tried that - it seemed to get so much further, going through a lot of installing from the CD.  Then on a blue screen with a grey box in the middle titled "Select and Install Software" and the progress bar at 6% it says "Please wait".

At first I thought happily how much better this seemed to be - it's even telling me I should be patient - its now been 15 mins without any activity or movement.  I cant even check if the same freeze has happened as theres no mouse on this one - it being text based.

Any thoughts?  Should I wait longer and do as I'm told, or crash out - if so, any suggestions as to what might be causing it, or how do I create a log to find out theres something offending?

All help appreciated.

Thanks

---

### Post by samyslo on 2008-06-15
Hi,

I am having the same problems as you, and I have the same computer as you, a Sony Vaio PCG FR102 (AMD Athlon XP, 256 ram, 120 gb). I've tried everything (instaling with dvd, cd, ubuntu, opensuse, mandriva...., but the computer always freeze during the instalation. Please reply if you found a solution.

bye

---

### Post by kaotiK0c on 2008-06-15
Same problems here! I am running a SOny VAIO PCG-FR130. Have tried the above almost in the same order, with no succes. Live CD itself runs GREAT, I am writing this post from Ubuntu---it will just NOT install. Always freezes (disk actvity stops, cursor locks, and then CD spins down) between 5% on partitioning and 23% on installing system. 

Did either of the two previous posters find a solution? Thanks!

---

### Post by samyslo on 2008-06-16
Hi there,

Nothing new. Today I will try to contact the Sony Vaio customer support, if they know something about this issue. I think that the problem is in our comoputer and not in the installation!!??!
If I will get any news I will let you know.

regards

---

### Post by kaotiK0c on 2008-06-17
Latest, have tried Ubuntu, Kubuntu, and Xubuntu hoping that I was running into RAM issues (512mb on system), but all have the same exact problem. Have not tried alternate CD yet, that is my next step.

---

### Post by kaotiK0c on 2008-06-17
Okay, installing from Xubuntu 8.04 ALT cd and it got to: "Installing the base system" 6% Retrieving libss10.9.8...

and has frozen here. HDD activity stopped, then CD spun down.

If anyone can advise I would greatly appreciate! 

Thanks!

---

### Post by kaotiK0c on 2008-06-17
Almost success....got past Base System install, past User Info, to "Select and Install Software", and it froze at 6%...just says "Please wait..."

Only thing I did differently was to tell the Partitioner to partition "with LVM"....(NOT encrypted LVM)

tried "Repair Broken System" option from CD but it just kept wanting to reformat, which would force me to start again. So am just going to try a clean install with LVM again.

---

### Post by samyslo on 2008-06-18
The sony support service replied:

Please note we can only support the preinstalled Operating System that came supplied with your Sony VAIO. 
For further assistance, we can only refer you to your software vendor.  


Now I am again on start point. I rally don't know what to do..... :S

If somebody has some new information, please bring it on.


thx

---

### Post by amethyst00 on 2008-06-18
Hello to everyone !
I encountered the same problem on a desktop, not a laptop.
I think you must be patient. The install process freezes several times ! 
When you launch the install CD, press F6 and try some of the cheatcodes. Cf. [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Good luck !

---

### Post by apieroux on 2008-06-18
Hi

I sort of got there eventually by installing Ubuntu 7 Gutsy - couldnt get HH to install at all with either disk.

7 installed from the alternative, with a lot of fiddling on the video settings.  By this stage I'd blown away my windows installation.

I also more or less managed to get to 8 by upgrading from 7

I spent a couple of weeks tweaking it and trying to learn Linux's nuances.  Had a number of restarts required and a lot of problems with the inbuilt nVidia graphics card and my PCMCIA wireless card (especially in 8).

In the end, I gave up and went back to Windows.

There was a lot I liked about Kubuntu - I love the concept of open source, but for me the apps (even compared to free Windows apps) weren't quite there.  Call me old fashioned but I prefer iTunes to any of the Ubuntu equivalents.  I use Firefox, VLC and some web apps quite happily and that gets me by.  I use Picasa for photos.

I'm glad I looked at Ubuntu, but it made me realise that for what I want to do, I prefer the stability of Windows XP and the ability to work with my current hardware.  Maybe in the future...?

Hope this helps explain a little, and sorry its not more use.

Thanks

Andy

---

### Post by kaotiK0c on 2008-06-19
Not sure if this is progress, but finally got an error message. 
[789.361107] Kernel panic - not syncing: Fatal exception in interrupt.

Same install as always except that I turned off the debian-installer framebuffer. So maybe this wasn't a good idea.

BTW: This was roughly at the 23% "Installing Software Packages" mark

---

### Post by AtomicSpark on 2008-07-06
I came across this while trying to salvage an old laptop. Happened to be the model in question. Pressing F6 and then using the boot option of "noapci" before the install, seemed to fix the problem. Hope that helps some of you! :)

Update: I spoke too soon. At least I got past creating the main user this time. I'll update this if I ever figure it out. More boot options here we come...

---

### Post by karachuonyo on 2008-07-15
I'm having the same problem except my laptop is acer 1310 and ironically was happily chugging along with kubuntu 7.04 before i succumbed to the bling of ubuntu 8.04.

---

### Post by da_norf on 2008-07-16
Hi, there !

I want to write here, cause I have the same computer : Sony PCG-FR102 but in a french flavour (as, basically, I'm French)(nobody's perfect...)
I use another Linux distro (Fedora) but I think I have (perhaps) the same problem you have : "pseudo-random" freeze.
For me the problem appeared after I had installed Fedora 7 (and is still there with Fedora 8 and 9). With previous distro (Fedora Core 6, 5, 4) I never had such freezes.

As far as I can see (and say), the computer freezes when on heavy disk (or CD-Rom) access and trying to make another bus access (mouse, display, ...). The heavy disk access is likely a constant when computer freeze but is not suffisant to make it freeze.

For exemple :
-Playing a CD without graphical visualization never freezes the computer but enabling graphical visualization makes the pc unstable.
-Opening Firefox (or any other app) when updating packages can make the pc freeze.
-Installing Fedora 7, 8 or 9 from CDs/DVDs either in graphical or non graphical mode freeze before the end
-Ripping music from any audio-CD freeze before the end.

... and so on...

I first thought that it was a problem with the kernel ide drivers used in Fedora : in this distro, "pata_via" has replaced "VIA_IDE" since F7. But I can't manage to make tests. Furthermore Ubuntu still uses VIA_IDE and you seem to have the same "freeze" problem.

Another possibility is that it could be a problem with the Apollo KT266/A/333 as this chipset was known to produce similar freeze on various OS a couple of years ago : see "PCI Latency" patch for VIA chipsets" section on [this page]("http://www.georgebreese.com/net/software/") or [this one]("http://usuario.cicese.mx/~mirsev/Linux/VIA/VIA-latency-linux.html")

I actualy never solved this problem myself (since more than 1 year) in any other way than "doing only one thing at a time on my laptop and live with some few remaining freezes" as I don't have suffisant technical skills to go further and untill this day I have felt myself a little bit alone on this problem...

But if we really have the same bug, if this bug is hardware related and cross-distro, this could be a good opportunity to get definitively rid of it.

Regards.

---

### Post by Aleksey1977 on 2008-07-24
Has anyone submitted a bug for this issue? If not, I'll do it, after a few more tests.

---

### Post by Aleksey1977 on 2008-07-30
The freeze also occurs for me in Intrepid Alpha 3.

I have submitted a bug report for the issue at [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/253321](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/253321)

---

### Post by kaotiK0c on 2008-07-31
> **Aleksey1977 said:**
> The freeze also occurs for me in Intrepid Alpha 3.

I have submitted a bug report for the issue at [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/253321](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/253321)

Thanks Aleksey, still having the problem here. I have tried every suggestion I can find with all the flavors and types of install of Ubuntu I can find. The one thing I have yet to try and is next on the list is installing a v7 distro. Hope someone take notice of the bug and fixes so we can use v8.

Cheers all!

---

### Post by karachuonyo on 2008-08-03
I think da_norf (no need to apologise being french, it's not your fault :lolflag:) may have something here. My mobo uses the KT 266 chipset and I experienced the same problem. Still does not explain why I never had any problem installing all the other Ubuntu versions except 8.04.
And in case someone still has the problem, just download and install Ubuntu 7.10 then do a distribution version upgrade. Works a treat if you have fast internet connection.

---

### Post by da_norf on 2008-08-06
> **karachuonyo said:**
> I think da_norf (no need to apologise being french, it's not your fault :lolflag:) may have something here. My mobo uses the KT 266 chipset and I experienced the same problem. Still does not explain why I never had any problem installing all the other Ubuntu versions except 8.04.
And in case someone still has the problem, just download and install Ubuntu 7.10 then do a distribution version upgrade. Works a treat if you have fast internet connection.

Hello everybody,

In fact, to be french is not a mistake as big as to think that Ubuntu v8.04 still uses VIA_IDE. In fact, since v8.04 (Hardy Heron), Ubuntu, as Fedora since v7, uses libata with pata_via module to handle disks accesses on VIA based plateform (like my Sony PCG-FR102).

So, for me, our problem definitively seems to be a compatibility problem between the pata_via module and some VIA chipsets (more reasonably the "southbridge" one than the "northbridge" one (as written in my first message)).

I've found [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639") which seems to lead to a workaround for Ubuntu 8.04. Perhaps, it's worth a try... (but it doesn't definitively solve the problem on Ubuntu nor on other distros).

---

### Post by cooke77 on 2008-08-29
When the "Language" windows shows,wait till it is nearly ended. 
Press 'ESC'......to bring up the CD's 'direction' window.
You get,....
 "Install to Hard-drive from CD.", etc.
Take notice of the "Check CD, for errors." option.
Run this, to check out your 'burnt' CD.
Bet there are a quite 'errors'...involved. (To explain away "why' you can't install.)

---

### Post by Aleksey1977 on 2008-09-03
This is definitely not the case in my situations. I have attempted installing from multiple CDs, burned at low speed and checked for errors in the way described. Install has failed for each of those CDs, but still worked with 7.10 liveCD.

---

### Post by Aleksey1977 on 2008-09-12
Tried Intrepid Alpha5, same problem. I have also tried using all_generic_ide boot option, but the system still freezes at Copying Files.

---

### Post by netdevil_germany on 2008-12-18
Hi guys - old thread but still same problem: I haven't had any luck installing 8.04, 8.10, nor OpenSuse 11+ on my laptop (Old Gericom ALSO with that %^&*& VIA KT 266). The LiveCDs always work as long as no writing on any harddisks is involved, as soon as I try to install the computer freezes. I do firmly believe that the root of the problem is a faulty VIA driver... I have no idea how to bypass that though - it worked up to Ubuntu 7.10. There are so many outdated packages though by now that I would REALLY like to switch to something a little bit newer...

Is there any way of using the OLD VIA driver instead of the new one?

---

### Post by netdevil_germany on 2008-12-19
Problem SOLVED!!

You guys were absolutely right. I just installed OpenSuse 11.1 which had crashed during install, just as Ubuntu 8+ had. But I noticed that it crashed only as soon as something substantial was written on the HDD, or the HDD was accessed for a longer time.

The solution, which should also work with Ubuntu: boot with "brokenmodules=pata_via". I did not have to turn off ACPI. I installed no problem and runs smoothly.

Thanks everybody for pointing me in this direction - I had tried for months.

---

### Post by Aleksey1977 on 2008-12-24
brokenmodules=pata_via did not work for me, not with Ubuntu 8.10, not with OpenSUSE 11.1 (I used Gnome LiveCD - netdevil, is that the one you used?).

Another strange thing is that for ```
lsmod | grep pata_via
```, I get:  

```

pata_via     16132  2
libata      177312  3 pata_via,pata_acpi,ata_generic

```

Also, for ```
modprobe -r pata_via
```, I get ```
FATAL: Module pata_via is in use
```

even with brokenmodules=pata_via option.

---

### Post by netdevil_germany on 2008-12-24
Hey Aleksey,

I tried the Opensuse Gnome Live CD - which did not work - then used the DVD version and it worked with the broken modules switch. In fact, I installed it twice in a row, just to make sure (once with noacpi and the other time with acpi). I am not sure how well the LiveCD would work since it boots a whole X server. Maybe that's why grep still reports the pata_via driver.
The DVD seems to be the better choice.
Hope that helps a bit - the download is a little longer but it worked for me great. And I finally have a stable and up-to-date Linux on my laptop ;)
Not sure if there is a way to make Ubuntu work that way - I am skiing in the Rocky Mountains right now (brrr... cold!) - but I will file a bug report once I get home next week.

---

### Post by Aleksey1977 on 2008-12-25
I have tried the same thing with OpenSUSE 11.1 DVD (well, almost, I used brokenmodules=pata_via acpi=off), and it *did* work for me, the install was successfull!

Now, the only thing left to do, is figure out how to load via82cxxx instead of pata_via for Intrepid...

---

### Post by netdevil_germany on 2008-12-28
Just another thought Aleksey: Did you try the alternate install cd/dvd from Ubuntu? Maybe that'll work with the brokenmodules-switch?

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by Aleksey1977 on 2008-12-31
I've managed to successfully install Intrepid using regular LiveCD by disabling DMA. The problem is, ide=nodma does not apply to libata. What I did, was

[LIST=1]
[*]Boot with "acpi=off break=top" boot options (acpi=off may not be needed, though)
[*]Once in BusyBox prompt, execute ```
echo 'options libata dma=0' >> /etc/modprobe.d/options
```
[*]Ctrl-D to continue
[*]From that point, install Ubuntu as usual.
[/LIST]

There may be an easier way to do this, but this method worked for me.

---

### Post by netdevil_germany on 2009-01-01
Great find! I will try that out too and see if it works on my laptop - having new/different issues right now ;)

---

