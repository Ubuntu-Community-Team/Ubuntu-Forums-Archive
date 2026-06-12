---
title: "Grub2 and Jaunty"
date: 2008-11-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2008-11-03
Hopefully Grub2 will make it to Jaunty so that we can have Ext4.
For anyone testing here is the place to share.

Not quite what you looking for plun but its a start.

[http://www.gnu.org/software/grub/grub-2-faq.en.html](http://www.gnu.org/software/grub/grub-2-faq.en.html)

[http://grub.enbug.org/](http://grub.enbug.org/)

---

### Post by Slug71 on 2008-11-03
A little old but also found this.

[http://www.techenclave.com/guides-and-tutorials/grub-2-installation-92883.html](http://www.techenclave.com/guides-and-tutorials/grub-2-installation-92883.html)


This ones a little newer.

[http://ubuntuforums.org/showthread.php?t=965538](http://ubuntuforums.org/showthread.php?t=965538)

---

### Post by Eclipse. on 2008-11-03
C&P of my post in the other thread.

"All this talk of Grub2, I'm sorry to disapoint but its never going to happen.Its just not ready yet.The developers havent even got to the stage of begining to stabilizing it.Plus it has been delayed so many times its unrealistic to put a date on its release, if were are going to use it we will just need to stick with grub legacy and patch it."

---

### Post by Slug71 on 2008-11-03
That doesnt mean for those of us who want to test it cant.

---

### Post by Eclipse. on 2008-11-03
> **Slug71 said:**
> That doesnt mean for those of us who want to test it cant.

I didnt say that, just I doubt it will be in Jaunty.

Please do test it, infact packages have been in the ubuntu repos since 6.06 for testing.

---

### Post by plun on 2008-11-03
I think we must find more about trouble shooting...

"Broken" GRUB is a real pain

Really old blueprint, as eclipse wrote ;)

[https://launchpad.net/ubuntu/+spec/grub2](https://launchpad.net/ubuntu/+spec/grub2)

---

### Post by ronacc on 2008-11-03
just keep a supergrub disk handy :lolflag:

---

### Post by of_darkness on 2008-11-04
well last time i installed it i just diddent work:/ and what i can findout from the grub wiki 64bit is not suported?.. and its not in the todo list for grub2..

---

### Post by gnomeuser on 2008-11-04
I have noticed that Fedora has Grub2 in their repos so you can test it. When you install the package it will give you a grub2 entry in your existing grub1. Thus keeping your working bootloader and allowing you to see if grub2 works on your machine.

This seems like a good way to let people try it.

---

### Post by ShirishAg75 on 2008-11-04
> **Slug71 said:**
> A little old but also found this.

[http://www.techenclave.com/guides-and-tutorials/grub-2-installation-92883.html](http://www.techenclave.com/guides-and-tutorials/grub-2-installation-92883.html)


This ones a little newer.

[http://ubuntuforums.org/showthread.php?t=965538](http://ubuntuforums.org/showthread.php?t=965538)

Hi Slug, the first one which you posted was done by yours truly. 

I see 1 issue . 

a. We don't sync and merge grub2 packages quickly  enough to what is in debian. The debian guys do quite regular packaging. 

Also , the last grub2 package screwed up my booting, it made all my entries, including grub1 entries to point to (hd1,1) while my boot entries are in (hd0,0) 

So its gonna take its own time I guess.

---

### Post by RawMustard on 2008-11-06
Been using grub2 in lenny for the past month on two different systems with no problems, touch wood.

It's a bit of a headache with all the different config files though, grub legacy was much simpler :(

---

### Post by RAOF on 2008-11-09
> **gnomeuser said:**
> I have noticed that Fedora has Grub2 in their repos so you can test it. When you install the package it will give you a grub2 entry in your existing grub1. Thus keeping your working bootloader and allowing you to see if grub2 works on your machine.

This seems like a good way to let people try it.

This is also the default behaviour for Debian (and hence Ubuntu's) grub2 packages (grup-pc et al).

---

### Post by Slug71 on 2008-11-10
Nice, will give that a try when Alpha 1 is out.

---

### Post by plun on 2008-11-10
Grub 1 changes today

> grub-installer (1.35ubuntu1) jaunty; urgency=low

  * Resynchronise with Debian. Remaining changes:
    - Show the grub menu and raise the menu timeout if other operating
      systems are installed.
    - Ask grub-installer/only_debian at medium priority.
    - Remove splash boot parameter unless debian-installer/framebuffer=true.
    - If / or /boot are on a removable device, install GRUB there by
      default.
    - Only mount /target/proc if it isn't already mounted.
    - Support setting OVERRIDE_UNSUPPORTED_OS in the environment to force
      grub-installer to use its default MBR selection method despite there
      being unsupported operating systems on the disk.
    - Unless grub-installer/make_active is preseeded to false, mark the
      partition to which GRUB is being installed as bootable, or failing
      that the first available primary partition on the disk to which GRUB
      is being installed.
    - Support grub-installer/bootdev_directory preseeding to make use of the
      relative path feature of grub4dos, so that we can point grub4dos at
      part of a disk for installation-from-windows. Setting this disables
      normal grub installation, but still generates a device.map.
    - [B]Only support grub-installer/grub2_instead_of_grub_legacy by preseeding
      for now[/B].  (????, my comment)
    - Handle cases where /boot is bind-mounted.
    - Add another guard against calling 'udevadm info' with an empty device
      name.
    - Add support for writing an MBR on each disk in an mdadm-managed RAID
      providing /boot.
    - Properly make use of output from os-prober to configure the booting of
      other operating systems on dmraid arrays. Attempt to guess where in
      the device map the array belongs, by substituting the first drive in
      the dmraid array for the dmraid array device node itself, and removing
      any reference to other member disks of the array.
    - Add support for lpia.
    - Handle /boot being on a virtio device.
    - Set a sensible default boot device when /cdrom is not iso9660, as this
      is probably a USB install and (hd0) does not make sense when
      installing from a removable disk.


[https://lists.ubuntu.com/archives/jaunty-changes/2008-November/000272.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-November/000272.html)

---

### Post by Josh04 on 2008-11-10
I've been using grub2 since hardy now, and it seems reasonably solid. The only problem I have is that the configuration files are so damn confusing. There's /boot/grub/grub.cfg, but you can't edit that, there's /etc/default/grub2 which has a few parameters in it, and there's the files in /etc/grub.d/ which are all non-straightforward.

---

### Post by Gina on 2008-11-11
> **Josh04 said:**
> I've been using grub2 since hardy now, and it seems reasonably solid. The only problem I have is that the configuration files are so damn confusing. There's /boot/grub/grub.cfg, but you can't edit that, there's /etc/default/grub2 which has a few parameters in it, and there's the files in /etc/grub.d/ which are all non-straightforward.That hardly seem like any improvement!!! :(

---

### Post by Slug71 on 2008-11-11
> **Gina said:**
> That hardly seem like any improvement!!! :(

Gotta remember though, Grub2 has been rebuilt from the ground up and not a continuation from Grub Legacy.
It probably still needs to be cleaned up.

---

### Post by ShirishAg75 on 2008-11-11
> **plun said:**
> Grub 1 changes today



[https://lists.ubuntu.com/archives/jaunty-changes/2008-November/000272.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-November/000272.html)

What do you mean by that? Do you mean in Jaunty Grub-installer would be there? If you are running it can you show it what it depends on and stuff like that. 

Would very much like to aptitude output of this grub-installer if somebody is running 

```
 $ aptitude show grub-installer
```

---

### Post by ShirishAg75 on 2008-11-11
> **Slug71 said:**
> Gotta remember though, Grub2 has been rebuilt from the ground up and not a continuation from Grub Legacy.
It probably still needs to be cleaned up.

I remember reading sometime back on the grub2 mailing list that documentation is something that still needs to be worked on as well as making things easier for newbies to comprehend. Perhaps sometime in the future we may have a GUI either asking questions and making the grub entry for us or something similar.

---

### Post by Slug71 on 2008-11-11
> **ShirishAg75 said:**
> I remember reading sometime back on the grub2 mailing list that documentation is something that still needs to be worked on as well as making things easier for newbies to comprehend. Perhaps sometime in the future we may have a GUI either asking questions and making the grub entry for us or something similar.

That would be pretty sweet! 
Dont see that happening anytime soon though. At least not with Grub2 as thats been going since like 2002 or something and its still not done. Stabilization is suppose to begin this month though.:guitar:

---

### Post by ShirishAg75 on 2008-11-18
Grub2 got a release about 18 hours ago. 

[https://launchpad.net/ubuntu/+source/grub2](https://launchpad.net/ubuntu/+source/grub2)

Specifically 
[https://launchpad.net/ubuntu/jaunty/+source/grub2/1.96+20080724-12ubuntu1](https://launchpad.net/ubuntu/jaunty/+source/grub2/1.96+20080724-12ubuntu1)

I also filed which I think are couple of bugs (of course its pre-release and all that )

[lpbug]299338[/lpbug] and [lpbug]299344[/lpbug]

Any ideas/solutions for the same are welcome.

---

### Post by Slug71 on 2008-11-18
Nice!!!

---

### Post by of_darkness on 2008-11-18
> **ShirishAg75 said:**
> Grub2 got a release about 18 hours ago. 

[https://launchpad.net/ubuntu/+source/grub2](https://launchpad.net/ubuntu/+source/grub2)

Specifically 
[https://launchpad.net/ubuntu/jaunty/+source/grub2/1.96+20080724-12ubuntu1](https://launchpad.net/ubuntu/jaunty/+source/grub2/1.96+20080724-12ubuntu1)

I also filed which I think are couple of bugs (of course its pre-release and all that )

[lpbug]299338[/lpbug] and [lpbug]299344[/lpbug]

Any ideas/solutions for the same are welcome.
Any info on how its doing on 64bits systems nowdays? any progress on making it work on 64bit?

---

### Post by RAOF on 2008-11-18
> **of_darkness said:**
> Any info on how its doing on 64bits systems nowdays? any progress on making it work on 64bit?

When has it *not* worked on x86-64 systems?

---

### Post by ShirishAg75 on 2008-11-19
Hi all, 
 Just made a [blog post]("http://flossexperiences.wordpress.com/2008/11/19/jaunty-and-grub2/#more-269") about the same, would be refining the same in the next couple of days as and when questions are answered.

---

### Post by plun on 2008-11-19
> **ShirishAg75 said:**
> Hi all, 
 Just made a [blog post]("http://flossexperiences.wordpress.com/2008/11/19/jaunty-and-grub2/#more-269") about the same, would be refining the same in the next couple of days as and when questions are answered.

Great  !

My observations

[http://paste.ubuntu.com/74227/](http://paste.ubuntu.com/74227/)

More pics

[[img]http://ubuntu-pics.de/thumb/5976/grub2_64Qu9k.jpg[/img]](http://ubuntu-pics.de/bild/5976/grub2_64Qu9k.jpg)

:confused:Whats this :confused:

[[img]http://ubuntu-pics.de/thumb/5977/grub_pc_2c7vxp.jpg[/img]](http://ubuntu-pics.de/bild/5977/grub_pc_2c7vxp.jpg)


NTFS seems to be thrown out....:-\"


EDIT

grub.cfg is default also "read-only"....


EDIT2
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/214642](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/214642)

EDIT3

> plun@plun:~$ man os-prober 
**No manual entry for os-prober**
See 'man 7 undocumented' for help when manual pages are not available.


---

### Post by dinxter on 2008-11-19
is grub2 not finding splash images for everyone else? the default search in  /etc/grub.d/05_debian_theme seems to be  
{/boot/grub,/usr/share/images/desktop-base}/WhateverSplashImageYouWant.{png,tga}

but the images i get from grub2-splashimages are in /usr/share/images/grub

changing that line to  {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/WhateverSplashImageYouWant.{png,tga}

and running update-grub2 generates the right grub.conf for me though.

bug [here]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/299861")

---

### Post by dinxter on 2008-11-19
was someone looking to disable the usplash? the line to change is in /etc/default/grub, change

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to remove splash and run update-grub2

i take it to have custom entries rather than the default for every linux entry there needs to be some tinkering in /etc/grub.d/ though i'm not sure what the approved way for doing that is

---

### Post by plun on 2008-11-19
> **dinxter said:**
> 
i take it to have custom entries rather than the default for every linux entry there needs to be some tinkering in /etc/grub.d/ though i'm not sure what the approved way for doing that is

Have you permanently installed Grub 2  ?

upgrade-from-grub-legacy command


I also added a comment to the bug about NTFS and GRUB2 is broken 
for Ubuntu if not NTFS partitions are handled correct.  IMHO...

---

### Post by ShirishAg75 on 2008-11-19
> **dinxter said:**
> was someone looking to disable the usplash? the line to change is in /etc/default/grub, change

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to remove splash and run update-grub2

i take it to have custom entries rather than the default for every linux entry there needs to be some tinkering in /etc/grub.d/ though i'm not sure what the approved way for doing that is

So basically it becomes 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```or what?

Also by usplash you mean the progress bar, not the boot screen right?

---

### Post by ShirishAg75 on 2008-11-19
> **dinxter said:**
> is grub2 not finding splash images for everyone else? the default search in  /etc/grub.d/05_debian_theme seems to be  
{/boot/grub,/usr/share/images/desktop-base}/WhateverSplashImageYouWant.{png,tga}

but the images i get from grub2-splashimages are in /usr/share/images/grub

changing that line to  {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/WhateverSplashImageYouWant.{png,tga}

and running update-grub2 generates the right grub.conf for me though.

bug [here]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/299861")

Interestingly I also looked at /usr/share/images/desktop-base

which has links to ultimately a GNOME splashscreen which is also cool (IMHO)

```

/usr/share/images/desktop-base$ ll
total 0
lrwxrwxrwx 1 root root 32 2008-10-24 11:40 desktop-splash -> /etc/alternatives/desktop-splash

```IF you look that up you get in turn 

```

$ ll /etc/alternatives/desktop-splash 
lrwxrwxrwx 1 root root 42 2008-10-24 11:40 /etc/alternatives/desktop-splash -> /usr/share/pixmaps/splash/gnome-splash.png

```which would also make a pretty good boot/splash screen.

I just updated it to reflect on my desktop

Here's my line 16 in /etc/grub.d/05_debian_theme

```
 for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub,/usr/share/pixmaps/splash/}/gnome-splash.{png,tga} ; do
```Then did the sudo update-grub which gave me :-

```

~$ sudo update-grub
Updating /boot/grub/grub.cfg ...
Found Debian background: gnome-splash.png
Found linux image: /boot/vmlinuz-2.6.27-7-generic
Found initrd image: /boot/initrd.img-2.6.27-7-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```But should this be the way of doing the same? There needs to be easier way to do than this.

I made [lpbug]299965[/lpbug] as well as see this discussion on the debian-bts 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=495282](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=495282)

---

### Post by dinxter on 2008-11-19
the fact that grub uses splash images and so does usplash is a bit confusing. but yes, that will move the usplash progress bar when you generate the grub config, your as well removing the 'quiet' option too so you get all the nice scrolling text information :) 

grub2 is properly installed to the mbr, the chainloader worked fine so i thought i'd commit to it properly :) i'll test out the ntfs bug in a few days, i need to stick a new ntfs drive on anyway

---

### Post by dinxter on 2008-11-19
the line in /etc/grub.d/05_debian_theme
```
  for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/BonsaiTridentMaple.{png,tga} ; do
```

basically searches those directories for a matching file BonsaiTridentMaple.png or BonsaiTridentMaple.tga, if a match is found then it will use that for the grub splash screen (if it meets the resolution requirements and so on for a grub background), if no match is found then no background_image is set in /boot/grub/grub.cfg. 

you can add whatever directories you like to the search and change the filename to match your preferred grub splash though i agree its not the most straightforward way, though most grub2 configuration isnt exactly easy at the moment.

the bug i filed is that the default search doesnt include the directory /usr/share/images/grub that is used by the grub2-splashimages package. if it was then you could just change BonsaiTridentMaple to one of the other images in that package and update-grub2 would use that one instead

---

### Post by dinxter on 2008-11-19
just to add, /usr/share/pixmaps/splash/gnome-splash.png is technically a splash screen for when you log into a gnome session (yet another kind of splash!) so it may not work for grub2, best stick with real grub2 splashimages for now that are meet the right grub2 criteria, whatever they are, i'm fairly sure theres a resolution constraint on them if nothing else

---

### Post by plun on 2008-11-19
> **dinxter said:**
> 
grub2 is properly installed to the mbr, the chainloader worked fine so i thought i'd commit to it properly :) i'll test out the ntfs bug in a few days, i need to stick a new ntfs drive on anyway

OK... the changelog is rather massive.

[http://changelogs.ubuntu.com/changelogs/pool/universe/g/grub2/grub2_1.96+20080724-12ubuntu1/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/g/grub2/grub2_1.96+20080724-12ubuntu1/changelog)

> * patches/00_ntfs_insensitive.diff: They say NTFS is an insensitive fool.
    It must be true! (use case insensitive match in NTFS) (Closes: #497889)


I also have this script from [the bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/214642")..

[http://launchpadlibrarian.net/13288057/14_windows](http://launchpadlibrarian.net/13288057/14_windows)

So here we go again....:)

EDIT for the records

```
plun@plun:~$ sudo upgrade-from-grub-legacy
[sudo] password for plun: 

Installing GRUB to Master Boot Record of your first hard drive ...

Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda

GRUB Legacy has been removed, but its configuration files have been preserved,
since this script cannot determine if they contain valuable information.  If
you would like to remove the configuration files as well, use the following
command:

  rm -f /boot/grub/menu.lst*


```

No NTFS....:^o

```
plun@plun:~$ sudo update-grub2
Updating /boot/grub/grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.28-rc5-candela
Found initrd image: /boot/initrd.img-2.6.28-rc5-candela
Found linux image: /boot/vmlinuz-2.6.27-7-generic
Found initrd image: /boot/initrd.img-2.6.27-7-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```


The script
```
plun@plun:~/Desktop$ sudo ./ntfs.sh
Detected an NTFS partition, marked as bootable, on: /dev/sda1. Adding as a "Windows" boot option for /dev/sda1.
menuentry "Windows (on /dev/sda1)" {
	set root=(hd0,1)
	chainloader +1
}
cat: /tmp/fdisk: No such file or directory


plun@plun:~/Desktop$ sudo update-grub2
Updating /boot/grub/grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.28-rc5-candela
Found initrd image: /boot/initrd.img-2.6.28-rc5-candela
Found linux image: /boot/vmlinuz-2.6.27-7-generic
Found initrd image: /boot/initrd.img-2.6.27-7-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by caljohnsmith on 2008-11-19
I haven't thoroughly researched all the features of Grub 2, but one thing I'm concerned about is that Grub 2 does not have a "mapping" feature like legacy Grub according to their [Wiki page]("http://grub.enbug.org/CommandList") that compares legacy Grub commands with Grub 2. If Grub 2 has no equivalent mapping technique, then it will be a royal pain to try and boot Windows from anything other than the first drive in the BIOS boot order (hd0). In other words, if you try and boot Windows from a drive (hdX) other than the first drive (hd0) in the BIOS boot order, you normally have to do something like:
```
title	   Windows
root       (hdX,0)
[COLOR="Blue"]map        (hd0) (hdX)
map        (hdX) (hd0)[/COLOR]
chainloader +1
```
Does anyone know if Grub 2 has some other technique for booting Windows from a drive that's not first in the BIOS boot order? If not, that could be a major issue with many Ubuntu users who have Windows on a different drive than the boot drive. Any thoughts?

---

### Post by plun on 2008-11-19
> **caljohnsmith said:**
> 
Does anyone know if Grub 2 has some other technique for booting Windows from a drive that's not first in the BIOS boot order? If not, that could be a major issue with many Ubuntu users who have Windows on a different drive than the boot drive. Any thoughts?

I am going to test exactly this.... please take look at the message before.  The bug says "fix released"....

Install GRUB2 permanently and maybe use the script  

Break risk....:)

---

### Post by ShirishAg75 on 2008-11-19
I had a very weird bootup although I do also have grub legacy still running as well. 

I chainloaded to grub2 to see my new splash image but got something really funny. 

There was the splash wallpaper as well as the default blue-white screen as well. What's going on here. 

Also can somebody please share what should be in /etc/default/grub setting 

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```

should it be 
```

GRUB_CMDLINE_LINUX_DEFAULT=""
```

or what?

---

### Post by dinxter on 2008-11-19
> **caljohnsmith said:**
> Does anyone know if Grub 2 has some other technique for booting Windows from a drive that's not first in the BIOS boot order? If not, that could be a major issue with many Ubuntu users who have Windows on a different drive than the boot drive. Any thoughts?

there is no map command or equivalent as far as i know for grub2 as of yet (there were people talking about implementing it at some point but i have no idea of what became of it). if you're booting windows i suggest sticking with grub as the mbr bootloader and only chainloading to grub2 (which is the default install) 

the script [http://launchpadlibrarian.net/13288057/14_windows](http://launchpadlibrarian.net/13288057/14_windows) is not to fix this particular problem

---

### Post by dinxter on 2008-11-19
> **ShirishAg75 said:**
> I had a very weird bootup although I do also have grub legacy still running as well. 

I chainloaded to grub2 to see my new splash image but got something really funny. 

There was the splash wallpaper as well as the default blue-white screen as well. What's going on here. 

Also can somebody please share what should be in /etc/default/grub setting 

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```should it be 
```

GRUB_CMDLINE_LINUX_DEFAULT=""
```or what?

make sure your using a proper grub2 splash image as i mentioned, gnome-splash isnt one. try those from the grub2-splashimages package if your not using them already

as for GRUB_CMDLINE_LINUX_DEFAULT, either will give you a text based boot up and no usplash, the 'quiet' option just gives you slightly less verbose text. if you want more text detail on bootup then just have 
```

GRUB_CMDLINE_LINUX_DEFAULT=""
```

---

### Post by plun on 2008-11-19
> **dinxter said:**
> there is no map command or equivalent as far as i know for grub2 as of yet (there were people talking about implementing it at some point but i have no idea of what became of it). if you're booting windows i suggest sticking with grub as the mbr bootloader and only chainloading to grub2 (which is the default install) 

the script [http://launchpadlibrarian.net/13288057/14_windows](http://launchpadlibrarian.net/13288057/14_windows) is not to fix this particular problem

Nope but this....

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=498439](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=498439)

So its broken without manual edits...

---

### Post by plun on 2008-11-19
Followup....

I blow up my NTFS partition...the boot sector is wrong checked with a repair tool. Seems to be complete empty.  :^o 

I can see a folder which I used for mounting created in /media

ntfs-3g was also updated today. :confused:

It was a couple a week ago I last used Windooze so maybe it was broken earlier.  :confused:

Nevertheless,  be careful...!

---

### Post by ShirishAg75 on 2008-11-19
> **dinxter said:**
> make sure your using a proper grub2 splash image as i mentioned, gnome-splash isnt one. try those from the grub2-splashimages package if your not using them already

as for GRUB_CMDLINE_LINUX_DEFAULT, either will give you a text based boot up and no usplash, the 'quiet' option just gives you slightly less verbose text. if you want more text detail on bootup then just have 
```

GRUB_CMDLINE_LINUX_DEFAULT=""
```

Tried and it works, although there is still the rectangular box (blue background with white text) in front of the image :(

Could that be fixed or that's also a work in progress ?

Some more observations :-

 I also upgraded from grub-legacy so there is only grub-2 now with  a file 

```
-rw-r--r-- 1 root root  4147 2008-11-18 11:01 menu.lst_backup_by_grub2_postinst 
``` alongwith the menu.lst in /boot/grub/menu.lst

---

### Post by dinxter on 2008-11-19
i'm not sure about the coloured box, its possible that the setting in 05_debian_theme that says 
'set menu_color_normal=cyan/blue'
means that the text background isnt transparent and that is creating the box, i havent noticed that here but i'll look into it tomorrow and see if theres anything that can be done. 
I wouldnt worry about menu.lst and various backups of it, these arent used at all by grub2 except to upgrade from grub on first install. best to keep them if a 'downgrade' to grub is needed though

---

### Post by dinxter on 2008-11-19
i've tried a few of the splashimages in /usr/share/images/grub and they all seem to be fine for me, the text background is transparent and there is no box in front of the image. im not sure where to look for a setting that could be causing it for you, the config files are all a bit new to me, do you get it with many diferent images? all the default ones im using are tga rather than png i dont know if that makes the diference

---

### Post by ShirishAg75 on 2008-11-19
> **dinxter said:**
> i'm not sure about the coloured box, its possible that the setting in 05_debian_theme that says 
'set menu_color_normal=cyan/blue'
means that the text background isnt transparent and that is creating the box, i havent noticed that here but i'll look into it tomorrow and see if theres anything that can be done. 

That would be cool. 

[quote=dinxter]
I wouldnt worry about menu.lst and various backups of it, these arent used at all by grub2 except to upgrade from grub on first install. best to keep them if a 'downgrade' to grub is needed though[/quote]

My thoughts exactly, it is needed for that just in case issue.

---

### Post by dinxter on 2008-11-19
looking at grub.conf the relevant part of mine has,

```
### BEGIN /etc/grub.d/05_debian_theme ###
set root=(hd0,2)
search --fs-uuid --set 578510f5-6baf-41e6-8dd8-08da6f584942
insmod tga
# EDIT - this tests that the image is a true grub2 
# image
if background_image /usr/share/images/grub/Windbuchencom.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
# EDIT - if it isnt a true grub2 image then 
# construct a text menu
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###
```

my guess is that the problem you're having is that the background_image test is false due to the supplied image failing the grub2 checks for it being a 'good' image and so the menu color variables are being set giving the coloured box. i suggest trying a few diferent grub2-splashimages and see if that improves things. it may be worth also checking that the image your using is the correct format which seems to be a 640x480 tga image

---

### Post by ShirishAg75 on 2008-11-19
> **dinxter said:**
> looking at grub.conf the relevant part of mine has,

```
### BEGIN /etc/grub.d/05_debian_theme ###
set root=(hd0,2)
search --fs-uuid --set 578510f5-6baf-41e6-8dd8-08da6f584942
insmod tga
# EDIT - this tests that the image is a true grub2 
# image
if background_image /usr/share/images/grub/Windbuchencom.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
# EDIT - if it isnt a true grub2 image then 
# construct a text menu
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###
```my guess is that the problem you're having is that the background_image test is false due to the supplied image failing the grub2 checks for it being a 'good' image and so the menu color variables are being set giving the coloured box. i suggest trying a few diferent grub2-splashimages and see if that improves things. it may be worth also checking that the image your using is the correct format which seems to be a 640x480 tga image

dmixter, 
from what I can tell

One the values need to be hard-coded in /etc/grub.d/debian_theme for which splashimage I want so doing the same. 

Going to try to add the same therein and let's see what happens. 

Aha I know what the issue is. What I did is have a backup of the file with the name debian.theme.original so that's also there. 

```
### BEGIN /etc/grub.d/05_debian_theme ###
set root=(hd0,2)
search --fs-uuid --set fc24631b-c156-4beb-bf61-be84e24bc946
insmod tga
if background_image /usr/share/images/grub/Lake_mapourika_NZ.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/05_debian_theme.original ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme.original ###

```

Then renamed the 05_debian_theme_original file 

```
sudo mv /etc/grub.d/05_debian_theme.original /etc/grub.d/debian_theme.original
```

Did an update-grub and wallah 

```
### BEGIN /etc/grub.d/05_debian_theme ###
set root=(hd0,2)
search --fs-uuid --set fc24631b-c156-4beb-bf61-be84e24bc946
insmod tga
if background_image /usr/share/images/grub/Lake_mapourika_NZ.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

```

So just need to reboot to find out how things are.

---

### Post by dinxter on 2008-11-20
looks like that should do it, update-grub2 was processing your backup and adding both the splashimage and the default text menu afterwards from 05_debian_theme_original. seems it processes every file that starts with a couple of integers

---

### Post by ShirishAg75 on 2008-11-20
I think it processes every file which is an executable rather than just integers which is in /etc/init.d/grub 

Oh and btw I retouched the whole thing at the blog [post]("http://flossexperiences.wordpress.com/2008/11/19/jaunty-and-grub2/") . The only thing left perhaps is timeout. I would just like timeout to be 'unlimited' (meaning giving me/the user the choice rather than having some clock ticking by) other than that everything is cool.

---

### Post by dinxter on 2008-11-20
seems so, a handy thing to know. i'm finding grub2 configuration a confusing thing compared to original grub, i'm sure it'll become clear eventually :)

---

### Post by plun on 2008-11-20
> **dinxter said:**
>  i'm sure it'll become clear eventually :)

Well... I am not going to touch this software...:)

It seems to be "blocking" bugs at Debian for Grub2.

My MBR went crazy and also fixmbr failed to repair it.

Messed around in chroot and ended up with grubs everywhere...:tongue: 

It was anyway time for a reinstall....

---

### Post by Gourgi on 2008-11-20
> **plun said:**
> It was anyway time for a reinstall....
watching your lately kernel and pulse activities i believe it also :lolflag:

---

### Post by plun on 2008-11-20
> **Gourgi said:**
> watching your lately kernel and pulse activities i believe it also :lolflag:

Well, I have never run a Ubuntu version as good as with the 2.6.28 kernel and PA ver 14, maybe to start remastersys...:guitar:


But Grub2 was something special  ....:^o

I just did a quick-look at Debians bug reports and apparently something is wrong...  including block requests for Lenny.


Nema problema with backups and /home on a separate partition....  the Windows junk takes time time to restore.

:)

---

### Post by Slug71 on 2008-12-28
So anyone know if Grub2 will be default in Jaunty after the discussion at UDS?

---

### Post by Starks on 2008-12-28
Grub2 is nice and all with its Windows detection, but the damn thing utterly destroys the menus in startupmanager.

---

### Post by Slug71 on 2008-12-29
> **Starks said:**
> Grub2 is nice and all with its Windows detection, but the damn thing utterly destroys the menus in startupmanager.

I wonder if it would have the same behaviour if it was installed by default and a fresh install was done though.

---

### Post by Gina on 2008-12-29
Yes, I've heard it's incompatible with the menu.list from grub1.  I gather it's quite different but haven't looked into it yet.

---

### Post by Slug71 on 2008-12-29
> **Gina said:**
> Yes, I've heard it's incompatible with the menu.list from grub1.  I gather it's quite different but haven't looked into it yet.

Yep, from what i gather it has something to do with the naming/numbering of the drives.
Grub Legacy begins the numbering from 0, whereas Grub2 begins the numbering from 1.

---

### Post by Starks on 2008-12-29
> **Slug71 said:**
> I wonder if it would have the same behaviour if it was installed by default and a fresh install was done though.

if i knew how to make a custom image, i might humor myself and try it out.

---

### Post by Gina on 2008-12-29
Yes, same here.

---

### Post by Slug71 on 2008-12-29
> **Starks said:**
> if i knew how to make a custom image, i might humor myself and try it out.

Yep definitely.

---

### Post by Starks on 2008-12-29
I think the bigger problem lies with the fact that a complete removal of all of the grub2 packages does not in fact remove all of the config files (eg: grub.cfg).

---

### Post by Gina on 2008-12-29
Reformatting does :lolflag:

---

### Post by plun on 2008-12-29
The major probem are bugs....

This one killed my NTFS partition

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=508567](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=508567)

Note that this is a **pending fix for Lenny**....


Jaunty got an old version within repo.

[http://packages.ubuntu.com/jaunty/grub2](http://packages.ubuntu.com/jaunty/grub2)



Some more of them...
[http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=grub2](http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=grub2)


"No documentation" is also outstanding... IMHO..

---

### Post by Slug71 on 2008-12-29
> **Starks said:**
> I think the bigger problem lies with the fact that a complete removal of all of the grub2 packages does not in fact remove all of the config files (eg: grub.cfg).

Could be possible. When i broke my Alpha 1 installation by installing Grub2 i just did a reinstall to fix it. 

All the how-to's for installing Grub2 that are around seem to be for older versions of Grub2 and for older versions of the Distro. So there is no way to find out if certain steps are no longer required or whats been fixed and what hasnt etc etc.

Would be nice if there was some updated info on this. I dont know how we are supposed to test something without some reasonably new information and how-to's. Perhaps that is why Grub2 is moving so slowly.

Devs could you please release just one alternative daily build where Grub2 is default?? Please? Pretty please?


[[IMG]http://brainstorm.ubuntu.com/idea/16899/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/16899/)

---

### Post by plun on 2008-12-29
> **Slug71 said:**
> 
Devs could you please release just one alternative daily build where Grub2 is default?? Please? Pretty please?

Can you please study earlier posted bugs from Debian.... ?

**Grave bugs** for many users... nothing to test until Debian sorts this out. Maybe someone from Canonical/Ubuntu can fix patches...:confused: 

Jauntys version must nevertheless be upgraded but somehow its pending for Lenny, unsure why ?  ...;)

---

### Post by Gina on 2008-12-29
Not worried about NTFS - the systems I'll be testing it on won't have any NTFS partitions :)

Not being able to boot more than one partition is "not very clever"!

Looks like it's not quite ready yet.

---

### Post by Slug71 on 2008-12-29
> **plun said:**
> 
Jaunty got an old version within repo.
[http://packages.ubuntu.com/jaunty/grub2](http://packages.ubuntu.com/jaunty/grub2)


I thought that version(1.96+20080724-12) was the latest.

---

### Post by plun on 2008-12-29
> **Slug71 said:**
> I thought that version(1.96+20080724-12) was the latest.

Nope...

Within experimental they got a later

[http://packages.debian.org/search?keywords=grub2&searchon=all&suite=all&section=all](http://packages.debian.org/search?keywords=grub2&searchon=all&suite=all&section=all)

Someone must nevertheless file a upgrade request and add this info.

I have others which just stands still........

---

### Post by Slug71 on 2008-12-29
> **plun said:**
> Nope...

Within experimental they got a later

[http://packages.debian.org/search?keywords=grub2&searchon=all&suite=all&section=all](http://packages.debian.org/search?keywords=grub2&searchon=all&suite=all&section=all)

Someone must nevertheless file a upgrade request and add this info.

I have others which just stands still........


Have filed a Bug(#312310) for the version to be updated.

---

### Post by Slug71 on 2008-12-29
So i just installed the start up manager which i think was made for Grub2 but could be wrong and it seems pretty cool little tool.

---

### Post by plun on 2008-12-29
> **Slug71 said:**
> Have filed a Bug(#312310) for the version to be updated.

OK... thanks !,  confirmed it and added upstream bug to Debian, done...:wink:

---

### Post by Slug71 on 2008-12-29
> **plun said:**
> The major probem are bugs....

This one killed my NTFS partition

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=508567](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=508567)

Note that this is a **pending fix for Lenny**....


Jaunty got an old version within repo.

[http://packages.ubuntu.com/jaunty/grub2](http://packages.ubuntu.com/jaunty/grub2)



Some more of them...
[http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=grub2](http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=grub2)


"No documentation" is also outstanding... IMHO..


No documentation is listed as a bug in your last link. ;)
[http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=grub2](http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=grub2)


Perhaps most of the above bugs are fixed with the newest version of Grub2?
Or at least the NTFS one.

---

### Post by plun on 2008-12-29
> **Slug71 said:**
> No documentation is listed as a bug in your last link. ;)
[http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=grub2](http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=grub2)


Perhaps most of the above bugs are fixed with the newest version of Grub2?
Or at least the NTFS one.

Yes but blowing away boots for other partiitons then for Jaunty must be fixed... in my case it was a NTFS partion which lost boot.

A user can have more then I installed _Linux distribution_.... also blown way.

Most important is that everything is known is up before testing...:)

- No manpage

- Wrong identification

- and so on...

---

### Post by Slug71 on 2008-12-29
> **plun said:**
> Yes but blowing away boots for other partiitons then for Jaunty must be fixed... in my case it was a NTFS partion which lost boot.

A user can have more then I installed _Linux distribution_.... also blown way.

Most important is that everything is known is up before testing...:)

- No manpage

- Wrong identification

- and so on...

Agreed.

Do you think Grub2 may have the same behaviour if it was used on a fresh install being default though?

---

### Post by plun on 2008-12-29
> **Slug71 said:**
> Agreed.

Do you think Grub2 may have the same behaviour if it was used on a fresh install being default though?

The challenge is that nothing is perfect and users have different configs and also installed software.
[B]
With a clean install on a _clean PC_ you cannot see these bugs.[/B]

But... with a mixed PC with Windows or for example Intrepid already installed the boot flag will be wiped with Grub2 for other then Jauntys boot partition.

But again... only  developers can make final judgements about this and the bug is filed.

---

### Post by inxygnuu on 2008-12-30
Hello, i don't mean to bust-in or change the topic, but it sounds like GRUB 2 is holding us back from ext4, and therefore Ubuntu development will slow down. Why don't we just find a different bootloader if the only more advanced one stinks and is incomplete, and the older version will hold us back? just a random idea...

---

### Post by autocrosser on 2008-12-30
Well--Grub2 is a new idea--just real long in development--It's usable, but not in a production/enduser way yet. I follow development & maybe by 9.10 it will be "really" ready for prime-time...The only problem with Grub (other than it's real old)--is not being able to boot EXT4--as long as you have a couple of work-arounds in place you can use EXT4 right now--the present Grub still needs a /boot formatted as EXT3.............

---

### Post by plun on 2008-12-30
> **autocrosser said:**
> Well--Grub2 is a new idea--just real long in development--It's usable, but not in a production/enduser way yet. I follow development & maybe by 9.10 it will be "really" ready for prime-time...The only problem with Grub (other than it's real old)--is not being able to boot EXT4--as long as you have a couple of work-arounds in place you can use EXT4 right now--the present Grub still needs a /boot formatted as EXT3.............

I also took a look at Debians changelog....

[http://packages.debian.org/changelogs/pool/main/g/grub2/grub2_1.96+20081201-1/changelog](http://packages.debian.org/changelogs/pool/main/g/grub2/grub2_1.96+20081201-1/changelog)

I can test it with Debians package...:D

---

### Post by inxygnuu on 2008-12-30
Wow. plun and Slug71 are like developers for grub 2. With you guys, we might have grub 2 being used by RC! what does that mean anyway?

---

### Post by plun on 2008-12-30
> **inxygnuu said:**
> Wow. plun and Slug71 are like developers for grub 2. With you guys, we might have grub 2 being used by RC! what does that mean anyway?

Nope... just reading bug and package info....:D  "Basic stuff"...

I also blowed away a NTFS partition so this is not something to play with....):P

---

### Post by ShirishAg75 on 2008-12-30
There is lot of gap between Debian grub2 packages and Ubuntu. 

I guess the devs only sync when that package is deemed to be worthy enough to be pushed to unstable as can be seen comparing the Ubuntu and Debian histories. 

[http://packages.debian.org/changelogs/pool/main/g/grub2/grub2_1.96+20081201-1/changelog](http://packages.debian.org/changelogs/pool/main/g/grub2/grub2_1.96+20081201-1/changelog)

[http://packages.ubuntu.com/search?keywords=grub2&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=grub2&searchon=names&suite=all&section=all)

---

### Post by plun on 2008-12-30
> **ShirishAg75 said:**
> There is lot of gap between Debian grub2 packages and Ubuntu. 

I guess the devs only sync when that package is deemed to be worthy enough to be pushed to unstable as can be seen comparing the Ubuntu and Debian histories. 



Well...broken IMHO...;)

I am up and running with Grub2 and found this solution for NTFS

[http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)

A missing Windows declaration....:-\"


But now I am getting a syntax error but Grub works..... also this bug is rather annoying which blocks the **kernel-helpers script**.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/253581](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/253581)

You cannot remove a kernel.....

---

### Post by plun on 2008-12-30
It works....:D

Found the d--ned NTFS partition.....

The guide is a little wrong with the  ¨--¨   signs

The file must look exactly as this:

```
#! /bin/sh -e

echo "Adding Windows" >&2
cat << EOF
menuentry "Windows XP" {
set root=(hd0,1)
chainloader +1
}
EOF
```


The kernel-helper script from old Grub also works and makes it possible to **add/remove** kernels....    (just download deb file > open with archive-manager > extract helper script)

Splash works....

Fix a new boot-splash....:D

---

### Post by Starks on 2008-12-30
Finding a lost NTFS partition manually or automatically is easy with Super Grub Disk.

---

### Post by plun on 2008-12-30
> **Starks said:**
> Finding a lost NTFS partition manually or automatically is easy with Super Grub Disk.

Nope... not this one, I did it a month ago. SuperGrub also failed..:^o

Also tried fixboot and fixmbr.


But now it works....:D   Added info to bug report  


"RAOF" is checking the newer version and for me it just works !

---

### Post by Starks on 2008-12-30
Meh. I guess it doesn't always work then.

---

### Post by Slug71 on 2008-12-30
> **inxygnuu said:**
> Wow. plun and Slug71 are like developers for grub 2. With you guys, we might have grub 2 being used by RC! what does that mean anyway?

Lol, hardly and i wish. Plun knows WAY more than i do. I'm just a tester, I still have much to learn with Linux.

---

### Post by Slug71 on 2008-12-30
> **plun said:**
> It works....:D

Found the d--ned NTFS partition.....

The guide is a little wrong with the  ¨--¨   signs

The file must look exactly as this:

```
#! /bin/sh -e

echo "Adding Windows" >&2
cat << EOF
menuentry "Windows XP" {
set root=(hd0,1)
chainloader +1
}
EOF
```


The kernel-helper script from old Grub also works and makes it possible to **add/remove** kernels....    (just download deb file > open with archive-manager > extract helper script)

Splash works....

Fix a new boot-splash....:D

Nice one plun!! Good thing we have you on our side.

See inxygnuu, i dont know any of that. Cant really get into heavy stuff like that either since i use Jaunty on our only computer(a laptop) and dual boot with Vista. If i break this machine i'll hear all about it from the wife.

Trying to got my old desktop here which is in another country at the moment and dedicate that to some serious testing and gonna build/buy another one for the same purposes.

---

### Post by ShirishAg75 on 2008-12-30
True, what I would like is if plun explains the script as well. For e.g. I don't understand the second line so having the whole script would also help us know what we are trying to do. That would be interesting for others here perhaps as well.

---

### Post by plun on 2008-12-30
> **ShirishAg75 said:**
> True, what I would like is if plun explains the script as well. For e.g. I don't understand the second line so having the whole script would also help us know what we are trying to do. That would be interesting for others here perhaps as well.

The blog URL again which I found

[http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)

""""""  must be changed within the script...:D


And this bug kills add or remove kernels for Grub2 users.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/253581](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/253581)

Walk around works....

---

### Post by Slug71 on 2008-12-30
plun, i see youve used packages grub2, grub-pc and grub-common from Debian to get grub2 working.
I just added Debians mirror to my sources list and opened synaptic and 196.20081201 is there but only Grub2 and grub-pc. No -common. Is that important or not. Im about to go ahead and give Grub2 another shot.

---

### Post by plun on 2008-12-30
> **Slug71 said:**
> plun, i see youve used packages grub2, grub-pc and grub-common from Debian to get grub2 working.
I just added Debians mirror to my sources list and opened synaptic and 196.20081201 is there but only Grub2 and grub-pc. No -common. Is that important or not. Im about to go ahead and give Grub2 another shot.

Its safest to use the same "platform" for all.... also a dependency

You can download the deb-file from the package info

[http://packages.debian.org/experimental/grub-common](http://packages.debian.org/experimental/grub-common)

Scroll down and choose your architecture > probably a US download

Also on the right you have other Grub-packages

You can do the same with Ubuntu packages.....

---

### Post by Slug71 on 2008-12-30
> **plun said:**
> Its safest to use the same "platform" for all.... also a dependency

You can download the deb-file from the package info

[http://packages.debian.org/experimental/grub-common](http://packages.debian.org/experimental/grub-common)

Scroll down and choose your architecture > probably a US download

Also on the right you have other Grub-packages

You can do the same with Ubuntu packages.....

Thanks, it was there, just had to type grub-common.
Only typed Grub2.

Just began the install.

---

### Post by Slug71 on 2008-12-30
The configuring grub-pc applet came up and 'chainload from menu.lst was checked. Do i need to add anything to the Linux command line?

Don't remember seeing that last time i tried grub2. Maybe thats why i broke it.

---

### Post by Starks on 2008-12-30
sudo upgrade-from-grub-legacy

---

### Post by Slug71 on 2008-12-30
> **Starks said:**
> sudo upgrade-from-grub-legacy

I just left it blank as i didnt want to make it permanent yet coz i hadnt restarted yet. 

Getting, "Error 11: Unrecognized device string" now when i try loading the kernel from Grub Legacy and when i try chainloading into Grub2.

---

### Post by RAOF on 2008-12-30
For those people with a Windows partition, it'd be interesting to see the output of
```

sudo os-prober

```

I don't have a Windows partition myself, but I *think* that should print something about Windows, and grub should automatically add it.

---

### Post by Slug71 on 2008-12-30
> **RAOF said:**
> For those people with a Windows partition, it'd be interesting to see the output of
```

sudo os-prober

```

I don't have a Windows partition myself, but I *think* that should print something about Windows, and grub should automatically add it.


I'll give it a try when i reinstall and try grub2 again.

---

### Post by Slug71 on 2008-12-31
> **Slug71 said:**
> The configuring grub-pc applet came up and 'chainload from menu.lst was checked. Do i need to add anything to the Linux command line?

Don't remember seeing that last time i tried grub2. Maybe thats why i broke it.

Ok so the applet that pops up during the Grub2 installation is a debconf applet and says "configuring grub-pc".

The little box under where it says "Linux command line" is for the 'kopt' parameter which i guess is supposed to be detected automatically from menu.lst  but for some reason mine was just blank and i left it that way.

When i reinstalled i tried it again but this time added
> kopt=root=UUID=0374d763-43b0-468d-9d22-3367b8f03608 ro
to the above mentioned box which i got from my menu.lst.
Then went to terminal and typed 
```
sudo update-grub
```
after the installation finished which i didnt do the first time.

Rebooted and still got the Error 11: Unrecognized device string.

What am i forgetting or doing wrong?

---

### Post by plun on 2008-12-31
> **RAOF said:**
> For those people with a Windows partition, it'd be interesting to see the output of
```

sudo os-prober

```

I don't have a Windows partition myself, but I *think* that should print something about Windows, and grub should automatically add it.

Yes it print for me 

```
plun@plun:~$ sudo os-prober
/dev/sda1:Microsoft Windows XP Home Edition:Windows:chain

```

If so, os-prober should be a **dependency for Grub2** ?

It seems to work because now its changed...:D

```
plun@plun:~$ sudo update-grub
Generating grub.cfg ...
Found Debian background: Plasma-lamp.tga
Found linux image: /boot/vmlinuz-2.6.28-4-generic
Found initrd image: /boot/initrd.img-2.6.28-4-generic
Found linux image: /boot/vmlinuz-2.6.28-3-generic
Found initrd image: /boot/initrd.img-2.6.28-3-generic
Adding Windows
Found memtest86+ image: /boot/memtest86+.bin
**Found Microsoft Windows XP Home Edition on /dev/sda1**
done

```


As I wrote this guide just works... except that paraphrases must be changed

[http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)

Someone must test this with just os-prober....


@Slug71

sudo update-grub

sudo update-grub2

---

### Post by pulpo69 on 2008-12-31
slug71 and plun thankyou, you will make that we see grub2 and ext4 in jaunty. happy new year

---

### Post by Slug71 on 2008-12-31
> **plun said:**
> 
@Slug71

sudo update-grub

sudo update-grub2

@plun
Ok, so i just reinstalled grub2,

entered this 

'kopt=root=UUID=0374d763-43b0-468d-9d22-3367b8f03608 ro'

as the 'kopt' parameter in grub-pc configuration. Installation finished then went to terminal and typed

```
sudo update-grub
sudo update-grub2
```

and thats ALL ive done.
Anything else i should do before i restart?

---

### Post by plun on 2008-12-31
I didn't add anything... left it blank

You can see my output earlier for a update-grub

---

### Post by Slug71 on 2008-12-31
> **plun said:**
> I didn't add anything... left it blank

You can see my output earlier for a update-grub

Ok thanks, will leave it blank on the next try if this one doesnt work.

i havent tried leaving it blank and typing

```
sudo update-grub
sudo update-grub2
```

into terminal which is probably why it hasnt worked.


my output from update-grub
> xxxxxxxx@xxxxxx:~$ sudo update-grub
[sudo] password for xxxxxxxx: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.27-7-generic
Found initrd image: /boot/initrd.img-2.6.27-7-generic
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by plun on 2008-12-31
> **Slug71 said:**
> Ok thanks, will leave it blank on the next try if this one doesnt work.

i havent tried leaving it blank and typing

```
sudo update-grub
sudo update-grub2
```

into terminal which is probably why it hasnt worked.


my output from update-grub

Ok... this must be tested and you are also blocked with the **kernel-helper script** mentioned earlier and also within the bug report which I added.

Newer kernels **are blocked** because of this Grub2 bug....

You can download standard GRUB, open with archive manager > extract the script > gksudo nautilus and put it in /usr/sbin...

"Bless this mess"...:D

---

### Post by Slug71 on 2008-12-31
> **plun said:**
> Ok... this must be tested and you are also blocked with the **kernel-helper script** mentioned earlier and also within the bug report which I added.

Newer kernels **are blocked** because of this Grub2 bug....

You can download standard GRUB, open with archive manager > extract the script > gksudo nautilus and put it in /usr/sbin...

"Bless this mess"...:D


Ok, so ive tried it by entering that above line to the box and leaving it blank and both times ive used the terminal commands and im still getting that damn error. :confused::confused:


Edit: Perhaps i need to change the drive numbering from 0 to 1 manually but where would i do that? Doesnt look like theres anything to change within menu.lst?

---

### Post by PmDematagoda on 2009-01-01
I've spent some time getting GRUB 2 up and running on my Gentoo install(well, on my desktop to be specific), and a few things have changed.

1) menu.lst is now grub.cfg, if you want to configure GRUB 2, that's where you should look.

2) The partition numbering is now changed, it now starts from 1, not 0. The hard-drive numbering is still the same.

3) The way in which menu items are specified are now different, they are more "bashish" so to say.

A grub.cfg example is [here]("http://grub.enbug.org/grub.cfg").

By the way, having a 1024x768 resolution with 32-bit colours(according to the wiki at the least), without hacks, is a pretty good feeling;).

---

### Post by plun on 2009-01-01
I didn't change anything except for Windows and also the os-prober after RAOF mentioned it.

He also mentioned this bug within the bug report

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497791](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497791)


With nano not gedit you can change grub.cfg


Debians versions can also be uninstalled and Jauntys installed instead... but then
other bugs will be involved..   "The cat and the rat"...

---

### Post by Gina on 2009-01-01
> **PmDematagoda said:**
> 
2) The partition numbering is now changed, it now starts from 1, not 0. The hard-drive numbering is still the same.

Oh dear - half a job :(  I'd have thought that if the partitioning numbering starts from 1 then the drive numbering should also start from 1 to be consistent.  Maybe this isn't the end of the matter though.

---

### Post by plun on 2009-01-01
> **Gina said:**
> Oh dear - half a job :(  I'd have thought that if the partitioning numbering starts from 1 then the drive numbering should also start from 1 to be consistent.  Maybe this isn't the end of the matter though.

Well... about numbering is also mentioned within this blog

[http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)


SuperGrub on a USB stick is also probably a good idea for happy testers ....:D

[http://forjamari.linex.org/projects/supergrub/](http://forjamari.linex.org/projects/supergrub/)


Nevertheless the numbering should be automagic.. if not "file a bug"  !!!

---

### Post by ShirishAg75 on 2009-01-01
Guys, has anybody tried the debian experimental?

[http://packages.debian.org/changelogs/pool/main/g/grub2/grub2_1.96+20081201-1/changelog](http://packages.debian.org/changelogs/pool/main/g/grub2/grub2_1.96+20081201-1/changelog)

---

### Post by plun on 2009-01-01
> **ShirishAg75 said:**
> Guys, has anybody tried the debian experimental?

[http://packages.debian.org/changelogs/pool/main/g/grub2/grub2_1.96+20081201-1/changelog](http://packages.debian.org/changelogs/pool/main/g/grub2/grub2_1.96+20081201-1/changelog)

Yup... I am

grub-pc_1.96+20081201-1_i386.deb

grub-common_1.96+20081201-1_i386.deb

grub2_1.96+20081201-1_i386.deb

and os-prober from Jauntys repo

Also the walk around for kernel-helper script.....


Startupmanager also works....no need for "fiddeling" with config files..:D

---

### Post by Starks on 2009-01-01
Are all of the startupmanager tabs preserved or different?

---

### Post by plun on 2009-01-01
> **Starks said:**
> Are all of the startupmanager tabs preserved or different?

No its the same startupmanager....

Package info:
[http://packages.ubuntu.com/jaunty/startupmanager](http://packages.ubuntu.com/jaunty/startupmanager)

According to changelog it should be compatible


Added boot splash and also text, also changed splash without any trouble

[[img]http://ubuntu-pics.de/thumb/7842/start_00zX1V.jpg[/img]](http://ubuntu-pics.de/bild/7842/start_00zX1V.jpg)


The menu splash must be configured with config as I can see 

[http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/](http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/)


A little ugly when going from menu to boot splash....:P

---

### Post by Starks on 2009-01-01
Same startupmanager my ***... This is how it should look.

[[IMG]http://img229.imageshack.us/img229/5301/youlosttabsll5.th.png[/IMG]](http://img229.imageshack.us/my.php?image=youlosttabsll5.png)

---

### Post by plun on 2009-01-01
> **Starks said:**
> Same startupmanager my ***... This is how it should look.

[[IMG]http://img229.imageshack.us/img229/5301/youlosttabsll5.th.png[/IMG]](http://img229.imageshack.us/my.php?image=youlosttabsll5.png)

Well... strange...:D

```
plun@plun:~$ **dpkg -s startupmanager**
Package: startupmanager
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 1072
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: all
**Version: 1.9.12-1**
Depends: python, python-central (>= 0.6.7), python-glade2 (>= 2.12), python-gnome2 (>= 2.20), python-libxml2 (>= 2.6.30), yelp, grub, menu
Description: Grub and Splash screen configuration
 StartUp-Manager configures some settings for grub and splash screens
 (Currently only Usplash). It provides an easy to use interface.
 .
 It is originally a Ubuntu project, adapted for Debian.
Original-Maintainer: Python Applications Packaging Team <python-apps-team@lists.alioth.debian.org>
Homepage: https://launchpad.net/startup-manager
Python-Version: current

```


But... Ive seen also your GUI....   gksudo gives the same...

:confused:

---

### Post by Slug71 on 2009-01-01
> **ShirishAg75 said:**
> Guys, has anybody tried the debian experimental?

[http://packages.debian.org/changelogs/pool/main/g/grub2/grub2_1.96+20081201-1/changelog](http://packages.debian.org/changelogs/pool/main/g/grub2/grub2_1.96+20081201-1/changelog)


Yep, thats the one iv'e been trying.

---

### Post by Starks on 2009-01-01
```
eric@kingfisher:~$ dpkg -s startupmanager
Package: startupmanager
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 1072
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: all
Version: 1.9.12-1
Depends: python, python-central (>= 0.6.7), python-glade2 (>= 2.12), python-gnome2 (>= 2.20), python-libxml2 (>= 2.6.30), yelp, grub, menu
Description: Grub and Splash screen configuration
 StartUp-Manager configures some settings for grub and splash screens
 (Currently only Usplash). It provides an easy to use interface.
 .
 It is originally a Ubuntu project, adapted for Debian.
Original-Maintainer: Python Applications Packaging Team <python-apps-team@lists.alioth.debian.org>
Homepage: https://launchpad.net/startup-manager
Python-Version: current

```

---

### Post by Slug71 on 2009-01-01
What i find strange is the output of 

```
sudo fdisk -l
```

gives me

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91fd7c02

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5471    43945776    b  W95 FAT32
/dev/sda2            5472       14593    73272465    5  Extended
/dev/sda5            5472       10942    43945776    b  W95 FAT32
/dev/sda6           10943       13009    16603146   83  Linux
/dev/sda7           13010       13258     2000061   82  Linux swap / Solaris
/dev/sda8           13259       14593    10723356   83  Linux


But my Hdd is partitioned as

Windows Vista
Shared FAT32
EXT3 /
Swap
EXT3 /home.

For some reason the above shows 2 FAT32 and an Extended in the middle??


Update: Nevermind i figured it out. sda5/6/7/8 are all divided on sda2 as sda5/6/7/8 are all Extended.
        
Weird how it lists it like that.

Perhaps /(sda6) should be a Primary partition??

---

### Post by Gina on 2009-01-01
Logical partitions within an Extended partition always start at 5.  Everything seems fine with you fdisk list except that your Vista partition is listed as W95 FAT32 rather than NTFS (unles you really DO have your Vista installed on a FAT32 partition).

Your fdisk list is saying you have one Primary partition (sda1) an Extended partition (sda2) and 4 Logical partitions numbered 5 - 8 which reside within the Extended partition.

This partitioning system seems to go back to the year dot! :lolflag:  Actually, it's not really funny, it's a pain!

EDIT To answer your question about sda6 (used as /) - Linux is quite happy to use Logical partitions.  Not sure about Vista but earlier versions of Windows needed to be installed on a Primary partition.

---

### Post by plun on 2009-01-01
Well... thats a challenge..:D

Can you boot ?

The easiest way to get SuperGrub is with UNetbootin

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Then just chooses the SuperGrub entry and your USB stick

And perhaps a pray....:P

---

### Post by Slug71 on 2009-01-01
As far as i know Vista is definitely an NTFS partition. When i install Ubuntu the partitioner recognises it as NTFS.

@plun, 
Yeh i can boot fine using Grub Legacy but when i install grub2, thats when i get 'Error 11: Unrecognisable device string'.



Update: Just booted Vista to check drive C: and it's NTFS.

---

### Post by plun on 2009-01-01
> **Slug71 said:**
> 
Yeh i can boot fine using Grub Legacy but when i install grub2, thats when i get 'Error 11: Unrecognisable device string'.

Thats great !!!

Did you read about the os-prober ???

There is **no need** for a Windows script if the os-prober is installed.

```
plun@plun:~$ sudo os-prober
/dev/sda1:Microsoft Windows XP Home Edition:Windows:chain

```

You can read about numbering in below URL

[http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)


Also **download UNetbootin** and create an **emergency SuperGrub** USB stick...

If something totally brakes ....:redface:

---

### Post by Slug71 on 2009-01-01
I did thanks plun,

Im curious though, when i select my Kernel from Grub Legacy the next screen says 'booting from (hdo,5) Ext3 but im pretty sure in my grub.cfg file when i install grub2 it says something about (hd0,6). Now i know the partition numbering changes but i can see how perhaps it has something to do with that.

Will post my menu.lst from Grub and then grub.cfg from Grub2.

---

### Post by Slug71 on 2009-01-01
Grub Legacy - menu.lst:


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=afd88923-0b1d-451a-993c-fe4ba4f7df8b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=afd88923-0b1d-451a-993c-fe4ba4f7df8b

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

---

### Post by Slug71 on 2009-01-01
Grub2 - grub.cfg from Debian experimental version 1.96.20081201.

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from  and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd0,6)
search --fs-uuid --set afd88923-0b1d-451a-993c-fe4ba4f7df8b
if font /usr/share/grub/ascii.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_freebsd ###
### END /etc/grub.d/10_freebsd ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu GNU/Linux, linux 2.6.28-4-generic" {
	set root=(hd0,6)
	search --fs-uuid --set afd88923-0b1d-451a-993c-fe4ba4f7df8b
	linux	/boot/vmlinuz-2.6.28-4-generic root=UUID=afd88923-0b1d-451a-993c-fe4ba4f7df8b ro quiet 
	initrd	/boot/initrd.img-2.6.28-4-generic
}
menuentry "Ubuntu GNU/Linux, linux 2.6.28-4-generic (single-user mode)" {
	set root=(hd0,6)
	search --fs-uuid --set afd88923-0b1d-451a-993c-fe4ba4f7df8b
	linux	/boot/vmlinuz-2.6.28-4-generic root=UUID=afd88923-0b1d-451a-993c-fe4ba4f7df8b ro single quiet
	initrd	/boot/initrd.img-2.6.28-4-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

---

### Post by plun on 2009-01-01
OK....

install os-prober

```
sudo apt-get install os-prober

sudo os-prober
```

Output ????
```

sudo update-grub2
```

Output ?

---

### Post by Timon&amp;Pumba on 2009-01-01
Well, I just upgraded my jaunty installation to grub2.
First I chainloaded to grub2 via grub-legacy. That step did not go as it should be. The script configured all the entries in grub-legacy with the UUID device string (something like 2218e778-3199-45b6-ab70-b84e908ee135). The error I got was "device string not recognized". Altering it manually in (hd0,0) gave me access to grub2, which in turn was configured fine. Running the "real" upgrade script (upgrade-from-grub-legacy) also succeeded.

So, basically, the "safe" way of testing grub2 was in my case the most troublesome. Anyone experienced that?

---

### Post by plun on 2009-01-01
> **Timon&Pumba said:**
>  Running the "real" upgrade script (upgrade-from-grub-legacy) also succeeded.

So, basically, the "safe" way of testing grub2 was in my case the most troublesome. Anyone experienced that?

Yup, it broke a month ago for me so I just skipped it now and went directly to  "upgrade-from-grub-legacy".....

But.. this breaks PCs for some users and some sort of precautions must be done.. I just dont know how, SuperGrub is a minimum 

AND BACKUPS....

I also dont think that Debian will do this for us.

---

### Post by Slug71 on 2009-01-01
> **plun said:**
> OK....

install os-prober

```
sudo apt-get install os-prober

sudo os-prober
```

Output ????
```

sudo update-grub2
```

Output ?

I currently have Grub Legacy installed. I installed Grub2 to post the grub.cfg file and then reinstalled Grub Legacy.

Installed os prober with Grub Legacy installed though and the output of 

```
sudo os-prober
```

gave me
> 
/dev/sda1:Windows Vista/Longhorn (loader):Windows:chain

---

### Post by Slug71 on 2009-01-01
> **Timon&Pumba said:**
> Well, I just upgraded my jaunty installation to grub2.
First I chainloaded to grub2 via grub-legacy. That step did not go as it should be. The script configured all the entries in grub-legacy with the UUID device string (something like 2218e778-3199-45b6-ab70-b84e908ee135). The error I got was "device string not recognized". Altering it manually in (hd0,0) gave me access to grub2, which in turn was configured fine. Running the "real" upgrade script (upgrade-from-grub-legacy) also succeeded.

So, basically, the "safe" way of testing grub2 was in my case the most troublesome. Anyone experienced that?

You refering to Error 11: Unrecognisable device string??

Thats what i'm getting when i try to chainload into Grub2.
And i cant access my Kernel below the 'chainload into Grub2' section either. Same Error.

---

### Post by plun on 2009-01-01
> **Slug71 said:**
> I currently have Grub Legacy installed. I installed Grub2 to post the grub.cfg file and then reinstalled Grub Legacy.

Installed os prober with Grub Legacy installed though and the output of 

```
sudo os-prober
```

gave me

OK....

Before you run a complete upgrade with  the command "upgrade-from-grub-legacy" you updates Grub2 with the command **update-grub2**

after complete upgrade with just **update-grub**
[B]
The bug report must be updated with findings !!![/B]

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/312310](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/312310)

I just added that os-prober works and you confirmed that with your command.


So...:D  upgrade-from-grub-legacy .....  its up to you...

Everything can break...!!!!

---

### Post by Slug71 on 2009-01-01
So i run 

```
update-grub
```

After 

```
upgrade-from-grub-legacy
```

??

---

### Post by plun on 2009-01-01
> **Slug71 said:**
> So i run 

```
update-grub
```

After 

```
upgrade-from-grub-legacy
```

??

Please read this one carefully.... **all steps !**

[http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)

os-prober covers the Windows problem, step 3


I am NOT using extended partitions and cannot give any recommendations...

It probably works as also Timon & Pumba wrote.


Then again to have a SuperGrub USB stick as a emergency entrance...not so fun sitting with a non-bootable PC...


Perhaps others within our community has better advices...:confused:

---

### Post by Slug71 on 2009-01-01
Well i'm not to worried about Windows for now. I can get into Windows fine, even after installing grub2.

the problem i have is i cannot chainload into grub2 from grub legacy and i cannot access Ubuntu in the lower grub 1.5 section but Windows is still accessable.

---

### Post by plun on 2009-01-01
> **Slug71 said:**
> Well i'm not to worried about Windows for now. I can get into Windows fine, even after installing grub2.

the problem i have is i cannot chainload into grub2 from grub legacy and i cannot access Ubuntu in the lower grub 1.5 section but Windows is still accessable.

Yes and that is probably the same as for "Timon & Pumba"

[http://ubuntuforums.org/showpost.php?p=6475167&postcount=130](http://ubuntuforums.org/showpost.php?p=6475167&postcount=130)

You can take a chance or use the bug report and wait.

or try to sort out your partitions why the chainload fails.

If you take a chance.. first take some time so you have a working SuperGrub.   

Or that someone else can give more clues....

---

### Post by Slug71 on 2009-01-01
AH HA, I has gots it!!

Installed Grub2 from Debian.
Left that box blank.

Then ran in Terminal 
```

sudo update-grub2
```

```
sudo upgrade-from-grub-legacy
```

```
sudo update-grub
```
```

sudo apt-get install os-prober
```

Rebooted and Grub2 works!

---

### Post by Slug71 on 2009-01-01
For some reason the chainloader didnt like my drive.

Output of os prober

```
/dev/sda1:Windows Vista/Longhorn (loader):Windows:chain
```


Vista isnt in my grub menu though but i can fix that.

---

### Post by plun on 2009-01-01
> **Slug71 said:**
> AH HA, I has gots it!!

Rebooted and Grub2 works!

Congrats.... :D

Please also add info about your error within the bug report....


The kernel-helper script is also broken,  I wrote a reference to that within the bug report


To give you your Windows partitions you probably also needs another round with os-prober

```
sudo os-prober

sudo update-grub
```

:popcorn:

Time to sleep...

---

### Post by Gina on 2009-01-01
Goodnight plun :)

---

### Post by Slug71 on 2009-01-01
> **plun said:**
> Congrats.... :D

Please also add info about your error within the bug report....


The kernel-helper script is also broken,  I wrote a reference to that within the bug report


To give you your Windows partitions you probably also needs another round with os-prober

```
sudo os-prober

sudo update-grub
```

:popcorn:

Time to sleep...

Goodnite plun and thanks :D and Happy New Year :D

```

sudo os-prober

sudo update-grub
```

Worked!:)

---

### Post by Gina on 2009-01-01
Happy New Year from me too :)

---

### Post by autocrosser on 2009-01-01
Happy New Year to all!!!!

It's great working with all of you!!!!

---

### Post by Slug71 on 2009-01-01
Sure is autocrosser,

Happy New Year to Everyone!!

---

### Post by Slug71 on 2009-01-01
> **RAOF said:**
> For those people with a Windows partition, it'd be interesting to see the output of
```

sudo os-prober

```

I don't have a Windows partition myself, but I *think* that should print something about Windows, and grub should automatically add it.

Worked for me too.:)

---

### Post by Slug71 on 2009-01-02
@plun,

Did you change your splash image using this method?

[http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/](http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/)

---

### Post by ShirishAg75 on 2009-01-02
I played around with that and yes it works. There are also a handy grub2-splashimages additional package as well. At the end it just needs a 16-bit color .TGA file with a path showing where to take from.

---

### Post by Slug71 on 2009-01-03
Hmmm..
This didnt work for me from that guide.

> debian:~# nano /etc/grub.d/05_debian_theme
and change the following line from:

for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga}

to

for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/Plasma-lamp.{png,tga}
and save the file.

I got this
> 
Error writing etc/grub.d/05_debian_theme: permission denied

I have the Grub2 Splash images installed. 

When i make the changes i want as per the guide above, i hit Ctrl-X to exit and then hit Enter on the following option 'File Name to Write: /etc/grub.d/05_debian_theme and then i get that Error message.

---

### Post by BwackNinja on 2009-01-04
Check the permissions on the file, it might be marked read-only.

---

### Post by plun on 2009-01-04
> **Slug71 said:**
> Hmmm..
This didnt work for me from that guide.






OK...

The author is a Debian user and probably runs with root permission...  sudo !!!!

> sudo nano  

```
sudo gedit
```   is better IMHO...

EDIT Howto

[http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/](http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/)

.

---

### Post by Slug71 on 2009-01-04
Thanks plun, :D

```
sudo gedit
```

worked.

---

### Post by Gina on 2009-01-04
Being pernickety... **gksudo gedit** is preferred (or gksu gedit).  I'm told there is a possibility of problems with sudo and GUI apps.

---

### Post by plun on 2009-01-04
> **Gina said:**
> Being pernickety... **gksudo gedit** is preferred (or gksu gedit).  I'm told there is a possibility of problems with sudo and GUI apps.

Yes you are 100% correct...:oops:

Just difficult to remember it...sudo can be done in sleep...:D

Psychocats about gksudo

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)


A user can mess up permissions with sudo....a "long-shot" IMHO but a risk..

---

### Post by Gina on 2009-01-04
Must admit I used sudo with gedit and other GUI apps until it was pointed out in these forums and linked to Psychocats.  Then I thought "better do as advised" :lolflag:

Didn't mean to embarrass you BTW :)

---

### Post by plun on 2009-01-04
> **Gina said:**
> Must admit I used sudo with gedit and other GUI apps until it was pointed out in these forums and linked to Psychocats.  Then I thought "better do as advised" :lolflag:

Didn't mean to embarrass you BTW :)

No... Its OK, no problem  :D

sudo gedit is no problem... but sudo firefox can be a mess.

sudo gedit is much better then sudo nano within a GUI.


Most important is to keep root intact as Ubuntu does with sudo....otherwise it can be a big "Windows mess" of everything.

---

### Post by ShirishAg75 on 2009-01-04
I like leafpad, its much more cleaner than gedit :)

---

### Post by ShirishAg75 on 2009-01-04
> **Gina said:**
> Being pernickety... **gksudo gedit** is preferred (or gksu gedit).  I'm told there is a possibility of problems with sudo and GUI apps.

what is most interesting/entertaining I like is just using gksu. Just try it 

```
$ gksu 
```

---

### Post by ShirishAg75 on 2009-01-05
Back on topic though. 
    The bugs need to be filed against ubiquity . One way would be to just file it against ubiquity (1)
and hope they look at it or do some sort of request/discussion on the ubuntu-installer mailing list (2) . 

1. [https://launchpad.net/ubiquity](https://launchpad.net/ubiquity)
2. [https://lists.ubuntu.com/mailman/listinfo/ubuntu-installer](https://lists.ubuntu.com/mailman/listinfo/ubuntu-installer)

---

### Post by albinootje on 2009-01-05
> **plun said:**
> No... Its OK, no problem  :D

sudo gedit is no problem... but sudo firefox can be a mess.


sudo firefox ?
Tell me why you would ever want to run Firefox as root ?

---

### Post by plun on 2009-01-05
> **albinootje said:**
> sudo firefox ?
Tell me why you would ever want to run Firefox as root ?

Well... for my personal needs never..  it a reference case within Psychocats howto.

 [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Just to read it...

---

### Post by albinootje on 2009-01-05
> **plun said:**
> Well... for my personal needs never..  it a reference case within Psychocats howto.

 [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Just to read it...

Yes, I read it before, and I find "sudo firefox" a hilarious example.

The psychocats pages are very nice to have, I appreciate them a lot, but the specific example is a very bad example imho.

Just my 2 cents.

---

### Post by plun on 2009-01-05
> **albinootje said:**
> Yes, I read it before, and I find "sudo firefox" a hilarious example.

The psychocats pages are very nice to have, I appreciate them a lot, but the specific example is a very bad example imho.

Just my 2 cents.

Yup... I called it a "long-shot" earlier within a post...

But everything is possible...  some "newbies" going nuts over root and therefore Psychocats howto is OK.

---

### Post by Gina on 2009-01-05
I found the Psychocats HowTos very helpful when I first started using Ubuntu :)

---

### Post by ShirishAg75 on 2009-01-07
On phoronix about grub2 new font engine for support of internationalization 

[http://www.phoronix.com/scan.php?page=news_item&px=Njk2Nw](http://www.phoronix.com/scan.php?page=news_item&px=Njk2Nw)

---

### Post by ShirishAg75 on 2009-01-07
People, 

 we already seem to have the latest e2fsprogs (atleast as far as debian is concerned) [http://packages.debian.org/search?keywords=e2fsprogs&searchon=names&suite=all&section=all](http://packages.debian.org/search?keywords=e2fsprogs&searchon=names&suite=all&section=all)

or am I missing something?

---

### Post by Slug71 on 2009-01-07
> **ShirishAg75 said:**
> People, 

 we already seem to have the latest e2fsprogs (atleast as far as debian is concerned) [http://packages.debian.org/search?keywords=e2fsprogs&searchon=names&suite=all&section=all](http://packages.debian.org/search?keywords=e2fsprogs&searchon=names&suite=all&section=all)

or am I missing something?

Indeed i believe we do.
Could be wrong though.

---

### Post by ShirishAg75 on 2009-01-07
I had read on this bug [lpbug]293465[/lpbug]

Look at Theodore Tso's comments. With just a week and a day to go for alpha 3 if they get ubiquity to do its bidding we might as well have ext4 as an installation option to play in the live CD.

---

### Post by cjwatson on 2009-01-08
Somebody's very confused. grub-installer is the installer component that installs grub. You can't use it on a regular system, and 'aptitude show' won't show it. Don't waste time following this red herring unless you are busy with installer development. :-)

---

### Post by cjwatson on 2009-01-08
Colin King has backported ext4 support to grub 1, so you don't need grub 2 just for that any more.

---

### Post by Slug71 on 2009-01-10
Just installed Grub2 to see if it plays nice with the Ext4 partition and it played very nice.
Used the version within Jaunty this time and not the Debian experimental and noticed that os-prober was part of the dependencies and picked my NTFS partition right off the bat. :D

---

### Post by Slug71 on 2009-01-10
My last post here just disappeared? :confused:

Now i see it.:P

---

### Post by ShirishAg75 on 2009-01-10
> **cjwatson said:**
> Somebody's very confused. grub-installer is the installer component that installs grub. You can't use it on a regular system, and 'aptitude show' won't show it. Don't waste time following this red herring unless you are busy with installer development. :-)

Thank you, found out the very same thing . The thing it seems is grub2 releases seem to be very inconsistent. 

They have been trying to follow 1 stable release and 2 unstable release within a span of 3 months but haven't been able to deliver on the same :(

---

### Post by Slug71 on 2009-01-10
> **ShirishAg75 said:**
> Thank you, found out the very same thing . The thing it seems is grub2 releases seem to be very inconsistent. 

They have been trying to follow 1 stable release and 2 unstable release within a span of 3 months but haven't been able to deliver on the same :(

Yeh Grub2 is all over the place and very slow. Probably why its been in development for such a long time.

---

### Post by ShirishAg75 on 2009-01-11
This is what I was talking about. Also gives a rough number of things of what is needed to grub2. 

[http://lists.gnu.org/archive/html/grub-devel/2009-01/msg00016.html](http://lists.gnu.org/archive/html/grub-devel/2009-01/msg00016.html)

---

### Post by Slug71 on 2009-01-11
> **ShirishAg75 said:**
> This is what I was talking about. Also gives a rough number of things of what is needed to grub2. 

[http://lists.gnu.org/archive/html/grub-devel/2009-01/msg00016.html](http://lists.gnu.org/archive/html/grub-devel/2009-01/msg00016.html)


Thanks, well lets hope it just happens so that Grub2 can get pushed out finally. :)

---

### Post by ShirishAg75 on 2009-01-11
Looking at that list I'll wager it will take atleast 6 months to a year. Would be happy with some good releases in the interim. Having USB support in grub2 would be nice though.

---

### Post by Slug71 on 2009-01-11
> **ShirishAg75 said:**
> Looking at that list I'll wager it will take atleast 6 months to a year. Would be happy with some good releases in the interim. Having USB support in grub2 would be nice though.

Hope the writer knows that NTFS is solved using os-prober.

---

### Post by ShirishAg75 on 2009-01-11
my guess is  that the os-prober is an interim solution. Grub2 (like its predecssor) needs to be able to do all in its own. It shouldn't need extra utilities. It is also used in low-memory devices as well.

---

### Post by Slug71 on 2009-02-05
Anyone know if Grub2 can boot XFS filesystems yet?

---

