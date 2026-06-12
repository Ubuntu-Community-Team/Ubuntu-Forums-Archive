---
title: "Please Read if you experience a Blank Screen when booting Edgy LiveCD or Install"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by Aikon- on 2006-11-01
**[COLOR="red"]UPDATE:[/COLOR]** The status of the bug report listed below has been updated thanks to Mark Reitblatt, bug triager, as follows:
[LIST]
[*]Importance: Undecided => High
[*]Stauts: Unconfirmed => Confirmed
[/LIST]

Please read the description carefully. There are several different problem-states that exhibit similar behaviour, but this one is quite specific.

If you are experiencing the **same issue**, please post here to confirm the bug. Please include your system specs. Please post the same comment to [this official bug report]("https://launchpad.net/distros/ubuntu/+bug/67487"). The more systems experiencing these symptoms that are recorded, the more likely this problem is to be fixed in future releases. Note that the bug report is still listed as "Unconfirmed" and of importance "Undecided". We feel that by this point this bug ***has*** been confirmed, and considering that the first thing potential Ubuntu users are going to try is the LiveCD, that it is also ***quite important*** to address this issue.

**Symptoms:**
[LIST]
[*]When booting Edgy from either the LiveCD or an installed system, you receive a blank screen after the boot phase, just as the GDM should be starting
[*]You do not hear the Ubuntu startup sound
[*]You cannot get a terminal using Ctrl-Alt-[F1-F6]
[/LIST]

**Cause:**

This is caused by poor configuration of the default X server in Edgy. The problem appears to be with the ATI graphics drivers, and until now has only been experienced on systems running ATI graphics cards. It is likely this bug was missed due to insufficient testing with a variety of ATI graphics cards.

**Workaround:**
[LIST]
[*]There is currently no workaround for booting the LiveCD since one cannot reach a terminal to alter driver settings or Xorg configuration.
[*]On installed systems, it should be possible to change the driver in xorg.conf to "VESA" instead of "ati", or to install the fglrx driver and change the driver to "fglrx". This should fix the problem on installed systems.
[/LIST]

Notes: The original thread can be found [here]("http://www.ubuntuforums.org/showthread.php?t=281111").

-Aikon

---

### Post by tedwick on 2006-11-01
well, that's comforting to know... too bad there's nothing to be done.

---

### Post by fletchinho on 2006-11-01
experienced the same issue, since forever.

i did have the same issue when i install fc4/fc5/fc6 but luckily they have text installation option. i tried to do the same with drake/eft but couldn't find the option, so i just stick with fedora.

in fedora, after text installation it brings straight to init 3, so i just edit xorg.conf file to include ```
Option "MonitorLayout" "LVDS"
```, change to the correct graphic card and change the screen resolution.

how do i do that in ubuntu? looking forward to migrate.](*,) 
btw, i'm using Acer notebook with ATi Mobility Radeon X700.

---

### Post by akijikan on 2006-11-01
how do I install fglrx drivers?  I tried changing xorg.conf to vesa, but it didn't work.

is it
```
$ sudo apt-get install fglrx
```?

---

### Post by Handssolow on 2006-11-01
I've already posted about this issue that I've got with my wife's PC. Unable to install Edgy because of the "out of range" error from the monitor during install plus I'm unable to access xorg.conf, I'm stuck also with my fall back install of Dapper but I cannot configure her Broadcom 4306 card.

My wife's PC- 
Asus A7V800 mobo, a Desktop PC,  AMD 2.4Ghz Athlon mobile,  1Gb Ram, ATI Radeon 9600 AGP x4.

Usually it runs XP from from the IDE HD but my first step is to attempt to install Ubuntu on a Sata HD. I've been disconnecting the XP IDE drive until I solve the Ubuntu install problem and wireless connection.

At least I've one of our PCs running Edgy Ubuntu but I did choose to upgrade it with an nvidia 6600gt graphics card. I wonder why !!

Help with an Edgy install on a PC running an ATI Radeon 9600 would be appreciated.

---

