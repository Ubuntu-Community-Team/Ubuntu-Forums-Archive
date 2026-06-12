---
title: "Still having Intrepid/KDE4.1 problems"
date: 2008-07-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xeddog on 2008-07-30
Am I the only one??

I installed intrepid/kde4.1 and still nothing that I want to do is working.  Here are the problems that I am having.

Adept_updater - Apparently the adept-notifier works because when I boot the system and let it set for a couple of hours I get the update icon in the lower panel.  But when I click on it to acutally do the updates nothing at all happens.

Adept add/remove programs - At least this one starts and asks for a password.  It then opens a window and the loading process begins.  But before the loading operation finishes, adept crashes.

KNetworkManager - When I try to do a manual configuration, absolutely nothing happens so I cannot set a fixed ip address.

Printing - When I try to add a printer and click on the "printing" application, I get the little jumping printer icon for a few seconds and then nothing.  

System settings - The window opens ok, but all options are greyed out.  ALL of them.  There is no place to unlock or enter the administraion mode so I cannot set the auto-login.

So I can't really do much with the system and I was hoping that updates would have helped by now, but nothing seems to have changed at all.  Any ideas????

Wayne

Notes:

System was installed using the alpha-1 disk.  Updates have been applied by booting into the recovery mode.  Once there I drop into "ROOT" command prompt and configure eth0 with an ip address and netmask, and set a default route.  The exit.  Next, I select the "DPKG" menu item and install all of the updates.  I usually run "DPKG" twice to make sure there are no follow on items.  A couple of times there have been one or two obsolete packages to be removed.  Once DPKG is done I then resume normal boot.  When the system is fully booted, I immediately do a restart to make sure that everything gets properly picked up.

The machine itself is an old Dell Dimension 4100.  It has a 1GHz cpu, 512MB ram, 320GB hard disk, and an nVidia 6200LE graphics card.  I am using the onboard Sound and ethernet controllers.  Oh, it also has a dvd drive and floppy.

---

### Post by xeddog on 2008-07-31
Update - 

I downloaded Alpha-3 liveCD and tried to install that.  The install seemed to go fine, but I got a Grub Error 18 on the restart.  Crap.

Then I got the alpha-3 alternate disk and installed that.  The install went ok there too, and the restart was fine.  But, I am still at the same point I was before.  Nothing I need to do to configure the system works yet.

Wayne

---

### Post by overdrank on 2008-08-01
moved to  Intrepid :)

---

### Post by Kevbert on 2008-08-01
Adept- Add Remove programs - same problem here.  It looks like the developers may still be working on that one.  Previously I had to try using a root password to install anything in A1/2. In A3 + updates I now can enter my log-in password before Adept decides to shut down.

---

### Post by jbernardo on 2008-08-01
I'm sorry, but all I can add to this is a "me too".
I also found that I've lost the "Folder View" applet, and re-adding it just puts a "unknown applet" on my desktop, and that applets installed from the kde-looks site don't show up in the available applets list.

---

### Post by Mighty_Joe on 2008-08-01
> **Kevbert said:**
> Adept- Add Remove programs - same problem here.  

I concur.  I did some testing with the Kubuntu Intrepid Alpha 3 with all updates installed and Adept doesn't do anything. apt works fine from the command line.

---

### Post by Kevbert on 2008-08-01
Regarding the adept-notifier.  Yes that' all it does (notify).  You'll need to update with
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
in terminal.

---

### Post by Kevbert on 2008-08-01
Can anyone access a floppy drive in KDE 4.1.0 (Alpha3) ?

---

### Post by Vorian on 2008-08-01
> **jbernardo said:**
> 
I also found that I've lost the "Folder View" applet, and re-adding it just puts a "unknown applet" on my desktop, and that applets installed from the kde-looks site don't show up in the available applets list.
This is a known bug we are working on getting fixed

> **Kevbert said:**
> Adept- Add Remove programs - same problem here.  It looks like the developers may still be working on that one.  Previously I had to try using a root password to install anything in A1/2. In A3 + updates I now can enter my log-in password before Adept decides to shut down.
this is a work in progress.

> **Kevbert said:**
> Can anyone access a floppy drive in KDE 4.1.0 (Alpha3) ?yes for me. Please file a bug if you can not mount your floppy drive. :)

Thanks for testing :)

---

### Post by Kevbert on 2008-08-01
Floppy problem - I'll just boot into Intrepid Kubuntu and sort that out, I'll also check it in Ubuntu A3 (but I think that's working). Thanks.
The bug report is #254009 and occurs in both Kubuntu and Ubuntu though there are minor differences between the two.
I've also raised a problem on the Program Launcher Menu (bug #254017) which is detailed in post [876790]("http://ubuntuforums.org/showthread.php?t=876790.").

---

### Post by stevebakerj on 2008-08-15
Installed Intrepid Alpha 4 KDE 4.1 and the Adept problem (shuts down) is still there, Apt works fine. Is there a bug open for this? does anyone have a link?

---

### Post by caryb on 2008-08-15
I have a question for the distro "tarts" are these problems KDE4.1 related or Kubuntu Intrepid issues :confused:



Cary

---

### Post by RIchard James13 on 2008-08-15
If you are having problems with Adept then you can get a alpha version of adept here --> [http://web.mornfall.net/blog/adept_3.0_alpha_6.html]("http://web.mornfall.net/blog/adept_3.0_alpha_6.html")
Note that the alpha version does not have the adept notifier and installing it will uninstall the current notifier. I get around this by refetching the package lists and updating manually using "adept updater".

I did have the folderview bug. It was related to having old 4.0 plasma widgets in the system and a 4.1 version of plasma. They don't work together. Maybe you could try using the new adept to remove all of plasma and re-install it again.

---

