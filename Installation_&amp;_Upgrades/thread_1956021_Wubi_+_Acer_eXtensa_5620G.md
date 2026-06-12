---
title: "Wubi + Acer eXtensa 5620G"
date: 2012-04-10
forum: Installation &amp; Upgrades
---

### Post by roelforg on 2012-04-10
Hey,
 
I need to give a presentation to my class in a few weeks.
So, what's better than giving it... Using linux!
 
My point is that, in a deal with my parents, i have 1 laptop for school only (sadly, it's win only... But hey, the deal was they would pay for it) and my old laptop is for home purposes and as backup in case the school laptop failes (good idea).
I never got around to installing ubuntu on it (got 5 desktops with their own hd (or more) dedicated to ubuntu).
But as part of the deal, the windows must be bootable at all times.
So, i decided to want to try wubi to make it work.
Now, i've read about acer's weired boot-sequence and the string of problems associated with this model.
 
So i need to know, will it work without corrupting the acer boot, windows or both?
And will the ATI card still work and support both video-outs?
The battery is shot anyways.
I also plan on, after installing, install lxde with apt-get, can i do that? Because i remember the initrd being rebuild as a part of the process which in turn caused grub-update which will corrupt my win-bootloader, right?
 
It's kinda stupid, i did all sorts of weired installs of ubuntu... But those were all on dedicated hd's with nothing to lose, here i do (besides my backup laptop, i also lose a lot of data as it was my first laptop and was used a lot.)
 
Side-note: It has a D:\ as well, will that cause problems?
 
Windows vista has never been reloaded nor have any service packs been installed. (did i say i haven't used it in years yet?)
I don't really care about wireless, though. (at home it'll use a cable and at school the routers do mac-filtering)

---

### Post by roelforg on 2012-04-10
Update:
Summary of long OP:
I have an Acer eXtensa 5620G.
I never got around to installing Ubuntu.
I want to install linux, but for reasons explained above i need to keep the Windows Vista install.
So i decided on Wubi.
However, i read that there are problems with this specific model regarding this.
Thus, i need to know if i can use Wubi without interfering with Vista or the Acer recovery partition.

Here are the specs of the laptop:
160GB HD
Intel Core 2 Duo 1.5Ghz
ATI Mobility Radeon HD 2400 XT Hypermemory (1gb)
2GB DDR2 Ram
Windows Vista SP0
C:\ - 50gb
D:\ - 50gb
Recover:\ ~15GB

---

### Post by roelforg on 2012-04-10
Do i have to install on C or D or doesn't it matter?
D is my datapartition i keep most my files (lol - my desktop has a similar thing... using 2 harddrives)
Is it safe???
or is it gonna mess with my acer recovery?

Aside: I can't find any vid showing the complete install process, paets are skipped every time (30% now 100% 0.1s later? i don't think so...)

I'm a WuBi noob, only worked with dedicated installs and vm's (no, i don't have win vm's anymore)

---

### Post by bcbc on 2012-04-10
Wubi won't affect windows booting. It adds an entry to the Windows boot manager to boot. (Note: the first reboot after installing boots straight to Ubuntu, thereafter you get to choose.)

The windows bootloader and bootsector are not affected by Wubi. In older releases there was a bug that could overwrite these with some user help. No longer an issue.

Wubi works the same as a normal install, apart from the way it uses Windows boot manager, grub4dos and the wubildr file to invoke grub2; and the virtual disk.

You'll probably need 'nomodeset' for the graphics card: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) (post #8 is wubi specific).

After that you can pretty much do anything you would do on a normal install, including install lxde etc.

It doesn't matter which 'drive' you install on. It cannot affect your recovery as it doesn't modify any partitions.

---

### Post by roelforg on 2012-04-11
> **bcbc said:**
> Wubi won't affect windows booting. It adds an entry to the Windows boot manager to boot. (Note: the first reboot after installing boots straight to Ubuntu, thereafter you get to choose.)

The windows bootloader and bootsector are not affected by Wubi. In older releases there was a bug that could overwrite these with some user help. No longer an issue.

Wubi works the same as a normal install, apart from the way it uses Windows boot manager, grub4dos and the wubildr file to invoke grub2; and the virtual disk.

You'll probably need 'nomodeset' for the graphics card: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) (post #8 is wubi specific).

After that you can pretty much do anything you would do on a normal install, including install lxde etc.

It doesn't matter which 'drive' you install on. It cannot affect your recovery as it doesn't modify any partitions.
Thanks!
I was kinda worried because for my desktops i paid a max of 30 bucks each and had wiped drives anyway, this laptop i did pay a lot for.
Had the thing for at least 5yrs. and it has had 5 bootrepair, it's good to know it won't interfer.
I prefer installing on D but i know some apps have hard-coded paths so i wanted to know if that could cause problems.
I only found docs regarding 8.10 on this model and there were always troubles.
And laptops are known troublemakers.

