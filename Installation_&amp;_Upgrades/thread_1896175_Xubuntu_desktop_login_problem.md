---
title: "Xubuntu desktop login problem"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by onebir on 2011-12-16
I installed xubuntu-desktop (over an ubuntu install with lubuntu-desktop installed) with *sudo apt-get install xubuntu-desktop*.

Although the install went fine, I still can't actually log in to a Xubuntu session (or Xfce for that matter). After entering username and password I'm just returned to the login screen.

It looks like a couple of other people have run into this problem*, but no fixes that worked (for me) have been posted so far.

Any ideas folks?

*Or similar? Like [this]("https://answers.launchpad.net/ubuntu/+source/xubuntu-meta/+question/176486").

---

### Post by onebir on 2011-12-17
Nobody else has come across this problem? I thought there would be quite a lot of defectors from Unity/Gnome 3...
:confused:

---

### Post by onebir on 2011-12-17
Someone else does have this problem:

[http://ubuntuforums.org//showthread.php?t=1864884](http://ubuntuforums.org//showthread.php?t=1864884)

---

### Post by cl8t0n on 2011-12-18
Since no Ubuntu users are responding, maybe a Debian user without an Ubuntu installation on hand can take a swing at it.... ;)

So to clarify, I assume you are not totally dead in the water and completely unable to login to X on this installation???  If so, on Debian I would press Ctrl-Alt-F1 to get right out of the window manager mess and to a terminal. You can then get back to X with Alt-Fx, probably F7 or F8.

Then I might try a generic window manager or three, ie.

apt-cache search display manager  --then, for instance--

apt-get install xdm  --or--

dpkg-reconfigure xdm

and see if any of them will handle the situation any better. Theoretically they should all be totally separate and not step on one another's toes. (If that is what is happening here, I would suggest filing bugs with the offending window manager(s) on Launchpad, which might get you a direct response from the developers. Never be shy about filing bugs if you think something is broken.)

If none of that works, and you are not on the latest version of Ubuntu, I would contemplate an upgrade to the next version of ubuntu. If you are on the latest stable version of Ubuntu, as a Debian user in a similar situation, I would be tempted to try and pull from unstable. Ie. temporarily change sources.list to whatever your current unstable development dist is called, and try to pull newer versions of the buggy display managers from there:

apt-get update
apt-get -t <name-of-unstable-dist> install <name-of-window-manager>

Note that this is potentially dangerous and might b0rk your installation, depending on how unstable Ubuntu unstable really is (Debian unstable tends to be not so unstable, for the record, and I do this quite regulary) so backup first, and if you are risk-averse and your current problems are mostly cosmetic, only pull those unstable packages if they do not try to bring a lot of other dependencies with them.

If all of the above fails, then you have a serious debugging session on your hands, I am afraid, possibly involving much poring over log files, and maybe downloading the sources and attaching gdb.... And file bug reports!!!

---

### Post by MAFoElffen on 2011-12-18
Ouch, xdm is not relative to Xubuntu nor Ubuntu. Think GDM or lightdm... but that's not what the problem is with the OP's...

