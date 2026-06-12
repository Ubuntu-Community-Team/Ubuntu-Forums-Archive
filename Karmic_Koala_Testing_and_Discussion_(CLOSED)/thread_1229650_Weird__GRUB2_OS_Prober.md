---
title: "Weird  GRUB2 OS Prober"
date: 2009-08-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xebian on 2009-08-02
Not sure if it just me but it found the UUID and used it on the search line.  However it insists on using /dev/sdaN for the root=  ???  It's annoying when these /dev/sdAN changes when you have PnP drives.  

I thought UUID is the proper and better way since Hardy? or Intrepid?

```
menuentry "Debian GNU/Linux (squeeze/sid) (on /dev/sda6)" {
        set root=(hd0,6)
        search --no-floppy --fs-uuid --set c48c772a-4217-482f-b264-344f303d2e20
        linux /boot/vmlinuz-2.6.30-1-amd64 root=/dev/sda6
        initrd /boot/initrd.img-2.6.30-1-amd64
}
```

What is even more weird is it picks up obsolete UUID if there is an old menu.lst around.

Anyone seeing this too?

---

### Post by ranch hand on 2009-08-03
Looks like my menu entries;
```

menuentry "Ubuntu, Linux 2.6.31-4-generic" {
	set root=(hd0,13)
	search --no-floppy --fs-uuid --set 291d5f24-4ce9-4125-953f-3d1f52376948
	linux	/boot/vmlinuz-2.6.31-4-generic root=UUID=291d5f24-4ce9-4125-953f-3d1f52376948 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-4-generic
}

```
Haven't had old files around but I am sure that it would because it has the search for grub-legacy files.

---

### Post by dino99 on 2009-08-03
yes, it need manual help to be up to date.
I've installed grub-pc & os-prober on 3 distro: karmic32, jaunty32 & jaunty64 (each on their own separate hdd).
When an kernel upgrade happen on Jaunty, the process seem to run normally but grub2 menu don't update, even if i remove the old kernel.
I have to boot Karmic & there in a console, run os-prober, grub-mkconfig & then update-grub2: now grub2 menu is updated.

Note: each distro is bootable from each hdd (security if one fail or if i move one hdd outside)

---

### Post by ranch hand on 2009-08-03
I would, in your Jaunty, remove (synaptic) anything about grub to make sure that grub-legacy is gone.

I would clean up as many old kernals as you can stand to see go.  9.04 is stable.  I would get rid of them all.  If you click on status (bottom left in synaptic) there should be a line about stuff that can be auto removed.  Clear it out.

Then install grub2 again.  It should work fine in Jaunty.

---

### Post by dino99 on 2009-08-03
Thanks Ranch,

yes i know all the good things to clean up my installs but, as you said, sometimes we need to remove/purge all and reinstall again, that's often happen on old install that have been upgraded a lot of time: not all old settings are removed. This is very irritating and common on linux, bad.
Hope the core devs, in future, have a look at this problem, to let the distro clean and stable: i have already report bugs made by non removed old settings.
Unfortunately, even if you search orphans or use janitor, that's not enough.

What i think: grub2 & os-prober are not ready yet to be included in a stable distro (maybe usable for karmic +1) and they are not often updated (know that some guys actively work on them)

---

### Post by ranch hand on 2009-08-03
I have 19 OS' on board at this time.  I am having trouble with 2 and do not think that grub2 is to blame as I was having trouble in grub-legacy (Mandriva2009-1 both KDE & Gnome).

I believe that it is ready, or will be for 9.10.  I think that it is harder for those of us that have come to love grub-legacy than it will be for new users as so much is different.

It better be released whit 9.10 so that we can develope experience and smooth the  operation before the deluge hits with 10.04 LTS.

Right now, though, I think we are all suffering from GAD (Gnome Anxiety Disorder).

