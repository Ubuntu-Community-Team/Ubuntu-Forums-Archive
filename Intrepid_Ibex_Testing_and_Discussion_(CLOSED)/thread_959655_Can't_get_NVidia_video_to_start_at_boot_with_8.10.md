---
title: "Can't get NVidia video to start at boot with 8.10"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by oliviercaro on 2008-10-26
[not sure this is the right forum, but...]

Hello,

I've cruised all along the forums here and (as far as I can tell) have found nothing to help.

I just updated (a little early maybe...) to 8.10 doing a "update-manager -d" from my 8.04

Now when booting the system, I get almost no image (only 2 pixel lines at the top).

The only way to log in is to run in recovery mode. But then, no way José: even if I activate NVidia drivers (says I should use 173.xx) for my video board (built on a GigaByte), settings don't survive another boot.

Any help?

aTdHvAaNnKcSe (Thanks in advance, huh?)

---

### Post by ju2wheels on 2008-10-26
It may be a side effect of upgrading and not doing a fresh install. I have Intrepid working fine out of the box with an NVidia GeForce 8500 GT. What model card do you have? Did you trying reconfiguring xorg?

---

### Post by oliviercaro on 2008-10-26
> **ju2wheels said:**
> It may be a side effect of upgrading and not doing a fresh install. I have Intrepid working fine out of the box with an NVidia GeForce 8500 GT. What model card do you have? Did you trying reconfiguring xorg?

I should have suspected upgrading would be risky. But 7.10 to 8.04 was such a breeze...

I can't tell which NVidia since it's integrated to the mother board and I can remember which one purchased. As far as I know, it's a Gigabyte GA-K8N51GMF-9 that's supposed to include:
- AMD K8
- nVidia GeForce 6100
- nVidia nForce 430

don't ask for more, I'm more into Macs than PCs... :|

---

### Post by oliviercaro on 2008-10-27
I tried a ```
dpkg-reconfigure xserver-xorg
``` with no success.

Any help?

---

### Post by inkrypted on 2008-10-27
I believe that is 
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by oliviercaro on 2008-10-27
> **inkrypted said:**
> I believe that is 
sudo dpkg-reconfigure -phigh xserver-xorg

OK but I can't boot other than recovery mode so I suspect that these settings don't stay after rebooting.

I've booted in recovery mode and activated NVidia 177 drivers but then I get this stupid and useless 2 pixel display at the top of the monitor.

It seems that the resolution is correct (as far as I can tell) but it's all shifted up to the top of the screen.

---

### Post by ju2wheels on 2008-10-27
Try booting up a 8.10 live cd and see if your display shows up ok just to see that its indeed a side effect of upgrading and not a hardware compatibility issue.

---

### Post by ju2wheels on 2008-10-27
Hey I just realized this when I was going to get the latest image of 8.10 to put on my Macbook, but the 8.10 RC (which incidentally is most likely the same snapshot you upgraded to) has an issue with the nvidia drivers that wont be fixed until the final release in 3 days. So im not sure if thats related to your issue but I would guess it is.

When I installed 8.10 I was using Alpha 5 and Alpha 6 and those gave me no problems with my nvidia drivers, its in fact the same install im using now. Theres a link on ubuntu download page for 8.10 under known problems...

---

### Post by wykedengel on 2008-10-27
sincei have a nvidia card integrated into my laptop. i think i will wait until the final release to save myself the headaches.

---

### Post by klamari on 2008-10-27
Hi there

I struggeled a while with getting 8.10 (I use Kubuntu) to work on the NVIDIA drivers. Now I installed the 8.10 RC and still the same issues as in my previous posts. EnvyNG not working, after installing driver 177 with Jockey no graphical desktop ...but could go into TTY.

After changing the xorg.conf file to the following


> Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	BusID		"2:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Monitor		"Monitor0"
	Device		"Videocard0"
	Option		"AllowSHMPixmaps" "0"
	Option		"PixmapCachesize" "2000000"
	DefaultDepth	24
EndSection



things are working now.   :guitar:

Maybe the problem by oliviercaro with his settings
> I can't tell which NVidia since it's integrated to the mother board and I can remember which one purchased. As far as I know, it's a Gigabyte GA-K8N51GMF-9 that's supposed to include:
- AMD K8
- nVidia GeForce 6100   :confused:
- nVidia nForce 430   :confused:

are the same as mine, two cards installled and this needs clear specifications in the xorg.conf what to use, the default setup by 8.10 does seemingly have a problem here. 

As said above, thanks God my probs are solved, maybe this helps in this case as well, good luck!!!

Greetings

martin

---

### Post by oliviercaro on 2008-10-27
> **klamari said:**
> Hi there