This problem does happen in all variants (even with only one desktop enviroment) and the solution is really very simple:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Reseting Authories Profile For Logging into X]("http://ubuntuforums.org/showpost.php?p=11404605&postcount=766")**[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by onebir on 2011-12-19
Thanks cl8t0n and MAFoElfen.

I had been able to log into Lubuntu/LXDE (& Ubuntu, but it wasn't working properly). I had the apparently bright idea of uninstalling Xubuntu piecemeal, but I think something in the first few lines [here]("http://www.psychocats.net/ubuntu/puregnome") uninstalled LXDM. A dialog appeared asking to choose between GDM and lightDM. Both were installed (I checked with dpkg --get-selections).

I opted for GDM, and after that could only log into the recovery command line. But it seems to be impossible to do much from there (couldn't get the wireless network up with ```
ifconfig wlan0 up
``` or even mount an external USB drive.

So I gave up, backed up my data, stuck xubuntu 11.10 on a USB stick and reinstalled. So far so good (more or less).

Unfortunately that means I can't really confirm if MAForElffen's diagnosis(/solution) was correct.

But as I understand it, all the ubuntu desktop flavours should be able to coexist seamlessly? So this is a bug? (If so I'll report it.)

Anyway, thanks again guys! :)

---

### Post by onebir on 2011-12-20
> **MAFoElffen said:**
> Ouch, xdm is not relative to Xubuntu nor Ubuntu. Think GDM or lightdm...

BTW, the original post mentions [**L**XDM]("http://blog.lxde.org/?p=531"), not XDM....

---

### Post by cbeer86 on 2011-12-20
I'm having a similar problem.

I've been putting together a file server on xUbuntu 11.10, and everything had been working fine.  Then, I switched my account to not ask for a password at login to facilitate using xvnc11.  After doing this, I have the same problem trying to login to my account.  I can start an xUbuntu session as a guest or login to my account in a text terminal, but trying to login normally I just get bounced right back to the login prompt.

Any help would be appreciated.

---

### Post by MAFoElffen on 2011-12-20
> **onebir said:**
> BTW, the original post mentions [**L**XDM]("http://blog.lxde.org/?p=531"), not XDM....
That was directed at cl8t0n's suggestion to install "xdm" in post 4(?). Just for "in case" reference...
```

sudo dpkg-reconfigure <package>

```
for instance using lightdm as the package, would have brought up dialog asking which Deskop Manager you wanted to use...

---

### Post by MAFoElffen on 2011-12-20
> **cbeer86 said:**
> I'm having a similar problem.

I've been putting together a file server on xUbuntu 11.10, and everything had been working fine.  Then, I switched my account to not ask for a password at login to facilitate using xvnc11.  After doing this, I have the same problem trying to login to my account.  I can start an xUbuntu session as a guest or login to my account in a text terminal, but trying to login normally I just get bounced right back to the login prompt.

Any help would be appreciated.
While logged in on that tty text terminal:
```
[FONT=monospace]
[/FONT]sudo rm .Xauthority* 
touch .Xauthority 
chmod 600 .Xauthority
sudo shutdown -r reboot

```That should reset the authorities profile for X.

If that doesn'r work... At the Grub Menu, select Menu Item 2, Recovery. When the recovery menu comes up, select the last menu item, "root". > When it gets to the root prompt:
```

service lightdm start

```Modify lightdm to whatever Desktop manger you use, such as lightdm, gdm, kde, xdm, etc...

When the Desktop starts, go to Users and Groups. Select your Username. Check "Ask Password at Login." Shutdown/Reboot.  Test and see what is going on.

I can see where my where you want to have graphical remote access to it.  My server bounce back up after a power failure (even though I have UPS), but all the services are there without anyone logging in locally. (You see the boot messages right?) 

I personally think that auto-logon is both a security risk and liability when things go wrong and you have to diagnose them.

---

### Post by onebir on 2011-12-20
> **MAFoElffen said:**
> That was directed at cl8t0n's suggestion to install "xdm" in post 4(?). Just for "in case" reference...
```

sudo dpkg-reconfigure <package>

```
for instance using lightdm as the package, would have brought up dialog asking which Deskop Manager you wanted to use...
Oh - I see.

> ```

sudo dpkg-reconfigure <package>

```
for instance using lightdm as the package, would have brought up dialog asking which Deskop Manager you wanted to use...

I think that must have been the dialog I mentioned a couple of posts up.

Interested to hear if resetting X authorities will fix cBeer's problem.

---

### Post by paul6 on 2012-02-15
onebir, I share your pain.  :frown:

I installed Xubuntu over Lubuntu  (after seeing some cool Xubuntu videos on Youtube), and it won't let me login to Xubuntu.

I tried MAFoElffen's code to reset Xauthority - still can't login.

I probably will end up reinstalling Xubuntu like you did, which is disappointing to me since I've spent nearly a week configuring Lubuntu to my preferences.

Oh well, live and learn :D

---

