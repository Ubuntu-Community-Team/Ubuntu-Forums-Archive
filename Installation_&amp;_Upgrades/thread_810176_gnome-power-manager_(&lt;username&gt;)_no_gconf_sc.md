---
title: "gnome-power-manager: (&lt;username&gt;) no gconf schema installed!"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by vonGrepa on 2008-05-28
Hi there.
Ive just installed ubuntu on an old laptop I had laying around.
The installation went just fine and the computer worked without any problems.
After a while the update manager tells me there are 71 updates that are either critical or recommended. Since Im all new to ubuntu and linux I figured it would be best to do what it said...

I downloaded and installed all 71 updates. When it was finished i told be that there where 2 updates that did not install ok. I did not write down the error messages because i belived that if they failed they would just appear on the update list again after the reboot that the system told me to do.

After restart and log on I get an error messages telling me that the GNOME Power Manager did not install as it should. The desktop looks strange (other icons) and I get no icons in menus etc.

Also, before the update when i pressed the icon for shutdown I got an screen with several options like hibernate, restart etc. Now the icon is a green running man, and when pressed I get thrown out to the log on screen where I can go on options and choose reboot. 

When I looked in the system log for messages I found this one:
"May 28 06:08:09 <computer-name> gnome-power-manager: (<username>) no gconf schema installed!"

Does anyone have a tip on how to fix this? Please keep in mind that I'm all green :-o 

Specs:
Compaq Armada M700
Mobile Pentium 2 @ 400Mhz
320Mb of internal memory
Running on powersupply
(yes it worked, but was slow :-)

/vonGrepa

---

### Post by vonGrepa on 2008-05-28
Hi, now its gone from bad to worse :-(

I google and searched the forums a bit and come to the conclusion that i could do the following:

```
apt-get install -f
```
 
```
apt-get remove gnome-power-manager
```

```
apt-get install gnome-power-manager
```

All went okey, and i rebooted the machine. The log on screen came up, but after logging on all i get are a beige background image and a mouse pointer.. no menus, no programs no nothing..  

Anybody got any ideas about what I should do now? I got logs from running the commands, but I cant get to em since I cant see my desktop...

This thread should probably have been in the complete beginners section.. sorry about that...

/vonGrepa

---

### Post by rufus25 on 2008-06-05
I had a similar problem. I removed gnome-power-manger with:

```
sudo apt-get purge gnome-power-manager gnome-applets
```

And reinstalled with:

```
sudo apt-get install gnome-power-manager gnome-applets
```

Fixed my error message but I got the same problem you have. Problem is, purging gnome-power-manager removes more packages than just gnome-power-manager, so you have to re-install them too. I was in a rush (I know bad thing when meesing with stuff like that) so I don't know exactly wich packets get purged along wit gnome-power-manager :roll:

But gnome-session get purged for sure. Installing it seemed to fix it for me: ```
**sudo apt-get install gnome-session**
```


Maybe someone can run a test (-s = just a simulation) and tell us, wich packets where purged, just to be sure.

```
sudo apt-get -s purge gnome-power-manager
```

---

### Post by Kimos on 2008-06-05
I'm having a similar problem, posted in this thread:
[http://ubuntuforums.org/showthread.php?p=5120342]("http://ubuntuforums.org/showthread.php?p=5120342")

I installed many updates over an unknown amount of time, then when I restarted power management failed and I'm getting a bunch of Gnome UI problems. Looks like these are all related, likely to some update.

I don't have a resolution yet, but I can at least provide you with this:
```
kevin@sephiroth:~$ sudo apt-get -s purge gnome-power-manager
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  gnome-power-manager* gnome-session* ubuntu-desktop*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Purg ubuntu-desktop [1.102]
Purg gnome-session [2.22.1.1-0ubuntu2]
Purg gnome-power-manager [2.22.1-1ubuntu4]
kevin@sephiroth:~$
```

---

### Post by rufus25 on 2008-06-05
Thanks Kimos! I missed th *ubuntu-desktop* package.
So, my problem with the gnome-power-manager is solved :)

@Kimos: I will take a look at your thread, seems I got the same problems.

---

### Post by Kimos on 2008-06-05
> **vonGrepa said:**
> When I looked in the system log for messages I found this one:
"May 28 06:08:09 <computer-name> gnome-power-manager: (<username>) no gconf schema installed!"

Resolved! Thanks to this thread:
[http://ubuntuforums.org/showthread.php?t=127660]("http://ubuntuforums.org/showthread.php?t=127660")

Basically, something caused some/all of the gconf schemas to become unregistered. To re-register them run:
```
cd /usr/share/gconf/schemas/
sudo /usr/sbin/gconf-schemas --register *.schemas
```

Restart X or your machine. My system came back up good as new after that!

---

### Post by CSEatOSU on 2008-06-13
I'm having the same problems.  Blank screen with just the mouse...  I'm using my laptop now.

I understand I'm supposed to do the steps above, but how do I get to a terminal to run if I can't get to a desktop?

Thanks.

---

### Post by CSEatOSU on 2008-06-13
AH HA!!  I got it, thanks to all the posts above.

---

### Post by stuaxo on 2008-12-29
I did a really silly thing and deleted the schemas file after getting these errors.

To fix it:

Navigate to the /usr/share/gconf/schemas folder in the terminal

I downloaded a gnome-power-manager.deb then browsed inside using 'mc' (midnight commander - apt-get was working enough to install this)

Then find the file by browsing inside the deb, and copy it over the original.

Now apt-get was working enough that I could try the other steps in the above posts

---

### Post by tomthumb99 on 2009-01-27
Folks, had this prob and your thread greatly helped, thanks. I now get the gnome screen with icons and fonts...  It looks like I have two corrupted schema files that appear to need an overwrite. The re-register of the schema file jumped out.  I ran a 'dpkg -c gnome-power-manager_2.24.0-0ubuntu8.1_amd64.deb' file, I did not see the schema files present.  The simple re-install of the gnome-power-manager failed multiple times. Can I get more details on how to pull them out of th deb file for an overwrite.

Thanks,

---

### Post by marina123 on 2009-03-18
I am having the same issue with booting from usb stick. I get in the end a black screen. How can I solve this problem? When I tried to boot from livecd and see the contents of the usb stick I don't see anything related. I tried to put in grub.conf menu.lst acpi=off but it didn't help. Need urgent help. First time it booted from usb, 2nd time I got this error and a black secreen with the arrow of the mouse. 

Thanks a lot in advance

---

