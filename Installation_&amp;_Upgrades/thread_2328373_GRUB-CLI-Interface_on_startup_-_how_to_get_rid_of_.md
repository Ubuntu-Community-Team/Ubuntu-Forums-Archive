---
title: "GRUB-CLI-Interface on startup - how to get rid of it?"
date: 2016-06-20
forum: Installation &amp; Upgrades
---

### Post by atmaps on 2016-06-20
Hi folks! I'm moving with my problem to this forum now, as I couldn't get any help elsewhere so far ...

I'm using Xubuntu 16.04 on an Acer TravelMate B116-M with an SSD (Samsung EVO 850) as its main HDD. The laptop is fully Linux-compatible, I've thoroughly checked it during an earlier install. Btw, I'm pretty sure the problem is not Xubuntu-specific, so I didn't tag the thread with "Xubuntu" ...

Having **this problem** now: **after re-installing Xubuntu on my laptop, GRUB will start with a CLI-interface!** The screen will look like this:

```

GNU GRUB version 2.02~beta2-36ubuntu3

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub> _

```

After first thinking "WTF?", I entered "exit". Startup continued, but quite strangely. I'm not using "quiet splash", so I'm getting all that ... how do you call it? Status messages? But at first, they're totally unreadable, they just look like blocks, not letters. After a few seconds they suddenly become readable (system changing to better screen resolution?), and I have to enter my passphrase (encrypted system, see background info).

The system then starts quite normal, and I can see that the installation seems to be OK - everything works just as it was supposed to.

**Background info:** I've installed a fully encrypted system as follows: unencrypted */boot (ext4)*, then an encrypted LUKS-LVM volume with */swap*, */(root)* and */home* partitions. I'm giving you the link to the "cooking recipe" for that install [here]("https://wiki.ubuntuusers.de/System_verschl%C3%BCsseln/"), but it's all in German, so you might not profit from that ... Suffice to say that I used that install once and it worked just perfect, out of the box - until my root file system got corrupted . If you can read it (or get something out of [Mr Google's translation]("https://translate.google.de/translate?sl=de&tl=en&js=y&prev=_t&hl=de&ie=UTF-8&u=https%3A%2F%2Fwiki.ubuntuusers.de%2FSystem_verschl%25C3%25BCsseln%2F&edit-text=&act=url")), let me add that I deviated from that recipe only in one point: not installing root and home integrally (one partition), but in two separate partitions. After I had been hit by the afore mentioned file system corruption I thought that might be a good idea: I'd fully install the system, then [dd]("http://pubs.opengroup.org/onlinepubs/9699919799/utilities/dd.html") the whole root partition, and if sh... happens again, I'd just re-dd that copy, and problem solved ...

I've already tried GRUB repair once, but it just bricked the system - no GRUB startup any more! I then re-installed, same problem, and I'm now asking you. **Thanks for your help in advance!**

And here some info to give you an idea about my system. I hope if I'm doing it so thoroughly, you will say: oh, that guy is so nice, let's just help him ;-) However, some of that output is in German, which pi... me off, too, but I can't help it for now. But maybe Linux itself is a language universal enough ... There you go:

