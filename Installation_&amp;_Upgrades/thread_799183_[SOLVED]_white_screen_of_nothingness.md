---
title: "[SOLVED] white screen of nothingness"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by Stolea on 2008-05-18
I just installed Ubuntu 8.04. It all started up fine and it notified me that there were some updates which I downloaded, including an Nvidia 3d driver.
On system restart I got to the bit where the startup sound plays and then I have a nice plain white screen with my mouse pointer. Makes a pleasant change from the windoze blue screen of death, but is pretty much the same outcome.:(
At a guess, its the graphics card driver that is causing the problem.
How do I reverse the install, or should I just reinstall?

---

### Post by iaculallad on 2008-05-18
This might be an issue of Compiz/Desktop Effect. Try doing this:

- Do wait for the normal login sound to finish. Give, say, 15 seconds for all the desktop component to load.
- Press Alt+F2 to launch the "Run Application" dialog box. Dialog box would be in the background of your "White Screen" but its there.
- Try entering: metacity --replace then press Enter key.

 That would probably bring back your GUI.

---

### Post by vrangforestillinger on 2008-05-18
Yes. This looks like a bug many nvidia-users experience.

For me, this happens when I bring the computer back from hibernate, when Im switching users or whenever the screen is locked. The screen will be totally white, but the mouse is visible. When moving the mouse to somewhere in the middle of the screen, it changes to a text-cursor. This is where my password-prompt would normally be when the screen is locked. When clicking that invisible area, entering my password, the screen is unlocked, and Im back to the desktop again.

(If this is the case for you as well, then Alt+F2 won't bring up Run Application.)

As iaculallad wrote, changing to metacity (turning off 3d desktop effects) probably will fix the problem. I do this in the "Desktop Effects" tab of the "Appearance" menu. The command "metacity --replace" does the same job, but im not shure if the change will persist in the next login unless you do it from the appearance-menu. (Correct me if Im wrong.) If you have run "metacity --replace, then you might need to change this setting on and off for it to persist in next login.

Personally, I keep the effects on, knowing how to unlock the screen blindfolded.

(Launchpad entry here for more techy stuff: [Bug #160264]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/160264"). Jugding by the comments, a fix is not far away from us end-users.)

---

### Post by zhuqing123 on 2008-05-18
The fourth [wow power leveling](http://www.wow-powerleveling.org) latest game in [wow power leveling](http://www.xowow.com) Warcraft series is ‘[wow power leveling](http://www.powerlevelingweb.com)’. Also known as [wow power leveling](http://www.igsstar.com), it represents a [wow power leveling](http://www.wowgoldweb.com) multiplayer online [wow power leveling](http://www.powerleveling-wow.com/siteMap.asp) game, the best of [wow power leveling](http://www.powerleveling-wow.com) kind. Initially, it was [wow gold](http://www.wow-powerleveling.org) it be released in 2001, but [wow powerleveling](http://www.powerleveling-wow.com) was delayed [wow powerleveling](http://www.powerlevelingweb.com) 2004, thus [wow powerleveling](http://www.xowow.com) the 10 years of[wow powerleveling](http://www.wow-powerleveling.org) franchise of this[wow gold](http://www.xowow.com) series. The [world of warcraft power leveling](http://www.powerlevelingweb.com) was not [world of warcraft power leveling](http://www.wow-powerleveling.org/wow+power+leveling.html)fulfilling, because [wow power level](http://www.powerleveling-wow.com/siteMap.asp)problems with [wow power level](http://www.powerlevelingweb.com) server’s stability [power leveling wow](http://www.powerleveling-wow.com/siteMap.asp) performance occurred, but [power leveling wow](http://www.xowow.com) game still [power leveling wow](http://www.powerlevelingweb.com) a financial success [powerleveling wow](http://www.powerleveling-wow.com/siteMap.asp) the most [powerleveling wow](http://www.xowow.com) game of its kind. The number [cheap wow power leveling ](http://www.powerlevelingweb.com) users that play [Maple Story mesos](http://www.igsstar.com/Maple-Story-mesos-us/), exceeds 8.5 [MapleStory mesos](http://www.igsstar.com/Maple-Story-mesos-us/), worldwide.As a form [ms mesos](http://www.igsstar.com/Maple-Story-mesos-us/),recognition for [mesos](http://www.igsstar.com/Maple-Story-mesos-us/),outstanding popularity, the game [SilkRoad Gold](http://www.igsstar.com/Silkroad-Online-Gold/), received a[SRO Gold](http://www.igsstar.com/Silkroad-Online-Gold/), of awards. Now the question [eq2 plat](http://www.igsstar.com/EverQuest-2-gold-plat/), why is [eq2 gold](http://www.igsstar.com/EverQuest-2-gold-plat/), game [eq2 Platinum](http://www.igsstar.com/EverQuest-2-gold-plat/), popular? For anyone[EverQuest 2 Platinum](http://www.igsstar.com/EverQuest-2-gold-plat/), played the previous [EverQuest 2 gold](http://www.igsstar.com/EverQuest-2-gold-plat/), and [EverQuest 2 plat](http://www.igsstar.com/EverQuest-2-gold-plat/), already initiated [lotro gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), the mysterious world [lotr gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), the breathtaking [Lord of the Rings online Gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), this [Rolex Replica](http://www.watchreplicashop.com/) nothing but an [Replica Rolex](http://www.watchreplicashop.com/) adventure that continues the story of ‘Warcraft III: Frozen Throne’, four years after conclusion, in the world of Azeroth. The game is online role-playing, the previous versions being online and offline strategy games. The major thrills and unique features are present as in every Blizzard game.

---

### Post by Stolea on 2008-05-18
Thanks for the help. Unfortunately none of the suggestions helped. Seeing that it was a brandnew install and nothing was going to be lost, I did a reinstall. 
Windoze has the safe desktop that will let you boot into a standard VGA setting to uninstall a patch or install a better version.
Is there a way to roll back an update?

---

### Post by iaculallad on 2008-05-19
If its the "Kernel" update, fortunately on newer kernels, Ubuntu offers a rollback option. Update manager will not automatically delete installed old kernel. If problems comes along, you can easily boot into the old kernel via the Grub menu at boot up.

---

### Post by Stolea on 2008-05-19
This is the current version of 8.04. I would imagine that its the latest version.
The grub lists ubuntu, ubuntu recovery?, ubuntu memchecK? and windoze.

---

### Post by vrangforestillinger on 2008-05-19
Seems to me the nvidia-driver is causing the problem, since it worked before you downloaded the driver. (You had to enable the driver in the restricted drivers menu?) When you are finished booting into the loginscreen, press Ctrl+F1. This will give you a commandline interface where you can change the screensettings.

If Ctrl+Alt+F1 does not give you a commandline, you can go into ubuntu recovery, which is a command line with root access. (I.e. no need to use "sudo".)

Once you are in a commandline, you can set the xserver back to generic settings by running
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If you remove the -phigh, you will be able to configure more aspects of the xserver manually (keyboard etc.).

Now, go back to the login with Ctrl+Alt+F7. Restart the xserver by pressing Ctrl+Alt+Backspace. (Or reboot into normal ubuntu if you are in recovery.) Hopefully, the GUI should work now when you login.

You can remove the now unused nvidia-driver with
```
sudo apt-get remove nvidia-glx-new
```
assuming that you are using the new driver. There is also nvidia-glx or nvidia-glx-legacy.

Hope this helps. Otherwise, its beyond my knowlegde. Good luck!

---

### Post by vrangforestillinger on 2008-05-19
Oh, I see you reinstalled. Oh well. Hope you got things working.

---

### Post by Stolea on 2008-05-19
Thanks, I will keep a note of this suggestion. It would seem that my Nvidia card doesn't like that driver. In that desktop setting where you can define the graphics it will only let me use the basic setting. I guess its better than a blank screen. Its an Asus (Nvidia) 9550 128mb. Only about 12 months old.
I never thought that I would ever have to work with command lines again. Its fun though and gets the brain working again. Bit like rediscovering a lost cellar. :)

---