One last question:
Do i edit \ubuntu\install\wubildr-disk.cfg for the initial reboot, and then reboot for the first time to ubuntu, correct?

---

### Post by bcbc on 2012-04-11
> **roelforg said:**
> Thanks!
...
One last question:
Do i edit \ubuntu\install\wubildr-disk.cfg for the initial reboot, and then reboot for the first time to ubuntu, correct?
If you run wubi.exe standalone, then yes, you need to update that file. If you run wubi.exe from a CD or with the desktop CD ISO in the same directory, then you use the other method.

You can tell since the wubildr-disk.cfg is only present on the standalone install.

---

### Post by roelforg on 2012-04-11
> **bcbc said:**
> If you run wubi.exe standalone, then yes, you need to update that file. If you run wubi.exe from a CD or with the desktop CD ISO in the same directory, then you use the other method.

You can tell since the wubildr-disk.cfg is only present on the standalone install.

Yes i was planning on standalone as i only have kickstart discs w/o wubi.
But i do need to select "reboot later" and edit the file, right?

---

### Post by bcbc on 2012-04-11
> **roelforg said:**
> Yes i was planning on standalone as i only have kickstart discs w/o wubi.
But i do need to select "reboot later" and edit the file, right?

yes. I suggest using write.exe (wordpad) as it supports the line endings (not notepad).

---

### Post by roelforg on 2012-04-11
> **bcbc said:**
> yes. I suggest using write.exe (wordpad) as it supports the line endings (not notepad).
 
I was planning to copy the file to the sambashare of my desktop (ubuntu) and copy it and use nano to edit, and then copy the edited one back to the laptop, that way i have a backup.
 
I'll try when i get home,
if it works, i owe you one.
 
Any extra suggestions are welcome.

---

### Post by roelforg on 2012-04-11
Gonna begin,
wish me luck!

I'm gonna use notepad++ for nomodeset though.

---

### Post by roelforg on 2012-04-11
Installed OK.
Currently installing ATI drivers.
It didn't boot with nomodeset after the configure stage (no "nomodeset" in /proc/cmdline).
I guess it worked!
 
 
...
Just finished the driver while typing ;)
Now running the fglrx updates package.
 
Thank you bcbc,
i owe you one!
 
You said i can just run
```

sudo apt-get install lxde

```
right?

---

### Post by roelforg on 2012-04-11
Update:
The post-release updates for the ATI card don't work.
It told me to reinstall the normal one, so i do.

---

### Post by bcbc on 2012-04-11
> **roelforg said:**
> Installed OK.
Currently installing ATI drivers.
It didn't boot with nomodeset after the configure stage (no "nomodeset" in /proc/cmdline).
I guess it worked!
 
 
...
Just finished the driver while typing ;)
Now running the fglrx updates package.
 
Thank you bcbc,
i owe you one!
 
You said i can just run
```

sudo apt-get install lxde

```
right?
The nomodeset should be for the first boot only. It doesn't persist anywhere. If it booted fine without it, you probably didn't need it (not always easy to tell which ATI require it)

Re. installing lxde, check out [http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu) 
I don't know how up to date that is - when I last tried it out I just installed lubuntu.

---

### Post by roelforg on 2012-04-11
LOL --- I'm typing this from the new install (now 5/7 of my pc's run ubuntu!).

I thank you all.
Now i can really blow them away at my presentation and maybe get some new linuxers!

---

### Post by roelforg on 2012-04-11
> **bcbc said:**
> The nomodeset should be for the first boot only. It doesn't persist anywhere. If it booted fine without it, you probably didn't need it (not always easy to tell which ATI require it)

Re. installing lxde, check out [http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu) 
I don't know how up to date that is - when I last tried it out I just installed lubuntu.

sorry, didn't notice your post until now...

My aticard doesn't need it, so now my resolution is higher then 1024x768, so i'm happy.

Yes the link is up to date,
```

sudo apt-get install lxde

```
is all there is to installing and to get a lxde session, just click on the cogwheel next to your username on the loginscreen and click on lxde, enter your pass and hit enter.

I owe you one man, it works great!

---

### Post by bcbc on 2012-04-11
> **roelforg said:**
> sorry, didn't notice your post until now...

My aticard doesn't need it, so now my resolution is higher then 1024x768, so i'm happy.

Yes the link is up to date,
```

sudo apt-get install lxde

```
is all there is to installing and to get a lxde session, just click on the cogwheel next to your username on the loginscreen and click on lxde, enter your pass and hit enter.

I owe you one man, it works great!

Great! Good luck with your presentation!

---