```


**uname -a; lsb_release -a**
Linux [[computer_name]] 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial


**sudo parted -l**
Modell: ATA Samsung SSD 850 (scsi)
Festplatte  /dev/sda:  500GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: gpt
Disk-Flags: 

Nummer  Anfang  Ende    Größe   Dateisystem  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      539MB   1902MB  1363MB  ext4         /boot
 3      1902MB  446GB   445GB


Modell: TOSHIBA TransMemory (scsi)
Festplatte  /dev/sdb:  7759MB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos
Disk-Flags: 

Nummer  Anfang  Ende    Größe   Typ      Dateisystem  Flags
 1      1049kB  5348MB  5347MB  primary  fat32        boot, LBA
 2      5348MB  7759MB  2412MB  primary  ext4


Modell: Linux device-mapper (linear) (dm)
Festplatte  /dev/mapper/vgubuntu-home:  410GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: loop
Disk-Flags: 

Nummer  Anfang  Ende   Größe  Dateisystem  Flags
 1      0,00B   410GB  410GB  ext4


Modell: Linux device-mapper (linear) (dm)
Festplatte  /dev/mapper/vgubuntu-root:  21,5GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: loop
Disk-Flags: 

Nummer  Anfang  Ende    Größe   Dateisystem  Flags
 1      0,00B   21,5GB  21,5GB  ext4


Modell: Linux device-mapper (linear) (dm)
Festplatte  /dev/mapper/vgubuntu-swap:  12,9GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: loop
Disk-Flags: 

Nummer  Anfang  Ende    Größe   Dateisystem     Flags
 1      0,00B   12,9GB  12,9GB  linux-swap(v1)


Fehler: /dev/mapper/lukslvm: unbekannte Partitionstabelle
Modell: Linux device-mapper (crypt) (dm)                                  
Festplatte  /dev/mapper/lukslvm:  445GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: unknown
Disk-Flags: 


**sudo lsblk -o NAME,UUID,FSTYPE,SIZE,LABEL,MOUNTPOINT**

NAME                UUID                                   FSTYPE        SIZE LABEL MOUNTPOINT
sda                                                                    465,8G       
&#9500;&#9472;sda1              69D1-DAA7                              vfat          512M       
&#9500;&#9472;sda2              e126b9ec-4f9c-40af-a3b3-c6212b38f049   ext4          1,3G       /boot
&#9492;&#9472;sda3              f5a136aa-f614-4fad-91dd-17e9fec5dfcf   crypto_LUKS   414G       
  &#9492;&#9472;lukslvm         39iTvW-Wd72-Vqi3-IZn0-zWf4-H9d9-m9JMGl LVM2_member   414G       
    &#9500;&#9472;vgubuntu-swap 05b0c138-3288-46d0-b963-ffb8e7ea40d5   swap           12G       [SWAP]
    &#9500;&#9472;vgubuntu-root eda5f2b6-5f60-4d05-ac64-ba33bd01f364   ext4           20G       /
    &#9492;&#9472;vgubuntu-home 9eb8ca14-ec50-427b-9d76-b786f9373d19   ext4          382G       /home
sdb                                                                      7,2G       
&#9500;&#9472;sdb1              3F70-4520                              vfat            5G       /media/[[user_name]]/3F70-4520
&#9492;&#9472;sdb2              7d9520c8-db1f-4ce1-9f51-2daaecc3d5e1   ext4          2,3G       /media/[[user_name]]/7d9520c8-db1f-4ce1-9f51-2daaecc3d5e1


**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vgubuntu-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=e126b9ec-4f9c-40af-a3b3-c6212b38f049 /boot           ext4    defaults        0       2
/dev/mapper/vgubuntu-home /home           ext4    defaults        0       2
/dev/mapper/vgubuntu-swap none            swap    sw              0       0


**sudo pvs**

  PV                  VG       Fmt  Attr PSize   PFree
  /dev/mapper/lukslvm vgubuntu lvm2 a--  413,98g    0 


**cat /etc/crypttab**

lukslvm    UUID=f5a136aa-f614-4fad-91dd-17e9fec5dfcf    none    luks
[[user_name]]@[[computer_name]]:~$ ls -la /dev/mapper/
insgesamt 0
drwxr-xr-x  2 root root     140 Jun 19 18:05 .
drwxr-xr-x 22 root root    4680 Jun 19 18:33 ..
crw-------  1 root root 10, 236 Jun 19 18:05 control
lrwxrwxrwx  1 root root       7 Jun 19 18:34 lukslvm -> ../dm-0
lrwxrwxrwx  1 root root       7 Jun 19 18:34 vgubuntu-home -> ../dm-3
lrwxrwxrwx  1 root root       7 Jun 19 18:34 vgubuntu-root -> ../dm-2
lrwxrwxrwx  1 root root       7 Jun 19 18:34 vgubuntu-swap -> ../dm-1

```