### Post by sloggerkhan on 2006-11-01
[http://ubuntuforums.org/showthread.php?t=281111&page=3](http://ubuntuforums.org/showthread.php?t=281111&page=3)
original thread with POSSIBLE workaround.

I didn't have this issue with 6.06, whoever was saying that past version had a problem....

---

### Post by dakini on 2006-11-01
I have ati drivers and I have had intermittent problems with this through all Edgy releases, including the final.  The early knots, I could rarely get past the black screen. Beginning with either Knot 3 or Beta, it rarely happened. In the early knots, I was able to bypass the problem by using acpi=off as a boot parameter. With the later knots, beta, etc, the acpi=off didn't work. I've done a *lot* of edgy installs on my hp zv5120us laptop.

On the other hand, the alternative install disk, from early on, was almost aways successful. Also, somehow or other, by burning a new disk or altering the boot parameters, I've never been unable to install.

---

### Post by Cable on 2006-11-01
I experience this issue as well.  It happened with both Edgy and Dapper.  However, I was able to boot into Edgy using either the beta or RC CD (I can't remember which) via the safe graphics mode, but the final LiveCD did not work.  I installed both Edgy and Dapper via the alternate CD without difficulty.

LiveCD's of other distro's work fine.  Ubuntu's is the only one I have ever had problems with.

---

### Post by BobBlum on 2006-11-03
I read this on element14.wordpress.com.  It was suggested by a posting on [http://www.planetmy.com/blog/](http://www.planetmy.com/blog/).  It worked for me.

-  When you get the blank screen upon bootup of Edgy, press enter to get a login prompt.

-  Supply your user login and password.

-  Then type the following:  sudo apt-get install xserver-xorg

-  Then type the following sudo rm /tmp/.X0-lock

That should solve the problem.

This Ubuntu/Kubuntu upgrade is truly a disgrace to the folks who designed it.  I had exactly the same upgrade problems with both the Ubuntu and the Kubuntu iterations of it.  Even after gaining access to the desktop using the method described above, the fonts and other parts of the configuration were a mess.  I can't even calculate the time I have spent on this upgrade.  It is still not right.  There are broken files (kdemultimedia) and in Nautilus and Konqueror, the navigation panel does not show the entire tree stucture from the top of the tree:  it shows only the Home and the Media directory.  To even see the full complement of files, you must click on "View" (on the top-line menu) and select "Show Hidden Files," even though these are not hidden files.  This upgrade has lessened my respect for the Ubuntu developers.  I'm seriously considering switching to PCLinuxOS, which installed and ran nearly flawlessly.

---

### Post by yalding on 2006-11-04
Oh, poor ATI users including me. The edgy upgrade break my two systems. I had to reinstall them with Dapper. Now I am happy with Dapper again.

---

### Post by chiselwright on 2006-11-18
I've seen something that sounds a lot like this and *I'm **not** an ATI user!* Booting off of the 6.10 LiveCD goes fine [which is a step up from 6.06, as it didn't recognise my SATA CD/HDD drives properly] - I see the Cylon-Bar for a minute or two while Ubuntu loads.

At the end of the process when it's switching to X my monitor goes blank, a monitor message appears "Out of Range" followed shortly by the start-up chime.
I didn't think at the time to try ALT+F1 for a terminal screen.

I rebooted, modifing the boot parameters to NOT use *splash*, then used "sudo dpkg-reconfigure xorg-xserver" to generate a useable xorg.conf.
Playing it safe I used the vesa driver and not the nv driver.

---

### Post by Windows_Is_God on 2006-11-18
I am trying to boot Ubuntu from the LiveCD to test it when I get a blank screen. I hope there is a way to solve it lol. Here are my system specs:

Graphics card: NVIDIA GeForce4 MX 440 with AGP8X
RAM: 512Mb
CPU: 1002Mhz (1Ghz)
Current OS(s) installed: Windows.

I would like to add Ubuntu as a second OS on a partition.

---

### Post by chiselwright on 2006-11-18
I've just rechecked, and the absolute minimum I need to do to get from the LiveCD xorg.conf to a useable/working xorg.conf is remove "1600x1200" from the modelines. No need for dpkg-reconfigure.
I don't know if the nv driver just can't output properly at 1600x1200.

To actually boot the system, I removed *splash* (as mentioned previously) *and* *quiet* from the boot parameters [F6].


I should probably have mentioned my system specs in my last post too:

Graphics Card: NVidia GeForce 7900GT
Monitor: ViewSonix 20" 2030b LCD
RAM: 2GB
Processor: AMD Athlon 64 3500+

---

### Post by Benchrest on 2007-04-13
The bug report for #67487, blank screen trying to boot 6.10 live cd has a workaround in the bug report. I have tried it and it worked for me. I set AGP to 4X in bios. This problem seems to effect many ATI graphics cards including Radeon XT that I have. May effect those running ATI agp 8X. Thought I would post this since there are so many post regarding this issue and it leaves one dead in the water without this work around.

---