[http://ubuntuforums.org/showthread.php?t=1223280&page=5](http://ubuntuforums.org/showthread.php?t=1223280&page=5)

The link above is kind of embarassing as it shows me in my grumpy geezer mode (I'm sorry - GAD) but the help is very good.

The ones below are great.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I used this one to set up a background 
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

---

### Post by drs305 on 2009-08-03
> **ranch hand said:**
> 
It better be released whit 9.10 so that we can develope experience and smooth the  operation before the deluge hits with 10.04 LTS.


Here are links to the official announcement that Grub 2 will be the default for Karmic:

[Official Announcement]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000573.html")
Story:
[http://www.ubuntugeek.com/grub-2-now-default-for-ubuntu-910-karmic-koala.html]("http://www.ubuntugeek.com/grub-2-now-default-for-ubuntu-910-karmic-koala.html")

---

### Post by ranch hand on 2009-08-03
Yup, I had read that and, with some GAD induced worry, am excited about this.  I think that there are going to be a LOT of problems in the next few months as folks have trouble dealing with grub2.

I think new users will be happier with it.

With my custom menu entries the 9.10 (test platforms) are all on top, the top is boot/root.  Starting at the lowest 9.10 and working up the one I am booting from updates auto (if needed) and I am on it to edit any custom entries I need to.

If it is running this well on this rather rough platform it should run very well on a stable release (actively repressing GAD).

---

### Post by beacon on 2009-08-17
This is silly, I know, but I have downloaded os-prober. How do I run it?

---

### Post by ranch hand on 2009-08-17
Applications->Accessories->Terminal

At the prompt type "sudo os-prober" like so;
```

jak@jak-desktop:~$ sudo os-prober
[sudo] password for jak: 
/dev/sda1:Debian GNU/Linux (5.0.2):Debian:linux
/dev/sda3:Ubuntu 9.04 (9.04):Ubuntu:linux
/dev/sda8:Debian GNU/Linux (5.0.2):Debian1:linux
/dev/sdb10:Ubuntu karmic (development branch) (9.10):Ubuntu1:linux
/dev/sdb12:Mandriva Linux 2009.0 (2009.0):MandrivaLinux:linux
/dev/sdb14:Mandriva Linux 2009.0 (2009.0):MandrivaLinux1:linux
/dev/sdb16:Ubuntu karmic (development branch) (9.10):Ubuntu2:linux
/dev/sdb18:Ubuntu 9.04 (9.04):Ubuntu3:linux
/dev/sdb20:Ubuntu karmic (development branch) (9.10):Ubuntu4:linux
/dev/sdb8:Ubuntu 9.04 (9.04):Ubuntu5:linux
/dev/sdg10:Ubuntu karmic (development branch) (9.10):Ubuntu6:linux
/dev/sdg11:Ubuntu 9.04 (9.04):Ubuntu7:linux
/dev/sdg12:Ubuntu karmic (development branch) (9.10):Ubuntu8:linux
/dev/sdg13:Ubuntu karmic (development branch) (9.10):Ubuntu9:linux
/dev/sdg14:Mandriva Linux 2009.1 (2009.1):MandrivaLinux2:linux
/dev/sdg15:Mandriva Linux 2009.1 (2009.1):MandrivaLinux3:linux
/dev/sdg16:Ubuntu karmic (development branch) (9.10):Ubuntu10:linux
/dev/sdg6:Ubuntu 8.04.3 LTS (8.04):Ubuntu11:linux
/dev/sdg7:Ubuntu 9.04 (9.04):Ubuntu12:linux
/dev/sdg8:Ubuntu karmic (development branch) (9.10):Ubuntu13:linux
/dev/sdg9:Ubuntu 9.04 (9.04):Ubuntu14:linux

```
That is the result of all 3 drives on my box.  They each actually have a menu individually.  Sda is my "working" drive, sdb is run on 32bit and has 32bit OS', sdg is 64bit OS'.

Sda is turned off when either of the others is run.  Right now I am transfering some files to the other 2 (I need my tunes).

---

### Post by drs305 on 2009-08-17
> **beacon said:**
> This is silly, I know, but I have downloaded os-prober. How do I run it?

You can get the results by running:
```
sudo os-prober # /usr/bin/os-prober
```
This is normally invoked while running the scripts called by the "update-grub" command (or grub-mkconfig) to help build the grub.cfg file. These scripts are contained in the executable files in /etc/grub.d

---

### Post by beacon on 2009-08-17
Thanks very much for the quick and helpful reply. Now I shall probably sound even sillier. When I run prober it refers to only one OS, when I have two in use. Moreover, when I go to /etc/grub.d, there is only one file labelled 20_memtest86+. Is that the way it should be?

Thanks again.

---

### Post by ranch hand on 2009-08-17
You will have to run update grub after os-prober and then look in /boot/brub/grub.cfg to see the results.  That is where all the info ends up so that you can, in theory, boot to all your OS'.

---

### Post by drs305 on 2009-08-17
> **beacon said:**
> When I run prober it refers to only one OS, when I have two in use. Moreover, when I go to /etc/grub.d, there is only one file labelled 20_memtest86+. Is that the way it should be?

os-prober looks for non-linux operating systems.

/etc/grub.d/ should contain a series of files, each of which helps set specific areas of the grub menu. All of these files should appear in the folder if Grub 2 has been installed properly:

00_header: basic grub settings such as timeouts, default OS selections.
05_debian_theme : themes
10_linux : linux distributions
20_memtest86+ : memtest86+ 
30_os-prober : other operating systems
40_custom : custom user-defined menus

You can read a bit more about them here:
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by xebian on 2009-08-17
> **drs305 said:**
> os-prober looks for non-linux operating systems.

..

Looks for  OS in other partitions, including Linux.

---