And at this point I tried to give you the output of **cat /var/log/syslog** for reboot -> startup -> system up & running (in a code block), but that was probably too much text so I couldn't post the whole thing. If you need it, please give me a hint on how to post it here.

---

### Post by QDR06VV9 on 2016-06-20
Thanks for posting with all the information you took the time to list here...really! But maybe to be clearer on what you need or asking for?
If I assume correctly then this might be of help: [http://www.pavelkogan.com/2014/05/23/luks-full-disk-encryption/](http://www.pavelkogan.com/2014/05/23/luks-full-disk-encryption/)

---

### Post by atmaps on 2016-06-20
> **runrickus said:**
> If I assume correctly then this might be of help: [http://www.pavelkogan.com/2014/05/23/luks-full-disk-encryption/](http://www.pavelkogan.com/2014/05/23/luks-full-disk-encryption/)

Well, thanks, but not quite ... Pavel's doing something similar, but on Arch Linux, and he seems to be ending up with quite another configuration, starting with an encrypted Boot-Partition (I didn't know that was possible; or why anyone would do that) ...

> **runrickus said:**
> But maybe to be clearer on what  you need or asking for?

Well, that's as easy as the thread title: **I want to know to get rid of GRUB's darned CLI interface during startup** ;-) I don't really think that encryption's the issue here - I believe it's rather just a GRUB issue. But I can' rule it out, of course, so I decided to mention it before anyone would tell me off for holding back info on my system configuration ...

Plus, I'd like to understand what has happened here, and why all that startup text comes running up my screen in blocks instead of letters ... Let me give you my */etc/default/grub* here, too. This here is just what I got out of the installation process, going by the book:

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="kopt=root=/dev/mapper/vgubuntu-root"
GRUB_CMDLINE_LINUX="persistent"