I struggeled a while with getting 8.10 (I use Kubuntu) to work on the NVIDIA drivers. Now I installed the 8.10 RC and still the same issues as in my previous posts. EnvyNG not working, after installing driver 177 with Jockey no graphical desktop ...but could go into TTY.

After changing the xorg.conf file to the following


martin
I've done that and now... guess what? No display anymore.

Since I didn't set up ssh remote login neither telnet, I'm now stuck with a dead screen... but the web server is still alive.

Any idea?

---

### Post by klamari on 2008-10-28
Sorry for the dead screen!!

- Are you able to get to a virtual terminal (using ALT-F2 forinstance)?
- Did you set the right BusID for the graphiccard you want to use? (this can be found by typing > lspci in a terminal)?
- Can you boot in failsafe mode? (this should overrun your xorg settings and give you a desktop with basic drivers)?
- Sorry if those questions seem basic, just trying to figure out what went wrong.

Greetings

martin

---

### Post by oliviercaro on 2008-10-28
> **klamari said:**
> Sorry for the dead screen!!

- Are you able to get to a virtual terminal (using ALT-F2 forinstance)?
- Did you set the right BusID for the graphiccard you want to use? (this can be found by typing  in a terminal)?
- Can you boot in failsafe mode? (this should overrun your xorg settings and give you a desktop with basic drivers)?
- Sorry if those questions seem basic, just trying to figure out what went wrong.

Greetings

martin
Sorry too... :|

- no, the screen is definitely black and don't even know where I am
- I didn't copy/paste the settings but I adapted them to be more talkative and be sure there wouldn't be any duplicates (ie: GE1600 for the card)
- I didn't try recovery mode but failsave? where from?
- Don't be sorry for basic questions: I'm not a real beginner but I still need pointers to obvious things

---

### Post by klamari on 2008-10-28
From what I understand you upgraded on your PC. Maybe using the installCD gives you an opportunity to free some 2-3 GB on your harddrive by reformatting, then with a new (second) install you might have the chance to change the settings for the first install....hmmm, nothing else to recommend for now....just be sure you keep your /home for any data you might not want to loose.
Working with the latest technology is amazing, a steep learning courve but still dangerous, some people say "never change a working system".
I was happy as I installed  on a new partition, keeping WinXP, VISTA and Hardy (Ubuntu and Kubuntu) on the same system.
Hope there is not too much loss for you.

Greetings

martin

---

### Post by oliviercaro on 2008-10-28
> **klamari said:**
> From what I understand you upgraded on your PC. Maybe using the installCD gives you an opportunity to free some 2-3 GB on your harddrive by reformatting, then with a new (second) install you might have the chance to change the settings for the first install....hmmm, nothing else to recommend for now....just be sure you keep your /home for any data you might not want to loose.
Working with the latest technology is amazing, a steep learning courve but still dangerous, some people say "never change a working system".
I was happy as I installed  on a new partition, keeping WinXP, VISTA and Hardy (Ubuntu and Kubuntu) on the same system.
Hope there is not too much loss for you.

Greetings

martin
The fact is that I have to keep my web server as well as my personal data.

Is there a way to boot on the install disc and just ask to update to 8.10 final release?

---

### Post by AdrianVeidt on 2008-10-28
Use the guide I posted here:

[http://ubuntuforums.org/showthread.php?p=5952369#post5952369](http://ubuntuforums.org/showthread.php?p=5952369#post5952369)

---

### Post by klamari on 2008-10-28
I guess what will work is to include the partitions where your data is stored during a new install without formatting. 
I did an upgrade from dapper to hardy via internet (took a long time even with dsl), I am not aware this works via cd. 
If you have no screen anymore the update-option might be difficult, maybe someone else can help here as I am not a real expert....

all the best 

martin

---

### Post by klamari on 2008-10-28
uuups, Adrian was faster.........

---

### Post by simonjp on 2008-10-28
I've seen this problem come up a few times where others have had problems with the nVidia drivers.  I've experienced the 1 or 2 pixel screen at the top after upgrading 8.04 to 8.10.

See these threads:

No Desktop Effects after upgrade to Intrepid - [http://ubuntuforums.org/showthread.php?t=958571](http://ubuntuforums.org/showthread.php?t=958571)

nVidia GeForce 6100 woes - [http://ubuntuforums.org/showthread.php?t=929610](http://ubuntuforums.org/showthread.php?t=929610)

Personally I'm going to wait until the 8.10 is released officially and try the LiveCD

---

### Post by oliviercaro on 2008-10-28
Thxs guys,

I'll give try to these links. If it doesn't help, I'll FTP the necessary folders on my Mac and put them back when 8.10 release correctly installed.

Will let you know

---

