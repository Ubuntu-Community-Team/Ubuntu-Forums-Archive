---
title: "Mint 8: Standard user missing elevated group permissions"
date: 2015-02-14
forum: MINT
---

### Post by OS/2-User on 2015-02-14
After some weird GUI freeze-up the other day, which required power-cycling to reboot, Karmic Gnome now gets stuck after switching to GUI mode with the small spinning wheel, right before the XFCE log-in screen is supposed to appear. 

Back then a few years past:
Due to Gnome power management issues, I added XFCE back in the day to use its version, but came to miss too many Desktop features compared to Gnome to stay with the XFCE desktop. So after a little while, I switched back to the Gnome Desktop, yet kept the XFCE power and also the network manager, since they often worked more reliable than Gnome's. 
But in the process, I got stuck with XFCE's blue mouse log-in screen and the Gnome session manager not working anymore.

Now and here again:
Log-in as root in a console works as usual. 
Log-in from a console as the regular user works now only partially (see attached screenshot). 
[ATTACH=CONFIG]259981[/ATTACH]Apparently the user's group permissions for root owned executables and directories are not being issued, so nothing that is owned by root (like i.e. /usr/bin/env, cal, lsusb or bc) can be accessed or executed. However, 'echo $PATH' shows that path is set correctly and works for the user's own files and executables.

Since I don't know about the inner workings of the log-in and start-up process, there might now a needed config file now be missing or corrupted somewhere. 

Sifting through dmesg and the most recent log files in /var/log/ I didn't come across anything that jumped right at me, but then again, I don't really know what exactly I would have to be looking for, if there actually would be any record of my current problem being recorded.

- How can I start the Gnome desktop from there and work as the now defunct user?
- How do I check for the regular user's group involvements and what should they be?
- Is it possible, to fix or recreate the current user account log-in data without damaging/deleting its existing files and settings, to see, if that would fix things?
- If not, what do I have to look into, to find out why the user account doesn't get those elevated group privileges for root owned files any longer?

Please be detailed and provide step by step instructions for where to go and what to do.

Thanks in advance

---

### Post by grahammechanical on 2015-02-14
I was wondering what Karmic Gnome was because Karmic was part of a code name for a release of Ubuntu 10 releases back. but I see from your screenshot that you are using Linux Mint and not Ubuntu Gnome. Also, you are able to login under the username of wolfi.

Other than that I cannot add anything more as I have absolutely no experience with Linux Mint.

Regards.

---

### Post by OS/2-User on 2015-02-14
Before the days of Ubuntu's Unity and switch to Gnome3, LM was very closely based on Ubuntu. So whatever was/is valid for Ubuntu 9.10/Karmic Koala, should also apply for LM8 at this level, where I now have problems.
And as I said, standard user 'wolfi' can log-in, but apparently doesn't have any longer the group privileges to access files that require more than his own access levels in f.e. /user/bin/, like some sudo or admin level stuff.

---

### Post by QIII on 2015-02-14
Karmic Koala is long past its End Of Life, as I imagine that version of Mint, which was based on Karmic, would be.

I suggest it might be better to get help in securing/recovering your files an updating to a new version rather than asking people to remember what might have been a solution over 5 years ago.

Would you prefer to do that?

You might also want to see if someone can help you on the [Mint forums]("http://forum.linuxmint.com").

---

### Post by OS/2-User on 2015-02-14
I am aware of that issue ;-) and I was actually planning on updating to the current version level sometime around May or June, after it took Ubuntu a few years to get rid of several bugs, that have been introduced with Lucid and later. Those hit me really bad in a few few key areas, so I just kept what was working good enough since. Now it seems that since last summer finally the current distri is as good again as Karmic in the areas I am concerned with.

Unfortunately at the moment, I don't have the time to deal with the whole new setup, since it also requires some major rework in how my specific setup has to be done in order to work on this laptop. Right now, I just need the darn thing to work again as quickly as possible ;-)

Since I am rather optimistic that it is just only some missing group  level privileges, preventing my standard user to be operational again,  it should be a relatively easy fix. 
I am just not yet experienced in that area and still lack the skills to  check where what needs to be there and if not, how to reinstate those  group memberships again.

I just need a kind guiding hand, me thinks [IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG]

---

### Post by OS/2-User on 2015-02-16
> **QIII said:**
> Karmic Koala is long past its End Of Life, as I imagine that version of Mint, which was based on Karmic, would be.

Over the weekend I did some testing with the current LM 17.1 Live DVD and ran into new problems. Somehow Debian/Ubuntu doesn't seem to like AMD (Nforce2 Ultra 400 chipset with Athlon XP 'Barton' & Radeon  X800 GTO AGP  (R420)) at all anymore. I also have to use the kernel boot option "nomodeset".

- Totem plays regular x264 coded 720x408 mp4 video files only very choppy and hence unusable, VLC doesn't play at all, it just sits there with the very first frame displayed. Each one causes a 100% CPU load.
[ATTACH=CONFIG]260018[/ATTACH]
- Shutdown from the Desktop doesn't work, not even when additionally forced via Ctrl-Alt-Del or "# Shutdown Now" in a Terminal or Console. It just gets stuck:
[ATTACH=CONFIG]260019[/ATTACH][ATTACH=CONFIG]260020[/ATTACH][ATTACH=CONFIG]260021[/ATTACH]
So apparently upgrading to the current level is out of the question and it looks like I need to fix keep my vintage Karmic and keep it alive, since both of the above there works just fine.

I also found, that apparently all the required file entries and permissions exist. For whatever reason, they just aren't applied to the standard user anymore and that is what I need to find out and fix.

# adduser newuser --> reboot --> same problems (missing root privileges)

$ less /etc/group|grep -i wolfi ==> adm:x:4:wolfi
                    dialout:x:20:wolfi
                    cdrom:x:24:wolfi
                    plugdev:x:46:wolfi
                    lpadmin:x:104:wolfi
                    admin:x:115:wolfi
                    sambashare:x:120:wolfi
                    wolfi:x:1000
    
$ less /etc/passwd|grep -i wolfi ==> wolfi:x:1000:1000:WR,,,:/home/wolfi:/bin/bash

# less /etc/sudoers --> Defaults        env_reset
            # User privilege specification
            root    ALL=(ALL:ALL) ALL
            # Members of the admin group may gain root privileges
            %admin ALL=(ALL) ALL

# less /etc/shadow --> "root" and "wolfi" entries of same pattern do exist


- So, who can tell me how the boot process works and when and how those elevated "admin" group privileges are being assigned to the regular user account.
- How can I start the GUI from  a root console. "start x" doesn't work.

---