```

I left out all the out-commented parts and just gave the active parameters. *"kopt=..."* is necessary for activating ext4-journaling for root, and I should probably add a similar parameter for */home*. Btw, this GRUB-configuration worked well (and without these ... phenomena) in my previous install (root and home in a single partition), and adding the same parameter for *.../vgubuntu-home* didn't change (or solve) my present problem.

It's just that I do not yet understand enough of GRUB, so my problem might have some easy solution. **But why the hell does it now behave like this?**

---

### Post by QDR06VV9 on 2016-06-20
Well mine shows different to get rid of Grub showing....Not sure what you mean by [B]CLI interface?

[/B]```
 &#8230;
    GRUB_DEFAULT=0
    GRUB_HIDDEN_TIMEOUT=0
    GRUB_HIDDEN_TIMEOUT_QUIET=true
    [COLOR=#ff0000]**GRUB_TIMEOUT=0**[/COLOR]
    GRUB_DISTRIBUTOR=&#8221;`lsb_release -i -s 2> /dev/null || echo Debian`&#8221;
    GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;
    GRUB_CMDLINE_LINUX=&#8221;"
```
And just to cover all bases do not forget to update grub
```
sudo update-grub
```
To make the changes on boot.

---

### Post by atmaps on 2016-06-20
> **runrickus said:**
> Not sure what you mean by **CLI interface?**

This here (as in my initial post). It shows up after I switch on the computer (first thing after the ACER logo):

> **atmaps said:**
> 
```

GNU GRUB version 2.02~beta2-36ubuntu3

Minimal BASH-like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device or file completions.

grub> _

```

CLI: "command line interface". Is CLI too unusual as an acronym? Sorry, but in our Linux culture over here, we're using it pretty much.

> **runrickus said:**
> ```
...
    GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;
...
```

I actually don't want "quiet splash", I'm OK with GRUB saying what it does. It gives me the illusion of knowing what's going on, or rather: that something IS going on. It's just the CLI I want to get rid of, without having to enter "exit". And I also want to see part one of the ... you call it "boot splash", right? The part that's presently only unreadable blocks instead of letters (see my first post).

Seriously: I need this system for productive work. And as long as GRUB doesn't work as expected, I can't be sure there's not some deeper problem that will one day come out of its shell and kill the whole system. So I'm not counting peas here, this is all about making sure that this install is really clean and good. And as long as I don't manage to cope with GRUB, I have to assume that this not the case. **It would also be helpful to just know what's going on here.**

---

### Post by atmaps on 2016-06-20
OK, I see. In the thread title I wrote "CLI interface", which is redundant. It should (of course) just read: "GRUB-CLI on startup - how to get rid of it?" Sorry again - but I'm not a native speaker.

---

### Post by QDR06VV9 on 2016-06-20
If this is what you are trying to remove
> GNU GRUB version 2.02~beta2-36ubuntu3  Minimal BASH-like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device or file completions.  grub> _
I also see that..and that is just part of systemd*
CLI I understand that... but I am trying to figure out how you are using it to refer to "The Grub Menu"
So forgive me here I am not trying to add to your frustration but rather trying to get a specific question to help with.
So I am going to ask you.. Do you want a grub-menu to show at boot? or was it just the text flashing by on the initial boot.

---

### Post by atmaps on 2016-06-20
> **runrickus said:**
> I am going to ask you.. Do you want a grub-menu to show at boot? or  was it just the text flashing by on the initial boot.

I want both. And I'm now having both, after editing and updating my /etc/default/grub. But the problem is still the same.

> I am not trying to add to your frustration ...

Don't worry, I wouldn't have thought of that. I appreciate your attention very much.

> that is just part of systemd*
CLI I understand that... but I am trying to figure out how you are using it to refer to "The Grub Menu"

We must have had some sort of misunderstanding - I haven't referred to any "Grub Menu" yet ... But I've done some research and some experiments, and I can tell you now that my GRUB starts not with that menu (where you can e. g. choose in a dualboot system which system to boot), but with some sort of the grub console / grub shell: a grub interface just like that into which you can get by pressing "c" in the grub menu.

Strange thing no. 1 is that it operates with a different set of commands than the grub console that I get into by pressing "c" in the menu. E. g. this initial console doesn't have commands like "vbeinfo" or "videoinfo".

When I type "exit", I'll ONLY NOW get into the grub menu (since my last post, I've */etc/default/grub* and out-commented GRUB_HIDDEN_TIMEOUT). When I now press "c", I'll enter another version of the grub console (but with the same intro text as in the code block above!). And here's strange thing no. 2: the commands "vbeinfo" and "videoinfo" (I haven't tried other commands yet) are now part of the command inventory (looked it up with "help"), but they don't work - they crash the system instead. Could it be that my GRUB's somehow seriously damaged and needs repair?

I tried to repair it: with ...

```
sudo apt-get --reinstall install grub-common grub-pc os-prober
sudo grub-install /dev/sda
```

... but that doesn't work, too. My MBR is in /dev/sda, but grub-install will only give me an error message (in English something like: "... has no BIOS boot partition, embedding would be impossible here").

I admit I'm out of my depth here. It now seems to me that my install is somehow corrupt or badly conceived, although I can't figure out what I could have done wrong. This here is just too strange.

Maybe you or someone else has still got some more ideas?

PS. I also downloaded and ran the Super GRUB2 Disk. When I'm booting from that, the issue with the first few boot splash text pages showing as unreadable blocks does NOT happen, the text is normal and readable. I really think my GRUB needs repair, but I just don't know how to do it.

---

### Post by QDR06VV9 on 2016-06-20
Have you had a look here:[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
It will show you how to reinstall Grub from a Working System.
And this is a bit dated but it will guide you through HOWTO: Purge and Reinstall Grub 2 from the Live CD
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
And usally if Boot Repair dose not fix it I use the Purge and Reinstall Grub 2 from the Live CD method.
Good Luck:)
Kind regards

---

### Post by atmaps on 2016-06-21
Thanks for your kind help, runrickus!

I've tried (once more) a chroot repair of Grub2, but it didn't work. On the plus side, while trying that, I discovered that there obviously was some issue with the live-USB-stick I had used for installing and trying to repair that system. Somehow, "initramfs" and some stuff that's used for dealing with the kernel was not installed properly. I'm now trying to re-install that laptop from scratch using a newly set up live-USB-stick.

But one more question: do you, or does anybody here know about issues when installing (XLK)Ubuntu from live-USB-sticks? Particularly if you use them with persistence? (I've been using UNetBootin for making it.)

---

### Post by mastablasta on 2016-06-21
> **atmaps said:**
> 
But one more question: do you, or does anybody here know about issues when installing (XLK)Ubuntu from live-USB-sticks? Particularly if you use them with persistence? (I've been using UNetBootin for making it.)

occasionally there would be issues. i was let down by unetbootin before. sometimes their script or whatever is running it is not pacthed on time to reflect changes in images. while other times it works perfectly. i had better success with yumi.

as for persistence - don't use it if you plan on system install.

garbled letters - if letters are exchanged with symbols it coul dbe a VRAM issue (GPU RAM), else it is a GPU driver issue (e.g garbeld text/graphics until driver is initialised).

re encryption - do a full one or just home. not sure what anyone would benefit from seing your listed programs and settings. it's the data you are trying to protect.

re GRUB rescue mode - indicates that something is wrongly configured or badly installed regarding GRUB

---

### Post by atmaps on 2016-06-22
**Problem identified and solved.** That strong hunch that I mentioned at the end of my last posting - it was right. **UNetBootin was the culprit.** I researched and found quite a few hits with the terms "unetbootin encryption problem". One guy in a German forum said that it was "well known that UNetBootin is altering the image", and suggested to try the latest version. But I had it right out of the repository.

Exactly repeating an earlier install that had worked when using the live-CD: broken when using a UNetBootin medium (in exactly the same way).
Exactly repeating what I tried to do during the last two days WITHOUT using a UNetBootin medium, but the live-CD instead: everything works perfect!

My conclusion is: **UNETBOOTIN IS BROKEN.** It may work well for regular installs, but if you deviate from that (with system encryption, and who knows in which other ways, too), chances are that you get into a problem loop and loose days of your life time just to find out WTF went wrong ... Pass it on to others.

I'm having access to a Win 7 installation, so I'm trying to get a USB live installer (Xubuntu) running with "Rufus". Quite a number of people recommended it in the forums.

---

### Post by atmaps on 2016-06-22
> **mastablasta said:**
> occasionally there would be issues. i was let down by unetbootin before. sometimes their script or whatever is running it is not pacthed on time to reflect changes in images. while other times it works perfectly.

Sorry - found this here only after my last posting. It had slipped on page 2 of the thread ... But anyway, you'd have helped me very much ;-)

>  re GRUB rescue mode - indicates that something is wrongly configured or badly installed regarding GRUB

Already tried - didn't work, and there were also a number of other issues with that install (standby not working, etc.)

> re encryption - do a full one or just home. not sure what anyone would benefit from seing your listed programs and settings. it's the data you are trying to protect.

I had that discussion a number of times in other places, please bear with me if I don't want that again. My reasons in short: I consciously don't want to follow a standard encryption scheme. If some possible attacker wants to get at me, let's give him some extra work. And I don't want to give possible access to my root system from my unencrypted secondary Windows install. No, I'm not wearing a tin-foil hat, and yes, I see that there are big loop-holes here, too. No need to point them out, and once more, thanks a lot :-)

---

### Post by mastablasta on 2016-06-23
> **atmaps said:**
>  If some possible attacker wants to get at me, let's give him some extra work. And I don't want to give possible access to my root system from my unencrypted secondary Windows install. 

encrpytion is primarily guarding against stolen device,. when you log in the data is not encrpyted anymore. ;-)

i hope no one ever steals your device. and if they do, they should have their work cut out for them....

---

